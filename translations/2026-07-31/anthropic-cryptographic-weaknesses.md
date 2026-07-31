# 用 Claude 发现密码学缺陷

> **原文**：[Discovering cryptographic weaknesses with Claude](https://www.anthropic.com/research/discovering-cryptographic-weaknesses)
> **翻译**：AI 自动翻译，经审校

---

## 摘要

使用 Claude Mythos Preview，Anthropic 的研究人员发现了改进的攻击密码算法（用于保护在线数据隐私的数学方法）的途径。第一种攻击显著削弱了 HAWK——一种为后量子世界构建的数字签名方案。第二种攻击找到了攻击简化轮次 AES（最广泛使用的对称密码）的新方法。这些都是实质性的研究进展，但目前不会影响任何生产系统。本文更详细地描述了这两项发现，并讨论了在强大 AI 模型时代密码学面临的启示。

## 引言

当我们发布 Claude Mythos Preview 时，我们展示了它能够自主地在我们指向的几乎所有软件中发现和利用漏洞。这包括几个主要的密码学库——用于加密数据的共享代码集合。

Claude 在这些密码学库中发现的漏洞是由于算法的不正确实现——即程序员在代码中使用算法时产生的错误，为攻击者创造了破解加密的机会。

现在，我们发现 Claude 能够找到算法本身的数学缺陷。

密码算法是数字安全的基础构建模块。例如，当你访问 [https://www.anthropic.com](https://anthropic.com) 这样的网页时，你的浏览器使用一种称为数字签名方案的算法来检查它正在与一个真实的网站通信。随后，你和网站之间的流量使用对称密码——允许共享相同密钥的各方之间安全传输数据的编码——进行加密。没有这样安全的密码系统，你的电子邮件、在线银行和其他互联网使用将向网络犯罪分子敞开，他们可以拦截或修改你的通信。这些广泛使用的密码系统中的缺陷可能使数十亿用户的数据面临风险。

我们在本文中描述的第一个结果——使用 Claude Mythos Preview 发现的——是对一种名为 [HAWK](https://csrc.nist.gov/csrc/media/Projects/pqc-dig-sig/documents/round-1/spec-files/hawk-spec-web.pdf) 的数字签名方案的改进攻击。2022 年，美国政府 [国家标准与技术研究院](https://www.nist.gov/)（NIST）发布了征集[额外密码系统](https://csrc.nist.gov/projects/pqc-dig-sig/round-3-additional-signatures)的公告，这些系统即使在量子计算机面前也能保持安全（量子计算机如果被开发出来，可能破解当今使用的大多数现有签名方案）。HAWK 是该征集的第三轮候选方案之一。尽管 HAWK 在两年内经历了两年两轮的人类专家审查，Mythos 仅用 60 小时就改进了已知最佳攻击——实际上将其密钥强度削减了一半。

第二个结果涉及 [高级加密标准](https://www.nist.gov/publications/advanced-encryption-standard-aes)（AES），一种由 NIST 于 2001 年采用的对称密码，它比几乎所有其他加密算法都受到了更多的审查。为了更好地理解 AES 的稳健性，密码学研究中经常研究算法的较弱变体；Mythos 找到了破解其中一种较弱版本的方法，消除了攻击者需要做出的一个猜测，将此前最佳攻击的速度提升了 200-800 倍。

需要明确的是，这两个结果目前都不会对当今的计算机系统产生实际影响；不会有生产软件因此需要更改。HAWK 只是一个候选签名方案，尚未部署；我们的第二个攻击针对的是 AES 的简化版本，并未破解完整密码。

尽管如此，两个结果都表明前沿 AI 模型在帮助发现重要密码算法中的缺陷方面具有潜力——无论是在实际部署之前还是之后。这是密码学研究按预期运作：对算法进行压力测试以建立信任，最终使系统更加安全。

Mythos Preview 在很大程度上自主完成了这些结果，大部分过程无需人工干预。在一周时间内，一名 Anthropic 研究员与 Claude 合作开发了 HAWK 攻击，另一名研究员构建了一个脚手架，使 Claude 能够完全自主地发现 AES 攻击。每个结果的开发成本约为 10 万美元的 API 费用。在看到这些结果后，我们扩大了搜索范围并开始发现其他攻击。我们在下文讨论了其中一些后续发现。

为了使其他人更容易地继续研究 LLM 的密码分析能力，我们与苏黎世联邦理工、特拉维夫大学和柏林工业大学的学者合作构建了 [CryptanalysisBench](https://arxiv.org/abs/2607.18538)，这是一个将许多密码打包在一起的基准，使其他人能够轻松评估 LLM 在这一重要主题上的能力。

在整个研究过程中，我们遵循了负责任的披露程序，并咨询了学者以确认发现的有效性。我们还向美国政府及行业合作伙伴分享了提前副本，并就这项研究的启示进行了讨论。关于 HAWK 发现，我们在 6 月向 HAWK 的作者分享了攻击，并在公布结果的同时协调向 NIST 公开邮件列表披露。

在本文的其余部分，我们进一步总结了两项发现的技术细节，并简要描述了一些其他近期的密码学研究成果。两项主要发现的完整描述在两篇新论文中提供，我们希望在未来发布其他发现的细节。

## 针对 HAWK 的改进密钥恢复攻击

与 Mythos Preview 合作，一名 Anthropic 研究员开发了对 [HAWK](https://hawk-sign.info/) 后量子数字签名方案的攻击。该攻击大幅加快了破解签名方案所需的时间——更技术性地说，它将"有效密钥大小"减少了二分之一。在我们的[论文](https://anthropic.com/document/hawk_key_recovery.pdf)中，我们提供了结果的完整技术细节，包括[演示代码](https://github.com/anthropics/cryptography-research-demo)。

HAWK 是 NIST [额外数字签名](https://csrc.nist.gov/projects/pqc-dig-sig/round-3-additional-signatures)征集的剩余第三轮候选方案之一。该竞赛是近十年努力标准化新的[后量子密码](https://csrc.nist.gov/Projects/post-quantum-cryptography/post-quantum-cryptography-standardization)（PQC）方案的一部分。随着构建密码学相关量子计算机的前景[日益临近](https://blog.google/innovation-and-ai/technology/safety-security/cryptography-migration-timeline/)并威胁到 RSA 或 ECDSA 等经典密码学，这一标准化努力变得至关重要。

HAWK 的安全性基于一个称为格同构问题的数学问题的困难性。Mythos 的攻击通过在 HAWK 使用的格中找到一种特定的、先前未被利用的对称性——称为非平凡自同构——来工作。[先前工作](https://eprint.iacr.org/2025/928)证明了有效地找到这样的自同构将允许攻击，但没有回答这样的自同构在 HAWK 使用的格中是否可访问。Mythos 发现的自同构允许更快的枚举攻击，虽然仍然是指数级的，但意味着需要将 HAWK 的密钥大小翻倍才能达到相同的安全水平。不幸的是，将 HAWK 的密钥大小翻倍会消除使该方案（就目前而言）成为有吸引力的 PQC 签名候选者的许多原因。

### 发现阶段

为找到攻击，Claude Mythos Preview 在代理式脚手架中半自主地工作，偶尔接受人类指导和非技术性指示。Mythos 在广泛的文献综述了解最新技术水平后，通过大量数学推理和计算实验找到了攻击。找到攻击后，Mythos 实现了端到端的验证流程，以使自己——以及人类操作者——相信攻击的正确性。

在这项实验中，我们使用了一个类似 Claude Code 的脚手架，支持多个工作代理在沙箱环境中协作，可以访问 Python 和 Sage 等计算工具以及已发表的密码学文献。人类操作者具有理论计算机科学背景，但不是基于格的密码学专家。在大多数情况下，Mythos 代理独立工作，人类输入仅限于项目管理，例如建议 Mythos 如何记录想法或使用哪些库进行计算验证。

多代理工作流产生了有趣的动态。例如，产生这项攻击的关键想法是由一对协作的工作代理发现的。两者都开始调查这个想法；第一个代理过早地否定了该想法，认为不可行，但第二个代理找到了完全利用它的方法。这对代理不断交换消息，最终两者都同意找到了有效的攻击。

发现、开发和验证攻击总共花了大约 60 小时。我们估计完整的攻击发现过程花费了大约 10 万美元的 API 费用。

### 影响

Mythos 发现的直接影响是 HAWK 提案中提出的密钥大小明显弱于原先建议的。例如，针对小型 HAWK-256 尺寸的完整密钥恢复攻击的预期成本原以为是 2^64，但 Mythos 证明为 2^38。对于更大的密钥，HAWK 因此仍然不切实际地难以攻击。也就是说：此攻击是比已知方法更快的指数时间攻击，并非多项式时间攻击。它特定于 HAWK，不影响其他 NIST 后量子签名候选方案或基于格的密码学整体。

NIST 提案公开分享的目的是允许广泛受众在部署前审查它们以发现缺陷。在过程后期发现关键缺陷并非前所未有：在 NIST 标准化 ML-KEM 和 ML-DSA 期间，几个竞争提案被证明是不安全的。一个候选方案 SIKE 被发现[可以在笔记本电脑上一小时内完全破解](https://www.quantamagazine.org/post-quantum-cryptography-scheme-is-cracked-on-a-laptop-20220824/)。

我们相信，使用 AI 审查 HAWK 等规范将成为开发新型密码标准的强大工具。我们期望配备了高度能力模型的密码设计者能持续改进保护互联网用户的标准。在更远的未来，我们希望 AI 将在设计下一代更强大、更具韧性的密码方案中发挥关键作用。

## 针对简化轮次 AES 的改进攻击

在第二个结果中，Mythos Preview 改进了对 [高级加密标准](https://www.nist.gov/publications/advanced-encryption-standard-aes)（AES）的一种更简单的"简化轮次"变体的攻击。AES 于 2001 年作为先前一次 [NIST 竞赛](https://csrc.nist.gov/news/1997/requesting-candidate-algorithm-nominations-for-aes)的一部分被采用。

AES 通过反复多次应用同一轮函数来加密输入。AES-128——我们攻击的具体密码——有 10 轮。我们的攻击仅针对完整 10 轮中 7 轮的修改版本。学者们经常研究简化轮次密码，以获得对攻击技术的洞察，这些技术未来可能推广到完整密码，并通过研究较简单的子问题来帮助估计完整密码的安全水平。

该攻击在选择性明文威胁模型下运行，这是研究 AES 等密码时使用的最常见假设。在此威胁模型下，我们假设攻击者能够请求防御者使用固定的、未知的密钥加密任意输入，然后看到相应的输出。攻击者可以反复发出加密请求，且可以发出大量请求。我们基于的先前工作假设攻击者可以请求 2^105 个选择性明文的加密。因此，此攻击完全不切实际，但在这些假设下量化了针对 AES 的攻击成本。

Mythos 能够开发出一种改进攻击，延续了长期以来一系列研究论文的努力，这些论文都旨在使用称为"中间相遇攻击"的类似技术找到对 7 轮 AES 的最佳攻击。从高层次来看，这些攻击通过以空间换时间来工作。通过存储中间计算然后重复使用这些计算，可以显著减少攻击的运行时间，代价是构建一个大型查找表。

Mythos 通过开发一种更复杂的指纹算法改进了此前最强的中间相遇攻击，该算法被称为 Möbius Bridge（莫比乌斯桥）。指纹算法的目标是增加表中成功查找的潜在次数。先前工作中攻击的一个阶段必须枚举 2^56 个不同的值，然后在预计算表中查找它们。Mythos 开发了一种对该猜测不变的指纹，直接将所需工作量减少了 2^56 倍。但这有一个代价：计算变换在计算上更昂贵；为了解决这个问题，Mythos 发现了其他几种优化技术，最终使攻击速度提高了 200 到 800 倍，具体取决于测量运行时使用的具体技术。

我们的[技术论文](https://anthropic.com/document/aes_mobius_bridge.pdf)包含了攻击方法的完整细节及其正确性和运行时分析。相比 Mythos 花费一周时间构思想法，人类研究者的大部分时间都花在验证其声明的正确性上（但需要注意的是，研究者并非密码学专家）。

### 发现过程

Mythos Preview 几乎完全自主发现了这一结果。Anthropic 的一名研究员构建了一个脚手架，使 Claude 能够提出假设、运行实验来实验性地验证或反驳这些假设，然后要求 Claude 设计一种改进 AES 最佳密码分析的攻击。

起初，Claude 不愿参与这个问题，因为它声称改进 AES 的密码分析是不可能的。我们第一次运行的结果以 Claude 写下这样的消息告终：

> "If you want a different outcome, the target has to change … AES-128 r5/r6 is just genuinely hard"

或者：

> "on AES-128 r5/r6/r7 it found nothing because there's nothing easy to find; this is the most-studied block cipher in existence."

为解决这个问题，我们给 Claude 写了一条消息（以下我们发布了研究员使用的真实提示，包括拼写和语法错误）："the models tend to think it is impossible to solve so they don't try they [sic] need a good amount of prompting." 作为对这一条消息的回应，Claude 用改进的设置重写了代理脚手架，告诉它搜索真正新颖的想法。这很有效，Claude 发现了一些有助于改进 AES 6 轮密码分析的新想法。

然后我们问 Claude "why not do aes-128 r7? the whole point is to find something better than existing approaches." 在接下来的三天里，Claude 自主产生了数亿个 token 来解决这个问题；我们只给了三个实质性提示：

- 在第一条消息几小时后，我们发现 Claude 仍在搜索简单攻击并发送了一条消息："no again the goal is that we have highly inteligent [sic] model as good top researcher, we want to find new attacks"；
- 第二天早上，Claude 想要尝试将目标更改为不同的密码；我们提醒模型："no we don't want to change the targets [...] agian [sic] we need to find something that worth [sic] publishing"；
- 那天晚上，我们发送了最后一条鼓励性消息："again we are not looking for low hanging fruit, we want proper research to find genuinly [sic] hard findings."

三天后，Mythos 发现了 Möbius Bridge 想法，由此产生了改进攻击。几天后，在 Claude 总共输出了十亿个输出 token 之后，它将攻击完善为论文中描述的形式。

Anthropic 的研究员随后花费了数百小时学习足够的密码学研究知识来验证模型的声明，并准备[研究论文](https://anthropic.com/document/aes_mobius_bridge.pdf)本身，我们将其与本文一同发布。

除了研究论文外，我们还发布了一份包含 [Claude 在发现关键算法洞察期间的思维链](https://anthropic.com/document/aes_mobius_bridge_cot.pdf)的文档。在这个会话中，Claude 首先回顾之前代理发现的内容，阅读各种批评，然后转向提出各种新的变换；在提出并否定了几个想法后，它想出了 Möbius 变换的关键想法。Claude 随后从数学和计算上验证了这一想法，然后撰写了一份报告，供未来的代理用于开发构成其论文的其余想法。

## 进一步研究

还有更多准备就绪的密码学研究可以用语言模型来执行。但我们正在达到自身知识的极限，过去几个月我们大部分时间都花在验证 Claude 结果的正确性上。HAWK 攻击可以端到端实现，因此更容易验证。但虽然 Mythos 仅用一周就自主发现了 AES 的改进攻击，两名研究员却花了近一个月才能确信其发现的方法是正确的。

尽管如此，我们继续使用 Claude 进行了许多其他初步的密码学实验。例如，轻量级加密算法（LEA）是一种为低功耗、资源受限环境设计的高效密码，已被编入 ISO/IEC 29192-2:2019 等国际标准。该密码与 AES 一样是分组密码；完整的 24 轮密码经受住了全轮密码分析，即使在评估简化轮次变体时也保持强健。目前，对 LEA 13 轮的最佳密码分析[需要](https://jeit.ac.cn/article/doi/10.11999/JEIT221282) 2^98 个明文对和 2^86 的工作量。

Mythos Preview 开发了一种实际攻击，可以在不到 2^30 个加密明文的情况下恢复 13 轮 LEA 密钥，并在现代台式计算机上不到一小时内运行完毕。同样，此攻击不适用于 24 轮密码，因此没有直接的实际影响。由于此攻击实际上可以端到端运行（如 HAWK 攻击一样），我们对其正确性更有信心：我们可以选择一个随机密钥，并验证此攻击能在几小时内恢复它。Mythos 更近期才发现此攻击，我们仍需做更多工作来理解完整结果（例如所需明文对数量的确切边界、某些密钥更难恢复的程度，以及如何扩展到 14 轮）。经过更多调查后，我们计划公开完整结果。

Mythos Preview 还发现了另一个针对 Serpent-128 密码 6 轮的实际完整密钥恢复攻击（Serpent-128 是一种 32 轮密码——再次限制了此攻击的影响），扩展了当前的[已发表工作](https://dl.acm.org/doi/10.5555/647935.740922)，后者需要超过 2^70 个明文对和 2^90 次解密。我们还发现了对 Salsa20 流密码、Poseidon 哈希函数和 SHA-1 哈希函数攻击的额外、相对有限的改进（增益 <10 倍）。这些攻击目前没有那么强——但通过进一步工作，我们希望既能改进上述结果，又能开发对其他密码的新攻击以测试其极限。

此外，我们计划继续在 [CryptanalysisBench](https://arxiv.org/abs/2607.18538) 上进行实验，以跟踪前沿 LLM 能力随时间的演变。我们认为跟踪语言模型在各领域能力的发展非常重要，并期望随着模型变得更强大，越来越依赖于此类具有挑战性的基准。

## 结论

这并非语言模型首次执行研究级别的数学。仅在最近几个月，Google 的研究人员使用 Gemini [解决了若干 Erdős 开放问题](https://deepmind.google/blog/alphaevolve-impact/)，OpenAI 的研究人员使用 GPT [解决了单位距离猜想](https://openai.com/index/model-disproves-discrete-geometry-conjecture/)（一个特别具有挑战性的 Erdős 问题），本月早些时候我们[宣布 Claude Fable 5 解决了](https://x.com/__alpoge__/status/2079028340955197566) [Jacobian 猜想](https://en.wikipedia.org/wiki/Jacobian_conjecture)。我们这里的结果——Claude 能够以顶尖专家的水平执行密码学研究——表明这些同样的能力也在密码学领域有应用，因此可能很快产生更实际的影响。

网络安全社区正在努力应对这样一个事实：语言模型能够发现[如此多的漏洞](https://www.anthropic.com/research/glasswing-initial-update)，以至于标准的人工流程（如漏洞分类、验证和修复）难以跟上。我们预测，学术密码学研究很快也会出现同样的情况。随着语言模型越来越多地自主产生新颖的研究成果，人类研究者可能会在研究和验证这些结果的技术有效性、新颖性和实用性方面遇到瓶颈。在未来几周，我们将举办一次学术研讨会，与学术界各领域的研究者讨论语言模型在安全和密码学研究中的角色。我们希望这场对话能在未来数月内在安全研究及更广泛领域持续下去。

我们的两项主要攻击都是预期结果。在 HAWK 的案例中，NIST 标准化流程的目的就是在候选方案部署前发现弱点。在 AES 的案例中，我们的攻击延续了此前成功攻击简化轮次变体的长期工作。但我们不应假设语言模型的能力会停滞在这个水平。仅一年时间，语言模型已经从无法进行哪怕是基础密码的密码分析，发展到能够在逃脱了多年人类专家审查的密码设计中发现缺陷。保护现代系统的许多密码受到的审查可能少于它们应得的——它们可能仍然隐藏着 LLM 很快就能发现的重要弱点。我们认为这是一个真正的机会，可以扩展我们研究全世界使用的长尾密码的能力，也可以更深入地研究最重要的密码。事实上，如上所述，我们已经开始了对其他方案的审计。

这两篇论文中描述的攻击是我们迄今为止发现的最强攻击。经过与美国政府和行业领导者的协商期后，我们正在分享这些结果。但随着我们开发出越来越强大的密码分析结果，如果语言模型在确实具有直接现实影响的密码系统中发现了漏洞，研究者应该如何应对，这是一个值得深思的问题。我们认为回答这个问题需要学术界、政府和行业的共同投入。我们希望我们在这里的工作能帮助启动这些对话。

密码学社区一直受益于对抗性审查：密码被提出、被审查、被修订，直到社区对其安全性满意。从长远来看，我们期望语言模型将在这一过程中发挥重要作用，带来更严格的审查、更安全的算法——最终为全世界带来更好的安全。

### 完整研究论文链接

阅读 [HAWK 完整论文](https://anthropic.com/document/hawk_key_recovery.pdf)。
阅读 [AES 完整论文](https://anthropic.com/document/aes_mobius_bridge.pdf) 及相关的[思维链文档](https://anthropic.com/document/aes_mobius_bridge_cot.pdf)。
阅读 [CryptanalysisBench 介绍论文](https://arxiv.org/abs/2607.18538)。

---

*译者注：本文为 AI 自动翻译，已尽最大努力保证准确性和完整性。如需引用，请以[英文原文](https://www.anthropic.com/research/discovering-cryptographic-weaknesses)为准。*
