---
title: "Sergei-Korneev/obsidian-local-images-plus: This repo is a reincarnation of obsidian-local-images plugin which main aim was downloading images in md notes to local storage."
source: "https://github.com/sergei-korneev/obsidian-local-images-plus"
author:
published:
created: 2026-08-27
description: "This repo is a reincarnation of obsidian-local-images plugin which main aim was downloading images in md notes to local storage. - Sergei-Korneev/obsidian-local-images-plus"
tags:
  - "clippings"
taxonomy: { doc_category: [obsidian] }
---
## 黑曜石本地图像增强版

Obsidian Local Images Plus 是适用于 Obsidian 平台的插件。

---

**使用本软件意味着您同意遵守所有条款条件，并同意本许可协议。**

**该软件的作者没有义务提供任何形式的支持，也不承担任何责任。**

---

## 该插件的主要特性包括：

- 从网页中复制粘贴的内容中下载媒体文件
- 将来自 Word 或 Open Office 文档中复制粘贴的内容中的媒体文件进行本地化处理
- 从网络下载任何类型的文件
- 保存与笔记相关联的附件，这些附件位于以笔记命名的文件夹中。
- 从网页下载嵌入在 Markdown 标签中的文件，保存到本地存储中。
- 将 Base64 编码的嵌入图像保存到存储中。
- 将 PNG 格式的图片转换为 JPEG 格式的图像，并可以选择不同的质量等级。
- 使用 MD5 哈希算法进行数据加密和解密
- 从存储库中移除孤立的附件

## 安装

- 从 GitHub 下载最新版本/查看 GitHub 页面上的说明。阅读发布说明。
- 移除黑曜石本地图片插件，以避免产生任何冲突。
- 将压缩包解压到你的 Obsidian 存储空间中（例如：Myvault/.obsidian/plugins）。
- 重新启动 Obsidian 程序。
- 或者从“Obsidian 社区插件”目录中进行安装。
- 打开“社区插件”对话框，然后随意修改插件的设置。
- 尽情享受吧！

## 更新

- 从 Obsidian 的设置中更新插件，然后重新启动 Obsidian 程序。

```
This plugin has known compatibility issues with the following plugins:

* Paste Image Rename

* Pretty BibTex
```

## 使用方法/用途

只需复制任何网页内容、Word/Open Office 文档中的文本，然后将其粘贴到你的常规笔记或画布上的笔记中即可。

这个插件还能够处理所有附件的传输问题，比如截图、文件或音频文件的拖放操作。

![img](https://github.com/Sergei-Korneev/obsidian-local-images-plus/raw/main/docs/exampleimage.gif?raw=true)

可以在命令/菜单模式下使用它，或者在自动模式下使用（在设置中切换“自动处理”选项）：

[![img](https://github.com/Sergei-Korneev/obsidian-local-images-plus/raw/main/docs/commands.png?raw=true)](https://github.com/Sergei-Korneev/obsidian-local-images-plus/blob/main/docs/commands.png?raw=true)

`Localize attachments for the current note (plugin folder)` - 您的活动笔记将被处理，附件将被保存在插件设置中预定义的文件夹中。

或

`Localize attachments for the current note (Obsidian folder)` - 您的活动笔记将被处理，附件将被保存在 Obsidian 设置中预先配置的文件夹中。

或

`Localize attachments for all your notes (plugin folder)` 将会处理您存储库中的所有页面。这相当于在插件设置中使用了“包含”参数；而附件则会被保存在插件设置中预先配置好的文件夹中。

**注意：这个插件可能会一次性修改所有的笔记内容，因此建议定期备份您的文件。**

您还可以插入任何文件，例如：

`![mypdf](http://mysite/mypdf.pdf)`

`![mylocalfile](file:///mylinuxdisk/mysong.mp3)`

文件将被复制或下载到您的附件文件夹中。

![img](https://github.com/Sergei-Korneev/obsidian-local-images-plus/raw/main/docs/examplepdf.gif?raw=true)

**注意：我不建议使用这个插件来复制非常大的文件，因为该插件还无法实现从磁盘进行缓冲读取的功能。**

这个插件还允许你通过执行相关命令来删除未使用的附件：

`Remove all orphaned attachments (Plugin folder)`

以及

`Remove all orphaned attachments (Obsidian folder)`

第一个功能会在当前活动笔记旁边的文件夹中搜索丢失的附件，而第二个功能则会搜索所有笔记中未使用的附件。（这需要在 Obsidian 设置中配置一些根子文件夹）

所有附件的名称都是根据 MD5 算法生成的，因此它们在存储库中都是独一无二的。

这意味着你可以将附件文件放置在 Vault 中的任何位置，只需用文件名称替换标签中的绝对路径即可，而 Obsidian 仍然会在你的笔记中显示该文件。

## 捐款

分享你们对于这款软件的期望和想法吧，或者请我喝杯咖啡（或热巧克力）。

[![Buy Me A Coffee](https://camo.githubusercontent.com/0cf29a542375e1a46e84d8bf5805a4e5c0a6ee98b6547ccdc0c55eed49d99c69/68747470733a2f2f63646e2e6275796d6561636f666665652e636f6d2f627574746f6e732f76322f64656661756c742d79656c6c6f772e706e67)](https://www.buymeacoffee.com/sergeikorneev)

## 致谢

[niekcandaele 的](https://github.com/niekcandaele/obsidian-local-images)

[阿列克谢-雷佐夫](https://github.com/aleksey-rezvov/obsidian-local-images)

## 从源代码开始构建

```
npm run build
npm run dev
```