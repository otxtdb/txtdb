---
title: "协议处理程序——思维工具箱 --- Protocol Handler"
source: "https://tfthacker.com/brat-protocol"
author:
published:
created: 2026-07-04
description: "Logging Support - Toolbox for Thought"
tags:
  - "clippings"
taxonomy: { doc_category: [obsidian] }
---
利用 Obsidian 的协议处理机制，BRAT 可以在 Obsidian 的内部或外部被调用。通过这个特殊格式的 URL，就可以打开相应的插件或主题仓库，以便在 BRAT 中进行安装。

要使用此功能，请按照以下格式创建一个 URL：

`obsidian://brat?<command>=<repository>`

该协议处理程序包含以下组成部分：

- 以 `obsidian:// 开头`
- 接着是 `brat?` ，
- 接着是 `plugin` command `theme` ，它要么是 `  ，要么是  ` 。
	- `plugin` 表示该 GitHub 仓库属于某种插件。
		- `theme` 表示以下的 GitHub 仓库属于主题类仓库。
- 接着是 `repository` ，它指的是该 GitHub 仓库的 URL 地址。

请查看以下示例，了解其运作方式。

## 插件示例

以下是使用该协议来安装 Meta Bind 插件的示例：

```
obsidian://brat?plugin=https://github.com/mProjectsCode/obsidian-meta-bind-plugin
```

不妨试一试吧：点击此处即可安装 Meta Bind 插件。

您也可以使用该 URL 的简写形式，同时去掉 `https://githbut.com/` ，如下所示：

```bash
obsidian://brat?plugin=mProjectsCode/obsidian-meta-bind-plugin
```

不妨试一试吧：点击此处即可安装 Meta Bind 插件。

## 主题示例

以下是使用该协议来安装 Gruvbox 主题的示例：

```
obsidian://brat?theme=https://github.com/insanum/obsidian_gruvbox
```

不妨试一试吧：点击此处即可安装 Gruvbox 主题。

## 启用与禁用插件

有人询问，是否也可以通过 BRAT 作为协议处理程序来实现这一功能。其实，高级 URI 插件已经具备这一功能，相关用法在文档中有所说明，涉及 `enable-plugin` 和 `disable-plugin` 命令。

## 禁用插件

要禁用某个插件，请使用如下命令：

`[Disable](obsidian://advanced-uri?disable-plugin=obsidian42-brat)`

## 启用插件

要启用某个插件，请按照以下步骤操作：

`[Enable](obsidian://advanced-uri?enable-plugin=obsidian42-brat)`

不过，对于某些插件来说，这种方法并不适用。因此，另一种方法是启用“允许通过 eval 执行任意代码”选项，然后再使用相应的方法。

`[Enable](obsidian://advanced-uri?eval=app.plugins.enablePluginAndSave("obsidian42-brat"))`