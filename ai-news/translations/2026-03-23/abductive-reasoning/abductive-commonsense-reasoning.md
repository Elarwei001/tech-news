# 溯因式常识推理

> **元信息**
> - **原文链接**：https://arxiv.org/abs/1908.05739
> - **作者**：Chandra Bhagavatula, Ronan Le Bras, Chaitanya Malaviya, Keisuke Sakaguchi, Ari Holtzman, Hannah Rashkin, Doug Downey, Scott Wen-tau Yih, Yejin Choi
> - **机构**：Allen Institute for AI（Seattle, WA, USA）；Facebook AI（Seattle, WA, USA）；Paul G. Allen School of Computer Science & Engineering, WA, USA
> - **发表会议**：ICLR 2020（第八届国际学习表征会议）
> - **翻译日期**：2026-03-23
> - **译者**：Alice Larry

---

## 摘要

溯因推理（Abductive reasoning）是指推断出最合理解释的推理过程。举例来说，Jenny 下班回家后发现家里一片狼藉，她记得自己出门时留了一扇窗户没关严，于是她推断：最有可能的解释是有小偷破窗而入，把家里弄得乱七八糟。溯因推理长期以来被认为是人们理解和解读自然语言"言外之意"的核心机制（Hobbs et al., 1988），但支持溯因自然语言推理与生成的研究却相对匮乏。

本文首次系统考察了基于语言的溯因推理的可行性。我们引入了一个挑战性数据集 ART，包含超过 2 万条常识性叙事情境和 20 万条解释性假设。基于这一数据集，我们提出了两项新任务：（i）**溯因 NLI（Abductive NLI, αNLI）**——一项多项选择问答任务，要求从候选项中选出更可信的解释；（ii）**溯因 NLG（Abductive NLG, αNLG）**——一项条件生成任务，要求用自然语言为给定观察生成解释性假设。

在 αNLI 任务上，最优模型的准确率仅为 68.9%，远低于人类表现的 91.4%。在 αNLG 任务上，当前最佳语言生成模型的表现更是差强人意——它们缺乏人类轻而易举就能运用的推理能力。我们的分析揭示了深度预训练语言模型在哪些类型的推理上存在缺陷——尽管这些模型在相关但定义更为狭窄的蕴含 NLI 任务上表现出色——为未来研究指出了有趣的方向。

---

## 1 引言

> 大脑是一台溯因机器，它持续不断地尝试用溯因方式证明：环境中观察到的一切构成了一个连贯的情境。
>
> ——Jerry Hobbs，ACL 2013 终身成就奖颁奖典礼¹

溯因推理是对不完整观察给出最合理解释的推理过程（Peirce, 1965a）。图 1 给出了一个例子。给定关于世界的不完整观察：O₁："Jenny 打扫了房间然后去上班，出门时只把窗户开了一条缝。"以及稍后的 O₂："Jenny 回到家，发现家里乱成一团。"我们可以提出不同的潜在解释，并推断哪种最有可能。H₃ 因为无法解释观察 O₂ 而被直接排除；H₁ 和 H₂ 都有一定的合理性，但基于常识，H₁ 是最可信的解释——H₂ 在 O₁ 的情境下显得不太合理（窗缝如此窄，大鸟很难飞进来）。

Peirce 关于溯因推理的一个关键洞察是：溯因是"唯一能引入新想法的逻辑运算"，这与蕴含等其他推理类型形成鲜明对比——蕴含只能推断出前提中已有的信息。

**图 1：溯因推理示例。** 给定观察 O₁ 和 O₂，αNLI 任务要求选出最合理的解释性假设。由于任何情境下的假设空间都极为庞大，ART 数据集作了简化假设，仅要求在两个候选解释之间进行选择。

| | 描述 |
|---|---|
| **O₁** | Jenny 打扫了房间然后去上班，出门时只把窗户开了一条缝。|
| **H₁** | 一个小偷通过撬开窗户闯入房间，翻找 Jenny 的东西，把家里弄乱了。（**最可信**）|
| **H₂** | 那天风很大，一只大鸟飞进了房间，在里面乱飞乱撞，把家里弄乱了。（**较不可信**——窗缝很窄，大鸟很难飞进来）|
| **H₃** | 在公司，她打开了窗户，风把文件吹得到处都是。（**不合理**——未能解释 O₂，此事发生在 Jenny 的工作地点）|
| **O₂** | Jenny 回到家，发现家里乱成一团！|

溯因推理长期被认为是理解叙事（Hobbs et al., 1988）、读懂言外之意（Norvig, 1987; Charniak & Shimony, 1990）、推断日常情境（Peirce, 1965b; Andersen, 1973）以及进行反事实推理（Pearl, 2002; Pearl & Mackenzie, 2018）的核心机制。然而尽管其重要性广受认可，溯因推理在叙事文本中的研究在 NLP 文献中却极少出现——很大程度上是因为以往关于溯因推理的工作主要聚焦于形式逻辑，而形式逻辑过于刚性，难以推广到自然语言的全部复杂性。

本文首次系统考察了基于语言的溯因推理的可行性。从逻辑推理到语言推理的这一转变，深受语言蕴含（Bowman et al., 2015; Williams et al., 2018b）、语言逻辑（Lakoff, 1970; MacCartney & Manning, 2007）以及语言常识推理（Mostafazadeh et al., 2016; Zellers et al., 2018）等大量相关工作的启发。具体而言，我们以自然语言作为表示媒介，并以此探测深度神经模型的语言溯因推理能力。

更具体地，我们在叙事情境中提出了**溯因自然语言推理（αNLI）**和**溯因自然语言生成（αNLG）**两项新型推理任务。² 我们将 αNLI 形式化为多项选择任务，便于自动评估：给定情境，从一对假设候选中选择更合理的解释。我们还引入了新的挑战性数据集 **ART**，包含 2 万条叙事情境及超过 20 万条解释性假设。³⁴ 随后，我们基于最先进的 NLI 和语言模型建立了全面的基线性能。基于 BERT 的最佳 αNLI 基线准确率为 68.9%，与人类表现 91.4% 相比仍有较大差距（§5.2）。基于 GPT2 的最优生成模型在 αNLG 任务上的表现同样远低于人类水平（§5.2）。我们的分析揭示了深度预训练语言模型在哪些类型的推理上存在不足——尽管这些模型在密切相关但本质不同的蕴含 NLI 任务上表现出色——从而为未来研究指出了方向。

---

## 2 任务定义

**溯因自然语言推理** 我们将 αNLI 形式化为多项选择问题，由一对观察作为情境、一对假设候选构成。ART 中的每个实例定义如下：

- **O₁**：时间 t₁ 的观察。
- **O₂**：时间 t₂（t₂ > t₁）的观察。
- **h⁺**：对两个观察 O₁ 和 O₂ 给出合理解释的假设。
- **h⁻**：对观察 O₁ 和 O₂ 不合理（或较不合理）的假设。

给定观察和一对假设，αNLI 任务要求选出最合理的解释（假设）。

**溯因自然语言生成** αNLG 任务要求在给定两个观察 O₁ 和 O₂ 的条件下，生成有效假设 h⁺。形式上，该任务要求最大化 P(h⁺ | O₁, O₂)。

---

## 3 溯因常识推理模型

### 3.1 溯因自然语言推理

**αNLI 的概率框架** αNLI 任务的一个显著特点是，它要求联合考虑所有可用观察及其常识性含义，才能识别正确的假设。形式上，αNLI 任务是选出在给定观察条件下概率最大的假设 h*：

$$h^* = \arg\max_i P(H = h_i | O_1, O_2) \tag{1}$$

利用贝叶斯规则，以 O₁ 为条件改写目标：

$$P(h_i | O_1, O_2) \propto P(O_2 | h_i, O_1) P(h_i | O_1) \tag{2}$$

我们基于方程 2 构建了一组对不同独立性假设作出不同处理的概率模型——从忽略观察的简单基线开始，逐步建立全联合模型。这些模型用贝叶斯网络的形式在图 2 中加以展示。

**图 2：概率框架所描述的图模型示意图。**

| 模型 | 结构描述 |
|---|---|
| a) 仅假设 | 只有节点 H，完全忽略观察。|
| b) 仅第一观察 | O₁ → H，仅依赖第一个观察。|
| c) 仅第二观察 | H → O₂，仅依赖第二个观察。|
| d) 线性链 | O₁ → H → O₂，线性马尔可夫链。|
| e) 全连接 | O₁ 和 O₂ 均直接连接 H，可联合利用两个观察。|

**仅假设（Hypothesis Only）**：最简单的模型，强假设假设与两个观察完全独立，即 (H ⊥ O₁, O₂)，目标是最大化边缘概率 P(H)。

**仅第一（或第二）观察（First/Second Observation Only）**：接下来两个模型的假设更弱：假设仅依赖 O₁ 或 O₂ 之一。

**线性链（Linear Chain）**：该模型利用两个观察，但将各观察对假设的影响视为相互独立，即不跨观察整合信息。形式上，模型假设 ⟨O₁, H, O₂⟩ 构成线性马尔可夫链，其中第二个观察在给定假设的条件下与第一个观察条件独立（即 O₁ ⊥ O₂ | H）。在此假设下，目标化简为：

$$h^* = \arg\max_i P(O_2 | h_i) P(h_i | O_1) \quad \text{其中} \quad (O_1 \perp O_2 | H) \tag{3}$$

**全连接（Fully Connected）**：最复杂的模型，按方程 2 对所有三个随机变量建立联合模型，原则上可跨两个观察整合信息以选出正确假设。

为说明线性链与全连接模型处理两个观察的细微差别，考虑如下例子：O₁："Carl 拼命在超市里找面粉玉米饼，备料做菜用。"O₂："Carl 离开超市时非常沮丧。"两个候选假设分别为不正确的 h₁："收银员态度粗鲁"和正确的 h₂："超市有玉米饼，但没有面粉玉米饼。"线性链模型可能得出错误答案——因为它分开考虑两个观察：单独看 O₁，h₁ 和 h₂ 都是可能的后续事件，但二者先验概率均较低；单独看 O₂（即不知道 O₁ 的情况下，对于一个随机顾客），收银员粗鲁（h₁）比超市没有面粉玉米饼（h₂）更能解释 Carl 的沮丧。将两个观察分开推理后叠加，线性链会选择 h₁ 为更合理的解释。只有像全连接模型那样，将 O₁ 中 Carl 的目标与 O₂ 中他的沮丧联合推理，才能得出 h₂ 是更合理解释的正确答案。

在实验中，我们在最优神经网络模型中编码不同的独立性假设。对于仅假设模型和单观察模型，通过限制模型输入来强制独立性。对于线性链模型，虽然取全部三个变量为输入，但通过限制模型形式来强制条件独立。具体地，我们学习一个判别分类器：

$$P_{\text{Linear Chain}}(h | O_1, O_2) \propto e^{\phi(O_1, h) + \phi'(h, O_2)}$$

其中 φ 和 φ' 是产生标量值的神经网络。

### 3.2 溯因自然语言生成

给定 h⁺ = {w₁ʰ ... wₗʰ}，O₁ = {w₁ᵒ¹ ... wₘᵒ¹} 以及 O₂ = {w₁ᵒ² ... wₙᵒ²} 为 token 序列，αNLG 任务可建模为：

$$P(h^+ | O_1, O_2) = \prod_i P(w_i^h | w_{<i}^h, w_1^{o1} \ldots w_m^{o1}, w_1^{o2} \ldots w_n^{o2})$$

可选地，模型还可以以背景知识 K 为条件。参数化模型可在 ART 的实例上通过最小化负对数似然进行训练：

$$\mathcal{L} = -\sum_{i=1}^{N} \log P(w_i^h | w_{<i}^h, w_1^{o1} \ldots w_m^{o1}, w_1^{o2} \ldots w_n^{o2}, K) \tag{4}$$

---

## 4 ART 数据集：叙事文本中的溯因推理

ART 是第一个用于研究叙事文本溯因推理的大规模基准数据集。它包含约 2 万条叙事情境（观察对 ⟨O₁, O₂⟩）以及超过 20 万条解释性假设。附录中的表 6 对 ART 数据集的语料库级统计数据进行了汇总。⁵ 图 4 展示了 ART（验证集）中的若干示例。基于 BERT 的最优模型对前两个验证集示例的预测均出现了错误。

**图 4：ART（验证集）中的示例。** 基于 BERT 的最优模型对前两个示例的预测均错误。

| 观察 | 更合理的假设 |
|---|---|
| **O₁** 那是一个非常炎热的夏日。<br>**O₂** 他感觉好多了！ | ✅ **H⁺**：他喝了一杯冰镇水。<br>❌ **H⁻**：他决定在烈日下跑步。|
| **O₁** Chad 非常喜欢 Barry Bonds。<br>**O₂** Chad 确保拍了张照片留作纪念。| ✅ **H⁺**：Chad 在赛后等候并与 Barry 见面了。<br>❌ **H⁻**：Chad 通过网络聊天与 Barry Bonds 认识了。|
| **O₁** Leslie 去商场寻找一款与新裙子搭配的包包。<br>**O₂** 她直接拿到收银台结账，高高兴兴地回家了。| ✅ **H⁺**：Leslie 找到了一款完美的包。<br>❌ **H⁻**：Leslie 找了好几个小时后找到了一条漂亮的裙子。|

**收集观察数据** ART 中的观察对 O₁、O₂ 来自 ROCStories 数据集（Mostafazadeh et al., 2016）。ROCStories 是一批经人工精心编写的短故事集，每篇故事包含五个句子，且每篇故事都有清晰的开头和结尾，自然地对应 ART 中的第一个（O₁）和第二个（O₂）观察。

**收集假设候选** 我们通过 Amazon Mechanical Turk（AMT）众包平台，以两项独立任务分别收集合理和不合理的假设候选：⁶

1. **合理假设**：向众包工作者呈现 O₁ 和 O₂ 作为叙事情境，要求他们用自然语言填写"中间发生了什么？"该任务设计促使工作者运用溯因推理，为两个给定观察提出可能的解释。

2. **不合理假设**：在此任务中，我们向工作者呈现观察 O₁、O₂ 以及从上一任务中收集的一个合理假设 h⁺ ∈ H⁺，要求工作者对给定的 h⁺ 进行最小幅度的修改（最多改动 5 个词），为每个合理假设创建不合理的变体 h⁻。

数据集构建中的一大挑战是避免标注偏差（annotation artifacts）——数据中泄露目标标签信息的无意模式——近期多项研究（Gururangan et al., 2018; Poliak et al., 2018; Tsuchiya, 2018）已对多个众包数据集中的此类问题进行了报道。为应对这一挑战，我们为每个 ⟨O₁, O₂⟩ 对收集了多个合理和不合理假设，并应用**对抗过滤（adversarial filtering）**算法，筛选出一组难以区分的挑战性假设对。我们在附录 A.5 中详细描述了该算法。尽管最终数据集以 BERT 作为对抗者，但初步实验中以 GPT 为对抗者时，所有模型（包括所有 BERT 变体）的性能下降幅度相似。两种对抗者的对比结果见表 1。

---

## 5 实验与结果

我们对最先进的预训练语言模型在 ART 数据集上进行微调评估，并为 αNLI 和 αNLG 建立多个基线系统。由于 αNLI 被定义为二分类问题，我们以准确率为主要评估指标。对于 αNLG，我们报告 BLEU（Papineni et al., 2002）、CIDEr（Vedantam et al., 2015）、METEOR（Banerjee & Lavie, 2005）等自动化指标的结果，同时报告人工评估结果。

### 5.1 溯因自然语言推理

尽管在多个其他 NLP 基准数据集上表现出色，最优基线模型（基于 BERT）在 ART 上的准确率仅为 68.9%，而人类表现为 91.4%。人类表现与最优系统之间的巨大差距，为更复杂的溯因推理模型的发展提供了广阔空间。实验表明，在完全连接模型的基础上引入第 3.1 节所述的额外独立性假设，总体上会使系统性能下降（见表 1）。

**表 1：基线和微调语言模型方法在 ART 测试集上的性能。** 测试准确率为五个不同随机种子训练模型的均值（括号内为标准差）。

| 模型 | GPT 对抗过滤准确率 (%) | ART 准确率 (%) |
|---|---|---|
| 随机（二选一） | 50.1 | 50.4 |
| 多数类（来自验证集） | 50.1 | 50.8 |
| Infersent (Conneau et al., 2017) | 50.9 | 50.8 |
| ESIM+ELMo (Chen et al., 2017) | 58.2 | 58.8 |
| **微调预训练语言模型** | | |
| GPT-ft | 52.6 (0.9) | 63.1 (0.5) |
| BERT-ft [仅假设] | 55.9 (0.7) | 59.5 (0.2) |
| BERT-ft [仅 O₁] | 63.9 (0.8) | 63.5 (0.7) |
| BERT-ft [仅 O₂] | 68.1 (0.6) | 66.6 (0.2) |
| BERT-ft [线性链] | 65.3 (1.4) | 68.9 (0.5) |
| BERT-ft [全连接] | 72.0 (0.5) | 68.6 (0.5) |
| **人类表现** | — | **91.4** |

**人类表现** 我们通过 AMT 计算人类表现。每个实例（两个观察和两个假设候选）分配给三名工作者，要求他们选出更合理的假设。⁷ 对所分配的标签取多数票，最终人类准确率为 ART 测试集上的 91.4%。

**基线** 我们加入依赖简单特征的基线，以验证 ART 不因明显的标注偏差而被简单解决。所有简单基线的准确率均接近随机水平，表明数据集中不存在简单的标注偏差。

相关但不同的蕴含 NLI 任务模型（如 SNLI）是 αNLI 的自然基线。我们重新训练了 ESIM+ELMo（Chen et al., 2017; Peters et al., 2018）模型，因为其在蕴含 NLI 上的性能（88.9%）接近当前最优水平（不含预训练语言模型）。该模型仅取得 58.8% 的准确率，表明在 ART 上表现出色需要模型远超语言蕴含的范畴。

**预训练语言模型** BERT（Devlin et al., 2018）和 GPT（Radford, 2018）近期在多项 NLP 基准上取得了最先进成果（Wang et al., 2018）。我们按照前人工作的建议对 BERT-Large 和 GPT 进行微调，并以自然叙事顺序呈现每个实例。BERT-ft（全连接）是表现最好的模型，准确率为 68.9%，而 GPT 为 63.1%。⁸ 我们的对抗过滤方法成功将 BERT 性能从 88% 以上压低了 20 个百分点。

**学习曲线与数据集规模** 图 5 显示，尽管基于 ROCStories 仍有相当大的数据扩展空间，最优模型的性能在约 10,000 个实例后就趋于平稳。此外，最优模型与人类表现之间仍存在约 23% 的巨大差距。

**图 5：BERT 在 ART 验证集上的学习曲线。** 横轴上的每个点对应以五个不同随机种子对 BERT 进行微调的结果。人类表现为 91.4%。

### 5.2 溯因自然语言生成

**生成式语言模型** 如方程 4 所述，我们在两个观察 O₁ 和 O₂ 的 token 上条件化训练 GPT2。两个观察均用专属域标签括起来。ATOMIC（Sap et al., 2019）是一个存储推理性 if-then 知识的知识库，是推理 ART 叙事情境所需背景常识的自然来源。然而，将 ATOMIC 中的知识直接整合进神经模型并不直接——因为 ATOMIC 的节点未经规范化，以短文本短语表示。因此，我们借助 COMeT——一个在 ATOMIC 上训练的 Transformer 模型，能以自然语言生成事件的九种常识推理结论。⁹ 具体地，我们探索了两种将 COMeT 信息整合进 GPT2 的方式：（i）以文本短语形式；（ii）以嵌入向量形式。

图 3 展示了我们如何整合 COMeT 表示。具体而言，在输入 token 经词嵌入层嵌入后，我们将 18 个 COMeT 嵌入（对应每个观察的九种关系，共两个观察）附加到序列中，再传入 Transformer 各层。这使得模型能够在注意 COMeT 嵌入的同时学习每个 token 的表示，从而将背景常识知识有效整合进语言模型。¹⁰

**图 3：整合了 COMeT（Bosselut et al., 2019）常识表示的 αNLG 模型概览。** 每个观察分别输入 COMeT 模型，获得九个嵌入向量，每个向量对应一种常识推理类型。左侧为 COMeT 常识 Transformer（如 COMeT 嵌入），右侧为结合上下文的词表示 Transformer（如词嵌入）。

**讨论** 表 2 报告了 αNLG 任务的结果。在自动化指标方面，我们报告了 BLEU-4（Papineni et al., 2002）、METEOR（Banerjee & Lavie, 2005）、ROUGE（Lin, 2004）、CIDEr（Vedantam et al., 2015）以及 BERT-Score（Zhang et al., 2019，使用 bert-base-uncased 模型）。我们通过在 AMT 上众包的方式建立人类表现基准：向工作者展示一对观察和一个生成的假设，请他们判断该假设是否解释了给定观察。最后一列报告人工评估得分；最后一行报告保留的人工撰写假设的得分，作为模型性能的上界。人工撰写的假设在 96% 的实例中被认定为正确，而我们最优的生成模型即便引入了背景常识知识，也仅能达到 45%——表明 αNLG 生成任务对当前最先进的文本生成器而言尤为困难。

**表 2：生成模型在 ART 测试集上的性能。** 除 GPT2-Fixed 外，所有模型均在 ART 上进行了微调。

| 模型 | BLEU | METEOR | ROUGE | CIDEr | BERT-Score | 人工评估 |
|---|---|---|---|---|---|---|
| GPT2-Fixed | 0.0 | 9.29 | 9.99 | 3.34 | 36.69 | — |
| O₁-O₂-Only | 2.23 | 16.71 | 22.83 | 33.54 | 48.74 | 42.26 |
| COMeT-Txt+GPT2 | 2.29 | 16.73 | 22.51 | 31.99 | 48.46 | 38.28 |
| COMeT-Emb+GPT2 | 3.03 | 17.66 | 22.93 | 32.00 | 48.52 | 44.56 |
| 人工撰写假设 | 8.25 | 26.71 | 30.40 | 53.56 | 53.30 | 96.03 |

**GPT 对抗者** 表 1 还包含了以 GPT 为对抗者的实验结果。值得注意的是，在这种情况下，对抗过滤将 GPT 性能压低到 53% 以下；而最优 BERT 模型（编码全连接贝叶斯网络）比编码线性链假设的 BERT 模型表现明显更好——分别为 72% 和 65%。因此，我们在 ART 中使用 BERT 全连接模型作为对抗者。当 BERT 作为对抗者时，线性链与全连接 BERT 模型之间的差距缩小了——尽管全连接模型更强——这表明对抗过滤对作为对抗者的模型产生了不成比例的影响。但该数据集对未作为对抗者的其他模型也变得更难了——例如，在任何过滤之前，BERT 得分 88%，OpenGPT 得分 80%，均远高于表 1 中以对方模型为过滤器时各自的得分。这一结果虽非保证，但合理地表明 ART 对未来发布的新模型仍将具有挑战性。

---

## 6 分析

### 6.1 αNLI 分析

**常识推理类别** 我们研究了当前系统难以应对的常识溯因推理类别，以及最优模型表现异常突出的类别。虽然之前已有研究尝试对蕴含推理所需的常识知识进行分类（LoBue & Yates, 2011; Clark et al., 2007），但在保持高质量和高注释者一致性的前提下大规模众包这一任务仍极具挑战。为此，我们转而通过将特定类别关键词列表与假设候选进行匹配来探测模型，以软类别的形式进行分析。

表 3 展示了最优模型（BERT-ft）在各常识知识类别上的准确率。BERT-ft 在涉及**数值（Numerical，56.8%）**和**空间（Spatial，65.4%）**常识的实例上表现明显较差。这两类别涉及对数值量和主体/物体空间位置的推理，揭示了语言模型的若干局限性。相比之下，该模型在**情感（Emotional，72.6%）**类别上表现明显更好——这类假设包含有关情绪和情感的强烈文本线索。

**表 3：BERT 在 ART 测试集 1,000 个实例上的性能及人类评估，按常识推理领域分类（数值、空间、情感）。括号内为类别样本量。**

| 类别 | 人类准确率 | BERT 准确率 | 差值 |
|---|---|---|---|
| 全部 (1,000) | 91.4 | 68.8 | 22.6 |
| 数值 (44) | 88.6 | 56.8 | 21.8 |
| 空间 (130) | 91.5 | 65.4 | 26.1 |
| 情感 (84) | 86.9 | 72.6 | 14.3 |

**不合理转换** 针对 ART 数据集中的实例，模型应在两个给定观察的情境下排除不合理的假设。在叙事情境中，假设被标注为不合理主要有三类原因：

1. **O₁ ↛ h⁻**：h⁻ 在第一个观察 O₁ 之后不太可能发生。
2. **h⁻ ↛ O₂**：h⁻ 在 O₁ 之后虽然合理，但不太可能先于第二个观察 O₂ 发生。
3. **合理替代（Plausible）**：⟨O₁, h⁻, O₂⟩ 构成连贯的叙事且形成合理的替代方案，但其合理性不如 ⟨O₁, h⁺, O₂⟩。

我们分析了 ART 中各类原因的分布情况。我们设计了一项众包任务，向工作者展示不合理假设和叙事情境 ⟨O₁, O₂⟩，请他们标注叙事链中哪个转换（O₁ ↛ h⁻、h⁻ ↛ O₂ 或两者均不）被打断了。表 4 展示了测试集 1,000 个实例子集中各类别的比例。

**表 4：测试集随机 1,000 个实例中，负假设导致特定故事转换中断的比例，以及 BERT-ft 全连接与线性链模型在各类别上的准确率。**

| 故事转换 | 占数据集比例 | BERT-ft 全连接准确率 (%) | BERT-ft 线性链准确率 (%) |
|---|---|---|---|
| O₁ ↛ h⁻ | 32.5% | 73.6 | 71.6 |
| h⁻ ↛ O₂ | 45.3% | 69.0 | 70.5 |
| 合理替代 | 22.2% | 62.5 | 58.5 |
| 全部 (1,000) | 100.0% | 69.1 | 68.2 |

h⁻ ↛ O₂ 占 ART 中不合理转换的近一半；三类原因在数据集中均占有相当比例。BERT 在各类别上的性能表明，当不合理假设所构成的叙事本身合理但整体合理性不如正确假设时，模型最难作出判断。在这一子集上，全连接模型优于线性链模型——因为需要联合考量两个观察才能得出更合理的假设。

### 6.2 αNLG 分析

图 6 展示了各训练模型与人工撰写假设的若干生成示例。左侧示例是只有人类才能给出正确解释的实例，而右侧示例中 COMeT-Emb+GPT2 也生成了正确的解释。

**图 6：两个 ART 实例中，不同模型及人工撰写假设的生成对比。**

**实例一：**
- **O₁**：Larry 的院子里落满了枯叶。
- **O₂**：Larry 决定放弃这一天，回屋去了。
- GPT2：不相关的内容（"…他不小心在妈妈的地下室住了一整年…"）
- O₁-O₂-Only：Larry 想着能拿这些叶子做什么。
- COMeT-Txt+GPT2：Larry 决定把院子里的泥铲掉。
- COMeT-Emb+GPT2：Larry 把叶子扔掉了。
- 人工撰写：他花了好几个小时试图打扫院子。

**实例二：**
- **O₁**：Junior 是我们养了 20 多年的乌龟。
- **O₂**：Junior 依然活力十足。
- GPT2：其实，那只乌龟咬不了你。
- O₁-O₂-Only：Junior 做了一根大跳绳。
- COMeT-Txt+GPT2：Junior 将做手术治疗，她的内脏受损了。
- COMeT-Emb+GPT2：Junior 和她的朋友们一起在泳池里游泳。
- 人工撰写：我们带 Junior 去兽医那里检查了一下。

---

## 7 从 ART 迁移学习

ART 包含大量针对溯因推理这一新型任务的训练样例。除作为基准测试之外，我们还探索了能否将 ART 作为资源来提升其他常识推理任务的性能。我们通过迁移学习的方式，先在 ART 上训练模型，再在四个目标数据集上进行训练——WinoGrande（Sakaguchi et al., 2020）、WSC（Levesque et al., 2011）、DPR（Rahman & Ng, 2012）以及 HellaSwag（Zellers et al., 2019）。实验表明，相比仅在目标数据集上训练的模型，先在 ART 上顺序预训练、再在目标数据集上训练的模型，在目标任务上的表现有所提升。尤其是当目标数据集训练样例较少时，ART 预训练能持续提升性能。

另一方面，对于拥有大量训练数据的目标数据集，ART 预训练带来的提升不显著。

**表 5：从 ART 的迁移学习。**

| 数据集 | BERT-ft(D) | BERT-ft(ART)→BERT-ft(D) |
|---|---|---|
| WinoGrande (Sakaguchi et al., 2020) | 65.8% | 67.2% |
| WSC (Levesque et al., 2011) | 70.0% | 74.0% |
| DPR (Rahman & Ng, 2012) | 72.5% | 86.0% |
| HellaSwag (Zellers et al., 2019) | 46.7% | 46.1% |

---

## 8 相关工作

**完形填空任务与溯因推理** 由于溯因推理本质上关注的是合理的因果链，本工作从若干处理叙事的先前工作中汲取灵感，包括脚本学习（Schank & Abelson, 1975）和叙事完形填空测试（Chambers & Jurafsky, 2009; Jans et al., 2012; Pichotta & Mooney, 2014; Rudinger et al., 2015）。与学习原型脚本或叙事链不同，我们在观察条件下推理最合理的事件。我们利用了专为叙事完形填空任务设计的 ROCStories 数据集（Mostafazadeh et al., 2016）。但不同于推理合理的事件序列，我们的任务要求推理叙事省略的合理解释。

**蕴含推理与溯因推理** αNLI 的形式化与蕴含 NLI 密切相关，但有两个关键区别使得溯因推理尤为具有挑战性。第一，溯因推理需要推理观察的常识性含义（例如，观察到"草是湿的"，可能的假设是"之前下雨了"），这超越了语言蕴含的范畴（Josephson, 2000 也指出了这一点）。第二，溯因推理需要对一组常识含义进行非单调推理——通过检查与多个观察之间的潜在矛盾，并比较不同假设的合理程度。这使得溯因推理比归纳和演绎等其他推理形式更具挑战性（Shank, 1998）。或许更重要的是，溯因推理与人类在日常情境中进行的推理密切相关——在信息不完整、无法作出确定性推断的情况下，人类日常正是这样推理的。

**生成式语言建模** 大规模预训练语言模型的最新进展（Radford, 2018; Devlin et al., 2018; Radford et al., 2019）提升了生成文本的质量与连贯性。尽管这些模型在以文本序列为条件时能生成相当连贯的文本，我们的实验揭示了这些模型的局限性：（1）无法非单调地生成语言；（2）无法遵循常识知识。我们尝试通过在假设生成过程中引入生成式常识模型来克服这些局限。

**相关数据集** ART 是对自然语言推理资源持续建设工作的有益补充（Dagan et al., 2006; MacCartney & Manning, 2009; Bowman et al., 2015; Williams et al., 2018a; Camburu et al., 2018）。现有数据集大多聚焦于演绎推理框架下的文本蕴含（Bowman et al., 2015; Williams et al., 2018a）以及对合理事件的推断（Maslan et al., 2015; Zhang et al., 2017）。在这些数据集的典型设定中，系统需要从给定前提中演绎出逻辑上必然成立的推论。相比之下，溯因推理的本质要求系统运用常识推理能力，而非聚焦于词汇蕴含。虽然溯因推理已被应用于蕴含数据集（Raina et al., 2005），但其被作为逻辑定理证明框架中的中间步骤来执行文本蕴含——这与 αNLI 是本质上不同的任务。

---

## 9 结论

本文首次系统考察了基于语言的溯因推理的可行性。我们提出并引入了**溯因自然语言推理（αNLI）**——一项专注于叙事情境溯因推理的新型任务，将其形式化为多项选择问答问题；同时引入了**溯因自然语言生成（αNLG）**——一项要求机器为给定观察生成合理假设的新型任务。为支持这两项任务，我们创建并发布了新的挑战性数据集 ART，包含 2 万条常识叙事及超过 20 万条解释性假设。在实验中，我们基于最先进的 NLI 和语言模型建立了全面的基线性能，最优基线准确率为 68.9%，与人类表现（91.4%）仍有较大差距。αNLG 任务更具挑战性——人类撰写有效解释的成功率为 96%，而最优生成模型仅能达到 45%。我们的分析揭示了深度预训练语言模型在哪些推理类型上存在不足——尽管它们在密切相关但本质不同的蕴含 NLI 任务上表现出色——从而为未来研究指出了有趣的方向。我们希望 ART 能成为未来基于语言的溯因推理研究的挑战性基准，αNLI 和 αNLG 任务能促进具备复杂推理能力的 AI 系统中的表示学习。

---

## 致谢

感谢匿名审稿人提供的深刻反馈。本研究得到 NSF（IIS-1524371）、美国国家科学基金会研究生研究奖学金（Grant No. DGE 1256082）、DARPA CwC（通过 ARO，W911NF15-1-0543）、DARPA MCS 项目（通过 NIWC Pacific，N66001-19-2-4031）以及 Allen Institute for AI 的部分支持。beaker.org 上的计算资源得到 Google Cloud 学分的部分支持。

---

## 参考文献

Henning Andersen. Abductive and deductive change. *Language*, pp. 765–793, 1973. URL https://www.jstor.org/stable/pdf/412063.pdf.

Satanjeev Banerjee and Alon Lavie. Meteor: An automatic metric for MT evaluation with improved correlation with human judgments. In *Proceedings of the ACL Workshop on Intrinsic and Extrinsic Evaluation Measures for Machine Translation and/or Summarization*, pp. 65–72, 2005.

Antoine Bosselut, Hannah Rashkin, Maarten Sap, Chaitanya Malaviya, Asli Celikyilmaz, and Yejin Choi. COMET: Commonsense transformers for automatic knowledge graph construction. *arXiv preprint arXiv:1906.05317*, 2019.

Samuel R. Bowman, Gabor Angeli, Christopher Potts, and Christopher D. Manning. A large annotated corpus for learning natural language inference. In *Proceedings of the 2015 Conference on Empirical Methods in Natural Language Processing (EMNLP)*. Association for Computational Linguistics, 2015. URL https://nlp.stanford.edu/pubs/snli_paper.pdf.

Oana-Maria Camburu, Tim Rocktäschel, Thomas Lukasiewicz, and Phil Blunsom. e-SNLI: Natural language inference with natural language explanations. In *Advances in Neural Information Processing Systems*, pp. 9560–9572, 2018. URL https://papers.nips.cc/paper/8163-e-snli-natural-language-inference-with-natural-language-explanations.pdf.

Nathanael Chambers and Dan Jurafsky. Unsupervised learning of narrative schemas and their participants. In *Proceedings of the Joint Conference of the 47th Annual Meeting of the ACL and the 4th International Joint Conference on Natural Language Processing of the AFNLP*, pp. 602–610, Suntec, Singapore, August 2009. Association for Computational Linguistics. URL http://www.aclweb.org/anthology/P/P09/P09-1068.

Eugene Charniak and Solomon Eyal Shimony. Probabilistic semantics for cost based abduction. Brown University, Department of Computer Science, 1990. URL https://www.aaai.org/Papers/AAAI/1990/AAAI90-016.pdf.

Qian Chen, Xiao-Dan Zhu, Zhen-Hua Ling, Si Wei, Hui Jiang, and Diana Inkpen. Enhanced LSTM for natural language inference. In *ACL*, 2017. URL https://www.aclweb.org/anthology/P17-1152.

Peter E. Clark, Philip Harrison, John A. Thompson, William R. Murray, Jerry R. Hobbs, and Christiane Fellbaum. On the role of lexical and world knowledge in RTE3. In *ACL-PASCAL@ACL*, 2007. URL https://www.aclweb.org/anthology/W07-1409.

Alexis Conneau, Douwe Kiela, Holger Schwenk, Loïc Barrault, and Antoine Bordes. Supervised learning of universal sentence representations from natural language inference data. In *Proceedings of the 2017 Conference on Empirical Methods in Natural Language Processing*, pp. 670–680, Copenhagen, Denmark, September 2017. Association for Computational Linguistics. doi: 10.18653/v1/D17-1070. URL https://www.aclweb.org/anthology/D17-1070.

Ido Dagan, Oren Glickman, and Bernardo Magnini. The PASCAL recognising textual entailment challenge. In *Machine Learning Challenges. Evaluating Predictive Uncertainty, Visual Object Classification, and Recognising Textual Entailment*, pp. 177–190. Springer, 2006. URL http://u.cs.biu.ac.il/~dagan/publications/RTEChallenge.pdf.

Jacob Devlin, Ming-Wei Chang, Kenton Lee, and Kristina Toutanova. BERT: Pre-training of deep bidirectional transformers for language understanding. *arXiv preprint arXiv:1810.04805*, 2018. URL https://arxiv.org/abs/1810.04805.

Suchin Gururangan, Swabha Swayamdipta, Omer Levy, Roy Schwartz, Samuel Bowman, and Noah A. Smith. Annotation artifacts in natural language inference data. In *Proceedings of the 2018 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies*, Volume 2 (Short Papers), pp. 107–112, New Orleans, Louisiana, June 2018. Association for Computational Linguistics. doi: 10.18653/v1/N18-2017. URL https://www.aclweb.org/anthology/N18-2017.

Jerry R. Hobbs, Mark Stickel, Paul Martin, and Douglas Edwards. Interpretation as abduction. In *Proceedings of the 26th Annual Meeting of the Association for Computational Linguistics*, pp. 95–103, Buffalo, New York, USA, June 1988. Association for Computational Linguistics. doi: 10.3115/982023.982035. URL https://www.aclweb.org/anthology/P88-1012.

Bram Jans, Steven Bethard, Ivan Vulić, and Marie-Francine Moens. Skip n-grams and ranking functions for predicting script events. In *Proceedings of the 13th Conference of the European Chapter of the Association for Computational Linguistics*, pp. 336–344, Avignon, France, April 2012. Association for Computational Linguistics. URL http://www.aclweb.org/anthology/E12-1034.

Susan G. Josephson. Abductive inference: Computation, philosophy, technology. 2000. URL https://philpapers.org/rec/JOSAIC.

George Lakoff. Linguistics and natural logic. *Synthese*, 22(1-2):151–271, 1970. URL https://link.springer.com/article/10.1007/BF00413602.

Hector J. Levesque, Ernest Davis, and Leora Morgenstern. The Winograd schema challenge. In *KR*, 2011.

Chin-Yew Lin. ROUGE: A package for automatic evaluation of summaries. *Text Summarization Branches Out*, 2004.

Peter LoBue and Alexander Yates. Types of common-sense knowledge needed for recognizing textual entailment. In *ACL*, 2011. URL https://www.aclweb.org/anthology/P11-2057.

Bill MacCartney and Christopher D. Manning. Natural logic for textual inference. In *Proceedings of the ACL-PASCAL Workshop on Textual Entailment and Paraphrasing*, pp. 193–200, Prague, June 2007. Association for Computational Linguistics. URL https://www.aclweb.org/anthology/W07-1431.

Bill MacCartney and Christopher D. Manning. An extended model of natural logic. In *Proceedings of the Eighth International Conference on Computational Semantics*, pp. 140–156, Tilburg, The Netherlands, January 2009. Association for Computational Linguistics. URL https://www.aclweb.org/anthology/W09-3714.

Nicole Maslan, Melissa Roemmele, and Andrew S. Gordon. One hundred challenge problems for logical formalizations of commonsense psychology. In *AAAI Spring Symposia*, 2015. URL http://people.ict.usc.edu/~gordon/publications/AAAI-SPRING15.PDF.

Nasrin Mostafazadeh, Nathanael Chambers, Xiaodong He, Devi Parikh, Dhruv Batra, Lucy Vanderwende, Pushmeet Kohli, and James Allen. A corpus and cloze evaluation for deeper understanding of commonsense stories. In *Proceedings of the 2016 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies (NAACL)*, pp. 839–849. Association for Computational Linguistics, 2016. doi: 10.18653/v1/N16-1098. URL http://aclweb.org/anthology/N16-1098.

Peter Norvig. Inference in text understanding. In *AAAI*, pp. 561–565, 1987. URL http://norvig.com/aaai87.pdf.

Kishore Papineni, Salim Roukos, Todd Ward, and Wei-Jing Zhu. BLEU: A method for automatic evaluation of machine translation. In *ACL*, 2002.

Judea Pearl. Reasoning with cause and effect. *AI Magazine*, 23(1):95, 2002. URL https://ftp.cs.ucla.edu/pub/stat_ser/r265-ai-mag.pdf.

Judea Pearl and Dana Mackenzie. *The Book of Why: The New Science of Cause and Effect*. Basic Books, Inc., New York, NY, USA, 1st edition, 2018. ISBN 046509760X, 9780465097609. URL https://dl.acm.org/citation.cfm?id=3238230.

Charles Sanders Peirce. *Collected Papers of Charles Sanders Peirce*, volume 5. Harvard University Press, 1965a. URL http://www.hup.harvard.edu/catalog.php?isbn=9780674138001.

Charles Sanders Peirce. *Pragmatism and Pragmaticism*, volume 5. Belknap Press of Harvard University Press, 1965b. URL https://www.jstor.org/stable/224970.

Jeffrey Pennington, Richard Socher, and Christopher Manning. GloVe: Global vectors for word representation. In *Proceedings of the 2014 Conference on Empirical Methods in Natural Language Processing (EMNLP)*, pp. 1532–1543, Doha, Qatar, October 2014. Association for Computational Linguistics. doi: 10.3115/v1/D14-1162. URL https://www.aclweb.org/anthology/D14-1162.

Matthew Peters, Mark Neumann, Mohit Iyyer, Matt Gardner, Christopher Clark, Kenton Lee, and Luke Zettlemoyer. Deep contextualized word representations. In *Proceedings of the 2018 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies*, Volume 1 (Long Papers), pp. 2227–2237, New Orleans, Louisiana, June 2018. Association for Computational Linguistics. doi: 10.18653/v1/N18-1202. URL https://www.aclweb.org/anthology/N18-1202.

Karl Pichotta and Raymond Mooney. Statistical script learning with multi-argument events. In *Proceedings of the 14th Conference of the European Chapter of the Association for Computational Linguistics*, pp. 220–229, Gothenburg, Sweden, April 2014. Association for Computational Linguistics. URL http://www.aclweb.org/anthology/E14-1024.

Adam Poliak, Jason Naradowsky, Aparajita Haldar, Rachel Rudinger, and Benjamin Van Durme. Hypothesis only baselines in natural language inference. In *Proceedings of the Seventh Joint Conference on Lexical and Computational Semantics*, pp. 180–191, New Orleans, Louisiana, June 2018. Association for Computational Linguistics. doi: 10.18653/v1/S18-2023. URL https://www.aclweb.org/anthology/S18-2023.

Alec Radford. Improving language understanding by generative pre-training. 2018.

Alec Radford, Jeffrey Wu, Rewon Child, David Luan, Dario Amodei, and Ilya Sutskever. Language models are unsupervised multitask learners. *OpenAI Blog*, 1(8), 2019.

Altaf Rahman and Vincent Ng. Resolving complex cases of definite pronouns: The Winograd schema challenge. In *EMNLP-CoNLL*, 2012.

Rajat Raina, Andrew Y Ng, and Christopher D Manning. Robust textual inference via learning and abductive reasoning. In *AAAI*, pp. 1099–1105, 2005. URL https://nlp.stanford.edu/~manning/papers/aaai05-learnabduction.pdf.

Rachel Rudinger, Pushpendre Rastogi, Francis Ferraro, and Benjamin Van Durme. Script induction as language modeling. In *Proceedings of the 2015 Conference on Empirical Methods in Natural Language Processing*, pp. 1681–1686, Lisbon, Portugal, September 2015. Association for Computational Linguistics. URL http://aclweb.org/anthology/D15-1195.

Keisuke Sakaguchi, Ronan Le Bras, Chandra Bhagavatula, and Yejin Choi. WinoGrande: An adversarial Winograd schema challenge at scale. In *AAAI*, 2020.

Maarten Sap, Ronan Le Bras, Emily Allaway, Chandra Bhagavatula, Nicholas Lourie, Hannah Rashkin, Brendan Roof, Noah A Smith, and Yejin Choi. ATOMIC: An atlas of machine commonsense for if-then reasoning. In *Proceedings of the AAAI Conference on Artificial Intelligence*, volume 33, pp. 3027–3035, 2019.

Roger C. Schank and Robert P. Abelson. Scripts, plans, and knowledge. In *Proceedings of the 4th International Joint Conference on Artificial Intelligence - Volume 1*, IJCAI'75, pp. 151–157, San Francisco, CA, USA, 1975. Morgan Kaufmann Publishers Inc. URL http://dl.acm.org/citation.cfm?id=1624626.1624649.

Gary Shank. The extraordinary ordinary powers of abductive reasoning. *Theory & Psychology*, 8(6):841–860, 1998. URL https://journals.sagepub.com/doi/10.1177/0959354398086007.

Masatoshi Tsuchiya. Performance impact caused by hidden bias of training data for recognizing textual entailment. *CoRR*, abs/1804.08117, 2018. URL http://www.lrec-conf.org/proceedings/lrec2018/pdf/786.pdf.

Ramakrishna Vedantam, C Lawrence Zitnick, and Devi Parikh. CIDEr: Consensus-based image description evaluation. In *Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition*, pp. 4566–4575, 2015.

Alex Wang, Amanpreet Singh, Julian Michael, Felix Hill, Omer Levy, and Samuel Bowman. GLUE: A multi-task benchmark and analysis platform for natural language understanding. In *Proceedings of the 2018 EMNLP Workshop BlackboxNLP: Analyzing and Interpreting Neural Networks for NLP*, pp. 353–355, Brussels, Belgium, November 2018. Association for Computational Linguistics. URL https://www.aclweb.org/anthology/W18-5446.

Adina Williams, Nikita Nangia, and Samuel Bowman. A broad-coverage challenge corpus for sentence understanding through inference. In *Proceedings of the 2018 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies*, Volume 1 (Long Papers), pp. 1112–1122. Association for Computational Linguistics, 2018a. URL http://aclweb.org/anthology/N18-1101.

Adina Williams, Nikita Nangia, and Samuel Bowman. A broad-coverage challenge corpus for sentence understanding through inference. In *Proceedings of the 2018 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies*, Volume 1 (Long Papers), pp. 1112–1122, New Orleans, Louisiana, June 2018b. Association for Computational Linguistics. doi: 10.18653/v1/N18-1101. URL https://www.aclweb.org/anthology/N18-1101.

Rowan Zellers, Yonatan Bisk, Roy Schwartz, and Yejin Choi. SWAG: A large-scale adversarial dataset for grounded commonsense inference. In *Proceedings of the 2018 Conference on Empirical Methods in Natural Language Processing (EMNLP)*, 2018. URL https://aclweb.org/anthology/D18-1009.

Rowan Zellers, Ari Holtzman, Yonatan Bisk, Ali Farhadi, and Yejin Choi. HellaSwag: Can a machine really finish your sentence? In *ACL*, 2019.

Sheng Zhang, Rachel Rudinger, Kevin Duh, and Benjamin Van Durme. Ordinal common-sense inference. *Transactions of the Association for Computational Linguistics*, 5:379–395, 2017. doi: 10.1162/tacl_a_00068. URL https://www.aclweb.org/anthology/Q17-1027.

Tianyi Zhang, Varsha Kishore, Felix Wu, Kilian Q Weinberger, and Yoav Artzi. BERTScore: Evaluating text generation with BERT. *arXiv preprint arXiv:1904.09675*, 2019.

---

## 附录

### A.1 数据收集细节

以下描述数据收集方法的众包细节。

**任务一：合理假设** 参与者看到一个不完整的三段式故事，包含第一个观察（O₁）和第二个观察（O₂）。然后要求他们补全故事，写出一个合理的中间句子，说明为什么第二个观察应该紧随第一个之后发生。我们要求参与者确保合理的中间句子：（1）简短（不超过 10 个词）；（2）简单，就像在给孩子讲故事；（3）避免引入多余信息；（4）尽量使用名字而非代词（如他/她）。

所有参与者须满足以下资格要求：（1）地理位置在美国；（2）HIT 通过率超过 95%；（3）已通过 HIT 数量超过 5,000。该任务每道题酬劳为 0.07 美元（平均时薪 14 美元），每个 HIT 分配给五名不同工作者（即 5 路冗余）。

**任务二：不合理假设** 参与者看到一个三段式故事，包含第一个观察（O₁）、来自任务一的中间句子（h⁺）以及第二个观察（O₂）。然后要求他们以最小幅度改写中间句子（h⁺），使故事变得不合理、不可信或前后矛盾（h⁻）。我们要求参与者在 h⁺ 的基础上最多增删四个词，同时保证新中间句的语法正确性。此外，我们要求他们紧扣给定故事的情境——例如，若故事涉及"医生"，可以谈及"健康"或"诊断"，但不能提及"外星人"。最后，我们还要求工作者确认给定的中间句（h⁺）是否构成合理的故事，以验证任务一中收集的 h⁺ 的合理性。

该任务的资格要求为：（1）地理位置在美国或加拿大；（2）HIT 通过率不低于 99%；（3）已通过 HIT 数量不低于 10,000。每道题酬劳为 0.1 美元（平均时薪 14 美元），每个 HIT 分配给三名不同参与者（即 3 路冗余）。

**任务三：αNLI 人类表现** 通过要求参与者回答 αNLI 问题来评估人类表现。给定叙事情境 ⟨O₁, O₂⟩ 和两个假设，要求他们选出更合理的假设；若两个假设均不合理，还可选"以上都不是"。

每道题由七名参与者作答，资格要求如下：（1）地理位置在美国、英国或加拿大；（2）HIT 通过率超过 98%；（3）已通过 HIT 数量超过 10,000。每道题酬劳为 0.05 美元。对每道题的七名参与者取多数票，以此计算人类表现。

### A.2 ART 数据集统计

表 6 给出了 ART 数据集的若干统计信息。

**表 6：ART 数据集统计摘要。** 训练集包含所有通过众包收集的合理和不合理假设，验证集和测试集仅包含通过对抗过滤算法选出的假设。

| 统计项 | 训练集 | 验证集 | 测试集 |
|---|---|---|---|
| **总计（唯一出现次数）** | | | |
| 情境对 ⟨O₁, O₂⟩ | 17,801 | 1,532 | 3,059 |
| 合理假设 h⁺ | 72,046 | 1,532 | 3,059 |
| 不合理假设 h⁻ | 166,820 | 1,532 | 3,059 |
| **每情境平均数量** | | | |
| 合理假设 h⁺ | 4.05 | 1 | 1 |
| 不合理假设 h⁻ | 9.37 | 1 | 1 |
| **平均词数** | | | |
| 合理假设 h⁺ | 8.34 | 8.62 | 8.54 |
| 不合理假设 h⁻ | 8.28 | 8.55 | 8.53 |
| 第一观察 O₁ | 8.09 | 8.07 | 8.17 |
| 第二观察 O₂ | 9.29 | 9.30 | 9.31 |

### A.3 BERT 微调

我们使用如下超参数组合进行网格搜索来微调 BERT：
- **批大小**：{3, 4, 8}
- **训练轮数**：{3, 4, 10}
- **学习率**：{1e-5, 2e-5, 3e-5, 5e-5}

预热比例设为 0.2，使用交叉熵计算损失。最优性能对应配置为：批大小 4，学习率 5e-5，训练轮数 10。表 7 描述了 GPT 和 BERT（及其变体）的输入格式。

**表 7：GPT 和 BERT 微调的输入格式。**

| 模型 | 输入格式 |
|---|---|
| GPT | [START] O₁ + hⁱ [SEP] O₂ [SEP] |
| BERT-ft [仅假设] | [CLS] hⁱ [SEP] |
| BERT-ft [仅第一观察] | [CLS] O₁ [SEP] hⁱ [SEP] |
| BERT-ft [仅第二观察] | [CLS] hⁱ [SEP] O₂ [SEP] |
| BERT-ft [线性链] | [CLS] O₁ [SEP] hⁱ [SEP] ; [CLS] hⁱ [SEP] O₂ [SEP] |
| BERT-ft [全连接] | [CLS] O₁ + O₂ [SEP] hⁱ [SEP] |

### A.4 基线模型

SVM 分类器基于词长、词汇重叠和情感等简单特征，从两个假设候选中选择一个。词袋基线计算每个句子中词的平均 GloVe（Pennington et al., 2014）嵌入向量，形成句子嵌入。一个故事中各句子（两个观察和一个假设候选）的句子嵌入拼接后，通过全连接层为每个假设产生分数。两种基线的准确率均接近 50%（SVM：50.6；词袋：50.5）。

具体而言，我们使用 GloVe 嵌入训练 SVM 分类器和词袋模型，两种模型的准确率均接近 50%。使用 Bi-LSTM token 表示上最大池化进行句子嵌入的 Infersent（Conneau et al., 2017）基线仅取得 50.8% 的准确率。

### A.5 假设候选对抗过滤

给定一个观察对和合理、不合理假设集 ⟨O₁, O₂, H⁺, H⁻⟩，我们的对抗过滤算法从中选出一对合理和不合理假设 ⟨O₁, O₂, h⁺, h⁻⟩，使得 h⁺ 和 h⁻ 难以区分。我们在 Zellers et al. (2018) 提出的对抗过滤（AF）方法基础上作出三项关键改进。

第一，我们利用合理假设池 H⁺ 而非单一正样本进行选择。第二，负样本池 H⁻（即不合理假设）由人工生成，而非机器生成。这样，干扰项不仅在文体上与正样本相近，还与情境（O₁ 和 O₂）风格一致——使负样本更难与正样本区分。第三，我们使用 BERT（Devlin et al., 2018）作为对抗者，并引入温度参数控制每次 AF 迭代中可修改的最大实例数——随着迭代次数增加，可修改的实例数减少，使 AF 算法收敛更平滑（详见下文）。

算法 1 给出了我们方法的形式化描述。在每次迭代 i 中，我们在数据的随机子集 Ti 上训练对抗模型 Mi，并更新验证集 Vi 使其对 Mi 更具挑战性。对于实例 k 的一对合理和不合理假设 (h⁺ₖ, h⁻ₖ)，记 δ = ΔMᵢ(h⁺ₖ, h⁻ₖ) 为模型对 h⁺ₖ 和 h⁻ₖ 评分之差。δ 为正表示模型 Mi 倾向于合理假设 h⁺ₖ 而非不合理假设 h⁻ₖ。以概率 tᵢ 更新 Mi 答对的实例 k，用能减小 δ 值的 (h⁺, h⁻) ∈ Hₖ⁺ × Hₖ⁻ 进行替换，其中 Hₖ⁺（Hₖ⁻）为实例 k 的合理（不合理）假设池。

我们运行 AF 50 次迭代，温度 tᵢ 由迭代次数参数化的 sigmoid 函数确定，从 tₛ = 1.0 到 tₑ = 0.2 衰减。最终数据集 ART 以 BERT 作为算法 1 中的对抗者生成。

**算法 1：双重对抗过滤（Dual Adversarial Filtering）**

**输入**：数据集 D₀，合理和不合理假设集 (H⁺, H⁻)，迭代次数 n，初始和终止温度 (tₛ, tₑ)

**输出**：数据集 Dₙ

```
for 迭代 i : 0..n-1 do
    tᵢ = tₑ + (tₛ - tₑ) / (1 + exp(0.3 * (i - 3n/4)))
    将 Dᵢ 随机划分为 (Tᵢ, Vᵢ)
    在 Tᵢ 上训练模型 Mᵢ
    Sᵢ = ∅（Vᵢ 中选出的假设）
    for (h⁺ₖ, h⁻ₖ) ∈ Vᵢ do
        从 [0, 1] 均匀随机抽取 r
        if r > tᵢ 或 ΔMᵢ(h⁺ₖ, h⁻ₖ) < 0 then
            将 (h⁺ₖ, h⁻ₖ) 加入 Sᵢ
        else
            在 Hₖ⁺ × Hₖ⁻ 中选 (h⁺, h⁻) 使 ΔMᵢ(h⁺, h⁻) < ΔMᵢ(h⁺ₖ, h⁻ₖ)
            将 (h⁺, h⁻) 加入 Sᵢ
        end
    end
    Dᵢ₊₁ = Tᵢ ∪ Sᵢ
end
```

### A.6 ATOMIC 关系

ATOMIC（Sap et al., 2019）将常识知识表示为图，事件为节点，以下九种关系为边：

1. **xIntent**：X 引发该事件的意图是什么？
2. **xNeed**：事件发生前 X 需要做什么？
3. **xAttr**：X 会被如何描述？
4. **xEffect**：该事件对 X 产生了什么影响？
5. **xWant**：事件发生后 X 可能想做什么？
6. **xReaction**：事件发生后 X 有何感受？
7. **oReact**：事件发生后他人有何感受？
8. **oWant**：事件发生后他人可能想做什么？
9. **oEffect**：该事件对他人产生了什么影响？

### A.7 生成模型输入格式

表 8 描述了各 GPT2 变体模型的输入格式。

**表 8：各 GPT2 模型的训练和生成输入格式。** cʲᵢ 表示由独立 Transformer 模型为关系 i 和观察 j 获得的 COMeT 嵌入；Tⁱⱼ 为关系 i、观察 j 对应的文本短语。在适当情况下，输入序列中添加了域专属的起止标签。

| 模型 | 输入格式 |
|---|---|
| GPT2-Fixed | w¹₁ ... w¹ₙ w²₁ ... w²ₙ Because, |
| O₁-O₂-Only | ⟨o1⟩ w¹₁ ... w¹ₙ ⟨/o1⟩ ⟨o2⟩ w²₁ ... w²ₙ ⟨/o2⟩ ⟨h⟩ |
| COMeT-Txt+GPT2 | ⟨p¹₁⟩ T¹₁ ... T¹₉ ⟨p¹₉⟩ ⟨p²₁⟩ T²₁ ... T²₉ ⟨p²₉⟩ ⟨o1⟩ w¹₁ ... w¹ₙ ⟨/o1⟩ ⟨o2⟩ w²₁ ... w²ₙ ⟨/o2⟩ ⟨h⟩ |
| COMeT-Emb+GPT2 | c¹₁ ... c¹₉ ; c²₁ ... c²₉ ⟨o1⟩ w¹₁ ... w¹ₙ ⟨/o1⟩ ⟨o2⟩ w²₁ ... w²ₙ ⟨/o2⟩ ⟨h⟩ |

---

¹ 其颁奖典礼完整演讲稿见：https://www.mitpressjournals.org/doi/full/10.1162/COLI_a_00171

² αNLI 和 αNLG 分别读作 alpha-NLI 和 alpha-NLG。

³ ART：叙事文本中的溯因推理（Abductive Reasoning in narrative Text）。

⁴ 数据下载地址：http://abductivecommonsense.xyz

⁵ ART 数据集将在论文录用后公开发布。

⁶ 两项众包任务均较为复杂，需要进行创意写作。我们将与 ART 数据集一同公开发布所有众包任务的模板和完整说明，以推动该方向未来的数据收集和研究。

⁷ 众包细节详见附录 A.1。

⁸ GPT 模型和 BERT 变体的输入格式详见附录 A.4。

⁹ 九种关系的完整列表详见附录 A.6。

¹⁰ 各模型输入格式的详细描述见附录 A.7。
