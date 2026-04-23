# Introducing workspace agents in ChatGPT

> 中文翻译，来源：OpenAI，原文发布于 2026-04-22  
> 原文链接：https://openai.com/index/introducing-workspace-agents-in-chatgpt/

今天，我们在 ChatGPT 中推出 workspace agents。团队现在可以创建共享 agent，让它们处理复杂任务和长时间运行的工作流，同时始终运行在组织设定的权限与控制范围内。

Workspace agents 是 GPTs 的一次演进。它们由 Codex 驱动，可以承担许多人已经在工作中做的任务，从准备报告、编写代码，到回复消息。它们运行在云端，因此即使你不在线，它们也能继续工作。它们还被设计为可在组织内部共享，因此团队可以把 agent 构建一次，然后在 ChatGPT 或 Slack 中共同使用，并随着时间不断改进。

AI 已经帮助人们在个人层面更快完成工作，但组织内部很多最重要的工作流依赖共享上下文、跨团队交接以及协同决策。Workspace agents 正是为这类工作而设计的，它们可以从合适的系统中收集上下文，遵循团队流程，在需要时请求批准，并在多个工具之间持续推进工作。举例来说，我们在 OpenAI 的销售团队会使用一个 agent，从通话记录和账户研究中整理信息，对新线索进行初步筛选，并直接在销售代表的邮箱中起草跟进邮件。这让客户团队能把更少时间花在拼接信息上，把更多时间花在客户身上。

要开始使用，只需点击 ChatGPT 侧边栏中的 Agents，然后描述一个你们团队经常会做的工作流。ChatGPT 会逐步引导你把它变成一个 agent。Workspace agents 目前以 research preview 形式向 ChatGPT Business、Enterprise、Edu 和 Teachers 计划开放。

编者注：GPTs 在团队测试 workspace agents 期间仍会继续可用。很快，我们也会让 GPTs 更容易转换成 workspace agents。

打开声音，可以观看五种你今天就能为团队构建的 agent 的引导式演示。

你可以描述你想完成的工作，或者直接拖入一个文件。ChatGPT 会帮助你把它转化成一个 agent，包括定义步骤、连接正确的工具、添加技能，并持续测试，直到它按你期望的方式工作。

以下是 OpenAI 团队已经构建的一些 agent，你的团队也同样可以构建：

- Software Reviewer：审查员工的软件申请，将其与批准工具和政策比对，给出下一步建议，并在需要时创建 IT 工单。
- Product Feedback Router：监控 Slack、支持渠道和公开论坛，把反馈转成优先级排序后的工单和每周产品摘要。
- Weekly Metrics Reporter：每周五拉取数据、生成图表、撰写总结，并与团队分享报告。
- Lead Outreach Agent：研究进入的销售线索，根据资格标准进行评分，起草个性化跟进邮件，并更新 CRM。
- Third-Party Risk Manager：研究供应商，评估制裁风险、财务状况和声誉风险等信号，并输出结构化报告。

你也可以通过 finance、sales、marketing 等[模板](https://chatgpt.com/agents/studio/new?from-template)快速开始。每个模板都自带技能和推荐工具，因此你可以迅速搭建一个 agent，再按需定制。

Workspace agents 可以跨数十种工具收集上下文并执行操作。

Agent 由云端 Codex 驱动，拥有一个用于文件、代码、工具和 memory 的工作空间。Agent 做的不只是回答提示词，它们还能编写或运行代码、使用已连接应用、记住已经学到的内容，并在多步骤任务中持续工作。

Workspace agents 即使在你离开时也能继续工作。你可以把它们设置成定时运行，或者把它们部署到 Slack 中，让它们在请求出现时自动接手。比如，我们的产品团队构建了一个 agent，能主动在 Slack 频道里回答员工问题。这个 agent 会给出清晰答案、附上相关文档链接，并在发现新问题时提交工单。它帮助团队更快解除阻塞，也避免重要的后续事项被遗漏。

今天，团队可以在 ChatGPT 和 Slack 中与 agents 互动，未来还会扩展到更多界面。Agents 可以进入工作已经发生的对话和工作流，在原本的协作场景里帮助团队推进任务、减少协调成本。

你可以在 ChatGPT 侧边栏的 Agents 标签页中管理共享，并发现团队中已经共享的 workspace agents。

知识往往分散在不同的人和系统中。Workspace agents 给团队提供了一种把这些知识转化成可复用工作流的方法，让流程遵循正确步骤、使用正确工具，并且能够在组织内部共享。

例如，我们的会计团队构建了一个 agent，用于准备月结流程中的关键部分，包括会计分录、资产负债表对账和差异分析。它可以在几分钟内完成这些工作，生成包含底层输入数据和控制总额的工作底稿，供后续审查使用，并遵循内部政策。这个 agent 既可以在 ChatGPT 中供整个团队使用，也可以被添加到 Slack 频道中，让团队围绕其输出进行提问和协作。

由于 agent 拥有 memory，且能在对话中被指导和纠正，它们会随着团队使用而不断变好。随着时间推移，agent 会成为让团队知识保持最新的务实方式：先构建一次，再通过使用不断完善，然后共享或复制到新的工作流中。

你还可以在编辑器菜单中查看 live workspace agents 的分析数据。

当你把工作委派给 agent 时，你仍然掌握控制权。你决定它可以使用哪些工具和数据、可以执行哪些动作、以及在哪些步骤必须获得批准。对于编辑电子表格、发送邮件、添加日历事件等敏感操作，你可以要求 agent 在继续前先请求许可。

在你共享一个 agent 之后，分析功能可以帮助你了解它的使用情况，包括它完成了多少次运行，以及有多少人在使用它。

Workspace agents 内置企业级监控和控制能力，让管理员能在保护敏感数据的同时，为团队提供一种更安全的 AI 加速方式。ChatGPT Enterprise 和 Edu 管理员可以控制哪些已连接工具和动作对哪些用户组开放。管理员还可以管理谁有权使用、构建和分享 agent。内置 safeguard 还帮助 agents 在遇到误导性的外部内容时继续遵循你的指令，其中包括 [prompt injection](https://openai.com/safety/prompt-injections/) 攻击。

[Compliance API](https://help.openai.com/en/articles/9261474-openai-compliance-platform-for-enterprise-customers) 让管理员能够查看每个 agent 的配置、更新与运行记录，从而监控和控制 agent 是如何被构建和使用的。管理员也可以在需要时暂停 agent。

很快，管理员还将能够在管理控制台中查看组织内构建的全部 agent，包括使用模式和已连接的数据源。

Workspace agents 的早期测试者已经开始看到更一致的结果，以及更多时间投入更高价值工作的效果。

“构建 agent 最难的部分不是模型，而是集成、memory 和用户体验。Workspace agents 把这些工作压缩到了一起，因此我们的一位销售顾问无需工程团队，就能端到端地构建、评估并迭代一个 Sales Opportunity agent。它会研究账户、总结 Gong 通话内容，并直接把 deal brief 发到团队的 Slack 房间。过去销售代表每周要花 5 到 6 小时做这件事，现在每笔交易都会在后台自动完成。”

Ankur Bhatt，Rippling AI Engineering

Workspace agents 目前以 research preview 形式向 ChatGPT Business、Enterprise、Edu 和 Teachers 计划开放。对于 Enterprise 和 Edu 计划，管理员可以通过基于角色的控制来启用 agents。

Workspace agents 在 2026 年 5 月 6 日之前免费，之后将开始采用基于 credits 的定价。

未来几周，我们还会继续增加更多能力，帮助团队用更少的人工作业完成更多工作。这包括可以自动启动工作的全新 trigger、更好的仪表盘以理解和提升性能、让 agents 能在企业工具间执行更多动作的能力，以及在 Codex app 中支持 workspace agents。

当知识更容易找到、流程更容易遵循、并且人们能够在工作流中获得帮助时，团队才能做出最好的工作。Workspace agents 是迈向这一未来的早期一步：让 AI 在工作已经发生的工具和对话中与人并肩工作，帮助团队减少协调时间，把更多精力投入到创造、构建和做出推动业务前进的决策上。
