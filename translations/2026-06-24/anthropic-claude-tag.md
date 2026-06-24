# Anthropic Claude Tag：把 Claude 带进 Slack 频道的团队协作层

> 原文：Anthropic, "Introducing Claude Tag"
> 发布日期：2026-06-23
> 链接：https://www.anthropic.com/news/introducing-claude-tag
> 说明：以下为 AI 译读，覆盖原文事实、结构和关键信息，但不逐字复刻原文。

---

## 核心要点

Anthropic 在 6 月 23 日推出 Claude Tag beta，面向 Claude Enterprise 和 Team 客户。它先从 Slack 开始，让团队可以在频道里直接 @Claude，把任务委派给一个共享的 Claude 身份。

Claude Tag 的重点不只是“在 Slack 里聊天”。Anthropic 把它描述成 Claude Code 演进的下一步：Claude 能在团队频道中积累上下文，连接被授权的工具、数据和代码库，拆解任务、异步执行，并在需要时主动提醒团队。

## 从个人助手到频道里的共享队友

传统 AI 助手通常围绕个人对话或单次任务运行。Claude Tag 的设计对象是团队频道：同一个频道里的成员看到的是同一个 Claude，Claude 可以跟随上下文，延续前面的讨论，并在任务完成后把结果回到 Slack 线程里。

Anthropic 称，内部版本的 Claude Tag 已经成为其团队的主要工作方式之一。公告中提到，Anthropic 产品团队 65% 的代码由内部 Claude Tag 创建；非工程团队也在用它追踪产品指标、处理支持工单、定位复杂 bug 的根因。

这个数字最值得注意的地方，不是单纯的“代码占比”，而是工作流变化：团队开始把 AI 当作可被多人共同委派、观察和接续的执行体，而不是每个人私有的聊天窗口。

## 四个新特性

Claude Tag 相比 Claude Code 或 Claude Cowork，有几个团队场景下更重要的特性。

第一，Claude 是多人共享的。频道中只有一个 Claude 身份，团队成员可以看到它在做什么，也可以从其他人的上下文继续推进任务。

第二，Claude 会随时间学习。它可以基于被授权频道里的信息形成更丰富的工作背景，减少反复解释项目状态、术语和决策历史的成本。Anthropic 强调，Claude 不会从私有频道向外报告信息，访问范围由管理员定义。

第三，Claude 可以主动行动。如果开启 ambient 行为，它能从被授权频道和工具中发现可能需要团队注意的信息，跟进停滞线程，或提醒未完成任务。

第四，Claude 支持异步工作。团队可以把任务交给 Claude，Claude 按阶段执行，并且可以为自己安排后续任务，在数小时或数天内推进项目。

## 权限、隔离与企业控制

Claude Tag 面向企业团队，因此 Anthropic 在公告中花了较多篇幅解释权限设计。管理员需要定义 Claude 可以进入哪些频道、连接哪些工具、访问哪些信息。

这种配置类似为不同场景创建不同 Claude 身份。销售频道里的 Claude 不会把记忆传给工程频道里的 Claude，也不会让工程团队访问销售数据。每个 Claude 的工具、数据和记忆都被限定在管理员定义的范围内。

管理员还可以设置组织级和频道级 token 花费上限，并查看 Claude 做过什么、由谁发起任务的日志。这些控制项说明 Claude Tag 不只是协作体验，也是企业治理问题：当 AI 进入团队沟通层，它必须具备可见性、边界和审计能力。

## Beta 入口与迁移

Claude Tag 目前以 beta 形式提供给 Claude Enterprise 和 Team 客户。管理员需要完成四步：连接 Slack workspace，授权工具，设置组织月度花费上限，并先在私有频道测试。

Claude Tag 将取代现有 Claude in Slack app。Anthropic 表示，管理员可以在 30 天内选择迁移，并为符合条件的 Enterprise 和 Team 组织提供启动额度。

公告还说明，Claude Tag 使用 Opus 4.8，并提供文档和产品页供客户开始配置。

## 编辑观察

Claude Tag 的核心意义，是把 AI agent 从个人生产力工具推向团队协作基础设施。

过去一年，企业 AI 的主线是让模型接入代码、文件、检索和业务系统。Claude Tag 进一步把 agent 放进团队的沟通平面：任务在频道里产生，权限在频道和工具层定义，执行过程在频道中可见，结果回到线程里被团队审查。

这带来明显好处：上下文复用、异步执行、多人协同和更低的委派摩擦。但它也把风险放大了。频道级记忆、主动提醒、跨工具行动和代码库访问，一旦边界设计不清楚，就可能产生数据泄漏、权限混淆、错误执行和责任不明。

因此，Claude Tag 最值得观察的不是 Slack 集成，而是 Anthropic 如何把“频道里的 AI 同事”做成可授权、可隔离、可审计、可控成本的企业系统。AI agent 真正进入组织，拼的不会只是模型能力，还会是组织边界设计。
