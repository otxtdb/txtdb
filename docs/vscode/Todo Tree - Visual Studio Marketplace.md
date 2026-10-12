---
title: "Todo Tree - Visual Studio Marketplace"
source: "https://marketplace.visualstudio.com/items?itemName=Gruntfuggly.todo-tree"
author:
published:
created: 2026-08-26
description: "Extension for Visual Studio Code - Show TODO, FIXME, etc. comment tags in a tree view"
tags:
  - "clippings"
taxonomy: { doc_category: [vscode] }
---
## Todo 树

以树状视图显示 TODO、FIXME 等注释标签

## Todo Tree

该插件会使用 ripgrep 工具快速搜索工作区中包含 TODO、FIXME 等标记的注释内容，并以树状结构显示在活动栏中。用户还可以将此视图从活动栏拖放到资源管理器窗格中，或放到自己希望显示它的任何位置。

在树状结构中点击某个待办事项，即可打开 해당文件，并将光标定位到包含该待办事项的那一行上。

在已打开的文件中，也可以高亮显示那些被标记为“待办事项”的内容。

*请参阅维基页面以获取配置示例。*

![screenshot](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/screenshot.png)

*备注：*

- *用户* `rg.conf` *的文件被忽略了。*

## 突出显示

> 新功能！如果你只是想为标签设置不同的颜色，现在可以启用 `todo-tree.highlights.useColourScheme` 这一选项。这样就能按照定义的顺序，为标签应用一组可更换的颜色。

标签的高亮显示是可以配置的。可以使用 `defaultHighlight` 来为所有标签设置高亮效果。如果你需要为个别标签进行不同的配置，可以使用 `customHighlight` 。如果 `customHighlight` 中没有指定具体的设置，那么就会使用 `defaultHighlight` 中的值作为默认设置。

如果使用了子标签，还可以指定个性化的高亮显示效果。

<sup><em>Note: <code>defaultHighlight</code> is not applied to sub tags.</em></sup>

`defaultHighlight` 和 `customHighlight` 都支持以下设置：

`foreground` – 用于设置编辑器中高亮显示部分以及标尺中标记对象的前景色。

`background` – 用于设置编辑器中高亮显示部分的背景颜色。

<sup><em>Note: Foreground and background colours can be specified using <a href="https://en.wikipedia.org/wiki/Web_colors">HTML/CSS colour names</a> (e.g. "Salmon"), RGB hex values (e.g. "#80FF00"), RGB CSS style values (e.g. "rgb(255,128,0)" or colours from the current theme, e.g. <code>peekViewResult.background</code>. See <a href="https://code.visualstudio.com/api/references/theme-color">Theme Color</a> for the details. Hex and RGB values can also have an alpha specified, e.g. "#ff800080" or "rgba(255,128,0,0.5)".</em></sup>

`opacity` - 与背景颜色相关的百分比值。100%的颜色会产生不透明的背景，从而掩盖选区和其它装饰元素。

<sup><em>Note: opacity can only be specified when hex or RGB colours are used.</em></sup>

`fontWeight` 、 `fontStyle` 、 `textDecoration` 可以使用标准的 CSS 属性来设置高亮显示的效果。

`borderRadius` – 用于设置高亮背景的边框半径。

`icon` – 用于在树形视图中设置不同的图标。图标必须是有效的图标格式（参见 [https://octicons.github.com），或者可以是代码图标（参见](https://octicons.github.xn--com\),\(-tx8ipa123i0ma21zvv8ayel4ig2k1e610axu8a/) [https://microsoft.github.io/vscode-codicons/dist/codicon.html）。如果使用的是代码图标，请使用“$](https://microsoft.github.io/vscode-codicons/dist/codicon.html%EF%BC%89%E3%80%82%E5%A6%82%E6%9E%9C%E4%BD%BF%E7%94%A8%E7%9A%84%E6%98%AF%E4%BB%A3%E7%A0%81%E5%9B%BE%E6%A0%87%EF%BC%8C%E8%AF%B7%E4%BD%BF%E7%94%A8%E2%80%9C$) (icon)”格式进行指定。如果图标无效，默认会使用勾选标记图标。如果你希望使用活动视图中的图标，可以使用“todo-tree”或“todo-tree-filled”作为图标名称。

`iconColour` – 用于设置树形菜单中图标的颜色。如果未指定颜色，系统会尝试使用前景色或背景色。颜色可以根据前景色和背景色来指定，但请参考下面的说明。

<sup><em>Note: Theme colours are only supported when using codicons. Hex, RGB and HTML colours are only supported when using octicons or the default icon.</em></sup>

`gutterIcon` - 设置为 true 时，会在编辑器的侧边栏中显示图标。

<sup><em>Note: Unfortunately, only octicons and the todo-tree icon can be displayed in the gutter.</em></sup>

`rulerColour` – 用于设置概览标尺中标记的颜色。如果未指定颜色，则默认使用前景色。颜色可以根据前景色和背景色的规则来设置。

`rulerOpacity` – 用于设置标尺标记的不透明度。

<sup><em>Note: Only works with hex and RGB colour settings.</em></sup>

`rulerLane` – 用于设置概览标尺中标记的所属通道。如果未指定，则默认使用右侧通道。可以使用“left”、“center”、“right”或“full”中的某个选项。也可以使用“none”来禁用标尺上的标记。

`type` - 用于控制在编辑器中哪些部分会被高亮显示。有效的值包括：

- `tag` – 只突出了那个标签
- `text` – 突出显示标签以及标签后面的所有文本
- `tag-and-comment` – 高亮显示注释中的字符（或匹配的开始位置），同时也会标出标签部分
- `tag-and-subTag` – 如上所述，但允许子标签也被高亮显示（高亮颜色可以在自定义高亮设置中定义）
- `text-and-comment` – 高亮显示注释中的字符（或匹配开始的文本）、标签以及标签之后的文本
- `line` – 高亮显示了包含该标签的整行文本
- `whole-line` – 高亮显示包含该标签的整行文本，使文本在编辑器的窗口中显示得更加清晰。
- `capture-groups:n,m...` - 高亮显示正则表达式中的捕获组，其中'n'表示在正则表达式中的索引位置
- `none` - 禁用文档中的高亮显示功能

`hideFromTree` – 用于在树状结构中隐藏标签，但在文件中仍会以高亮方式显示出来。

`hideFromStatusBar` - 防止该标签被计入状态栏的计数中

`hideFromActivityBar` - 防止该标签被计入活动栏中的徽章数量中

示例：

```json
"todo-tree.highlights.defaultHighlight": {
    "icon": "alert",
    "type": "text",
    "foreground": "red",
    "background": "white",
    "opacity": 50,
    "iconColour": "blue"
},
"todo-tree.highlights.customHighlight": {
    "TODO": {
        "icon": "check",
        "type": "line"
    },
    "FIXME": {
        "foreground": "black",
        "iconColour": "yellow",
        "gutterIcon": true
    }
}
```

<sup><em>Note: The highlight configuration is separate from the settings for the search. Adding settings in <code>customHighlight</code> does not automatically add the tags into <code>todo-tree.general.tags</code>.</em></sup>

<sup>*Note: Using the <code>capture-groups</code> setting in <code>type</code> may have an impact on performance with large files.</sup>

## 正在安装中

你可以通过这里的 Visual Studio Marketplace 来安装该扩展程序的最新版本。

或者，打开 Visual Studio Code，按 `Ctrl+P` 或 `Cmd+P` ，然后输入：

> 执行命令：ext install Gruntfuggly.todo-tree

### 源代码

该源代码可在 GitHub 上查看。

## 控制装置/操控方式

树状视图标题栏中可以包含以下按钮：

\- 收起所有树状节点  
\- 展开所有树节点  
\- 将树状视图显示为扁平列表，同时显示每个待办事项的完整文件路径。  
\- 将该视图以标签列表的形式显示出来  
\- 以树状视图显示，每个文件夹都可以展开查看其子内容（默认设置）  
\- 按标签对任务列表中的待办事项进行分类  
\- 按文件对待办事项进行分类整理（默认设置）  
\- 仅显示与所输入的过滤条件相匹配的项。  
\- 移除所有当前生效的过滤条件  
\- 重新构建树结构  
\- 仅显示来自已打开文件的标签  
\- 显示当前文件中的标签信息  
\- 仅显示工作区中的标签  
\- 显示工作区及已打开文件中的标签  
\- 显示树状结构中的当前文件  
\- 将树形结构的内容导出到文件中

## 文件夹筛选器上下文菜单

在树状视图中右键点击，会弹出包含以下选项的上下文菜单：

隐藏此文件夹/隐藏此文件——将该文件夹或文件从目录结构中移除。  
仅显示此文件夹——从目录树中删除所有其他文件夹和子文件夹。  
仅显示此文件夹及其子文件夹——从目录树中删除其他文件夹，但保留子文件夹。  
重置文件夹筛选条件——重置之前使用上述规则筛选过的所有文件夹。  
切换徽章显示状态——启用/禁用 SCM 装饰元素  
切换压缩文件夹功能——启用/禁用压缩文件夹名显示  
切换项目计数功能——启用/禁用标签的计数功能  
仅扫描已打开的文件——仅显示在 VSCode 中已打开的文件中的待办事项（不进行搜索）  
仅扫描当前文件——仅显示当前打开文件中的待办事项。  
扫描工作区并打开文件——显示工作区中的待办事项以及所有已打开的文件  
仅扫描工作区——仅显示该工作区中的待办事项（需要手动刷新）  
展开树结构/折叠树结构——展开或折叠整个树结构。 显示树状视图/显示平面视图/仅显示标签——更改树状视图的显示方式。 按标签分组/取消按标签分组——切换按标签对项目进行分组的模式。 按子标签分组/取消按子标签分组——切换按子标签对项目进行分组的模式。 导出树结构——将树结构的内容导出为文件。 在树结构中显示当前文件——如果当前有编辑中的文件，則在树结构中显示该文件。

<sup><em>Note: The current filters are shown in the debug log. Also, the filter can always be reset by right clicking the <strong>Nothing Found</strong> item in the tree. If your tree becomes invisible because everything is filtered and <code>hideTreeWhenEmpty</code> is set to true, you can reset the filter by pressing <strong>F1</strong> and selecting the <strong>Todo Tree: Reset Folder Filter</strong> command.</em></sup>

## 命令/指令

为了更方便地设置这些标签，共有两个可用命令：

Todo Tree：添加标签——允许为用户输入用于搜索的新标签

“Todo Tree”功能中的“移除标签”选项：会显示当前所有的标签，用户可以从中选择需要移除的标签。

<sup><em>Note: The Remove Tag command can be used to show current tags - just press Escape or Enter with out selecting any to close it.</em></sup>

### 出口

可以使用“Todo Tree: Export Tree”功能来导出树形结构中的内容。系统会按照 `todo-tree.general.exportPath` 所指定的路径创建一个只读文件。该文件可以通过“文件：另存为…”来保存。注意：目前“文件：保存”功能无法使用，这似乎是 VSCode 的漏洞（详见 [https://github.com/microsoft/vscode/issues/101952）。](https://github.com/microsoft/vscode/issues/101952%EF%BC%89%E3%80%82)

### 切换范围

Todo Tree：切换范围——显示可选择的已配置范围列表

“待办事项树：跳转到下一个”和“待办事项树：跳转到上一个”这两个命令可以用来在当前编辑器中切换到下一个或上一个待办事项。

## 配置

该扩展功能可按以下方式自定义（括号内为默认值）：

todo-tree.general.debug ( `false` )  
在输出视图中显示调试信息。

todo-tree.general.periodicRefreshInteval ( `0` )  
自动刷新树状结构的间隔时间（以分钟为单位）。将此值设置为“0”可取消自动刷新功能；否则，输入所需的刷新间隔分钟数。注意：通常情况下无需设置此参数，因为当文件发生变化时，树状结构会自动刷新。

todo-tree.general.automaticGitRefreshInterval ( `0` )  
当仓库发生更新时，用于自动刷新目录结构的轮询间隔时间（以秒为单位）。该功能会检查仓库的 HEAD 指针是否发生了变化，如果发生了变化，则会重新扫描工作区。该功能取代了传统的文件监视功能。将此值设置为“0”即可禁用该功能；否则，请输入希望的轮询间隔时间。

todo-tree.general.exportPath ( `~/todo-tree-%Y%m%d-%H%M.txt` )  
导出树形结构时所使用的路径。环境变量会被替换掉，例如 `${HOME}` 。该路径会经过 strftime 函数进行处理（详见 [https://github.com/samsonjs/strftime）。若要将数据导出为](https://github.com/samsonjs/strftime%EF%BC%89%E3%80%82%E8%8B%A5%E8%A6%81%E5%B0%86%E6%95%B0%E6%8D%AE%E5%AF%BC%E5%87%BA%E4%B8%BA) JSON 格式，请将扩展名设置为 `.json` 。

todo-tree.general.rootFolder ( `""` )  
默认情况下，所有打开的工作空间在视图中都会以树状结构呈现。可以使用此功能来指定某个文件夹作为树的根目录。此外，还可以使用环境变量，或者直接使用${workspaceFolder}。例如：  
`"todo-tree.general.rootFolder": "${workspaceFolder}/test"`  
或者  
`"todo-tree.general.rootFolder": "${HOME}/project"`.

<sup><em>Note: Other open files (outside of the rootFolder) will be shown (as they are opened) with their full path in brackets.</em></sup>

todo-tree.general.schemes ( `['file','ssh','untitled']` )  
编辑器提供了用于查找“TODO”项的规则。例如，若要在配置文件中查找“TODO”项，可添加 `vscode-userdata` ；若要在输出窗口中查找“TODO”项，则可添加 `output` 。

todo-tree.general.tags ( `["TODO","FIXME","BUG"]` )  
这定义了那些被识别为“待办事项”的标签。该列表会自动被添加到正则表达式中。

todo-tree.general.tagGroups ( `{}` )  
此设置允许将多个标签视为一个整体来处理。例如：

```json
"todo-tree.general.tagGroups": {
    "FIXME": [
        "FIXME",
        "FIXIT",
        "FIX",
    ]
},
```

这将把 `FIXME` 、 `FIXIT` 或 `FIX` 中的任何一个都视为 `FIXME` 。当树木结构按标签进行分组时，所有这些元素都会显示在 `FIXME` 节点下。这也意味着，自定义高亮效果是应用到整个分组上的，而不是针对每种标签类型分别应用的。

<sup><em>Note: all tags in the group should also appear in <code>todo-tree.general.tags</code>.</em></sup>

todo-tree.general.revealBehaviour ( `start of todo` )  
在点击树状结构中的待办事项时，可以更改光标的移动方式。您可以选择以下选项： `start of line` start of todo `leave focus in tree` （将光标移至该待办事项的起始位置）、 `end of todo` （将光标移至该待办事项的末尾）、 `  （将光标移至该行的开头）。或者选择  ` ，这样光标仍会保留在树状结构中，从而可以继续使用键盘来导航树状结构。

todo-tree.general.statusBar ( `none` )  
在状态栏中显示什么内容：什么都不显示（ `tags` none `top three` ）、总数（ `current file` total `  ）、每个标签的计数（  ` ）、排名前三的标签的计数（ `  ），或者仅显示当前文件的计数（  ` ）。

todo-tree.general.statusBarClickBehaviour ( `reveal` )  
可以将点击状态栏时的操作方式设置为：在各种状态栏显示格式之间切换（ `toggle highlights` cycle `  ）、显示树状结构（  ` reveal `  ），或者切换高亮显示模式（  ` ）。

todo-tree.general.showIconsInsteadOfTagsInStatusBar ( `false` )  
在状态栏中显示图标，而非标签。

todo-tree.general.showActivityBarBadge ( `false` )  
在活动栏中显示一个徽章，用以表明已找到的待办事项的总数。

<sup><em>Note: When the tree view is in the Explorer pane, the badge is displayed on the Explorer icon, which may not be desirable.</em></sup>

todo-tree.filtering.includeGlobs ( `[]` )  
用于通过指定模式来限制搜索结果的匹配范围。例如，使用 `[\"**/unit-tests/*.js\"]` 可以只显示位于单元测试子文件夹中的.js 文件。这种模式非常有用。

<sup><em>Note: globs paths are absolute - not relative to the current workspace.</em></sup>

todo-tree.filtering.excludeGlobs ( `["**/node_modules/*/**"]` )  
用于通过排除规则来限制搜索结果的匹配项（在 applyGlobs 之后使用）。例如， `[\"**/*.txt\"]` 可用于忽略所有.txt 文件。

<sup><em>Note: <code>node_modules</code> are excluded by default.</em></sup>

todo-tree.filtering.includedWorkspaces ( `[]` )  
需要作为树结构中的根节点的工作区名称列表（可以使用通配符）。如果该数组为空，则表示包含所有工作区文件夹。

**todo-tree.filtering.excludedWorkspaces** (`[]`)  
需要排除在树结构中的工作区名称列表（可使用通配符）。

todo-tree.filtering.passGlobsToRipgrep ( `true` )  
将此选项设置为“false”，则会在搜索完成后再应用全局替换规则（即保持旧有的行为方式）。

todo-tree.filtering.useBuiltInExcludes ( `none` )  
将其设置为使用 VSCode 内置的文件排除或搜索排除规则。可选值为： `search excludes` none `file and search excludes` 、 `file excludes` （使用“文件：排除”规则）、 `  （使用“搜索：排除”规则），或  ` （同时使用两者）。

todo-tree.filtering.ignoreGitSubmodules ( `false` )  
如果情况属实，那么在搜索过程中，任何包含 `.git` 文件的子文件夹都将被忽略。

todo-tree.filtering.includeHiddenFiles ( `false` )  
如果属实，那么以点（.）开头的文件也会被包含在内。

**todo-tree.highlights.enabled** (`true`)  
将此选项设置为“false”即可关闭高亮显示功能。

todo-tree.highlights.highlightDelay ( `500` )  
高亮显示之前的延迟时间（以毫秒为单位）。

todo-tree.highlights.defaultHighlight ( `{}` )  
设置默认高亮显示内容。例如：

```json
{
    "foreground": "white",
    "background": "red",
    "icon": "check",
    "type": "text"
}
```

todo-tree.highlights.customHighlight ( `{}` )  
为每个标签（或标签组）设置高亮显示内容。例如：

```json
{
    "TODO": {
        "foreground": "white",
        "type": "text"
    },
    "FIXME": {
        "icon": "beaker"
    }
}
```

todo-tree.highlights.useColourScheme ( `false` )  
使用简单的方案来为高亮部分着色即可。只需按照标签的顺序来应用相应的颜色即可。相比为每个标签单独设置高亮颜色，这种方式要简单得多。

<sup><em>Note: The colour scheme overrides the colours defined in</em> <code>todo-tree.highlights.defaultHighlight</code> <em>but not</em> <code>todo-tree.highlights.customHighlight</code><em>.</em></sup>

todo-tree.highlights.backgroundColourScheme ( `["red","orange","yellow","green","blue","indigo","violet"]` )  
用于与 `todo-tree.highlights.useColourScheme` 一起使用，以指定高亮部分的颜色。颜色的定义方式与其他颜色相同（例如十六进制代码、主题名称等）。如果标签的数量多于颜色的数量，则会重复使用这些标签来指定颜色。

todo-tree.highlights.foreroundColourScheme ( `["white","black","black","white","white","white","black"]` )  
定义了与 `todo-tree.highlights.backgroundColourScheme` 一起使用来为高亮部分着色的颜色。这些颜色应与背景颜色相得益彰。

todo-tree.regex.enableMultiLine ( `false` )  
通常，多行支持是通过在正则表达式中检测到 `\n` 的存在来启用的。将此参数设置为 `true` ，则多行支持将默认被启用。这样一来， `[\s\S]` 就可以用来匹配包括换行符在内的所有字符了。

todo-tree.regex.regex ( (//|#|<!--|;|/\\\\\*|^|^\[ \\\\t\]\*(-|\\\\d+.))\\\\s\*($TAGS) )

这定义了用于识别待办事项的正则表达式。默认情况下，该正则表达式会搜索以 // 、 # 、 ; 、 <!-- 或 /\* 开头的注释中的标签，同时也会识别 Markdown 格式的待办事项列表。这样应该能覆盖大多数语言环境。不过，如果你想进一步精确匹配，请确保保留 ($TAGS) ，因为 ($TAGS) 会被替换为完整的标签列表。为了使某些扩展功能正常工作，正则表达式中必须包含 ($TAGS) 。不过，即使不显式展开标签列表，基本功能仍然可以正常使用。

<sup><em>Note: This is a <a href="https://docs.rs/regex/1.0.0/regex">Rust regular expression</a>, not javascript.</em></sup>

todo-tree.regex.subTagRegex：这是一条用于处理标签右侧文本的正则表达式。例如，它可以用来提取子标签或删除不需要的字符。所有与这条正则表达式匹配的内容都会从文本中被删除。如果正则表达式中包含了捕获组，那么这些捕获到的内容会被提取出来，形成子标签。这些子标签可以在树结构中被用来对相似的标签进行分组。此外，子标签还可以在 `todo-tree.tree.subTagClickUrl` 和 `todo-tree.tree.labelFormat` 中作为占位符使用。通过在 `todo-tree.highlights.customHighlights` 设置中指定相应的部分，还可以突出显示子标签。如果想突出显示子标签本身，可以在该标签的自定义高亮设置中，将“type”设置为“tag-and-subTag”。

示例：

`"^:\s*"` 可用于删除标签后面的冒号。

`"^\s*\((.*)\)"` 可用于提取该标签后面括号内的任何内容，并将其作为子标签使用。

todo-tree.regex.regexCaseSensitive ( `true` )  
将此参数设置为“false”，则无论大小写如何，标签都能被匹配到。

todo-tree.ripgrep.ripgrep ( `""` )  
通常情况下，该插件会在需要时自动找到 ripgrep 的安装位置。如果你想使用 ripgrep 的其他版本，请将该参数设置为该版本的安装路径。

todo-tree.ripgrep.ripgrepArgs ( `"--max-columns=1000"` )  
使用此方式可以向 ripgrep 传递额外的参数。例如，使用 `"-i"` 可使搜索不区分大小写。请谨慎使用！

todo-tree.ripgrep.ripgrepMaxBuffer ( `200` )  
默认情况下，ripgrep 程序会使用 200KB 的缓冲区大小。不过，对于那些需要显示的标签来说，这个大小有时不够用。可以通过调整此设置来增加缓冲区大小。

todo-tree.ripgrep.usePatternFile ( `true` )  
默认情况下，ripgrep 会使用模式文件来进行匹配操作。如果您在删除该模式文件时遇到问题，可以将此参数设置为“false”，从而恢复为使用传统的正则表达式来指定匹配规则的方式。

todo-tree.tree.hideTreeWhenEmpty ( `true` )  
通常情况下，如果未找到任何内容，该树形结构会从浏览视图中消失。将此选项设置为“false”即可使该树形结构保持显示状态。

todo-tree.tree.filterCaseSensitive ( `false` )  
如果需要按大小写进行过滤，请使用此选项。

<sup><em>Note: this does not the apply to the search</em>.</sup>

todo-tree.tree.trackFile ( `true` )  
如果您想阻止在树状视图中显示已打开的文件，请将此选项设置为“false”。

todo-tree.tree.showBadges ( `true` )  
将此参数设置为“false”，即可取消在树状结构中显示 SCM 状态和徽章。\*

<sup><em>Note: This also unfortunately turns off themed icons.</em></sup>

**todo-tree.tree.expanded <sup>*</sup>** (`false`)  
如果希望新视图默认被展开，可以将此参数设置为 true。

**todo-tree.tree.flat <sup>*</sup>** (`false`)  
如果希望新视图默认情况下是平铺式的，可以将此参数设置为 true。

**todo-tree.tree.grouped <sup>*</sup>** (`false`)  
如果希望新视图默认时分组，可以将此参数设置为“true”。

**todo-tree.tree.tags 仅限 <sup>*</sup>** 用户使用 ( `false` 除外)  
如果希望默认情况下只显示带有标签的新视图，可以将此参数设置为 true。

**todo-tree.tree.sortTagsOnlyViewAlphabetically** (`false`)  
仅通过标签对物品进行排序，而不是按照标签列表的顺序进行排列。这样就能实现按字母顺序查看物品的功能。

**todo-tree.tree.showCountsInTree** (`false`)  
设置为 true 以显示树中待办事项的数量。

todo-tree.tree-labelFormat ( `${tag} ${after}` )  
TODO 项标签的格式。可用的占位符包括： `${line}` 、 `${column}` 、 `${tag}` 、 `${before}` （标签前的文本）、 `${after}` （标签后的文本）、 `${filename}` 、 `${filepath}` 以及 `${afterOrBefore}` （如果“之后”文本为空，则使用“之前”文本）。当使用 `${tag}` 或 `${subTag}` 时，还可以对文本进行“大写”、“小写”或“首字母大写”的处理，例如 `${tag:lowercase}` 。

todo-tree.tree.scanMode ( `workspace` )  
默认情况下，该扩展程序会扫描整个工作区( `current file` workspace `  )。你可以选择仅扫描打开的文件(  `open files `  )，或者仅扫描当前文件(  ` )。

todo-tree.tree.showScanModeButton ( `false` )  
在树形视图的标题栏中添加一个按钮，用于切换扫描模式（参见上文）。

**todo-tree.tree.hideIconsWhenGroupedByTag** (`false`)  
在按标签分组时隐藏项目图标。

todo-tree.tree.sort( `true` )  
ripgrep 通过多线程进行搜索，从而提高性能。在目录被填充后，会对其进行排序，从而保持稳定性。如果您希望使用 ripgrep 自带的排序参数，可以将此参数设置为 false。

<sup><em>Note: Depending on what scan mode you select, you may also want to disable auto-refresh when disabling the sort, otherwise the tree may still be unstable.</em></sup>

**todo-tree.tree.disableCompactFolders** (`false`)  
通常情况下，该树会遵循 VSCode 的 `explorer.compactFolders` 设置。如果你想要禁用待办事项树中压缩文件夹的功能，可以将此设置设置为 true。

todo-tree.treetooltipFormat ( `${filepath}, ${line}` )  
树形项目工具提示的格式。使用与 `todo-tree.tree.labelFormat` 相同的占位符（参见上文）。

**todo-tree.tree.subTagClickUrl**  
一个 URL 地址（可以包含占位符），当在树状结构的子标签上点击时就会打开该页面。例如，如果子标签提取了用户名，那么可以使用 `https://github.com/${subTag}` 作为 URL 地址。

todo-tree.tree.buttons.reveal ( `true` )  
在树视图的标题栏中添加一个按钮，用于显示当前项的信息（仅当该功能未被启用时生效）。

todo-tree.tree.buttons.scanMode ( `false` )  
在树形视图的标题栏中添加一个按钮，用于切换扫描模式设置。

todo-tree.tree.buttons.viewStyle ( `true` )  
在树视图的标题栏中添加一个按钮，用于切换视图模式（树状视图、平面视图或仅标签视图）。

**todo-tree.tree.buttons.groupByTag** (`true`)  
在树视图的标题栏中添加一个按钮，用于启用按标签分组项目的功能。

**todo-tree.tree.buttons.groupBySubTag** (`false`)  
在树视图的标题栏中添加一个按钮，以便按子标签对项目进行分组。

<sup><em>Note: This button will only be visible when sub tags have been found and are present in the tree.</em></sup>

todo-tree.tree.buttons.filter ( `true` )  
在树视图的标题栏中添加一个按钮，通过输入一些文本来实现对树状结构的过滤功能。

**todo-tree.tree.buttons.refresh** (`true`)  
在树形视图标题栏中显示一个刷新按钮。

**todo-tree.tree.buttons.expand** (`true`)  
在树视图的标题栏中显示一个按钮，可以用来展开或折叠整个树状结构。

**todo-tree.tree.buttons.export** (`false`)  
在树视图的标题栏中添加一个按钮，用于创建一个文本文件，其中包含树状结构的内容。

<sup>*</sup> *仅适用于新的工作区。当工作区的视图发生更改后，当前状态会被保留下来。*

todo-tree.filtering.scopes ( `{}` )  
定义了一组文件作用域，可以通过 todo-tree.switchScope 命令快速在这些作用域之间切换。

这是一个复杂的配置属性，只能通过配置 JSON 文件来进行设置。例如：

```json
"todo-tree.scopes": [
    {
        "name": "Production ",
        "excludeGlobs": [
            "**/tests/**"
        ]
    },
    {
        "name": "Tests",
        "includeGlobs": [
            "**/tests/**"
        ]
    },
    {
        "name": "All"
    }
]
```

### 多行待办事项列表

如果正则表达式包含 `\n` ，那么多行 TODO 列表将被启用。在这种模式下，搜索结果的处理方式会有所不同。如果找到的结果不包含 `todo-tree.general.tags` 中的任何标签，那么就会认为这些结果属于之前有标签的结果。例如，如果你将正则表达式设置为如下形式：

```json
"todo-tree.regex.regex": "(//)\\s*($TAGS).*(\\n\\s*//\\s{2,}.*)*"
```

这将能够处理多行待办事项，在这些待办事项中，额外的行之间至少会有两个空格，这两个空格位于注释字符和待办事项之间。例如：

```json
// TODO multiline example
//  second line
//  third line
```

如果你想要匹配 C++风格的多行注释块中的多个待办事项，你需要使用类似这样的工具：

```json
"todo-tree.regex.regex": "(/\\*)\\s*($TAGS).*(\\n\\s*(//|/\\*|\\*\\*)\\s{2,}.*)*"
```

应该与以下内容匹配：

```json
/* TODO multiline example
**  second line
**  third line
*/
```

<sup><em>Note: If you are modifying settings using the settings GUI, you don't need to escape each backslash.</em></sup>

**警告：多行待办事项在使用 Markdown 格式时可能会出现问题，也可能产生其他意想不到的效果。此外，性能也可能下降。**

### 不包括文件和文件夹

要限制搜索的文件夹范围，可以定义 `todo-tree.filtering.includeGlobs` 。这是一个包含模糊匹配项的数组，搜索结果会与这些项进行匹配。如果搜索结果符合任何一项匹配项，那么该项就会显示在结果中。默认情况下，这个数组是空的，表示搜索所有文件夹。有关模糊匹配项的更多信息，请参考这里。

<sup><em>Note: globs paths are absolute - not relative to the current workspace.</em></sup>

如果你想将某些文件夹或文件排除在搜索结果之外，可以定义 `todo-tree.filtering.excludeGlobs` 这样的模式。如果搜索结果包含这些模式中的任何一个，那么这些结果将被忽略。

你也可以使用上下文菜单来指定是否将某些文件夹包含或排除在树形结构中之外。这种文件夹过滤功能是独立于“包含/排除通配词”功能的。

<sup><em>Note: By default, ripgrep ignores files and folders from your <code>.gitignore</code> or <code>.ignore</code> files. If you want to include these files, set</em> <code>todo-tree.ripgrep.ripgrepArgs</code> <em>to</em> <code>--no-ignore</code>.</sup>

### Markdown 支持

在最初编写这个扩展功能时，只是通过在默认正则表达式中添加一种模式来简单地支持基本的 Markdown 格式，以匹配“ `- [ ]` ”。不过，处理 Markdown 格式的待办事项更好的方法是，在正则表达式的第一部分中添加“ `(-|\d+.)` ”，然后在 `settings.json` 中的标签列表中添加“ `[ ]` ”和“ `[x]` ”。例如：

```json
"todo-tree.regex.regex": "(//|#|<!--|;|/\\*|^|^\\s*(-|\\d+.))\\s*($TAGS)"
"todo-tree.general.tags": [
        "BUG",
        "HACK",
        "FIXME",
        "TODO",
        "XXX",
        "[ ]",
        "[x]"
    ]
```

<sup><em>Note: If you modify the settings via the GUI, replace every instance of</em> <code>\\</code> <em>in the regex setting with</em> <code>\</code>.</sup>

那么，这将匹配所有后续的条目：

```markdown
- [ ] Do something
- [x] Something I've done

1. [ ] Do this first
2. [ ] Followed by this
```

这还允许应用自定义的高亮显示效果，例如：

```json
"todo-tree.highlights.customHighlight": {
    "[ ]": {
        "background": "#ff000080"
    },
    "[x]": {
        "background": "#00ff0080"
    }
}
```

这将把待处理的待办事项标记为红色，而已完成的待办事项则标记为绿色。

最后，这将使得按标签（以及子标签）进行分组变得可行，并且在显示状态栏中的计数信息时，这种分组方式也会表现得更加理想。

<sup><em>Note: The default regex will be updated to reflect these changes at some point in the future.</em></sup>

## 已知问题

仅当您的配置使用 `todo-tree.general.tags` 设置定义标签时，按标签分组才有效。在旧版本的功能扩展中，标签是直接定义在 `todo-tree.regex.regex` 中的；而现在，正则表达式将$TAGS 替换为 `todo-tree.general.tags` 中的内容。

对于 Markdown 任务列表项来说，使用标签进行分组是不适用的，因为这类列表项并没有可供分组的标签。在这种情况下，树形结构会同时显示文件名称和标签组。

当按标签分组时，在树形视图中跟踪该文件会显示第一个匹配的标签。

当没有当前的工作区时，树形菜单中会显示默认的图标。

## 捐款

如果您认为这个扩展功能很有用，请随时在这里进行捐赠。谢谢！

### 致谢/鸣谢

使用了经过修改版的 ripgrep-js 工具。

这些主要图标最初由 Freepik 在 www.flaticon.com 上设计，其使用权限遵循 CC 3.0 BY 协议。

这些由 Vaadin 制作的树状视图图标，来源于 www.flaticon.com，其授权协议为 CC 3.0 BY 许可。

这些标签图标由 Dave Gandy 在 www.flaticon.com 上设计，其使用许可遵循 CC 3.0 BY 协议。

该标签图标由 www.flaticon.com 提供的 Vectors Market 制作，其使用许可遵循 CC 3.0 BY 协议。

由 Gregor Cresnar 创作的 Reveal Icon 图标，来自 www.flaticon.com

许多图标已经由 johnletey 更新，以匹配新的 VS Code 1.37.0 界面风格。非常感谢！

#### 翻译结果

由 loniceras 翻译的简体中文版本。