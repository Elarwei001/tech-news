# Project Glasswing 初步更新：中文译介

> 原文：Anthropic, [Project Glasswing: An initial update](https://www.anthropic.com/research/glasswing-initial-update)  
> 日期：2026-05-22  
> 说明：本文为版权合规的完整译介，覆盖原文结构、关键论点和核心数据，但不逐段复刻原文表达。

---

## 概览

Anthropic 在 2026 年 5 月 22 日更新 Project Glasswing，介绍其在使用 Claude Mythos Preview 协助关键软件安全防护方面的初步成果。Project Glasswing 是 Anthropic 与约 50 个合作伙伴开展的协作项目，目标是在能力更强的 AI 模型可能被滥用之前，帮助世界上最关键的软件系统提前加固。

这次更新的核心结论是：高能力 AI 模型已经显著提高了漏洞发现速度，软件安全的主要瓶颈正在从“发现漏洞”转向“验证漏洞、协调披露、修补漏洞和部署补丁”。

---

## 初步成果

Anthropic 表示，自 Project Glasswing 启动以来，团队和合作伙伴使用 Claude Mythos Preview 在关键软件中发现了超过 10,000 个高危或严重漏洞。由于这些漏洞涉及真实软件和真实用户风险，Anthropic 没有公开尚在披露窗口内的具体细节，而是提供示例、汇总数据和披露进度。

截至这次更新，Anthropic 估计已经向维护者披露了 530 个高危或严重漏洞。另有 827 个已确认漏洞也被估计为高危或严重，正在等待尽快披露。

在已经报告的 530 个高危或严重漏洞中，75 个已经被修复，其中 65 个已经获得公开安全公告。Anthropic 认为修复数量偏低有三个原因：

- 许多漏洞仍处于协调披露政策设定的 90 天窗口早期。
- 有些漏洞已经修复但没有公开公告，因此统计可能低估了实际修复数。
- 即便披露速度相对克制，Mythos Preview 产生的漏洞数量仍会给已经超负荷的软件安全生态增加压力。

---

## 披露仪表盘

Anthropic 同时维护一个 Coordinated Vulnerability Disclosure dashboard，用于公开披露进度。截至 2026 年 5 月 22 日，该 dashboard 显示：

- 已披露 1,596 个漏洞。
- 涉及 281 个开源项目。
- 已知 97 个漏洞已经修复。
- 其中 88 个已有 CVE 或 GitHub Security Advisory。

Dashboard 还包含披露 ledger。对于尚在披露窗口内、不能公开细节的发现，Anthropic 会发布 sealed report 的 SHA-3-512 hash，用于证明该发现已经在某个时间点存在，同时避免暴露可被攻击者利用的信息。

---

## 新阶段的网络安全问题

Anthropic 的判断是，具备 Mythos Preview 类似网络安全能力的模型很快会更加普遍。这样的模型会降低发现和利用漏洞的时间与成本，因此也会放大“发现、修补、部署之间存在时间差”所带来的风险。

从长期看，这类模型可以帮助开发者在软件发布前发现更多缺陷，从而提高软件安全性。但在过渡期内，漏洞被快速发现、补丁却相对缓慢地生成和部署，这会形成新的风险窗口。

Anthropic 建议软件开发者缩短补丁周期，尽快发布安全修复，并让用户更容易保持软件更新。对于仍在运行已知有漏洞版本的用户，开发者应在可行范围内提供更强的升级提醒或推动机制。

对于网络防守方，Anthropic 建议缩短补丁测试和部署时间，同时落实基础安全控制，例如默认配置加固、多因素认证、完整日志记录、检测与响应能力等。这些措施不会依赖某一个补丁是否及时发布，因此在漏洞发现速度上升时更加重要。

---

## 面向防守方的 AI 工具

Anthropic 认为，许多公开可用模型已经能发现大量软件漏洞，虽然它们未必能像 Claude Mythos Preview 那样发现最复杂的漏洞或构造 exploit。为了让防守方更好利用这些能力，Anthropic 正在提供一组工具和流程。

首先，Anthropic 已向 Claude Enterprise 客户推出 Claude Security public beta。该工具可以扫描代码库中的漏洞，并生成修复建议。Anthropic 称，在发布后的三周内，Claude Opus 4.7 已被用于修补超过 2,100 个漏洞。

其次，Anthropic 启动 Cyber Verification Program。该项目允许安全专业人士在合法安全场景中使用模型，例如漏洞研究、渗透测试和红队评估，同时避免某些面向防滥用的限制误伤正当工作。

再次，Anthropic 将向符合条件的客户安全团队提供其与合作伙伴使用 Mythos Preview 时构建的工具，包括：

- 用于重复安全工作的 skills。
- 帮助 Claude 理解代码库、启动扫描子任务、triage 发现并撰写报告的 harness。
- threat model builder，用于映射代码库中的潜在攻击目标并排列优先级。

Anthropic 还提到，Project Glasswing 合作伙伴 Cisco 已开源 Foundry Security Spec，帮助其他防守方构建类似评估系统。

---

## 生态支持

Anthropic 已与 Open Source Security Foundation 的 Alpha-Omega 项目建立合作，支持其帮助维护者处理和 triage 漏洞报告。Anthropic 还支持 ExploitBench 和 ExploitGym，这两个 benchmark 用于追踪 frontier AI 模型的 exploit development 能力。

此外，Anthropic 通过 External Researcher Access Program 支持其他高质量定量 benchmark，并通过 Claude for Open Source 支持开源维护者和贡献者。Anthropic 还承诺，未来如果公司采用某个开源包，将扫描该包以帮助降低供应链风险。

---

## 后续计划

Anthropic 认为，类似 Mythos Preview 能力的模型将由多家公司陆续开发出来。但目前包括 Anthropic 在内，还没有任何公司拥有足够强的防护措施，可以确保这类模型公开发布后不会被滥用并造成严重伤害。因此，Anthropic 暂时没有公开发布 Mythos-class 模型。

这也是 Project Glasswing 的背景：如果未来某个类似能力模型在缺乏足够防护的情况下发布，利用有缺陷软件的成本会显著下降。Glasswing 的目标是让关键防守方提前获得不对称优势。

接下来，Anthropic 将与美国及盟友政府等关键伙伴合作，把 Project Glasswing 扩展到更多参与方。Anthropic 也表示，一旦开发出更强防护措施，未来希望能以通用发布形式开放 Mythos-class 模型。

---

## 译介总结

这篇更新最重要的信号是：AI 正在把网络安全从“找不到足够多问题”的阶段推进到“发现速度超过修补速度”的阶段。真正的挑战不只是模型是否强大，而是整个生态是否能建立足够快、足够可信、足够负责任的漏洞处理机制。

Project Glasswing 对开源和企业安全团队都有双重含义。一方面，高能力模型可以成为防守方的放大器，帮助发现、解释和修复更多漏洞。另一方面，如果验证、披露和补丁部署没有同步升级，AI 也会让漏洞积压和攻击窗口变得更危险。

因此，本文的实际建议可以概括为一句话：让 AI 帮你更快发现问题，但更重要的是让组织更快、更可靠地解决问题。
