---
title: "[Fooocus 2.1.822] Fooocus 涂抹或扩展（Midjourney 左/右/上/下）"
source: "https://github.com/lllyasviel/Fooocus/discussions/414"
author:
published:
created: 2026-05-19
description: "[Fooocus 2.1.822] Fooocus Inpaint or Outpaint (Midjourney Left/Right/Top/Bottom)"
tags:
  - "clippings"
taxonomy: { doc_category: [fooocus] }
---
Fooocus 2.1.822 添加了类似 Midjourney “左/右/上/下”箭头的 inpaint 和 outpaint 功能：

在 Fooocus 中的效果如下：

这个“Fooocus Inpaint”不仅是一个用户友好的界面，也是一种算法生成。Fooocus 使用自己的算法 DPMPP Fooocus inpaint，并且使用 Fooocus 自身的控制模型来最小化对基础模型风格的影响。该方法部分灵感来源于 [基于扩散的掩码引导语义图像编辑](https://openreview.net/forum?id=3lge0p5o-M-) 。

在整个 SDXL 开源社区中，Fooocus 是唯一一款允许您使用基于控制模型的 inpaint 功能，并配合任意基础模型的软件。

请注意，这种方法通常需要使用未更改或仅轻微更改的提示词来处理生成的图像。我们建议用户像这样拖动图像：

## Inpaint 示例

## Outpaint 示例

使用拖动进行 Outpaint：

## 高级：细节修复（面部、手部、眼睛、...）

有时，你可能会得到这样的图片：

整体都很完美，但眼睛/面部只是烦人：

现在你可以修复这样的细节：

请注意，这个界面还允许你为这次 inpaint 过程添加一些提示。如果你太懒了，也可以在这里使用快捷键：

然后你就能得到这样的结果

[![image](https://private-user-images.githubusercontent.com/19834515/284318752-c86d5da9-51f0-4bd7-a36f-9cb6fc14f9c9.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxNzk4MjYsIm5iZiI6MTc3OTE3OTUyNiwicGF0aCI6Ii8xOTgzNDUxNS8yODQzMTg3NTItYzg2ZDVkYTktNTFmMC00YmQ3LWEzNmYtOWNiNmZjMTRmOWM5LnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA1MTklMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNTE5VDA4MzIwNlomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWZjMTAwYTcwODhkMjU5Nzc4ZDc3NGIyYmU4ZThjMzQzMDEzNWJmYTUyNzBlN2ZkZWJmZjZmNTBlOTE1YzA4ZWEmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.rEoHjSQbljT6HFRXthr4zipLl_3a9aQ98P-ZgkXcxwg)](https://private-user-images.githubusercontent.com/19834515/284318752-c86d5da9-51f0-4bd7-a36f-9cb6fc14f9c9.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxNzk4MjYsIm5iZiI6MTc3OTE3OTUyNiwicGF0aCI6Ii8xOTgzNDUxNS8yODQzMTg3NTItYzg2ZDVkYTktNTFmMC00YmQ3LWEzNmYtOWNiNmZjMTRmOWM5LnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA1MTklMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNTE5VDA4MzIwNlomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWZjMTAwYTcwODhkMjU5Nzc4ZDc3NGIyYmU4ZThjMzQzMDEzNWJmYTUyNzBlN2ZkZWJmZjZmNTBlOTE1YzA4ZWEmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.rEoHjSQbljT6HFRXthr4zipLl_3a9aQ98P-ZgkXcxwg)

另一个例子：

之前：

之后：

## 高级：添加新对象/更改背景

你可以始终使用默认设置来添加新对象。但如果修改幅度太大，更好的方法是使用

例如：

更换背景：

这种"修改"模式会完全忽略原始内容，擅长处理具有纯色背景的图像，例如

## 非常高级：多遍修复

你可以先用常规的 inpaint 功能获取图像，然后将图像再次拖拽到 inpaint 输入中，接着将模式切换为"提升细节"并再次进行 inpaint。这样你将得到非常高的质量结果。（提升细节功能可用于改善任何细节，而不仅限于面部或手部）。