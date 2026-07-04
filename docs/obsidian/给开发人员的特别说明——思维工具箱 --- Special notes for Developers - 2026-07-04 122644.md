---
title: "给开发人员的特别说明——思维工具箱 --- Special notes for Developers"
source: "https://tfthacker.com/brat-developers"
author:
published:
created: 2026-07-04
description: "Protocol Handler - Toolbox for Thought"
tags:
  - "clippings"
taxonomy: { doc_category: [obsidian] }
---
## 插件开发人员的 BRAT 指南

本指南介绍了如何配置 Obsidian 插件，以便与 BRAT 进行测试版测试。

> [!warning] 警告
> 请注意：这些说明仅适用于插件。主题的处理方式则有所不同。

## Obsidian 是如何加载插件的

以下是该插件工作原理的简要说明。

Obsidian 会检查该插件仓库的根目录中是否存在名为 `manifest.json` 的文件。 `manifest.json` 文件中包含了该插件的版本号。Obsidian 会利用这个版本号，在该 GitHub 仓库中查找版本号相同的“发布版本”。一旦找到匹配的版本，Obsidian 就会下载 `main.js` 、 `manifest.json` 和 `styles.css` 文件，并将它们安装到用户的 Vault 中。

对于插件的“测试版”而言，BRAT 采用了略有不同的处理方式，但在安装插件时，所使用的流程则完全相同。

## 如何让你的插件适用于 BRAT 平台

如果你想测试插件的预发布版本：

1. 在 GitHub 上创建一个新版本/发布内容
2. 可以选择将其标记为“预发布版本”。
3. 在发布的内容中，请包含 `manifest.json` 、 `main.js` 和 `styles.css` （如有必要）。

这样一来，你实际上仍然可以使用那些“实时”和“测试版”频道，只不过所有操作都是通过 GitHub 的发布系统来完成的。

> [!important] 重要
> 请先不要将 `manifest.json` 提交到默认分支中。一旦您所在仓库的默认分支中的 `manifest.json` 发生变化，Obsidian 会自动检测到并更新该内容。
> 
> 如果你发布了用于测试的版本，那么暂时不要将版本号的更改提交到 `manifest.json` 的默认分支中。

## GitHub 发布内容与 manifest.json 文件

从 v1.1.0 版本开始，BRAT 主要与 GitHub 上的软件发布版本兼容。在安装或更新插件时，BRAT 会：

1. 对于某个特定版本（已冻结的版本）：请下载该确切的版本，无论其是否被标记为“预发布版本”。
2. 如需最新版本：请下载当前可用的最新版本或预发布版本，优先选择语义版本号较高的版本。

`manifest.json` 是直接从发布包中获取的，因此 BRAT 的版本号与仓库根目录中的版本编号无关。

## 遗留文件：manifest-beta.json

在 1.1.0 版本之前，BRAT 会在仓库的根目录下使用一个额外的 `manifest-beta.json` 文件来覆盖 `manifest.json` 中的版本号。虽然为了向后兼容性，该文件仍然被支持，但在这种基于新版本的更新方式下，该文件已不再必要。

## BRAT 是如何运作的

BRAT 会检查你的代码仓库在 GitHub 上的发布记录。在安装和更新过程中，它会：

1. 获取可用版本的列表
2. 请选择合适的版本：对于需要固定版本的安装情况，请选择特定版本；否则，请选择符合 SemVer 规范的最新版本。
3. 直接从发布资源中下载 `manifest.json` 、 `main.js` 和 `styles.css` 。

这种方法使得 BRAT 更加可靠，因为它以 GitHub 上的发布内容作为权威信息来源。

> [!important] 重要
> Obsidian 不支持完整的 `semver` 规范。如果你使用 `-preview` 及其他分支来构建插件的测试版，Obsidian 不会自动识别这些测试版。除非新版本的版本号比测试版高出至少一个次要版本号，否则 Obsidian 仍不会自动识别该新版本。在这种情况下，最好使用 BRAT 工具来将插件升级到最新版本。
> 
> 如果用户安装了像 `1.0.1-preview.1` 这样的预发布版本，那么当 `1.0.1` 正式发布后，Obsidian 将无法自动识别它。用户必须通过 BRAT 手动进行更新。
> 
> 不过，一旦 `1.0.2` 或更高版本发布，Obsidian 的更新机制将会再次启动，让用户可以选择升级到相应的预发布版本。
> 
> 下表展示了按照 Semver 标准进行的版本比较结果，按版本号从低到高排序。同时，该表还标明了哪些版本会被 Obsidian 的更新机制所识别，哪些则不会。
> 
> | 语义版本号 |  |  |
> | --- | --- | --- |
> | `1.0.0` | 1 |  |
> | `1.0.1-alpha.25` | 2 |  |
> | `1.0.1-beta.5` | 3 |  |
> | *`1.0.1-preview.1`* | 4 | *由用户使用 BRAT 工具进行安装* |
> | `1.0.1` | 5 | 未被 Obsidian 的更新机制所识别/未包含在 Obsidian 的更新内容中 |
> | **`1.0.2`** | 6 | **已通过 Obsidian 的更新机制进行更新。** |