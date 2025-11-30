---
title: "Word 文档监视器"
source: "https://distill.io/docs/web-monitor/word-doc-monitor/"
author:
  - "[[Distill]]"
published: 2024-02-14
created: 2025-11-30
description: "Learn how to set up and troubleshoot Word Document monitors on Distill tracking changes in online Word docs with step-by-step instructions."
tags:
  - "clippings"
---
>   
> Word 文档监控目前仅在 Flexi 和 Enterprise 计划中提供。

###   
什么是 Word 文档监控？

  
Word 文档监控允许您跟踪托管在 URL 上的整个 Word 文档。这些 URL 通常以“.doc”或“.docx”结尾，表明文档的文件格式。它们通常出现在托管可下载内容的网站上，例如学术资源、电子书、通知、公司文件、法律表格等。

###   
如何设置 Word 文档监控？

1. 点击`添加监控 `，从列表中选择 `Word 文档 `。
![adding a word document monitor](https://distill.io/docs/web-monitor/word-doc-monitor/images/word-doc-monitor.jpg)

2. 在此处粘贴文档的 URL。这些通常以.doc 或.docx 结尾 *(您可以右键点击任何包含 word doc 的链接，复制链接地址并粘贴在此处)*

![adding the URL of a word document](https://distill.io/docs/web-monitor/word-doc-monitor/images/add-doc-url.jpg)

3. 点击“保存”。

###   
解决错误和故障排除步骤

  
如果解析 Word 文档时出现问题，您将遇到带有 `ERR_DOC_PARSE` 的错误消息。

![error parsing word doc](https://distill.io/docs/web-monitor/word-doc-monitor/images/err-doc-parse.jpg)

  
您可以点击`查看详情`获取有关错误的更多信息。当它遇到错误时，将显示文档 URL 的快照。

![error parsing word doc](https://distill.io/docs/web-monitor/word-doc-monitor/images/err-details.jpg)