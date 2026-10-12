---
title: "Local History (New) - Visual Studio Marketplace"
source: "https://marketplace.visualstudio.com/items?itemName=ctf0.local-history-new"
author:
published: 2026-05-28
created: 2026-08-26
description: "Extension for Visual Studio Code - Save files into local history"
tags:
  - "clippings"
taxonomy: { doc_category: [vscode] }
---
## 当地历史（新内容）


将文件保存到本地历史记录中。

## 地方历史

基于的是 [https://github.com/zabel-xyz/local-history](https://github.com/zabel-xyz/local-history) 这个项目，看起来已经停止开发了。

- 查看变更日志

> ## 视觉时间轴

![demo](https://github.com/ctf0/local-history/releases/download/010/demo.png)

一款功能齐全的差异比对工具，能够浏览文件历史记录，并支持从快照到当前状态的差异比对。

### 交互式差异化和块管理

- 高级应用/拒绝功能——可以点击任何已修改的行字段，将快照中的更改应用到当前文件，或者拒绝当前的修改操作（恢复快照中的内容）。
- 部分（单行）块级操作—— `Cmd/Ctrl + Click` 在块内只操作单行，可以选中或拒绝仅这一行，而保持块内的其他部分不变。
- 撤销堆栈——每一个操作都会有一个基于文件的撤销副本作为支持，因此你可以使用 `Cmd/Ctrl + Z` 来进行撤销操作。撤销功能在会话期间仍然有效，即使关闭或重新打开面板也不会失效。可以通过 `localHistory.fileBackedUndo` 进行配置。
- 右键点击任何行或块，即可复制其内容。
- 检测到有移动过的方块。

### 视觉元素

- 并排视图与统一视图——可以在并排视图（默认模式）和统一差异视图之间切换。当编辑器宽度较窄时，系统会自动切换到统一视图模式，该功能由 `diffEditor.renderSideBySideInlineBreakpoint` 控制。
- 在线词级差异对比——被修改的行会显示内嵌的词级高亮显示（行内呈现红色或绿色边框），从而让用户可以清晰地看到具体的修改内容。
- 语法高亮显示——通过 TextMate 语法规则，在快照文件和当前文件中都能实现完整的语法高亮显示功能。
- 主题设置——使用 VS Code 的活动主题颜色（编辑器、差异编辑器、标题栏、按钮、滚动条等），并遵循 `editor.lineHeight` 、 `editor.fontFamily` 、 `editor.fontSize` 的设置规则。
- 可折叠的不变区域——遵循 `diffEditor.hideUnchangedRegions` 的设置；不变的区块可以通过点击来折叠或展开。

### 快照导航

- 时间轴条——顶部有一个水平时间轴条，上面以日期为标记的点表示了所有快照。点击任何一个点即可直接跳转到该快照。可以使用鼠标滚轮进行水平滚动。
- **使用箭头键 `←` / `→`** 可以在不同的快照之间切换（即更旧或更新的状态）。连续快速点击会暂时停止，以确保渲染过程的流畅性。
- 副显示屏——在前后按钮之间显示当前位置（例如： `3 / 15` ）。
- 直接执行快照操作——可以在编辑器中选择任何快照进行打开（使用“在编辑器中等位”按钮），或者通过确认对话框将其恢复为当前文件（ `Restore This Version` 按钮）。
- 光标跟踪——当时间轴打开时，视图会滚动到编辑器中光标所在的那一行（以便快速查看该行历史信息）。
- 左右视图之间的滚动同步。

### 默认视图

- 可以通过 `localHistory.defaultView` 进行配置（使用 `side-by-side` 或 `unified` ）。

### 键盘快捷键

| 命令 | Windows | macOS |
| --- | --- | --- |
| 切换模式 | `Tab` | `Tab` |
| 上一个检查点 | `←` | `←` |
| 下一个检查点 | `→` | `→` |
| 向上/向下滚动 | `↑` / `↓` | `↑` / `↓` |
| 滚动到顶部/底部 | `Ctrl` + `↑` / `↓` | `Cmd` + `↑` / `↓` |
| 关闭时间线/上下文菜单 | `Esc` | `Esc` |
| 放大查看 | `Ctrl` + `+` | `Cmd` + `+` |
| 缩小视野 | `Ctrl` + `-` | `Cmd` + `-` |
| 恢复缩放功能 | `Ctrl` + `0` | `Cmd` + `0` |
| 撤销整个操作 | `Ctrl` + `Z` | `Cmd` + `Z` |

> ## 地方历史
> 
> 一个用于维护文件本地历史记录的可视化源代码插件。
> 
> 每次你修改一个文件时，旧版本的内容都会被保存在本地历史中。你可以随时将当前文件与历史中的任何旧版本进行比较。这一点在你需要误删或误改文件时非常有用。如果工作区出现严重问题，历史记录也能为你提供帮助。每个文件的修订版本都存储在工作区目录的.history 文件夹中；你也可以选择使用其他位置来存储历史记录，详见 local-history.path 文档。例如： `.history/foo/bar/myFile_20151212205930.ts`
> 
> 你可以在浏览器面板中使用 `local-history tree` 来轻松地在各个历史文件之间切换。
> 
> 当你点击某个文件时，会显示与当前版本的对比结果。  
> 你也可以通过上下文菜单访问其他命令。
> 
> 您有多种过滤选项：
> 
> - 全部
> - 当前文件（默认）
> - 特定文件（您可以输入搜索关键词）
> 
> 所显示的文件取决于 `localHistory.maxDisplay` 的设置。要查看更多内容，可以使用搜索加号图标。
> 
> ## 设置
> 
> ```markdown
> "localHistory.daysLimit":  30  // A day number to purge local history. (0: no purge)
> "localHistory.maxDisplay": 10  // A max files to display with local history commands
> "localHistory.saveDelay":   0  // A delay in seconds to save file in local history. {0: no delay}
> "localHistory.dateLocale":     // The locale to use when displaying date (e.g.: "fr-CH" or "en-GB" or ...)
> "localHistory.dateFormat":     // Date format: "timestamp" (28/05/2026, 20:07:00) or "human" (Thu, May 28, 2026, 08:07 PM)
> 
> "localHistory.path":     // Specify another location for .history folder (null: use workspaceFolder)
> This settings must be an absolute path.
> 
>   You can start your path with:
>       - ${workspaceFolder}: current workspace folder
>           e.g. ${workspaceFolder}/.vscode to save in each workspace folder .vscode/.history
>       - ${workspaceFolder: index}: specific workspace index
>           e.g. workspace folders A, B, C. But save always in A/.history => ${workspaceFolder: 0}
> 
>   Your can also use specific variable in path:
>       - %variable%: an environnement variable (e.g. %AppData%)
>       - ~: the home directory (linux)
> 
> "localHistory.absolute": // Save absolute or relative path in localHistory.path
>    true:  (absolute) // <localHistory.path>/.history/<absolutePath>
>    false: (relative) // (default) <localHistory.path>/.history/<workspaceFolder.basename>/<relativePath>
> 
> "localHistory.enabled":
>    0: Never     // Possibility to disabled the extension for some project
>    1: Always    // (default) Save also single file with no workspaceFolder ("localHistory.path" must be defined)
>    2: Workspace // Save only files within workspaceFolder
> 
> "localHistory.exclude": // Files or folders to not save
> // (default) ['**/.history/**', '**/.vscode**', '**/node_modules/**', '**/typings/**', '**/out/**']
> 
> "localHistory.treeLocation": // Specify a location for tree view
>    explorer (default): // Show tree in Explorer item
>    localHistory:       // Show tree in a special active bar item
> ```
> 
> ## 命令/指令
> 
> ```markdown
> local-history.showAll // Show all history available to select (limited with maxDisplay settings)
> local-history.showCurrent // Show current version (if history version is active)
> local-history.compareToCurrent // compare current version with another version in history
> local-history.compareToActive // compare active file with another version in history
> local-history.compareToPrevious // compare a version in history with its previous version
> ```
> 
> ## 注意
> 
> 当.history 文件夹存储在工作区中时，可以添加“files.exclude”配置。这样可以将.history 文件夹隐藏起来，从而避免一些问题出现（例如，某些扩展名的文件会被排除在外）。  
> 感谢@pabloarista（问题编号 13）的帮助。