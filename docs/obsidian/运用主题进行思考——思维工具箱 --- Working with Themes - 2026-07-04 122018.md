---
title: "运用主题进行思考——思维工具箱 --- Working with Themes"
source: "https://tfthacker.com/brat-themes"
author:
published:
created: 2026-07-04
description: "Working with Plugins - Toolbox for Thought"
tags:
  - "clippings"
taxonomy: { doc_category: [obsidian] }
---
## 主题设置

在 BRAT 的设置中，你可以删除任何已注册的测试版主题。

## 一些有必要了解的、但比较枯燥的细节信息

## 版本控制

BRAT 的一个目标是让用户能够轻松地安装和更新自己想要测试的主题。

BRAT 会检查 Github 仓库中 themes.css 文件的提交日期。如果该文件的提交日期比本地安装的文件日期更新，BRAT 就会下载更新后的文件并替换掉本地版本。虽然这种方法通常有效，但并不能保证 100%可靠。

## BRAT 是如何将主题文件保存到保险库中的

BRAT 会从 Github 仓库中下载 theme.css 和 manifest.json 这两个文件，然后将它们保存到您在 Vault 中的“themes”文件夹里。

## theme.css 或 theme-beta.css

主题文件会被下载并以“theme.css”的名称存储在用户的仓库中。BRAT 会像 Obsidian 在下载主题时那样，去指定的仓库中查找名为“theme.css”的文件。不过，BRAT 会先查找名为“theme-beta.css”的文件。如果“theme-beta.css”存在，它就会被下载并作为主题来使用。这意味着什么呢？使用 BRAT 时，主题开发者有两种选择。

- 方案 1：在代码仓库中，放置一个名为 theme.css 的文件。BRAT 会自动下载该文件以进行测试。
- 方案 2：在仓库中，放置一个名为 theme-beta.css 的文件。BRAT 会自动下载该文件以进行测试。如果同时存在名为 theme.css 的文件，BRAT 会忽略 theme.css，而使用 theme-beta.css。这样一来，主题开发者就可以为公众提供正式版的 theme.css，同时保留用于测试的 theme-beta.css。测试结束后，主题开发者只需删除 theme-beta.css，并将经过修改的 theme.css 发布给公众。请注意，只要 theme-beta.css 存在，theme.css 就会被忽略。主题开发者需要妥善处理这种情况，避免让测试人员使用到过时的 theme-beta.css 文件。

请记住，由于缓存的原因，GitHub 上主题的更新需要几分钟时间才能显示给用户。因此，建议您在完成更改后让用户等待几分钟再尝试更新。否则，BRAT 可能会出现混乱。关于如何处理这种情况，请参阅接下来的说明。

此外，有时 BRAT 可能会搞不清主题文件的最新版本是什么。在这种情况下，请让测试人员从 BRAT 中取消该主题的注册，并删除磁盘上的相关文件。

BRAT 并不查看 manifest.json 文件中的主题信息，而是通过检查主题的校验和来判断是否有变化。因此，如果你想更新正在测试中的主题，就需要修改相应的文件：要么是 theme-beta.css，要么是 theme.css。具体取决于你在代码仓库中采用的测试策略。

## 删除测试版主题

当某个主题从 BRAT 设置界面中的“测试版主题”列表中被删除后，该主题的 theme.css 和 manifest.json 文件并不会从系统中被删除。用户可以通过“设置”>“外观”来删除该主题。此时，BRAT 将不再对该主题进行更新检测。