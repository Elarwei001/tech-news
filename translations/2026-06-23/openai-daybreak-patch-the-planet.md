# OpenAI Daybreak 与 Patch the Planet：把 AI 安全能力从“发现漏洞”推进到“落地补丁”

> 原文：OpenAI, "Daybreak: Tools for securing every organization in the world" 与 "Patch the Planet: a Daybreak initiative to support open source maintainers"
> 发布日期：2026-06-22
> 链接：https://openai.com/index/daybreak-securing-the-world/
> 链接：https://openai.com/index/patch-the-planet/
> 说明：以下为 AI 译读，完整覆盖两篇原文的事实、结构和关键信息，但不逐字复刻原文。

---

## 核心要点

OpenAI 在 6 月 22 日扩展 Daybreak 网络安全计划，并推出 Patch the Planet。两篇公告的共同主题是：AI 已经能更快发现漏洞，但真正保护用户的不是“发现更多问题”，而是验证问题、评估影响、开发补丁、测试修复、协调披露，并让补丁真正合入项目。

这次发布包括几项内容：

- 更新 Codex Security plugin，用于发现、验证和修复代码库中的安全问题。
- 向可信防御者有限发布完整版本的 GPT-5.5-Cyber。
- 启动 Daybreak Cyber Partner Program，让安全软件和服务提供商把 OpenAI 的防御能力带给更多组织。
- 与 Trail of Bits、HackerOne、Calif、研究人员和维护者合作推出 Patch the Planet，面向关键开源项目提供安全研究和补丁支持。

## Daybreak：网络安全瓶颈正在变化

OpenAI 对当前网络安全形势的判断很明确：过去，最稀缺的是发现严重漏洞的能力；现在，AI 让大规模发现漏洞变得更快，防御方的新瓶颈转向补丁和修复流程。

漏洞报告本身不能保护系统。有效防御需要完成整个闭环：确认漏洞是否真实、判断是否可达、理解风险、编写并测试修复、协调披露、让维护者审查并合入补丁。Daybreak 的定位就是把模型、Codex Security、可信访问、合作伙伴生态和人类安全专家结合起来，帮助防御方把发现转化为真实风险下降。

## Codex Security：从扫描结果到可审查补丁

OpenAI 称，自 3 月以 research preview 形式推出 Codex Security cloud 以来，它已经扫描超过 3,000 万个 commit、覆盖超过 30,000 个代码库；人工审查者已经将超过 70,000 个发现标记为已修复，另有超过 500,000 个发现被自动判定为已修复。

这次更新后的 Codex Security plugin 面向开发者和 AppSec 团队，支持：

- 对整个代码库、代码库子集、特定变更或 commit 运行深度扫描。
- 生成包含严重性、受影响代码位置、验证证据和修复建议的报告。
- 构建或完善 threat model。
- 追踪真实攻击路径，而不是只列出静态扫描告警。
- 生成代码库相关的补丁，供人类审查和合入。
- 与现有漏洞管理系统、SARIF、CodeQL 查询和开发工作流集成。

OpenAI 强调，人类仍然控制哪些发现需要调查、哪些修改要应用、哪些信息可以共享。

## GPT-5.5-Cyber：更强但受控的防御模型

OpenAI 同时发布了更新后的 GPT-5.5-Cyber。这个模型面向经过验证的授权防御任务，比通用 GPT-5.5 更适合高级网络安全工作，同时配套更严格的身份验证、范围控制、日志记录、监控和审核。

OpenAI 披露的评测结果包括：

- CyberGym：GPT-5.5-Cyber 达到 85.6%，高于 GPT-5.5 的 81.8%。
- ExploitGym：GPT-5.5-Cyber 为 39.5%，高于 GPT-5.5 的 25.95%。
- SEC-bench Pro：GPT-5.5-Cyber 为 69.8%，高于 GPT-5.5 的 63.1%。

这些数字说明，OpenAI 正在把“更强的网络安全能力”与“更严格的访问控制”一起发布，而不是把高风险能力直接开放给所有用户。对多数防御者来说，OpenAI 建议从 GPT-5.5 with Trusted Access for Cyber 和 Codex Security 开始；GPT-5.5-Cyber 则留给需要更高级授权测试能力的可信团队。

## Partner Program：通过安全生态分发能力

Daybreak Cyber Partner Program 让安全软件厂商、系统集成商、咨询公司和托管安全服务商把 GPT-5.5 with Trusted Access for Cyber 纳入自己的产品和服务。

OpenAI 的思路是：企业客户未必需要直接拿到最高权限模型；很多时候，更现实的路径是让现有安全工具和服务商把 AI 能力嵌入扫描、验证、事件响应、检测工程、补丁和审计流程中。这样既能扩大覆盖面，也能让模型访问留在受管控的合作伙伴体系里。

公告中列出的合作生态覆盖 Accenture、Akamai、Cisco、Cloudflare、CrowdStrike、IBM、Palo Alto Networks、Proofpoint、SentinelOne、Tenable、Wiz、Zscaler 等安全与企业技术公司。

## Patch the Planet：为关键开源项目补安全短板

Patch the Planet 是 Daybreak 下的开源安全计划，由 OpenAI 与 Trail of Bits 发起，并与 HackerOne、Calif、研究人员和维护者合作。

OpenAI 选择开源项目作为重点，是因为开源软件已经成为公共服务、企业产品、开发工具和关键基础设施的共同底座。一个广泛使用的网络库、加密库或语言基础设施中的漏洞，可能影响大量下游系统。

但许多关键项目由很小的维护团队支撑。OpenAI 引用 Linux Foundation 和 Harvard 的研究称，在其研究的广泛使用项目中，94% 的项目由不到 10 名开发者负责一年中超过 90% 的新增代码。AI 如果只带来更多报告，可能会增加维护者负担；Patch the Planet 的设计目标是先由专家安全工程师去重、验证、修补和测试，再与维护者协作落地。

## 初始参与项目与早期结果

Patch the Planet 的初始参与项目包括 cURL、NATS Server、pyca/cryptography、Sigstore、aiohttp、Go、freenginx、Python 和 python.org。OpenAI 还称，已有超过 30 个开源项目承诺参与后续工作。

在早期冲刺中，Trail of Bits 安全工程师使用 Codex 和 GPT-5.5-Cyber，在 19 个开源项目上开展工作，已经识别出数百个安全问题并合入数十个补丁，还有更多问题处于协调披露阶段。

公告提到的早期成果包括：

- 在不到一天内搭建覆盖多个入口、构建变体、平台和测试种子的 fuzzing 实验室。
- 构建历史 CVE 驱动的变体发现 pipeline，把过往漏洞模式应用到目标代码库，并通过专门的 judging agents 过滤重复和误报。
- 在 FreeBSD 工作中确认 34 个漏洞并产出 7 个本地提权 PoC。
- 在 dnsmasq 中识别与多个后续修复 CVE 对应的脆弱模式。
- 在 HTTP/2 服务器实现中发现 denial-of-service 技术，并指出大量面向互联网的网站可能受影响。
- 在 Chrome V8、Safari WebKit、Firefox WebAssembly 等浏览器相关目标中发现并报告可利用问题，其中 Firefox 相关问题在 Pwn2Own Berlin 前由 Mozilla 修补。

## 政府与关键基础设施合作

OpenAI 还表示，正与各国政府和机构合作提升防御能力，特别是关键基础设施和敏感系统。公告提到，过去一个月 OpenAI 已与澳大利亚、加拿大、法国、德国、日本、韩国以及 ENISA 等欧盟机构建立 Trusted Access for Cyber 伙伴关系，并继续与英国政府合作。

对关键基础设施运营者，OpenAI 的目标是基于其具体系统和保护对象制定更合适的安全边界，让高级 AI 对防御者更有用，同时让恶意行为者更难利用这些能力。

## 编辑观察

这两篇公告的新闻价值不在于“AI 又能找到更多漏洞”，而在于 OpenAI 正在把网络安全能力产品化、流程化和治理化。

AI 安全工具的真正竞争点正在从发现能力转向 remediation throughput：谁能把漏洞验证、风险判断、补丁生成、测试、披露和合入连成可审计流程，谁才可能在企业和开源生态中产生实际安全收益。

但风险同样存在。更强的网络安全模型天然具有两用性。OpenAI 在公告中反复强调 verified defenders、scope controls、monitoring、human oversight 和 coordinated disclosure，说明它也知道问题的敏感性。Daybreak 的成败，最终不只取决于模型分数，而取决于这些治理约束是否能在真实组织里长期有效运行。
