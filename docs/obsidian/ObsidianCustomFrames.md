---
title: "Ellpeck/ObsidianCustomFrames: An Obsidian plugin that turns web apps into panes using iframes with custom styling. Also comes with presets for Google Keep, Todoist and more."
source: "https://github.com/Ellpeck/ObsidianCustomFrames"
author:
published:
created: 2026-08-27
description: "An Obsidian plugin that turns web apps into panes using iframes with custom styling. Also comes with presets for Google Keep, Todoist and more. - Ellpeck/ObsidianCustomFrames"
tags:
  - "clippings"
taxonomy: { doc_category: [obsidian] }
---
## Ellpeck/ObsidianCustomFrames：这是一个由 Obsidian 开发的插件，能够使用 iframe 将网页应用转换为面板，并拥有自定义的样式。该插件还提供了针对 Google Keep、Todoist 等应用预设设置。

## 黑曜石定制框架

这是一个由黑曜石公司开发的插件，能够利用 iframe 技术将网页应用转换为面板形式，并拥有自定义的样式设置。该插件还提供了针对 Google Keep、Todoist 等应用的内置预设配置。

[![A screenshot of the plugin in action, where you can see Google Keep attached as a narrow side pane on the right](https://raw.githubusercontent.com/Ellpeck/ObsidianCustomFrames/master/screenshot.png)](https://raw.githubusercontent.com/Ellpeck/ObsidianCustomFrames/master/screenshot.png)

[![A screenshot of the plugin in action, where you can see Google Calendar opened in the center, and the mouse hovering over the corresponding ribbon button](https://raw.githubusercontent.com/Ellpeck/ObsidianCustomFrames/master/screenshot-big.png)](https://raw.githubusercontent.com/Ellpeck/ObsidianCustomFrames/master/screenshot-big.png)

[![A screenshot of the plugin's settings](https://raw.githubusercontent.com/Ellpeck/ObsidianCustomFrames/master/settings.png)](https://raw.githubusercontent.com/Ellpeck/ObsidianCustomFrames/master/settings.png)

## 🤔 使用方式

要使用此插件，只需进入其设置界面，然后添加一个新框架。这个框架可以是插件自带的预设框架，也可以是你自己编辑的自定义框架。

### 🪟 面板模式

要将一个自定义框架作为面板打开，可以使用“自定义框架：打开”命令。

此外，还有许多设置可以进一步定制框架的外观。例如，可以为网站添加自定义的 CSS 样式，添加纹理图标，或者将框架显示在编辑器的中央位置等等。

### 🗒️ Markdown 模式

您也可以在 Markdown 文档中显示自定义的框架。自定义框架提供了一种特殊的代码块语法，可以将代码块在实时预览和阅读模式下转换为自定义的框架。您的代码块应该看起来像这样：

```
\`\`\`custom-frames
frame: YOUR FRAME'S NAME
\`\`\`
```

此外，您还可以为嵌入样式传递自定义设置。这样您可以改变嵌入的高度，同时还可以为框架的常规 URL 附加一个额外的后缀。这一点在需要将特定笔记显示在 Google Keep 中时非常有用。

以下是使用 Google Keep 预设功能的示例：

```nix
\`\`\`custom-frames
frame: Google Keep
style: height: 1000px;
urlSuffix: #reminders
\`\`\`
```

### 📱 在 Obsidian 移动平台上

不幸的是，Obsidian Mobile 并不支持 Electron 框架。而 Electron 能够轻松实现在网页中显示框架，并且对 cookies、跨源资源共享等方面几乎没有限制。这意味着许多网站在 Obsidian Mobile 上无法正常运行，尤其是那些需要登录的网站。不过，当你创建框架时，可以选择“禁用移动设备版”选项，这样就可以在 Obsidian Mobile 中只显示适用于桌面的框架了。

需要帮助使用该插件吗？欢迎加入 Discord 服务器寻求帮助！

[![Join the Discord server](https://camo.githubusercontent.com/a1cee8e88b3d6f2778670817b35955595ae6e99dc7b77af985a63979bc867ba0/68747470733a2f2f656c6c7065636b2e64652f7265732f646973636f72642d776964652e706e67)](https://link.ellpeck.de/discordweb)

## 📦 预设设置

默认情况下，Custom Frames 提供了一些预设置选项，这些选项可以帮助你快速为常见的网站创建新的面板。

- [黑曜石论坛](https://forum.obsidian.md/)
- 谷歌 Keep，专为侧边栏宽度有限的情况而优化设计
- 通过移除一些按钮来优化谷歌日历的功能。可以使用左上角的按钮关闭侧边栏。
- Todoist 这款应用经过优化，专为窄型侧面面板设计，通过移除一些按钮并缩小边距来适应这一布局需求。
- “Notion”功能（如果将其作为侧边窗格来使用，建议关闭其侧边栏）
- [推特](https://twitter.com/)
- [《阅读周刊每日回顾》](https://readwise.io/dailyreview)

如果你创建了一个你认为其他人会喜欢的框架，那么请毫不犹豫地提交一个新的预设，以便进行合并请求。

## 🛣️ 路线图

- 允许在除 Obsidian 之外的其他环境中创建链接，这些链接可以在自定义框架中打开。
- 为 Markdown 模式添加更多选项，比如允许出现前进和后退按钮。
- 可能允许将选定的文本提取到笔记中，就像“笔记编辑器”插件所做的事情一样。此外，还可能允许使用包含从网站中提取的链接的笔记模板。
- ~~允许为每个面板设置自定义的图标。~~
- ~~允许在 Markdown 代码块中显示自定义框架。~~
- ~~添加一种功能，可以在主视图中打开框架时，添加一个带状按钮来展开该框架。~~
- ~~可能会允许在框架中执行自定义的 JavaScript 代码（不过仍需考虑相关的安全问题）。~~
- 添加一项全局设置，使得弹出窗口会在新的 Obsidian 窗口中打开，而不是在默认的浏览器中打开（请参阅网络查看器核心插件）。

## ⚠️ 已知问题

在自定义框架中存在一些已知的问题。如果您遇到任何这些问题，请不要将其报告到问题跟踪系统中。

- 在默认浏览器中，弹出窗口和新标签页会打开在自定义框架之外，这可能会给使用外部登录功能的网站带来登录问题。为了解决这个问题，可以启用 Web 查看器核心插件，该插件会将会话信息共享给自定义框架，从而在 Obsidian 中打开弹出窗口。
- 一些链接在自定义框架内无法打开，这种情况在 Obsidian 1.3.7 版本之前尤为明显。您可以参考相关文档获取更多信息。

## 🙏 感谢大家的支持

感谢 lishid 在让 iframe 在 Obsidian 中正常运行方面提供的帮助。同时也感谢他们激励我将 Obsidian Keep 打造成一个更通用的插件，从而诞生了 Custom Frames。

如果你喜欢这个插件，并且希望支持其发展，可以通过我的网站点击这个图片来捐款！

[![Support me (if you want), via Patreon, Ko-fi or GitHub Sponsors](https://camo.githubusercontent.com/c74a25f62cb20e8dd18a0acb26615686a41e3dca076e0b8cdd4487a752005674/68747470733a2f2f656c6c7065636b2e64652f7265732f67656e6572616c737570706f72742d776964652e706e67)](https://ellpeck.de/support)