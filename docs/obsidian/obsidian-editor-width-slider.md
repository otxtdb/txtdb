---
title: "MugishoMp/obsidian-editor-width-slider: With this plugin you can set the line width of the editor in obsidian."
source: "https://github.com/mugishomp/obsidian-editor-width-slider"
author:
published:
created: 2026-08-27
description: "With this plugin you can set the line width of the editor in obsidian. - MugishoMp/obsidian-editor-width-slider"
tags:
  - "clippings"
taxonomy: { doc_category: [obsidian] }
---
## MugishoMp/obsidian-editor-width-slider：通过使用这个插件，你可以自定义 Obsidian 编辑器的行宽度。

## 黑曜石线条宽度滑块插件

> 这是一个适用于 Obsidian 编辑器的插件，它允许你通过状态栏中的简单滑块来调整编辑器的行宽度。

## 特点

- 通过状态栏中的滑块来调整编辑器的行宽度。
- 可以调整线条的粗细，以定制你的编辑体验。
- 简单直观的界面设计，方便用户使用。

### 特性：使用 YAML 格式为单个文件进行自定义配置

通过使用黑曜石行距滑块插件，您可以通过在笔记的 YAML 头部指定“editor-width”字段来自定义单个文件的编辑器宽度。这一功能使得您能够为不同的文件设置不同的行距，从而在笔记记录和编辑过程中获得更大的灵活性。

#### 设置编辑器宽度

要为特定的文件设置自定义的编辑器宽度，请按照以下步骤操作：

1. 请打开您想要调整编辑器宽度的笔记。
2. 在笔记顶部的 YAML 前言部分，添加一个名为“editor-width”的字段。该字段的值应该是一个介于 0 到 100 之间的数字，表示期望的编辑器宽度占视口宽度的百分比。例如：0。
	```yaml
	---
	title: My Customized Note
	editor-width: 75
	---
	```

## 演示版

![Demo GIF](https://github.com/MugishoMp/obsidian-editor-width-slider/raw/master/images/demo-gif-full-size.gif)

> 以下是一个简短的演示，展示了 Line Width Slider 插件的基本功能。

## 安装

1. 从插件发布页面下载该插件的最新版本。
2. 从下载的 ZIP 文件中提取插件文件夹。
3. 将插件文件夹复制到你的 Obsidian 存储库的 `.obsidian/plugins` 目录下。
4. 启动 Obsidian 软件，然后打开设置界面。
5. 请前往“社区插件”选项卡，并启用“线条宽度滑块”插件。
6. 可以使用状态栏中的线宽滑块来调整编辑器的线宽。

## 使用方法/用途

1. 一旦该插件被启用，你会在状态栏中看到一个滑块图标。
2. 将滑块向左或向右拖动，即可增加或减少编辑器的行宽度。
3. 这些更改将实时应用于编辑器。

## 反馈与支持

如果您遇到任何问题或希望提出改进建议，请请在 GitHub 仓库中创建一个新的问题。

## 请支持我吧。

如果您认为我的工作有价值，或者想要支持这位靠咖啡因维持活力的编程学生，您可以通过 PayPal 进行捐赠。您的贡献非常宝贵，有助于让我的工作持续下去！☕️🖥️

![Donate](https://camo.githubusercontent.com/e1ff554a09e8e92bef25abc553ff05b88f45afd695877cf12f3a46558ef65b2e/68747470733a2f2f7777772e70617970616c6f626a656374732e636f6d2f656e5f55532f692f62746e2f62746e5f646f6e61746543435f4c472e676966)

## 许可证

## 该插件采用 MIT 许可证进行授权。更多详细信息请参考许可证文件。

请注意，这个插件是免费提供的，没有任何形式的保证。请自行承担使用此插件的风险。