# The next evolution of the Agents SDK

> 原文：<https://openai.com/index/the-next-evolution-of-the-agents-sdk/>
>
> 说明：以下为对 OpenAI 原文的完整中文翻译，保留原始结构与核心术语。

我们正在为 [Agents SDK](https://developers.openai.com/api/docs/guides/agents) 引入新能力，为开发者提供标准化基础设施，既易于上手，又是专门为 OpenAI 模型正确构建的：一个模型原生的 harness，让 agent 能跨文件与工具在计算机上工作，以及用于安全运行这些工作的原生 sandbox execution。

例如，开发者可以给 agent 一个受控工作区、明确指令，以及它检查证据所需的工具。

开发者要构建真正有用的 agent，需要的不只是最好的模型，他们还需要支持 agent 检查文件、运行命令、编写代码，并在多步骤任务中持续工作的系统。

现有系统在团队从原型走向生产时都存在取舍。模型无关框架很灵活，但无法完全发挥前沿模型的能力；模型提供商 SDK 更贴近模型，但往往缺少足够的 harness 可见性；托管 agent API 可以简化部署，但会限制 agent 在哪里运行，以及它们如何访问敏感数据。

下面是一些与我们一起测试新 SDK 的客户反馈。

通过今天的发布，Agents SDK 的 harness 对于处理文档、文件和系统的 agent 来说变得更强大了。它现在具备可配置 memory、面向 sandbox 的 orchestration、类似 Codex 的文件系统工具，以及与前沿 agent 系统中越来越常见的原语的标准化集成。

这些原语包括：通过 [MCP](https://modelcontextprotocol.io) 使用工具，通过 [skills](https://agentskills.io) 实现渐进式信息披露，通过 [AGENTS.md](https://agents.md) 提供自定义指令，使用 [shell](https://developers.openai.com/api/docs/guides/tools-shell) 工具执行代码，使用 [apply patch](https://developers.openai.com/api/docs/guides/tools-apply-patch) 工具编辑文件，等等。随着时间推移，这个 harness 还会继续吸收新的 agentic patterns 和原语，让开发者可以把更少时间花在核心基础设施更新上，把更多时间花在让 agent 真正有用的领域逻辑上。

这个 harness 也帮助开发者释放更多前沿模型的能力，因为它让执行方式与这些模型表现最好的方式保持一致。这使 agent 更贴近模型的自然工作模式，在复杂任务上，尤其是在长时运行或需要协调多种工具与系统时，能够提升可靠性和性能。

此外，我们也意识到每个产品都是独特的，很少能完全套进固定模版。我们设计 Agents SDK 时就考虑到了这种多样性。开发者得到的是一个开箱即用、但又足够灵活的 harness，可以方便地适配到自己的技术栈里，包括工具使用、memory 和 sandbox 环境。

更新后的 Agents SDK 原生支持 sandbox execution，因此 agent 可以在受控的计算机环境中运行，并获得任务所需的文件、工具和依赖。

许多有用的 agent 都需要一个工作区，在其中读取和写入文件、安装依赖、运行代码并安全地使用工具。原生 sandbox 支持为开发者直接提供了这层执行能力，而不必由他们自己拼装。

开发者可以自带 sandbox，也可以使用对 Blaxel、Cloudflare、Daytona、E2B、Modal、Runloop 和 Vercel 的内建支持。

为了让这些环境能够跨提供方移植，SDK 还引入了 Manifest 抽象，用来描述 agent 的工作区。开发者可以挂载本地文件、定义输出目录，并从包括 AWS S3、Google Cloud Storage、Azure Blob Storage 和 Cloudflare R2 在内的存储提供方引入数据。

这让开发者可以用一致的方式来塑造 agent 的环境，从本地原型一路过渡到生产部署。它也让模型拥有一个可预测的工作区：知道输入在哪里、输出写到哪里，以及如何在长时任务中保持工作有条理。

Agent 系统应当在设计时就假设会遭遇 prompt injection 和 exfiltration 尝试。将 harness 和 compute 分离，有助于把凭证隔离在模型生成代码执行不到的环境之外。

这也支持 durable execution。当 agent 状态被外置后，即便 sandbox 容器丢失，也不意味着这次运行会丢失。借助内建的 snapshotting 和 rehydration，Agents SDK 可以在原始环境失败或过期时，在一个新的容器中恢复 agent 状态，并从最近的检查点继续执行。

最后，这也让 agent 更具可扩展性。一次 agent 运行可以使用一个 sandbox，也可以使用多个；只在需要时调用 sandbox；把 subagents 路由到隔离环境中；并跨容器并行工作，以更快完成执行。

这些新的 Agents SDK 能力已经通过 API 面向所有客户正式可用，并采用标准 API 定价，按 token 和工具使用计费。

随着我们继续开发 Agents SDK，我们会持续扩展开发者能构建的能力，让他们用更少的自定义基础设施，就能更容易地把更强的 agent 带入生产，同时保留将 agent 适配进自身环境所需的灵活性和控制力。

新的 harness 和 sandbox 能力将首先在 Python 中推出，对 TypeScript 的支持计划在未来版本提供。我们也在努力把更多 agent 能力，包括 code mode 和 subagents，带到 Python 和 TypeScript。

此外，我们希望随着时间推移，帮助更广泛的 agent 生态系统逐步走向整合，支持更多 sandbox 提供方、更多集成方式，以及更多让开发者将 SDK 接入其现有工具和系统的方法。
