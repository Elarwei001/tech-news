# What Parameter Golf taught us

> 原文链接：[What Parameter Golf taught us](https://openai.com/index/what-parameter-golf-taught-us/)  
> 译文类型：AI 完整翻译  
> 日期：2026-05-18

我们推出 Parameter Golf，是为了吸引并支持机器学习研究社区探索一个新的、约束非常紧的机器学习问题。我们希望这个挑战足够有趣，能够奖励真正的技术创造力，同时又在概念上足够简单、容易验证。

参与者必须在固定的 FineWeb 数据集上最小化 held-out loss，同时遵守 16 MB artifact 限制，这个 artifact 包括模型权重和训练代码，并且训练预算是在 8×H100 上运行 10 分钟。我们提供了 baseline、数据集和评测脚本，让参与者可以 fork 仓库、改进模型，并通过 GitHub 提交结果。

在 8 周时间里，我们收到了来自 1,000 多名参与者的 2,000 多次提交。我们对这些提交展现出的技术广度、创造力和规则边缘探索印象很深，从细致的优化器调参和量化工作，到新的建模思路和 test-time training 都有覆盖。

这个挑战最令人兴奋的部分之一，是看到参与者多么广泛地使用 AI coding agents。Agent 帮助降低了实验成本，让更多人更容易参与，也改变了比赛节奏。它们同时也给提交审核、归因和评分带来了新的挑战。

这项挑战也成为一个有意义的人才发现表面。这是我们推出 Parameter Golf 的目标之一，而结果也表明，开放式技术挑战能够揭示出非凡的机器学习品味和坚持力。

在这篇文章中，我们重点介绍一些让我们觉得意外且有趣的提交，并分享我们在强大 AI agents 时代运行 coding contest 学到的东西。

## 技术观察

我们评审并独立复现了 record-track leaderboard 上的每一项提交，并验证每项提交在提交时确实打破了当时的记录。有几个主题很突出。

### 训练优化

一些最强结果来自对现有组件的细致调优。

| 提交 | 贡献者 | 技术 | 为什么重要 |
|---|---|---|---|
| [#60](https://github.com/openai/parameter-golf/pull/60) | @notapplica | 结合了 [#50](https://github.com/openai/parameter-golf/pull/50)、[#42](https://github.com/openai/parameter-golf/pull/42) 以及很可能还有 [#39](https://github.com/openai/parameter-golf/pull/39) 的已有胜出方案，然后通过 Muon weight decay、spectral embedding initialization、residual-mix scheduling 和 compiled evaluation 让一个更深的模型有效工作。 | 这是一个有纪律的 leaderboard 工作范例：识别哪些已有改进真正重要，并把它们干净地组合起来。 |

### 量化

有几项提交在压缩和导出方面推进得很深入。

| 提交 | 贡献者 | 技术 | 为什么重要 |
|---|---|---|---|
| [#414](https://github.com/openai/parameter-golf/pull/414) | @signalrush | 在训练后使用 GPTQ-lite 对权重进行量化。 | 这是第一个成功使用 GPTQ-lite 的 leaderboard 提交，带来了更好的评测结果。 |
| [#1060](https://github.com/openai/parameter-golf/pull/1060) | @dexhunter | 在 @raahilshah 的 [#634](https://github.com/openai/parameter-golf/pull/634) 基础上，成功使用 full Hessian GPTQ。 | 把早期量化工作扩展成更强的压缩路径。 |

### Test-time 和评测策略

一些提交推动了模型改进和评测策略之间的边界。这些方法在规则下是有效的，但作为组织者，我们需要仔细审查。

| 提交 | 贡献者 | 技术 | 为什么重要 |
|---|---|---|---|
| [#77](https://github.com/openai/parameter-golf/pull/77) | @samacqua | 使用 score-first、按文档执行的 LoRA test-time training：先评分，只在已经评分的 chunk 上适配，并在文档边界重置。 | 在规则内推动了模型改进与评测策略之间的边界，同时保持可审核。 |
| [#1019](https://github.com/openai/parameter-golf/pull/1019) | @abaybektursun | 使用自生成 GPTQ calibration：从训练后的模型生成校准文本，然后基于这些激活构建 GPTQ Hessians。 | 这是一种有创造力的校准策略，需要组织者仔细审查。 |

### 新的建模和数据思路

有几项提交引入了特别有创造力的建模或数据思路。

| 提交 | 贡献者 | 技术 | 为什么重要 |
|---|---|---|---|
| [#1729](https://github.com/openai/parameter-golf/pull/1729) | @romeerp | 引入 CaseOps tokenizer：使用无损 capitalization operator tokens，并用 original-byte BPB sidecar accounting。 | 这是一个有创造力的 tokenizer 和数据表示思路。 |
| [#265](https://github.com/openai/parameter-golf/pull/265) | @unnir | 引入 XSA，一种高效的 partial Exclusive Self Attention 方法，带有 GQA-aware grouped views。 | 把一种高效 attention 变体带入了挑战。 |
| [#65](https://github.com/openai/parameter-golf/pull/65) | @aquariouseworkman | 引入 SmearGate 和 BigramHash：一种 learned previous-token embedding blend，以及相邻 token pair 的 hash features。 | 从零增加了新的特征机制。 |
| [#1204](https://github.com/openai/parameter-golf/pull/1204) | @msisovic | 引入 mini depth recurrence：重复第 4 和第 5 层，推迟到训练中段再启用 recurrence，并对重复的 MLP 进行部分 untie。 | 这是第一个被接受进 leaderboard、并让 recurrent layers 有效工作的提交。 |

我们选择重点介绍这 9 项提交，是因为它们代表了我们希望这项挑战能够呈现出的成果范围。有些参与者通过细致调优找到改进；另一些人推进了量化和低秩技术；有些探索了评测规则的边缘；还有几项引入了来自文献或从零发明的建模与数据思路，并产生了意外收益。

nonrecord track 也有很多有创造力的提交。我们重点介绍了 15 个最喜欢的方案，其中的方法从非自回归文本建模到动态 tokenization 都有。

因为这个 track 更偏实验性，我们较少关注原始性能，而更关注方法在技术上是否有趣。有 3 项提交特别突出：

这些是我们最喜欢的 3 项 nonrecord 提交，尽管它们不一定是性能排名前三。

话虽如此，nonrecord track 的竞争依然激烈。半数 nonrecord leaderboard entries 超过了 1.22 BPB 的 naive baseline，而排名最高的提交达到了 1.12 BPB。

我们觉得这很令人鼓舞。即使面对强 transformer baselines，替代方法有时也能与主流架构相抗衡。

我们还认为，这个 track 尤其受益于强 coding agents 的可用性。Agent 让原型化投机性想法的成本低得多，包括那些过去在短期比赛中可能显得太耗时或太不确定、不值得尝试的方法。

## 收获

Parameter Golf 和早期类似比赛之间的一个主要差异，是 coding agents 的广泛使用。绝大多数提交者都提到他们在工作中使用了 agents。

这降低了参与门槛。参与者可以更快搭建实验、检查不熟悉的代码，并用更少阻力测试想法。RunPod 赞助的 1,000,000 美元 compute 也在让更多人能够参与这项挑战方面发挥了重要作用。

与此同时，agent 使用也给提交和评分带来了新问题。很多提交只是对已有 top scorers 的小改动，而不是根本上的新方法。这通常是有用的：强想法传播很快，并被其他人继续优化。但它也制造了噪音。当某些超出比赛指南的提交产生异常强的分数时，其他 agents 有时会复制这些想法，并沿着同一条无效路径继续前进。

提交量也改变了我们运行比赛的方式。我们不可能手动检查每一项提交，同时又让 leaderboard 保持更新。在挑战期间，我们开发了一个内部 Codex-based triage bot，用来监控新提交并标记需要人工审核的内容。在每天收到数百次提交的阶段，这一点尤其重要。

AI agents 也成为挑战社区的一部分。在比赛的大部分时间里，@notapplica 和他们的 coding agent 运行了一个 “Live Updates” bulletin，追踪重大事件、解释 leaderboard 方法，并帮助其他参与者跟上比赛进展。社区也出现了审核工具，帮助经验较少的参与者检查他们的提交是否符合规则，并避免常见的无效方法。

## 下一步是什么？

我们的主要目标，是推出一个让 [eligible participants](https://cdn.openai.com/pdf/d5caec5a-ee81-419d-b0d7-39f1424d819c/OpenAI%20Model%20Craft_%20Parameter%20Golf%20Challenge%20Terms%20and%20Conditions.pdf) 能够参与并体验机器学习研究的挑战。Parameter Golf 带来了范围广泛、技术扎实且富有创造力的提交，也让我们更清楚地看到，随着 AI agents 变得更强、更普及，开放研究竞赛可能会如何变化。

我们正在考虑未来推出更多类似挑战。如果你感兴趣，请填写 [challenge participant form](https://jobs.ashbyhq.com/openai/form/open-ai-challenge-parameter-golf)。
