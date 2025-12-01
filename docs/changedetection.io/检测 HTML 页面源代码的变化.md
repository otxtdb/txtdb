---
title: "检测 HTML 页面源代码的变化"
source: "https://github.com/dgtlmoon/changedetection.io/wiki/Detecting-changes-in-HTML-page-sources"
author:
  - "[[GitHub]]"
published:
created: 2025-12-01
description: "Best and simplest tool for website change detection, web page monitoring, and website change alerts. Perfect for tracking content changes, price drops, restock alerts, and website defacement monitoring—all for free or enjoy our SaaS plan! - Detecting changes in HTML page sources · dgtlmoon/changedetection.io Wiki"
tags:
  - "clippings"
---


  
对于某些网页，最好通过查看 HTML 页面的源代码获取相关信息。

## 用例  
例如，像 [https://www.campuspoint.de](https://www.campuspoint.de/) 这样的网站的 HTML 响应包含了以 JSON 格式发布的产品列表，然后在客户端用 JS 处理以生成最终标记。也可以使用支持 JS 的 [Playwright 内容获取器](https://github.com/dgtlmoon/changedetection.io/wiki/Playwright-content-fetcher)来创建这样的网页，但与页面源码对照更高效。

## 方法- 在“通用”标签页中，在目标 URL 前加上`来源：`（示例： `source:https://www.campuspoint.de/mobile/notebooks/lenovo/thinkpad-t-serie/thinkpad-t14s.html` ）
- 在请求标签页中，选择“基本快速明文/HTTP 客户端”取指方法
- 在“筛选与触发器”标签中选择合适的触发器，例如基于正则表达式的“提取文本”触发器。
	- 举个例子：用 `/“product_count”:(\d+）/i` 来检查 campuspoint.de 是否会将某个系列笔记本的新型号加入库存。

  
更多内容请见 [https://changedetection.io/tutorial/source-code-monitor-how-get-alerts-changes-html-source-code](https://changedetection.io/tutorial/source-code-monitor-how-get-alerts-changes-html-source-code)