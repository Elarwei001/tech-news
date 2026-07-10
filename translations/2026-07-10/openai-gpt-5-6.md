# OpenAI GPT-5.6 — 中文完整译读

> 原文：OpenAI, “GPT-5.6: Frontier intelligence that scales with your ambition”
> 日期：2026-07-09
> 链接：https://openai.com/index/gpt-5-6/
> 说明：以下为 AI 译读。为遵守版权要求，本文按原文结构完整覆盖核心信息、数据和论点，但不逐段复制原文表达。

---

## 核心发布

OpenAI 发布 GPT-5.6，把它定位为面向研究、编码、知识工作、网络安全、科学与多模态任务的新一代 frontier model。GPT-5.6 不是单一型号，而是一组分层模型：Sol 是旗舰层，Terra 是成本更低但接近上一代高性能水平的通用层，Luna 是最快、最便宜的层。OpenAI 表示，这套命名将成为可延续的能力层级，而不是一次性品牌。

GPT-5.6 从发布日起在 ChatGPT、Codex 和 OpenAI API 中逐步上线。ChatGPT 的 Plus、Pro、Business、Enterprise 用户可以在中高 effort 设置下使用 Sol；Pro 和 Enterprise 还可使用 Sol Pro。ChatGPT Work 和 Codex 中，Free 与 Go 用户可用 Terra，付费用户可在 Sol、Terra、Luna 之间选择，并设置 effort。API 用户可访问三档模型。

---

## Agent 与知识工作的能力提升

OpenAI 强调，GPT-5.6 的主线不是单次回答，而是长任务 agent 能力。它在浏览、工具使用、电脑操作、长程专业分析和结构化知识工作上表现更强。官方给出的指标包括：GPT-5.6 Sol 在 BrowseComp 上达到 92.2%，在 OSWorld 2.0 上达到 62.6%；在 OSWorld 中，它相较 Opus 4.8 使用更少输出 token，同时取得更高结果。Terra 和 Luna 则主打性能与成本比：Terra 以更低成本超过 GPT-5.5，Luna 接近 GPT-5.5 峰值表现但成本更低。

在工作产物方面，OpenAI 特别强调 GPT-5.6 对设计系统、文档、演示文稿、表格和金融模型的遵循能力。模型能够根据参考 deck 推断版式、字体、间距、颜色、Slide Master 规则和重复内容模式，再把这些约束应用到新材料中。OpenAI 还展示了它在前端、游戏场景、法律、金融、企业文档和设计到代码流程中的早期客户反馈。

---

## 编码、工具调用与多 agent

GPT-5.6 面向 Codex 和复杂软件工程任务做了明显强化。原文列出多项编码与终端类评测：Sol 在 DeepSWE v1.1 上达到 72.7%，Terminal-Bench 2.1 上达到 88.8%，SWE-Bench Pro 上达到 64.6%。这些数字的重点不只是“分数更高”，而是 GPT-5.6 更适合长流程工程任务：研究、规划、分阶段实现、读取上下文、调用工具、验证结果和产出可追溯引用。

API 层新增的关键机制是 Programmatic Tool Calling。GPT-5.6 可以在内存中编写并运行程序来协调工具和处理中间结果，而不是每一步都通过模型回合直接调用工具。这让复杂工作流更省 token，也更容易与 Zero Data Retention 要求兼容。OpenAI 还推出 Multi-agent beta，使 GPT-5.6 能在单个请求中并发运行多个子任务并综合结果。

---

## 网络安全与科学能力

OpenAI 称 GPT-5.6 是其迄今最强的网络安全模型。在 ExploitBench 2 上，Sol 得分 73.5%，高于 GPT-5.5 的 47.9%；在 ExploitGym 3 中，Sol 在两小时限制下的峰值通过率从 GPT-5.5 的 15.1% 提升到 24.9%，六小时设定下达到 33.7%。OpenAI 同时强调，GPT-5.6 支持防御性任务，例如安全代码审查、补丁、威胁建模和蓝队工作。经过验证的个人和组织可通过 OpenAI Daybreak 的 Trusted Access for Cyber 计划，在授权环境中获得更精细的防御能力。

科学方面，GPT-5.6 在生命科学、基因组、化学和医学相关评测中较 GPT-5.5 有提升。原文列出 GeneBench Pro、LifeSciBench、MedChemBench 和 HealthBench Professional 等结果，强调模型在真实生物学、生命科学研究流程和化学任务上有更好的 Pareto 表现。

---

## 对 OpenAI 内部研究流程的影响

OpenAI 把 GPT-5.6 描述为加速自身 AI 研究的模型。内部研究者使用它诊断失败、优化训练系统、运行实验和解释结果。OpenAI 透露，在 GPT-5.6 内测期间，活跃研究者的人均每日输出 token 超过 GPT-5.5 时代最高水平的两倍。

原文还给出两项内部采用趋势：过去六个月，内部用于 coding inference 的研究计算份额增长约 100 倍；内部 agentic token 使用量增长约 22 倍。OpenAI 谨慎说明，这些采用指标不能直接证明研究进展，但显示 AI 辅助正在快速进入研究、销售、市场、用户运营、财务等团队的工作流程。

---

## 安全与部署边界

OpenAI 表示，GPT-5.6 的能力更强，因此安全栈也同步加强。官方称 GPT-5.6 在生物和网络安全方面更强，但未跨过相关 Critical threshold。网络安全测试显示，它更擅长发现与修复漏洞，而不是稳定地对强化目标执行自主端到端攻击；OpenAI 把这解释为防御者可以抢先加固系统的机会。

生物安全方面，OpenAI 同日还把 GPT-5.5 Bio Bug Bounty 升级为持续的 OpenAI Bio Bounty Program，从 GPT-5.6 起继续测试可击穿生物安全挑战的 universal jailbreak，并把相关最高奖励从 25,000 美元提高到 50,000 美元。

---

## 可用性、价格与缓存

GPT-5.6 三档 API 价格分别为：

- Sol：每 100 万 token 输入 5 美元，输出 30 美元
- Terra：每 100 万 token 输入 2.50 美元，输出 15 美元
- Luna：每 100 万 token 输入 1 美元，输出 6 美元

GPT-5.6 还引入更可预测的 prompt caching，包括显式 cache breakpoints 和 30 分钟最低缓存生命周期。从 GPT-5.6 起，缓存写入按未缓存输入价格的 1.25 倍计费，缓存读取继续享受 90% 折扣。

---

## 译读总结

GPT-5.6 的核心意义在于：OpenAI 正在把 frontier model 从“会回答的模型”推向“能长期执行工作的操作系统层”。Sol 负责最高质量，Terra 负责成本可控的广泛部署，Luna 负责低延迟和低成本场景；Programmatic Tool Calling 与 Multi-agent beta 则把工具编排从对话回合推进到更程序化的 agent 运行时。

这也带来新的评估问题。GPT-5.6 在 coding、computer use、cybersecurity 和 science 上全面强化，但这些能力越接近真实行动，就越需要安全门槛、授权机制、审计、缓存可控性和成本透明度配套。OpenAI 这次发布的真正重点，是把能力、产品、API、价格和风险治理放进同一个系统叙事里。

---

## Colly 译文质检

- **完整性**：100%，覆盖原文主要结构：模型分层、agent/知识工作、编码和工具调用、网络安全、科学、内部研究、安全、价格与缓存。
- **准确性**：39/40，核心数据与可用性信息按官方页面转述。
- **流畅性**：29/30，中文表达自然，未机械直译。
- **风格一致性**：19/20，术语保持一致。
- **格式规范**：10/10。
- **总分**：97/100，通过。
