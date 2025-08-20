
# 自动检测网站变化 — 实时监控网页更改

[](https://github.com/dgtlmoon/changedetection.io#detect-website-changes-automatically--monitor-web-page-changes-in-real-time)

监控网站更新 — 通过 Discord、邮件、Slack、Telegram、Webhook 等多种方式接收通知。

**检测网页内容变化并立即收到警报。**

适用于监控价格变动、内容编辑、条件变化等多种情况。

### 使用视觉选择工具针对网页的特定部分进行监控。

[](https://github.com/dgtlmoon/changedetection.io#target-specific-parts-of-the-webpage-using-the-visual-selector-tool)

在连接到 [playwright 内容抓取器](https://github.com/dgtlmoon/changedetection.io/wiki/Playwright-content-fetcher) （作为订阅服务的一部分提供）时可用

[![Select parts and elements of a web page to monitor for changes](https://cdn.jsdelivr.net/gh/otxtdb/txtdb@master/_txtdbpic/38a6fe0b419bab5fbdefa21f735d1002_MD5.gif)](https://changedetection.io/?src=github)

### 轻松查看发生了哪些变化，逐词、逐行或逐个字符进行检查。

[](https://github.com/dgtlmoon/changedetection.io#easily-see-what-changed-examine-by-word-line-or-individual-character)

[![Self-hosted web page change monitoring context difference](https://cdn.jsdelivr.net/gh/otxtdb/txtdb@master/_txtdbpic/756b88ba25a0991ee462a67d3a6d9144_MD5.png)](https://changedetection.io/?src=github)

### 执行交互式浏览器操作

[](https://github.com/dgtlmoon/changedetection.io#perform-interactive-browser-steps)

填写文本框，点击按钮等，设置你的网站变化检测场景。

使用**浏览器步骤**配置，添加在进行变化检测之前的基本步骤，例如登录网站、将商品加入购物车、接受 cookie 登录、输入日期并细化搜索。

[![Website change detection with interactive browser steps, detect changes behind login and password, search queries and more](https://cdn.jsdelivr.net/gh/otxtdb/txtdb@master/_txtdbpic/ebc90beae1269332b7ea761a02743808_MD5.gif)](https://changedetection.io/?src=github)

运行完**浏览器步骤**后，访问**视觉选择器**标签以细化你感兴趣的内容。这需要启用 Playwright。

### 超赞的补货和价格变动通知

[](https://github.com/dgtlmoon/changedetection.io#awesome-restock-and-price-change-notifications)

启用 _"单个产品页面的补货和价格检测"_ 选项，以激活最佳的产品价格监控方式。这将提取 HTML 页面中的元数据，并提供多种选项来跟踪产品的价格。

从仪表板中轻松组织和监控产品的价格，当产品的价格发生变化或重新上架时，你将收到警报和通知！

[![Easily keep an eye on product price changes directly from the UI](https://cdn.jsdelivr.net/gh/otxtdb/txtdb@master/_txtdbpic/8621040c9cf6bb801ebf9f47a1be034b_MD5.png)](https://changedetection.io/?src=github)

设置价格变动通知参数，包括最高价、最低价、价格变动百分比等。随时了解产品降价信息。

[![Set upper lower and percentage price change notification values](https://cdn.jsdelivr.net/gh/otxtdb/txtdb@master/_txtdbpic/9183f8168c1f5496cb23ec0675957974_MD5.png)](https://changedetection.io/?src=github)

### 示例应用场景

[](https://github.com/dgtlmoon/changedetection.io#example-use-cases)

- 产品和服务价格发生变化
- 缺货通知和重新上架通知
- 监控和跟踪 PDF 文件更改，了解 PDF 文件何时有文本更改。
- 政府部门更新（更改通常仅在其网站上）
- 新软件发布、安全公告（如果您不在其邮件列表中）
- 节日中的更改
- Discogs 补货提醒和监控
- 房地产列表变更
- 了解你喜爱的威士忌何时打折，或在其他人之前获悉其他特别优惠
- 政府网站上的疫情相关新闻
- 大学/组织网站上的新闻
- 检测和监控 JSON API 响应中的变化
- JSON API 监控和告警
- 法律和其他文件中的变更
- 当网站上出现特定文本时触发 API 调用通知
- 使用 JSON 过滤器和 JSON 通知连接 API
- 根据网页内容变更创建 RSS 订阅
- 监控 HTML 源代码以检测意外更改，增强您的 PCI 合规性
- 你有一个非常敏感的 URL 列表需要监控，并且你不想使用付费替代方案。（记住，你是产品）
- 当某些关键词出现在 Twitter 搜索结果中时，你将收到通知
- 主动搜索工作机会，在公司更新其招聘页面时接收通知，以及在求职网站中搜索关键词。
- 在 Bamboo HR 和其他求职平台上获取新的职位空缺通知
- 网站篡改监控
- 宝可梦卡复购追踪器 / 宝可梦 TCG 追踪器
- 监管科技 - 保持对监管变化的领先，确保合规

_需要支持 JavaScript 的 Chrome 运行器吗？我们支持通过 WebDriver 和 Playwright 进行抓取！_

#### 主要功能

[](https://github.com/dgtlmoon/changedetection.io#key-features)

- 支持多种触发过滤器，如“文本触发”，“通过选择器移除文本”，“忽略文本”，“提取文本”，还可以使用正则表达式！
- 使用 xPath 1 和 xPath 2 选择目标元素，使用 CSS 选择器，轻松使用 JSONPath 或 jq 监控复杂 JSON 数据
- 切换使用快速非 JS 和基于 Chrome 的 JS "fetchers"
- 跟踪 PDF 文件的变化（监控 PDF 中的文本更改，同时监控 PDF 文件大小和校验和）
- 轻松指定检查站点的频率
- 在提取文本前执行 JS（适用于登录操作，UI 中提供示例！）
- 覆盖请求头，指定 `POST` 或 `GET` 及其他方法
- 使用“视觉选择器”来帮助定位特定元素
- 可配置的[监控代理](https://github.com/dgtlmoon/changedetection.io/wiki/Proxy-configuration)
- 检测到网页发生变化时，随通知发送截图

我们推荐并使用 Bright Data 的全球代理服务。通过我们的注册链接，Bright Data 将为您匹配最高 150 美元的首次存款。

请为这个项目点个 ⭐ 星 ⭐ ，帮助它成长！[https://github.com/dgtlmoon/changedetection.io/](https://github.com/dgtlmoon/changedetection.io/)

### 条件网页变更

[](https://github.com/dgtlmoon/changedetection.io#conditional-web-page-changes)

轻松配置条件动作，例如，仅在价格高于或低于预设金额时触发，或当网页包含（或不包含）某个关键词时触发。

[![Conditional web page changes](https://cdn.jsdelivr.net/gh/otxtdb/txtdb@master/_txtdbpic/c239c65a0adc8579ef7c624340dc0576_MD5.png)](https://github.com/dgtlmoon/changedetection.io/blob/master/docs/web-page-change-conditions.png)

### 在任何时区安排网页监控，在每周的特定日子和特定时间限制监控。

[](https://github.com/dgtlmoon/changedetection.io#schedule-web-page-watches-in-any-timezone-limit-by-day-of-week-and-time)

轻松设置重新检查的时间表，例如，您可以将网页变更检测限制在工作时间内运行。或者，根据时区（例如，您希望在上午9点检查某个外国国家的最新新闻头条）。

[![How to monitor web page changes according to a schedule](https://cdn.jsdelivr.net/gh/otxtdb/txtdb@master/_txtdbpic/f7b834852b62a60e940d647304c5d33a_MD5.png)](https://github.com/dgtlmoon/changedetection.io/blob/master/docs/scheduler.png)

包含仅在工作时间或周末设置定时任务的快捷按钮。

### 我们有一个 Chrome 扩展！

[](https://github.com/dgtlmoon/changedetection.io#we-have-a-chrome-extension)

只需安装扩展，点击“同步”即可将其与您现有的 changedetection.io 安装连接起来，轻松将当前网页添加到 changedetection.io 工具中。

[![Chrome Extension to easily add the current web-page to detect a change.](https://cdn.jsdelivr.net/gh/otxtdb/txtdb@master/_txtdbpic/58422e28a2cf5ad1624c4625824eafc1_MD5.png)](https://chromewebstore.google.com/detail/changedetectionio-website/kefcfmgmlhmankjmnbijimhofdjekbop)

[前往 Chrome 网上应用店下载扩展程序。](https://chromewebstore.google.com/detail/changedetectionio-website/kefcfmgmlhmankjmnbijimhofdjekbop)（ 或访问 [GitHub 仓库](https://github.com/dgtlmoon/changedetection.io-browser-extension) ）

## 安装

[](https://github.com/dgtlmoon/changedetection.io#installation)

### Docker

[](https://github.com/dgtlmoon/changedetection.io#docker)

使用 Docker Compose，只需克隆此仓库并...

```shell
$ docker compose up -d
```

Docker 独立运行

```shell
$ docker run -d --restart always -p "127.0.0.1:5000:5000" -v datastore-volume:/datastore --name changedetection.io dgtlmoon/changedetection.io
```

`:latest` 标签是我们最新的稳定版本，`:dev` 标签是我们的尖端 `master` 分支。

替代的 Docker 仓库可以在 ghcr 中找到 - [ghcr.io/dgtlmoon/changedetection.io](https://ghcr.io/dgtlmoon/changedetection.io)

### Windows

[](https://github.com/dgtlmoon/changedetection.io#windows)

请参阅维基上的安装说明 [https://github.com/dgtlmoon/changedetection.io/wiki/Microsoft-Windows](https://github.com/dgtlmoon/changedetection.io/wiki/Microsoft-Windows)

### Python Pip

[](https://github.com/dgtlmoon/changedetection.io#python-pip)

查看我们的 pypi 页面 [https://pypi.org/project/changedetection.io/](https://pypi.org/project/changedetection.io/)

```shell
$ pip3 install changedetection.io
$ changedetection.io -d /path/to/empty/data/dir -p 5000
```

然后访问 [http://127.0.0.1:5000](http://127.0.0.1:5000/) ，您现在应该能够访问 UI。

_现在每个站点都可以配置使用快速内置 HTTP 获取器，或者使用基于 Chrome 的获取器来监控 JavaScript 网站！_

## 更新 changedetection.io

[](https://github.com/dgtlmoon/changedetection.io#updating-changedetectionio)

### Docker

[](https://github.com/dgtlmoon/changedetection.io#docker-1)

```
docker pull dgtlmoon/changedetection.io
docker kill $(docker ps -a -f name=changedetection.io -q)
docker rm $(docker ps -a -f name=changedetection.io -q)
docker run -d --restart always -p "127.0.0.1:5000:5000" -v datastore-volume:/datastore --name changedetection.io dgtlmoon/changedetection.io
```

### docker compose

[](https://github.com/dgtlmoon/changedetection.io#docker-compose)

```shell
docker compose pull && docker compose up -d
```

查看维基以获取更多信息 [https://github.com/dgtlmoon/changedetection.io/wiki](https://github.com/dgtlmoon/changedetection.io/wiki)

## 过滤器

[](https://github.com/dgtlmoon/changedetection.io#filters)

XPath(1.0), JSONPath, jq 和 CSS 支持已内置！您可以根据需要进行详细设置，并使用各种 XPath 元素查询创建工具导出的 XPath。我们支持 LXML 的 ``re:test``、``re:match`` 和 ``re:replace``。

## 通知设置

[](https://github.com/dgtlmoon/changedetection.io#notifications)

ChangeDetection.io 通过 [apprise](https://github.com/caronc/apprise) 库在检测到网页变更时支持大量通知（包括电子邮件、Office365、自定义 API 等）。只需在“编辑”标签页中设置一个或多个通知 URL。

仅作一些示例

```
discord://webhook_id/webhook_token
flock://app_token/g:channel_id
gitter://token/room
gchat://workspace/key/token
msteams://TokenA/TokenB/TokenC/
o365://TenantID:AccountEmail/ClientID/ClientSecret/TargetEmail
rocket://user:password@hostname/#Channel
mailto://user:pass@example.com?to=receivingAddress@example.com
json://someserver.com/custom-api
syslog://
```

[以及这份列表中的其他所有内容！](https://github.com/caronc/apprise#popular-notification-services)

[![Self-hosted web page change monitoring notifications](https://cdn.jsdelivr.net/gh/otxtdb/txtdb@master/_txtdbpic/38700b6296a8feb0fe494a687f170aad_MD5.png)](https://raw.githubusercontent.com/dgtlmoon/changedetection.io/master/docs/screenshot-notifications.png)

现在您还可以自定义通知内容，并使用 [Jinja2 模板](https://jinja.palletsprojects.com/en/3.0.x/templates/)来设置标题和正文！

## JSON API �监控

[](https://github.com/dgtlmoon/changedetection.io#json-api-monitoring)

使用 JSONPath 或 jq 来过滤、解析和重新结构化 JSON 以检测变化和监控 JSON API 中的数据。

[![image](https://cdn.jsdelivr.net/gh/otxtdb/txtdb@master/_txtdbpic/355decb73e1631e045d5050bc420a98c_MD5.png)](https://raw.githubusercontent.com/dgtlmoon/changedetection.io/master/docs/json-filter-field-example.png)

这将重新解析 JSON 并对其格式进行调整，使监控和检测 JSON API 结果的变化变得极其简单

[![image](https://cdn.jsdelivr.net/gh/otxtdb/txtdb@master/_txtdbpic/a4b5ee91dd1d66f89450f1eff39d7c0b_MD5.png)](https://raw.githubusercontent.com/dgtlmoon/changedetection.io/master/docs/json-diff-example.png)

### JSONPath 或 jq？

[](https://github.com/dgtlmoon/changedetection.io#jsonpath-or-jq)

对于更复杂的 JSON 数据解析、过滤和修改，推荐使用 jq，因为它内置了操作符和函数。请参阅[文档](https://stedolan.github.io/jq/manual/)以获取更多关于 jq 的详细信息。

jq 的一大优势是你可以使用逻辑来过滤 JSON 数据，例如只显示值大于/小于等条件的项。

请参阅维基 [https://github.com/dgtlmoon/changedetection.io/wiki/JSON-Selector-Filter-help](https://github.com/dgtlmoon/changedetection.io/wiki/JSON-Selector-Filter-help) 以获取更多信息和示例

### 解析嵌入在 HTML 中的 JSON！

[](https://github.com/dgtlmoon/changedetection.io#parse-json-embedded-in-html)

启用 ``json:`` 或 ``jq:`` 过滤器后，你甚至可以自动提取并解析 HTML 页面中的嵌入 JSON！这非常适合基于 JSON 构建内容的网站，比如许多电商平台。

```
<html>
...
<script type="application/ld+json">

{
   "@context":"http://schema.org/",
   "@type":"Product",
   "offers":{
      "@type":"Offer",
      "availability":"http://schema.org/InStock",
      "price":"3949.99",
      "priceCurrency":"USD",
      "url":"https://www.newegg.com/p/3D5-000D-001T1"
   },
   "description":"Cobratype King Cobra Hero Desktop Gaming PC",
   "name":"Cobratype King Cobra Hero Desktop Gaming PC",
   "sku":"3D5-000D-001T1",
   "itemCondition":"NewCondition"
}
</script>
```

`json:$..price` 或 `jq:..price` 可以提取 `3949.99`，或者你可以提取整个结构（可以使用 JSONpath 测试网站进行验证）

该应用程序还支持自动通知您它可以自动跟踪这些信息

## 代理配置

[](https://github.com/dgtlmoon/changedetection.io#proxy-configuration)

请参阅维基 [https://github.com/dgtlmoon/changedetection.io/wiki/Proxy-configuration](https://github.com/dgtlmoon/changedetection.io/wiki/Proxy-configuration)，我们还支持在可能的情况下使用 [Bright Data 代理服务](https://github.com/dgtlmoon/changedetection.io/wiki/Proxy-configuration#brightdata-proxy-support) 和 [Oxylabs 代理服务](https://oxylabs.go2cloud.org/SH2d) 。

## 支持树莓派吗？

[](https://github.com/dgtlmoon/changedetection.io#raspberry-pi-support)

支持树莓派和 Linux/arm/v6、Linux/arm/v7、arm64 设备！请参阅维基 [以获取详细信息](https://github.com/dgtlmoon/changedetection.io/wiki/Fetching-pages-with-WebDriver)

## Import support  

[](https://github.com/dgtlmoon/changedetection.io#import-support)

Easily [import your list of websites to watch for changes in Excel .xslx file format](https://changedetection.io/tutorial/how-import-your-website-change-detection-lists-excel), or paste in lists of website URLs as plaintext.  

Excel import is recommended - that way you can better organise tags/groups of websites and other features.  

## API 支持

[](https://github.com/dgtlmoon/changedetection.io#api-support)

支持通过我们的 API 管理监控的网站列表 [via our API](https://changedetection.io/docs/api_v1/index.html)

## 支持我们

[](https://github.com/dgtlmoon/changedetection.io#support-us)

你使用 changedetection.io 赚钱了吗？它是否帮你节省了时间和金钱？它是否让你的生活更轻松，更不那么压力山大？请记住，我们编写这款软件的时候本可以去做实际的有偿工作，我们同样需要买食物和支付房租，就像你一样。

考虑订阅一个官方支持的 [网站变更检测订阅](https://changedetection.io/?src=github) ，即使你目前不使用它，你仍然会因为帮助项目而感到温暖和愉快。（谁知道呢，你可能真的会用到它！）

## 商业支持

[](https://github.com/dgtlmoon/changedetection.io#commercial-support)

我提供商业支持，这款软件被网络安全、航空航天、数据科学和数据记者等专业人士依赖，如果你有任何咨询需求，请联系 [dgtlmoon@gmail.com](mailto:dgtlmoon@gmail.com)，我很乐意与你的组织合作，进一步探索 changedetection.io 的可能性。

## 商业授权

[](https://github.com/dgtlmoon/changedetection.io#commercial-licencing)

如果您将此软件部分或全部作为任何商业安排的一部分进行销售，您必须遵守我们在代码仓库中找到的 COMMERCIAL_LICENCE.md，敬请联系 [dgtlmoon@gmail.com](mailto:dgtlmoon@gmail.com) 和 [contact@changedetection.io](mailto:contact@changedetection.io) 。

## 第三方授权

[](https://github.com/dgtlmoon/changedetection.io#third-party-licenses)

changedetectionio.html_tools.elementpath_tostring: 版权所有 (c) 2018-2021，SISSA（国际高级研究大学），授权使用 [MIT 许可证](https://github.com/sissaschool/elementpath/blob/master/LICENSE)


# 从外部文件添加表头


(0.43+) 可以从文本文件中为每个请求使用额外的标头

这些文本文件与您的主要数据存储目录相关联

以下所有选项均适用于纯文本、Playwright/Browserless，可能还包括 selenium（未测试）

到目前为止，标头的文本文件是一个简单的纯文本文件，如果您使用 Docker，可以通过 `-v` 命令将此文件挂载到容器中 `-v /local/path/headers.txt:/datastore/headers.txt`

```
My-header: some value
Another-header: another-value
```

### 全球范围内的监控

[](https://github.com/dgtlmoon/changedetection.io/wiki/Adding-headers-from-an-external-file#global-for-all-watches)

`/datastore/headers.txt`

### 在一个单一的监视中

[](https://github.com/dgtlmoon/changedetection.io/wiki/Adding-headers-from-an-external-file#on-a-single-watch)

`/datastore/d4e929f1-d467-491f-94e9-139537b9bd91/headers.txt`

在页面的 UI 中的**编辑**中可以查看到的 `url-wwatch.json` 文件（或从 文件中）

### 对于任何标签

[](https://github.com/dgtlmoon/changedetection.io/wiki/Adding-headers-from-an-external-file#for-any-group-tag)

如果您的标签是类似 ``Favorite`` 的形式，则

`/datastore/headers-favourite.txt`


# API 参考

# Changedetection.io API

[](https://github.com/dgtlmoon/changedetection.io/wiki/API-Reference#changedetectionio-api)

使用我们的 RESTful API 从其他系统驱动 changedetection.io。

在`设置`  > `API` 中找到为您生成的 API 密钥

![](https://cdn.jsdelivr.net/gh/otxtdb/txtdb@master/_txtdbpic/09723afee253623c91a9d7d2e445f8e1_MD5.png)

如果启用，请始终包含 `x-api-key` 头部值，从全局设置页面复制/粘贴密钥

所有 API 文档现在可在 [https://changedetection.io/docs/api_v1/index.html](https://changedetection.io/docs/api_v1/index.html) 获取



# 浏览器步骤


从版本 `0.40.0`（以及当前的 `dev` 版本）开始，可以设置“ **浏览器步骤** ”，这是一种执行操作的方法（例如点击接受 cookies 的框，或登录网站）

这会在视觉选择器运行之前执行，以准备进行变更检测的步骤

![Browser Steps for login, cookie accept, etc](https://cdn.jsdelivr.net/gh/otxtdb/txtdb@master/_txtdbpic/ebc90beae1269332b7ea761a02743808_MD5.gif)

第一步加载可能需要一些时间，因为需要启动浏览器的各种后台进程，所以请耐心等待 :)

每次检查网站时，这些步骤都会重新执行

它需要与 Playwright 连接，请参阅 [https://github.com/dgtlmoon/changedetection.io/wiki/Playwright-content-fetcher](https://github.com/dgtlmoon/changedetection.io/wiki/Playwright-content-fetcher)



# 社区监控列表


在这里您可以与社区分享您的监控列表。

# 技术

[](https://github.com/dgtlmoon/changedetection.io/wiki/Community-watch-list#technology)

|网站|添加日期|[共享链接](https://github.com/dgtlmoon/changedetection.io/wiki/Sharing-a-Watch)|评论|
|---|---|---|---|
|[Github 变化检测社区观察列表](https://github.com/dgtlmoon/changedetection.io/wiki/Community-watch-list)|2022-07-30|[github](https://changedetection.io/share/X6acmml4VZUa)|监控此页面新增内容|
|[OpenHAB 版本检查](https://www.openhab.org/download/)|2022-09-01|[OpenHAB](https://changedetection.io/share/s7pF37JSDSca)|检查最新稳定版 OpenHAB 的版本|
|[iOS 版本检查](https://support.apple.com/en-us/HT201222/)|2022-09-01|[iOS](https://changedetection.io/share/Uk7aoaRs3qEa)|最新 iOS 版本检查|
|[K8s 版本检查](https://github.com/kubernetes/kubernetes/releases)|2022-09-01|[Kubernetes](https://changedetection.io/share/IHMFvxBH0Gka)|最新 K8s 版本检查|
|[ASUS 主板固件版本检查](https://rog.asus.com/motherboards/rog-strix/rog-strix-x570-e-gaming-wifi-ii-model/helpdesk_bios/)|2022-09-01|[ASUS FW](https://changedetection.io/share/VObvUQZtKREa)|最新固件版本检查 - 请接受 cookies|
|[3D 打印机固件版本检查](https://github.com/knutwurst/Marlin-2-0-x-Anycubic-i3-MEGA-S/releases)|2022-09-01|[Knutwurst](https://changedetection.io/share/lwCdGTbRXFIa)|3D 打印机最新固件版本检查|
|[Unraid 稳定版发布](https://wiki.unraid.net/Manual/Release_Notes)|2022-09-01|[Unraid](https://changedetection.io/share/IJ_7hGWsnHMa)|最新稳定版 Unraid 软件的版本检查|
|[Amazon 商品库存](https://www.amazon.com/Lock-Classic-Airtight-Container-HPL889/dp/B001CMUOBK)|2022-09-01|[Amazon](https://changedetection.io/share/mabPR85EPAMa)|检查商品是否上架或下架|
|[检查 NUC 固件版本](https://www.intel.com/content/www/us/en/download/16873)|2022-09-01|[Intel](https://changedetection.io/share/xoAaEY1940Ia)|检查最新 NUC 固件版本|

# 游戏

[](https://github.com/dgtlmoon/changedetection.io/wiki/Community-watch-list#gaming)

|站点|添加日期|[共享链接](https://github.com/dgtlmoon/changedetection.io/wiki/Sharing-a-Watch)|评论|
|---|---|---|---|
|[Epic](https://store.epicgames.com/en-US/free-games)|2022-07-30|[epic games](https://changedetection.io/share/6zVK-ip6Kc0a)|免费监控 epicgames.com 的游戏|
|[Path of Exile 官方公告](https://www.pathofexile.com/forum/view-forum/news)|2022-08-28|[https://changedetection.io/share/ApXNQuwRJqwa](https://changedetection.io/share/ApXNQuwRJqwa)|监控 Path of Exile 开发者在论坛上的官方公告。通过帖子标题的 css 类进行过滤。|
|[最终幻想 XIV 官方公告（NA）](https://na.finalfantasyxiv.com/lodestone/topics/)|2022-08-28|[https://changedetection.io/share/J0evuN4GzuIa](https://changedetection.io/share/J0evuN4GzuIa)|监控来自《最终幻想 XIV》开发者的官方公告。通过过滤帖子标题的 CSS 类，并使用伪造的 User Agent 来避免浏览器兼容性警告。通过将 URL 中的 NA 更改为所需的地区，应该可以适用于其他地区。|




# 可配置的 BASE_URL 设置



The BASE_URL 设置目前用于发送通知时，您可以使用 `{base_url}` 占位符来自定义通知内容。

初始设置 `BASE_URL` 可以在您的环境变量中进行配置

`export BASE_URL=https://mysite.com:5000`

或者从您的 `docker-compose.yml` 脚本中进行配置。

您还可以在设置页面中覆盖 `BASE_URL` 设置。

**注意**：`BASE_URL` 设置与在 changedetection.io 安装中设置正确的域名/路径基础链接无关，这应通过反向代理来处理，请参见 [https://github.com/dgtlmoon/changedetection.io/wiki/Running-changedetection.io-behind-a-reverse-proxy](https://github.com/dgtlmoon/changedetection.io/wiki/Running-changedetection.io-behind-a-reverse-proxy)

然而，如果未设置 BASE_URL，RSS 将使用默认 web 服务器的路径来构建链接的 RSS 索引

别忘了包含 ``:port`` 号



# CSS 选择器帮助


什么是 CSS 选择器？请阅读 [https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors)

在 CSS 选择器过滤器字段中，您需要输入 **CSS 选择器** - 而不是 HTML

例如，如果 HTML 是

```html
<div class="points">
  <span id="interesting">
  57 points
  </span>
</div>
```

那么选择器就是 `.points #interesting`

在这个例子中

```html
<span class="chapter lastchapter">
  Chapter 53
</span>
```

这三个选择器将匹配 `.chapter`, `.lastchapter`, `.chapter.lastchapter`。最后一个只会匹配当两个 CSS 类都匹配时。 `.chapter lastchapter` 在这种情况下是错误的。

# 使用 xpath 从 ``<A>`` 标签中选择/提取 just the HREF。

[](https://github.com/dgtlmoon/changedetection.io/wiki/CSS-Selector-help#selectextract-just-the-href-from-a-tag-using-xpath)

如果需要

```
<h3>
  <a href..></a>
</h3>
```

filter: ``//h3/parent::a//@href``

# 仅使用 XPath 过滤器选择所有 img "src"标签

[](https://github.com/dgtlmoon/changedetection.io/wiki/CSS-Selector-help#select-all-img-src-tag-only-with-xpath-filter)

```
//img//@src
```

# 仅选择某事物的第一个实例

[](https://github.com/dgtlmoon/changedetection.io/wiki/CSS-Selector-help#select-just-the-first-instance-of-something)

```
xpath:(//h3[contains(@class, 'PagePromo-title')])[1]
```

这只会选择包含类 PagePromo-title 的第一个 h3 元素

# 通过 data- 属性选择

[](https://github.com/dgtlmoon/changedetection.io/wiki/CSS-Selector-help#select-by-data--source)

```
<div data-test-id="productSizeList"...
```

`//div[@data-test-id = 'productSizeList']`

# xPath 和非拉丁文本出现乱码

[](https://github.com/dgtlmoon/changedetection.io/wiki/CSS-Selector-help#xpath-and-non-latin-text-getting-garbled)

xPath: 类型过滤器和非 UTF-8 不兼容，如果你看到文本出现乱码，例如 “Нема планираних искључења.” 变成了 `Ð�ÐµÐ¼Ð° Ð¿Ð»Ð°Ð½Ð¸Ñ�Ð°Ð½Ð¸Ñ Ð¸Ñ�ÐºÑ�Ñ�Ñ�ÐµÑ�Ð°.` ，你应该将 xPath 过滤器转换为 CSS [https://extendsclass.com/xpath-to-css.html](https://extendsclass.com/xpath-to-css.html)

例如 [#1546](https://github.com/dgtlmoon/changedetection.io/issues/1546)




# 检测 HTML 页面源代码中的更改


对于一些网页，相关信息最好通过检查 HTML 页面源代码来获取。

## 使用案例

[](https://github.com/dgtlmoon/changedetection.io/wiki/Detecting-changes-in-HTML-page-sources#use-case)

例如，类似于的网上商店的 HTML 响应包含以 JSON 格式的产品列表，然后由客户端的 JS 处理以生成最终的标记。可以使用启用了 JS 的来处理此类网页，但检查页面源代码会更高效。

## 方法

[](https://github.com/dgtlmoon/changedetection.io/wiki/Detecting-changes-in-HTML-page-sources#approach)

- 在常规选项卡中，在目标 URL 前添加 ``source:``（示例： `source:https://www.campuspoint.de/mobile/notebooks/lenovo/thinkpad-t-serie/thinkpad-t14s.html` ）
- 在请求选项卡中，选择“基本快速纯文本/HTTP 客户端”获取方法

更多内容请参见 [https://changedetection.io/tutorial/source-code-monitor-how-get-alerts-changes-html-source-code](https://changedetection.io/tutorial/source-code-monitor-how-get-alerts-changes-html-source-code)




# 检测图像变化


有时一个监控项仅包含含一张图片。

当时，， detection.io 仅支持监控网页 _文本_ 的变化，但你也可以在 URL 中使用 `source:` 关键字来告诉 detection.io 监控 HTML。

这意味着你可以使用 detection.io 来监控当 HTML 变为包含一张图片。

例如，假设 现在显示一张图片。

```
<HTML>
<BODY>
   <div id="wrapper">
      <img src="november-calendar.jpg">
   </div>
   <div id="other stuff">
     our new calendar!
    </div>
</BODY>
</HTML>
```

然后在**视觉选择器**中选择了“wrapper”元素

### 如何检测图片变化？

[](https://github.com/dgtlmoon/changedetection.io/wiki/Detecting-changes-in-images#how-to-detect-when-the-image-changes)

使用 **`source:`** luke...

通过在 URL 开头添加"`source:`" - `source:https://the-site-you-are-watching.com` 并设置 CSS/xPath 过滤器（在**视觉选择器**工具中创建），当网站将图片"`november-calendar.jpg`"更改为"`december-calendar.jpg`"时，你将收到通知

自从0.45.3版本以来，我们尝试添加一条消息来帮助识别这种情况

除了消息 `Got HTML content but no text found (With 200 reply code),` （因为只有一张图片），如果你指定了过滤器/选择器，它会尝试通过说“ `Got HTML content but no text found (With 200 reply code), it's possible that the filters you have give an empty result or contain only an image.` ”来帮助你



# 开发者理念


我的目标是保持技术栈相对“扁平”，我希望人们能够提交有意义的更改，而不希望仅限于那些只了解 Vue/React/Angular/其他框架的人。我觉得唯一非常适合的框架是 Flask Python 框架。

截至 2022 年的互联网充斥着难以深入学习的领域特定框架，即便如此，也没有人愿意为这些代码库做贡献，它们通常都不易维护，而且除了 VueJS 及其类似框架外，一般会限制谁能够为代码库做贡献。

虽然将来我同意在前端绝对使用 VueJS 或类似框架会更加合理，但目前 JavaScript 的需求相对简单，目前还是手工完成更好。

另一个例外是使用 SASS 预处理器来节省编写大量 CSS 时的脑力，然而 Node 的世界仍然有很多不足之处，我已经尽可能详细地记录了 Node 版本和重建主题的步骤。

在讨论存储（`store.py`）方面，我确实认为这有点疯狂，但另一方面，它工作得非常好。不过，如果我真的发现一种不错的非 SQL 方式来存储这些数据，且不会导致大量领域特定的集成代码，我肯定是支持的。




# 使用 WebDriver 获取页面



许多现代网页使用 JavaScript 来填充内容，它们更加动态，有时需要真正的 Chrome 浏览器来获取内容，尽管许多页面可能使用我们内置的'fetcher'也能工作

后端可以配置为通过 ChromeDriver（内置的 WebDriver 网络接口）获取页面内容，这主要用于那些使用 JavaScript 渲染页面内容的页面（基本的 fetcher 不会执行任何 JS！）。启用它的最简单方法是在本地的 [docker-compose.yml](https://www.selenium.dev/documentation/webdriver/) 中取消注释以下内容并重启 docker-compose。

**注意：**RaspberryPi 需要不同的 selenium/webdriver 运行器，请编辑你的 `docker-compose.yml` 并使用推荐的 RaspberryPi 镜像`` 更多信息请参阅此处 - 使用 `seleniarm/standalone-chromium:4.0.0-20211213` 而不是 `selenium/standalone-chrome-debug:3.141.59` ``

```
    browser-chrome:
        hostname: browser-chrome
        image: selenium/standalone-chrome-debug:3.141.59
        volumes:
            # Workaround to avoid the browser crashing inside a docker container
            # See https://github.com/SeleniumHQ/docker-selenium#quick-start
            - /dev/shm:/dev/shm
        restart: unless-stopped
```

如果使用 docker（而不是 docker-compose），以下命令将启动 ChangeDetection.io 和 chromium WebDriver：

```
docker run -d \
  --name selenium \
  --restart unless-stopped \
  -p 4444:4444 \
  --shm-size="2g" \
  selenium/standalone-chrome-debug:3.141.59

docker run -d \
  --name changedetectionio \
  --restart unless-stopped \
  --link selenium \
  -p 5000:5000 \
  -e WEBDRIVER_URL="http://selenium:4444/wd/hub" \
  -v datastore-volume:/datastore \
  dgtlmoon/changedetection.io

```

然后访问 `/settings` 和 `[Fetching]` 选项卡并启用 WebDriver/Chrome 选项

![image](https://user-images.githubusercontent.com/275001/160246012-a9e886fd-d1ff-4038-9598-231cebb5d930.png)

WebDriver 接口的 URL 由 `WEBDRIVER_URL` 环境变量设置（默认为 `http://browser-chrome:4444/wd/hub` ）

### Raspberry Pi 注意事项

[](https://github.com/dgtlmoon/changedetection.io/wiki/Fetching-pages-with-WebDriver#raspberry-pi-notes)

已知在 RaspberryPi-4 上可用，请使用 `seleniarm/standalone-chromium:4.0.0-20211213` 作为 `image:`。请注意，目前仅支持 Raspbian OS 的 64 位版本。

- 将环境变量 `FETCH_WORKERS` 设置为较低的值，比如 2 或 3 是个不错的选择，因为同时开启 10 个 Chrome 会话可能会对你的树莓派（rPi）造成不小的负担

# Microsoft Windows - 使用 ChromeDriver（无需 Docker）

[](https://github.com/dgtlmoon/changedetection.io/wiki/Fetching-pages-with-WebDriver#microsoft-windows---running-chromedriver-natively-without-docker)

你需要安装 WebDriver/ChromeDriver，它会“监听”来自 changedetection.py 的指令，并驱动浏览器获取结果。

此方法最适合在使用 python/pip 安装软件时使用 [https://github.com/dgtlmoon/changedetection.io/wiki/Microsoft-Windows#method-1-with-python-pip-install](https://github.com/dgtlmoon/changedetection.io/wiki/Microsoft-Windows#method-1-with-python-pip-install) - 请有人添加基于 docker-compose 安装的说明 :)

测试使用的是 Chrome 版本 99.0

1. 安装 Chrome 网页浏览器 [https://www.google.com/chrome/](https://www.google.com/chrome/)
2. 安装与您安装的 Chrome 版本相匹配的正确 Chromium WebDriver [https://chromedriver.chromium.org/downloads](https://chromedriver.chromium.org/downloads)。
3. 解压并运行 WebDriver，这将与 Chrome 通信以获取结果![image](https://user-images.githubusercontent.com/275001/160232808-9796464b-197d-4b09-8e31-61c43ab618da.png)
4. 在系统范围或`cmd`级别设置环境变量，让 Changedetection.io 知道在哪里找到 ChromeDriver，从命令行启动 `set WEBDRIVER_URL=http://localhost:9515`
5. 在同一窗口中运行应用，使用`changedetection.py` ![image](https://user-images.githubusercontent.com/275001/160232891-51c69279-8e2e-40d7-a0ef-56f495cf2bdf.png) 
6. 别忘了为那些需要 JavaScript 的站点启用 Chrome 抓取，或者你希望通过 Chrome 抓取的任何站点，在用户界面中应该显示`"http://localhost:9515"`，如果你正确设置了环境变量。 ![image](https://user-images.githubusercontent.com/275001/160232926-70fee16f-634b-42cd-86c3-0ffaa5a0aa22.png) 

你不需要通过浏览器访问这个页面，这只是为了让你的 Changedetection 安装能够与 Chromedriver 通信。




# 处理被监控 URL 中的的变量


在第 1057 行，我们增加了在 URL 中使用 Jinja2 模板的可能性，使用 Jinja2 时间扩展，你可以指定一个日期（例如，根据你的时区当前的日期）或一个相对日期（例如，昨天的日期和一个月后的日期）。

非常适合需要在日期之间进行搜索的网站，例如。

有时你需要在请求的 URL 中插入当前日期，这可以通过使用 Jinja2 模板语法来实现，你也可以使用任何其他 Jinja2 语法（例如，如果今天是星期二，那么插入单词"foobar"或其他内容）

```
https://changedetection.io/test.txt?date={% now 'Europe/Berlin', '%d' %}.{% now 'Europe/Berlin', '%m' %}.{% now 'Europe/Berlin', '%Y' %}
```

根据`Europe/Berlin`时区

```
https://changedetection.io/test.txt?date=24.10.2022
```

接受的时间区列表 [https://en.wikipedia.org/wiki/List_of_tz_database_time_zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)

日期格式代码列表（如 %d 等）[https://docs.python.org/3/library/datetime.html#strftime-and-strptime-format-codes](https://docs.python.org/3/library/datetime.html#strftime-and-strptime-format-codes)





# iPadOS 安装说明（草稿）


版本: [https://github.com/dgtlmoon/changedetection.io/tree/0.39.22.1](https://github.com/dgtlmoon/changedetection.io/tree/0.39.22.1)

使用 iSH 在 iPad（iPadOS 16.1）上通过 PIP 安装。

构建失败，缺少多个依赖项：

1. 请确保已安装 libxml2 和 libxslt 开发包 ✅
    
2. 编译 cryptography（pyproject.toml）时出错 ✅ — 错误：找不到 Rust 编译器（此包需要 Rust >=1.41.0。）
    
3. cryptography 的附加错误 - 未成功运行。❌ │ 返回码：1 ╰─> [输出 160 行]
    

编译命令 '/usr/bin/gcc' 执行失败，返回码：1 [输出结束]

错误：编译 cryptography 失败 失败的项目中缺少 cryptography，无法构建基于 pyproject.toml 的项目

build/temp.linux-i686-cpython-310/_openssl.c:575:10: 严重错误：openssl/opensslv.h: 没有此文件或目录 575 | #include <openssl/opensslv.h> | ^~~~~~~~~~~~~~~~~~~~ 编译终止。

调试建议：• 确保已安装最新版本的 Rust 工具链：[https://cryptography.io/en/latest/installation.html#rust](https://cryptography.io/en/latest/installation.html#rust) • 如果您仅在此次发布中遇到 Rust 问题，可以设置环境变量 `CRYPTOGRAPHY_DONT_BUILD_RUST=1` 。

** 解决措施 ** 1: apk add libxslt-dev libxml2-dev ✅ 2: export CRYPTOGRAPHY_DONT_BUILD_RUST=1 ✅ 3: a) apk get python3-dev（不确定是否能解决问题） ❌ b) apk add rust ❌（大失败 - 导致 iSH 挂起）



