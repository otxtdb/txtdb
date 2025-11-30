---
title: "Feed 监视器"
source: "https://distill.io/docs/web-monitor/feed-monitor/"
author:
  - "[[Distill]]"
published: 2024-02-17
created: 2025-11-30
description: "Learn how to monitor RSS, XML, and JSON feeds with Distill. Set up automated tracking for content updates and new feed items."
tags:
  - "clippings"
---
###   
什么是订阅源监控器？

  
Distill Feed Monitor 跟踪 RSS 和 Atom 等网络订阅源，并自动监控来自不同在线来源的更新。

###   
Feed Monitoring 支持的 HTTP 方法

![Supported HTTP methods in feed monitor](https://distill.io/docs/web-monitor/feed-monitor/images/036-options-in-feed.jpg)

- **GET**：从指定资源获取数据，是 Feed 监控最常用的方法。Distill 使用 GET 请求从 Feed URL 获取最新内容，托管 RSS feed 的服务器返回请求的数据。
- **POST**、**PUT**、**PATCH**、**DELETE**：这些方法用于创建、更新、部分修改或删除 Feed，但它们不是监控所必需的。

###   
如何使用 Distill 添加 Feed 监控？

1. 在网页应用中打开监控列表，或在浏览器扩展中打开 [https://monitor.distill.io](https://monitor.distill.io/)。
2. 点击 `Add Monitor`\-> `Feed`。

![Add feed monitor from Watchlist](https://distill.io/docs/web-monitor/feed-monitor/images/036-add-feed.jpg)

3. 在 URL 字段中输入您要监控的网页服务的 URL。如果服务需要这些参数才能访问，请配置任何必要的 HTTP 请求参数、标头或正文内容。
4. 点击“GO”向 Feed URL 发送 HTTP GET 请求。

![adding feed monitor monitor URL](https://distill.io/docs/web-monitor/feed-monitor/images/036-add-feed-url.jpg)

5. 一旦订阅源加载完毕，点击“选择”。

![adding feed monitor URL](https://distill.io/docs/web-monitor/feed-monitor/images/036-select-feed.jpg)

6. 选项页面将打开进行配置。
7. 设置所需的检查间隔、警报操作和条件。
8. 点击“保存”将此订阅监控添加到您的监控列表中。

  
观看此视频学习如何设置订阅监控。

<iframe src="https://www.youtube-nocookie.com/embed/iaK2bs2pMH4?rel=0&amp;modestbranding=1" title="How to import and export monitors" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen="" loading="lazy" style="position:absolute;top:0;left:0;width:100%;height:100%;"></iframe>

[Watch on YouTube](https://youtu.be/iaK2bs2pMH4)

##   
如何在页面上找到订阅链接？

  
许多提供 RSS 订阅的网站会显示一个带有白色无线电波的橙色 RSS 图标。点击这个图标通常会带你到订阅的 URL 或提供一个链接。

![How to find rss feed on website](https://distill.io/docs/web-monitor/feed-monitor/images/036-find-rss.jpg)

  
有些网站使用标准的 Feed URL 模式。尝试在网站的主 URL 末尾添加 `/feed`、`/rss` 或 `/atom`。

  
另一种方法是查看页面的源代码。右键点击并选择“查看页面源代码”以打开 HTML 视图，然后搜索关键词如“feed”、“RSS”或“Atom”。

  
找到订阅链接，复制 `href` 属性中的 URL，并使用它来设置监控。

![How to find rss feed on website](https://distill.io/docs/web-monitor/feed-monitor/images/036-find-feed-url.jpg)

- 如果你想监控 JSON 订阅，可以使用 [JSON 监控](https://distill.io/docs/web-monitor/json-monitor/) 。
- 要监控除 RSS 和 Atom 订阅以外的 XML 文件，可以考虑使用 [XML 监控](https://distill.io/docs/web-monitor/xml-monitor/) 。

  
如果你需要关于订阅监控的帮助，或者有我们不处理的订阅 URL，请随时通过我们的 [Distill 论坛](https://forums.distill.io/)联系我们。你可以浏览现有讨论或在任何主题上发帖寻求帮助。