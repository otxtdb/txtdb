---
title: "访问私有代码库——思维工具箱 --- Accessing Private Repositories"
source: "https://tfthacker.com/brat-private-repo"
author:
published:
created: 2026-07-04
description: "Quickly open GitHub repositories for Plugins and Themes - Toolbox for Thought"
tags:
  - "clippings"
taxonomy: { doc_category: [obsidian] }
---
> [!warning] 实验性的/通过实验得出的
> 该功能仍处于测试阶段。如有任何问题，请反馈至 [https://github.com/TfTHacker/obsidian42-brat/issues。请注意，该功能的设计初衷是保持简单易用，因此可能无法满足某些复杂项目的需求。](https://github.com/TfTHacker/obsidian42-brat/issues%E3%80%82%E8%AF%B7%E6%B3%A8%E6%84%8F%EF%BC%8C%E8%AF%A5%E5%8A%9F%E8%83%BD%E7%9A%84%E8%AE%BE%E8%AE%A1%E5%88%9D%E8%A1%B7%E6%98%AF%E4%BF%9D%E6%8C%81%E7%AE%80%E5%8D%95%E6%98%93%E7%94%A8%EF%BC%8C%E5%9B%A0%E6%AD%A4%E5%8F%AF%E8%83%BD%E6%97%A0%E6%B3%95%E6%BB%A1%E8%B6%B3%E6%9F%90%E4%BA%9B%E5%A4%8D%E6%9D%82%E9%A1%B9%E7%9B%AE%E7%9A%84%E9%9C%80%E6%B1%82%E3%80%82)

BRAT 支持使用个人访问令牌来访问 GitHub 上被标记为私有的代码库。

插件开发者可以为私有仓库创建访问令牌，该令牌允许用户仅以只读方式访问该仓库中的内容。你可以通过以下链接在用户个人资料中完成此操作： [https://github.com/settings/tokens?type=beta](https://github.com/settings/tokens?type=beta)

1. 在“设置”>“开发者设置”>“个人访问令牌”>“细粒度令牌”选项下，选择“生成新令牌”。
2. 将存储库的权限设置为希望授予访问权限的用户所对应的权限级别。
3. 请确保内容长度至少为 `read-only` 。

GitHub 现在会生成一个令牌，你可以将该令牌提供给你的测试用户。这些测试用户需要在 BRAT 的“设置”选项卡中，将此令牌填入“私有令牌”字段中。