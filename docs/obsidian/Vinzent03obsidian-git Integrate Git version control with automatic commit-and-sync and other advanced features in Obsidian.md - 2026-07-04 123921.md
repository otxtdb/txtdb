---
title: "Vinzent03/obsidian-git: Integrate Git version control with automatic commit-and-sync and other advanced features in Obsidian.md"
source: "https://github.com/vinzent03/obsidian-git"
author:
published:
created: 2026-07-04
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

## 主要特点/核心功能

- 🔁 按预定时间自动执行提交和同步操作（包括提交、拉取和推送）。
- 📥 在 Obsidian 启动时自动执行相关操作
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

### 📜 历史记录查看

显示该代码仓库的提交历史记录。可以查看每次提交的详细信息，包括提交消息、提交者、提交日期以及被修改的文件。如截图所示，提交者和提交日期默认是隐藏的，但可以在设置中将其显示出来。

[![History View](https://raw.githubusercontent.com/Vinzent03/obsidian-git/master/images/history-view.png)](https://raw.githubusercontent.com/Vinzent03/obsidian-git/master/images/history-view.png)

### 🔍 差异视图

使用清晰简洁的差异对比工具来比较不同版本。可以通过源代码控制视图或使用 `Open diff view` 命令来打开该工具。

[![Diff View](https://raw.githubusercontent.com/Vinzent03/obsidian-git/master/images/diff-view.png)](https://raw.githubusercontent.com/Vinzent03/obsidian-git/master/images/diff-view.png)

### 📝 编辑器中的各种标记/符号

可以直接在编辑器中查看每一行的更改情况，同时还能看到哪些行被添加、修改或删除了。你可以直接通过这些标记来暂存或重置更改。此外，还有用于在各个代码块之间切换、以及暂存/重置光标所在位置的代码块的命令。该功能需要在插件设置中启用才能使用。

[![Signs](https://raw.githubusercontent.com/Vinzent03/obsidian-git/master/images/signs.png)](https://raw.githubusercontent.com/Vinzent03/obsidian-git/master/images/signs.png)

## 可用命令

> 这并非全部命令——这些只是最常用的命令而已。如需完整列表，请查看 Obsidian 中的命令面板。

- 🔄 变更内容
	- `List changed files` ：在模态窗口中列出所有更改内容
		- `Open diff view` ：打开当前文件的差异视图
		- `Stage current file`
		- `Unstage current file`
		- `Discard all changes` ：丢弃仓库中的所有更改
- ✅ 提交
	- `Commit` ：如果文件只是被标记为待提交状态，那么只有这些文件会被提交；否则，只有那些已经被标记为待提交状态的文件才会被提交。
		- `Commit with specific message` ：与上面相同，只不过添加了自定义消息。
		- `Commit all changes` ：提交所有更改，但不进行推送操作
		- `Commit all changes with specific message` ：与上面相同，只不过添加了自定义消息。
- 🔀 提交并同步
	- `Commit-and-sync` ：在默认设置下，该操作会提交所有更改，同时执行“拉取”和“推送”操作。
		- `Commit-and-sync with specific message` ：与上面相同，只不过添加了自定义消息。
		- `Commit-and-sync and close` ：与 `Commit-and-sync` 相同。不过，如果在桌面端使用，该功能会关闭 Obsidian 窗口。在移动端使用时，不会退出 Obsidian 应用程序。
- 🌐 远程办公/远程操作
	- `Push`, `Pull`
		- `Edit remotes` ：添加新的遥控器或编辑现有的遥控器设置
		- `Remove remote`
		- `Clone an existing remote repo` ：会弹出对话框，要求输入 URL 和进行身份验证，以便克隆远程仓库。
		- `Open file on GitHub` ：在浏览器窗口中打开 GitHub 上当前文件的查看页面。注意：该功能仅适用于桌面端。
		- `Open file history on GitHub` ：在浏览器窗口中查看当前文件在 GitHub 上的版本历史记录。注意：该功能仅适用于桌面端。
- 🏠 管理本地仓库
	- `Initialize a new repo`
		- `Create new branch`
		- `Delete branch`
		- `CAUTION: Delete repository`
- 🧪 其他/杂项
	- `Open source control view` ：打开侧边窗格，显示源代码控制视图
		- `Open history view` ：打开侧边栏，显示历史记录视图
		- `Edit .gitignore`
		- `Add file to .gitignore` ：将当前文件添加到 `.gitignore 中`

## 💻 桌面笔记

### 🔐 认证/验证

某些 Git 服务可能需要额外的设置才能实现 HTTPS/SSH 认证。请参阅《认证指南》以获取详细信息。

### Linux 系统上的黑曜石软件

- ⚠️ 由于沙箱限制，Snap 功能无法使用。
- ⚠️ 不建议使用 Flatpak，因为它无法访问系统的所有文件。虽然开发者正在积极解决各种问题，但仍然存在不少缺陷。尤其是在需要更复杂的配置时。
- ✅ 请改用 AppImage 格式的文件，或者通过系统包管理器进行完整安装（Linux 安装指南）

## 📱 移动端支持功能（ ⚠️ 测试中）

这款插件在移动设备上的运行效果极不稳定！我不建议在移动设备上使用该插件，建议尝试其他同步服务。

其中一种替代方案是 GitSync，该应用在 Android 和 iOS 平台上都能使用。虽然 GitSync 与这个插件没有关联，但对于移动端用户来说，它可能是个更好的选择。关于如何安装该应用的教程可以在这里找到。

> 🧪 由于 isomorphic-git 的存在，Git 插件能够在移动设备上正常使用。isomorphic-git 是一种基于 JavaScript 的 Git 实现方式。不过，该插件存在不少限制和问题。在 Android 或 iOS 系统中，Obsidian 插件无法直接使用系统自带的 Git 安装程序。

### ❌ 移动端功能限制

- 没有 SSH 认证功能（这是 isomorphic-git 带来的问题）
- 由于内存限制，回购规模有限。
- 不采用重新基准合并策略
- 没有子模块提供支持。

### ⚠️ 性能注意事项

> [!caution] Caution
> 根据您的设备性能和可用内存大小，Obsidian 的使用效果可能会有所不同。
> 
> - 在克隆/拉取操作时发生崩溃
> - 制造缓冲区溢出错误
> - 可以无限期地运行下去。
> 
> 这是由于移动设备上所使用的 Git 实现方式效率低下所导致的。我不知道该如何解决这个问题。如果你也遇到同样的情况，那恐怕这个插件对你来说是无法使用的。因此，无论你发表评论还是创建新的问题，都不会有任何帮助。很抱歉。

### 手机使用小贴士：

如果你有一个很大的代码仓库/文件存储空间，我建议先将单个文件单独标记出来，然后再提交这些被标记的文件。

## 🙋 联系方式与致谢信息

- “线条绘制”功能是由 GollyTicker 开发的，因此，如有任何疑问，最好直接咨询她。
- 该插件最初是由 denolehov 开发的。从 2021 年 3 月开始，由我 Vinzent03 继续负责该插件的开发工作。因此，该插件的 GitHub 仓库也在 2024 年 7 月被转移到了我的账户下。
- 如果您有任何反馈或问题，请随时通过 GitHub 的 Issue 功能与我们联系。

## ☕ 支持服务

如果您觉得这个插件很有用，并希望支持其开发工作，您可以在 Ko-fi 上向我捐款支持。