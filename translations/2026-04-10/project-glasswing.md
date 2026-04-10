# Project Glasswing: Securing the World's Most Critical Software in the AI Era
# Project Glasswing：在 AI 时代保护世界上最关键的软件

## Introduction
## 简介

Today we're announcing Project Glasswing, a new initiative that brings together Amazon Web Services, Anthropic, Apple, Broadcom, Cisco, CrowdStrike, Google, JPMorganChase, the Linux Foundation, Microsoft, NVIDIA, and Palo Alto Networks in an effort to secure the world's most critical software.
今天我们宣布 Project Glasswing，这是一个新举措，汇集了 Amazon Web Services、Anthropic、Apple、Broadcom、Cisco、CrowdStrike、Google、JPMorganChase、Linux Foundation、Microsoft、NVIDIA 和 Palo Alto Networks，共同致力于保护世界上最关键的软件。

We formed Project Glasswing because of capabilities we've observed in a new frontier model trained by Anthropic that we believe could reshape cybersecurity. Claude Mythos Preview is a general-purpose, unreleased frontier model that reveals a stark fact: AI models have reached a level of coding capability where they can surpass all but the most skilled humans at finding and exploiting software vulnerabilities.
我们发起 Project Glasswing 是因为观察到 Anthropic 训练的一个新型前沿模型所具备的能力，我们认为这种能力可能重塑网络安全。Claude Mythos Preview 是一个通用的、未发布的前沿模型，它揭示了一个严峻的事实：AI 模型在代码能力方面已经达到一个水平，能够超越几乎所有人类（除了最顶尖的专家）在发现和利用软件漏洞方面的能力。

Mythos Preview has already found thousands of high-severity vulnerabilities, including some in every major operating system and web browser. Given the rate of AI progress, it will not be long before such capabilities proliferate, potentially beyond actors who are committed to deploying them safely. The fallout—for economies, public safety, and national security—could be severe. Project Glasswing is an urgent attempt to put these capabilities to work for defensive purposes.
Mythos Preview 已经发现了数千个高危漏洞，包括每个主要操作系统和 Web 浏览器中的一些漏洞。鉴于 AI 的进步速度，这种能力很快就会扩散，可能扩散到那些不致力于安全部署的人手中。其后果——对经济、公共安全和国家安全的影响——可能是严重的。Project Glasswing 是将这些能力用于防御目的的紧急尝试。

As part of Project Glasswing, the launch partners listed above will use Mythos Preview as part of their defensive security work; Anthropic will share what we learn so the whole industry can benefit. We have also extended access to a group of over 40 additional organizations that build or maintain critical software infrastructure so they can use the model to scan and secure both first-party and open-source systems. Anthropic is committing up to $100M in usage credits for Mythos Preview across these efforts, as well as $4M in direct donations to open-source security organizations.
作为 Project Glasswing 的一部分，上述启动合作伙伴将使用 Mythos Preview 进行防御性安全工作；Anthropic 将分享我们所学到的内容，以便整个行业都能受益。我们还向构建或维护关键软件基础设施的 40 多个额外组织扩展了访问权限，使他们能够使用该模型扫描和保护第一方和开源系统。Anthropic 承诺为这些工作提供高达 1 亿美元的 Mythos Preview 使用额度，以及向开源安全组织直接捐赠 400 万美元。

Project Glasswing is a starting point. No one organization can solve these cybersecurity problems alone: frontier AI developers, other software companies, security researchers, open-source maintainers, and governments across the world all have essential roles to play. The work of defending the world's cyber infrastructure might take years; frontier AI capabilities are likely to advance substantially over just the next few months. For cyber defenders to come out ahead, we need to act now.
Project Glasswing 是一个起点。没有任何一个组织能够独自解决这些网络安全问题：前沿 AI 开发者、其他软件公司、安全研究人员、开源维护者以及世界各地的政府都发挥着至关重要的作用。保护世界网络基础设施的工作可能需要数年时间；前沿 AI 能力可能在未来几个月内取得实质性进展。为了使网络防御者占据优势，我们现在就需要行动。

## Cybersecurity in the age of AI
## AI 时代的网络安全

The software that all of us rely on every day—responsible for running banking systems, storing medical records, linking up logistics networks, keeping power grids functioning, and much more—has always contained bugs. Many are minor, but some are serious security flaws that, if discovered, could allow cyberattackers to hijack systems, disrupt operations, or steal data.
我们每天依赖的软件——负责运行银行系统、存储医疗记录、连接物流网络、保持电网运行等等——总是包含错误。许多是次要的，但有些是严重的安全缺陷，如果被发现，可能允许网络攻击者劫持系统、中断操作或窃取数据。

We have already seen the serious consequences of cyberattacks for important corporate networks, healthcare systems, energy infrastructure, transport hubs, and the information security of government agencies across the world. On the global stage, state-sponsored attacks from actors like China, Iran, North Korea, and Russia have threatened to compromise the infrastructure that underpins both civilian life and military readiness. Even smaller-scale attacks, such as those where individual hospitals or schools are targeted, can still inflict substantial economic damage, expose sensitive data, and even put lives at risk. The current global financial costs of cybercrime are challenging to estimate, but might be around $500B every year.
我们已经看到网络攻击对企业网络、医疗系统、能源基础设施、交通枢纽以及世界各地政府机构信息安全造成的严重后果。在全球舞台上，来自中国、伊朗、朝鲜和俄罗斯等行为体的国家资助攻击威胁要破坏支撑民用生活和军事准备的基础设施。即使是较小规模的攻击，例如针对个别医院或学校的攻击，仍然可能造成重大的经济损失、暴露敏感数据，甚至危及生命。目前网络犯罪的全球财务成本难以估计，但可能每年约为 5000 亿美元。

Many flaws in software go unnoticed for years because finding and exploiting them has required expertise held by only a few skilled security experts. With the latest frontier AI models, the cost, effort, and level of expertise required to find and exploit software vulnerabilities have all dropped dramatically. Over the past year, AI models have become increasingly effective at reading and reasoning about code—in particular, they show a striking ability to spot vulnerabilities and work out ways to exploit them. Claude Mythos Preview demonstrates a leap in these cyber skills—the vulnerabilities it has spotted have in some cases survived decades of human review and millions of automated security tests, and the exploits it develops are increasingly sophisticated.
软件中的许多缺陷多年来一直未被注意到，因为发现和利用它们需要少数熟练安全专家所掌握的专业知识。有了最新的前沿 AI 模型，发现和利用软件漏洞所需的成本、工作和专业知识水平都急剧下降。过去一年，AI 模型在阅读和推理代码方面变得越来越有效——特别是，它们表现出发现漏洞和找出利用方法的惊人能力。Claude Mythos Preview 展示了这些网络技能的飞跃——它发现的漏洞在一些情况下经受住了数十年的人工审查和数百万次自动化安全测试，而它开发的漏洞利用程序也变得越来越复杂。

Ten years after the first DARPA Cyber Grand Challenge, frontier AI models are now becoming competitive with the best humans at finding and exploiting vulnerabilities. Without the necessary safeguards, these powerful cyber capabilities could be used to exploit the many existing flaws in the world's most important software. This could make cyberattacks of all kinds much more frequent and destructive, and empower adversaries of the United States and its allies. Addressing these issues is therefore an important security priority for democratic states.
在第一次 DARPA 网络大挑战十年后，前沿 AI 模型现在在发现和利用漏洞方面正在与最优秀的人类竞争。如果没有必要的保障措施，这些强大的网络能力可能被用来利用世界上最重要软件中存在的许多缺陷。这可能使各类网络攻击更加频繁和破坏性，并使美国及其盟国的对手获得优势。因此，解决这些问题是民主国家的重要安全优先事项。

Although the risks from AI-augmented cyberattacks are serious, there is reason for optimism: the same capabilities that make AI models dangerous in the wrong hands make them invaluable for finding and fixing flaws in important software—and for producing new software with far fewer security bugs. Project Glasswing is an important step toward giving defenders a durable advantage in the coming AI-driven era of cybersecurity.
尽管 AI 增强的网络攻击风险严重，但有理由保持乐观：同样的能力使 AI 模型在错误的人手中变得危险，也使其在发现和修复重要软件中的缺陷以及生产安全缺陷少得多的新软件方面变得无价。Project Glasswing 是在即将到来的 AI 驱动的网络安全时代为防御者提供持久优势的重要一步。

## Identifying vulnerabilities and exploits with Claude Mythos Preview
## 使用 Claude Mythos Preview 识别漏洞和利用程序

Over the past few weeks, we have used Claude Mythos Preview to identify thousands of zero-day vulnerabilities (that is, flaws that were previously unknown to the software's developers), many of them critical, in every major operating system and every major web browser, along with a range of other important pieces of software.
在过去几周里，我们使用 Claude Mythos Preview 在每个主要操作系统和每个主要 Web 浏览器以及其他各种重要软件中发现了数千个零日漏洞（即软件开发者以前不知道的缺陷），其中许多是严重的。

In a post on our Frontier Red Team blog, we provide technical details for a subset of these vulnerabilities that have already been patched and, in some cases, the ways that Mythos Preview found to exploit them. It was able to identify nearly all of these vulnerabilities—and develop many related exploits—entirely autonomously, without any human steering. The following are three examples:
在我们的 Frontier Red Team 博客上，我们提供了这些漏洞中已修补子集的技术细节，在某些情况下，还包括 Mythos Preview 发现利用它们的方法。它能够完全自主地识别几乎所有这些漏洞——并开发许多相关的漏洞利用程序——而不需要任何人工指导。以下是三个例子：

- Mythos Preview found a 27-year-old vulnerability in OpenBSD—which has a reputation as one of the most security-hardened operating systems in the world and is used to run firewalls and other critical infrastructure. The vulnerability allowed an attacker to remotely crash any machine running the operating system just by connecting to it;
- Mythos Preview 发现了一个 OpenBSD 中存在 27 年的漏洞——OpenBSD 声誉是世界上安全加固程度最高的操作系统之一，用于运行防火墙和其他关键基础设施。该漏洞允许攻击者只需连接到运行该操作系统的机器即可远程使其崩溃；

- It also discovered a 16-year-old vulnerability in FFmpeg—which is used by innumerable pieces of software to encode and decode video—in a line of code that automated testing tools had hit five million times without ever catching the problem;
- 它还发现了一个 FFmpeg 中存在 16 年的漏洞——FFmpeg 被无数软件用于视频编码和解码——这条代码行被自动化测试工具访问了五百万次却从未发现这个问题；

- The model autonomously found and chained together several vulnerabilities in the Linux kernel—the software that runs most of the world's servers—to allow an attacker to escalate from ordinary user access to complete control of the machine.
- 该模型自主发现并将 Linux 内核（运行世界大多数服务器的软件）中的多个漏洞链接在一起，允许攻击者从普通用户访问权限升级到对机器的完全控制。

We have reported the above vulnerabilities to the maintainers of the relevant software, and they have all now been patched. For many other vulnerabilities, we are providing a cryptographic hash of the details today (see the Red Team blog), and we will reveal the specifics after a fix is in place.
我们已向相关软件的维护者报告了上述漏洞，现在它们都已被修补。对于许多其他漏洞，我们今天提供细节的加密哈希（见 Red Team 博客），我们将在修补就位后揭示具体细节。

Evaluation benchmarks such as CyberGym reinforce the substantial difference between Mythos Preview and our next-best model, Claude Opus 4.6:
CyberGym 等评估基准强化了 Mythos Preview 和我们次优模型 Claude Opus 4.6 之间的巨大差异：

Cybersecurity Vulnerability Reproduction
网络安全漏洞复现

Mythos Preview: 83.1%
Opus 4.6: 66.6%

In addition to our own work, many of our partners have already been using Claude Mythos Preview for several weeks. This is what they've found:
除了我们自己的工作，我们的许多合作伙伴已经使用 Claude Mythos Preview 数周。这是他们的发现：

"AI capabilities have crossed a threshold that fundamentally changes the urgency required to protect critical infrastructure from cyber threats, and there is no going back. Our foundational work with these models has shown we can identify and fix security vulnerabilities across hardware and software at a pace and scale previously impossible. That is a profound shift, and a clear signal that the old ways of hardening systems are no longer sufficient.
"AI 能力已经跨越了一个门槛，从根本上改变了保护关键基础设施免受网络威胁所需的紧迫性，而且没有回头路。我们与这些模型的基础工作表明，我们可以以前所未有的速度和规模识别和修复硬件和软件中的安全漏洞。这是一个深刻的转变，也是旧有系统加固方式不再充分的明确信号。

Providers of technology must aggressively adopt new approaches now, and customers need to be ready to deploy. That is why Cisco joined Project Glasswing—this work is too important and too urgent to do alone."
技术提供商现在必须积极采用新方法，客户需要准备好部署。这就是 Cisco 加入 Project Glasswing 的原因——这项工作太重要、太紧迫，不能独自完成。"

"At AWS, we build defenses before threats emerge, from our custom silicon up through the technology stack. Security isn't a phase for us; it's continuous and embedded in everything we do. Our teams analyze over 400 trillion network flows every day for threats, and AI is central to our ability to defend at scale.
"在 AWS，我们在威胁出现之前构建防御，从我们的定制硅片到整个技术栈。对我们来说，安全不是一个阶段；它是持续的，并嵌入我们所做的一切。我们的团队每天分析超过 400 万亿个网络流量以寻找威胁，而 AI 是我们大规模防御能力的关键。

We've been testing Claude Mythos Preview in our own security operations, applying it to critical codebases, where it's already helping us strengthen our code. We're bringing deep security expertise to our partnership with Anthropic and are helping to harden Claude Mythos Preview so even more organizations can advance their most ambitious work with security that sets the standard."
我们一直在自己的安全运营中测试 Claude Mythos Preview，将其应用于关键代码库，它已经在帮助我们加强我们的代码。我们将深厚的安全专业知识带给与 Anthropic 的合作伙伴关系，并帮助加强 Claude Mythos Preview，以便更多组织可以在安全方面推进其最雄心勃勃的工作，树立标准。"

"As we enter a phase where cybersecurity is no longer bound by purely human capacity, the opportunity to use AI responsibly to improve security and reduce risk at scale is unprecedented. Joining Project Glasswing, with access to Claude Mythos Preview, allows us to identify and mitigate risk early and augment our security and development solutions so we can better protect customers and Microsoft.
"当我们进入网络安全不再纯粹受限于人类能力的阶段时，有机会负责任地使用 AI 大规模改善安全性和降低风险是前所未有的。加入 Project Glasswing，访问 Claude Mythos Preview，使我们能够早期识别和减轻风险，并增强我们的安全和开发解决方案，以便更好地保护客户和 Microsoft。

When tested against CTI-REALM, our open-source security benchmark, Claude Mythos Preview showed substantial improvements compared to previous models. We look forward to partnering with Anthropic and the broader industry to improve security outcomes for all."
当针对我们的开源安全基准 CTI-REALM 进行测试时，Claude Mythos Preview 与以前的模型相比显示出实质性改进。我们期待与 Anthropic 和更广泛的行业合作，改善所有人的安全结果。"

Igor Tsyganskiy
Executive Vice President of Cybersecurity and Microsoft Research, Microsoft
网络安全和企业研究执行副总裁，Microsoft

The powerful cyber capabilities of Claude Mythos Preview are a result of its strong agentic coding and reasoning skills. For example, as shown in the evaluation results below, the model has the highest scores of any model yet developed on a variety of software coding tasks.
Claude Mythos Preview 的强大网络能力归功于其强大的 Agent 编码和推理技能。例如，正如下面的评估结果所示，该模型在各种软件编码任务上具有迄今为止开发的任何模型中最高的分数。

[评测数据已从摘要中省略]

We do not plan to make Claude Mythos Preview generally available, but our eventual goal is to enable our users to safely deploy Mythos-class models at scale—for cybersecurity purposes, but also for the myriad other benefits that such highly capable models will bring. To do so, we need to make progress in developing cybersecurity (and other) safeguards that detect and block the model's most dangerous outputs. We plan to launch new safeguards with an upcoming Claude Opus model, allowing us to improve and refine them with a model that does not pose the same level of risk as Mythos Preview.
我们不打算让 Claude Mythos Preview 普遍可用，但我们最终的目标是让我们的用户能够安全地大规模部署 Mythos 级模型——出于网络安全目的，但也出于此类高能力模型将带来的无数其他好处。为此，我们需要在开发网络安全（和其他）保障措施方面取得进展，这些措施可以检测和阻止模型最危险的输出。我们计划在即将推出的 Claude Opus 模型中启动新的保障措施，使我们能够使用不构成 Mythos Preview 那样风险级别的模型来改进和完善它们。

## Plans for Project Glasswing
## Project Glasswing 计划

Today's announcement is the beginning of a longer-term effort. To be successful, it will require broad involvement from across the technology industry and beyond.
今天的宣布是一个长期努力的开端。要取得成功，它需要来自科技行业和更广泛领域的广泛参与。

Project Glasswing partners will receive access to Claude Mythos Preview to find and fix vulnerabilities or weaknesses in their foundational systems—systems that represent a very large portion of the world's shared cyberattack surface. We anticipate this work will focus on tasks like local vulnerability detection, black box testing of binaries, securing endpoints, and penetration testing of systems.
Project Glasswing 合作伙伴将获得访问 Claude Mythos Preview 的权限，以发现和修复其基础系统中的漏洞或弱点——这些系统代表世界上共享网络攻击表面的很大一部分。我们预计这项工作将专注于本地漏洞检测、二进制黑盒测试、端点保护和系统渗透测试等任务。

Anthropic's commitment of $100M in model usage credits to Project Glasswing and additional participants will cover substantial usage throughout this research preview. Afterward, Claude Mythos Preview will be available to participants at $25/$125 per million input/output tokens (participants can access the model on the Claude API, Amazon Bedrock, Google Cloud's Vertex AI, and Microsoft Foundry).
Anthropic 承诺向 Project Glasswing 和其他参与者提供 1 亿美元的模型使用额度，将覆盖此研究预览期间的大量使用。之后，Claude Mythos Preview 将以每百万输入/输出标记 25/125 美元的价格提供给参与者（参与者可以通过 Claude API、Amazon Bedrock、Google Cloud 的 Vertex AI 和 Microsoft Foundry 访问模型）。

In addition to our commitment of model usage credits, we've donated $2.5M to Alpha-Omega and OpenSSF through the Linux Foundation, and $1.5M to the Apache Software Foundation to enable the maintainers of open-source software to respond to this changing landscape (maintainers interested in access can apply through the Claude for Open Source program).
除了模型使用额度的承诺外，我们还通过 Linux Foundation 向 Alpha-Omega 和 OpenSSF 捐赠了 250 万美元，向 Apache Software Foundation 捐赠了 150 万美元，以使开源软件的维护者能够应对这一不断变化的格局（有兴趣访问的维护者可以通过 Claude for Open Source 项目申请）。

We intend for this work to grow in scope and continue for many months, and we'll share as much as we can so that other organizations can apply the lessons to their own security. Partners will, to the extent they're able, share information and best practices with each other; within 90 days, Anthropic will report publicly on what we've learned, as well as the vulnerabilities fixed and improvements made that can be disclosed.
我们打算让这项工作在范围上扩大并持续数月，我们将尽可能多地分享内容，以便其他组织能够将这些教训应用到他们自己的安全工作中。合作伙伴将在能力范围内相互分享信息和最佳实践；在 90 天内，Anthropic 将公开报告我们所学到的内容，以及可以披露的已修复漏洞和所做的改进。

We will also collaborate with leading security organizations to produce a set of practical recommendations for how security practices should evolve in the AI era. This will potentially include:
我们还将与领先的安全组织合作，制定一套关于安全实践如何在 AI 时代演变的实用建议。这可能包括：

- Vulnerability disclosure processes;
- 漏洞披露流程；
- Software update processes;
- 软件更新流程；
- Open-source and supply-chain security;
- 开源和供应链安全；
- Software development lifecycle and secure-by-design practices;
- 软件开发生命周期和安全设计实践；
- Standards for regulated industries;
- 受监管行业的标准；
- Triage scaling and automation; and
- 分诊扩展和自动化；以及
- Patching automation.
- 补丁自动化。

Anthropic has also been in ongoing discussions with US government officials about Claude Mythos Preview and its offensive and defensive cyber capabilities. As we noted above, securing critical infrastructure is a top national security priority for democratic countries—the emergence of these cyber capabilities is another reason why the US and its allies must maintain a decisive lead in AI technology. Governments have an essential role to play in helping maintain that lead, and in both assessing and mitigating the national security risks associated with AI models. We are ready to work with local, state, and federal representatives to assist in these tasks.
Anthropic 还一直在与美国政府官员就 Claude Mythos Preview 及其攻击性和防御性网络能力进行持续讨论。如上所述，保护关键基础设施是民主国家的国家安全优先事项——这些网络能力的出现是美国及其盟友必须在 AI 技术方面保持决定性领先地位的另一个原因。政府在帮助保持这种领先地位以及评估和减轻与 AI 模型相关的国家安全风险方面发挥着重要作用。我们准备与地方、州和联邦代表合作，协助完成这些任务。

We are hopeful that Project Glasswing can seed a larger effort across industry and the public sector, with all parties helping to address the biggest questions around the impact of powerful models on security. We invite other AI industry members to join us in helping to set the standards for the industry. In the medium term, an independent, third-party body—one that can bring together private- and public-sector organizations—might be the ideal home for continued work on these large-scale cybersecurity projects.
我们希望 Project Glasswing 能够为行业和公共部门的更大努力播下种子，所有各方都帮助解决强大模型对安全影响的最大问题。我们邀请其他 AI 行业成员加入我们，帮助为行业制定标准。在中期内，一个独立的第三方机构——一个能够汇集私营和公共部门组织的机构——可能是继续进行这些大规模网络安全项目的理想家园。
