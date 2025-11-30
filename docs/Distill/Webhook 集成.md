---
title: "Webhook 集成"
source: "https://distill.io/docs/web-monitor/trigger-webhook-on-website-change/"
author:
  - "[[Distill]]"
published: 2024-05-28
created: 2025-11-30
description: "Trigger webhooks on website changes. Integrate Distill with external applications, APIs, and services for automated workflow responses."
tags:
  - "clippings"
---
### 什么是 Webhook？

  
Webhook 是用户定义的 HTTP 回调。它们由事件触发，并可用于将第三方应用程序与 Distill 集成。您可以在 Distill 中使用 webhook 操作向 webhook URL 发送 POST 请求。

###   
如何在 Distill 中使用 Webhook 操作？

  
您可以从操作列表中设置 webhook 操作。此功能仅限付费客户使用。

  
以下是添加 webhook 操作的步骤。

1. 通过点击监控的上下文菜单选项（如下面所示的下箭头图标），进入“选项页面”。![context menu for options page](https://distill.io/docs/web-monitor/trigger-webhook-on-website-change/images/options-page.png "options-page")
2. 从操作列表中选择“Webhook 调用”，并在占位符中添加 Webhook URL。
3. 点击 Webhook 下的“显示选项”来配置需要作为 POST 请求发送的 Webhook 参数。![option for webhook parameters](https://distill.io/docs/web-monitor/trigger-webhook-on-website-change/images/web-hook-show-options.jpg "webhook parameter options")
4. 您还可以通过点击 Webhook 下的“Header”来配置头部参数。
5. 完成 webhook 配置后保存。

### Webhook 参数

  
以下值可用于 webhook 参数字段。

1. {{sieve.id}} - 监控器的 ID。
2. {{sieve.name}} - 监控器的名称。
3. {{sieve.tags}} - 监控器的标签。这仅在云环境中有效。
4. {{sieve.uri}} - 监控器的 URL。
5. {{sieve\_data.text}} - 监控器的文本值。
6. {{sieve\_data.ts}} - 检测到变更的时间戳。
7. {{sieve\_data.data}} - 监控的 HTML 数据。

  
您还可以组合这些值。例如，字段中的值可以是：{{sieve\_data.name}} - {{sieve.uri}} - {{sieve\_data.text}}

  
这是默认 webhook 字段的样式。此外，您可以通过点击“添加查询参数”来添加参数。

![webhook-fields](https://distill.io/docs/web-monitor/trigger-webhook-on-website-change/images/webhook-options.jpg "webhook-fields")

### 故障排除

1. 确保 webhook URL 是公开可访问的。
2. 检查你是否订阅了来自 [https://accounts.distill.io/account/#/plans/](https://accounts.distill.io/account/#/plans/) 的付费计划。
3. 检查您是否未达到每月 webhook 操作的配额，请访问 [https://monitor.distill.io/#/usage/monthly](https://monitor.distill.io/#/usage/monthly)。
4. 要测试您的 Webhook URL，您可以在 Distill 的浏览器扩展中添加一个测试监控器，监控 [https://www.timeanddate.com/](https://www.timeanddate.com/)（选择当前时间），然后手动运行监控器来检查 POST 数据。您还可以使用 POSTMAN 等服务，在您的测试 URL 上发送 GET 请求并接收 POST 请求。

###   
如何测试 Webhook？

1. 在浏览器扩展中为 [https://www.timeanddate.com/](https://www.timeanddate.com/) 添加一个测试监控。
2. 设置 Webhook 操作，并从测试提供网站如 [https://webhook.site/](https://webhook.site/) 添加一个 Webhook URL，然后保存。
3. 通过点击运行按钮，在监控列表中手动检查此监控。
	![manual-check-button](https://distill.io/docs/web-monitor/trigger-webhook-on-website-change/images/manual-check.png "manual-check-button")
4. 打开 webhook 网站检查 POST 数据。它以 [https://webhook.site/#!/](https://webhook.site/#!/) 开头，后面跟着 URL ID。上面测试 URL 的样子就是这样。
	![webhook-post-data-format](https://distill.io/docs/web-monitor/trigger-webhook-on-website-change/images/webhook-post-data.png "webhook-post-data-format")