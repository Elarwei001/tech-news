# Gemma 4：同等参数量下最强大的开源模型

*2026年4月2日*

*作者：Clement Farabet（Google DeepMind 研究副总裁）、Olivier Lacombe（Google DeepMind 产品经理）*

---

今天，我们发布 [Gemma 4](https://aistudio.google.com/prompts/new_chat?model=gemma-4-31b-it)——我们迄今最智能的开源模型。Gemma 4 专为高级推理和智能体工作流设计，提供了前所未有的"每参数智能水平"。这一突破建立在令人难以置信的社区势头之上：自首代模型发布以来，开发者已下载 Gemma 超过 4 亿次，构建了一个由超过 10 万个变体组成的充满活力的 [Gemmaverse](https://deepmind.google/models/gemma/gemmaverse/)。我们仔细倾听了创新者们推动 AI 边界所需的内容，Gemma 4 就是我们的答案：在 [Apache 2.0 许可证](https://goo.gle/gemma-4-apache-2) 下广泛提供的突破性能力。

*图表：开源模型在 [Arena.ai](http://arena.ai/) 聊天竞技场的性能与参数量对比（截至4/1）*

Gemma 4 基于与 Gemini 3 相同的世界级研究和技术构建，是您能在自己硬件上运行的最强大模型家族。它们与我们的 Gemini 模型相辅相成，为开发者提供业界最强大的开源和专有工具组合。

## 行业领先的能力与移动优先的 AI

我们发布四种多用途尺寸的 Gemma 4：[Effective 2B (E2B)](https://huggingface.co/gg-hf-gg/gemma-4-E2B-it)、[Effective 4B (E4B)](https://huggingface.co/gg-hf-gg/gemma-4-E4B-it)、[26B 混合专家 (MoE)](https://huggingface.co/gg-hf-gg/gemma-4-26B-A4B-it) 和 [31B Dense](https://huggingface.co/gg-hf-gg/gemma-4-31B-it)。整个系列已超越简单对话，能够处理复杂逻辑和智能体工作流。我们的大型模型在其参数量级别实现了最先进的性能，31B 模型目前在行业标准 [Arena AI 文本排行榜](https://arena.ai/leaderboard/text?license=open-source) 上排名开源模型第 3，26B 模型排名第 6。在那里，Gemma 4 超越了比它大 20 倍的模型。对于开发者而言，这种新水平的"每参数智能"意味着用显著更少的硬件开销实现前沿级能力。

在边缘端，我们的 E2B 和 E4B 模型重新定义了设备端效用，优先考虑多模态能力、低延迟处理和无缝生态系统集成，而非原始参数数量。

## 强大、可访问、开源

为了推动下一代开创性研究和产品，我们专门设计了 Gemma 4 模型的尺寸，使其能够在各种硬件上高效运行和微调——从全球数十亿台 Android 设备，到笔记本电脑 GPU，一直到开发者工作站和加速器。

通过使用这些高度优化的模型，您可以微调 Gemma 4 以在特定任务上实现最先进的性能。我们已经看到了这种方法取得的惊人成功；例如，INSAIT 创建了一个开创性的保加利亚语优先语言模型（[BgGPT](https://deepmind.google/models/gemma/gemmaverse/insait/)），我们与耶鲁大学合作的 [Cell2Sentence-Scale](https://blog.google/innovation-and-ai/products/google-gemma-ai-cancer-therapy-discovery/) 发现了癌症治疗的新途径，等等。

以下是 Gemma 4 成为我们迄今最强大开源模型家族的原因：

- **高级推理**：能够进行多步规划和深度逻辑推理，Gemma 4 在需要这些能力的数学和指令遵循基准测试中展示了显著改进。
- **智能体工作流**：原生支持函数调用、结构化 JSON 输出和原生系统指令，使您能够构建可与不同工具和 API 交互并可靠执行工作流的自主智能体。
- **代码生成**：Gemma 4 支持高质量离线代码编写，将您的工作站变成本地优先的 AI 代码助手。
- **视觉和音频**：所有模型原生处理视频和图像，支持可变分辨率，在 OCR 和图表理解等视觉任务上表现出色。此外，E2B 和 E4B 模型具有原生音频输入功能，支持语音识别和理解。
- **更长的上下文**：无缝处理长格式内容。边缘模型具有 128K 上下文窗口，而大型模型提供高达 256K，允许您在单个提示中传递代码仓库或长文档。
- **140+ 语言**：原生训练支持超过 140 种语言，Gemma 4 帮助开发者为全球受众构建包容性、高性能的应用程序。

## 适用于多种硬件的多功能模型

我们发布的 Gemma 4 模型权重针对特定硬件和用例量身定制，确保您在任何需要的地方都能获得前沿级推理能力：

### 26B 和 31B 模型：前沿智能，在个人电脑上离线运行

经过优化，为研究人员和开发者在可访问的硬件上提供最先进的推理能力，我们未量化的 bfloat16 权重可高效地在单张 80GB NVIDIA H100 GPU 上运行。对于本地设置，量化版本可在消费级 GPU 上原生运行，为您的 IDE、代码助手和智能体工作流提供动力。我们的 26B 混合专家 (MoE) 专注于延迟优化，在推理过程中仅激活其总参数的 38 亿，以提供极快的每秒 token 数，而我们的 31B Dense 则最大化原始质量，为微调提供强大的基础。

*表格：这些模型针对大量不同的数据集和指标进行了评估，以涵盖文本生成的不同方面。更多基准测试请参见我们的[模型卡](https://ai.google.dev/gemma/docs/core/model_card_4)。*

### E2B 和 E4B 模型：移动和物联网设备的新智能水平

从零开始为最大计算和内存效率而设计，这些模型在推理过程中激活等效 20 亿和 40 亿参数的占用空间，以节省 RAM 和电池寿命。在与 Google Pixel 团队以及 Qualcomm Technologies 和 MediaTek 等移动硬件领导者的密切合作下，这些多模态模型可在手机、Raspberry Pi、NVIDIA 和 Jetson Orin Nano 等边缘设备上完全离线运行，延迟接近零。Android 开发者现在可以在 [AICore Developer Preview](https://android-developers.googleblog.com/2026/03/AI-Core-Developer-Preview) 中原型化智能体流程，以实现与 Gemini Nano 4 的向前兼容。

## 开源许可证

你们给了我们反馈，我们听取了。构建 AI 的未来需要协作方式，我们相信在没有限制性障碍的情况下赋能开发者生态系统。这就是为什么 Gemma 4 采用商业许可宽松的 [Apache 2.0 许可证](https://goo.gle/gemma-4-apache-2) 发布。

这个开源许可证为完全的开发者灵活性和数字主权提供了基础；授予您对数据、基础设施和模型的完全控制权。它允许您自由构建并在任何环境中安全部署，无论是本地还是云端。

## 建立在信任和安全的基础上

这些模型经历了与我们专有模型相同的严格基础设施安全协议。通过选择 Gemma 4，企业和主权组织获得了一个可信、透明的基础，在满足最高安全性和可靠性标准的同时提供最先进的能力。

## 选择丰富的生态系统

- **几秒钟内开始实验**：即时访问 Gemma 4 并立即开始构建。在 [Google AI Studio](https://aistudio.google.com/prompts/new_chat?model=gemma-4-31b-it)（31B 和 26B MoE）或 Google [AI Edge Gallery](https://developers.googleblog.com/bring-state-of-the-art-agentic-skills-to-the-edge-with-gemma-4/)（E4B 和 E2B）中探索 Gemma 4。对于 [Android 开发](http://android-developers.googleblog.com/2026/03/gemma-4-new-standard-for-local-agentic-intelligence.html)，用它来驱动 [Android Studio](http://android-developers.googleblog.com/2026/04/android-studio-supports-gemma-4-local.html) 中的 Agent Mode，并使用 [ML Kit GenAI Prompt API](https://android-developers.googleblog.com/2026/03/AI-Core-Developer-Preview) 开始在 Android 上构建生产应用。

- **使用您喜爱的工具**：首日支持 [Hugging Face](https://huggingface.co/blog/gemma4)（Transformers、TRL、Transformers.js、Candle）、LiteRT-LM、vLLM、llama.cpp、[MLX](https://huggingface.co/collections/mlx-community/gemma-4)、[Ollama](https://ollama.com/library/gemma4)、[NVIDIA NIM](https://build.nvidia.com/google/gemma-4-31b-it) 和 [NeMo](https://github.com/NVIDIA-NeMo/Automodel/tree/main/docs/guides/vlm/gemma4.md)、[LM Studio](https://lmstudio.ai/models/gemma-4)、[Unsloth](https://unsloth.ai/docs/models/gemma-4)、SGLang、Cactus、[Baseten](https://www.baseten.co/library/publisher/gemma/)、[Docker](https://hub.docker.com/r/ai/gemma4)、MaxText、Tunix、Keras，您可以灵活选择最适合项目的工具。

- **下载模型**：从 [Hugging Face](https://huggingface.co/collections/google/gemma-4)、[Kaggle](https://www.kaggle.com/models/google/gemma-4) 或 [Ollama](https://ollama.com/library/gemma4) 获取模型权重。

- **根据您的特定需求自定义 Gemma 4**：使用您首选的平台训练和调整模型，如 Google Colab、[Vertex AI](https://console.cloud.google.com/vertex-ai/publishers/google/model-garden/gemma4) 甚至您的游戏 GPU。

- **在 Google Cloud 上扩展到生产环境**：虽然本地设备端推理非常适合离线使用，但 Google Cloud 消除了所有计算上限。通过 Vertex AI、[Cloud Run](https://codelabs.developers.google.com/codelabs/cloud-run/cloud-run-gpu-rtx-pro-6000-gemma4-vllm)、[GKE](https://docs.cloud.google.com/kubernetes-engine/docs/tutorials/serve-gemma-gpu-vllm)、Sovereign Cloud、TPU 加速服务以及针对受监管工作负载的最高合规保证，以您的方式部署。在[此处](https://cloud.google.com/blog/products/ai-machine-learning/gemma-4-available-on-google-cloud)了解更多关于在 Google Cloud 上入门的信息。

- **在多个硬件平台上加速您的 AI 开发**：Gemma 4 针对行业领先硬件开箱即用进行了优化。在从 NVIDIA Jetson Orin Nano 到 Blackwell GPU 的 NVIDIA AI 基础设施上体验最佳性能，通过开源 ROCm™ 堆栈与 AMD GPU 集成，或在 Trillium 和 Ironwood TPU 上部署以获得大规模的效率。

- **为影响力而竞争**：加入 Kaggle 上的 [Gemma 4 Good Challenge](https://www.kaggle.com/competitions/gemma-4-good-hackathon)，构建能够在世界上创造有意义的积极变化的产品。

---

*原文链接：https://blog.google/innovation-and-ai/technology/developers-tools/gemma-4/*

*(AI 翻译 — Alice Larry)*
