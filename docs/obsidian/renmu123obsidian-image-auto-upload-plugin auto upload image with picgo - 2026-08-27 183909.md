---
title: "renmu123/obsidian-image-auto-upload-plugin: auto upload image with picgo"
source: "https://github.com/renmu123/obsidian-image-auto-upload-plugin"
author:
published:
created: 2026-08-27
description: "auto upload image with picgo. Contribute to renmu123/obsidian-image-auto-upload-plugin development by creating an account on GitHub."
tags:
  - "clippings"
taxonomy: { doc_category: [obsidian] }
---
## renmu123/obsidian-image-auto-upload-plugin：使用 PicGo 进行图片自动上传

## 黑曜石图片自动上传插件

这是一个用于支持通过 PicGo、PicList 和 PicGo-Core 将图片上传到图片库的工具。更新插件后，请记得重新启动 Obsidian 软件。

**未在 Mac 系统上进行测试**

## 开始

1. 安装 PicGo 工具并对其进行配置，请参阅官方网站上的说明。
2. 请启用 PicGo 的服务器服务，并记住相关的端口号。
3. 安装插件
4. 打开插件设置，并将其设置为 `http://127.0.0.1:{{port set in PicGo}}/upload` （例如 `http://127.0.0.1:36677/upload` ）。
5. 请尝试看看上传是否成功。

## 设置图片和 configName

如果您使用的是 PicList（版本大于等于 2.5.3），可以通过 URL 参数来设置图片的存储位置和配置名称。例如： `http://127.0.0.1:36677/upload?picbed=smms&configName=piclist` 这样可以将图片上传到 `smms` 指定的位置，并使用 PicList 的配置名称。利用这一功能，您可以將图片上传到不同 Obsidian 存储库中的不同存储位置。

## 特点

## 上传时同时粘贴图片

当你在 Obsidian 平台上粘贴一张图片时，这个插件会自动将图片上传到相应的位置。

你可以在 `frontmatter` 中设置 `image-auto-upload: false` 来控制一个文件。

支持".png"、".jpg"、".jpeg"、".bmp"、".gif"、".svg"、".tiff"、".webp"、".avif"格式的文件。

由于 PicGo 2.3.0-beta7 中存在漏洞，无法使用此功能。请安装其他版本的 PicGo。

```yaml
---
image-auto-upload: true
---
```

## 通过命令上传所有本地图片文件

点击 `ctrl+P` ，输入 `upload all images` ，然后按 Enter 键，所有本地图片将会自动上传。

## 将整个互联网内容下载到本地

点击 `ctrl+P` ，输入 `download all images` ，然后按 Enter 键。这样就能自动将所有的网络图片下载到本地。仅在 Windows 10 操作系统上测试。

## 通过 contextMenu 功能上传图片

现在你可以在编辑模式下通过 contextMenu 来上传图片了。

## 支持拖放操作

只适用于 picgo 或 picList 应用程序。

## 服务器模式

你可以在服务器上部署 PicList 或 PicList-Core，然后将其用于上传操作。

请支持 PicList 2.6.3 版本，或者 PicList-Core1.3.0 版本之后的版本。

在这种模式下，你无法上传网络文件。如果你在粘贴图片时遇到上传失败的情况，可以尝试启用该模式。

## 支持 picgo-core 功能

你可以使用 npm 来安装 picgo-core 模块。更多详细信息请参阅文档。

## 待办事项

- 通过命令上传所有本地图像文件
- 如果上传了图片，请使用 YAML 格式作为配置文件。
- 支持 picgo-core 模块
- 支持从系统中上传图片，并选择已选定的图片进行上传。
- 支持网络图片