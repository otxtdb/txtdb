---
title: "使用 Chrome 扩展程序"
source: "https://distill.io/docs/web-monitor/distill-chrome-extension/"
author:
  - "[[Distill]]"
published: 2019-09-05
created: 2025-11-30
description: "Learn how to use the Distill Chrome Extension to monitor website changes set up page monitors customize notifications and track updates across different web pages."
tags:
  - "clippings"
---
Distill 是专业人士最先进的页面监控工具。浏览器扩展是监控页面或信息流的最容易和最快的方式。它也可以监控动态页面和 iframe。了解更多功能，请访问 [distill.io/features](https://distill.io/features)。

> **  
> 开始使用，请下载扩展程序 - [Chrome](https://chrome.google.com/webstore/detail/distill-web-monitor/inlikjemeeknofckkjolnjbpehgadgge?hl=en) | [Firefox](https://addons.mozilla.org/en-US/firefox/addon/distill-web-monitor-ff) | [Opera](https://addons.opera.com/en/extensions/details/distill-web-monitor) | [Edge](https://microsoftedge.microsoft.com/addons/detail/distill-web-monitor/hldhhgncaohjmpcjjhggekonocabhceg)**

  
安装完成后，点击扩展程序托盘并将 Distill 固定到浏览器中，以便轻松访问。

![Steps to pin Distill extension to browser](https://distill.io/docs/web-monitor/distill-chrome-extension/images/pin_distill.jpg)

##   
使用 Distill Chrome 扩展监控网站变化的步骤

<iframe src="https://www.youtube-nocookie.com/embed/8bT_GRlY7aE?rel=0&amp;modestbranding=1" title="How to import and export monitors" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen="" loading="lazy" style="position:absolute;top:0;left:0;width:100%;height:100%;"></iframe>

[Watch on YouTube](https://youtu.be/8bT_GRlY7aE)

  
**第一步：** 打开你想监控的网页。

  
**步骤 2:** 点击 Chrome 工具栏中的 Distill 液滴图标。它会打开一个带有菜单的窗口。点击向下的箭头图标以展开下拉菜单。

  
**步骤 3:** 点击“监控整个页面”选项以监控整个网页，或点击“监控页面部分”选项以仅监控网页的选定部分或区域。例如，仅监控商品的价格。

![Steps to set up page monitor with Distill Chrome extension](https://distill.io/docs/web-monitor/distill-chrome-extension/images/options-menu.jpg)

  
如果网页支持，你也可以选择监控 RSS 订阅页面。

  
**步骤 4:** 如果你要监控页面的部分内容，视觉选择器会打开。使用鼠标光标点击并选择。你可以使用尖括号图标来收缩/展开和删除选择区域。

  
接下来，在预览中验证你的选择，然后点击“保存选择”。

![Steps to set up page monitor with Distill Chrome extension](https://distill.io/docs/web-monitor/distill-chrome-extension/images/visual-selector.jpg)

  
**第 5 步：** 现在您将被重定向到选项页面。在这里，您可以自定义监控器的设置。

*  
注意：如果您正在监控整个页面，您将直接进入第5步，并且不需要执行第4步。*

![Steps to set up page monitor with Distill Chrome extension](https://distill.io/docs/web-monitor/distill-chrome-extension/images/option-page.jpg)

  
**第 6 步：** 您可以选择用于检查页面的设备，重命名您的监控器，并[安排检查频率](https://distill.io/docs/web-monitor/schedule-checks/)进行监控。

  
**步骤 7：** 要设置通知，请点击“添加操作”。要使用电子邮件和短信等方法，您需要登录并添加您的详细信息。警报方法的可用性取决于您的[订阅计划](https://distill.io/pricing/) 。

  
**步骤 8：** 完成后，点击“保存”。现在，您的第一个监控器已添加到 Distill。

  
您的监控器将出现在 Distill 的“ [监控列表](https://distill.io/docs/web-monitor/what-is-watchlist/ "Watchlist") ”中。这是一个包含所有监控器的仪表板。

*  
注意：您可以使用相同的步骤开始使用 Distill 的 Opera、Edge 和 Firefox 扩展。*

###   
如何禁用本地监控器的检查？

  
要关闭单个监控器，请点击开/关按钮。要禁用多个监控器，使用复选框选择它们，然后点击“批量编辑”并选择“关闭”以禁用所有选定的监控器。

![Steps to turn off web monitors](https://distill.io/docs/web-monitor/distill-chrome-extension/images/turn-off-monitor.jpg)

  
或者，您可以通过点击扩展程序，点击下拉菜单并选择“关闭本地监控”来关闭本地监控。

![Steps to turn off web monitors](https://distill.io/docs/web-monitor/distill-chrome-extension/images/disable-monitor.jpg)

###   
如何更改并发工作者的数量？

  
并发工作者决定在本地设备（浏览器扩展或桌面应用）上同时执行的最大检查次数。默认情况下，限制设置为3，最大值为10。增加此数字允许进行更多并发检查，但由于资源使用量更高，可能会降低系统性能。

  
要更改并发工作者的数量，请点击齿轮图标，进入“设置”→“高级”，并在提供的文本框中更改并发工作者的数量。

![Changing number of concurrent workers](https://distill.io/docs/web-monitor/distill-chrome-extension/images/concurrent-workers.jpg)

###   
如何阻止页面在标签页中加载？

  
您可以选择在后台或窗口中强制执行所有检查。前往“设置”->“高级”，并选择页面应如何打开和检查更改。

![Options to run webpage checks in extension](https://distill.io/docs/web-monitor/distill-chrome-extension/images/tab-for-checks.jpg)

| **选项** | **描述** |
| --- | --- |
| `Tab` | （默认）将在您的活动浏览器中打开一个新标签页并运行检查。网页检查完成后，该标签页将自动关闭。 |
| `Window` | 将打开一个新的浏览器窗口来运行检查，完成后自动关闭。 |
| `Background` | 将强制在后台进行检查。最适合静态网页。它不适用于具有动态内容的页面。 |
| `Sticky Window` | 将保留一个最小化的窗口用于检查。此窗口将保持打开状态，并在检查完成后不会自动关闭。 |

  
或者，您可以使用 [Distill 桌面应用](https://distill.io/apps/web-monitor/)来运行您的监控器。这不会为检查打开新标签页。在页面在不活跃的标签页中不显示内容的情况下，桌面应用运行效果良好。

###   
如何为检查添加时间段？

>   
> 仅限本地监控器的付费计划可用。

  
您可以定义检查的具体时间段。例如：

  
开始时间：上午5:00

  
结束时间：下午6:00

  
日期：周一至周五

  
在这个例子中，检查的时间段将是工作日的早上5点到下午6点。检查将在周一至周五的这段时间内进行。

  
配置检查时间段步骤：

1. 点击左下角的设置齿轮图标。
2. 点击高级。
3. 使用复选框启用时间段，并根据您的需求设置时间段。
![How to add time slots for checks?](https://distill.io/docs/web-monitor/distill-chrome-extension/images/time-slot.jpg)

##### 常见问题解答

**  
1\. 如果我的设备关机了，监控器还会工作吗？**

  
不，如果您的设备关机了，监控器将不会工作。Distill Chrome 扩展依赖于您设备的浏览器进行检测。如果您的设备关机，浏览器扩展无法运行或检查监控页面的更新。

**  
2\. 我如何删除一个监控器？**

  
要删除监控器，请选择该监控器并点击垃圾桶按钮。您的监控器将被移至回收站。

**  
3\. 我如何编辑我的账户设置？**

  
点击齿轮图标 → 点击设置 → 选择账户。在这里你可以编辑你的个人资料信息并访问其他账户设置选项。

**  
4\. 如何解决遇到错误的监控器？**

  
如果监控器出现错误，你会在监控列表中看到它对应的红色时间戳。点击更多详情并参考我们的[故障排除文档](https://distill.io/docs/web-monitor/troubleshooting-errors/)进行下一步操作。

**  
5\. 我应该选择什么设备来运行我的监控器？**

  
在使用 Distill Chrome 扩展进行本地监控时，请选择您的 Chrome 浏览器作为运行监控器的设备。有关本地和云监控器的更多信息 [请点击这里。](https://distill.io/docs/web-monitor/cloud-local-monitors/)

##### 联系我们

  
如果您有任何疑问或需要帮助，可以通过 [Distill 论坛](https://forums.distill.io/)联系我们。将您的建议发送至 [support@distill.io](https://distill.io/docs/web-monitor/distill-chrome-extension/)。我们期待您的反馈。

  
要了解如何使用 Distill 解决各种用例，请查看我们的以下快速入门文章：

1. [  
	如何监控商品价格？](https://distill.io/blog/how-to-track-price-drop-on-sneakers/)
2. [  
	如何监控演唱会和活动门票？](https://distill.io/blog/track-tickets-on-ticketmaster/)
3. [如何监控网络以获取竞争情报](https://distill.io/blog/competitive-intelligence-tips/) ？
4. [  
	如何追踪最新的 SEC 文件？](https://distill.io/blog/track-sec-filings/)
5. [  
	如何追踪即将发布的 PS4 游戏发售日期？](https://distill.io/blog/track-game-release-dates/)

[  
在 Distill 博客上探索更多用例。](https://distill.io/tags/usecase/)

Distilling 愉快！