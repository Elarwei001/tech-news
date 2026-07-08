# Meta《Introducing Muse Image and Muse Video》中文译读

> 原文：Meta AI, [Introducing Muse Image and Muse Video](https://ai.meta.com/blog/introducing-muse-image-muse-video-msl/)
> 日期：2026-07-07
> 说明：以下为中文译读，完整覆盖原文主要事实、结构、能力点和行业含义；为遵守版权合规要求，不逐字复刻英文原文。

---

## 核心摘要

Meta Superintelligence Labs 发布 Muse Image，并预告 Muse Video。这是 Meta 新超级智能实验室推出的第一组媒体生成模型。Muse Image 面向图像生成和编辑，强调指令遵循、多参考图像组合、精准编辑、Instagram 社交语境，以及 agentic tool use。Muse Video 与 Muse Image 基于同一预训练底座，主打高视觉保真度，并原生支持音频。

Muse Image 已在 Meta AI app、meta.ai、美国 Instagram Stories，以及部分国家的 WhatsApp 上线，并计划随后进入 Facebook。Muse Video 仍处于预览阶段，之后会面向创作者和 Meta AI 推出。

---

## Agentic Image Generation

Meta 将 Muse Image 描述为“agentic image generation”。它不是简单地把提示词直接映射成图像，而是在生成过程中调用工具、反思结果、改进输出，并通过增加测试时计算提升质量。

工具调用包括两类。第一类是代码工具：模型在强化学习过程中学会编写和执行代码，用来生成准确的图表、二维码和其他结构化视觉内容，并把渲染结果作为条件输入，提升图像准确性。Meta 还表示，Muse Spark 与 Muse Image 可以结合代码和媒体生成能力，制作动图、带嵌入图像的网站，以及互动视觉游戏。

第二类是搜索工具：Muse Image 可以通过搜索获得事实信息、实时信息和视觉参考。Meta 称，启用搜索后，模型在涉及当前事件和现实世界事实的知识密集型提示中表现更好。

---

## 自我修正与测试时计算

Muse Image 在生成过程中会自我检查和修正。它可能对当前草稿做局部编辑，也可能重新生成整张图，或者改变策略，调用工具来补足事实信息。Meta 强调，这种行为不是人工写死的规则，而是在强化学习中因为能带来更高奖励而自然出现。

Meta 还把 Muse Image 的质量提升与测试时计算联系起来。模型在推理阶段“思考”越多，就越可能使用更多工具调用和更多自我修正步骤。Meta 称，人类偏好 Elo 分数与推理强度之间呈近似对数线性关系。相比单纯生成多个候选再挑一个，Meta 认为把同样的计算预算用于有意图的推理、工具调用和自我修正，能带来更持续的质量提升。

---

## 图像编辑与多参考组合

Muse Image 支持精准图像编辑，目标是只改变用户要求改变的部分，并在多轮编辑中保持上下文一致。它也支持多参考图像组合，可以从多个输入参考中提取人物、物体、服装、风格和环境等元素，并处理文字与图片交错的复杂提示。

Meta 称，按 2026 年 7 月 5 日的 Arena 人类偏好 Elo 排名，Muse Image 在文本生成图像、单图编辑和多图编辑三个榜单中都位列第二。

---

## Muse Video 预览

Meta 同时预告 Muse Video。它与 Muse Image 共享底层预训练基础，面向文本到视频生成，强调提示遵循、视觉保真度和时间一致性。Meta 承认目前仍有需要继续投入的短板，包括音画同步和高速运动的物理准确性。

Meta 称，按 2026 年 7 月 5 日的 Arena 人类偏好 Elo 排名，Muse Video 在文本到视频榜单中位列第三。Muse Video 将先面向创作者和 Meta AI 推出。

---

## Content Seal 与产品落地

为了帮助用户识别 AI 生成内容，Muse Image 生成的图像会带有 Meta 的 Content Seal 隐形水印。Meta 表示，这个水印在裁剪、压缩、缩放和截图之后仍能保留，并计划未来扩展到视频。

Meta 还预览了检测工具，用户可以用它检查图像是否带有 Content Seal。产品层面，Muse Image 会与 Meta AI、Instagram 和其他社交工具深度结合，支持用户与朋友一起创作、重构 Instagram 照片，并帮助创作者和商家生成动态营销素材。

---

## 译读观察

这篇发布的关键点不是“Meta 又做了一个图像模型”，而是 Meta 把媒体生成也放进了 agent loop：搜索、代码执行、自我修正、多步推理、工具协作和内容溯源同时出现。媒体生成正在从一次性 prompt 输出，转向可验证、可迭代、可接入社交语境的创作系统。

另一个重要信号是分发。Muse Image 一开始就进入 Meta AI、Instagram Stories 和 WhatsApp，说明 Meta 不是只在研究页面展示能力，而是要把生成模型塞进日常社交和创作者工作流。对竞争对手来说，Meta 的优势不只是模型本身，还有它能把模型放到数十亿用户已经在使用的内容入口里。

---

## 译文质量自检

- **完整性**：覆盖发布、agentic generation、工具使用、自我修正、测试时计算、编辑、多参考组合、Muse Video、Content Seal、产品落地和行业意义。
- **准确性**：保留关键日期、上线范围、Arena 排名、能力描述和产品名称。
- **表达**：采用中文科技新闻风格，避免机械逐句翻译。
- **版权处理**：未逐字复刻原文长段落，保留原文链接供读者查阅完整英文内容。
