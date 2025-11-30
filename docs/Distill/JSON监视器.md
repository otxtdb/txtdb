---
title: "JSON监视器"
source: "https://distill.io/docs/web-monitor/json-monitor/"
author:
  - "[[Distill]]"
published: 2024-02-21
created: 2025-11-30
description: "Monitor JSON APIs and data feeds with Distill. Track changes in JSON responses, API endpoints, and structured data automatically."
tags:
  - "clippings"
---
>   
> JSON Monitor 可在 Starter 计划及以上版本中使用。

  
JSON（JavaScript 对象表示法）是一种用于网络数据交换的标准格式，常用于 Web 服务 API。由于其易于解析的特性，它被广泛用于数据存储和传输。JSON 可以有效地序列化复杂的数据结构，促进跨系统的数据交换。

###   
JSON 页面用在哪里？

  
驱动 API 的服务、电子商务平台、新闻聚合器、金融服务、社交媒体平台等由于其在数据组织方面的效率、快速解析能力和快速处理大型数据集以实现实时更新的能力，而使用 JSON 进行网络服务。

###   
什么是 JSON 监控器？

  
如果 URL 上有 JSON 数据，您可以使用 Distill JSON Monitor 进行监控。它自动跟踪 JSON 格式数据的更改并发送警报。这些更改警报可以涉及任何修改，例如内容、结构或值的更新。

  
JSON 监控器加载 URL 中的参数（如果有）。这些参数以键值对的形式表示。

![getting response from JSON page](https://distill.io/docs/web-monitor/json-monitor/images/038-json-params.jpg)

  
您可以通过点击“添加查询参数”来添加参数。

###   
JSON 监控器支持的 HTTP 方法

- **GET**: 从指定资源获取数据。它是获取 JSON 数据最常用的方法。
- **POST**, **PUT**, **PATCH**, **DELETE**: 这些是 JSON 监控器中分别用于创建、完全更新、部分修改和删除资源所使用的 HTTP 方法。

###   
如何设置 JSON 监控器？

1. 从网络应用程序打开监视列表 [https://monitor.distill.io](https://monitor.distill.io/)，或导航到您的扩展程序的监视列表。
2. 点击 `  添加监控  ` -> `JSON`。
	![Adding a JSON monitor for a webservice](https://distill.io/docs/web-monitor/json-monitor/images/038-json-monitor.jpg)
3. 在 URL 字段中输入您要监控的 Web 服务的 URL。![Adding a JSON monitor for a webservice](https://distill.io/docs/web-monitor/json-monitor/images/038-add-json-url.jpg)
4. GET 请求将显示 JSON URL 的内容。在这里，您可以使用复选框来监控您感兴趣的属性。
![Selecting params and properties to track on JSON service](https://distill.io/docs/web-monitor/json-monitor/images/038-json-page-properties.jpg)

5. 点击“GO”按钮。
6. 点击“保存”按钮。它将打开监控器的配置选项页面。
7. 设置所需的检查间隔、警报操作和条件。
8. 完成后，点击“保存”，JSON 监控器应该会出现在您的监控列表中。