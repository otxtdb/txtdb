---
title: "Local History - Visual Studio Marketplace"
source: "https://marketplace.visualstudio.com/items?itemName=xyz.local-history"
author:
published:
created: 2026-10-12
description: "Extension for Visual Studio Code - Save files into local history"
tags:
  - "clippings"
taxonomy: { doc_category: [vscode] }
---
## 地方历史


将文件保存到本地历史记录中。

## 地方历史

一个用于维护文件本地历史记录的可视化源代码插件。

每次你修改一个文件时，旧版本的内容都会被保存在本地历史中。你可以随时将当前文件与历史中的任何旧版本进行比较。这一点在你需要误删或误改文件时非常有用。如果工作区出现严重问题，历史记录也能为你提供帮助。每个文件的修订版本都存储在工作区目录的.history 文件夹中；你也可以选择使用其他位置来存储历史记录，详见 local-history.path 文档。例如： `.history/foo/bar/myFile_20151212205930.ts`

你可以在浏览器面板中使用 `local-history tree` 来轻松地在各个历史文件之间切换。

当你点击某个文件时，会显示与当前版本的对比结果。  
你也可以通过上下文菜单访问其他命令。

![Image of tree](https://github.com/zabel-xyz/local-history/raw/master/images/Tree.png)

您有多种过滤选项：

- 全部
- 当前文件（默认）
- 特定文件（您可以输入搜索关键词）

![Image of tree](https://github.com/zabel-xyz/local-history/raw/master/images/Tree2.png)

所显示的文件取决于 `local-history.maxDisplay` 的设置。要查看更多内容，可以使用搜索加号图标。

## 设置

```markdown
"local-history.daysLimit":  30  // A day number to purge local history. (0: no purge)
"local-history.maxDisplay": 10  // A max files to display with local history commands
"local-history.saveDelay":   0  // A delay in seconds to save file in local history. {0: no delay}
"local-history.dateLocale":     // The locale to use when displaying date (e.g.: "fr-CH" or "en-GB" or ...)

"local-history.path":     // Specify another location for .history folder (null: use workspaceFolder)
    This settings must be an absolute path.

    You can start your path with:
    ${workspaceFolder}: current workspace folder
        e.g. ${workspaceFolder}/.vscode to save in each workspace folder .vscode/.history
    ${workspaceFolder: index}: specific workspace index
        e.g. workspace folders A, B, C. But save always in A/.history => ${workspaceFolder: 0}

    Your can also use specific variable in path:
    - %variable%: an environnement variable (e.g. %AppData%)
    - ~: the home directory (linux)

"local-history.absolute": // Save absolute or relative path in local-history.path
    true:  (absolute) // <local-history.path>/.history/<absolutePath>
    false: (relative) // (default) <local-history.path>/.history/<workspaceFolder.basename>/<relativePath>

"local-history.enabled":
    0: Never     // Possibillity to disabled the extension for some project
    1: Always    // (default) Save also single file with no workspaceFolder ("local-history.path" must be defined)
    2: Workspace // Save only files within workspaceFolder

"local-history.exclude": // Files or folders to not save
    // (default) ['**/.history/**', '**/.vscode**', '**/node_modules/**', '**/typings/**', '**/out/**']

"local-history.treeLocation": // Specify a location for tree view
    explorer (default): // Show tree in Explorer item
    localHistory:       // Show tree in a special active bar item
```

## 命令/指令

```markdown
local-history.showAll // Show all history available to select (limited with maxDisplay settings)
local-history.showCurrent // Show current version (if history version is active)
local-history.compareToCurrent // compare current version with another version in history
local-history.compareToActive // compare active file with another version in history
local-history.compareToPrevious // compare a version in history with its previous version
```

## 注意

当.history 文件夹存储在工作区中时，可以添加“files.exclude”配置。这样可以将.history 文件夹隐藏起来，从而避免一些问题出现（例如，某些扩展名的文件会被排除在外）。  
感谢@pabloarista（问题编号 13）的帮助。