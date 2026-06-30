---
title: "Error Lens - Visual Studio Marketplace"
source: "https://marketplace.visualstudio.com/items?itemName=usernamehw.errorlens"
author:
published:
created: 2026-06-30
description: "Extension for Visual Studio Code - Improve highlighting of errors, warnings and other language diagnostics."
tags:
  - "clippings"
taxonomy: { doc_category: [vscode] }
---
[跳转至内容部分](#start-of-content)

## 错误镜头/有缺陷的镜头

## 亚历山大

|

9,201,320 次安装量

| (187) | 免费

改进对错误、警告以及其他语言相关问题的提示方式。

ErrorLens 通过让诊断信息更显眼来提升语言诊断功能的效率：无论语言处理过程中在哪一行产生了诊断信息，ErrorLens 都会将该行全部高亮显示，并同时将诊断信息直接显示在该行上。

![Demo image](https://raw.githubusercontent.com/usernamehw/vscode-error-lens/master/img/demo.png)

## 特点/特色

- 高亮显示包含诊断信息的行。
- 将诊断信息以文本形式添加到该行末尾。
- 在侧边栏中显示图标
- 在状态栏中显示消息

## 命令（15 条）

| 命令/指令 | 描述 |
| --- | --- |
| errorLens.toggle | 错误透镜：切换所有功能的开启/关闭状态（切换全局设置 `"errorLens.enabled"` ） |
| errorLens.toggleError | 错误显示功能：在 `"errorLens.enabledDiagnosticLevels"` 设置中启用/禁用错误信息的显示。 |
| errorLens.toggleWarning | 错误提示功能：在 `"errorLens.enabledDiagnosticLevels"` 设置中开启/关闭警告提示。 |
| errorLens.toggleInfo | 错误透镜：在 `"errorLens.enabledDiagnosticLevels"` 设置中启用/禁用相关功能。 |
| errorLens.toggleHint | 错误提示功能：在 `"errorLens.enabledDiagnosticLevels"` 设置中可开启/关闭该功能。 |
| errorLens.toggleInlineMessage | 错误透镜：切换全局设置 `"errorLens.messageEnabled"` 。 |
| errorLens.searchForProblem | 错误透镜：默认浏览器中存在的缺陷问题（由 `errorLens.searchForProblemQuery` 设置所控制）。 |
| errorLens.selectProblem | 错误范围：将编辑器的选择范围设置为出现问题的区域（由 `errorLens.selectProblemType` 设置来控制）。 |
| errorlens.toggleWorkspace | 错误处理机制：通过文件系统路径来决定是排除还是包含当前工作区。 |
| errorLens.disableLine | 错误处理：为该行添加注释，以使 linter 规则不再对该行进行检测。注释的格式由 `"errorLens.disableLineComments"` 设置决定。 |
| errorLens.findLinterRuleDefinition | 错误检测机制：在本地的代码检查工具文件中搜索相应的规则定义。目标文件由“errorLens.lintFilePaths”设置来指定。 |
| errorLens.copyProblemMessage | 错误提示：将错误信息复制到剪贴板中（复制位置为当前光标所在处）。 |
| errorLens.excludeProblem | 错误处理功能：忽略当前光标所在位置的问题（需在设置中启用该功能）。 |
| errorLens.copyProblemCode | 错误提示：请将错误代码复制到剪贴板中（复制位置为当前光标所在处）。 |
| errorLens.updateEverything | 错误处理：更新所有装饰元素。支持参数 {"kind": "update" \| "clear"} |

## 设置 (75)

> Error Lens 扩展设置以 `errorLens. 开头。`

| 设置 | 默认值 | 描述 |
| --- | --- | --- |
| 已启用 | **真实/正确** | 控制所有的装饰元素和功能（命令除外）。 |
| respectUpstreamEnabled | {"enabled":true, "inlineMessage":true, "gutter":true, "statusBar":false} | 启用该功能后，扩展程序会遵循 VSCode 的全局设置 `#problems.visibility#` 。（1.85.0 版本更新日志） |
| enabledInMergeConflict | **真实/正确** | 用于控制：当编辑器中存在 git 合并冲突标记 `<<<<<<<` 、 `=======` 或 `>>>>>>>` 时，是否显示相关装饰元素。 |
| 字体家族 | "" | 内嵌消息所使用的字体系列。演示用。可能会破坏 `#errorLens.alignMessage# 的格式。` |
| 字体粗细/字体重量 | “正常” | 内嵌消息的字体粗细。 `"normal"` 代表 400 号字体粗细， `"bold"` 代表 700 号字体粗细。演示用。 |
| fontStyle 斜体 | **虚假的/不真实的** | 启用该功能后，内嵌消息将以斜体字显示。演示版 |
| 字体大小 | "" | 内嵌消息的字体大小（以 CSS 单位表示）。使用负数值可以让字体大小相对于编辑器的默认字体大小来决定（例如： `-3px` ）。不过这种方式可能会破坏 `#errorLens.alignMessage#` 的格式。演示示例。 |
| 边际/利润空间 | “4ch” | 行尾最后一个单词与内联消息起始位置之间的距离（以 CSS 单位计）。演示用例 |
| alignMessage | {"start":0, "end":0, "minimumMargin":4, "padding":\[0, 0\], "useFixedPosition":true} | 对齐内联错误消息的显示位置（可以通过设置起始位置或结束位置来实现）。该功能仅适用于等宽字体。如需禁用此功能，请将“起始位置”和“结束位置”设置为 0。演示版。 |
| 边界/边缘 | \["", "", "", ""\] | 内嵌消息的边框。示例： `1px solid` 、 `1px dashed` 、 `2px dotted` 、 `1px solid [#00000050](https://github.com/usernamehw/vscode-error-lens/issues/00000050)` ……将此字段设置为空字符串即可取消该功能。演示版 |
| 填充物/衬垫 | "" | 内嵌消息的填充内容。当 `#errorLens.messageBackgroundMode#` 被设置为“message”时，该填充内容会显示出来。演示版 |
| borderRadius | “0.2em” | 内嵌消息的边框圆角。当 `#errorLens.messageBackgroundMode#` 设置为“message”时，该效果才会显示。演示版 |
| 启用诊断级别 | \["错误", "警告", "信息"\] | 可以自定义要突出显示的诊断级别/严重性。演示版 |
| messageTemplate | “$message” | 用于所有内嵌消息的模板。各项目之间的空格很重要。   变量列表：   \- `$message` - 诊断信息文本   \- `$count` - 该线路上的诊断项数量   \- `$severity` - 严重性前缀取自 `#errorLens.severityText#`   \- `$source` - 用于诊断的工具或来源，例如“eslint”   \- `$code` - 诊断演示程序的代码 |
| 消息最大字符数 | **500** | 如果内联消息的长度超过这个数值，就会将其截断。这样可以提升诊断消息较长时的性能。演示版 |
| 严重程度文本 | \["⛔", "⚠", "ℹ", "🍏"\] | 用 `#errorLens.messageTemplate#` 中的 `$severity` 变量来替换它。演示版 |
| 消息启用 | **真实/正确** | 控制是否显示内嵌消息（包括背景高亮效果）。演示版 |
| 消息背景模式 | “线” | 控制编辑器中内嵌消息的高亮显示方式：整行高亮/仅消息高亮/不高亮。演示版 |
| problemRangeDecorationEnabled | **虚假的/不真实的** | 选中后，会高亮显示整个出错范围。演示版 |
| 编辑器悬停部分启用 | {"messageEnabled":false, "sourceCodeEnabled":false, "buttonsEnabled":false} | 控制编辑器中哪些部分会显示悬停提示框。 |
| statusBarIconsEnabled | **虚假的/不真实的** | 启用该功能后，状态栏中会显示被标记出的错误/警告图标。演示版 |
| statusBarIconsPriority | **\-9000** | 通过调整数值的优先级，可以将状态栏图标向左或向右移动。 |
| statusBarIconsAlignment | “左” | 可以选择图标状态栏位于哪一侧：左侧或右侧。 |
| statusBarIconsTargetProblems | “全部” | 在图标状态栏中，应该使用哪些问题来作为计数题呢？ |
| statusBarIconsUseBackground | **真实/正确** | 启用该功能后，状态栏中的图标会以背景色来突出显示；禁用该功能后，则以前景色来突出显示。 |
| statusBarIconsAtZero | “移除背景” | 当没有错误/警告时该怎么做呢？可以将该元素隐藏起来，或者去掉其背景颜色。 |
| statusBarMessageEnabled | **虚假的/不真实的** | 启用该功能后，会在状态栏中显示相关消息。演示版。 |
| statusBarMessagePriority | **\-10000** | 通过调整数值的优先级，可以将状态栏中的消息向左或向右移动。 |
| statusBarMessageAlignment | “左” | 选择消息状态栏应位于哪一侧：左侧还是右侧。 |
| statusBarColorsEnabled | **虚假的/不真实的** | 启用该功能后，状态栏文本的颜色将采用消息装饰中的前景色。可使用的颜色为 `errorLens.statusBarErrorForeground` 、 `errorLens.statusBarWarningForeground` 、 `errorLens.statusBarInfoForeground` 、 `errorLens.statusBarHintForeground` 。演示版。 |
| 状态栏消息类型 | “activeLine” | 选择在状态栏中显示的内容：是显示最近的消息，还是仅显示当前活动线路上的消息。 |
| statusBarCommand | “goToProblem” | 点击状态栏时执行的命令。 |
| statusBarMessageTemplate | "" | 状态栏消息的模板。各项目之间的空格很重要。   变量列表：   \- `$message` - 诊断信息文本   \- `$count` - 该线路上的诊断项数量   \- `$severity` - 严重性前缀取自 `#errorLens.severityText#`   \- `$source` - 用于诊断的工具或来源，例如“eslint”   \- `$code` - 诊断代码 |
| 替换 | \[\] | 请指定需要转换的消息内容。例如，如果配置为\[{ matcher: ‘foo (.\*)’, message: ‘just $1’ }\]，那么消息“foo bar”将会显示为“just bar”。演示版 |
| 转化/转变 | {} | 针对特定问题，可以更改编辑器的显示样式（目前仅支持调整严重性级别）。 |
| excludeByMessage | \[\] | 按消息内容排除诊断信息。如果诊断消息中包含指定的排除字符串，则该消息将被忽略（不区分大小写）。可以使用正则表达式进行匹配（请使用对象而非字符串形式）。 |
| excludeBySource | \[\] | 请指定要排除的 `source` 或 `source(code)` 组合。示例：   \- `eslint` 禁用所有 ESLint 警告/错误提示   \- `eslint(padded-blocks)` 禁用 ESLint 的 `padded-blocks` 规则   \- `Pylance` 禁用所有 Pylance 代码检查工具所报的错误/问题   \- `Pylance(reportUndefinedVariable)` 禁用 Pylance 的 `reportUndefinedVariable` 规则 |
| excludePatterns | \[\] | 使用通配符模式来排除某些文件。例如： `["**/*.{ts,js}"]` |
| excludeWorkspaces | \[\] | 按路径排除特定工作空间。 |
| 禁用行注释 | {...} | 用于 `errorLens.disableLine` 命令，该命令可添加注释，从而暂时禁用某行的代码检查规则。   若想让评论显示在同一行上，请在消息中添加 `SAME_LINE` ： `"eslint": "// eslint-disable-line $code SAME_LINE"` |
| lintFilePaths | {...} | 指定在何处根据诊断来源来查找 linter 规则定义（对于本地的 linter 文件，可使用通配符）。 `node_modules` 文件夹被排除在外。 |
| searchForProblemQuery | " [https://duckduckgo.com/?q=$message](https://duckduckgo.com/?q=$message) " | 在使用 `errorLens.searchForProblem` 命令搜索问题时，选择在默认浏览器中打开查询结果。 |
| selectProblemType | “closestProblem” | 在执行 `errorLens.selectProblem` 命令时，应该选择哪个问题来处理：距离最近的那个问题，还是当前正在处理的问题？ |
| 光/光线 |  | 当灯光采用浅色主题时，请指定装饰物的颜色。 |
| 延迟/推迟 | **0** | 在显示问题提示之前需要等待的延迟时间（以毫秒为单位）。（设置为 0 则取消该功能。）该扩展程序要求最小延迟时间为 500 毫秒。 `#errorLens.delayMode#` 用于指定如何处理这种延迟。 |
| delayMode | “新的” | 选择要使用的延迟效果版本。 |
| onSave | **虚假的/不真实的** | 启用该功能后，只有在手动保存文档时，才会更新装饰元素。 |
| onSaveTimeout | **500** | 在文档保存后，用于显示各种装饰效果的时长（以毫秒为单位）。该过程为手动操作，而非自动保存。 |
| onSaveUpdateOnActiveEditorChange | **真实/正确** | 当 `#errorLens.onSave#` 处于启用状态时，即使当前活跃/可见的编辑器发生了变化，扩展模块仍会继续绘制各种装饰元素。 |
| enableOnDiffView | **虚假的/不真实的** | 在编辑器中查看差异对比时，启用装饰效果（例如在 Git diff 模式下）。演示版 |
| 跟随光标 | “allLines” | 仅突出显示部分问题。演示版 |
| 跟随光标更多 | **0** | 增强 `#errorLens.followCursor#` 的功能。   当 `#errorLens.followCursor#` 被设置为 `activeLine` 时，页面的上下边缘会各增加相应的行数。   当 `#errorLens.followCursor#` 为 `closestProblem` 演示模式时，会显示最接近的问题的数量。 |
| gutterIconsEnabled | **虚假的/不真实的** | 启用该功能后，会显示边距图标（取代了调试断点图标）。演示版 |
| gutterIconsFollowCursorOverride | **真实/正确** | 当该功能被启用，且 `#errorLens.followCursor#` 的设置不是 `allLines` 时，所有问题都会显示相关的图标。不过，行装饰元素（背景、提示信息等）仅会显示在当前被选中的行上。演示版 |
| gutterIconSize | “100%” | 更改侧边栏图标的大小。示例： `auto` 、 `contain` 、 `cover` 、 `50%` 、 `150%` （CSS 单位）。演示版 |
| gutterIconSet | “默认” | 更改侧边栏图标样式。演示版 |
| gutterEmoji | {"error":"💀", "warning":"😞", "info":"🆗", "hint":"🍏"} | 当 `#errorLens.gutterIconSet#` 为 `emoji` 时，为侧边栏图标选择合适的表情符号。演示版 |
| errorGutterIconPath | "" | 通往错误提示图标所在位置的绝对路径。演示版 |
| warningGutterIconPath | "" | 警告图标所在的绝对路径。演示用。 |
| infoGutterIconPath | "" | 信息栏图标的绝对路径。演示版 |
| hintGutterIconPath | "" | 提示栏图标的绝对路径。演示用。 |
| errorGutterIconColor | "#e45454" | 简单边距图标（包括各种形状和字母）的错误显示颜色。演示版 |
| warningGutterIconColor | #ff942f | 简单排水口图标的警告颜色（包括各种形状和字母）。演示版 |
| infoGutterIconColor | "#00b7e4" | 关于简单排水槽图标（包括各种形状和文字）的颜色信息。演示版。 |
| hintGutterIconColor | "#2faf64" | 简单边距图标的提示颜色（包括形状和文字）。演示版 |
| 移除换行符 | **真实/正确** | 启用该功能后，内嵌的诊断信息中的换行符将被替换为空格。 |
| replaceLinebreaksSymbol | “⏎” | 用于替代换行符的符号。需先启用 `#errorLens.removeLinebreaks#` 功能。 |
| scrollbarHackEnabled | **虚假的/不真实的** | 启用该功能后，可以避免在编辑器中显示水平滚动条（该现象是由内联装饰元素导致的）。同时，也会阻止鼠标悬停在内联消息上。演示版。 |
| 忽略“无标题”内容 | **虚假的/不真实的** | 控制是否对未命名/未保存的文件也进行操作。 |
| 忽略脏数据 | **虚假的/不真实的** | 控制是否在已修改但未保存的文件上运行程序。 |
| codeLensEnabled | **虚假的/不真实的** | 控制是否在代码上方以“代码透镜”的形式显示“错误透镜”。演示版 |
| codeLensLength | {"min":0, "max":200} | 必须规定代码镜像消息的最小和最大长度限制。 |
| codeLensTemplate | “$severity $message” | 该模板用于 `#errorLens.codeLensEnabled#` 中出现的所有消息。各项目之间的空格非常重要。   变量列表：   \- `$message` - 诊断信息文本   \- `$count` - 该线路上的诊断项数量   \- `$severity` - 严重性前缀取自 `#errorLens.severityText#`   \- `$source` - 用于诊断的工具或来源，例如“eslint”   \- `$code` - 诊断代码 |
| codeLensOnClick | “showQuickFix” | 控制点击 `#errorLens.codeLensEnabled#` 时会发生什么操作。 |
| 实验性的/通过实验得出的 | {...} | 实验性/临时设置。 |

## 颜色（30 种）

可以在 `settings.json` （ **`workbench.colorCustomizations`** 部分）中指定。

| 颜色 | 黑暗的 | 光 | HC | 描述 |
| --- | --- | --- | --- | --- |
| errorLens.errorBackground | `#e454541b` | `#e4545420` | `#e454541b` | 包含错误的整行的背景颜色。 |
| errorLens.errorMessageBackground | `#e4545419` | `#e4545419` | `#e4545419` | 错误消息的背景颜色。 |
| errorLens.errorRangeBackground | `#e4545419` | `#e4545419` | `#e4545419` | 错误范围的背景颜色（当 errorLens.problemRangeDecorationEnabled 设置为启用状态时）。 |
| errorLens.errorBackgroundLight | `#e4545420` | `#e4545420` | `#e4545420` | 包含错误的整行的背景颜色（仅适用于浅色主题）。 |
| errorLens.errorForeground | `#ff6464` | `#e45454` | `#ff6464` | 用于突出显示包含错误的行的文本颜色。 |
| errorLens.errorForegroundLight | `#e45454` | `#e45454` | `#e45454` | 用于突出显示包含错误的行的文字颜色（仅适用于浅色主题）。 |
| errorLens.warningBackground | `#ff942f1b` | `#ff942f20` | `#ff942f1b` | 用于突出显示包含警告的行的背景颜色。 |
| errorLens.warningMessageBackground | `#ff942f19` | `#ff942f19` | `#ff942f19` | 警告消息的背景颜色。 |
| errorLens.warningRangeBackground | `#ff942f19` | `#ff942f19` | `#ff942f19` | 警告区域的背景颜色（当 errorLens.problemRangeDecorationEnabled 设置为启用状态时）。 |
| errorLens.warningBackgroundLight | `#ff942f20` | `#ff942f20` | `#ff942f20` | 用于突出显示包含警告的线条的背景颜色（仅适用于浅色主题）。 |
| errorLens.warningForeground | `#fa973a` | `#ff942f` | `#fa973a` | 用于突出显示包含警告内容的行的文字颜色。 |
| errorLens.warningForegroundLight | `#ff942f` | `#ff942f` | `#ff942f` | 用于突出显示包含警告的行的文字颜色（仅适用于浅色主题）。 |
| errorLens.info 背景信息 | `#00b7e420` | `#00b7e420` | `#00b7e420` | 用于突出显示包含信息的文字行的背景颜色。 |
| errorLens.infoMessageBackground | `#00b7e419` | `#00b7e419` | `#00b7e419` | 信息消息的背景颜色。 |
| errorLens.infoRangeBackground | `#00b7e419` | `#00b7e419` | `#00b7e419` | 信息区域的背景颜色（当 errorLens.problemRangeDecorationEnabled 选项处于启用状态时）。 |
| errorLens.info 背景光线 | `#00b7e420` | `#00b7e420` | `#00b7e420` | 用于突出显示包含信息的线条的背景颜色（仅适用于浅色主题）。 |
| errorLens.info 前景 | `#00b7e4` | `#00b7e4` | `#00b7e4` | 用于突出显示包含信息的文字行的颜色。 |
| errorLens.info 前景光 | `#00b7e4` | `#00b7e4` | `#00b7e4` | 用于突出显示包含信息的文字的颜色（仅适用于浅色主题）。 |
| errorLens.hintBackground | `#17a2a220` | `#17a2a220` | `#17a2a220` | 用于突出显示包含提示的文字行的背景颜色。 |
| errorLens.hintMessageBackground | `#17a2a219` | `#17a2a219` | `#17a2a219` | 提示信息的背景颜色。 |
| errorLens.hintRangeBackground | `#17a2a219` | `#17a2a219` | `#17a2a219` | 提示范围的背景颜色（当 errorLens.problemRangeDecorationEnabled 选项处于启用状态时）。 |
| errorLens.hintBackgroundLight | `#17a2a220` | `#17a2a220` | `#17a2a220` | 用于突出显示包含提示的线条的背景颜色（仅适用于浅色主题）。 |
| errorLens.hintForeground | `#2faf64` | `#2faf64` | `#2faf64` | 用于突出显示包含提示的文字的字体颜色。 |
| errorLens.hintForegroundLight | `#2faf64` | `#2faf64` | `#2faf64` | 用于突出显示包含提示的文字的颜色（仅适用于浅色主题）。 |
| errorLens 状态栏图标错误前景色 | `#ff6464` | `#e45454` | `#ff6464` | 状态栏图标项的错误颜色。当 `errorLens.statusBarIconsUseBackground` 设置被禁用时，会使用前景色来显示该图标项。 |
| errorLens 状态栏图标警告前景色 | `#fa973a` | `#ff942f` | `#fa973a` | 状态栏图标项的错误颜色。当 `errorLens.statusBarIconsUseBackground` 设置被禁用时，会使用前景色来显示该图标项。 |
| errorLens 状态栏错误前景色 | `#ff6464` | `#e45454` | `#ff6464` | 状态栏项目的错误颜色。 |
| errorLens 状态栏警告前景色 | `#fa973a` | `#ff942f` | `#fa973a` | 状态栏项目的警告颜色。 |
| errorLens 状态栏信息前景色 | `#00b7e4` | `#00b7e4` | `#00b7e4` | 状态栏项目信息的颜色。 |
| errorLens 状态栏提示前景色 | `#2faf64` | `#2faf64` | `#2faf64` | 状态栏项目提示颜色。 |

> 行高亮显示方式取决于 **`"errorLens.messageBackgroundMode"`** 的设置。

> `#fff0` - 完全透明的颜色。

## 上游问题/上游环节的难题

请给以下的 VS Code 问题点赞：

- [用于编辑器插件的 API 接口](https://github.com/microsoft/vscode/issues/85682)
- [以编程方式获取主题颜色](https://github.com/microsoft/vscode/issues/32813)
- [内嵌的文本装饰会打断单词的自动换行。](https://github.com/microsoft/vscode/issues/32856)
- [支持在行号上悬停以显示装饰元素，即所谓的“边距装饰”。](https://github.com/microsoft/vscode/issues/28080)

## 📚 更多文档/示例

[https://github.com/usernamehw/vscode-error-lens/tree/master/docs/docs.md](https://github.com/usernamehw/vscode-error-lens/tree/master/docs/docs.md)