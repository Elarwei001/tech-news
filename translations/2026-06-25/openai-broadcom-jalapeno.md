# OpenAI 与 Broadcom 发布 Jalapeño：面向 LLM 推理优化的 Intelligence Processor

> 原文：OpenAI, "OpenAI and Broadcom unveil LLM-optimized inference chip"
> 发布日期：2026-06-24
> 链接：https://openai.com/index/openai-broadcom-jalapeno-inference-chip/
> 说明：以下为 AI 译读，覆盖原文结构、事实和关键论点，但不逐字复刻原文全文。

---

## 核心摘要

OpenAI 和 Broadcom 发布 Jalapeño，这是 OpenAI 的首款 Intelligence Processor。它是一款围绕 LLM 推理需求设计的加速器，也是双方多代计算平台的第一代芯片。OpenAI 将它定位为让先进 AI 更快、更可靠、更普惠的基础设施项目。

Jalapeño 由 OpenAI 按照自身对 LLM inference 的理解从头设计，并与 Broadcom、Celestica 合作推进 silicon implementation、board、rack system integration、高性能网络和可规模化生产。OpenAI 表示，工程样片已经在实验室以目标频率和功耗运行 ML workload，包括 GPT-5.3-Codex-Spark。

OpenAI 还称，早期测试显示 Jalapeño 的性能每瓦显著优于当前先进方案。完整性能技术报告将在未来数月发布。

## 面向 LLM 推理的专用设计

Jalapeño 不是把通用加速器改造成 AI 芯片，而是为现代 LLM 推理重新设计。OpenAI 表示，设计依据来自它每天在 ChatGPT、Codex、API 和未来 agentic products 中运行模型的经验。

这类推理 workload 的核心难点不只是 raw compute，还包括 memory movement、networking、kernel、serving pattern 和用户交互延迟。OpenAI 强调，Jalapeño 的架构目标是减少数据移动，平衡 compute、memory 和 networking 资源，让实际利用率更接近理论峰值。

从产品角度看，推理是 AI 与用户接触的地方。每一次 ChatGPT 回复、Codex 任务、API 调用和未来 agent 步骤，都会受到推理速度、成本和可靠性的影响。Jalapeño 的意义在于把这一层从外部供给，部分变成 OpenAI 自己可以参与设计和优化的底层平台。

## 九个月 tape-out 与 AI 辅助芯片开发

OpenAI 表示，Jalapeño 从初始设计到生产 tape-out 用了 9 个月。公告把这一速度归因于 OpenAI 工程团队、Broadcom silicon implementation 能力，以及使用 OpenAI 模型加速部分设计和优化工作。

这带来一个值得关注的循环：今天提供给用户的 AI 模型，也被用来改进运行未来模型的基础设施。如果 AI 能帮助工程团队更快设计芯片、优化系统，长期看可能降低 compute 成本，并扩大先进 AI 的可用性。

当然，公告中的早期性能仍需后续技术报告和生产部署验证。芯片项目最终要看量产、良率、软件栈、供应链、数据中心集成和真实总体拥有成本。

## 多代平台与合作伙伴

Jalapeño 是 OpenAI 与 Broadcom 多代计算平台的第一步。OpenAI 称，该平台计划在 2026 年底前开始部署，并在之后几年继续扩展。

Broadcom 提供 silicon implementation、networking 和 connectivity 技术，其中包括 Tomahawk networking silicon。Celestica 参与 board、rack 和 system expertise。公告还提到，这一平台会与数据中心伙伴一起推进 gigawatt scale deployment。

这说明 OpenAI 的目标不是做一次性芯片展示，而是建设一条可以持续迭代的 inference infrastructure 路线。

## 为什么 OpenAI 要做推理芯片

OpenAI 在公告中反复强调一个逻辑：推理效率决定先进 AI 的可获得性。更好的 performance per watt 可以带来更快的 ChatGPT 回复、更长程的 Codex 任务、更低成本的 API 产品，以及在高需求时更可靠的访问。

随着 AI 使用量增长，推理会成为长期成本中心。训练可能是前期大额投入，但推理会随着每个用户请求、每个企业 workflow、每个 agent 任务持续发生。对 OpenAI 这样的模型和产品公司来说，优化推理平台就是优化业务底盘。

## 编辑观察

Jalapeño 的行业意义不只是“OpenAI 也有自研芯片”。更准确地说，这是 OpenAI 把自己的模型路线图、产品需求和基础设施路线图绑定到一起。

如果 OpenAI 能在推理层获得更高效率，它就能用同样功率服务更多请求，或用同样成本提供更低延迟、更高可靠性的产品。这对 ChatGPT、Codex、API 和未来 agent 产品都很关键。agent 越长程，推理步骤越多，单位成本越容易成为产品边界。

这也会改变 AI 基础设施竞争。NVIDIA 仍然拥有强大的通用生态，尤其在训练和通用加速上优势明显；但大型 AI 公司会越来越倾向于围绕自身流量做 inference specialization。Google TPU、AWS Trainium/Inferentia、Microsoft Maia 和现在 OpenAI Jalapeño，都反映出同一趋势：AI 巨头不想只购买算力，也想参与定义算力。

真正需要观察的是三件事。第一，Jalapeño 的真实性能和能效能否在公开报告和生产环境中成立。第二，OpenAI 能否把芯片、kernel、serving system 和产品调度做成稳定软件栈。第三，自研推理平台是否能真正降低用户侧成本，而不只是提高 OpenAI 自身毛利。

如果这些问题有正面答案，Jalapeño 会成为 OpenAI 从模型公司走向 AI infrastructure company 的重要标志。

## 译读 QA

- **内容覆盖**：覆盖原文的芯片定位、设计动机、九个月 tape-out、多代平台、合作伙伴、早期性能说法和可用性目标。
- **未逐字翻译原因**：为避免复刻官方全文，本文件采用结构化译读和事实摘要。
- **术语处理**：Jalapeño、Intelligence Processor、LLM、inference、tape-out、kernel、serving system、performance per watt、gigawatt scale deployment 等保留英文或采用行业常用表达。
