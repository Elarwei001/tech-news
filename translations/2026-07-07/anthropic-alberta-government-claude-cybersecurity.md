# Anthropic《Government of Alberta uses Claude to find and fix cybersecurity vulnerabilities across government systems》中文译读

> 原文：Anthropic, [Government of Alberta uses Claude to find and fix cybersecurity vulnerabilities across government systems](https://www.anthropic.com/news/alberta-government-claude-cybersecurity)
> 日期：2026-07-06
> 说明：以下为中文译读，完整覆盖原文主要事实、结构、流程和行业含义；为遵守版权合规要求，不逐字复刻英文原文。

---

## 核心摘要

Anthropic 发布案例研究称，加拿大 Alberta 省政府自 2025 年以来一直使用 Claude Code，并结合 Claude Opus 与 Sonnet 模型，审查政府系统、发现漏洞并修复问题。Alberta Ministry of Technology and Innovation 的一个内部团队在 20 小时内扫描了 4.66 亿行代码，发现并修补多个系统中的安全缺口，同时构建了新的工具，让这些系统在后续开发和维护中更安全。

Anthropic 将该案例作为政府机构大规模使用 Claude 和 Claude Code 保护系统的示例。政府系统通常承担福利发放、公共服务和关键运营，但很多代码年代久远、缺乏文档、存在安全隐患，因此系统化安全审查难度很高。Alberta 还公开了一组技术白皮书，供其他政府机构参考。

Alberta Technology and Innovation Minister Nate Glubish 表示，民众把大量敏感信息托付给政府，政府有责任保护这些信息。通过 AI 查找和修复系统漏洞，Alberta 在数小时内完成了传统方式可能需要多年完成的工作。

---

## Alberta 的方法

Alberta Ministry of Technology and Innovation 负责维护全部 27 个省级部门的系统，覆盖社会服务、公共安全、野火响应等场景。它管理约 1,280 个应用和 3,400 个代码仓库，其中大部分从未经历系统性安全审查。长期积累的技术债包括不安全代码、未处理 bug、过时软件和不足的文档，规模可能达到数十亿美元级别。

这些系统中保存着高度敏感的信息，包括税务记录、政府采购数据和社会服务案卷。为降低风险，Alberta 在 2025 年建立了内部团队，目标是在 Claude 的协助下提高系统安全性，并让系统随着时间推移更易维护。

---

## 4.66 亿行代码扫描

Alberta 团队将 Claude 用于其维护的代码库，结合 Claude Code、Claude Opus 和 Sonnet 模型展开安全审查。约 50 个 agent 自主并行运行，扫描系统中的安全漏洞、底层基础设施和部署流程弱点，以及技术文档缺口。

Claude Code 的流程分为两个阶段。第一阶段，规则引擎扫描各个仓库，标记已知问题模式。第二阶段，Claude Code 审查这些标记，引用每个发现对应的具体文件和行号，方便开发人员验证。此次扫描覆盖 Alberta 拥有的全部仓库，并发现了一些传统自动化扫描工具遗漏的问题。

Anthropic 称，Alberta 的实现耗时约 20 小时。团队估计，如果使用传统方式进行同类审查，可能需要约 6.5 年。

---

## 修复与现代化

当扫描发现漏洞时，Claude Code 往往可以生成修复方案、运行测试并完成构建。如果某个系统缺少足够的自动化测试来验证补丁是否安全，Claude 会先编写测试。对于过于陈旧或复杂、难以在原有形态下高效修补的代码，Claude 会帮助将其重写为更现代、更易维护的语言。

Anthropic 提到，在某些场景下，系统可以在四到五天内重建完成。其中一个例子是某补贴项目门户：原系统约 25 年前用 Java 手写，首次构建耗时五个月，而在 Claude 协助下的现代化周期显著缩短。

这些工作并不是无人类参与的自动发布。每个补丁在上线前，都需要 Ministry 工程师审查和批准。Claude 的角色是扩大审查和修复能力，而不是取代工程治理。

---

## 持续安全审查 agent

Alberta 的网络安全团队还建立了一组专门的 Claude review agents，在开发流程中持续运行。

其中，red team agent 会从外部视角探测应用，模拟攻击者如何发现和利用漏洞，并绘制潜在利用路径。blue team agent 会按照国际安全标准评估应用防御能力，并写出修复计划，指出需要修改的具体文件。

此外，还有 agent 检查代码质量，以及公众看到的文本是否清晰。每个应用在每次检查中都会对照约 95 项安全控制。这些 agent 基于 Claude Agent SDK 构建，并对每个应用执行一系列分析和检查。

---

## AI Academy 与能力扩散

除了扫描、加固和现代化自身系统，Alberta 还通过 Alberta AI Academy 培训政府工作人员和公众使用 AI。已有数千名政府员工，以及超过 10,000 名公众成员，使用该平台学习有效使用 AI 的基础知识，内容覆盖提示、企业应用交付等方面。

Alberta Ministry of Technology and Innovation 希望通过 Academy，将单个团队或项目形成的方法扩展到需要它的每个部门。

---

## 后续计划

目前，Claude 已经帮助 Ministry 编写、审查和部署代码，支持其现代化工作。下一步，Alberta 计划扩大 agent 使用范围，让 AI agents 与工程师协作构建全新的软件和工具。

Alberta 还将继续推进系统现代化。Anthropic 举例称，某个部门有 185 个遗留应用仍在生产中运行，维护成本高且难以更新。Alberta 计划使用 Claude Code 分析这些系统，理解其功能，并将其整合为 16 个使用现代语言和约定构建的可复用应用。

目标是降低复杂度、减少维护成本，并加快原本需要多年才能完成的现代化工作。

---

## 对其他政府的意义

Anthropic 指出，Alberta 正在处理的技术债和安全漏洞并不特殊。世界各地的省、州和联邦机构中都存在类似问题。Alberta 发布的技术白皮书为其他政府提供了处理这类问题的参考方案。

除白皮书外，Alberta 还将在 7 月于 Edmonton 举办 industry day，分享经验。今年秋季，它将启动一项计划，把该方法扩展到整个省政府。Anthropic 表示会继续与 Alberta 合作，并希望其记录的方法能帮助其他政府保护自身系统。

---

## 译文质量自检

- **完整性**：覆盖原文主要结构，包括项目背景、Alberta 方法、代码扫描、修复与现代化、持续审查 agent、AI Academy、后续计划和跨政府参考价值。
- **准确性**：保留关键数字、机构名称、时间、模型名称和流程关系。
- **表达**：采用中文科技新闻风格，避免机械逐句翻译。
- **版权处理**：未逐字复刻原文长段落，保留原文链接供读者查阅完整英文内容。
