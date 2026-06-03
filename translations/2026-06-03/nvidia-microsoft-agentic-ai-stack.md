# NVIDIA 与 Microsoft 合作构建统一的智能体 AI 部署全栈——从 Windows 设备到云端到本地

> 原文：[NVIDIA Partners With Microsoft on Unified Stack for Agentic AI Deployment, From Windows Devices to Cloud to Local](https://blogs.nvidia.com/blog/microsoft-build-windows-local-cloud-devices/)
>
> *(AI 翻译 — Alice Larry)*

智能体 AI 时代已经到来，但要实现其承诺，光靠优秀的模型是不够的。还需要快速硬件、安全运行时、响应迅速的数据层以及为长时间运行推理而优化的模型。NVIDIA 和 Microsoft 正在将这一完整技术栈带给 Windows 设备、Azure 云端和本地部署的开发者。

在 Microsoft Build 大会上，NVIDIA 创始人兼 CEO Jensen Huang 从台北通过直播参与了 Microsoft 董事长兼 CEO Satya Nadella 的主题演讲，讨论了扩展后的合作：[NVIDIA RTX Spark](https://nvidianews.nvidia.com/news/nvidia-microsoft-windows-pcs-agents-rtx-spark) 和 [DGX Station for Windows](https://nvidianews.nvidia.com/news/nvidia-rtx-station-with-windows-puts-a-trillion-parameter-ai-supercomputer-on-every-enterprise-desk)、NVIDIA GPU 加速的 Microsoft Fabric、Microsoft Foundry 上的 NVIDIA 开放模型、[NVIDIA OpenShell](https://build.nvidia.com/openshell) 安全运行时集成至 GitHub Copilot，以及下一代 NVIDIA 驱动的 AI 工厂。

## 为智能体重新定义 Windows：从 RTX Spark 到 DGX Station for Windows

NVIDIA 和 Microsoft 正在为 AI 智能体时代重新构想 Windows PC。借助 RTX Spark 笔记本和小型台式机，以及 DGX Station for Windows 桌边 AI 超级计算机，开发者可以在 Windows 上原生构建、调优和运行智能体。

RTX Spark 是一个新起点，驱动全球首批专为个人智能体设计的 Windows PC，具备 1 PFLOPS AI 算力、最高 128GB 统一内存、全天续航，且不插电时 AI 和图形性能不打折。承载了超过 30 年的 NVIDIA 创新——包括 CUDA、RTX、DLSS 和 TensorRT——来自 Microsoft Surface、华硕、戴尔、惠普、联想和微星的设备将于今秋上市。

DGX Station for Windows 是在 Windows 企业应用和工作流上构建和运行智能体的最强大桌边 AI 超级计算机。搭载 NVIDIA GB300 Grace Blackwell Ultra 桌面超级芯片，配备最高 748GB 一致性内存和 20 PFLOPS FP4 算力，可运行高达 1 万亿参数的前沿模型，支持永远在线的企业智能体。华硕、戴尔、技嘉、惠普、微星和超微的设备预计 Q4 出货。两款产品均运行 NVIDIA OpenShell——一个为自主智能体设计的安全运行时。

## 用 Microsoft Foundry 上的 NVIDIA 开放模型驱动企业级智能体工作流

智能体 AI 运行在一个模型系统之上。借助 NVIDIA、Anthropic 和 OpenAI 的模型——以及 Hermes 专用智能体——现已在 Foundry Agent Service 的托管智能体中可用，企业可以在 Azure 上利用内置身份和治理将智能体系统变为现实。

Anthropic 的 Claude 模型现已在 Azure 的 NVIDIA GB300 Blackwell Ultra 系统上原生运行，客户可在未来数周内获得使用权限。

NVIDIA Nemotron 3 Ultra 是一款全新的开放前沿推理模型，面向编码、研究和企业工作流中的长时运行智能体，本月将通过 Foundry 托管计算提供，同时提供的还有 Nemotron 3.5 ASR（语音识别）和 Nemotron 3.5 内容安全模型。开发者可以将 Nemotron 与前沿模型和本地模型组合，为每个工作流优化成本和质量。

NVIDIA 在 Foundry 上的开放模型组合现已涵盖智能体、物理和科学 AI。[NVIDIA Cosmos 3](https://nvidianews.nvidia.com/news/nvidia-launches-cosmos-3-the-open-frontier-foundation-model-for-physical-ai) 是首个完全开放的物理 AI 全能模型，提供视觉推理、世界仿真和动作生成能力。NVIDIA Earth-2 AI 气象模型可通过 [Microsoft Planetary Computer Pro 和 Foundry](https://aka.ms/MPCP_GA) 为企业提供预测和风险分析。

[NVIDIA Agent Toolkit](https://nvidianews.nvidia.com/news/enterprise-software-leaders-build-ai-agents-with-nvidia) 和 [NVIDIA NemoClaw](https://www.nvidia.com/en-us/ai/nemoclaw/) 蓝图为开发者提供了在 Foundry 上构建生产智能体的开源平台。NVIDIA CUDA-X 库（包括 cuDF、cuOpt、AI-Q 和 NeMo）现在可作为领域专用技能被智能体访问。

## 为 AI 时代加速企业数据仓库

数据驱动智能体 AI，快速访问数据至关重要。

NVIDIA 加速计算现已内置至 Microsoft Fabric 数据仓库。Microsoft 内部基准测试显示，在高并发工作负载下，SQL 执行速度比 CPU 基线快 6 倍，比三家领先的云数据仓库提供商快 7 倍。

企业数据层现在可以跟上持续查询和推理数据的 AI 智能体的节奏——这是 NVIDIA 和 Microsoft 从研究到生产多年深度工程合作的成果。

## 推进物理 AI 和自主系统

物理 AI 是智能体的下一个前沿。

Microsoft 正在将 [NVIDIA 的开源物理 AI 技能和工具](https://nvidianews.nvidia.com/news/nvidia-releases-major-collection-of-open-source-agent-tools-and-skills-for-physical-ai)与 Azure 及其[物理 AI 工具链](https://github.com/microsoft/physical-ai-toolchain)集成。开发者获得统一平台，由 Cosmos 3 的混合 Transformer 架构驱动，用于仿真、训练和部署自主系统——包括机器人、自动驾驶汽车和工业系统——这些系统可以感知、推理、规划并在物理世界中行动。Cosmos 3 在视觉推理、世界生成和动作生成的关键基准中位居开放模型榜首。

## 用 NVIDIA RTX PRO 6000 Blackwell Server Edition 和 Nemotron 模型增强 Azure Local 和 Foundry Local

智能体 AI 正在超越云端。

Microsoft 正在将 Foundry Local on Azure Local 引入 NVIDIA RTX PRO 6000 Blackwell Server Edition 平台。配合 NVIDIA Nemotron 开放模型系列，企业可以在数据所在的位置运行高性能 AI 工作负载——无论是在本地、混合还是主权环境中——而不会牺牲性能或治理能力。

Foundry Local on Azure Local 现支持多节点部署和 vLLM 运行时，为制造业、能源、主权数据中心和其他延迟敏感场景扩展推理能力。

## 通过 NVIDIA OpenShell 将安全智能体开发带入 GitHub Copilot

随着智能体从编码辅助走向自主执行，它们需要真正的能力但不需要真实的凭证。

NVIDIA OpenShell 现已集成至 GitHub Copilot，解决了这个问题：每个智能体在其自己的沙箱容器中隔离运行，每个出站调用在能够访问文件、网络或凭证之前都要经过策略评估。策略以代码形式编写，在仓库中版本化管理，可即时更新。OpenShell 在 Apache 2.0 下开源，模型无关，跨越本地、混合和云环境。

## Fairwater Wisconsin 上线，已通过 NVIDIA Vera Rubin 验证

Microsoft 的 Fairwater Wisconsin AI 工厂[现已上线](https://x.com/i/status/2044767391293509761)，提前交付，运行数十万块 NVIDIA Grace Blackwell 系统作为单一 AI 工厂，并与佐治亚州的类似 AI 工厂连接，为最苛刻的前沿模型提供可扩展的分布式 AI 系统。通过在电力、散热、NVIDIA Spectrum-X 以太网和新的[多路径可靠连接](https://blogs.nvidia.com/blog/spectrum-x-ethernet-mrc/)（MRC）传输协议上的联合工程，Microsoft 的 Fairwater AI 数据中心设计正在优化 token 经济学。

此外，Microsoft 已经验证了 [现已全面量产](https://nvidianews.nvidia.com/news/vera-rubin-full-production-agentic-ai-factory)的 NVIDIA Vera Rubin 平台用于 Azure 数据中心部署。

Vera Rubin 与 Blackwell 无缝兼容，无需改造，每兆瓦提供高达 10 倍的推理吞吐量，将每个智能体 token 的成本降低一个数量级。内置的 NVIDIA 机密计算在智能体大规模推理时保护模型和数据。[NVIDIA Dynamo](https://www.nvidia.com/en-us/ai/dynamo/) 推理框架将这些收益扩展到软件层面，加速 AKS 上的模型冷启动，并通过 [NVIDIA Grove](https://developer.nvidia.com/grove) 带来 Kubernetes 原生的分布式推理编排。
