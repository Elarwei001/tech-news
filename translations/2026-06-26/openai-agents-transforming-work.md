# OpenAI《How agents are transforming work》中文译读

> 原文：OpenAI, "How agents are transforming work", 2026-06-25  
> 链接：https://openai.com/index/how-agents-are-transforming-work/  
> 说明：出于版权合规，本文件提供完整结构化译读与关键事实翻译，不逐字复刻原文全文。

---

## 核心结论

OpenAI 这篇经济研究文章的中心观点是：agentic AI 正在把知识工作的基本单位，从一次短对话，改造成一个可委派、可长时间运行、可使用工具、可与环境交互并不断迭代的任务。Codex 是 OpenAI 用来观察这一变化的主要样本。

文章认为，chatbot 通常处理短而自包含的交互；agent 则可以独立运行数分钟甚至数小时，协调工具调用、与环境交互，并朝着解决方案迭代。因此，agent 正迅速成为工作场景中最有力的 AI 工具。

---

## OpenAI 内部的使用迁移

OpenAI 称，在 Codex 公开发布后的最初几个月，ChatGPT 仍是 OpenAI 内部默认的 AI 工作工具。到 2025 年 8 月，OpenAI 员工平均只有不到 10% 的 token 用在 Codex 上。

但到 2026 年，情况已经发生改变。OpenAI 表示，包括 Legal、Finance、Recruiting 等非技术部门在内，所有部门都已把 Codex 作为主要 AI 工作工具。平均员工现在超过 85% 的输出 token 来自 Codex。由于 Codex 用户总体 token 使用量更高，Codex 在 OpenAI 每周总输出 token 中的占比更高，达到 99.8%。

---

## 四个主要趋势

OpenAI 将过去一年 Codex 的变化总结为四个趋势。

第一，用户把 Codex 用于更长周期的工作。到 2026 年 5 月，在抽样个人用户中，80.6% 至少发起过一次估计超过 30 分钟人工工作量的 Codex 请求，70.2% 发起过超过 1 小时的请求，25.6% 发起过超过 8 小时的请求。

第二，Codex 成为 OpenAI 各部门的主要 AI 工具。工程部门最早迁移；Legal、Finance 和 Recruiting 等部门大约在 2026 年 4 月左右也转向以 Codex 为主。

第三，非开发者采用增长尤其快。自 2025 年 8 月以来，个人用户中的非开发者增长 137 倍，组织用户中的非开发者增长 189 倍，OpenAI 内部非开发者增长 12 倍。

第四，Codex 让 OpenAI 员工能够完成岗位描述之外的任务。即使技术使用仍主要集中在工程师群体，非技术用户也经常用 Codex 完成编码、自动化、数据转换、工具构建、调试和结构化分析等技术执行工作。

---

## Agent 工作时长变长，任务变难

OpenAI 指出，接近四分之一的 Codex 请求对应超过一小时的人类工作量。随着 Codex 在独立、长上下文工作上的能力提升，用户逐渐从短交互转向更复杂、更长周期的任务。

在 OpenAI 内部，Codex 的日常运行时间也能体现这一点。到 2026 年 6 月，OpenAI 日活用户中 99 分位用户每天经常生成超过 60 小时的 Codex agent turns，并分布在多个并行 agent 上。

这说明用户不再只是一次让 Codex 回答一个问题，而是开始在一天内编排多个 agent 任务。

---

## 从工程师扩散到非工程部门

OpenAI 工程师最早采用 Codex。到 2025 年 12 月，平均工程师已经把自己使用 OpenAI 产品的大部分输出迁移到 Codex。现在，平均工程师 99% 的输出 token 来自 Codex，而不是 ChatGPT。

Legal、Finance、Recruiting 的迁移较晚，大约在 2026 年 4 月跨过多数使用门槛，但迁移速度更快。OpenAI 称，平均律师或招聘人员现在超过 85% 的输出 token 来自 Codex。

在 2025 年 11 月到 2026 年 6 月之间，OpenAI 内部活跃用户的 Codex 输出 token 增长明显。Research 的中位使用量增长 56 倍，Customer Support 增长 32 倍，Engineering 增长 27 倍，Legal 增长 13 倍。

---

## 非开发者为何增长更快

Codex 一开始是 coding tool，天然吸引开发者。但随着它扩展到更一般的知识工作，非开发者的增长速度超过开发者。

这并不意味着所有非开发者都像工程师一样使用 Codex。更准确的理解是，越来越多非开发者开始把 Codex 用于某种 agentic work。

OpenAI 的热力图显示，不同部门使用 Codex 产出的工作类型不同。Engineering 和 Data Science/Research 中，工程和编码占比最高；Finance/Biz Ops、Product/Marketing/Ops 等部门中，knowledge work 占比更高。但任务边界正在松动。例如，商业职能员工通过 Codex 完成的工作中，超过四分之一属于 engineering 或 coding。

---

## 对经济潜力的含义

OpenAI 的结论是：当非工程员工也能使用 agentic tools 时，他们可以完成的工作边界会扩大。这对企业如何重设计流程、员工该培养哪些技能、政策制定者和研究者如何理解 AI 对劳动力市场的影响，都很重要。

文章展示的是前沿用户如何采用前沿 agentic tools。随着工具能力提升，人们会把它们用于更长、更复杂、更跨职能的工作。OpenAI 认为，随着时间推移，这很可能就是未来工作的样子。

---

## 方法限制

OpenAI 在脚注中提醒，任务时长是通过 LLM-as-judge 基于 Codex transcript 估计的。这些超过 30 分钟、1 小时、4 小时、8 小时的阈值应被视为方向性指标，而不是精确测量。

此外，部分数据基于个人用户 0.1% 的随机样本，OpenAI 内部员工也不是普通企业用户的代表样本。因此，最稳妥的解读不是把数字当作全行业平均值，而是把它们当作前沿采用模式的信号。

---

## 编辑观察

这篇文章最重要的启发是：agent 产品的核心指标正在变化。过去，AI 产品关注回答质量、响应速度、日活和 token 消耗；现在，新的关键指标包括可委派工作量、长程任务完成率、并行任务运行时间、跨工具执行能力、权限边界、失败恢复和组织流程集成。

如果这个趋势继续，企业 AI 的采购与治理也会变化。企业不会只问模型是否聪明，还会问：这个 agent 能运行多久？能访问哪些系统？失败时如何解释？谁批准不可逆操作？成本能否按任务预测？审计日志是否完整？结果由谁验收？

OpenAI 的数据说明，agent adoption 正在从“开发者效率工具”走向“组织工作层”。这也是今天 Mistral connectors、NVIDIA Agent Toolkit、BioNeMo Agent Toolkit 和 Google agent control roadmap 同时显得重要的原因：模型能力只是起点，真正进入生产环境还需要连接、权限、工具、运行时、检索和控制面。

---

## Alice 翻译说明

- 保留原文关键专有名词：Codex、agentic AI、LLM-as-judge、output tokens、agent turns。
- 数字和日期按原文含义翻译，并在中文中保持可核对。
- 未逐字复刻全文；采用结构化译读，以覆盖主要事实、论证路径和方法限制。

## Colly 质检

- 完整性：通过。覆盖原文核心论点、四个趋势、关键数字、内部迁移、非开发者增长、经济含义和方法限制。
- 准确性：37/40。数字与来源一致；少量表达为编辑性概括。
- 流畅性：27/30。中文表达自然，适合日报读者。
- 风格一致性：18/20。术语保留与中文解释平衡较好。
- 格式规范：9/10。Markdown 结构清晰。

**总分：91/100，通过。**
