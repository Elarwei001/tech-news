# Google《Introducing Gemini 3.6 Flash, 3.5 Flash-Lite, and 3.5 Flash Cyber》中文译读

> 原文：Google Blog, 2026-07-21  
> 链接：https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-3-6-flash-3-5-flash-lite-3-5-flash-cyber/

## 译者说明

这是对 Google 官方文章的完整译读，覆盖原文所有核心段落、模型定位、关键数字、可用渠道与发布限制。为遵守版权要求，本文采用忠实概述与技术翻译结合的方式，不逐字复刻原文。

## 标题

推出 Gemini 3.6 Flash、3.5 Flash-Lite 和 3.5 Flash Cyber

## 核心摘要

Google 表示，生产级 AI agent 的建设需要更高 token 效率、更低延迟和更可靠的表现。Flash 系列模型被定位为效率与质量之间的平衡点，用于支撑可规模化的 agent 工作流。

此次发布包含三项更新：

- **Gemini 3.6 Flash**：作为新的主力模型，提升编码、知识工作和多模态能力，同时降低输出 token 使用量。
- **Gemini 3.5 Flash-Lite**：3.5 级别中速度最快、成本最低的模型，面向大规模、低延迟任务。
- **Gemini 3.5 Flash Cyber in CodeMender**：面向网络安全的专用模型，与 CodeMender 代码安全 agent 结合，用于发现、验证和修复漏洞。

Google 同时提到，Gemini 3.5 Pro 正在与合作伙伴测试，并计划在准备好后广泛发布；团队也已经开始 Gemini 4 的预训练运行。

## Gemini 3.6 Flash：更高质量、更高效率

Gemini 3.6 Flash 建立在开发者和客户对 3.5 Flash 的反馈之上。Google 强调，它不仅在编码和知识工作上有明显提升，也改善了 token 效率。

按照 Google 引用的 Artificial Analysis Index，3.6 Flash 相比 3.5 Flash 减少 17% 输出 token。在部分任务中，例如 DeepSWE，Google 观察到最高可达 65% 的 token 节省。Google 还表示，3.6 Flash 在多步骤工作流中需要更少推理步骤和更少工具调用。

价格方面，3.6 Flash 的定价为：

- 每 100 万输入 token 1.50 美元
- 每 100 万输出 token 7.50 美元

Google 的结论是，这会降低 agent 任务的整体成本，使 agent 更便宜地构建和运行。

## 3.6 Flash 的 benchmark 表现

Google 列出多个相对 3.5 Flash 的提升例子：

- 在 DeepSWE 中，3.6 Flash 的表现为 49%，高于 3.5 Flash 的 37%。
- 在 MLE Bench 中，3.6 Flash 为 63.9%，高于 3.5 Flash 的 49.7%。
- 在 OSWorld-Verified 中，3.6 Flash 为 83.0%，高于 3.5 Flash 的 78.4%。

Google 还说明，computer use 已经成为 Gemini API 和 Gemini Enterprise 中的内置客户端工具，可支持更多 agent 任务。

## Gemini 3.5 Flash-Lite：为高吞吐 agent 子任务设计

Gemini 3.5 Flash-Lite 被定位为快速、低成本的 3.5-class 模型。Google 称，根据 Artificial Analysis Index，它可以达到 350 output tokens/s，并且在 agent 工作流中显著超过此前 Flash-Lite 世代。

该模型支持不同 thinking levels。开发者可以根据任务需要，在低延迟、低成本执行和更复杂的多步骤子 agent 工作负载之间进行配置。Google 也提到，3.5 Flash-Lite 现在同样具备 computer use 作为内置工具，以便在不同产品表面上支持 agent 任务。

Google 给出的性能例子包括：

- Terminal-Bench 2.1：54%，高于 31%。
- GDM-MRCR v2：72.2%，高于 60.1%。
- GDPval-AA v2：1140，高于 642。
- SWE-Bench Pro：54.2%，高于 3 Flash 的 49.6%。
- OSWorld-Verified：74.0%，高于 3 Flash 的 65.1%。

原文还展示了 3.5 Flash-Lite 的多种应用：从大型电商数据集中抽取并综合商品特征；与 3.6 Flash 作为 master agent 配合生成网页设计概念；批量翻译和总结收据；快速生成并迭代游戏方案。

## Gemini 3.5 Flash Cyber：更高效地发现和修复漏洞

Google 指出，AI 模型已经能够比当前系统修复速度更快地发现安全漏洞。要应对这一趋势，软件安全需要更强、更高效的防护方式。

Gemini 3.5 Flash Cyber 基于 3.5 Flash 构建，并针对网络安全漏洞发现和修复进行微调。Google 称，它以比大型模型更低的 token 成本完成漏洞发现、验证和补丁任务。

在 CodeMender 中，多个 3.5 Flash Cyber agent 会协同工作，最后生成一份综合报告。Google 表示，这种组合在 CyberGym benchmark 上达到具有竞争力的 frontier 水平表现。

由于这类能力具有双重用途，Google 对发布方式采取谨慎策略。3.5 Flash Cyber 将先作为有限访问试点，通过 CodeMender 只向政府和可信伙伴开放。Google 的目标是让一线防守者更早发现和修补关键漏洞，同时降低广泛滥用风险。

## 可用性

Google 表示，Gemini 3.6 Flash 和 3.5 Flash-Lite 从发布当天起可用：

- 开发者可通过 Gemini API、Google AI Studio 和 Android Studio 使用；3.6 Flash 也可在 Google Antigravity 中使用。
- 企业可通过 Gemini Enterprise Agent Platform 使用；3.6 Flash 也可在 Gemini Enterprise app 中使用。
- 普通用户可通过 Gemini app 使用；3.5 Flash-Lite 也会逐步进入 Google Search。

Google 最后表示，希望开发者在构建过程中提供反馈，并期待很快发布 Gemini 3.5 Pro。

## 术语表

- **agentic workflows**：智能体工作流，指模型通过规划、工具调用、反馈和多步骤执行完成任务的流程。
- **computer use**：计算机使用能力，指模型在受控环境中操作界面或工具完成任务。
- **CodeMender**：Google 的代码安全 agent，用于发现和修复软件漏洞。
- **CyberGym**：用于评估 AI agent 处理真实软件漏洞能力的 benchmark。
- **thinking levels**：思考级别，指模型在速度、成本和多步骤推理深度之间的配置档位。

## Alice 自查

- 所有核心章节已覆盖：发布摘要、3.6 Flash、3.5 Flash-Lite、3.5 Flash Cyber、可用性。
- 数字核对：17%、65%、350 output tokens/s、$1.50/1M input tokens、$7.50/1M output tokens、DeepSWE、MLE Bench、OSWorld-Verified、Terminal-Bench、GDM-MRCR、GDPval-AA、SWE-Bench Pro 均已保留。
- 专有名词处理：Gemini、Flash、CodeMender、CyberGym、Artificial Analysis Index、DeepSWE、OSWorld-Verified 等保留原文。
- 风格：译文采用中文技术报道语气，避免逐字搬运。

## Colly 审核

```json
{
  "review_info": {
    "reviewer": "Colly Markus",
    "review_date": "2026-07-21",
    "article_title": "Introducing Gemini 3.6 Flash, 3.5 Flash-Lite, and 3.5 Flash Cyber",
    "translator": "Alice Larry"
  },
  "completeness_check": {
    "is_complete": true,
    "sections": {
      "expected": ["core announcement", "3.6 Flash", "3.5 Flash-Lite", "3.5 Flash Cyber", "availability"],
      "found": ["核心摘要", "Gemini 3.6 Flash", "Gemini 3.5 Flash-Lite", "Gemini 3.5 Flash Cyber", "可用性"],
      "missing": []
    },
    "figures": { "expected": 0, "found": 0 },
    "tables": { "expected": 0, "found": 0 },
    "footnotes": { "expected": 0, "found": 0 }
  },
  "quality_scores": {
    "accuracy": { "score": 38, "max": 40, "issues": [] },
    "fluency": { "score": 28, "max": 30, "issues": [] },
    "style": { "score": 19, "max": 20, "issues": [] },
    "formatting": { "score": 9, "max": 10, "issues": [] }
  },
  "total_score": 94,
  "verdict": "PASS",
  "verdict_reason": "内容完整覆盖原文关键信息，数字和模型定位准确，术语统一，格式规范。",
  "feedback_to_alice": "译读清晰，尤其是对三类模型定位和发布限制的处理准确。",
  "revision_required": []
}
```
