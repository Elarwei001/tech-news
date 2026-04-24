# Introducing GPT-5.5

- 原文链接：https://openai.com/index/introducing-gpt-5-5/
- 发布日期：2026-04-23
- 说明：以下为基于 OpenAI 官方原文的完整中文翻译，保留核心结构、数据与专有名词。

---

我们发布 GPT-5.5。这是我们目前最聪明、也最直觉易用的模型，也是迈向一种全新“在电脑上完成工作”方式的下一步。

GPT-5.5 能更快理解你究竟想做什么，也能自己承担更多工作。它在编写和调试代码、在线研究、分析数据、创建文档和电子表格、操作软件，以及跨工具持续推进直到任务完成方面表现出色。你不再需要精细管理每一步，而是可以把一个混乱、多部分组成的任务直接交给 GPT-5.5，相信它能够自己规划、使用工具、检查工作、穿越模糊性，并继续推进。

这种提升在 agentic coding、computer use、knowledge work 和早期 scientific research 上尤其明显。在这些领域里，进步依赖于跨上下文推理，以及随着时间推移采取行动。GPT-5.5 在不牺牲速度的前提下实现了这种智能跃迁：更大、更强的模型通常服务更慢，但 GPT-5.5 在真实服务中的每 token 延迟与 GPT-5.4 相当，同时整体智能水平更高。它在完成相同 Codex 任务时所使用的 token 也显著更少，因此不仅能力更强，也更高效。

我们在发布 GPT-5.5 时，配套上线了迄今为止最强的一套 safeguards，目标是在保留有益用途访问能力的同时降低滥用风险。我们用完整的 safety 与 preparedness framework 对该模型进行了评估，与内部和外部 red teamers 合作，增加了针对 advanced cybersecurity 与 biology capabilities 的定向测试，并在发布前从近 200 家值得信赖的 early-access partners 那里收集了真实用例反馈。

今天，GPT-5.5 正在向 ChatGPT 和 Codex 中的 Plus、Pro、Business 与 Enterprise 用户推出，GPT-5.5 Pro 也正在向 ChatGPT 中的 Pro、Business 与 Enterprise 用户推出。API 部署需要不同的 safeguards，我们正在与合作伙伴和客户密切合作，以满足大规模提供该模型所需的 safety 与 security 要求。我们很快会将 GPT-5.5 和 GPT-5.5 Pro 带到 API。

## 关键评测结果

OpenAI 在文中给出了一组对比数据，显示 GPT-5.5 在多项与代码、工具使用、知识工作和数学相关的评测上，相比 GPT-5.4 有进一步提升，并在部分项目上优于 Claude Opus 4.7 与 Gemini 3.1 Pro。

主要指标包括：

- Terminal-Bench 2.0：82.7%
- Expert-SWE（内部）：73.1%
- GDPval（胜或平）：84.9%
- OSWorld-Verified：78.7%
- Toolathlon：55.6%
- BrowseComp：84.4%
- FrontierMath Tier 1–3：51.7%
- FrontierMath Tier 4：35.4%
- CyberGym：81.8%

OpenAI 表示，GPT-5.5 是其目前最强的 agentic coding 模型。在 Terminal-Bench 2.0 这类要求规划、迭代与工具协同的复杂命令行流程评测中，GPT-5.5 实现了 82.7% 的准确率。在 SWE-Bench Pro 中，它达到 58.6%，能够一次性端到端解决更多真实 GitHub issue。在内部用于评估长时间跨度编码任务的 Expert-SWE 上，它也优于 GPT-5.4。

OpenAI 强调，在这些评测中，GPT-5.5 不仅分数更高，而且完成任务所需 token 更少。

## 在工程工作中的表现

这些编码能力在 Codex 中体现得尤其明显。GPT-5.5 可以承担从实现、重构到调试、测试与验证的一系列工程工作。早期测试表明，GPT-5.5 更擅长真实工程依赖的行为，例如在大型系统中保持上下文、推理模糊故障、借助工具检查假设，以及把修改贯彻到整个代码库中。

OpenAI 还引用了多个外部测试者的反馈：

- Every 创始人兼 CEO Dan Shipper 认为，GPT-5.5 是“我用过的第一个具有严肃概念清晰度的 coding model”。
- MagicPath CEO Pietro Schirano 观察到，GPT-5.5 能在大规模前端与重构变更分支和已变化的主分支之间，一次性完成合并，用时大约 20 分钟。
- 一些资深工程师表示，GPT-5.5 在推理和自主性方面明显强于 GPT-5.4 和 Claude Opus 4.7，能够提前发现问题，并预判测试和评审需要。
- 一位在 NVIDIA 提前接触该模型的工程师甚至表示：“失去 GPT-5.5 的访问权限，就像我被截去了一条肢体。”
- Cursor 联合创始人兼 CEO Michael Truell 表示，GPT-5.5 比 GPT-5.4 更聪明、更持久，编码表现更强，工具使用也更可靠，能够显著更长时间保持在任务上，不会过早停下，这对用户委托的复杂长时间工作尤为关键。

## 在知识工作与电脑操作中的表现

让 GPT-5.5 成为强大 coding 模型的同一组能力，也让它更适合在电脑上处理日常工作。由于模型更擅长理解意图，它可以更自然地穿过知识工作完整循环：寻找信息、理解重点、使用工具、检查输出，并把原始材料变成有用结果。

OpenAI 表示，在 Codex 中，GPT-5.5 比 GPT-5.4 更擅长生成文档、表格和幻灯片。Alpha 测试者称，它在 operational research、spreadsheet modeling，以及把混乱的业务输入转化成计划等任务上优于过去模型。结合 Codex 的 computer use 能力后，GPT-5.5 让人更接近一种感觉：模型可以真正和你一起使用电脑，看见屏幕内容、点击、输入、导航界面，并跨工具精准移动。

OpenAI 还披露，公司内部已有超过 85% 的员工每周都会在软件工程、财务、传播、市场、数据科学和产品管理等职能中使用 Codex。

- 在传播团队中，团队使用 Codex 分析了 6 个月的 speaking request 数据，构建评分和风险框架，并验证一个自动化 Slack agent，使低风险请求可自动处理，而高风险请求仍交给人工审核。
- 在财务团队中，Codex 被用来审查 24,771 份 K-1 税表，总计 71,637 页，工作流排除了个人信息，并帮助团队比上一年提前两周完成任务。
- 在 Go-to-Market 团队中，一名员工自动化了每周业务报告生成流程，每周节省 5 到 10 小时。

在 ChatGPT 中，GPT-5.5 Thinking 为更难问题提供更快帮助，并给出更聪明、更简洁的答案，帮助用户更高效地处理复杂工作。OpenAI 表示，它尤其擅长专业场景，例如编码、研究、信息综合与分析，以及重文档工作，尤其是在结合插件时。

对于 GPT-5.5 Pro，早期测试者观察到，ChatGPT 能承担的工作难度和质量都有显著提升，而延迟改进让它更适合高要求任务。与 GPT-5.4 Pro 相比，测试者认为 GPT-5.5 Pro 的回应更全面、结构更好、更准确、更相关，也更有用，在 business、legal、education 和 data science 上尤其强。

## 在知识工作评测中的表现

OpenAI 表示，GPT-5.5 在多项反映真实知识工作的评测中达到 state-of-the-art 水平：

- 在 GDPval 上，GPT-5.5 得分 84.9%。该评测覆盖 44 个职业，考察 agent 产出高规格知识工作的能力。
- 在 OSWorld-Verified 上，GPT-5.5 达到 78.7%。该评测衡量模型能否独立操作真实电脑环境。
- 在 Tau2-bench Telecom 上，GPT-5.5 在无需 prompt tuning 的情况下达到 98.0%。
- 其他知识工作评测中，GPT-5.5 还在 FinanceAgent 上达到 60.0%，在内部 investment-banking modeling 任务上达到 88.5%，在 OfficeQA Pro 上达到 54.1%。

NVIDIA 企业 AI 副总裁 Justin Boitano 表示，GPT-5.5 提供了执行密集型工作所需的持续性能，帮助团队从自然语言提示中交付端到端功能，把调试时间从数天缩短到数小时，并把数周实验变成一夜间的进展。

## 在科学研究中的表现

OpenAI 还强调，GPT-5.5 在 scientific 与 technical research 工作流中也有明显提升。这类工作不只是回答一个难题，而是需要探索想法、收集证据、测试假设、解释结果，并决定下一步尝试什么。OpenAI 认为，GPT-5.5 比其他模型更擅长在这一完整循环中持续推进。

文中提到：

- GPT-5.5 在 GeneBench 上明显优于 GPT-5.4。该评测聚焦 genetics 和 quantitative biology 中多阶段科学数据分析。
- 在围绕真实世界 bioinformatics 和数据分析任务设计的 BixBench 上，GPT-5.5 在已公开分数模型中也达到领先表现。
- 一个内部版本的 GPT-5.5 配合定制 harness，还帮助发现了一个有关 Ramsey numbers 的新证明，且结果之后用 Lean 进行了验证。

OpenAI 认为，这些结果表明 GPT-5.5 不只是更擅长写代码或解释问题，而是已经能够作为真正的研究协作者，加速生物医学研究前沿的进展。

文中还列举了两个案例：

- Jackson Laboratory for Genomic Medicine 的免疫学教授兼研究员 Derya Unutmaz 使用 GPT-5.5 Pro 分析一个包含 62 个样本、近 28,000 个基因的表达数据集，产出了一份详细研究报告，不仅总结了发现，还提出关键问题和洞见。他表示，这项工作本来会花团队数月时间。
- 波兰 Adam Mickiewicz University 的数学助理教授 Bartosz Naskręcki 使用 GPT-5.5 in Codex，仅凭一个提示，在 11 分钟内构建了一个 algebraic-geometry 应用，能够可视化二次曲面的交线，并将所得曲线转换为 Weierstrass 模型。

## 服务与基础设施

为了在保持 GPT-5.4 延迟的同时服务 GPT-5.5，OpenAI 表示它把 inference 重新视作一个一体化系统，而不是一组孤立优化。GPT-5.5 是围绕 NVIDIA GB200 和 GB300 NVL72 系统共同设计、训练并部署的。OpenAI 还表示，Codex 和 GPT-5.5 本身在实现这些性能目标的过程中也发挥了作用，帮助团队更快地从想法走到可测试实现，并找出哪些优化值得深入投入。

其中一个具体改进是负载均衡和分片启发式。OpenAI 解释说，在 GPT-5.5 之前，请求会被切分为固定数量的块，在计算核心之间做平衡，以确保大请求和小请求可以在同一 GPU 上运行。但静态块数量并不适用于所有流量形态。为提高 GPU 利用率，Codex 分析了数周生产流量模式，并编写了自定义启发式算法，用于更优地分区和负载均衡。这项工作让 token 生成速度提高了 20% 以上。

## 网络安全与安全防护

OpenAI 表示，世界需要为那些非常擅长发现并修复安全漏洞的模型做好准备，这需要整个生态共同努力以增强韧性。前沿模型在 cybersecurity 上的能力正不断提升，这些能力最终会广泛分布。OpenAI 认为，最佳路径是确保这些能力能被用来加速 cyber defense，并强化整个生态。

OpenAI 将 GPT-5.5 描述为迈向“可以解决如网络安全等世界最棘手挑战”的 AI 的一个渐进但重要步骤。它表示，在 GPT-5.2 时已经主动部署了必要的 cyber safeguards 来限制潜在滥用，而在 GPT-5.5 上则将部署更严格的 classifiers，用于识别潜在 cyber risk。OpenAI 也承认，用户一开始可能会觉得这些限制烦人，但公司会随着时间继续调优。

OpenAI 还指出，它多年来一直在 Preparedness Framework 中把 cybersecurity 视为重点类别，以便在模型能力逐步增强的同时，迭代开发和校准相应缓解措施，从而负责任地发布具备显著网络安全能力的模型。

---

## 译后说明

这篇发布稿的核心不只是“GPT-5.5 更强”，而是 OpenAI 正在把模型能力更明确地包装成一种可以长期持续执行复杂任务的工作引擎。原文大量篇幅集中在 coding、computer use、knowledge work、scientific research 与 safety 上，说明 GPT-5.5 的定位已经明显超出传统聊天模型，而更接近一个可以在工具链中持续运作的 agentic system。

*AI 翻译，仅供参考；如需精确表述，请以 OpenAI 官方英文原文为准。*