---
title: "SearXNG：插件列表"
source: "https://docs.searxng.org/admin/plugins.html"
author:
published:
created: 2026-03-01
description:
tags:
  - "clippings"
taxonomy: { doc_category: [searxng] }
---

进一步阅读 ..

- [SearXNG 设置](https://docs.searxng.org/admin/settings/settings_plugins.html#settings-plugins)
- [插件开发](https://docs.searxng.org/dev/plugins/development.html#dev-plugin)

| 名称 | 激活 | 描述 |
| --- | --- | --- |
| 计算器 | 是 | 解析并求解数学表达式。 |
| 个人信息 | 是 | 如果查询是“ip”，则显示您的 IP 地址；如果查询是“user-agent”，则显示您的用户代理。 |
| 哈希插件 | 是 | 将字符串转换为不同的哈希摘要。可用函数：md5, sha1, sha224, sha256, sha384, sha512。 |
| 时区插件 | 是 | 显示不同时区的当前时间。 |
| Tor 检查插件 | 否 | 此插件检查请求地址是否为 Tor 出口节点，如果是，会通知用户；类似于 check.torproject.org，但来自 SearXNG。 |
| 单位转换插件 | 是 | 单位转换 |
| 无限滚动 | 不 | 滚动到当前页底部时自动加载下一页 |
| 开放获取 DOI 重写 | 不 | 避免通过重定向到可用的出版物开放获取版本来绕过付费墙 |
| 追踪器 URL 移除器 | 是 | 从返回的 URL 中移除追踪器参数 |