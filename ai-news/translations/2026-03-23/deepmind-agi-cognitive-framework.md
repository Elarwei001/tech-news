# 衡量迈向 AGI 的进展：一个认知框架

---

**元信息**

- **原文标题**: Measuring Progress Toward AGI: A Cognitive Framework
- **作者**: Ryan Burnell, Yumeya Yamamori, Orhan Firat, Kate Olszewska, Steph Hughes-Fitt, Oran Kelly, Isaac R. Galatzer-Levy, Meredith Ringel Morris, Allan Dafoe, Alison M. Snyder, Noah D. Goodman\*, Matthew Botvinick\*, Shane Legg（均来自 Google DeepMind；\*工作完成时就职于 Google DeepMind）
- **发布日期**: 2026-03-16
- **原文链接**: https://arxiv.org/（论文预印本，通讯作者：rburnell@google.com）
- **翻译日期**: 2026-03-23
- **译者**: Alice Larry（技术翻译）

---

尽管关于 AGI 的讨论已相当广泛，目前却缺乏一套衡量其进展的清晰框架。这种模糊性助长了主观臆断，使进展追踪愈加困难，也可能阻碍负责任的治理。为填补这一空白，本文提出了一个用于理解系统能力与人类认知能力关系的框架。我们借鉴心理学、神经科学和认知科学数十年的研究成果，构建了一套**认知分类体系（Cognitive Taxonomy）**，将通用智能解构为 10 个关键认知能力维度。在此基础上，我们提出了一套严格的评估协议：通过在一系列有针对性的、保留测试集的认知任务上衡量系统表现，生成一份可用于了解系统优劣势的"认知画像"。我们希望这一框架能提供切实可行的路线图，并成为对 AGI 进行更严格、更具实证性评估的第一步。

---

## 1. 引言

人工通用智能（Artificial General Intelligence，AGI）有潜力加速科学发现、提升生产力，并帮助解决人类面临的一些最紧迫的问题。然而，我们对距离这一关键里程碑有多远的认识，却因为缺乏关于通用智能应如何被操作化和测量的清晰共识而受到阻碍。由此导致的结果是：当今 AI 工具的能力往往被低估或高估，未来系统潜在的收益与风险也难以得到充分理解。这种缺乏实证依据的状况，既妨碍研究人员清晰传达进展，也使政策制定者难以制定有效的治理措施，最终阻碍了我们以负责任的方式共同走向 AGI。为解决这一关键空白，我们提出了一个认知框架，用以衡量日益强大的 AI 系统的进展。

### 1.1 AGI 的操作化

"AGI"这一术语有着悠久的历史。它最早由 Mark Gubrud 在 1997 年的一篇论文中提出，指代能"在复杂度和速度上媲美甚至超越人类大脑、能获取并操控和推理通用知识、且在任何原本需要人类智能的操作阶段均可使用"的系统（Gubrud，1997）。此后，2001 年，Shane Legg 在不知晓 Gubrud 工作的情况下，独立创造了"人工通用智能"（Artificial General Intelligence）这一术语，并将其用于 Ben Goertzel 随后出版的同名著作（Goertzel and Pennachin，2007）。书中将 AGI 定义为"具备合理程度的自我理解和自主控制能力，能够在不同情境下解决各类复杂问题，并能学会解决在其被创建时尚未掌握的新问题的 AI 系统"。自此，AGI 成为 AI 能力讨论中的常见术语。然而，这个词经常被用作描述各类高度强大 AI 系统的简写。鉴于通用 AI 系统在社会和科学层面的重大意义，建立精确而稳健的方式来衡量迈向这一里程碑的进展至关重要。

作为这一方向的第一步，Google DeepMind 于 2023 年提出了 AGI 等级框架（Levels of AGI），描绘了迈向通用智能路途中的若干重要阶段（Morris et al.，2024）。该框架将智能视为一种连续的、多维度的构念，并认为系统同时具备高能力和高通用性至关重要。在这两个维度上，人类能力显然是关键参照点。构建一个能够展现人类所有认知能力的系统，将标志着历史性的时刻和哲学上的里程碑。此外，这样的系统将开辟无数应用场景，包括通用助手、个性化学习，以及强大的新型科学工具。

目前仍不清楚的是，我们如何理解 AI 系统距离达到这些认知能力还有多远。过去几年间，已有多个旨在衡量 AGI 进展的基准被提出（例如 Chollet，2019 和 Hendrycks et al.，2025）。然而，现有努力未能覆盖人类认知的全部广度，也缺乏与人类表现的严格比较。本文旨在从两方面填补这一空白：首先，我们提出一套认知分类体系，涵盖 AGI 系统应能达到的人类认知重要方面；其次，我们描述了一个评估 AI 系统在这一认知空间中表现的框架，以帮助我们更好地理解系统能力的定位。

---

## 2. 认知分类体系

要了解 AI 系统相对于人类认知能力所处的位置，首先需要识别使人类得以应对复杂多变世界的关键认知过程。在这一工作中，我们可以借鉴数十年来对人类认知的研究，尤其是心理学、神经科学和认知科学领域，这些学科通过迭代实验构建并完善了认知理论。它们采用广泛的方法，包括实验范式、脑成像技术、患者研究和计算建模，提供了丰富且有实证依据的洞见，可供我们参考。在此，我们运用这些洞见，构建一套认知分类体系，描述证据表明对通用智能至关重要的认知能力。

当然，刻画智能绝非易事。即便在人类认知科学领域内，许多争论仍悬而未决，许多问题尚待回答（Stainton，2006）。人工系统的世界或许更为复杂，各种架构和训练算法的进化速度令生物进化望尘莫及。因此，人类认知的某些方面在人工系统的语境下可能并不适用——这是完全有可能、甚至很可能发生的事情。反过来，这些人工系统中也很可能存在人类所不具备的认知过程。

正因如此，我们的目标并非创作一份涵盖所有认知的权威论述，而是构建一个既有理论依据、又足够全面以覆盖人类智能广度的实用评估框架。我们将这一框架视为起点，并希望它能为人工通用智能的严谨科学研究奠定基础。

### 2.1 认知能力维度

我们的认知分类体系列举了科学研究认为对智能行为至关重要的 10 个认知能力维度（见图 1）。对于每个维度和过程，我们确定了一套具体的能力和子能力，期望一个具有通用智能的系统能够展现。为简洁起见，下文仅对每个维度作简要描述，完整分类体系见附录。

我们分类体系的一个重要特征是：它聚焦于系统**能够做到什么**，而非它**如何做到**（关于这一区分的讨论见 Marr，1982）。这使我们得以对系统所采用的底层机制保持不可知立场，不预设任何特定建模方法。

---

**图 1 | 10 个认知能力维度概览。橙色轮廓标注的为复合维度。**

---

我们从八个捕捉人类认知基本构建块的维度开始：

**感知（Perception）**：从环境中提取和处理感官信息的能力。

**生成（Generation）**：产生输出的能力，包括语音、文本、运动动作和计算机控制动作。

**注意（Attention）**：将认知资源集中于感知刺激、思维或任务需求特定方面的能力。

**学习（Learning）**：通过经验、学习或指导获取新知识、技能或理解的能力。

**记忆（Memory）**：随时间存储和检索信息的能力。

**推理（Reasoning）**：通过运用逻辑原则得出有效结论并进行推断的能力。

**元认知（Metacognition）**：系统对自身认知过程的了解，以及监控和控制这些过程的能力。

**执行功能（Executive functions）**：促进目标导向行为的能力，包括规划、抑制和认知灵活性。

这八个维度构成了基本构建块，但它们并非孤立运作——恰恰相反，它们相互作用、彼此重叠、协同工作、相互依存（Kovacs and Conway，2016）。要全面理解系统的能力，还需要了解它将多个维度协同运用的能力。因此，我们还提出了另外两个**复合维度**，捕捉各认知维度协同运用的两种关键心理情境：

**问题解决（Problem solving）**：找到特定领域问题有效解决方案的能力。

**社会认知（Social cognition）**：处理和解读社会信息并在社会情境中做出适当回应的能力。

我们假设这十个维度捕捉了系统实现高度通用性和高度能力所需的关键能力。在十个维度中的一个或多个存在显著弱点的系统，很可能无法完成大多数人类能够完成的某些现实任务。

---

## 3. 评估认知能力

要了解 AI 系统的认知能力，需要在每个认知维度上对系统进行稳健评估，并与有意义的人类基线进行比较。为此，我们提出以下三阶段评估协议：

1. 在覆盖广泛认知任务的套件中对系统进行认知评估；
2. 在相同认知任务上收集人类基线，以建立比较参照；
3. 构建认知画像，以对应人类表现映射系统在 10 个认知维度上的优势与劣势。

### 3.1 开展认知评估

评估迈向 AGI 进展的第一步，是在覆盖每个认知维度的广泛认知任务套件上评估系统表现。认知任务应当：

- **有针对性地测试特定认知能力**。必须纳入能够隔离每个认知维度的任务，以精确诊断模型弱点。
- **采用保留测试集**。评估应尽可能使用私有的、保留的测试集以防止数据污染——如果系统此前已见过特定测试项目的解法或策略，这些测试的表现便难以反映通用智能（参见 Jacovi et al.，2023）。
- **经独立验证**。为确保社区对研究结论有信心，认知任务和评估结果均应由独立第三方进行审计。
- **对人类而言难度各异**。有些任务对人类来说容易，但对 AI 系统来说很难（参见 Chollet et al.，2025），因此纳入此类任务与挑战人类极限的任务同样重要。
- **结构和形式多样**。特定任务结构上的特异性可能人为地提升（或抑制）该任务上的表现（这对人类和 AI 系统均适用，参见 Cheng and Holyoak，1985；Dasgupta et al.，2024）。因此，每个维度的评估应包含多种结构和形式的任务（例如多选题与开放作答、文本输入与多模态、多步骤与单轮对话）。

### 3.2 收集人类基线

要了解系统能力在一组任务上接近人类水平的程度，需要量化人类在这些相同任务上的表现。

这些人类基线可通过让大量人类样本完成与 AI 系统相同的任务来构建。任务应在相同条件下完成，包括相同的任务说明（以及少样本示例，如果有的话）、回应格式和外部工具访问权限。由于我们希望了解人类能力的全貌，从人类群体中广泛抽样至关重要。与此同时，我们希望了解系统在现实场景中的表现——这些场景涉及通常只有在成年后才能充分发展、并通常需要经过正规教育磨砺的知识和能力。因此，我们建议合理的人类基线应由**在人口统计上具有代表性的成年人样本**构成，且受教育程度至少相当于高中毕业¹。

> ¹ 相当于美国的高中文凭。

### 3.3 构建认知画像

利用认知评估和人类基线的评估结果，我们可以为每个系统构建认知画像，绘制系统相对于人类表现在 10 个认知维度上的优势与劣势。

具体方法是计算系统超越人类样本中多少比例的人，并将系统置于人类表现分布上（见图 2 的示例）。鉴于系统能力的锯齿状特征（Morris et al.，2026），可能出现多种画像形态，例如：

1. 系统在一个或多个认知维度上的得分低于人类基线样本中位数。这样的系统在认知上存在显著弱点，可能在至少某些现实情境下举步维艰。
2. 系统在全部十个认知维度上的得分均高于人类基线样本中位数。这样的系统展现了匹配至少 50% 人类样本认知能力的能力，很可能在许多现实情境中表现良好。
3. 系统在全部十个认知维度上均达到第 99 百分位（图 2C）。这样的系统展现了其能够在整个认知空间中匹配人类样本中几乎任何人的能力。² 当然，任何实际的人类基线样本——即便具有高度代表性——都不太可能捕捉到人类能力的全部范围，因此在基于这种模式得出结论之前，需要进一步的审查。

> ² 一个稍强的检验是要求系统在每个维度上均达到或超过样本最大值。但量化最大值的不确定性较为困难。

以下是若干重要的方法论注意事项：构建认知画像时，需要计算每个人和每个 AI 系统在每个维度上的总体得分（见图 2）。计算这些分数的方式多种多样。最简单的方法是汇总一个维度内各认知任务的指标。但采用更复杂的统计方法——例如构建系统能力的项目反应理论（Item-Response Theory）模型（参见 Martínez-Plumed et al.，2019）——可能会提供更稳健、更具信息量的结果。

无论采用何种方法，量化每项能力估计周围的不确定性都至关重要。这一语境下的不确定性至少来源于三个方面：

1. **任务质量**：提示词质量和任务多样性等因素会极大地影响结果的信息量。
2. **构念效度（Construct validity）**：认知评估旨在提供对广泛认知维度（如推理或注意）的洞察。然而，如果数据集未能有效隔离目标维度，或数据存在污染，结果可能无法准确反映系统的通用能力。
3. **随机性（Stochasticity）**：生成式 AI 系统的随机性为评估结果增添了噪声——要求系统多次完成相同任务，在不同重复中可能产生截然不同的结果（这在具有多个步骤的复杂任务中尤为突出）。

刻画这种不确定性，对于理解系统之间或系统与人类样本之间的差异是否具有实质意义至关重要。

---

**图 2 | 三个假想系统的认知画像。面板 A：相对于人类样本存在显著认知弱点的假想系统。面板 B：在全部认知维度上均优于人类样本中位数的假想系统。面板 C：在全部认知维度上均优于人类样本最大值的假想系统。假想人类样本分数在每个维度上已标准化，仅供示意。**

---

## 4. 讨论

### 4.1 构建认知评估

本文提供了一个在人类认知能力全范围内衡量 AI 系统的框架。要落实这一框架，需要稳健的认知基准。在认知空间的某些领域，已存在许多有用的基准，包括问题解决（Phan et al.，2025）、感知（Patraucean et al.，2023）和世界知识（Cheng et al.，2025；Haas et al.，2025）。但在元认知、注意、学习和社会认知等领域仍存在大量覆盖空白。此外，现存的许多高质量基准已完全公开，因此容易受到数据污染，可能无法提供可泛化的信号。出于这一原因，我们认为现有基准不足以可靠地评估 AI 认知能力。

为填补这些空白，我们正与学术界合作，构建稳健的保留评估集，以更好地评估日益强大的 AI 系统。

### 4.2 超越认知维度

我们的分类体系聚焦于认知能力。但要全面了解 AI 能力和 AI 行为，还需要考虑和评估许多其他系统特性。下文讨论几个我们认为重要的特性，所有这些特性都可以参照人类基线来理解。

#### 4.2.1 处理速度与响应速度

一个响应要具有适应性或实用价值，正确性并不总是充分条件。通常，响应还必须及时。以自动驾驶汽车系统为例，系统的可靠性不仅取决于识别潜在危险的能力，还取决于快速完成这一识别的能力。即便在速度不那么关键的情况下，速度对于理解现实世界的实用性仍然重要——一个能在一分钟内修复编码错误或预订机票的系统，很可能比需要六小时才能完成任务的系统有用得多。

处理速度这一构念至少部分具有认知属性（Danthiir et al.，2005）——例如，问题解决速度取决于系统所采用的思维策略以及其将知识与相关信息联系起来的能力。但速度也取决于硬件和网络速度等其他因素，因此并不完全适合作为认知维度。无论如何，响应速度是应在整个认知空间中加以测量的关键性能指标。

#### 4.2.2 系统倾向性

决定系统部署后行为的另一个重要因素是其**倾向性（propensities）**（即系统的行为趋势，而非仅仅是其能力）。系统愿意承担多大风险？它与人类价值观的对齐程度如何？其典型的问题解决策略是什么？它如何与人交流互动？这些行为因素将显著影响该系统的安全性和可靠性，因此需要稳健的工具来评估它们。对系统倾向性的完整描述超出了本文范围，但将是为部署决策提供信息、实现有效治理的关键研究领域（参见 Romero-Alvarado et al.，2026；Taubenfeld et al.，2026）。

#### 4.2.3 创造力

人类的创造力长期以来是哲学和认知科学感兴趣的主题。然而，关于创造力应如何概念化和测量的争论至今持续（参见 Boden，1994；Kaufmann，2003）。一种常见的思考创造性产出的方式是，它们需要同时具备**新颖性**和**高质量**（Sternberg and Lubart，1998）。但产出是否高质量是高度主观且领域相关的，尤其是当其具有全然新颖的特征时。此外，有观点认为，这些特征不过是智能行为的一般性属性。因此，客观地隔离和评估 AI 系统的创造力可能较为困难。

尽管如此，我们仍可以评估涉及创造力的认知过程。例如，创造力通常与**认知灵活性**相关（即切换思维模式的能力以及生成广泛不同想法的能力），这在分类体系中作为执行功能的组成部分加以涵盖。此外，分类体系还涵盖了世界知识（作为语义记忆的一部分）和问题解决，这两者与创造力均相关（Sternberg and Lubart，1998）。

#### 4.2.4 端到端部署评估

最后，有必要明确指出：认知基准测试并不能替代应用性、端到端的评估——如果一个系统正在被部署于特定情境中，对该系统进行重要部署工作流的评估是绝对必要的。这两种方法是互补的——认知评估有助于解释模型失败并指导模型改进；现实世界的部署评估有助于部署决策并预测经济影响（参见 Mazeika et al.，2025；Patwardhan et al.，2025）。

### 4.3 模型评估与系统评估

历史上，评估主要集中于特定的模型检查点。但现代 AI 系统不仅仅是一个模型——它们部署时附有特定的系统指令，可以访问工具，能够通过动作操控环境，甚至可能具备调用其他 AI 系统的能力。

面对这种日益增加的复杂性，我们应如何开展评估？我们认为，试图将系统的核心模型与其他组件分离将越来越不切实际，因为新系统的内部工作原理往往未被披露，这些不同组件也可能无法轻易分离。这种"仅评估模型"的方法也将变得越来越缺乏信息量，因为在系统部署时能够访问这些组件的情况下，单独评估模型的结果并不能代表系统实际运行或表现的方式。模块化也并非人工系统的专有特征——毕竟，人类大脑也有着具有不同但相互关联功能的各种认知系统和模块（Yeo et al.，2011）。因此，我们认为最佳方案是对系统整体进行评估，包括任何内置工具或模块。

将智能作为系统整体属性进行测量确实有其缺点。例如，一个困难的影响是：赋予特定模型的智能程度取决于围绕它构建的系统框架——类似于得出"一个人在可以使用计算器或电脑时变得更聪明"这一结论。此外，这一方法引发了关于如何构建具有信息量的认知测试的问题。在测试人类时，为维持测试条件的可控性并针对特定认知过程，通常限制外部工具的使用。如果允许 AI 系统在评估中使用任何和所有工具，这些工具可能会混淆研究结果的解读。例如，假设我们想测试历史事件的语义记忆，如果系统可以直接在互联网上搜索这些事件的信息，我们测量的便不再是系统的记忆，而是其搜索互联网的能力。这些是棘手的问题，需要针对每个认知测试逐一考量。至少，任何人类基线研究都应确保参与者可以访问与我们期望 AI 系统使用的相同工具。

### 4.4 验证与迭代

与任何科学一样，人工通用智能的科学在本质上是迭代的。这里描述的认知分类体系无疑只是一个起点——AI 系统很可能会继续发展出无法整齐映射到我们分类体系的认知能力。实际上，AI 系统已经拥有一些人类所不具备的能力，例如 LiDAR 感知和原生图像生成。这一分类体系的未来迭代版本需要探索如何识别、刻画并整合这些智能的新兴组成部分。

关于特定认知维度与现实世界表现之间的关系，我们也还有很多需要了解。如果一个系统在 10 个维度中的一个或多个维度上落后于人类，将清晰表明该系统无法匹配人类智能的通用性。但当系统被部署于现实世界时，特定维度的弱点意味着什么？从理论上有充分理由期待，这里识别的 10 个认知能力每一个对现实世界表现的不同方面都很重要。例如，一个无法规划的系统很可能在长期、多步骤任务中举步维艰；而社会理解力存在缺陷的系统，则可能在涉及与人复杂互动的情境中表现不佳。但仍需实证研究来证明这些关联，并进一步理解每个认知能力在实际现实任务中的重要性。

---

## 5. 结论

对人工通用智能的追求代表着人类的关键时刻。通过提供一个植根于人类认知既有科学的清晰、实证框架，我们旨在将围绕 AGI 的对话从主观断言和推测，引向一个有根基、可测量的科学事业。我们的认知分类体系和评估协议，提供了一种绘制 AI 能力锯齿状景观、追踪迈向通用智能进展的方式。

---

## 6. 贡献者与致谢

**贡献者**

| | | | |
|---|---|---|---|
| Alex Siegman | Dima Yeroshenko | Martin Polacek | Viorica Patraucean |
| Alëna Aksënova | Edward Loper | Martyna Płomecka | Virginia Aglietti |
| Anastasios Kementsietsi­dis | Ellie Pavlick | Mor Hazan Taege | William Cunningham |
| Arjun Narayanan | Evan Rosen | Nicholas Cain | William Isaac |
| Ashwin Vaswani | Georgi Karadzhov | Nico Duduta | Xin Liu |
| Bernd Bohnet | Jed McGiffin | Rasmi Elasmar | Yao Yan |
| Chrysovalantis Anastasiou | Joe Heyward | Reut Aharony | Yuan Yuan |
| Claire Yao | Julia Haas | Rivka Moroshko | |
| Daniel McDuff | Kartikeya Badola | Silvia Chiappa | |
| Laura Kampis | Kate Lin | Steve Zheng | |
| | | Vik Sharma | |

本项工作凝聚了 Google 众多人员的贡献，包括研究人员、工程师和运营人员。我们对每位贡献者在这项工作中所付出的专注与努力深表感谢。贡献者按字母顺序排列。

我们对来自 Dharshan Kumaran、Joel Z Leibo、Ellie Pavlick、Mike Mozer、Martin Chadwick、Zoubin Ghahramani、Rohin Shah、Iason Gabriel、Lucy Cheke 和 Jose Hernandez-Orallo 的宝贵反馈深表感激。

---

## 7. 附录：认知分类体系

### 7.1 感知（Perception）

从世界中接收和处理感官信息（如图像、音频和文本）的能力（Harris and Smith，2022）。感知使系统能够观察环境并对其特征作出响应。³ 我们按感官通道对本节进行组织，并在相关通道中包含语言处理的相关方面。

> ³ 输入通道高度依赖于系统特性。一个系统可能不需要感知所有通道就能表现出智能行为，尽管每增加一个感知通道都可能提供一些有益信息。

#### 7.1.1 视觉感知

从光线中接收和处理视觉信息的能力（Cornsweet，1970；Haber and Hershenson，1973）。

**低级视觉感知** 检测和识别视觉信息表层特征（如光照强度、颜色和对比度）的能力。⁴

> ⁴ 这里，我们将涉及"表层"处理且几乎不需要语义解读的能力归类为低级感知。反之，需要更深层语义处理的能力归类为高级视觉感知。这是因为有证据表明，在人类中，高级和低级感知处理可以相互分离（如 Farah，1990）。不过，两者之间的分界线有些模糊——感知能力呈现从几乎不需要语义处理（如对比度检测）到高度依赖语义处理（如场景理解）的连续谱。

- **光照检测**：检测视觉场景不同部分亮度的能力（Gilchrist et al.，1999）。
- **对比度（边缘）检测**：检测图像中明暗区域之间对比度的能力（Marr and Hildreth，1980）。对图像分割至关重要。
- **颜色检测**：区分图像中不同颜色的能力（Gegenfurtner，2003）。
- **深度感知**：识别视觉场景中物体距离的能力（Parker，2007）。
- **运动检测**：检测动态视觉场景中运动的能力（Borst and Egelhaaf，1989）。
- **形状检测**：识别和定位图像中简单形状的能力（Biederman，1987；Todd，2004）。

**高级视觉感知** 处理、解读和理解视觉信息语义含义的能力（Ullman，1996）。

- **物体识别**：识别和归类视觉场景中物体的能力（Riesenhuber and Poggio，2000）。
- **视觉空间定位**：确定视觉场景中物体空间位置的能力（Hollingworth，2007）。
- **视觉计数**：确定视觉场景中物体或实体数量的能力（Trick and Pylyshyn，1994）。
- **静态场景理解（图像理解）**：对静态视觉场景中出现的事件形成高层次理解的能力（Epstein and Baker，2019）。
- **动态场景理解（视频理解）**：对动态视觉场景中发生的事件形成高层次理解的能力（Zacks et al.，2010）。
- **词语分割**：在视觉场景中分割和识别字母与词语的能力（Norris，2013）。
- **阅读理解**：理解以视觉形式呈现的语言含义的能力（Kendeou et al.，2016）。⁵

> ⁵ 要展现阅读理解能力，系统需要掌握至少一种语言。学习新语言的能力涵盖在"学习"维度下，系统所掌握语言的数量是其语义记忆的一项功能。

#### 7.1.2 听觉感知

从声波中接收和处理听觉信息的能力（Warren，1982）。

**低级听觉感知** 提取听觉信息表层特征（如音量、音高和空间位置）的能力。

- **音量检测**：识别声音响度（音量）的能力（Fechner，1860）。
- **音高检测**：识别声音音高的能力（Oxenham，2012）。
- **声音辨别**：区分同时出现的听觉场景组成部分（如不同声音或说话者）的能力（Bizley and Cohen，2013）。
- **声源定位**：识别声音方向及其来源距离的能力（Blauert，1996）。
- **语音分割**：将连续声音信息流分割为独立词语的能力（Brent，1999）。
- **节奏感知**：识别声音信息中模式或节奏的能力（Grahn，2012）。

**高级听觉感知** 处理、解读和理解听觉信息的能力。

- **语音理解**：理解口语含义的能力（Diehl et al.，2004）。
- **说话者识别**：识别和区分个别说话者的能力（McDermott，2009）。
- **声音识别**：识别不同类型声音的能力。
- **听觉场景理解**：理解和解读听觉场景中发生事件的能力（Bregman，1994）。
- **听力理解**：理解以听觉形式呈现的语言含义的能力（Friederici，2002）。⁶

> ⁶ 如同阅读理解，要展现听力理解能力，系统需要掌握至少一种语言。学习新语言的能力涵盖在"学习"维度下，系统所掌握语言的数量是其世界知识的一项功能。

#### 7.1.3 文本感知

处理、解读和理解以文本形式呈现信息的能力。

与人类不同，人类只能通过其他感官通道感知文本（例如通过阅读感知视觉文字，或通过触摸感知盲文），今天的 AI 系统通过分词（tokenization）和嵌入（embedding）将文本作为完全独立的通道加以感知。这些过程与其他形式的感知处理一样存在缺陷和信息损耗（Shin and Kaneko，2024）——系统在拼写方面的困难（比如"strawberry"里到底有几个字母 r？）以及对文本输入扰动的脆弱性，都清晰地说明了这一点。

尽管文本感知并非人类严格意义上的基础能力，但文字信息在当今社会居于核心地位，也是当今系统学习理解语言和世界的重要途径。绕过视觉而直接感知基于文本的语言，是当今 AI 系统一项引人入胜且独特的属性。语言模型已证明，这种能力可以在一系列任务上带来出色的表现，因此值得关注和测量。当然，人类中缺乏直接对应物这一事实，引发了关于文本感知应如何纳入 AGI 判断的疑问。从某种意义上说，这种能力可以被视为阅读的"简化版"，无需将视觉信息分割为字母和词语。因此，我们认为 AGI 至少应能够以不低于人类以视觉形式阅读相同文本时的理解水平来理解给定文本。

**低级文本感知** 从文本输入中提取表层特征（如字母和词语）的能力。

- **符号辨别**：区分字符流中不同符号（如字母和数字）的能力。
- **词语分割**：将字符流分割为词语的能力。

**高级文本感知** 处理、解读和理解文本信息的能力。

- **语言理解**：理解以文本形式呈现的语言含义的能力（Traxler and Gernsbacher，2006）。
- **代码理解**：理解书面代码的含义和功能的能力。

#### 7.1.4 其他感知通道

人类或其他动物所具有的还有许多其他类型的感知，可能对 AI 系统具有实用价值。每增加一种感知通道，都很可能为系统提供一些有用的信息，帮助它们驾驭现实世界。例如，触觉（de Haan and Dijkerman，2020）、嗅觉（Stevenson，2009）和温度感知（Jung et al.，2023）对于专为协助烹饪或制造业而设计的系统来说都可能非常有用。然而，这些通道对智能行为的相对重要性目前尚不明确，因此在本分类体系的初始版本中，我们未对其进行详细收录。尽管如此，这些感知通道仍值得关注，无论是对构建新系统的研究人员，还是对构建模型评估的研究人员而言。

#### 7.1.5 多感官整合

将来自多个通道的信息整合在一起的能力。由于不同感知通道提供关于环境特征（如形状、位置、大小和运动速度）的互补信息，多感官整合有助于实现跨信息的联合处理、推理和规划（Zmigrod and Hommel，2013）。应针对每种通道组合分别测量这一能力。

### 7.2 生成（Generation）

产生输出（如文本、语音）或动作（如运动动作、计算机控制动作或工具调用）的能力。输出生成对系统有效沟通和完成任务的能力至关重要。

产生高质量输出的能力，至少可以部分地与决定产生何种输出的能力相分离（想象一个见解深刻但技巧欠佳的网球运动员，他可能正确判断了最佳击球方式，却未能将其付诸实施）。换言之，输出生成捕捉的是系统的**执行能力**，而非其进行推理和规划以确定尝试何种动作的能力。

#### 7.2.1 文本生成

产生文本输出的能力。在人类中，文本生成是间接的，通常通过运动动作（书写或打字）来实现，但在 AI 系统中，文本可以是直接输出。

**自然语言生成** 以文本形式生成自然语言的能力。在认知科学中通常被称为语言产出（Garrett，1988；Pickering and Garrod，2013）。

- **语法正确性**：产生语法正确句子的能力。
- **词汇选择**：选择适当词语以传达丰富含义的能力。

**代码生成** 生成结构和语法上正确代码的能力（关于讨论见 Fedorenko et al.，2019）。

#### 7.2.2 音频生成

产生音频输出（即声音）的能力。

**语音生成** 生成自然且富有表现力的语音的能力（Traxler and Gernsbacher，2006）。

- **清晰度**：清晰发音词语和音素的能力。
- **语法正确性**：产生语法正确句子的能力。
- **词汇选择**：选择适当词语以传达丰富含义的能力。
- **韵律控制**：控制语音节奏（如音高、重音、语速和语调）的能力。
- **情感表达**：通过韵律变化表达广泛情感的能力。

#### 7.2.3 动作生成

产生操控环境的动作的能力。

**运动控制** 控制躯体或机器人执行器的能力（Nishikawa et al.，2007）。

**计算机控制** 产生计算机控制动作（如按键和鼠标移动）的能力（Smith et al.，1999）。

**工具使用** 使用外部对象、系统或资源以辅助实现目标的能力（Baber，2003）。

#### 7.2.4 思维生成

产生可用于指导决策的内部思维的能力（Holyoak and Spellman，1993）。思维可以以语言形式、图像形式（类似于人类的视觉想象），或更抽象的形式呈现。

根据定义，思维是内在的，可能难以或无法被评估。然而，有意识的思维对人类问题解决至关重要，且有大量证据表明它在 AI 系统中也具有价值（Comanici et al.，2025；OpenAI，2024），因此评估系统思维的特征和质量几乎肯定会带来启示。

### 7.3 注意（Attention）

将认知资源集中于感知刺激、信息或思维的特定方面的能力（Styles，2006；Treisman，1969）。当系统面临复杂环境且认知资源有限时，这一能力至关重要。

在狭窄聚焦于当前目标重要信息（以避免分心）与保持对更广泛环境的警觉（以便在出现意外变化或刺激时能够响应）之间，需要保持微妙的平衡（Burgoyne and Engle，2020；Engle，2018）。

#### 7.3.1 注意容量

系统可以同时专注的信息量。这一容量对于不同通道或信息类型（如文本、图像、音频）可能有所不同（Cowan et al.，2005；Fritz et al.，2007）。

#### 7.3.2 选择性注意／注意控制

选择性关注与当前目标相关的信息、忽略与目标无关的信息的能力（Theeuwes，1991）。这种主动的、自上而下的注意形式对于有效的目标驱动行为非常重要，通常被视为一种执行功能。

**持续注意** 随时间保持对目标相关信息的专注的能力（Esterman and Rothlein，2019；Sarter et al.，2001）。

**感知抑制** 忽略令人分心的或与目标无关的感知信息的能力（Van Moorselaar and Slagter，2020）。

**注意转换** 主动将注意从一个位置或信息转移到另一个的能力（Brown and Tait，2016）。

#### 7.3.3 刺激驱动注意

注意以"自下而上"的方式被新刺激或环境变化所引导的能力（Awh et al.，2012；Katsuki and Constantinidis，2014）。这对于快速识别需要响应的情境转变至关重要。

### 7.4 学习（Learning）

通过经验、学习或指导获取新知识、技能或行为的能力。学习对系统适应新情境或环境变化的能力至关重要（Ginsburg and Jablonka，2010；Morand-Ferron，2017）。⁷ 下文列举了 AGI 应能运用的几种重要学习类型。

> ⁷ 对于当前许多系统而言，学习仅发生在训练期间或上下文内。然而，为实现真正稳健和自适应的行为，AI 系统应能够随时间学习（并保留）新知识和技能（例如作为持续学习过程的一部分）。

#### 7.4.1 概念形成

抽象对象、事件和想法的关键特征，以形成类别、概念、图式和脚本的能力（Bruner，1986；Gershman and Niv，2010；Goodman et al.，2008；Tenenbaum et al.，2011）。对泛化至关重要。

#### 7.4.2 联结学习

学习同时出现的事件、对象或刺激之间关系的能力（Shanks，1995）。

#### 7.4.3 强化学习（操作性条件反射）

基于特定动作或情境的后果（奖励和惩罚）进行学习的能力（Skinner，1963；Sutton et al.，1998）。

#### 7.4.4 观察性学习

通过观察他人执行技能或任务来学习的能力（Bandura，2008）。

#### 7.4.5 程序性学习

通过执行或练习来学习技能、动作模式或任务的能力（Cohen and Squire，1980）。⁸

> ⁸ 在人类中，程序性学习可以与学习事实和其他显性信息的能力相分离（Willingham et al.，1989）。

#### 7.4.6 语言学习

学习新的语言相关信息（如语法和词汇）的能力（Bates，1976；Chomsky，1965；Pinker，1994；Saffran，2003）。包括自然语言、编程语言以及工具使用框架。

### 7.5 记忆（Memory）

随时间跟踪信息的能力（Squire and Kandel，1999）。记忆与学习紧密相连——区别在于，学习侧重于新知识的获取，而记忆关注的是随时间维持这些知识的能力。评估记忆通常包括测试系统的既有知识，以及其存储和检索新习得信息的能力。系统记忆的质量可以从以下角度考量：系统能记住多少信息、信息可以被维持多长时间，以及记忆的准确程度。⁹

> ⁹ 大多数人类记忆研究侧重于理解大脑特有的记忆机制，如"长时记忆"和"短时记忆"。但这些机制是人类特有的，可能与 AI 系统无关。因此，我们认为重要的是对底层记忆实现保持不可知立场，专注于评估系统随时间跟踪信息的能力。

鉴于学习与记忆的紧密联系，在评估系统能力时，两者可能难以分离。然而，至少存在一些各自特有的失效模式。例如，在能够成功回忆已存储知识的情况下却无法更新语义知识，被视为学习失败；而对最初成功习得的信息随时间出现遗忘，则被视为记忆失败。

#### 7.5.1 语义记忆（世界知识）

跟踪与特定情节无关的事实和其他通用信息的能力（Kumar，2021；Yee et al.，2013）。

**常识性知识** 关于世界基本规则、属性和特征的知识。包括：

- 通用知识
- 因果知识
- 时间知识
- 空间知识
- 直觉物理知识

**领域知识** 关于特定主题或领域的专业知识（Ericsson et al.，2018）。例如：

- 语言学知识
- STEM 知识
- 编程知识
- 法律知识
- 金融知识
- 医学知识
- 历史知识
- 社会文化知识

#### 7.5.2 情景记忆

跟踪与特定事件相关信息（包括与这些事件关联的感官信息，如图像、声音等）的能力（Conway，2009；Tulving et al.，1972）。¹⁰

> ¹⁰ 记忆感官信息的能力有时与记忆特定事件事实细节的能力相分离。这些事件记忆方面之间的关系是复杂的，因此出于实用目的，我们用情景记忆同时指代两者。

**感官记忆** 跟踪特定事件感官信息（如视觉、听觉或嗅觉信息）的能力。

**时间记忆** 跟踪事件之间序列和时间关系的能力。

**空间记忆** 跟踪特定事件中物体空间关系（如位置、方向和运动）的能力。

#### 7.5.3 程序性记忆

跟踪执行技能所需动作和输出模式的能力（Cohen and Squire，1980）。

#### 7.5.4 前瞻性记忆

记住在特定线索出现时执行计划动作的能力，例如某个时间节点或特定事件的响应（如"当我去商店时，我应该记得买牛奶"；McDaniel and Einstein，2007）。

#### 7.5.5 遗忘

从记忆中移除过时、错误或无关信息的能力。这可能涉及信息压缩或对特定记忆的整体删除。遗忘对于高效存储和检索至关重要（Bjork，1989）。

### 7.6 推理（Reasoning）

通过运用逻辑原则或进行推断得出有效结论的能力（Leighton and Sternberg，2003；Rips，1990）。通常，自动模式匹配不被视为推理。

#### 7.6.1 演绎（逻辑）推理

从一组前提、规则或事实推导得出合乎逻辑结论的能力（Johnson-Laird，1999）。演绎的一个决定性特征是缺乏歧义——只要可以确定前提为真，正确运用演绎推理得出的结论就是确定的。演绎要求掌握逻辑概念，如否定、"AND"、"OR"、"XOR"和"ALL"。

#### 7.6.2 归纳推理

基于一组特定事实、信息或观察得出普遍性结论的能力（例如，"迄今为止太阳每天都在升起；因此，明天太阳也将升起"）。

与演绎推理不同，这些普遍性结论是概率性的，并非确定的。因此，归纳推理有时会将我们引入歧途。然而，在充满不确定性的世界中，归纳推理对于避免持续陷入瘫痪不可或缺（Heit，2000）。

#### 7.6.3 溯因推理

对一组观察结果的最佳或最可能解释进行推断的能力。与归纳推理相似，溯因推理也是不确定的。溯因的关键特征是，它涉及生成新的解释性假设，而不仅仅是从一组观察中进行泛化（Bhagavatula et al.，2020）。

#### 7.6.4 类比推理

识别情境或概念之间相似性，并利用这些相似性基于一者的已知信息得出关于另一者未知属性结论的能力（Alexander et al.，2016；Gentner and Maravilla，2018）。

#### 7.6.5 数学推理

执行数学计算和运算的能力（Gilmore et al.，2018）。包括基础算术和代数。

### 7.7 元认知（Metacognition）

系统对自身认知过程的了解，以及监控和控制这些过程的能力（Dunlosky and Metcalfe，2009；Tarricone，2011）。

#### 7.7.1 元认知知识

元认知知识是系统关于自身能力、局限、知识、学习过程和行为倾向的自我认识（Flavell，1979；Tarricone，2011）。从某种意义上说，元认知知识可以简单地被视为世界知识的一个特殊情形。

**对局限的认识** 对自身能力和局限的认识（Fleming and Daw，2017；Fleming and Lau，2014）。

**对学习过程的认识** 对自身学习过程以及能够辅助或妨碍学习的因素的认识（Binz et al.，2024；Wang，2021）。

**元记忆（对知识的认识）** 关于记忆中存储的信息以及存储或检索这些信息所涉及过程的认识（Nelson，1990）。

**对行为模式的认识** 对自身倾向和行为模式的认识（Grant，2001；Vazire and Carlson，2010）。

#### 7.7.2 元认知监控

监控认知过程状态（如评估学习状态或当前表现）的能力（Dunlosky and Metcalfe，2009；Nelson，1990）。

**置信度校准** 准确估计动作成功或响应正确概率的能力（Fleming and Lau，2014；Harvey，1997；Yeung and Summerfield，2012）。

**学习判断** 在学习新信息时监控进展的能力（Arbuckle and Cuddy，1969；Rhodes，2016）。

**错误监控** 注意到错误发生的能力（Yeung and Summerfield，2012）。

**来源判断** 判断一条信息是从何处产生或习得的能力（Johnson et al.，1993；Mitchell and Johnson，2000）。

#### 7.7.3 元认知控制

模型利用元认知知识和监控的洞察，调整认知过程或策略的能力（例如，基于所犯错误的类型切换学习策略；Botvinick，2007；Nelson，1990；Son and Schwartz，2002）。有时被视为一种执行功能。

**错误纠正** 调整动作模式或策略以纠正错误的能力（Metcalfe，2017）。

**学习策略选择** 基于元记忆和学习判断选择适当学习策略的能力（如终止对已充分学习信息的学习，转而专注于尚未充分学习的信息）（Dunlosky et al.，2013）。

### 7.8 执行功能（Executive functions）

通过调节和统筹思维与行动，实现目标导向行为的高阶认知能力（Diamond，2013）。

#### 7.8.1 目标设定与维持

为组织和引导行动而设定并维持目标的能力（Buschman and Miller，2014；Dickinson and Balleine，1994）。

#### 7.8.2 规划

制定未来行动序列以实现特定目标的能力（Owen，1997）。规划是解决多步骤或长期问题的关键环节。规划过程可以广义地理解为构建（并剪枝）某种决策树（Mattar and Lengyel，2022）。

#### 7.8.3 抑制控制

改变、抑制或压制已习得或习惯性反应，转而采用更受控制、更符合目标的反应的能力（Bari and Robbins，2013；Miyake et al.，2000）。

#### 7.8.4 认知灵活性

在不同任务、概念或思维方式之间切换的能力（Braem and Egner，2018）。

#### 7.8.5 冲突解决

管理和解决相互冲突的信息、矛盾的目标或竞争性反应以选择适当行动的能力（Botvinick et al.，2001；Veen and Carter，2006）。不应与社会冲突解决相混淆。

#### 7.8.6 工作记忆

在服务于目标的过程中，在内部操作信息的能力（例如，在解决问题时执行中间计算，或在脑海中旋转图像以从不同角度审视它）（Baddeley，1992）。尽管名称暗示这一能力是记忆的子集，但工作记忆实际上涉及包括记忆、注意，有时还包括推理在内的多种能力的协调（Engle，2002）。

### 7.9 问题解决（Problem solving）

顾名思义，这一广泛能力指的是解决问题和克服障碍的能力（Mayer and Wittrock，2006）。这是一种复合能力，严重依赖于规划、推理和上下文内学习。问题解决需要：

- 理解和表征问题（如通过感知和抽象）
- 识别和检索相关知识（如事实、类似情境、关于有效解题策略的元知识）
- 将问题分解为子目标
- 规划行动序列
- 执行计划（如通过推理和输出生成）

列举人类能够解决的所有问题类型是不可能的，但下文描述了几种重要类型。

#### 7.9.1 流体推理

识别模式并将其应用于解决新颖问题的能力。依赖于演绎、归纳和溯因推理的组合（Cattell，1943；Kent，2017）。

#### 7.9.2 数学问题解决

运用数学概念和技术解决问题（Schoenfeld，1985）。

#### 7.9.3 算法问题解决

使用算法技术解决逻辑问题——编写代码的关键组成部分。

#### 7.9.4 常识性问题解决

通过应用通用知识和对世界的日常理解解决现实世界问题（Brachman and Levesque，2022）。

**时间问题解决** 理解和推理时间概念，如事件的顺序和持续时间、基于时间的关系和时间约束。

**空间问题解决** 推理空间中物体之间的关系，包括其位置、方向和运动。

**因果问题解决** 推理事件或实体之间的因果关系。

**直觉物理** 推理基本物理原理和物体在世界中的行为方式。包括以下概念：

- 物体恒存性
- 重力
- 动量
- 力

#### 7.9.5 知识发现

产生新颖假设、实验和科学问题解决方案的能力（Dunbar，2001；Klahr，2000；Nersessian，2002）。

### 7.10 社会认知（Social cognition）

处理和解读社会信息并在社会情境中做出适当回应的能力。对于与人类或其他系统互动至关重要（Higgins and Bargh，1987）。

#### 7.10.1 社会感知

根据面部表情、语调或肢体语言等感知信息解读社会线索的能力（Tajfel，1962）。

#### 7.10.2 心智理论（Theory of mind）

推理他人心理状态（包括信念、欲望、情感、意图、期望和视角）的能力。心智理论对于预测和解释他人行为的能力至关重要（Frith and Frith，2005；Leslie et al.，2004）。

#### 7.10.3 社会技能

识别、理解并根据社会规范或期望行事的能力（Chung and Rimal，2016）。

**合作** 与他人共同追求共同目标的能力（Rand and Nowak，2013）。

**谈判** 与目标不一致或存在冲突的他人协同工作的能力（Bazerman et al.，2000）。

**欺骗** 通过隐藏或掩盖意图或行为来误导他人以实现目标的能力（Spence et al.，2004）。根据情境不同，这可能被视为一种有害能力。

**说服** 影响他人态度、信念或行为的能力（Wood，2000）。根据情境不同，这可能被视为一种有害能力。

---

## 参考文献

- Alexander, P. A., Dumas, D., Grossnickle, E. M., List, A., & Firetto, C. M. (2016). Measuring relational reasoning. *The Journal of Experimental Education*, 84(1), 119–151. https://doi.org/10.1080/00220973.2014.963216
- Arbuckle, T. Y., & Cuddy, L. L. (1969). Discrimination of item strength at time of presentation. *Journal of experimental psychology*, 81(1), 126.
- Awh, E., Belopolsky, A. V., & Theeuwes, J. (2012). Top-down versus bottom-up attentional control: A failed theoretical dichotomy. *Trends in cognitive sciences*, 16(8), 437–443.
- Baber, C. (2003). *Cognition and tool use: Forms of engagement in human and animal use of tools*. CRC Press.
- Baddeley, A. (1992). Working memory. *Science*, 255(5044), 556.
- Bandura, A. (2008). Observational learning. In *The international encyclopedia of communication*. Wiley Online Library.
- Bari, A., & Robbins, T. W. (2013). Inhibition and impulsivity: behavioral and neural basis of response control. *Progress in neurobiology*, 108, 44–79.
- Bates, E. (1976). *Language and context: The acquisition of pragmatics*. Academic Press.
- Bazerman, M. H., Curhan, J. R., Moore, D. A., & Valley, K. L. (2000). Negotiation. *Annual review of psychology*, 51(1), 279–314.
- Bhagavatula, C., Bras, R. L., Malaviya, C., Sakaguchi, K., Holtzman, A., Rashkin, H., ... & Choi, Y. (2020). Abductive commonsense reasoning. arXiv:1908.05739.
- Biederman, I. (1987). Recognition-by-components: a theory of human image understanding. *Psychological review*, 94(2), 115.
- Binz, M., Dasgupta, I., Jagadish, A. K., Botvinick, M., Wang, J. X., & Schulz, E. (2024). Meta-learned models of cognition. *Behavioral and Brain Sciences*, 47, e147.
- Bizley, J. K., & Cohen, Y. E. (2013). The what, where and how of auditory-object perception. *Nature Reviews Neuroscience*, 14(10), 693–707. https://doi.org/10.1038/nrn3565
- Bjork, R. A. (1989). Retrieval inhibition as an adaptive mechanism in human memory. In *Varieties of memory and consciousness* (pp. 309–330). Lawrence Erlbaum Associates.
- Blauert, J. (1996). *Spatial Hearing: The Psychophysics of Human Sound Localization*. The MIT Press. https://doi.org/10.7551/mitpress/6391.001.0001
- Boden, M. A. (1994). What is creativity? In M. A. Boden (Ed.), *Dimensions of Creativity* (pp. 75–117). The MIT Press.
- Borst, A., & Egelhaaf, M. (1989). Principles of visual motion detection. *Trends in neurosciences*, 12(8), 297–306.
- Botvinick, M. M. (2007). Conflict monitoring and decision making: reconciling two perspectives on anterior cingulate function. *Cognitive, Affective, & Behavioral Neuroscience*, 7(4), 356–366.
- Botvinick, M. M., Braver, T. S., Barch, D. M., Carter, C. S., & Cohen, J. D. (2001). Conflict monitoring and cognitive control. *Psychological review*, 108(3), 624.
- Brachman, R. J., & Levesque, H. J. (2022). *Machines like Us: Toward AI with Common Sense*. The MIT Press. https://doi.org/10.7551/mitpress/14299.001.0001
- Braem, S., & Egner, T. (2018). Getting a grip on cognitive flexibility. *Current directions in psychological science*, 27(6), 470–476.
- Bregman, A. S. (1994). *Auditory scene analysis: The perceptual organization of sound*. MIT press.
- Brent, M. R. (1999). Speech segmentation and word discovery: A computational perspective. *Trends in Cognitive Sciences*, 3(8), 294–301.
- Brown, V. J., & Tait, D. S. (2016). Attentional Set-Shifting Across Species. In *Current Topics in Behavioral Neurosciences*, vol. 28 (pp. 363–395). Springer. https://doi.org/10.1007/7854_2015_5002
- Bruner, J. S. (1986). *A Study of Thinking* (2nd ed.). Routledge.
- Burgoyne, A. P., & Engle, R. W. (2020). Attention control: A cornerstone of higher-order cognition. *Current Directions in Psychological Science*, 29(6), 624–630.
- Buschman, T. J., & Miller, E. K. (2014). Goal-direction and top-down control. *Philosophical Transactions of the Royal Society B*, 369(1655), 20130471.
- Cattell, R. B. (1943). The measurement of adult intelligence. *Psychological bulletin*, 40(3), 153.
- Cheng, A., Jacovi, A., Globerson, A., et al. (2025). The facts leaderboard: A comprehensive benchmark for large language model factuality. arXiv:2512.10791.
- Cheng, P. W., & Holyoak, K. J. (1985). Pragmatic reasoning schemas. *Cognitive Psychology*, 17(4), 391–416.
- Chollet, F. (2019). On the measure of intelligence. arXiv:1911.01547.
- Chollet, F., Knoop, M., Kamradt, G., Landers, B., & Pinkard, H. (2025). Arc-agi-2: A new challenge for frontier ai reasoning systems. arXiv:2505.11831.
- Chomsky, N. (1965). *Aspects of the theory of syntax*. MIT Press.
- Chung, A., & Rimal, R. N. (2016). Social norms: a review. *Review of Communication Research*, 4, 1–28.
- Cohen, N. J., & Squire, L. R. (1980). Preserved learning and retention of pattern-analyzing skill in amnesia: Dissociation of knowing how and knowing that. *Science*, 210(4466), 207–210.
- Comanici, G., Bieber, E., Schaekermann, M., et al. (2025). Gemini 2.5: Pushing the frontier with advanced reasoning, multimodality, long context, and next generation agentic capabilities. arXiv:2507.06261.
- Conway, M. A. (2009). Episodic memories. *Neuropsychologia*, 47(11), 2305–2313.
- Cornsweet, T. N. (1970). *Visual Perception*. Academic Press.
- Cowan, N., Elliott, E. M., Saults, J. S., et al. (2005). On the capacity of attention: Its estimation and its role in working memory and cognitive aptitudes. *Cognitive psychology*, 51(1), 42–100.
- Danthiir, V., Roberts, R. D., Schulze, R., & Wilhelm, O. (2005). Mental speed: On frameworks, paradigms, and a platform for the future. In *Handbook of Understanding and Measuring Intelligence* (pp. 27–46). Sage Publications.
- Dasgupta, I., Lampinen, A. K., Chan, S. C. Y., et al. (2024). Language models show human-like content effects on reasoning tasks. arXiv:2207.07051.
- de Haan, E. H., & Dijkerman, H. C. (2020). Somatosensation in the brain: a theoretical re-evaluation and a new model. *Trends in Cognitive Sciences*, 24(7), 529–541.
- Diamond, A. (2013). Executive functions. *Annual review of psychology*, 64(1), 135–168.
- Dickinson, A., & Balleine, B. (1994). Motivational control of goal-directed action. *Animal learning & behavior*, 22(1), 1–18.
- Diehl, R. L., Lotto, A. J., & Holt, L. L. (2004). Speech perception. *Annu. Rev. Psychol.*, 55(1), 149–179.
- Dunbar, K. (2001). What scientific thinking reveals about the nature of cognition. In *Designing for science: Implications from everyday, classroom, and professional settings* (pp. 115–140). Lawrence Erlbaum Associates.
- Dunlosky, J., & Metcalfe, J. (2009). *Metacognition*. Sage Publications.
- Dunlosky, J., Rawson, K. A., Marsh, E. J., Nathan, M. J., & Willingham, D. T. (2013). Improving students' learning with effective learning techniques. *Psychological Science in the Public Interest*, 14(1), 4–58.
- Engle, R. W. (2002). Working memory capacity as executive attention. *Current directions in psychological science*, 11(1), 19–23.
- Engle, R. W. (2018). Working memory and executive attention: A revisit. *Perspectives on psychological science*, 13(2), 190–193.
- Epstein, R. A., & Baker, C. I. (2019). Scene perception in the human brain. *Annual review of vision science*, 5(1), 373–397.
- Ericsson, K. A., Hoffman, R. R., Kozbelt, A., & Williams, A. M. (Eds.). (2018). *The Cambridge Handbook of Expertise and Expert Performance* (2nd ed.). Cambridge University Press.
- Esterman, M., & Rothlein, D. (2019). Models of sustained attention. *Current opinion in psychology*, 29, 174–180.
- Farah, M. J. (1990). *Visual agnosia: disorders of object recognition and what they tell us about normal vision*. The MIT Press.
- Fechner, G. T. (1860). *Elemente der psychophysik* (Vol. 2). Breitkopf u. Härtel.
- Fedorenko, E., Ivanova, A., Dhamala, R., & Bers, M. U. (2019). The language of programming: A cognitive perspective. *Trends in Cognitive Sciences*, 23(7), 525–528.
- Flavell, J. H. (1979). Metacognition and cognitive monitoring: A new area of cognitive–developmental inquiry. *American psychologist*, 34(10), 906.
- Fleming, S. M., & Daw, N. D. (2017). Self-evaluation of decision-making: A general bayesian framework for metacognitive computation. *Psychological review*, 124(1), 91.
- Fleming, S. M., & Lau, H. C. (2014). How to measure metacognition. *Frontiers in human neuroscience*, 8, 443.
- Friederici, A. D. (2002). Towards a neural basis of auditory sentence processing. *Trends in cognitive sciences*, 6(2), 78–84.
- Frith, C., & Frith, U. (2005). Theory of mind. *Current biology*, 15(17), R644–R645.
- Fritz, J. B., Elhilali, M., David, S. V., & Shamma, S. A. (2007). Auditory attention—focusing the searchlight on sound. *Current opinion in neurobiology*, 17(4), 437–455.
- Garrett, M. F. (1988). Processes in language production. In *Language: Psychological and biological aspects* (pp. 69–96). Cambridge University Press.
- Gegenfurtner, K. R. (2003). Cortical mechanisms of colour vision. *Nature Reviews Neuroscience*, 4(7), 563–572.
- Gentner, D., & Maravilla, F. (2018). Analogical reasoning. In *The Routledge international handbook series* (pp. 186–203). Routledge.
- Gershman, S. J., & Niv, Y. (2010). Learning latent structure: carving nature at its joints. *Current opinion in neurobiology*, 20(2), 251–256.
- Gilchrist, A., Kossyfidis, C., Bonato, F., et al. (1999). An anchoring theory of lightness perception. *Psychological review*, 106(4), 795.
- Gilmore, C., Göbel, S. M., & Inglis, M. (2018). *An introduction to mathematical cognition*. Routledge.
- Ginsburg, S., & Jablonka, E. (2010). The evolution of associative learning: A factor in the cambrian explosion. *Journal of theoretical biology*, 266(1), 11–20.
- Goertzel, B., & Pennachin, C. (Eds.). (2007). *Artificial General Intelligence*. Springer Berlin. https://doi.org/10.1007/978-3-540-68677-4
- Goodman, N. D., Tenenbaum, J. B., Feldman, J., & Griffiths, T. L. (2008). A rational analysis of rule-based concept learning. *Cognitive science*, 32(1), 108–154.
- Grahn, J. A. (2012). Neural mechanisms of rhythm perception: current findings and future perspectives. *Topics in cognitive science*, 4(4), 585–606.
- Grant, A. M. (2001). Rethinking psychological mindedness: Metacognition, self-reflection, and insight. *Behaviour Change*, 18(1), 8–17.
- Gubrud, M. (1997). Nanotechnology and international security. *Fifth Foresight Conference on Molecular Nanotechnology*, November 1997.
- Haas, L., Yona, G., D'Antonio, G., Goldshtein, S., & Das, D. (2025). Simpleqa verified: A reliable factuality benchmark to measure parametric knowledge. arXiv:2509.07968.
- Haber, R. N., & Hershenson, M. (1973). *The psychology of visual perception*. Holt, Rinehart & Winston.
- Harris, J., & Smith, J. (2022). *Sensation and perception*. SAGE Publications Ltd.
- Harvey, N. (1997). Confidence in judgment. *Trends in cognitive sciences*, 1(2), 78–82.
- Heit, E. (2000). Properties of inductive reasoning. *Psychonomic bulletin & review*, 7(4), 569–592.
- Hendrycks, D., Song, D., Szegedy, C., et al. (2025). A definition of agi. pre-print.
- Higgins, E. T., & Bargh, J. A. (1987). Social cognition and social perception. *Annual review of psychology*, 38(1), 369–425.
- Hollingworth, A. (2007). Object-position binding in visual memory for natural scenes and object arrays. *Journal of Experimental Psychology: Human Perception and Performance*, 33(1), 31.
- Holyoak, K. J., & Spellman, B. A. (1993). Thinking. *Annual review of psychology*, 44(1), 265–315.
- Jacovi, A., Caciularu, A., Goldman, O., & Goldberg, Y. (2023). Stop uploading test data in plain text: Practical strategies for mitigating data contamination by evaluation benchmarks. arXiv:2305.10160.
- Johnson, M. K., Hashtroudi, S., & Lindsay, D. S. (1993). Source monitoring. *Psychological bulletin*, 114(1), 3.
- Johnson-Laird, P. N. (1999). Deductive reasoning. *Annual review of psychology*, 50(1), 109–135.
- Jung, J.-H., Seo, P. J., Oh, E., & Kim, J. (2023). Temperature perception by plants. *Trends in Plant Science*, 28(8), 924–940.
- Katsuki, F., & Constantinidis, C. (2014). Bottom-up and top-down attention: different processes and overlapping neural systems. *The Neuroscientist*, 20(5), 509–521.
- Kaufmann, G. (2003). What to measure? a new look at the concept of creativity. *Scandinavian Journal of Educational Research*, 47(3), 235–251.
- Kendeou, P., McMaster, K. L., & Christ, T. J. (2016). Reading comprehension: Core components and processes. *Policy Insights from the Behavioral and Brain Sciences*, 3(1), 62–69.
- Kent, P. (2017). Fluid intelligence: A brief history. *Applied Neuropsychology: Child*, 6(3), 193–203.
- Klahr, D. (2000). *Exploring science: The cognition and development of discovery processes*. MIT press.
- Kovacs, K., & Conway, A. R. (2016). Process overlap theory: A unified account of the general factor of intelligence. *Psychological Inquiry*, 27(3), 151–177.
- Kumar, A. A. (2021). Semantic memory: A review of methods, models, and current challenges. *Psychonomic bulletin & review*, 28(1), 40–80.
- Leighton, J. P., & Sternberg, R. J. (Eds.). (2003). *The Nature of Reasoning*. Cambridge University Press.
- Leslie, A. M., Friedman, O., & German, T. P. (2004). Core mechanisms in 'theory of mind'. *Trends in cognitive sciences*, 8(12), 528–533.
- Marr, D. (1982). *Vision: A Computational Investigation into the Human Representation and Processing of Visual Information*. Henry Holt and Co.
- Marr, D., & Hildreth, E. (1980). Theory of edge detection. *Proceedings of the Royal Society of London. Series B*, 207(1167), 187–217.
- Martínez-Plumed, F., Prudêncio, R. B., Martínez-Usó, A., & Hernández-Orallo, J. (2019). Item response theory in ai: Analysing machine learning classifiers at the instance level. *Artificial Intelligence*, 271, 18–42.
- Mattar, M. G., & Lengyel, M. (2022). Planning in the brain. *Neuron*, 110(6), 914–934.
- Mayer, R. E., & Wittrock, M. C. (2006). Problem solving. In *Handbook of Educational Psychology* (pp. 287–303). Lawrence Erlbaum Associates.
- Mazeika, M., Gatti, A., Menghini, C., et al. (2025). Remote labor index: Measuring ai automation of remote work. arXiv:2510.26787.
- McDaniel, M. A., & Einstein, G. O. (2007). *Prospective memory: An overview and synthesis of an emerging field*. Sage Publications.
- McDermott, J. H. (2009). The cocktail party problem. *Current Biology*, 19(22), R1024–R1027.
- Metcalfe, J. (2017). Learning from errors. *Annual review of psychology*, 68(1), 465–489.
- Mitchell, K. J., & Johnson, M. K. (2000). Source monitoring: Attributing mental experiences. In *The Oxford handbook of memory* (pp. 179–195). Oxford University Press.
- Miyake, A., Friedman, N. P., Emerson, M. J., et al. (2000). The unity and diversity of executive functions and their contributions to complex "frontal lobe" tasks. *Cognitive psychology*, 41(1), 49–100.
- Morand-Ferron, J. (2017). Why learn? the adaptive value of associative learning in wild populations. *Current opinion in behavioral sciences*, 16, 73–79.
- Morris, M. R., Sohl-Dickstein, J., Fiedel, N., et al. (2024). Position: Levels of agi for operationalizing progress on the path to agi. *Forty-first International Conference on Machine Learning*.
- Morris, M. R., Altman, D., Belfield, H., et al. (2026). Characterizing model jaggedness supports safety and usability. *Google DeepMind Technical Report*. https://cs.stanford.edu/~merrie/papers/jaggedness_preprint.pdf
- Nelson, T. O. (1990). Metamemory: A theoretical framework and new findings. In *The Psychology of Learning and Motivation*, vol. 26 (pp. 125–173). Academic Press.
- Nersessian, N. (2002). The cognitive basis of model-based reasoning in science. *The Cognitive Basis of Science*. https://doi.org/10.1017/CBO9780511613517.008
- Nishikawa, K., Biewener, A. A., Aerts, P., et al. (2007). Neuromechanics: an integrative approach for understanding motor control. *Integrative and Comparative Biology*, 47(1), 16–54.
- Norris, D. (2013). Models of visual word recognition. *Trends in cognitive sciences*, 17(10), 517–524.
- OpenAI. (2024). Learning to Reason with LLMs. https://openai.com/index/learning-to-reason-with-llms/
- Owen, A. M. (1997). Cognitive planning in humans: neuropsychological, neuroanatomical and neuropharmacological perspectives. *Progress in neurobiology*, 53(4), 431–450.
- Oxenham, A. J. (2012). Pitch perception. *Journal of Neuroscience*, 32(39), 13335–13338.
- Parker, A. J. (2007). Binocular depth perception and the cerebral cortex. *Nature Reviews Neuroscience*, 8(5), 379–391.
- Patraucean, V., Smaira, L., Gupta, A., et al. (2023). Perception test: A diagnostic benchmark for multimodal video models. *Advances in Neural Information Processing Systems*, 36, 42748–42761.
- Patwardhan, T., Dias, R., Proehl, E., et al. (2025). Gdpval: Evaluating ai model performance on real-world economically valuable tasks. arXiv:2510.04374.
- Phan, L., Gatti, A., Han, Z., et al. (2025). Humanity's last exam. arXiv:2501.14249.
- Pickering, M. J., & Garrod, S. (2013). An integrated theory of language production and comprehension. *Behavioral and Brain Sciences*, 36(4), 329–347.
- Pinker, S. (1994). *The Language Instinct: The New Science of Language and Mind*. William Morrow and Company.
- Rand, D. G., & Nowak, M. A. (2013). Human cooperation. *Trends in cognitive sciences*, 17(8), 413–425.
- Rhodes, M. G. (2016). Judgments of learning: Methods, data, and theory. In *The Oxford Handbook of Metamemory* (pp. 65–80). Oxford University Press.
- Riesenhuber, M., & Poggio, T. (2000). Models of object recognition. *Nature neuroscience*, 3(11), 1199–1204.
- Rips, L. J. (1990). Reasoning. *Annual review of psychology*, 41, 321–353.
- Romero-Alvarado, D., Martínez-Plumed, F., Pacchiardi, L., et al. (2026). Capabilities ain't all you need: Measuring propensities in ai. arXiv:2602.18182.
- Saffran, J. R. (2003). Statistical language learning: Mechanisms and constraints. *Current directions in psychological science*, 12(4), 110–114.
- Sarter, M., Givens, B., & Bruno, J. P. (2001). The cognitive neuroscience of sustained attention: where top-down meets bottom-up. *Brain research reviews*, 35(2), 146–160.
- Schoenfeld, A. (1985). *Mathematical Problem Solving*. Academic Press.
- Shanks, D. R. (1995). *The psychology of associative learning* (Vol. 13). Cambridge University Press.
- Shin, A., & Kaneko, K. (2024). Large language models lack understanding of character composition of words. arXiv:2405.11357.
- Skinner, B. F. (1963). Operant behavior. *American psychologist*, 18(8), 503.
- Smith, M. W., Sharit, J., & Czaja, S. J. (1999). Aging, motor control, and the performance of computer mouse tasks. *Human Factors*, 41(3), 389–396.
- Son, L. K., & Schwartz, B. L. (2002). The relation between metacognitive monitoring and control. In *Applied metacognition* (pp. 15–38). Cambridge University Press.
- Spence, S. A., Hunter, M. D., Farrow, T. F. D., et al. (2004). A cognitive neurobiological account of deception: evidence from functional neuroimaging. *Philosophical Transactions of the Royal Society of London. Series B*, 359(1451), 1755–1762.
- Squire, L. R., & Kandel, E. R. (1999). *Memory: from mind to molecules*. Scientific American Library.
- Stainton, R. J. (Ed.). (2006). *Contemporary Debates in Cognitive Science*. Wiley-Blackwell.
- Sternberg, R. J., & Lubart, T. I. (1998). The Concept of Creativity: Prospects and Paradigms. In *Handbook of Creativity* (pp. 3–15). Cambridge University Press.
- Stevenson, R. J. (2009). An initial evaluation of the functions of human olfaction. *Chemical Senses*, 35(1), 3–20.
- Styles, E. (2006). *The psychology of attention*. Psychology Press.
- Sutton, R. S., Barto, A. G., et al. (1998). *Reinforcement learning: An introduction* (Vol. 1). MIT press.
- Tajfel, H. (1962). Social perception. In *Social Psychology Through Experiment* (pp. 20–54). Methuen.
- Tarricone, P. (2011). *The taxonomy of metacognition*. Psychology press.
- Taubenfeld, A., Gekhman, Z., Nezry, L., et al. (2026). Evaluating alignment of behavioral dispositions in llms. arXiv:2602.11328.
- Tenenbaum, J. B., Kemp, C., Griffiths, T. L., & Goodman, N. D. (2011). How to grow a mind: Statistics, structure, and abstraction. *Science*, 331(6022), 1279–1285.
- Theeuwes, J. (1991). Exogenous and endogenous control of attention: The effect of visual onsets and offsets. *Perception & psychophysics*, 49(1), 83–90.
- Todd, J. T. (2004). The visual perception of 3d shape. *Trends in cognitive sciences*, 8(3), 115–121.
- Traxler, M. J., & Gernsbacher, M. A. (Eds.). (2006). *Handbook of Psycholinguistics* (2nd ed.). Academic Press.
- Treisman, A. M. (1969). Strategies and models of selective attention. *Psychological review*, 76(3), 282.
- Trick, L. M., & Pylyshyn, Z. W. (1994). Why are small and large numbers enumerated differently? *Psychological Review*, 101(1), 80–102.
- Tulving, E., et al. (1972). Episodic and semantic memory. In *Organization of memory* (pp. 381–403). Academic Press.
- Ullman, S. (1996). *High-Level Vision: Object Recognition and Visual Cognition*. The MIT Press.
- Van Moorselaar, D., & Slagter, H. A. (2020). Inhibition in selective attention. *Annals of the New York Academy of Sciences*, 1464(1), 204–221.
- Vazire, S., & Carlson, E. N. (2010). Self-knowledge of personality: Do people know themselves? *Social and personality psychology compass*, 4(8), 605–620.
- Veen, V. v., & Carter, C. S. (2006). Conflict and cognitive control in the brain. *Current Directions in Psychological Science*, 15(5), 237–240.
- Wang, J. X. (2021). Meta-learning in natural and artificial intelligence. *Current Opinion in Behavioral Sciences*, 38, 90–95.
- Warren, R. M. (1982). *Auditory Perception*. Pergamon.
- Willingham, D. B., Nissen, M. J., & Bullemer, P. (1989). On the development of procedural knowledge. *Journal of experimental psychology: learning, memory, and cognition*, 15(6), 1047.
- Wood, W. (2000). Attitude change: Persuasion and social influence. *Annual review of psychology*, 51(1), 539–570.
- Yee, E., Chrysikou, E. G., & Thompson-Schill, S. L. (2013). Semantic memory. In *The Oxford Handbook of Cognitive Neuroscience, Volume 1: Core Topics*. Oxford University Press.
- Yeo, B. T., Krienen, F. M., Sepulcre, J., et al. (2011). The organization of the human cerebral cortex estimated by intrinsic functional connectivity. *Journal of neurophysiology*.
- Yeung, N., & Summerfield, C. (2012). Metacognition in human decision-making: confidence and error monitoring. *Philosophical Transactions of the Royal Society B*, 367(1594), 1310–1321.
- Zacks, J. M., Speer, N. K., Swallow, K. M., & Maley, C. J. (2010). The brain's cutting-room floor: Segmentation of narrative cinema. *Frontiers in human neuroscience*, 4, 168.
- Zmigrod, S., & Hommel, B. (2013). Feature integration across multimodal perception and action: a review. *Multisensory research*, 26(1-2), 143–157.
