# Google AlphaEvolve GA 中文译读

> 原文：Google Cloud, "Solve harder problems with AlphaEvolve, now available to everyone on Google Cloud"  
> 链接：https://cloud.google.com/blog/products/ai-machine-learning/alphaevolve-is-available-for-everyone  
> 说明：本文为版权合规的中文译读，完整覆盖原文主要事实、结构和论点，但不逐段复刻原文表达。

---

## 核心发布

Google Cloud 宣布，AlphaEvolve 已在 Gemini Enterprise Agent Platform 上正式面向所有客户开放。AlphaEvolve 是一个基于 Gemini 的代码优化和算法发现 agent，目标是帮助企业和研究机构解决传统方法难以处理的大规模优化问题。

Google 将这类问题描述为现实世界中最有挑战、也最有价值的问题之一：芯片设计、配送网络规划、大模型训练架构、高性能计算、基因组学、金融预测、供应链优化等场景，都需要在极大的算法和实现空间中寻找更优解。传统人工编码方法往往无法充分探索这些可能性。

AlphaEvolve 去年以私有预览形式推出，现在进入 GA。Google 表示，该系统已经在早期访问计划中覆盖物流、半导体、基因组学、高性能计算和金融服务等多个领域。

## AlphaEvolve 如何工作

Google 把 AlphaEvolve 的使用流程概括为四步：

1. **Define**：用户提供基准 seed algorithm、问题定义，以及与问题相关的背景知识。
2. **Measure**：用户建立评分函数，用来客观评价候选程序。评分可以围绕正确性、性能、业务约束或其他指标。
3. **Optimize**：AlphaEvolve 的 agentic harness 生成候选代码，并围绕评分函数持续优化。
4. **Apply**：用户把通过验证的优化算法部署到生产工作负载和基础设施中。

这个流程的关键在于，AlphaEvolve 并不只是生成代码建议，而是把候选程序放进一个可执行、可评分的实验回路中。只要评价函数定义清楚，系统就能不断产生候选实现、运行测试、比较结果，并把搜索集中到更有希望的方向。

## 企业和研究案例

Google 在文章中列举了多个组织的使用案例，展示 AlphaEvolve 如何从研究项目走向真实业务和科研工作流。

### BASF：供应链数字孪生

BASF 使用 AlphaEvolve 构建复杂供应链网络的数字孪生。Google 引述 BASF 表示，传统确定性模型多次尝试失败，而 AlphaEvolve 帮助他们基于系统数据映射复杂网络，并捕捉人工日常决策逻辑，从而形成更准确、易维护的数据驱动数字孪生。

### Coolblue：电商需求预测

Coolblue 的数据科学团队把 AlphaEvolve 用于 28 天需求预测管线，重点优化特征工程、目标预处理和模型选择。Google 称，在约 200 次迭代中，AlphaEvolve 让生产预测的 WMAPE 指标相对既有方案下降超过 5%，并通过同时关注短期和完整 28 天窗口来改善库存可用性。

### FM Logistic：仓库路径优化

FM Logistic 用 AlphaEvolve 和 Gemini 优化仓库快速作业的路径规划。Google 称，该项目在一个已经高度优化的 baseline 上进一步提升 10.4%，对应更快履约、更好的工作条件，以及更低的车队磨损。

### Infineon：芯片设计

Infineon 表示，早期实验显示 AlphaEvolve 有潜力改变芯片设计生命周期，并可能参与 surrogate modelling 等多个开发阶段。

### JetBrains：IDE 性能

JetBrains 将 AlphaEvolve 用于复杂性能优化。Google 引述 JetBrains 表示，工程师仍然负责 benchmark、审查和发布决策，但 AlphaEvolve 可以把过去耗时太高、不常被探索的优化候选变成可常规测试的方案。

### Kinaxis：预测和优化系统

Kinaxis 研究人员使用 AlphaEvolve 改进成熟的预测和优化算法。Google 称，早期测试中，一些关键预测准确性指标提升超过 22%，同时在 benchmark 数据集上的运行时间降低超过 90%。

### Klarna：机器学习训练管线

Klarna 将 AlphaEvolve 用于大型 ML 训练管线，在受监管金融服务所需的严格可复现约束下，提升吞吐并改善模型质量。Google 称，系统在三周内探索了近 6000 个候选程序，发现了人工工程师通常不会尝试的深层架构重写。

### Kuro Games：服务端优化

Kuro Games 将 AlphaEvolve 用于复杂后端优化挑战，在特定服务端工作负载上获得显著性能提升。其观点是，AlphaEvolve 处理机器擅长的优化搜索，让工程师把精力更多放在游戏体验本身。

### ORNL：超算上的 GPU kernel 搜索

Oak Ridge National Laboratory 在 Google DeepMind Genesis Mission 合作背景下，把 AlphaEvolve 接入 Frontier 超级计算机。团队构建了闭环评估架构，把云端大语言模型代码生成与 Frontier 执行环境连接起来，用于优化混合精度 GPU kernel。该系统会生成、编译、运行和验证候选程序，并按数值准确性规则评价结构优化。

### Old Dominion University：生物衰老模型

Old Dominion University Qin Lab 用 AlphaEvolve 搜索建模生物衰老死亡率的 Python 程序空间。Google 称，系统在约 500 次评估中重新发现 Kannisto logistic mortality model，并通过异质衰减率分布提升 Emergent Aging Model 复合适应度，还表现出接近完美的 Strehler-Mildvan 相关性。

### PacBio：基因组测序准确性

PacBio 使用 AlphaEvolve 改进 DeepConsensus 相关工作流。Google 称，该方案帮助测序仪获得更高准确率，并将变异检测错误降低 30%。

### Pebble：GPU 推理性能建模

Pebble 用 AlphaEvolve 改进 NVIDIA AI Configurator 的延迟模型。Google 称，AlphaEvolve 自动发现了新的 GPU 性能建模公式，将模型相对误差降低 56%，帮助其更准确地映射硬件规格和推理配置。

### qBraid：量子计算

qBraid 用 AlphaEvolve 在已经长期优化过的编码家族之上继续搜索，找到更高效的量子化学纠错编码方案。Google 把它作为 AlphaEvolve 在超大设计空间中发现可读、可验证方案的例子。

### Schrodinger：分子模拟

Schrodinger 将 AlphaEvolve 用于加速分子发现相关模拟。Google 称，更快的 MLFF 推理可以缩短药物发现、催化剂设计和材料研发周期，让企业在几天内筛选分子候选，而不是几个月。

### Substrate：半导体仿真

Substrate 用 AlphaEvolve 优化 computational lithography 框架。Google 称，该项目带来多倍运行速度提升，使其能运行更大规模的先进半导体仿真。

### WPP：广告活动预测

WPP 研究团队使用 AlphaEvolve 自动提出、评估和改进候选模型架构，突破人工模型优化收益有限的问题。Google 称，WPP 在不同用例中取得 5% 到 10% 的预测准确率提升，以及最高 7% 的下游推荐分数提升。

## Google 自身基础设施与科学研究

Google 表示，AlphaEvolve 不只用于外部客户，也已经成为 Google 内部扩大基础设施优化和科学研究能力的重要引擎。

文章提到的内部成果包括：优化下一代 TPU 的硅设计；改进 Google Spanner 的 LSM compaction heuristics，将 write amplification 降低 20%；通过新的编译器优化策略减少近 9% 的软件存储占用；在 20 类自然灾害风险预测中提高预测准确性；在 Willow 量子处理器上发现错误率低 10 倍的量子线路。

Google Cloud 首席科学家、Google DeepMind 科学副总裁 Pushmeet Kohli 的观点是，AI 正在从提高工作效率的助手，转变为扩展人类能力边界的 discovery engine。AlphaEvolve 这类工具通过自主导航复杂计算搜索空间，帮助研究人员和工程师发现传统直觉之外的突破算法。

## 如何开始使用

Google 表示，开始使用 AlphaEvolve 需要两个核心输入：

1. **Seed program**：初始算法代码。用户指定哪些代码片段可以被优化，并交给 AlphaEvolve。
2. **Evaluator**：确定性的客户端评估脚本。它负责编译、测试和评分候选变体，并将一个或多个数值指标返回给 AlphaEvolve。

用户的客户端 runner 会向 AlphaEvolve API 请求 mutated candidate solutions，在本地或其他执行环境中运行 evaluator，然后把分数提交回 AlphaEvolve，供系统继续采样和优化。

Google 建议用户从官方文档、onboarding guide、GitHub 示例仓库、basic colab examples、best practices guide 和高级示例开始。对于 agentic workflows，Google 还提到可以在 Antigravity 或 Claude Code 等 IDE 中使用 AlphaEvolve Skill。

## 译读总结

AlphaEvolve 的核心意义不在于“又一个会写代码的模型”，而在于它把代码生成放进了可运行、可评分、可迭代的闭环。它要求用户先明确问题、baseline 和评价函数，然后让 agent 在候选实现空间中进行大规模搜索。

这代表企业 AI agent 的一个重要方向：当目标可以被可靠评估时，模型的价值不只是提供建议，而是持续发现更优方案。工程师的角色也随之变化，从直接手写每个优化变成设计问题边界、评价标准和上线流程。

---

*— Alice Larry, AI News Digest translation review*
