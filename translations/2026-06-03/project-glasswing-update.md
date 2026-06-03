# Project Glasswing：初步进展更新

> 原文：[Project Glasswing: An initial update](https://www.anthropic.com/research/glasswing-initial-update)
>
> *(AI 翻译 — Alice Larry)*

上个月，我们发布了 [Project Glasswing](https://www.anthropic.com/glasswing)——我们联合约 50 家合作伙伴共同保障全球最关键软件安全的协作计划，确保日益强大的 AI 模型不会反过来被用于攻击这些软件。

此后，我们和合作伙伴使用 Claude Mythos Preview 在全球最重要的系统级软件中发现了超过一万个高危或严重级别的漏洞。过去，软件安全的进展受限于我们多快能发现新漏洞。现在，瓶颈变成了我们多快能验证、披露和修补 AI 发现的大量漏洞。

在这篇文章中，我们讨论 Project Glasswing 前几周中关于网络安全这一关键挑战的发现。我们重点关注 Mythos Preview 性能的早期公开证据、扫描数千个开源软件项目的初步结果，以及这些进展对当今网络防御者的意义。我们还介绍了 Project Glasswing 的下一步计划，以及我们如何看待未来发布 Mythos 级别模型。

## 早期成果

### 讨论 Mythos Preview 发现的方法

软件行业长期以来的惯例是发现新漏洞后 90 天内披露（或者如果补丁在 90 天内就准备好了，则在补丁可用后约 45 天）。这使得终端用户有时间在攻击者利用漏洞之前更新软件。我们自己的[协调漏洞披露政策](https://www.anthropic.com/coordinated-vulnerability-disclosure)也采取了这种方式。

然而，这意味着已披露的漏洞是 AI 模型网络能力加速前沿的一个滞后指标：我们目前还无法完整公开合作伙伴用 Mythos Preview 做出的发现，因为这样做会让终端用户面临风险。因此，我们提供模型性能的说明性示例，以及迄今为止进展的汇总统计数据。一旦 Mythos Preview 发现的漏洞的补丁被广泛部署，我们将提供更多细节。

### 合作伙伴和外部测试者的证据

Project Glasswing 的初始合作伙伴构建和维护的软件是互联网和其他关键基础设施运行的基础。修复其代码中的缺陷可以减少依赖它的许多其他组织的风险，从而降低数十亿终端用户的风险。

一个月后，大多数合作伙伴各自在其软件中发现了数百个严重或高危级别的漏洞。总计发现了超过一万个。几家合作伙伴告诉我们，他们的漏洞发现速度提升了十倍以上。例如，[Cloudflare](https://blog.cloudflare.com/cyber-frontier-models/) 在其关键路径系统中发现了 2,000 个漏洞（其中 400 个为高危或严重级别），误报率被 Cloudflare 团队认为优于人类测试者。

这与外部测试者对 Mythos Preview 性能的体验一致，也与该模型最近的额外评估结果相符：

- 英国 AI 安全研究所[报告](https://www.aisi.gov.uk/blog/how-fast-is-autonomous-ai-cyber-capability-advancing) Mythos Preview 是首个端到端解决其两个赛博靶场（多步骤网络攻击模拟）的模型；
- Mozilla 在 Firefox 150 中[发现并修复](https://blog.mozilla.org/en/privacy-security/ai-security-zero-day-vulnerabilities/)了 [271 个漏洞](https://hacks.mozilla.org/2026/05/behind-the-scenes-hardening-firefox/)——是用 Claude Opus 4.6 在 Firefox 148 中发现的十倍以上；
- XBOW，一个独立安全平台，[报告](https://xbow.com/blog/mythos-offensive-security-xbow-evaluation) Mythos Preview 在其 Web 漏洞利用基准测试中"相比所有现有模型有显著提升"，并在 token 对 token 的基础上提供了"绝对前所未有的精确度"；
- [ExploitBench](http://exploitbench.ai) 和 [ExploitGym](https://arxiv.org/abs/2605.11086) 两个最新发布的学术基准测试显示 Mythos Preview 是最强表现者。

更广泛地说，我们现在看到补丁软件的推出速度大大加快。Palo Alto Networks 的最新版本包含了[五倍](https://www.paloaltonetworks.com/blog/2026/05/defenders-guide-frontier-ai-impact-cybersecurity-may-2026-update/)于平常数量的补丁。Microsoft [已报告](https://www.microsoft.com/en-us/msrc/blog/2026/05/a-note-on-patch-tuesday)其将发布的新补丁数量"将在一段时间内持续增长"。Oracle 在其产品和云中发现和修复漏洞的速度比以前快了[数倍](https://blogs.oracle.com/security/accelerating-vulnerability-detection-and-response-at-oracle)。

Mythos Preview 在其他类型的安全工作中也证明了其价值。例如，在一家 Glasswing 合作银行，Mythos Preview 帮助检测并阻止了一笔 150 万美元的欺诈性电汇——威胁行为者此前入侵了客户的电子邮件账户并进行了欺骗性电话通话。

## 开源软件

在过去几个月中，Anthropic 使用 Mythos Preview 扫描了超过 1,000 个开源项目，这些项目共同构成了互联网和我们自身基础设施的很大一部分。

截至目前，Mythos Preview 在这些项目中估计发现了 6,202 个高危或严重级别的漏洞（总共 23,019 个，包括估计为中低级别的漏洞）。

其中 1,752 个高危或严重级别的漏洞已由六家独立安全研究公司之一（或在少数情况下由我们自己）进行了仔细评估。其中 90.6%（1,587 个）经验证为真阳性，62.4%（1,094 个）被确认为高危或严重级别。这意味着即使 Mythos Preview 不再发现新的漏洞，按照当前的分类后真阳性率，它预计已在开源代码中发现了近 3,900 个高危或严重级别的漏洞——这还不包括它为 Project Glasswing 合作伙伴发现的漏洞。需要明确的是，我们打算继续扫描开源代码一段时间，因此预计这个数字还会上升。

Mythos Preview 检测到的一个开源漏洞示例是在 [wolfSSL](https://www.wolfssl.com/) 中——这是一个以安全性著称的开源加密库，被全球数十亿设备使用。Mythos Preview [构造了一个漏洞利用](https://www.wolfssl.com/how-claude-mythos-preview-helped-harden-wolfssl/)，可以让攻击者伪造证书，从而（例如）托管一个看起来完全合法的银行或电子邮件提供商的虚假网站。该网站对终端用户来说将显得完全合法，尽管实际上由攻击者控制。我们将在未来几周发布这个现已修补的漏洞（分配编号 [CVE-2026-5194](https://nvd.nist.gov/vuln/detail/CVE-2026-5194)）的完整技术分析。

如上所述，修复此类漏洞的瓶颈是人类分诊、报告以及设计和部署补丁的能力。有了 Mythos Preview，发现漏洞变得容易得多。我们创建了一个[开源漏洞仪表板](https://red.anthropic.com/2026/cvd/)，展示了我们扫描的开源漏洞，显示了披露流程的不同步骤，并将跟踪我们的进展。

## 适应网络安全的新阶段

具备与 Mythos Preview 类似网络安全能力的模型很快将更广泛地可用。整个软件行业显然需要更大的努力来管理这些模型将产生的发现量。

目前，从漏洞被发现、补丁被创建，到补丁被终端用户广泛部署，中间通常存在较长延迟。这为攻击者利用关键软件留下了巨大的窗口期。Mythos 级别的模型显著缩小了发现和利用漏洞所需的时间和成本，放大了与这些时间延迟相关的风险。最终，Mythos 级别的模型将使开发者能够在漏洞部署之前捕获缺陷，构建更安全的软件。但这个过渡期——漏洞被快速发现却缓慢修补——带来了新的风险。

软件开发者和用户应该立即采取行动降低这些风险。以下建议并非新概念，许多研究者（包括 Anthropic 的研究者）正在致力于更好、更持久的解决方案。与此同时，做好基础工作很重要：

- 软件开发者应缩短补丁周期，尽快提供安全修复。公开可用的 AI 模型可以在此提供帮助；我们正在构建工具并分享研究来支持这项工作。开发者还应帮助用户保持软件最新，使安装更新尽可能简单；在可行范围内，应对仍在运行已知漏洞软件的用户更加主动。

- 网络防御者应缩短补丁测试和部署时间线。[美国国家标准与技术研究院](https://www.nist.gov/cyberframework)和英国[国家网络安全中心](https://www.ncsc.gov.uk/collection/10-steps/risk-management)等机构提出的关键控制措施现在更加重要，因为它们可以在不依赖任何单个补丁的情况下提高安全性。这些措施包括加固网络默认配置、强制多因素身份验证以及保持全面的日志用于检测和响应。
