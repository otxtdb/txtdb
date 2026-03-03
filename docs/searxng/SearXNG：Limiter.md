---
title: "SearXNG：Limiter"
source: "https://docs.searxng.org/admin/searx.limiter.html"
author:
published:
created: 2026-03-01
description:
tags:
  - "clippings"
taxonomy: { doc_category: [searxng] }
---

info

Limiter 需要一个 [Valkey](https://docs.searxng.org/admin/settings/settings_valkey.html#settings-valkey) 数据库。

- [启用 Limiter](https://docs.searxng.org/admin/#enable-limiter)
- [配置 Limiter](https://docs.searxng.org/admin/#configure-limiter)
- [`limiter.toml`](https://docs.searxng.org/admin/#limiter-toml)
- [实现](https://docs.searxng.org/admin/#implementation)

机器人保护/IP 速率限制。速率限制的目的是限制来自某个 IP 的可疑请求。其背后的动机是 SearXNG 会转发来自机器人的请求，因此本身也被归类为机器人。结果，SearXNG 引擎会收到 CAPTCHA，或以其他方式被搜索引擎（源头）阻止。

为了避免被阻止，必须阻止机器人向 SearXNG 发送的请求，这就是 Limiter 的任务。为了执行这项任务，Limiter 使用来自 [机器人检测](https://docs.searxng.org/src/searx.botdetection.html#botdetection)的方法：

- 分析请求 / [探测 HTTP 头部](https://docs.searxng.org/src/searx.botdetection.html#botdetection-probe-headers) 中的 HTTP 头部 可以轻易绕过。
- 包含列出 IP 的阻止和传递列表 / [IP 列表](https://docs.searxng.org/src/searx.botdetection.html#botdetection-ip-lists) 难以维护，因为机器人的 IP 并非全部已知且会变化。 时间。
- 基于请求行为检测并动态限制机器人的速率。对于需要动态更改的 IP 列表，需要使用 Valkey 数据库。

基于 IP 的方法的前提是正确确定客户端的 IP 地址。客户端的 IP 地址通过 [X-Forwarded-For](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Forwarded-For) HTTP 头确定。

注意

正确设置 HTTP 请求头 `X-Forwarded-For` 和 `X-Real-IP` 对于正确地将请求分配给 IP 至关重要：

- [NGINX 请求头](https://docs.searxng.org/admin/installation-nginx.html#nginx-s-searxng-site)
- [Apache 请求头](https://docs.searxng.org/admin/installation-apache.html#apache-s-searxng-site)

## [启用限制器](https://docs.searxng.org/admin/#id3) [¶](https://docs.searxng.org/admin/#enable-limiter "Link to this heading")

要启用限制器，请激活：

server:
  ...
  limiter: true  \# rate limit the number of request on the instance, block some bots

并设置 valkey-url 连接。检查该值，它取决于你的 valkey 数据库（参见 [valkey:](https://docs.searxng.org/admin/settings/settings_valkey.html#settings-valkey)），例如：

valkey:
  url: valkey://localhost:6379/0

## [配置 Limiter](https://docs.searxng.org/admin/#id4)[¶](https://docs.searxng.org/admin/#configure-limiter "Link to this heading")

  
Limiter 使用的 [Bot Detection](https://docs.searxng.org/src/searx.botdetection.html#botdetection) 方法配置在本地文件 `/etc/searxng/limiter.toml` 中。默认值显示在 [limiter.toml](https://docs.searxng.org/admin/#limiter-toml) / 不要将所有值复制到本地配置中，只需通过覆盖默认值来启用所需选项。例如，要在 [Method ip\_limit](https://docs.searxng.org/src/searx.botdetection.html#botdetection-ip-limit) 中激活 `link_token` 方法，您只需将此选项设置为 true：

\[botdetection.ip\_limit\]
link\_token \= true

## [`limiter.toml`](https://docs.searxng.org/admin/#id5)[¶](https://docs.searxng.org/admin/#limiter-toml "Link to this heading")

在该文件中，limiter 查找 [Bot Detection](https://docs.searxng.org/src/searx.botdetection.html#botdetection) 的配置：

- [IP 列表](https://docs.searxng.org/src/searx.botdetection.html#botdetection-ip-lists)
- [速率限制](https://docs.searxng.org/src/searx.botdetection.html#botdetection-rate-limit)
- [探测 HTTP 头](https://docs.searxng.org/src/searx.botdetection.html#botdetection-probe-headers)

\[botdetection\]

\# The prefix defines the number of leading bits in an address that are compared
\# to determine whether or not an address is part of a (client) network.

ipv4\_prefix \= 32
ipv6\_prefix \= 48

\# If the request IP is in trusted\_proxies list, the client IP address is
\# extracted from the X-Forwarded-For and X-Real-IP headers. This should be
\# used if SearXNG is behind a reverse proxy or load balancer.

trusted\_proxies \= \[
  '127.0.0.0/8',
  '::1',
  \# '192.168.0.0/16',
  \# '172.16.0.0/12',
  \# '10.0.0.0/8',
  \# 'fd00::/8',
\]

\[botdetection.ip\_limit\]

\# To get unlimited access in a local network, by default link-local addresses
\# (networks) are not monitored by the ip\_limit
filter\_link\_local \= false

\# activate link\_token method in the ip\_limit method
link\_token \= false

\[botdetection.ip\_lists\]

\# In the limiter, the ip\_lists method has priority over all other methods -> if
\# an IP is in the pass\_ip list, it has unrestricted access and it is also not
\# checked if e.g. the "user agent" suggests a bot (e.g. curl).

block\_ip \= \[
  \# '93.184.216.34',  # IPv4 of example.org
  \# '257.1.1.1',      # invalid IP --> will be ignored, logged in ERROR class
\]

pass\_ip \= \[
  \# '192.168.0.0/16',      # IPv4 private network
  \# 'fe80::/10'            # IPv6 linklocal / wins over botdetection.ip\_limit.filter\_link\_local
\]

\# Activate passlist of (hardcoded) IPs from the SearXNG organization,
\# e.g. \`check.searx.space\`.
pass\_searxng\_org \= true

## [实现](https://docs.searxng.org/admin/#id6) [¶](https://docs.searxng.org/admin/#implementation "Link to this heading")

searx.limiter.LIMITER\_CFG\_SCHEMA *\= PosixPath('/home/runner/work/searxng/searxng/searx/limiter.toml')*[¶](https://docs.searxng.org/admin/#searx.limiter.LIMITER_CFG_SCHEMA "Link to this definition")

botdetection 的基础配置（架构）。

searx.limiter.get\_cfg() → [Config](https://docs.searxng.org/src/searx.botdetection.html#searx.botdetection.config.Config "searx.botdetection.config.Config")[\[source\]](https://docs.searxng.org/_modules/searx/limiter.html#get_cfg)[¶](https://docs.searxng.org/admin/#searx.limiter.get_cfg "Link to this definition")

返回 SearXNG 的全局限制器配置。

searx.limiter.pre\_request()[\[source\]](https://docs.searxng.org/_modules/searx/limiter.html#pre_request)[¶](https://docs.searxng.org/admin/#searx.limiter.pre_request "Link to this definition")

参见 [`flask.Flask.before_request`](https://flask.palletsprojects.com/en/stable/api/#flask.Flask.before_request "(in Flask v3.1.x)")

searx.limiter.is\_installed()[\[source\]](https://docs.searxng.org/_modules/searx/limiter.html#is_installed)[¶](https://docs.searxng.org/admin/#searx.limiter.is_installed "Link to this definition")

  
如果限流器处于活动状态且存在 valkey 数据库，则返回 `True`。

searx.limiter.initialize(*app: [Flask](https://flask.palletsprojects.com/en/stable/api/#flask.Flask "(in Flask v3.1.x)")*, *settings*)[\[source\]](https://docs.searxng.org/_modules/searx/limiter.html#initialize)[¶](https://docs.searxng.org/admin/#searx.limiter.initialize "Link to this definition")

安装 limiter