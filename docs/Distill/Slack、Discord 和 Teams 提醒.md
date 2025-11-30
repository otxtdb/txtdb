---
title: "Slack、Discord 和 Teams 提醒"
source: "https://distill.io/docs/web-monitor/change-notifications-on-slack-discord-and-teams/"
author:
  - "[[Distill]]"
published: 2020-02-14
created: 2025-11-30
description: "Get website change notifications in Slack, Discord, and Microsoft Teams. Set up instant alerts and collaborate with your team on web monitoring."
tags:
  - "clippings"
---
Distill 与第三方服务集成，以发送即时变更通知。Slack 和 Discord 的集成使用 webhook。这是一个高级功能，所有付费客户均可使用。要配置 webhook 操作，请按照以下步骤操作。

## Slack 输入 webhook

  
请查看 [https://api.slack.com/messaging/webhooks/getting\_started](https://api.slack.com/messaging/webhooks#getting_started) 以创建一个用于频道的输入 webhook URL。按照步骤操作后，您应该会得到一个类似此 URL 的链接：

```
https://hooks.slack.com/services/T00000000/B00000000/XXXXXXXXXXXXXXXXXXXXXXXX
```

  
复制此 URL 并按照以下步骤操作：

1. 前往您监控列表中的监控器的选项页面：[https://monitor.distill.io](https://monitor.distill.io/)
2. 在操作部分点击“添加操作”>“Slack 通知”。
3. 将 webhook URL 粘贴到输入框中，如下所示，然后保存。

![Slack change notification action](https://distill.io/docs/web-monitor/change-notifications-on-slack-discord-and-teams/images/slack-change-notification-action-.png "Slack change notification action")

  
对监控的后续更改将发送到配置在 Slack 入站 webhook 中的频道。

## Discord Webhook

  
查看 [https://support.discordapp.com/hc/en-us/articles/228383668-Intro-to-Webhooks](https://support.discordapp.com/hc/en-us/articles/228383668-Intro-to-Webhooks) 创建一个 Discord 的 webhook URL。完成后，你应该会得到一个类似这样的 URL：

```
https://discordapp.com/api/webhooks/400000000000000/XXXXXXXXXXX-XXXXXXXXXXXXXXXXXX
```

  
复制这个 URL 并按照以下步骤操作：

1. 前往 [https://monitor.distill.io](https://monitor.distill.io/) 在你的 Watchlist 中的监控器的选项页面
2. 点击“添加操作” > “Discord 通知”在操作部分。
3. 将 webhook URL 粘贴到输入框中，如下所示，然后保存。

![Discord change notification action](https://distill.io/docs/web-monitor/change-notifications-on-slack-discord-and-teams/images/discord-change-notification-action-.png "Discord change notification action")

  
对监控的后续更改将发送到 Discord webhook 设置中配置的频道。

## MS Teams Webhook

  
检查 [https://learn.microsoft.com/en-us/microsoftteams/platform/webhooks-and-connectors/how-to/add-incoming-webhook](https://learn.microsoft.com/en-us/microsoftteams/platform/webhooks-and-connectors/how-to/add-incoming-webhook) 以创建 MS Teams 的 webhook URL。完成后，你应该会得到一个类似这样的 URL：

```
https://XXXX.webhook.office.com/webhookb2/XXXXXX@XXXXXXX/IncomingWebhook/XXXXXXXXXX/XXXXXXXXXXX
```

  
复制这个 URL 并按照以下步骤操作：

1. 前往 [https://monitor.distill.io](https://monitor.distill.io/) 在你的 Watchlist 中的监控器的选项页面
2. 点击“添加操作” > “Microsoft Teams 通知”在操作部分下。
3. 将 webhook URL 粘贴到输入框中，如下所示，然后保存。

![MS Teams change notification action](https://distill.io/docs/web-monitor/change-notifications-on-slack-discord-and-teams/images/teams-change-notification-action-.png "Teams change notification action")

  
对监控的后续更改将发送到 Teams webhook 设置中配置的频道。