---
title: "可配置的 BASE_URL 设置"
source: "https://github.com/dgtlmoon/changedetection.io/wiki/Configurable-BASE_URL-setting"
author:
  - "[[GitHub]]"
published:
created: 2025-12-01
description: "Best and simplest tool for website change detection, web page monitoring, and website change alerts. Perfect for tracking content changes, price drops, restock alerts, and website defacement monitoring—all for free or enjoy our SaaS plan! - Configurable BASE_URL setting · dgtlmoon/changedetection.io Wiki"
tags:
  - "clippings"
---


  
BASE\_URL 设置目前用于发送通知，您可以使用 `{base_url}` 标记来定制通知正文。

  
`BASE_URL` 最初在你的环境变量中设置

`export BASE_URL=https://mysite.com:5000`

  
或者从你的 `docker-compose.yml` 配方中设置。

  
`BASE_URL` 设置也可以在设置页面中覆盖。

  
**注意** ：`BASE_URL` 设置与在 changedetection.io 安装中设置正确的域/路径基本链接无关，这应该通过反向代理处理，请参阅 [https://github.com/dgtlmoon/changedetection.io/wiki/Running-changedetection.io-behind-a-reverse-proxy](https://github.com/dgtlmoon/changedetection.io/wiki/Running-changedetection.io-behind-a-reverse-proxy)

  
但是，如果未设置 BASE\_URL，RSS 将使用默认的 web 服务器路径来构建链接的 RSS 索引

  
别忘了包含 `:port` 号码