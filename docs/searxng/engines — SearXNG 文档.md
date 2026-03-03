---
title: "engines: — SearXNG 文档"
source: "https://docs.searxng.org/admin/settings/settings_engines.html"
author:
published:
created: 2026-03-01
description:
tags:
  - "clippings"
taxonomy: { doc_category: [searxng] }
---
进一步阅读 ..

- [配置的引擎](https://docs.searxng.org/user/configured_engines.html#configured-engines)
- [引擎概述](https://docs.searxng.org/dev/engines/engine_overview.html#engines-dev)

在 `engines:` 部分中列出了实例中将提供的搜索引擎。每个列表项都是一个键/值映射。

engines:

  \- name: dummy.online
    engine: dummy
    ..
  \- name: dummy.offline
    engine: dummy-offline
    ..
  ..

  
在下面的代码示例中，展示了一个来自虚拟引擎的 YAML 设置的完整示例。大多数选项都有默认值，甚至有些是可选的。

提示

还有一些其他选项是可能的，但它们非常特定于某些引擎（ [Engine Implementations](https://docs.searxng.org/dev/engines/index.html#engine-implementations)）。

\- name: example
  engine: example
  shortcut: demo
  base\_url: 'https://{language}.example.com/'
  send\_accept\_language\_header: false
  categories: general
  timeout: 3.0
  api\_key: 'apikey'
  disabled: false
  language: en\_US
  tokens: \[ 'my-secret-token' \]
  weight: 1
  display\_error\_messages: true
  about:
     website: https://example.com
     wikidata\_id: Q306656
     official\_api\_documentation: https://example.com/api-doc
     use\_official\_api: true
     require\_api\_key: true
     results: HTML

  \# overwrite values from section 'outgoing:'
  enable\_http2: false
  retries: 1
  max\_connections: 100
  max\_keepalive\_connections: 10
  keepalive\_expiry: 5.0
  using\_tor\_proxy: false
  proxies:
    http:
      \- http://proxy1:8080
      \- http://proxy2:8080
    https:
      \- http://proxy1:8080
      \- http://proxy2:8080
      \- socks5://user:password@proxy3:1080
      \- socks5h://user:password@proxy4:1080

  \# other network settings
  enable\_http: false
  retry\_on\_http\_error: true \# or 403 or \[404, 429\]

`name` :

SearXNG 中用于定义此搜索引擎的名称。在设置中，在结果页面上…

`engine` :

用于处理与该搜索引擎的请求和响应的 Python 文件名称。

`shortcut ` :

用于执行感叹号请求的代码（在这种情况下使用 `!bi`）

`base_url` 可选

URL 的一部分，应该在每次请求中都保持稳定。可以用于多个站点使用同一个引擎，或者在更新站点 URL 时无需修改代码。

`send_accept_language_header` :

一些支持语言（或地区）的引擎处理 HTTP 头 `Accept-Language` 用于构建符合本地环境的响应。当此选项被激活时，用户选择的语言（本地环境）将用于构建并发送到原始搜索引擎的请求中的 `Accept-Language` 头部。

`categories` 可选

指定引擎应添加到哪些类别中。引擎可以被分配到多个类别。

类别可以在 UI 中显示为标签页（[categories\_as\_tabs:](https://docs.searxng.org/admin/settings/settings_categories_as_tabs.html#settings-categories-as-tabs)）。在标签页（在 UI 中）中的搜索将查询该标签页中所有激活的引擎。在偏好设置页面（ `/preferences`）—— 在 *engines* 下——用户可以选择在查询此标签页时应激活哪个引擎。

或者，可以使用 [!bang](https://docs.searxng.org/user/search-syntax.html#search-syntax) 来搜索某一类别下的所有搜索引擎，无论它们是否处于活动状态，或者是否在 UI 的标签页中。例如，可以使用 `!dictionaries` 来查询该类别（组）下的所有搜索引擎。

`timeout` 可选

  
当前搜索引擎的搜索超时时间。覆盖 来自 [outgoing:](https://docs.searxng.org/admin/settings/settings_outgoing.html#settings-outgoing) 的 request\_timeout。 **小心，这将修改 SearXNG 的全局超时时间。**

`api_key` 可选

在某些情况下，使用 API 需要使用一个密钥。如何获取它们 在文件中描述。需要 API 密钥的引擎设置为 `不活跃：  是 ` 为默认设置。要启用此类引擎，请提供 API 密钥并将 `  不活跃：  否  ` 设置为 不活跃： 否 。

`disabled`可选

默认禁用引擎，但不会删除它。这将允许用户在设置中手动激活它。

`inactive`: 可选

  
从设置中移除引擎（ *禁用并删除* ）。对于需要 API 密钥的引擎，默认值为 `true`，如果您想启用此类引擎，请参阅 `api_key` 部分。

`language` 可选

如果您想为特定引擎使用另一种语言，可以通过使用语言（和地区）的 ISO 代码来定义，例如 `fr`、`en-US`， `de-DE`.

`tokens` 可选

一个用于使此引擎 *私有* 的秘密令牌列表，更多详情请参阅 [私有引擎（令牌）](https://docs.searxng.org/admin/settings/#private-engines).

`weight` 默认 `1`

此引擎结果的权重。

`display_error_messages` 默认 `true`

当引擎返回错误时，消息会显示在用户界面上。

`network`可选

使用另一个引擎的网络配置。此外，还有两个默认网络：

- `IPv4` 将 `local_addresses` 设置为 `0.0.0.0`（仅使用 IPv4 本地地址）
- `ipv6` 设置 `local_addresses` 为 `::` (仅使用 IPv6 本地地址)

`enable_http` 可选

为该引擎启用 HTTP（默认情况下仅启用 HTTPS）。

`retry_on_http_error` 可选

在某些 HTTP 状态码上重试请求。

示例：

- `true` : 在 400 到 599 之间的 HTTP 状态码。
- `403` : 在 HTTP 状态码 403。
- `[403, 429]`: 在 HTTP 状态码 403 和 429 时。

`proxies` :

覆盖来自 [outgoing:](https://docs.searxng.org/admin/settings/settings_outgoing.html#settings-outgoing) 的代理设置。

`using_tor_proxy` :

  
为该引擎使用 tor 代理（`true`）或不使用（`false`）。默认值来自 [outgoing:](https://docs.searxng.org/admin/settings/settings_outgoing.html#settings-outgoing) 中的 using\_tor\_proxy。

`max_keepalive_connection#s` :

[池限制配置](https://www.python-httpx.org/advanced/#pool-limit-configuration) ，覆盖此引擎的 `pool_maxsize` 值。

[outgoing:](https://docs.searxng.org/admin/settings/settings_outgoing.html#settings-outgoing)。

`max_connections` :

[池限制配置](https://www.python-httpx.org/advanced/#pool-limit-configuration) ，覆盖此引擎的 `pool_connections` 值。 [出站：](https://docs.searxng.org/admin/settings/settings_outgoing.html#settings-outgoing) 对此引擎。

`keepalive_expiry` :

[池限制配置](https://www.python-httpx.org/advanced/#pool-limit-configuration) ，覆盖此引擎的 `keepalive_expiry` 值。 [出站：](https://docs.searxng.org/admin/settings/settings_outgoing.html#settings-outgoing) 对此引擎。

##   私有引擎（`tokens`）¶

管理员可能希望限制对其实例上某些已启用引擎的访问权限。这可能是因为他们不希望通过 [离线引擎](https://docs.searxng.org/dev/engines/index.html#offline-engines)暴露某些私有信息。或者他们更倾向于只与信任的朋友或同事共享引擎。

info

最初由[搜索与发现基金](https://nlnet.nl/discovery)的 [NLnet 基金会](https://nlnet.nl/)赞助。

为解决此问题，存在 *私有引擎* 的概念。

为引擎添加了一个名为 tokens 的新选项。它期望一个字符串列表。如果发起请求的用户提供了某个引擎的令牌之一，他们可以访问有关该引擎的信息并发起搜索请求。

限制对 Arch Linux Wiki 引擎访问的示例配置：

\- name: arch linux wiki
  engine: archlinux
  shortcut: al
  tokens: \[ 'my-secret-token' \]

除非用户配置了正确的令牌，否则引擎将对他们隐藏。它将不会出现在偏好设置页面的引擎列表中，也不会出现在 /config REST API 调用的输出中。

可以在“引擎令牌”下的“偏好设置”页面中向配置添加令牌。输入需要是一个用逗号分隔的字符串列表。

管理员向用户分配令牌的分配方式并非一成不变。由于提供对这类引擎的访问意味着管理员了解并信任用户，我们认为没有必要制定严格的流程。相反，我们希望在功能文档中添加一些指导方针。

##   示例：多语言搜索

SearXNG 不支持真正的多语言搜索。当你在不同语言中搜索时，你必须在搜索查询中使用语言前缀。

但有一个解决方法：通过添加一个不同语言的新搜索引擎，SearXNG 将搜索你的默认语言和其他语言。

德语和英语使用者的 settings.yml 中的示例配置：

search:
    default\_lang : "de"
    ...

engines:
  \- name : google english
    engine : google
    language : en
    ...

在搜索时，默认的 google 引擎会返回德语结果，而“google english”会返回英语结果。