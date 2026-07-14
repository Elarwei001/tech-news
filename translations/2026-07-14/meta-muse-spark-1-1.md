# Meta Muse Spark 1.1 中文译读

> 原文：Meta AI, [Introducing Muse Spark 1.1](https://ai.meta.com/blog/introducing-muse-spark-meta-model-api/)  
> 日期：2026-07-09  
> 说明：以下为版权合规的中文译读，覆盖原文核心信息、结构和主要事实点，不是逐字全文翻译。

---

## 概览

Meta Superintelligence Labs 发布 Muse Spark 1.1，称其为 Muse Spark 的重要升级版本。它是一个面向 agentic tasks 的多模态推理模型，重点提升工具使用、电脑操作、代码能力和多模态理解。Meta 将这次发布与本周 Muse Image 的推出放在同一条线上，称这些能力让公司更接近“personal superintelligence”的愿景：帮助用户追求目标、创造想象中的内容、加深关系，并对重要事情采取行动。

同时，Meta 开启新的 Meta Model API 公共预览，开发者可以通过该 API 访问 Muse Spark 1.1。模型也已经在 Meta AI app 和 meta.ai 的 Thinking mode 中开放。

## Agent 能力

Muse Spark 1.1 面向需要规划和跨外部应用、服务编排的个人 agent 任务。Meta 称它可以 zero-shot 泛化到新的原生工具、MCP servers 和 custom skills。

相比前代 Muse Spark，1.1 在复杂项目上完成速度明显更快。Meta 的解释是，模型被训练为能够编排多 agent 系统以优化端到端延迟：作为主 agent，它可以收集上下文、制定计划并把执行任务分配给并行 subagents；作为 subagent，它能理解自己的职责、可用工具，并知道何时把问题升级回主 agent。

Muse Spark 1.1 还可以主动管理 100 万 token 上下文窗口。它能记住已执行的动作，从早期工作中检索相关信息，并在压缩上下文时保留后续任务所需的关键步骤。

## 电脑操作

在 computer use 场景中，Muse Spark 1.1 面向跨多个应用、信息持续变化的工作流。它能够在长会话中保留上下文，根据需求变化调整行动，并在较少人工干预下导航陌生界面。

Meta 强调，Muse Spark 1.1 不会机械地一步一步点击界面，而是能判断什么时候用脚本自动化更快，什么时候直接使用界面更简单。模型被训练为根据任务选择写脚本、点击界面或批量生成动作。

原文给出的例子是 dinner party organization：在真实应用中，新上下文可能会改变任务，例如下单过程中出现变化。Muse Spark 1.1 能注意到这些变化，并在不需要用户额外介入的情况下更新订单安排。

## 代码能力

Meta 称 Muse Spark 1.1 在大型复杂代码库的真实任务上显著提升。它可以诊断并修复复杂 bug、实现企业级系统的新功能，并执行大型代码迁移。在创建 Web 应用和端到端问答等用例中，1.1 相比第一代模型有明显进步。

Meta 还表示，模型被训练为能适应不同 harness，并可靠处理复杂多轮动态。它适用于常见 agentic coding setup，包括 planning mode、goal conditioning、subagent delegation 和 context compaction。

在 OpenCode debugging demo 中，Muse Spark 1.1 构建一个聊天 Web app，使用自动截图识别用户可见问题，追踪到相关代码后完成修复，并验证改动。这个例子展示了模型同时使用 coding、多模态理解和 tool calling 的能力。

Meta 内部的开发者和研究人员也在日常使用 Muse Spark 1.1。Meta 称，在其主要内部代码评测 Meta Internal Coding Bench 上，Muse Spark 1.1 相比 Muse Spark 明显提升，并能与领先替代方案竞争。研究人员还用 Muse Spark 1.1 自动化模型开发和评估任务，例如在 OpenCode 中对 DeepSWE 子集进行自评，并基于结果生成分析 dashboard。

## 多模态能力

除了 coding 和 agent 能力，Muse Spark 1.1 还强调感知、多模态推理和工具使用。它能与真实环境交互，生成有 grounding 的输出，并在 visual-to-code artifact generation、超详细图像与视频 caption、以及多模态 agent workflow execution 中表现突出。

Meta 认为，当感知和行动需要结合时，多模态能力尤其有价值。模型可以检查图像和音频，在长工作流中保留关键细节，并在代表用户操作电脑时使用这些信息。

原文给出的例子是 Facebook Marketplace agent：用户用手机拍摄视频后，Muse Spark 1.1 可以从视频中提取有用照片，理解商品信息，并操作浏览器替用户创建 Facebook Marketplace listing。

## 安全

Meta 表示，在部署前对 Muse Spark 1.1 进行了广泛安全评估，并遵循 Advanced AI Scaling Framework。该框架定义了面向高级模型的评估、威胁模型和部署阈值。

在 frontier risk categories 中，Meta 提到化学与生物、网络安全和失控风险。公司称评估结果显示 Muse Spark 1.1 处于安全边界内，并且对 direct jailbreaks、来自不可信数据的 indirect attacks、prompt injection 和 developer-prompt attacks 有较强抵抗力。Meta 还称，1.1 的 adversarial robustness 更好、hallucination rates 更低、sycophancy 更少。

完整安全情况记录在 Muse Spark 1.1 Evaluation Report 中。

## 可用性与早期反馈

开发者首次可以通过新的 Meta Model API 构建 Muse Spark 1.1 应用，该 API 目前处于公共预览阶段。Meta 表示，早期合作伙伴认为 Muse Spark 1.1 是完整的 agentic foundation，把长上下文处理、强代码能力和推理能力结合起来，适合大型 agentic workloads。

原文引用了多位合作伙伴评价：

- Replit CEO Amjad Masad 认为，Muse Spark 把百万 token 上下文、完整多模态支持、内置搜索与引用、强推理、顶级 coding、structured output 和 parallel tool calling 放进了一个 OpenAI-compatible package。
- Cline CEO Saoud Rizwan 强调 Meta 正在认真构建 agentic coding 能力，强工具使用和价格点让真实 coding workloads 可以规模化运行。
- Box AI Products VP Yashodha Bhavnani 表示，在 Box 企业工作评估集中，Muse Spark 展示了与当前领先 frontier models 竞争的企业能力，尤其适合专业服务、公共部门和工业运营等 structured, procedural workflows。
- OpenClaw Foundation 的 Dave Morin 评价 Muse Spark 1.1 适合运行 agents，并称它快速、强大且与 OpenClaw 配合良好。

Meta 在结尾表示，Muse Spark 1.1 体现了其研究动能，并称更强模型仍在训练中，未来会继续分享。

## 译读总结

Muse Spark 1.1 的核心不是单一模型能力，而是 Meta 把个人 AI 推向可执行 agent 平台的信号。它同时覆盖长上下文、多模态、工具调用、computer use、coding、多 agent 编排、API 分发和安全评估。对开发者而言，Meta Model API 是关键入口；对用户而言，Meta 正在把个人 AI 从回答问题推进到跨应用执行任务。
