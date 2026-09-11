---
title: "frame-indent-rainbow - Visual Studio Marketplace"
source: "https://marketplace.visualstudio.com/items?itemName=firejump.frame-indent-rainbow"
author:
published:
created: 2026-08-26
description: "Extension for Visual Studio Code - Makes indentation easier to read by coloring frames around each indent level (block). Helpful for people with dyslexia."
tags:
  - "clippings"
taxonomy: { doc_category: [vscode] }
---
[跳转至内容部分](#start-of-content)

## 框架缩进-彩虹效果

## 纵跃

|

15,582 次安装量

通过为每个缩进层级加上颜色标记，使文本更易于阅读。这对有阅读障碍的人非常有帮助。

## 框架-缩进-彩虹效果

## 一个简单的改进措施，旨在提升代码的可读性。

该扩展功能会为缩进文本周围的边框着色，每一步都会使用不同的颜色。一些有阅读障碍的人表示，这一功能有助于他们理解那些不熟悉的代码。

既可以在独立的 Visual Studio Code 中使用，也可以在 vscode-web（github.dev）上使用。请在 Visual Studio Code Marketplace 中下载即可。

这个扩展程序其实是 oderwat 的 indent-rainbow 功能的改进版。

![Example](https://github.com/firejump/vscode-frame-rainbow/blob/master/assets/example.png?raw=true)

该工具会使用当前编辑器中标签页的宽度来设置缩进格式。此外，它还会标出那些缩进宽度不是标签页宽度的整数倍、或者同时使用了制表符和空格的情况。这种可视化显示方式有助于用户发现某些情况下的缩进错误。

## 配置

虽然可以直接使用该扩展，但实际上也可以对其中的某些设置进行自定义。最简单的操作方式就是通过扩展的设置界面来进行调整。

![Settings](https://github.com/firejump/vscode-frame-rainbow/blob/master/assets/extension_settings_1.png?raw=true)

您可以将以下设置覆盖内容添加到本地的 `settings.json` 文件中：

```js
// For which languages frame-indent-rainbow should be activated (if empty it means all).
"frameIndentRainbow.includedLanguages": [] // for example ["nim", "nims", "python"]

// For which languages frame-indent-rainbow should be deactivated (if empty it means none).
"frameIndentRainbow.excludedLanguages": ["plaintext"]

// The delay in ms until the editor gets updated.
"frameIndentRainbow.updateDelay": 100 // 10 makes it super fast but will cost more CPU
```

*注意：同时定义 `includedLanguages` 和 `excludedLanguages` 并没有太大意义。请只使用其中一个即可！*

你可以通过添加或修改以下代码来自定义颜色：

```js
"frameIndentRainbow.colors": [
  "hsla(312, 70%, 50%, 0.2)",
  "hsla(250, 70%, 50%, 0.2)",
  "hsla(191, 70%, 50%, 0.2)",
  "hsla( 20, 70%, 50%, 0.2)",
]
```

您还可以使用 RGBA 格式的颜色表示方式（ `rgba(255,255,64,0.2)` ）、带阿尔法通道的十六进制颜色表示方式（ `#0080FF80` ），或者任何 CSS 所支持的色彩表示方式。我建议使用比较鲜艳的颜色，然后通过将阿尔法值设置为 0.2 左右来降低颜色的亮度。如果阿尔法值过高，那么文本的颜色就很难被区分出来了。

### 隐藏错误高亮显示功能

默认情况下，该插件会标出以下几种缩进错误：

- 制表符与空格混合使用
- 缩进宽度不是制表符大小的整数倍。

在某些情况下，违反这些规则的缩进方式并不算错误。你可以定义正则表达式，让工具忽略那些符合特定规则的行上的错误提示。默认情况下，带有 JavaDoc/JSdoc 注释以及 `//` 格式注释的行上的错误提示会被隐藏。

```js
// Example of regular expression in JSON (note double backslash to escape characters)
"frameIndentRainbow.ignoreLinePatterns" : [
  "/[ \t]* [*]/g",  // lines begining with <whitespace><space>*
  "/[ \t]+[/]{2}/g" // lines begininning with <whitespace>//
]
```

可以跳过对某些或所有语言的错误高亮显示。例如，您可以选择不显示 `markdown` 和 `haskell` 语言中的缩进错误（这其实是默认设置）。

```js
"frameIndentRainbow.ignoreErrorLanguages" : [
  "markdown",
  "haskell"
]
```

## 发展/进步

使用以下工具来构建该扩展：

```markdown
npm install
npm run vscode:prepublish
```