---
title: "k4a-l/obsidian-heading-shifter: Easily Shift and Change markdown headings."
source: "https://github.com/k4a-l/obsidian-heading-shifter"
author:
published:
created: 2026-08-27
description: "Easily Shift and Change markdown headings. Contribute to k4a-l/obsidian-heading-shifter development by creating an account on GitHub."
tags:
  - "clippings"
taxonomy: { doc_category: [obsidian] }
---
## k4a-l/obsidian-heading-shifter：可以轻松切换和改变 Markdown 标题的格式。

[!["Buy Me A Coffee"](https://camo.githubusercontent.com/9f44ce2dc3b3eecdd02598900866ffc518801df1932849703dae1e5ce5031070/68747470733a2f2f7777772e6275796d6561636f666665652e636f6d2f6173736574732f696d672f637573746f6d5f696d616765732f6f72616e67655f696d672e706e67)](https://www.buymeacoffee.com/kasahala)

轻松切换和更改 Markdown 标题的格式。

## 为什么使用这个插件？

黑曜石将多个 Markdown 格式的文件链接起来，从而形成知识体系。定期重新整理这些链接对于构建良好的知识体系非常重要。

在这个过程中，通常会出现以下几种情况。

1. 将文件 1 中的某一部分分离出来，作为独立的文件 2，并与其链接在一起。
	- 文件 1 中的 Heading3 被改为文件 2 中的 Heading1。
2. 将文件 3 的内容合并到文件 4 的某一部分中。
	- 文件 3 中的 Heading2 被改为文件 4 中的 Heading4

通过使用这个插件，你可以批量更改标题的大小（即 `#` 的数量），而无需手动逐一修改。

## 如何安装

### 从黑曜石内部出发

您可以通过在 Obsidian 中执行以下操作来激活此插件：

- 打开设置 > 社区插件选项
- 确保 `Restricted mode` 处于关闭状态。
- 点击“浏览”按钮 `community plugins`
- 搜索 `Heading Shifter`
- 点击 `Install` -> 会跳转到 `Enable`

### 手动安装

从最新发布的版本中下载相关目录（包括 `main.js, manifest.json, styles.css` ），并将它们放入 `<vault>/.obsidian/plugins/` 文件夹中。

## 特点

### 应用标题标签

![Applying Heading Demo](https://raw.githubusercontent.com/k4a-dev/obsidian-heading-shifter/main/doc/attachment/applyingHeading.gif)

Applying Heading Demo

#### 命令

| 命令 | 描述 | 快捷键 |
| --- | --- | --- |
| 应用标题样式为 0 | 将当前行改为无标题。 | \- |
| 应用标题 1~6 | 将当前行改为标题 1~6。 | \- |

> 分配一个快捷键比如 `Ctrl + 0 ~ 6 是很有用的。`

### 切换标题显示模式

Headings Shift Demo

#### 设置

| 设置 | 描述 | 默认值 |
| --- | --- | --- |
| 标题的下限 | 由于方向调整，较小的航向尺寸将会被减小。 | 0~6(1) |
| 启用覆盖选项卡的行为功能 | 如果为真，按 Tab 键则执行“提高标题级别”，而按 Shift-Tab 键则执行“降低标题级别”\[^2\] | 布尔值（false） |

\[^2\]: 可能会与其他插件的行为产生冲突

#### 命令

| 命令 | 描述 | 快捷键 |
| --- | --- | --- |
| 增加标题的字体大小 | 增加选中行文本的标题显示效果。 |  |
| 增加标题的字体大小（强制操作） | 增加选定行文本的对齐方式（即使没有设置对齐方式也行） |  |
| 减少标题数量 | 减少选定行文本的标题显示 |  |

> 分配一个快捷键比如 `Ctrl + Shift + Left/Right 是很有用的。`

- 如果所选行中的内容少于 `Lower limit of heading` ，那么 `Increase headings` 和 `Increase headings(forced)` 的选择将无效。
- 如果所选行中包含超过 6 级标题的内容，那么 `Decrease headings` 功能将无效。

### 插入标题

#### 命令

| 命令 | 描述 | 快捷键 |
| --- | --- | --- |
| 在当前级别插入标题 | 将当前行的标题更改为与当前级别相匹配的形式。 |  |
| 插入一个层次更深的标题 | 将当前行的标题改为当前等级加 1 的标题。 |  |
| 在上一层结构中插入标题 | 将当前行的标题更改为当前级别 - 1 |  |

## 常见设置

| 设置 | 描述 | 默认值 |
| --- | --- | --- |
| 移除样式（默认设置） | 如果这种风格已经处于线的末端了，那就把它移除吧。 | 布尔值（全部为真） |
| 用于删除（其他任意一组正则表达式）的模式 | 如果这种风格已经处于线的末端了，那就把它移除吧。 | 字符串 |
| 儿童列表的行为设置 | 当目标行包含子列表时的行为 | `"outdent to zero"(default)` / `"sync with headings"` / `"noting"` |

#### 移除样式

这是在进行“单行”标题操作时，选择是否保留 `specific style` 的开关。

##### 开始

`-` 或 `1.` 、 `2.` 、 `n.` 或 `user defined string(RegExp)`

|  | 之前 | 之后（真实情况） | 之后（False） |
| --- | --- | --- | --- |
| `- ` (ul) | `- line` | `## line` | `## - line` |
| `1. ` (或) | `1. line` | `## line` | `## 1. line` |
| `🤔` （用户自定义） | `🤔line` | `## line` | `## 🤔line` |

##### 周围

`**` 、 `_` 等……或者 `user defined string(RegExp)`

|  | 之前 | 之后（真实情况） | 之后（False） |
| --- | --- | --- | --- |
| `**` （加粗） | `**line**` | `## line` | `## **line**` |
| `_` (斜体) | `_line_` | `## line` | `## _line_` |
| `🤔` （用户自定义） | `🤔line🤔` | `## line` | `## 🤔line🤔` |

### 列表行为

```markdown
- heading target
    - listA
        - listB
```

如果你调用“应用标题 2”，

#### 没有什么

```markdown
## heading target
    - listA
        - listB
```

后续的列表将保持深度格式，并且不会采用正确的 markdown 结构。

#### 缩进至零

```markdown
## heading target

- listA
    - listB
```

#### 与标题同步

```
\t\t- ## heading target
\t\t\t- listA
\t\t\t\t- listB
```

## 使用场景

像使用大纲工具一样来操作标题。如下所示：

```
## The Festival Myster -> hit "Apply 1"

This is a great document.

### Chapter One -> hit "Insert deeper"

#### Prologue -> hit "Insert deeper"

The sun was setting over the horizon...

#### The Summer Festival -> hit "Insert current"

As the townspeople gathered in the town square...

### Chapter Two -> hit "Insert higher"

#### The Mystery of the Missing Prize -> hit "Insert deeper"

As the summer festival came to a close...
```

如果你想要让标题的字体高度超过 2 个单位，可以使用“shift”或“应用”功能。

## 负载映射

目前没有具体的信息。

## 贡献于他人

如果您遇到任何问题或需要添加某些功能，请随时告诉我们。