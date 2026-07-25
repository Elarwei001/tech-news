# Claude Opus 5 发布：中文译读

> 原文：Anthropic, [Introducing Claude Opus 5](https://www.anthropic.com/news/claude-opus-5)  
> 日期：2026-07-24  
> 说明：这是为日报准备的版权合规中文译读，覆盖原文主要章节、关键事实、数字和产品含义，不逐字复刻全文。

---

## 核心信息

Anthropic 发布 Claude Opus 5，并表示该模型已经可用。公司把它描述为一个“审慎、主动”的模型：在日常使用场景中接近 Claude Fable 5 的前沿智能，但成本约为后者的一半。

Opus 5 面向 coding、knowledge work、科学研究和长程 agentic workflows。Anthropic 称它在 Frontier-Bench、GDPval-AA、CursorBench、ARC-AGI、Zapier AutomationBench、OSWorld 等评测和任务中表现突出，并在 Claude Max 中成为默认模型，在 Claude Pro 中成为最强模型。

## 性能与成本效率

Anthropic 的核心主张是：Opus 5 在与 Opus 4.8 相同价格下，带来明显更高的性能。用户可以通过 effort setting 在智能水平、速度和 token 成本之间做权衡。

在软件工程任务上，Opus 5 的重点不是只生成代码，而是完成复杂工作。Anthropic 称，在 Frontier-Bench v0.1 中，Opus 5 超过其他模型，并以更低的单任务成本把 Opus 4.8 的表现提高到两倍以上。在 CursorBench 3.2 中，Opus 5 在最高 effort 下接近 Fable 5 峰值表现，但单任务成本约为一半。

在知识工作和问题解决上，Anthropic 提到几组结果：

- 在 ARC-AGI 3 中，Opus 5 的得分约为下一个最佳模型的三倍。
- 在 Zapier AutomationBench 中，Opus 5 在相同单任务成本下的通过率约为下一个最佳模型的 1.5 倍。
- 在 OSWorld 2.0 中，Opus 5 在给定成本下优于其他模型，并以约三分之一多一点的成本超过 Fable 5 的最佳结果。

Anthropic 还表示，Opus 5 在生命科学评测中相对 Opus 4.8 全面提升，尤其是在有机化学结构推断和蛋白质功能相关任务上改进明显。

## 如何与 Opus 5 协作

Anthropic 强调，Opus 5 更擅长验证自身工作，并在失败或不确定时继续迭代。原文举了几类早期访问案例：

- 在一个根据机器零件图重建 3D FreeCAD 模型的任务中，模型没有直接查看图像的方式，于是写了自己的计算机视觉管线，从原始像素中提取几何信息并完成重建。
- 在真实开源包管理器 bug 中，Opus 5 找到根因并修复了社区补丁遗漏的边界条件。
- 在交易公司工程场景中，Opus 5 用单个 session 搭建了新交易所市场数据 feed，并在缺少真实 live feed 的情况下建立测试工具验证解析逻辑。

早期客户反馈集中在几个共同点：困难调试、根因分析、全栈应用构建、长程分析、金融和法务任务、代码审查、可视化输出，以及在执行前自我检查的能力。

## 对齐与安全

Anthropic 表示，Opus 5 是公司目前最 aligned 的模型之一，在自动行为审计中，整体 misaligned behavior 得分低于近期其他模型。公司称它更遵守 Claude's Constitution，更少出现欺骗性行为，也更不容易被诱导误用。

在安全能力边界上，Anthropic 明确说 Opus 5 不推进高风险双用能力前沿。它在生物研究和进攻性网络安全方面仍落后于 Mythos 5。公司还指出，虽然 Opus 5 没有专门用网络任务训练，但通用能力提升使它在漏洞发现上接近 Mythos 5；不过在把漏洞转化为实际 exploit 的能力上，仍明显弱于 Mythos 5。

这一区分很关键：Anthropic 希望让 Opus 5 成为可广泛用于专业工作和科学研究的模型，同时避免把更危险的能力作为默认产品能力释放。

## Opus 5 的护栏

Opus 5 的安全护栏总体类似 Opus 4.8，但在一小部分网络安全任务上更强。Anthropic 表示，Opus 5 的 cyber classifiers 比 Fable 5 限制更少，允许源代码漏洞发现，但会阻断更可能与恶意活动相关的二进制漏洞扫描、渗透测试和 exploit 生成。

当 Claude.ai、Claude Code 或 Claude Cowork 中的请求被 Opus 5 安全分类器拦截时，系统默认回退到 Opus 4.8。API 用户也可以启用自动 fallback。Anthropic 还为 Cyber Verification Program 用户提供限制更少的 Opus 5 版本，以支持经过验证的企业和研究人员开展安全工作。

## 上手与价格

Opus 5 已在 Claude API 中以 `claude-opus-5` 提供。价格为每百万输入 token 5 美元、每百万输出 token 25 美元，与 Opus 4.8 相同。

它也提供 Fast mode，速度约为默认模式的 2.5 倍。Fast mode 在 Claude Platform 上按基础价格的两倍计费，在 Claude Code 中通过 usage credits 使用。

同时，Anthropic 还发布了两个 beta 更新：

- Mid-conversation tool changes：开发者可以在对话中调整 Claude 可用工具，而不使 prompt cache 失效。
- Automatic fallbacks：API 用户可以让被安全分类器拦截的请求自动路由到其他模型，从而减少生产流程中的硬失败。

## 译读判断

Opus 5 的发布重点不是单纯拉高前沿能力，而是把“能长期完成工作的模型”做成更可用、更可控、更可预测的产品。它在性能、价格、安全分类、fallback 和平台工具上一起更新，说明前沿模型公司的竞争正在从 benchmark 转向生产系统。

对开发者和企业而言，最值得关注的不是 Opus 5 是否在某个榜单第一，而是它是否能在真实任务中减少循环次数、减少人工返工、降低总成本，并在风险任务上给出可预期的边界。
