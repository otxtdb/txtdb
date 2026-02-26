---
title: "关于 SearXNG"
source: "https://docs.searxng.org/user/about.html"
author:
published:
created: 2026-02-26
description:
tags:
  - "clippings"
taxonomy: { doc_category: [searxng] }
---
SearXNG 是一个[元搜索引擎](https://en.wikipedia.org/wiki/Metasearch_engine) ，聚合其他 `搜索引擎   的结果 `，同时不存储用户信息。

SearXNG 项目由开放社区驱动。如果你有任何问题或只是想聊聊 SearXNG，欢迎加入 Matrix： [#searxng:matrix.org](https://matrix.to/#/#searxng:matrix.org)

让 SearXNG 变得更好：

- 您可以在 [Weblate](https://translate.codeberg.org/projects/searxng/) 上改进 SearXNG 翻译，或者…
- 跟踪开发，提交贡献，报告问题请访问 [SearXNG 源代码](https://github.com/searxng/searxng) 。
- 获取更多信息，请访问 [SearXNG 文档](https://docs.searxng.org/) 。

## 为什么要使用它？[¶](https://docs.searxng.org/user/#why-use-it "Link to this heading")

- SearXNG 可能不会像 Google 那样为您提供个性化的结果，但它不会为您生成个人资料。
- SearXNG 不关心你搜索什么，从不与第三方分享任何信息，也无法被用来损害你。
- SearXNG 是自由软件；代码完全开放，欢迎所有人使其变得更好。

如果你关心隐私，想做一个有意识的用户，或者在其他方面相信数字自由，将 SearXNG 设为你的默认搜索引擎或在自己的服务器上运行它！

##   如何将其设置为默认搜索引擎？

SearXNG 支持 [OpenSearch](https://github.com/dewitt/opensearch/blob/master/opensearch-1-1-draft-6.md)。有关更改默认搜索引擎的信息，请参阅浏览器的文档：

- [Firefox](https://support.mozilla.org/en-US/kb/add-or-remove-search-engine-firefox)
- [Microsoft Edge](https://support.microsoft.com/en-us/help/4028574/microsoft-edge-change-the-default-search-engine) - 链接背后，你还会找到一些适用于 Chrome 和 Safari 的实用说明。
- [Chromium](https://www.chromium.org/tab-to-search)\-基于的浏览器仅添加用户直接访问的网站，无需路径。

添加搜索引擎时，不能有同名的重复项。如果你遇到无法添加搜索引擎的问题，可以采取以下措施：

- 删除重复项（默认名称：SearXNG），或
- 联系所有者，为实例指定一个不同于默认名称的名称。

## 它是如何工作的？¶

SearXNG 是知名 [searx](https://github.com/searx/searx) [元搜索引擎](https://en.wikipedia.org/wiki/Metasearch_engine) 的分支，其灵感来源于 [Seeks 项目](https://beniz.github.io/seeks/) 。它通过将您的查询与其他平台进行混合搜索来提供基本的隐私保护，且不存储搜索数据。SearXNG 可添加到您的浏览器搜索栏中；此外，它还可以被设置为默认搜索引擎。

  
`stats  页面 ` 包含一些关于所使用引擎的匿名使用统计信息。

##   
如何让它成为我的专属？¶

SearXNG 感谢您对日志的关切，因此请从 [SearXNG 源代码](https://github.com/searxng/searxng) 并自行运行！

将您的实例添加到这个 [公共实例列表](https://searx.space/) 中，以帮助其他人夺回他们的隐私，让互联网更加自由。互联网越去中心化，我们拥有的自由就越多！