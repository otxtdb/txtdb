---
title: "Vinzent03/obsidian-git: Integrate Git version control with automatic commit-and-sync and other advanced features in Obsidian.md"
source: "https://github.com/vinzent03/obsidian-git"
author:
published:
created: 2026-08-27
description: "Integrate Git version control with automatic commit-and-sync and other advanced features in Obsidian.md - Vinzent03/obsidian-git"
tags:
  - "clippings"
taxonomy: { doc_category: [obsidian] }
---
## Vinzent03/obsidian-git：将 Git 版本控制功能与 Obsidian.md 中的自动提交、同步等高级功能相结合。

## Obsidian Git 插件

这是一款功能强大的 Obsidian.md 插件，它将 Git 功能直接整合到了 Obsidian 中。你可以在 Obsidian 内自动完成提交、拉取和推送操作，同时还能随时查看自己的修改内容。

## 📚 文档资料

所有的设置指南（包括移动端相关设置）、常见问题解答、使用技巧以及高级配置方法，都可以在📖完整文档中找到。

> 手机用户：该插件极不稳定 ⚠️ ！请查看下方的手机用户专用板块。

## 主要特点

- 🔁 按预定时间自动执行提交和同步操作（包括提交、拉取和推送）。
- 📥 在 Obsidian 平台上，系统会自动加载启动组件
- 📂 支持通过子模块来管理多个代码库（仅限桌面端，需手动启用该功能）
- 🔧 源代码控制视图：可用于将文件标记为待处理状态/取消标记、提交文件以及比较文件差异。请使用 `Open source control view` 命令来打开该视图。
- 📜 历史记录视图：用于查看提交日志和已更改的文件。可通过 `Open history view` 命令来打开该视图。
- 🔍 “差异视图”用于查看文件中的更改——请使用 `Open diff view` 命令来打开该视图。
- 📝 编辑器中会显示已添加、已修改和已删除的行/代码块（仅限桌面端）。
- 通过 GitHub 集成，你可以在浏览器中直接打开文件并查看文件的历史记录。

> 如需查看详细的文件版本历史记录，建议将此插件与“版本历史对比”插件一起使用。

## UI 预览

### 🔧 源代码控制视图

你可以在 Obsidian 中直接管理文件的更改，比如将单个文件标记为“已暂存”或“未暂存”，然后再进行提交。

[![Source Control View](https://raw.githubusercontent.com/Vinzent03/obsidian-git/master/images/source-view.png)](https://raw.githubusercontent.com/Vinzent03/obsidian-git/master/images/source-view.png)

### 📜 历史视图

显示该代码仓库的提交历史记录。可以查看每次提交的详细信息，包括提交消息、提交者、提交日期以及被修改的文件。如截图所示，提交者和提交日期默认是隐藏的，但可以在设置中将其显示出来。

[![History View](https://raw.githubusercontent.com/Vinzent03/obsidian-git/master/images/history-view.png)](https://raw.githubusercontent.com/Vinzent03/obsidian-git/master/images/history-view.png)

### 🔍 差异查看

使用清晰简洁的差异对比工具来比较不同版本。可以通过源代码控制视图或使用 `Open diff view` 命令来打开该工具。

[![Diff View](https://raw.githubusercontent.com/Vinzent03/obsidian-git/master/images/diff-view.png)](https://raw.githubusercontent.com/Vinzent03/obsidian-git/master/images/diff-view.png)

### 📝 编辑器中的各种标记/符号

可以直接在编辑器中查看每一行的更改情况，同时还能看到哪些行被添加、修改或删除了。你可以直接通过这些标记来暂存或重置更改。此外，还有用于在各个代码块之间切换、以及暂存/重置光标所在位置的代码块的命令。该功能需要在插件设置中启用才能使用。

[![Signs](https://raw.githubusercontent.com/Vinzent03/obsidian-git/master/images/signs.png)](https://raw.githubusercontent.com/Vinzent03/obsidian-git/master/images/signs.png)

## 可用的命令

> 这些并不是全部命令——它们只是一些最常见的命令而已。想要获取完整的命令列表，请参考 Obsidian 软件中的命令面板。

- 🔄 已发生变化
	- `List changed files` ：在模态窗口中列出所有变更内容
		- `Open diff view` ：为当前文件打开对比视图
		- `Stage current file`
		- `Unstage current file`
		- `Discard all changes` ：丢弃仓库中的所有更改
- ✅ 提交
	- `Commit` ：如果文件只是被标记为“已提交”，那么这些文件才会被提交；否则，只有那些被标记为“已提交”的文件才会被提交。
		- `Commit with specific message` ：与上面相同，但包含自定义消息
		- `Commit all changes` ：提交所有更改，但不进行推送
		- `Commit all changes with specific message` ：与上面相同，但包含自定义消息
- 🔀 提交与同步
	- `Commit-and-sync` ：使用默认设置时，这将提交所有更改、拉取数据以及推送内容。
		- `Commit-and-sync with specific message` ：与上面相同，但包含自定义消息
		- `Commit-and-sync and close` ：与 `Commit-and-sync` 相同，但在桌面环境下运行时，会关闭 Obsidian 窗口。而在移动设备上运行时，则不会退出 Obsidian 应用程序。
- 🌐 远程操作
	- `Push`, `Pull`
		- `Edit remotes` ：添加新的远程设备或编辑现有的远程设备
		- `Remove remote`
		- `Clone an existing remote repo` ：会打开一个对话框，要求输入 URL 以及认证信息，以便克隆远程仓库。
		- `Open file on GitHub` ：在浏览器窗口中打开当前文件在 GitHub 上的文件视图。注意：仅适用于桌面环境。
		- `Open file history on GitHub` ：在浏览器窗口中打开当前文件在 GitHub 上的文件历史记录。注意：仅适用于桌面环境。
- 🏠 管理本地仓库
	- `Initialize a new repo`
		- `Create new branch`
		- `Delete branch`
		- `CAUTION: Delete repository`
- 🧪 其他杂项
	- `Open source control view` ：打开侧边窗格，显示源代码控制视图
		- `Open history view` ：打开侧边窗格，显示历史记录视图
		- `Edit .gitignore`
		- `Add file to .gitignore` ：将当前文件添加到 `.gitignore 中`

## 💻 桌面笔记

### 🔐 身份验证

一些 Git 服务可能需要进一步的配置来完成 HTTPS/SSH 认证设置。请参阅认证指南以获取更多信息。

### Linux 操作系统上的黑曜石

- ⚠️ 由于沙盒限制的原因，Snap 并不被支持。
- ⚠️ 不建议使用 Flatpak，因为它无法访问所有的系统文件。虽然他们正在积极修复许多问题，但仍然存在一些问题。尤其是在更复杂的配置环境下。
- ✅ 请使用 AppImage 或系统包管理器进行完全权限化的安装（参见 Linux 安装指南）。

## 📱 移动设备支持（ ⚠️ 实验性功能）

在移动设备上使用的 Git 实现非常不稳定！不建议在移动设备上使用这个插件，建议尝试其他同步服务。

其中一个这样的替代方案是 GitSync，该工具在 Android 和 iOS 平台上都能使用。虽然它并非与本插件相关联，但对于移动设备用户来说，它可能是更好的选择。关于如何使用的教程可以在这里找到。

> 🧪 这个 Git 插件在移动设备上能够正常运行，得益于 isomorphic-git 这一基于 JavaScript 的 Git 重实现。不过，该插件存在一些严重的限制和问题。Obsidian 插件无法在 Android 或 iOS 设备上使用本地的 Git 安装版本。

### ❌ 移动设备的功能限制

- 没有进行 SSH 认证（与 isomorphic-git 问题相关）
- 由于内存限制，回购的数量有限。
- 不使用重新合并策略
- 没有子模块被支持。

### ⚠️ 性能注意事项

> [!caution] Caution
> 根据您的设备类型和可用内存情况，Obsidian 可能会有所不同。
> 
> - 在克隆/拉取操作中发生崩溃
> - 制造缓冲区溢出错误
> - 无限期运行。
> 
> 这个问题是由于移动端使用的 git 实现不够高效所导致的。我不知道该如何解决这个问题。如果你也遇到同样的问题，那我必须承认这个插件对你来说是无法使用的。因此，对现有问题进行评论或提出新的问题都是无济于事的。非常抱歉。

### 移动设备使用指南：

如果你有一个很大的仓库或存储库，我建议将文件分阶段提交，只提交那些已经经过阶段化的文件。

## 🙋 联系方式与致谢信息

- 《The Line Authoring》功能是由 GollyTicker 开发的，因此任何问题都可以通过她来解答。
- 这个插件最初是由 denolehov 开发的。自 2021 年 3 月以来，由我，Vinzent03 负责维护这个插件。因此，在 2024 年 7 月，GitHub 上的仓库资源被移到了我的账户上。
- 如果您有任何反馈或问题，请随时通过 GitHub 的问题反馈机制与我们联系。

## ☕ 支持

如果您认为这个插件很有用，并且希望支持其开发工作，您可以通过在 Ko-fi 上为我捐款来表达您的支持。