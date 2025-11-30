---
title: XML 监控器
source: https://distill.io/docs/web-monitor/xml-monitor/
author:
  - "[[Distill]]"
published: 2024-02-21
created: 2025-11-30
description: Learn how to monitor XML files for changes using Distill with support for XPath selection and various HTTP methods.
tags:
  - clippings
---
>   
> 适用于起步计划及以上版本。

### 什么是 XML？

  
XML（可扩展标记语言）是一种灵活的、基于标签的文本格式，主要用于数据结构和交换。

  
它既可被人类阅读，也可被机器读取，通常用于网络服务、RSS 源和配置文件中，因为它能够在不同系统中始终如一地组织数据。

###   
如何监控 XML 文件的变化？

  
Distill XML 监控器跟踪用于网络服务、RSS 源和数据交换的在线 XML 文件。XML 监控器自动检查在线托管 XML 格式数据的变化，并在检测到变化时发送警报。

  
在 XML 监控器中，您可以使用 XPath 来选择 XML 格式数据中的部分。 [使用 XPath 选择 XML 数据中的部分](https://distill.io/docs/web-monitor/xml-monitor/#xpath-xml-monitor) 。

*  
注意：常用 XML 格式的 RSS 和 Atom 订阅源可以通过 [Distill 订阅源监控](https://distill.io/docs/web-monitor/feed-monitor)进行有效监控。*

####   
支持 XML 监控的 HTTP 方法

- **GET**：从指定资源获取数据，是最常用的方法。
- **POST**、**PUT**、**PATCH**、**DELETE**：这些方法通常用于创建、更新或删除资源。

###   
如何使用 Distill 添加 XML 监控？

1. 从网络应用程序打开监视列表 [https://monitor.distill.io](https://monitor.distill.io/)，或导航到您的扩展程序的监视列表。
2. 点击 `  添加监控  ` -> `XML`。
	![Adding XML monitor](https://distill.io/docs/web-monitor/xml-monitor/images/037-xml-monitor.jpg)
3. 在 URL 字段中输入您要监控的 Web 服务的 URL。如果需要额外的配置，例如特定的 HTTP 请求参数、标头或正文内容，请使用“添加查询参数”。
4. 点击“GO”按钮。此操作将向指定 URL 发送 HTTP GET 请求。![Adding xml web service to monitor](https://distill.io/docs/web-monitor/xml-monitor/images/037-add-xml-url.jpg)
5. 当页面内容加载时，点击“选择”按钮。
![Setting up the XML URL](https://distill.io/docs/web-monitor/xml-monitor/images/037-selecting-params-xml.jpg)

6. 点击“保存”按钮。它将打开包含监控配置的选项页面。你可以根据需要修改此设置。
7. 设置所需的检查间隔、警报操作和条件。
8. 完成后，点击“保存”，XML 监控器应该会出现在您的监控列表中。您可以从监控列表中预览所跟踪的更改。
![Adding XML monitor](https://distill.io/docs/web-monitor/xml-monitor/images/037-change-history-xml.jpg)

###   
使用 XPath 选择 XML 页面中的特定元素

  
XPath 有助于在 XML 文档中精确选择特定节点。它非常适合监控目标部分以检测任何变化或更新。

1. 创建能够精确定位你感兴趣节点的 XPath 表达式。
	  
	例如，/bookstore/book 用于选择所有位于“bookstore”下的“book”元素。您可以使用谓词添加更复杂的表达式，例如：要选择需要“Mostly Shady”光照条件的植物：//plant\[@light='Mostly Shady'\]。
2. 在选项页面，点击“打开 XML 选择器”按钮旁边的齿轮图标。
3. 选择“配置 JSON”。
4. 在配置文本框中添加 XPath 选择器表达式。
5. 点击“保存”。
![Adding Xpath expression to XML monitor](https://distill.io/docs/web-monitor/xml-monitor/images/037-xpath-xml-monitor.jpg)