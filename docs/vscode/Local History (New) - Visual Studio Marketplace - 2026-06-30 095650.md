---
title: "Local History (New) - Visual Studio Marketplace"
source: "https://marketplace.visualstudio.com/items?itemName=ctf0.local-history-new"
author:
published:
created: 2026-06-30
description: "Extension for Visual Studio Code - Save files into local history"
tags:
  - "clippings"
taxonomy: { doc_category: [vscode] }
---
## 本地历史记录

基于 [https://github.com/zabel-xyz/local-history，该项目似乎已停止维护](https://github.com/zabel-xyz/local-history，该项目似乎已停止维护)

- 查看更新日志

> ## 本地历史
> 
> 一款用于维护文件本地历史的可视化源代码插件。
> 
> 每次修改文件时，旧内容的副本都会保存在本地历史中。您可以随时将当前文件与历史记录中的任意早期版本进行对比。在误改或误删文件时，它能帮您快速恢复；当工作区遭遇严重问题时，它也能助您一臂之力。每个文件的修订版本均存储在工作区目录下的 \`.history\` 文件夹中的独立文件内（您也可以自定义保存路径，详见 \`local-history.path\`）。例如： `.history/foo/bar/myFile_20151212205930.ts`
> 
> 您可以在资源管理器面板中通过 `local-history tree` 轻松在历史文件之间切换。
> 
> 当您单击某个文件时，将显示与当前版本的对比结果。  
> 您还可以通过上下文菜单访问其他命令。
> 
> 您可以筛选不同的视图：
> 
> - 全部
> - 当前文件（默认）
> - 指定文件（可输入搜索模式）
> 
> 显示的文件取决于设置。如需查看更多，请使用“搜索+”图标。 `localHistory.maxDisplay`
> 
> ## 设置
> 
> ```markdown
> "localHistory.daysLimit":  30  // A day number to purge local history. (0: no purge)
> "localHistory.maxDisplay": 10  // A max files to display with local history commands
> "localHistory.saveDelay":   0  // A delay in seconds to save file in local history. {0: no delay}
> "localHistory.dateLocale":     // The locale to use when displaying date (e.g.: "fr-CH" or "en-GB" or ...)
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
> ## 命令 
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
> 当工作区中存在 \`.history\` 文件夹时，您可以添加 \`"files.exclude"\` 配置。这将隐藏 \`.history\` 文件夹并避免一些问题（例如 \`csproj\` 扩展名）。  
> 感谢 @pabloarista（问题 #13）

