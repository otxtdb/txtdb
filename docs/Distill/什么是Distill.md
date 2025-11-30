---
title: "什么是Distill"
source: "https://distill.io/docs/web-monitor/what-is-distill/"
author:
  - "[[Distill]]"
published: 2023-02-22
created: 2025-11-30
description: "Distill is a website change monitoring tool that allows users to track changes to websites and receive alerts when changes are detected across various document types."
tags:
  - "clippings"
---
Distill 是一款网站变更监控工具。它允许用户追踪网站的变更，并在检测到变更时接收警报。

## Distill 的工作原理

  
Distill 通过按计划打开网页、读取页面的 HTML 内容，并在检测到变化时通知您来监控网页。

###   
运行监控器的两种方式

| **类型** | **如何添加**                                  | **运行位置**           | **   您的设备需要开机吗？**     |
| ------ | ----------------------------------------- | ------------------ | --------------------- |
| 本地监控   | 通过 Distill 的浏览器扩展或桌面应用程序添加（默认设置）          | 在您的设备上（您的浏览器/应用程序） | 是的。保持浏览器/应用程序打开以运行检查。 |
| 云监控    | 通过网页应用程序在 `monitor.distill.io` 处添加（默认在那里） | 在 Distill 的服务器上    | 不运行检查，即使您的设备已关闭。      |

  
关于本地和云检查的更多信息，请访问 [https://distill.io/docs/web-monitor/cloud-local-monitors/](https://distill.io/docs/web-monitor/cloud-local-monitors/)。

###   
每次检查时会发生什么

1. **  
	打开源 URL**
	- 本地监控：你的浏览器/应用程序打开 URL。
	- 云端监控：Distill 的服务器打开 URL。
2. **读取内容** 。
3. **与上次比较。** 如果内容不同，Distill 会将新版本记录在**变更历史**中。
4. **  
	评估条件（可选）。**
	- 如果**条件**已设置，Distill 会使用它们检查检测到的变更。只有当条件为 `true` 时，才会继续下一步。
5. **触发警报**
	- 所有**操作**在监控器上设置后都会被触发。

>   
> **注意：** 操作可以包括为监控器设置的通知等内容。

## 支持的监控类型

1. [网页](https://distill.io/docs/web-monitor/using-web-app-to-track-webpage-changes/)
2. [PDF](https://distill.io/docs/web-monitor/monitor-pdf-for-changes/)
3. [JSON](https://distill.io/docs/web-monitor/json-monitor/)
4. [Word doc](https://distill.io/docs/web-monitor/word-doc-monitor/)
5. [XML](https://distill.io/docs/web-monitor/xml-monitor/)
6. [信息流](https://distill.io/docs/web-monitor/feed-monitor/)
7. [运行时间](https://distill.io/docs/web-monitor/uptime-monitor/)
8. [网站地图](https://distill.io/docs/web-monitor/sitemap-monitor-using-a-crawler/)

  
变更通知可以通过电子邮件、短信（文本消息）、推送通知（移动应用）、Discord、Slack、MS Teams 以及其他与 Distill 的 webhook 调用集成的应用程序接收。

## 平台

- Web 应用 - 可随时从云端访问 [https://monitor.distill.io/](https://monitor.distill.io/)。
- 浏览器扩展 - 支持 [Chrome](https://chrome.google.com/webstore/detail/distill-web-monitor/inlikjemeeknofckkjolnjbpehgadgge)、[Firefox](https://addons.mozilla.org/en-US/firefox/addon/distill-web-monitor-ff/)、[Opera](https://addons.opera.com/en/extensions/details/distill-web-monitor/) 和 [Edge](https://microsoftedge.microsoft.com/addons/detail/distill-web-monitor/hldhhgncaohjmpcjjhggekonocabhceg)。
- 手机应用 - 支持 [iOS](https://apps.apple.com/us/app/distill-web-monitor/id1118660791?ls=1) 和 [Android](https://play.google.com/store/apps/details?id=com.neemb.distill&hl=en-US&ah=y7Mom-e3CqGdwzdBm8TCBMVK3Sc)。
- 桌面应用 - 目前处于公开阿尔法测试阶段。请查看 [https://distill.io/apps/web-monitor/](https://distill.io/apps/web-monitor/) 获取应用链接。

  
网站可以在 Distill 的服务器（云端）或用户的浏览器（本地检查）上检查变化。

  
Distill 支持免费计划。请查看 [Distill 计划与价格](https://distill.io/pricing/) 了解更多详情。

  
这里有一些有用的文章，展示了您如何使用 Distill 来监控不同类型的网页：

- [  
	在线跟踪和购买音乐会及活动门票](https://distill.io/blog/track-concert-tickets-and-event-tickets/)
- [  
	监测美国签证预约日期的可用性](https://distill.io/blog/track-availability-of-us-visa-appointment-slots-using-distill/)
- [  
	使用网络监控进行竞争情报](https://distill.io/blog/competitive-intelligence-tips/)
- [  
	追踪即将发布的运动鞋、尺码补货和限量版产品](https://distill.io/blog/track-upcoming-sneaker-releases/)

  
查看 [Distill 博客](https://distill.io/blog/) ，了解更多关于不同用例和如何使用网络监控的指南