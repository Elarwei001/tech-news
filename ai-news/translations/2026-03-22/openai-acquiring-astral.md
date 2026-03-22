# 关于 OpenAI 收购 Astral（uv/ruff/ty）的思考

> 📄 **原文**：[Thoughts on OpenAI acquiring Astral and uv/ruff/ty](https://simonwillison.net/2026/mar/19/openai-acquiring-astral/) by Simon Willison
> 🤖 **翻译说明**：本文由 AI 自动翻译，仅供参考。如有疑问请以原文为准。
> 📅 **翻译日期**：2026-03-22

---

*2026年3月19日*

今天早上的大新闻：[Astral 加入 OpenAI](https://astral.sh/blog/openai)（Astral 博客公告）和 [OpenAI 收购 Astral](https://openai.com/index/openai-to-acquire-astral/)（OpenAI 官方公告）。Astral 是 [uv](https://simonwillison.net/tags/uv/)、[ruff](https://simonwillison.net/tags/ruff/) 和 [ty](https://simonwillison.net/tags/ty/) 背后的公司——这三个项目在 Python 生态系统中越来越重要。我有一些想法要分享！

## OpenAI 和 Astral 的官方说法

Astral 团队将加入 OpenAI 的 Codex 团队。

Charlie Marsh [这样说](https://astral.sh/blog/openai)：

> 开源是这一切影响力和故事的核心；它是我们所做一切的中心。与我们的理念和 [OpenAI 的公告](https://openai.com/index/openai-to-acquire-astral/)一致，OpenAI 将在交易完成后继续支持我们的开源工具。我们将继续在开放环境中构建，与我们的社区一起——为更广泛的 Python 生态系统服务——就像我们从一开始就做的那样。[...]
> 
> 加入 Codex 团队后，我们将继续构建开源工具，探索它们与 Codex 更无缝集成的方式，并扩展我们的视野，更广泛地思考软件开发的未来。

OpenAI 的声明[重点略有不同](https://openai.com/index/openai-to-acquire-astral/)（重点标注为我所加）：

> 作为我们开发者优先理念的一部分，OpenAI 计划在交易完成后**支持** Astral 的开源产品。通过将 Astral 的工具和工程专业知识引入 OpenAI，我们将**加速 Codex 的工作**，并扩展 AI 在软件开发生命周期中的能力。

这是一条有些令人困惑的信息。[Codex CLI](https://github.com/openai/codex) 是一个 Rust 应用，而 Astral 拥有业内一些最优秀的 Rust 工程师——光是 [BurntSushi](https://github.com/burntsushi)（[Rust regex](https://github.com/rust-lang/regex)、[ripgrep](https://github.com/BurntSushi/ripgrep)、[jiff](https://github.com/BurntSushi/jiff)）可能就值这次收购的价格！

那么这是关于人才还是产品？我预计两者都有，但根据过去的经验，产品+人才的收购之后可能会变成仅关于人才的收购。

## uv 是重中之重

在 Astral 的项目中，影响力最大的是 [uv](https://github.com/astral-sh/uv)。如果你不熟悉它，uv 是目前为止对 Python 环境管理问题最有说服力的解决方案，这个问题最好的说明是[这幅经典的 XKCD 漫画](https://xkcd.com/1987/)。

把 `python` 换成 `uv run`，大多数问题就消失了。我在过去几年里大量使用它，它已经成为我工作流程中必不可少的一部分。

我不是唯一这样的人。根据 PyPI 统计，[uv 上个月被下载了](https://pypistats.org/packages/uv)超过 1.26 亿次！自 2024 年 2 月发布以来——仅仅两年前——它已经成为运行 Python 代码最流行的工具之一。

## Ruff 和 ty

Astral 的另外两个大项目是 [ruff](https://github.com/astral-sh/ruff)——一个 Python linter 和格式化工具——以及 [ty](https://github.com/astral-sh/ty)——一个快速的 Python 类型检查器。

这些都是提供出色开发体验的流行工具，但它们不像 uv 那样是"承重"的基础设施。

不过，它们确实与 Codex 等编程 Agent 工具有很好的协同效应——让 Agent 能够访问快速的 linting 和类型检查工具可以帮助提高它们生成的代码质量。

我不确信把它们整合到编程 Agent 本身（而不是告诉 Agent 何时运行它们）会产生有意义的差异，但也许我的想象力还不够。

## pyx 怎么办？

自从 uv 开始流行以来，Python 社区一直担心一家 VC 支持的公司拥有 Python 基础设施关键部分的战略风险。我在 2024 年 9 月[详细写过](https://simonwillison.net/2024/Sep/8/uv-under-discussion-on-mastodon/)其中一次讨论。

当时的讨论集中在 Astral 的商业计划可能是什么，这在 [2025 年 8 月](https://simonwillison.net/2025/Aug/13/pyx/)开始成形，当时他们宣布了 [pyx](https://astral.sh/pyx)——一个面向组织的私有 PyPI 风格的包注册中心。

我不太确定 pyx 在 OpenAI 内部是否有意义，值得注意的是它在 Astral 和 OpenAI 的公告中都没有被提及。

## 竞争格局

这笔交易的一个有趣方面是它可能如何影响 Anthropic 和 OpenAI 之间的竞争。

两家公司在 2025 年的大部分时间都专注于提高模型的编程能力，最终在 [2025 年 11 月达到拐点](https://simonwillison.net/tags/november-2025-inflection/)，编程 Agent 从"经常有用"变成了软件开发中"几乎不可或缺"的工具。

Anthropic 的 Claude Code 和 OpenAI 的 Codex 之间的竞争非常激烈。那些每月 200 美元的订阅加起来每年有数十亿美元的收入，对于非常需要这笔钱的公司来说。

Anthropic 在 2025 年 12 月[收购了 Bun JavaScript 运行时](https://www.anthropic.com/news/anthropic-acquires-bun-as-claude-code-reaches-usd1b-milestone)，这次收购看起来与 Astral 的收购形状有些相似。

Bun 已经是 Claude Code 的核心组件，那次收购主要是为了确保一个关键依赖能够得到积极维护。自那以后，得益于 Bun 创始人 Jarred Sumner 的努力，Claude Code 的性能有了显著提升。

这笔交易的一个糟糕版本是，如果 OpenAI 开始利用他们对 uv 的所有权作为与 Anthropic 竞争的筹码。

## Astral 的悄悄进行的 A 轮和 B 轮融资

Astral 公告中有一个细节引起了我的注意，在感谢团队、投资者和社区的部分：

> 其次，感谢我们的投资者，特别是来自 Accel 的 [Casey Aylward](https://www.accel.com/team/casey-aylward#bay-area)，他领投了我们的种子轮和 A 轮，以及来自 Andreessen Horowitz 的 [Jennifer Li](https://a16z.com/author/jennifer-li/)，她领投了我们的 B 轮。作为一个首次创业的、技术型的、单独的创始人，你们对我展现的信任远超我对自己的信任，我永远不会忘记。

据我所知，A 轮和 B 轮融资此前都没有公开宣布——我只能找到 [2023 年 4 月](https://astral.sh/blog/announcing-astral-the-company-behind-ruff)原始种子轮的报道。

那些投资者现在大概可以将他们在 Astral 的股份换成 OpenAI 的一部分。我想知道他们对 Astral 出售决定有多大影响。

## Fork 作为可信的退出策略？

Armin Ronacher 构建了 [Rye](https://til.simonwillison.net/python/rye)，后来被 Astral 接管并有效地与 uv 合并。在 [2024 年 8 月](https://lucumr.pocoo.org/2024/8/21/harvest-season/)，他写了关于 VC 支持的公司拥有开源基础设施关键部分的风险，并说了以下内容（重点为我所加）：

> 然而，在看过代码和 uv 正在做的事情之后，即使在最坏的可能未来，这也是一个**非常可以 fork 和维护的东西**。我相信即使 Astral 关闭或做出任何令人难以置信的授权许可方面的骚操作，社区的处境也会比 uv 存在之前更好。

Astral 自己的 Douglas Creager [今天在 Hacker News 上强调了这个角度](https://news.ycombinator.com/item?id=47438723#47439974)：

> 我只能说的是，现在，我们承诺以与以前相同的努力、关注和细节来维护我们的开源工具。这不会因为这次收购而改变。没有人能保证多年后动机、激励和决策会如何变化。但这就是为什么我们通过宽松许可来嵌入可选性。这使得最坏情况的形态是"fork 然后继续前进"，而不是"软件永远消失"。

我喜欢并信任 Astral 团队，我乐观地认为他们的项目在新家会得到良好的维护。

OpenAI 在收购和维护开源项目方面还没有太多记录。不过，他们在过去三个月里进行了一系列收购，收购了 [Promptfoo](https://openai.com/index/openai-to-acquire-promptfoo/) 和 [OpenClaw](https://steipete.me/posts/2026/openclaw)（某种程度上，他们雇用了创始人 Peter Steinberger 并将 OpenClaw 剥离给一个基金会），以及闭源 LaTeX 平台 [Crixet（现名 Prism）](https://openai.com/index/introducing-prism/)。

如果 uv 和其他 Astral 项目的情况真的变糟，我们将有机会看到 fork 退出策略的可信度如何。

---

*本翻译由 AI News Digest 自动生成*
