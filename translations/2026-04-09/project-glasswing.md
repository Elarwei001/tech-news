# Project Glasswing：保护世界最关键软件的新计划

> 本文翻译自 Anthropic 官方公告 [Project Glasswing](https://www.anthropic.com/glasswing)，由 AI 翻译并经审校。

---

## 引言

今天我们宣布推出 Project Glasswing¹，这是一项新的计划，汇集了 Amazon Web Services、Anthropic、Apple、Broadcom、Cisco、CrowdStrike、Google、JPMorganChase、Linux Foundation、Microsoft、NVIDIA 和 Palo Alto Networks，共同致力于保护世界上最关键的软件。

我们发起 Project Glasswing 的原因在于，我们在 Anthropic 训练的一款新前沿模型中观察到了某些能力，我们相信这些能力可能重塑网络安全领域。Claude Mythos² Preview 是一款通用的、尚未发布的前沿模型，它揭示了一个严峻的事实：AI 模型在编码能力方面已经达到了一个水平，能够超越除最顶尖人类之外的所有人，在发现和利用软件漏洞方面。

Mythos Preview 已经发现了数千个高危漏洞，包括在所有主要操作系统和 Web 浏览器中的漏洞。鉴于 AI 进步的速度，这些能力在不承诺安全部署的行为者中普及只是时间问题。其后果——对经济、公共安全和国家安全——可能是严重的。Project Glasswing 是一次紧迫的尝试，旨在将这些能力用于防御目的。

作为 Project Glasswing 的一部分，上述创始合作伙伴将把 Mythos Preview 作为其防御安全工作的一部分；Anthropic 将分享我们的所学，使整个行业受益。我们还向 40 多家额外组织扩展了访问权限，这些组织构建或维护关键的软件基础设施，以便它们可以使用该模型扫描和保护自有和开源系统。Anthropic 承诺为这些工作提供高达 1 亿美元的 Mythos Preview 使用额度，以及 400 万美元对开源安全组织的直接捐赠。

Project Glasswing只是一个起点。没有任何一个组织能独自解决这些网络安全问题：前沿 AI 开发者、其他软件公司、安全研究人员、开源维护者和世界各国政府都发挥着不可或缺的作用。保护世界网络基础设施的工作可能需要数年时间；而前沿 AI 能力在短短几个月内就可能大幅进步。为了让网络防御者占据上风，我们必须现在就采取行动。

## AI 时代的网络安全

我们每天依赖的软件——负责运行银行系统、存储医疗记录、连接物流网络、维持电网运行等等——从来都包含 bug。许多是次要的，但一些是严重的安全缺陷，如果被发现，可能允许网络攻击者劫持系统、破坏运营或窃取数据。

我们已经看到网络攻击对[企业网络](https://cloud.google.com/blog/topics/threat-intelligence/oracle-ebusiness-suite-zero-day-exploitation)、[医疗系统](https://www.nao.org.uk/reports/investigation-wannacry-cyber-attack-and-the-nhs/)、[能源基础设施](https://www.cisa.gov/news-events/news/attack-colonial-pipeline-what-weve-learned-what-weve-done-over-past-two-years)、[交通枢纽](https://www.lawfaremedia.org/article/lessons-from-the-european-airports-ransomware-attack)以及世界各地[政府](https://www.reuters.com/world/us/hackers-solarwinds-breach-stole-data-us-sanctions-policy-intelligence-probes-2021-10-07/)[机构](https://www.reuters.com/technology/cybersecurity/us-treasurys-workstations-hacked-cyberattack-by-china-afp-reports-2024-12-30/)的信息安全造成的严重后果。在全球舞台上，来自中国、伊朗、朝鲜和俄罗斯等国家支持的攻击已经威胁到支撑民用生活和军事准备的基础设施。即使是较小规模的攻击——例如针对个别[医院](https://www.sciencedirect.com/science/article/pii/S2950386825000103)或[学校](https://www.vic.gov.au/cyber-incident-impacting-victorian-government-schools)的攻击——仍然可能造成巨大的经济损失、暴露敏感数据，甚至危及生命。目前全球网络犯罪的金融成本难以精确估算，但可能[每年约 5000 亿美元](https://www.governance.ai/research-paper/estimating-global-yearly-cybercrime-damage-costs)。

软件中的许多缺陷多年来未被注意到，因为发现和利用它们需要少数顶尖安全专家才能掌握的专业知识。随着最新前沿 AI 模型的出现，发现和利用软件漏洞所需的成本、精力和专业水平都大幅下降。[在过去一年中](https://www.anthropic.com/research/building-ai-cyber-defenders)，AI 模型在阅读和推理代码方面变得越来越有效——特别是，它们展现出了发现[漏洞](https://red.anthropic.com/2026/firefox/)和找出利用[方法](https://red.anthropic.com/2026/exploit/)的惊人能力。Claude Mythos Preview 展示了这些网络技能的一次飞跃——它发现的漏洞有些已经在人类审查和数百万次自动化安全测试中存活了数十年，它开发的漏洞利用程序越来越复杂。

在首次 DARPA 网络大挑战赛十年之后，前沿 AI 模型现在在发现和利用漏洞方面正在与最优秀的人类竞争。如果没有[必要的保障措施](https://openai.com/index/strengthening-cyber-resilience/)，这些强大的网络能力可能被利用来攻击世界上最重要软件中现存的众多缺陷。这可能使各种网络攻击变得更加频繁和具破坏性，并赋予美国及其盟友的对手更多力量。因此，解决这些问题是民主国家的重要安全优先事项。

尽管 AI 增强的网络攻击风险是严重的，但也有乐观的理由：使 AI 模型在错误的人手中变得危险的同样能力，也使它们在发现和修复重要软件缺陷方面——以及生产安全漏洞更少的新软件方面——具有不可估量的价值。Project Glasswing 是在即将到来的 AI 驱动的网络安全时代中，为防御者带来持久优势的重要一步。

## 使用 Claude Mythos Preview 识别漏洞和利用程序

在过去的几周里，我们使用 Claude Mythos Preview 识别了数千个零日漏洞（即软件开发者此前未知的缺陷），其中许多是关键性的，涵盖所有主要操作系统和所有主要 Web 浏览器，以及其他重要软件。

我们在 [Frontier Red Team 博客](https://red.anthropic.com/2026/mythos-preview)上提供了已修复漏洞子集的技术细节，在某些情况下还包括 Mythos Preview 发现利用这些漏洞的方法。它几乎完全自主地识别了所有这些漏洞——并开发了许多相关利用程序——无需任何人工引导。以下是三个例子：

- Mythos Preview 发现了 OpenBSD 中一个存在 27 年的漏洞——OpenBSD 以世界上最安全加固的操作系统之一著称，被用于运行防火墙和其他关键基础设施。该漏洞允许攻击者仅通过连接到运行该操作系统的任何机器就远程使其崩溃；
- 它还发现了 FFmpeg 中一个存在 16 年的漏洞——FFmpeg 被无数软件用于编码和解码视频——该漏洞位于自动化测试工具已经命中 500 万次却从未发现问题的代码行中；
- 该模型自主发现并串联了 Linux 内核中的多个漏洞——Linux 内核运行着世界上大多数服务器——允许攻击者从普通用户权限升级到对机器的完全控制。

我们已将上述漏洞报告给相关软件的维护者，它们现在都已修复。对于许多其他漏洞，我们今天提供细节的加密哈希值（见 Red Team 博客），我们将在修复到位后公布具体细节。

CyberGym 等评估基准强化了 Mythos Preview 与我们次佳模型 Claude Opus 4.6 之间的显著差距：

| 网络安全漏洞复现 | |
|---|---|
| Mythos Preview | 83.1% |
| Opus 4.6 | 66.6% |

除了我们自己的工作，许多合作伙伴已经使用 Claude Mythos Preview 数周。以下是他们的一些反馈：

> "AI 能力已经越过一个门槛，从根本上改变了对保护关键基础设施免受网络威胁所需的紧迫性，而且不可逆转。我们与这些模型的基础工作表明，我们可以以前所未有的速度和规模识别和修复硬件和软件中的安全漏洞。这是一个深刻的转变，也是一个明确的信号：旧的加固系统方式已经不再足够。技术提供商必须立即积极采用新方法，客户需要准备好部署。这就是 Cisco 加入 Project Glasswing 的原因——这项工作太重要、太紧迫，不能独自完成。"

> "在 AWS，我们在威胁出现之前就构建防御，从我们的定制芯片一直到技术栈的每一层。安全不是一个阶段；它是持续的，嵌入我们所做的一切。我们的团队每天分析超过 400 万亿网络流量以识别威胁，AI 是我们大规模防御能力的核心。我们一直在自己的安全运营中测试 Claude Mythos Preview，将其应用于关键代码库，它已经在帮助我们加固代码。"

> "当针对 CTI-REALM（我们的开源安全基准）进行测试时，Claude Mythos Preview 与以前的模型相比显示出实质性改进。我们期待与 Anthropic 和更广泛的行业合作，改善所有人的安全成果。"
> — Igor Tsyganskiy，Microsoft 网络安全和研究执行副总裁

> "漏洞被发现和被对手利用之间的时间窗口已经坍塌——曾经需要数月的事情，现在在 AI 帮助下几分钟就能完成。Claude Mythos Preview 展示了防御者现在可以大规模实现的能力，而对手不可避免地会寻求利用同样的能力。这不是放慢脚步的理由；而是一起更快行动的理由。"
> — CrowdStrike

---

¹ Project Glasswing（玻璃翼计划）以某些蝴蝶翅膀上透明的"玻璃翅"命名，象征着透明和防御。

² Mythos（神话）是此模型系列的项目名称。

---

*翻译：Alice Larry | 审校：Colly Markus*
