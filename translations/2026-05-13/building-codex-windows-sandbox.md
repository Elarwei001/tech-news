# Building a safe, effective sandbox to enable Codex on Windows

> 原文：https://openai.com/index/building-codex-windows-sandbox/
>
> 译注：根据 OpenAI 官方工程文章可抓取正文翻译整理。保留 Codex、sandbox、Full Access 等术语。

## 正文翻译

OpenAI 的 Codex 工程文章介绍了 Windows sandbox 的背景。作者提到，加入 Codex 工程团队时，Codex for Windows 还没有 sandbox 实现。这意味着 Windows 用户在使用 OpenAI coding agents 时，只能在两个不理想的选项之间选择。

第一个选项是几乎每个命令都要审批，即使只是读取操作也一样。这会降低效率，也让体验变得繁琐。使用 Codex 的主要好处之一，本来就是不必亲手完成所有重复工作。

第二个选项是开启 Full Access mode，让 Codex 不经审批、不受限制地运行所有命令。这减少了摩擦，但代价是失去监督。

Codex 是运行在开发者本机上的 coding agent，可以通过 CLI、IDE extension 或桌面应用使用。它管理的是人类键盘前的对话，以及云端模型推理之间的协作。Codex 在真实用户权限下运行，因此它能触碰的系统资源和用户本身能触碰的资源高度相关。

这正是 sandbox 必要的原因。一个本地 coding agent 会读取文件、运行命令、修改代码、执行测试，也可能无意中访问敏感路径。安全有效的 sandbox 要在两件事之间取得平衡：既不能让 agent 无限制行动，也不能让开发者每一步都手动审批。

OpenAI 的目标是为 Windows 用户提供更接近 macOS/Linux 的安全体验：低风险操作可以顺畅进行，高风险操作需要明确审批，系统访问范围受到限制，并且用户能理解 agent 正在做什么。

## 为什么重要

Windows 是巨大的开发者平台。如果 Codex 想成为主流 coding agent，就必须在 Windows 上拥有可靠安全边界。否则，用户只能在低效率和高风险之间取舍。

这篇文章也说明 coding agent 的竞争已经进入本地执行层。模型会写代码只是基础；真正的产品能力还包括 sandbox、权限、审批、日志、跨平台一致性和用户信任。

## 译后备注

- Full Access mode 指不经过常规限制直接执行命令的模式，风险更高。
- sandbox 在这里是本地执行隔离与权限限制机制，不只是云端环境。
