# Streaming Tokens and Tools：NVIDIA Dynamo 的多轮 agentic harness 支持

> 原文：https://developer.nvidia.com/blog/streaming-tokens-and-tools-multi-turn-agentic-harness-support-in-nvidia-dynamo/
>
> 译注：根据 NVIDIA 官方开发者博客可抓取正文翻译整理。保留 harness、tool call、reasoning、Dynamo 等术语。

## 正文翻译

一个 agentic exchange 必须保留结构化互动：assistant 的回合会交错出现 reasoning 和一个或多个工具调用；随后的 user 回合则把相应工具结果返回到模型上下文中。reasoning replay 还依赖模型和具体回合：有些 reasoning 应该保留，有些应该丢弃。

推理引擎需要支持这种更复杂的互动模型，并产出分段正确的 API 结果。工具调用解析和 reasoning 解析必须在外部 harness 消费响应之前完成。高价值 agentic workflow，例如 coding，也依赖响应式 harness 体验：reasoning 片段、工具调用事件和请求元数据需要随着回合展开而流式返回，而不是等最终文本一次性到达。

NVIDIA 这篇文章总结了让真实 agentic client 跑在 NVIDIA Dynamo 之上的经验。Dynamo 需要处理的不是传统单轮 prompt-response，而是多轮、工具驱动、状态持续变化的工作流。agent 可能在一个任务中连续调用多个工具，每个工具结果都会改变下一步上下文。

这对 serving 层提出了新的要求。系统必须正确区分普通文本、reasoning、tool call、tool result 和 metadata；必须在流式输出中保持边界清晰；还必须支持不同模型对 reasoning 保留策略的差异。

文章的核心观点是：agentic inference 不是普通聊天推理的简单放大版。它是一类新的运行时负载，需要推理引擎、工具 harness 和 API 设计共同适配。

## 为什么重要

这解释了为什么 AI agent 的瓶颈正在从模型能力转向运行系统。模型会推理只是第一步；真正难的是让多轮状态、工具调用、审批、错误处理和流式体验稳定协作。

如果 serving 层无法正确处理这些结构，agent 就会在长任务中丢失上下文、错配工具结果，或者让用户无法及时介入。Dynamo 的这类工作，本质上是在为 agent 产品补底层操作系统。

## 译后备注

- harness 可理解为连接模型、工具、用户界面和执行环境的运行框架。
- reasoning 是否保留是模型和产品策略问题，不同系统可能不同。
