# OpenAI《Previewing GPT-5.6 Sol: a next-generation model》中文译读

> 原文：OpenAI, "Previewing GPT-5.6 Sol: a next-generation model", 2026-06-26  
> 链接：https://openai.com/index/previewing-gpt-5-6-sol/  
> 说明：出于版权合规，本文件提供完整结构化译读与关键事实翻译，不逐字复刻原文全文。

---

## 核心发布

OpenAI 开始有限预览 GPT-5.6 系列。这个系列包括三个层级：

- **Sol**：旗舰模型，定位为 GPT-5.6 系列中最强能力版本。
- **Terra**：面向日常工作的平衡模型，OpenAI 称其性能可与 GPT-5.5 竞争，同时成本便宜 2 倍。
- **Luna**：快速、低成本模型，OpenAI 称其在最低成本层级提供强能力。

OpenAI 表示，GPT-5.6 Sol 是公司迄今最强模型之一，并配套使用其最稳健的安全栈。公司在发布说明中把重点放在三个方向：能力提升、网络安全能力与防护、以及分阶段可用性和价格。

---

## 发布方式和政府沟通

OpenAI 表示，公司计划在未来数周让 GPT-5.6 Sol、Terra 和 Luna 更广泛可用。但在正式扩大之前，OpenAI 先启动有限预览，只面向一小组可信伙伴开放。

OpenAI 解释称，作为与美国政府持续沟通的一部分，公司在发布前预览了模型能力和发布计划。应政府要求，OpenAI 先从可信伙伴有限预览开始，并继续测试与协调，然后再推进更广泛发布。

OpenAI 同时强调，这种政府访问流程不应成为长期默认模式。公司认为，长期把最佳工具限制在少数人手中，会让需要这些能力的用户、开发者、企业、网络防御者和全球伙伴无法及时受益。因此，OpenAI 把这次安排描述为短期步骤，目标是在未来数周实现更广泛可用，同时与美国政府围绕 cyber Executive Order 框架和未来模型发布流程继续协调。

---

## 能力概览

OpenAI 称 GPT-5.6 Sol 是公司最强模型。为了预览模型表现，OpenAI 分享了一组评估，重点展示 coding、biology 和 cybersecurity 中的 agentic 能力提升。更完整的安全与 preparedness 评估则放在 system card 中。

GPT-5.6 还引入新的 `max` reasoning effort，让 Sol 有更多时间进行深度推理。与此同时，OpenAI 引入 `ultra` mode，通过 subagents 加速复杂任务，使其超出单个 agent 的能力边界。

在 coding 工作流中，OpenAI 称 GPT-5.6 Sol 在 Terminal-Bench 2.1 上达到新的 state of the art。该 benchmark 测试的是需要规划、迭代和工具协调的命令行工作流。

在 biology 工作流中，GPT-5.6 Sol 也显示出整体提升。OpenAI 提到，在 GeneBench v1 这类评估长程 genomics 和 quantitative-biology 分析的 benchmark 上，GPT-5.6 Sol 相比 GPT-5.5 取得更强结果，同时使用更少 token。

在 cybersecurity 方面，OpenAI 称 GPT-5.6 Sol 是其迄今最强 cyber 模型之一，并在 vulnerability research 和 exploitation 等长程安全任务上移动了 performance-efficiency frontier。

---

## 网络安全能力与防护

OpenAI 对 GPT-5.6 的 cyber 能力使用了谨慎表述。公司承认模型在安全任务上更强，但强调其目标是让正当防御工作受益，同时显著限制被禁止的攻击性使用。

OpenAI 表示，GPT-5.6 Sol 更擅长帮助人们发现并修复漏洞，而不是可靠地执行端到端攻击。公司认为，随着这类能力进步，关键是让防御者能够使用这些工具来发现弱点、开发补丁并强化系统。

根据 OpenAI 的 Preparedness Framework 评估，GPT-5.6 Sol 未跨过 Cyber Critical 阈值。在 Chromium 和 Firefox 相关评估中，模型能够识别 bug 和 exploitation primitives，也就是 exploit 的构建块，但在测试条件下没有自主产出一个功能完整的 full-chain exploit。

不过 OpenAI 也承认，benchmark 阈值无法覆盖模型可能被使用或与其他工具组合的所有方式。因此，模型能力提升带来的不确定性，是 OpenAI 同时加强防护并采用分阶段发布的原因。

---

## 分层安全栈

OpenAI 表示，没有任何单一防护足以抵挡有决心、会适应的滥用者。因此，在 GPT-5.6 预览期间，公司采用分层防护策略，并根据不同模型能力配置不同保护。

这些防护包括：

- 模型内部训练出的拒绝能力；
- 生成过程中的实时检查；
- 账号层级信号；
- 差异化访问；
- 监控和执行机制；
- 持续测试；
- 针对真实攻击压力的红队测试。

OpenAI 称，GPT-5.6 被训练为拒绝被禁止的 cyber assistance，包括用户试图伪装意图或越狱模型的情形。模型层面的防护是第一道边界，但不是唯一边界。

---

## 自动化红队和持续修复

OpenAI 表示，公司用自动化红队不断寻找模型和防护的弱点。相关测试不仅关注单次提示是否会绕过规则，也关注多轮对话、工作流和现实场景中的组合风险。

OpenAI 强调，任何评估都无法代表所有产品配置、多步骤攻击或真实工作流。因此，公司保留快速响应流程：当发现新的 jailbreak 或失败模式时，会复现、评估、排序、修复，并把相关样例加入持续评估，以便未来测试类似失败。

这部分内容说明，OpenAI 正在把模型安全看作一个持续运营系统，而不是发布前一次性检查。

---

## 可用性和价格

预览期间，GPT-5.6 模型会先通过 API 和 Codex 提供给精选可信伙伴和组织。OpenAI 计划之后很快扩展到 ChatGPT、Codex 和 API。

OpenAI 还介绍了新的命名体系：数字代表模型 generation，Sol、Terra 和 Luna 代表可独立演进的长期能力层级。OpenAI 的目标是让用户和开发者在智能、速度和成本之间有更清晰选择。

GPT-5.6 的价格按每 100 万 token 计算：

- **Sol**：输入 5 美元，输出 30 美元；
- **Terra**：输入 2.50 美元，输出 15 美元；
- **Luna**：输入 1 美元，输出 6 美元。

GPT-5.6 还引入更可预测的 prompt caching，包括显式 cache breakpoints 和 30 分钟最短 cache life。对 GPT-5.6 及后续模型，cache writes 按未缓存输入价格的 1.25 倍计费，cache reads 继续享受 cached-input 90% 折扣。

OpenAI 还表示，GPT-5.6 Sol 将于 7 月在 Cerebras 上以最高 750 tokens/second 的速度上线，初期面向精选客户开放，并随着容量扩展。

---

## 编辑观察

这篇发布说明最重要的地方，不是某一个 benchmark，而是 OpenAI 如何组织“前沿模型发布”这件事。

第一，模型发布正在被治理流程包围。OpenAI 不再只是说模型更强，而是同时说明政府沟通、可信伙伴、分阶段发布、网络安全防护和长期发布流程。

第二，cyber 能力已经成为前沿模型发布中的核心风险议题。OpenAI 一方面强调 GPT-5.6 Sol 对防御者有价值，另一方面必须详细解释它没有跨过 Cyber Critical 阈值，以及为什么仍需要更强 safeguard。

第三，模型商品化正在更细。Sol、Terra、Luna 是能力层级，也是成本层级；cache breakpoint、cache life 和 cache pricing 则服务于长程 agent 工作的成本可预测性。

第四，GPT-5.6 与 OpenAI 近期 Codex 研究可以放在一起理解。如果 agent 能并行执行小时级任务，那么模型能力、访问权限、成本、缓存、监控和故障恢复都必须成为产品的一部分。

---

## Alice 翻译说明

- 保留关键专有名词：GPT-5.6 Sol、Terra、Luna、Codex、API、Terminal-Bench、GeneBench、Preparedness Framework、Cyber Critical、jailbreak、prompt caching。
- 数字、价格、日期和可用性按原文含义翻译，并保持可核对。
- 未逐字复刻原文；采用结构化译读，覆盖主要事实、论证路径、安全说明、价格和发布安排。

## Colly 质检

- 完整性：通过。覆盖原文核心发布、能力、安全防护、红队、可用性、价格和编辑观察。
- 准确性：38/40。关键事实与来源一致；个别段落为编辑性概括。
- 流畅性：27/30。中文表达自然，适合日报读者。
- 风格一致性：18/20。技术术语保留和中文解释平衡较好。
- 格式规范：9/10。Markdown 结构清晰。

**总分：92/100，通过。**
