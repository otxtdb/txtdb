---
title: "windingblack/obsidian-global-proxy: 🚀 Obsidian Global Proxy is an Obsidian plugin that makes it easy to configure web proxies and use proxies throughout Obsidian."
source: "https://github.com/windingblack/obsidian-global-proxy"
author:
published:
created: 2026-07-20
description: "🚀 Obsidian Global Proxy is an Obsidian plugin that makes it easy to configure web proxies and use proxies throughout Obsidian. - windingblack/obsidian-global-proxy"
tags:
  - "clippings"
taxonomy: { doc_category: [obsidian] }
---
## 全球代理服务

Global Proxy 是一款 Obsidian 插件，它能够简化网络代理的配置过程，让用户可以在整个 Obsidian 系统中轻松使用这些代理。目前，该插件支持的代理类型包括 Socks、HTTP 和 HTTPS。对于那些处于网络限制较严地区的用户来说，这款插件非常有用。

## 如何使用

- 请在输入框中填入相应的代理地址。如果所有代理地址都无效，那么所有请求都将直接发送，而不会经过代理服务器。如果同时设置了 SOCKS 代理和 HTTP/HTTPS 代理，那么系统会优先使用 SOCKS 代理；如果 SOCKS 代理无法使用，系统则会使用 HTTP/HTTPS 代理。如果 HTTP/HTTPS 代理也无法使用，那么请求将直接发送。
- 有一些插件会维持自己独立的网络连接，不会使用 Obsidian 的默认会话机制。因此，这些插件的网络流量不会被代理。不过，你可以为其中某个插件指定一个“插件令牌”，从而让该插件的网络流量被代理。
- 如果设置了黑名单，该插件将不会对列表中的 URL 使用代理服务器。旁路列表是由逗号分隔的规则列表。这些规则的详细说明请参见“黑名单”部分。

[![Setting Tab](https://github.com/windingblack/obsidian-global-proxy/raw/master/assets/SettingTab.png)](https://github.com/windingblack/obsidian-global-proxy/blob/master/assets/SettingTab.png)

### 插件令牌

以下是一些流行的 Obsidian 插件的示例。

| 回购协议 | 插件令牌 |
| --- | --- |
| [黑曜石冲浪](https://github.com/PKM-er/Obsidian-Surfing) | `persist:surfing-vault-${appId}` |
| [媒体扩展功能](https://github.com/PKM-er/media-extended) | `persist:mx-player-${appId}` |

### 黑名单

> `Bypass List` 实际上是由下面所描述的规则组成的、以逗号分隔的列表：
> 
> - `[ URL_SCHEME "://" ] HOSTNAME_PATTERN [ ":" <port> ]` 匹配所有符合 HOSTNAME\_PATTERN 模式的域名。例如：foobar.com、\*foobar.com、\*.foobar.com、\*foobar.com:99、https://x.\\\*.y.com:99
> - `"." HOSTNAME_SUFFIX_PATTERN [ ":" PORT ]` 匹配特定的域名后缀。例如：.google.com、.com、 [http://.google.com](http://.google.com/)
> - `[ SCHEME "://" ] IP_LITERAL [ ":" PORT ]` 匹配那些为 IP 地址形式的 URL。例如：127.0.1、\[0:0::1\]、\[::1\]、http://\[::1\]:99
> - `IP_LITERAL "/" PREFIX_LENGTH_IN_BITS` 匹配那些属于给定范围内的 IP 地址的 URL。IP 地址范围是用 CIDR 表示法来指定的。例如：192.168.1.1/16、ffe:13::abc/33。
> - `<local>` 匹配本地地址。 `<local>` 的含义是指该主机是否与以下地址之一相符：127.0.0.1、::1、localhost。