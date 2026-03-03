---
title: "SearXNG：Favicons"
source: "https://docs.searxng.org/admin/searx.favicons.html"
author:
published:
created: 2026-03-01
description:
tags:
  - "clippings"
taxonomy: { doc_category: [searxng] }
---

警告

在阅读文档之前不要激活 Favicons。

- [基础设施](https://docs.searxng.org/admin/#infrastructure)
- [设置缓存](https://docs.searxng.org/admin/#setting-up-the-cache)
	- [维护缓存](https://docs.searxng.org/admin/#maintenance-of-the-cache)
- [代理配置](https://docs.searxng.org/admin/#proxy-configuration)
	- [注册解析器](https://docs.searxng.org/admin/#register-resolvers)

在 SearXNG 中启用 favicon 非常简单，但这会**显著增加客户端/服务器通信的负载** ，并增加服务器所需的资源。

为了减轻这些缺点，已经实现了多种方法，包括一个 *缓存* 。缓存必须根据您的要求进行参数化，并定期维护。

  
要在 SearXNG 的结果列表中启用 favicon，请在[搜索](https://docs.searxng.org/admin/settings/settings_search.html#settings-search)设置中设置一个默认的 favicon\_resolver：

search:
  favicon\_resolver: "duckduckgo"

默认情况下，且没有任何扩展时，SearXNG 提供这些解析器：

- `duckduckgo`
- `allesedv`
- `google`
- `yandex`

在上述设置中，favicons 会显示，用户可以在设置中禁用此功能。如果用户需要从多个 *resolvers* 中选择，则需要进一步设置/但此设置将在本文 [后面](https://docs.searxng.org/admin/#register-resolvers)讨论，首先我们得设置 favicons 缓存。

## [基础设施](https://docs.searxng.org/admin/#id3) [¶](https://docs.searxng.org/admin/#infrastructure "Link to this heading")

提供 favicons 的基础设施基本上由三个部分组成：

- [`Favicons-代理 `](https://docs.searxng.org/src/searx.favicons.html#module-searx.favicons.proxy "searx.favicons.proxy") （又名*代理* ）
- [`Favicons-Resolvers`](https://docs.searxng.org/src/searx.favicons.html#module-searx.favicons.resolvers "searx.favicons.resolvers") (又名 *resolver*)
- [`Favicons-Cache`](https://docs.searxng.org/src/searx.favicons.html#module-searx.favicons.cache "searx.favicons.cache") (又名 *cache*)

为保护用户隐私，Favicons 通过一个 *代理* 提供。这 个 *代理* 会随着 *resolver* 的激活而自动启用。提供 Favicons 需要额外的请求：首先， *代理* 必须处理传入的请求，其次， *解析器*必须向外部源发起传出请求以获取 favicons。

已开发一个*缓存*以大幅减少传入和传出请求。该 *缓存*也会随着上述 *解析器*的激活而自动激活。然而，默认情况下，该*缓存*非常基础，不适合生产环境！

## [设置缓存](https://docs.searxng.org/admin/#id4) [¶](https://docs.searxng.org/admin/#setting-up-the-cache "Link to this heading")

为了参数化*缓存*和 favicons 基础设施的更多设置， [TOML](https://toml.io/en/) 配置是在文件 `/etc/searxng/favicons.toml` 中创建的。

\[favicons\]

cfg\_schema \= 1   \# config's schema version no.

\[favicons.cache\]

db\_url \= "/var/cache/searxng/faviconcache.db"  \# default: "/tmp/faviconcache.db"
LIMIT\_TOTAL\_BYTES \= 2147483648                 \# 2 GB / default: 50 MB
\# HOLD\_TIME = 5184000                            # 60 days / default: 30 days
\# BLOB\_MAX\_BYTES = 40960                         # 40 KB / default 20 KB
\# MAINTENANCE\_MODE = "off"                       # default: "auto"
\# MAINTENANCE\_PERIOD = 600                       # 10min / default: 1h

[`cfg_schema`](https://docs.searxng.org/src/searx.favicons.html#searx.favicons.config.FaviconConfig.cfg_schema "searx.favicons.config.FaviconConfig.cfg_schema"):

需要触发未来升级所需的任何进程，不要更改它。

[`cache.db_url`](https://docs.searxng.org/src/searx.favicons.html#searx.favicons.cache.FaviconCacheConfig.db_url "searx.favicons.cache.FaviconCacheConfig.db_url"):

  
SQLite 数据库文件的路径。默认路径位于 [/tmp](https://refspecs.linuxfoundation.org/FHS_3.0/fhs/ch03s18.html) 文件夹中，该文件夹在每次重启时都会被删除，因此不适合生产环境。FHS 规范为应用程序缓存提供了 [/var/cache](https://refspecs.linuxfoundation.org/FHS_3.0/fhs/index.html) 文件夹，因此 SearXNG 缓存的一个合适的存储位置是文件夹 `/var/cache/searxng`。

在标准安装（比较[创建用户](https://docs.searxng.org/admin/installation-searxng.html#create-searxng-user) ）中，必须创建该文件夹，并且运行 SearXNG 进程的用户必须对此文件夹有写权限。

$ sudo mkdir /var/cache/searxng
$ sudo chown root:searxng /var/cache/searxng/
$ sudo chmod g+w /var/cache/searxng/

在容器系统中，应该为此文件夹挂载一个卷。检查容器中的进程是否对挂载的文件夹有读写访问权限。

[`cache.LIMIT_TOTAL_BYTES`](https://docs.searxng.org/src/searx.favicons.html#searx.favicons.cache.FaviconCacheConfig.LIMIT_TOTAL_BYTES "searx.favicons.cache.FaviconCacheConfig.LIMIT_TOTAL_BYTES"):

所有 blob 在缓存中存储的最大字节数。该限制在每个维护间隔后才会达到，届时最旧的 BLOB 将被删除；在维护期间，该限制可能会被超过。

注意

如果维护期过长或完全关闭维护，缓存将无限制增长。

SearXNG 主机可以按需更改缓存的其它参数：

- [`cache.HOLD_TIME`](https://docs.searxng.org/src/searx.favicons.html#searx.favicons.cache.FaviconCacheConfig.HOLD_TIME "searx.favicons.cache.FaviconCacheConfig.HOLD_TIME")
- [`cache.BLOB_MAX_BYTES`](https://docs.searxng.org/src/searx.favicons.html#searx.favicons.cache.FaviconCacheConfig.BLOB_MAX_BYTES "searx.favicons.cache.FaviconCacheConfig.BLOB_MAX_BYTES")

### [维护缓存](https://docs.searxng.org/admin/#id5) [¶](https://docs.searxng.org/admin/#maintenance-of-the-cache "Link to this heading")

需要定期维护缓存！默认情况下，定期维护作为客户端请求的一部分自动触发：

- [`cache.MAINTENANCE_MODE`](https://docs.searxng.org/src/searx.favicons.html#searx.favicons.cache.FaviconCacheConfig.MAINTENANCE_MODE "searx.favicons.cache.FaviconCacheConfig.MAINTENANCE_MODE") (默认 `auto`)
- [`cache.MAINTENANCE_PERIOD`](https://docs.searxng.org/src/searx.favicons.html#searx.favicons.cache.FaviconCacheConfig.MAINTENANCE_PERIOD "searx.favicons.cache.FaviconCacheConfig.MAINTENANCE_PERIOD") (默认 `6000` / 1h)

作为客户端请求过程中维护的替代方案，也可以使用外部进程进行维护。例如，通过为维护创建一个 [crontab](https://manpages.debian.org/jump?q=crontab) 条目：

$ python \-m searx.favicons cache maintenance

以下命令可用于显示缓存状态：

$ python \-m searx.favicons cache state

## [代理配置](https://docs.searxng.org/admin/#id6) [¶](https://docs.searxng.org/admin/#proxy-configuration "Link to this heading")

大多数 [`Favicons-Proxy`](https://docs.searxng.org/src/searx.favicons.html#module-searx.favicons.proxy "searx.favicons.proxy") 的选项已经通过 [settings.yml](https://docs.searxng.org/admin/settings/index.html#searxng-settings-yml) 的设置合理配置，通常不需要调整。

\[favicons.proxy\]

max\_age \= 5184000             \# 60 days / default: 7 days (604800 sec)

[`max_age`](https://docs.searxng.org/src/searx.favicons.html#searx.favicons.proxy.FaviconProxyConfig.max_age "searx.favicons.proxy.FaviconProxyConfig.max_age"):

  
[HTTP Cache-Control max-age](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cache-Control#response_directives) 响应指令表示响应在生成后 N 秒内保持新鲜。因此，该设置决定了 favicon 在客户端缓存中保留的时间。通常情况下，在 SearXNG 的 favicon 基础设施中，此设置仅影响字节大小超过 [BLOB\_MAX\_BYTES](https://docs.searxng.org/admin/#favicon-cache-setup) 的 favicon（其他已缓存的 favicon 则嵌入为 [数据 URL](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/Data_URLs) 在[`生成  HTML`](https://docs.searxng.org/src/searx.favicons.html#searx.favicons.proxy.favicon_url "searx.favicons.proxy.favicon_url") 中，这可以大大减少额外的请求数量)。

### [注册解析器](https://docs.searxng.org/admin/#id7) [¶](https://docs.searxng.org/admin/#register-resolvers "Link to this heading")

一个 `  解析器  ` 是一个从外部源获取 favicons 的函数。用户可用的解析器函数以其完整限定名（ [完整限定名](https://en.wikipedia.org/wiki/Fully_qualified_name) ）在 `  解析器映射  ` 中注册。

如果没有在 `resolver_map` 中定义 `favicon.toml`，SearXNG 的 favicon 基础设施会根据 `settings.yml` 自动生成这个 `resolver_map`。SearXNG 会从以下 YAML 配置自动生成以下 TOML 配置：

search:
  favicon\_resolver: "duckduckgo"

\[favicons.proxy.resolver\_map\]

"duckduckgo" \= "searx.favicons.resolvers.duckduckgo"

如果不需要这个自动化功能，那么（并且只有在这种情况下）必须创建一个单独的 `resolver_map`。例如，如果要给用户两个选择解器的选项，可以使用以下配置：

\[favicons.proxy.resolver\_map\]

"duckduckgo" \= "searx.favicons.resolvers.duckduckgo"
"allesedv" \= "searx.favicons.resolvers.allesedv"
\# "google" = "searx.favicons.resolvers.google"
\# "yandex" = "searx.favicons.resolvers.yandex"

注意

每个解析器都会显著增加资源需求。

解析器的数量增加：

- 入站/出站请求数量
- 要存储在缓存中的 favicons 数量。

在以下部分，我们列出了 SearXNG 核心中可用的解析器，但通过 [FQN](https://en.wikipedia.org/wiki/Fully_qualified_name)，您也可以实现自己的解析器并将其集成到 *代理*中：

- [`searx.favicons.resolvers.duckduckgo`](https://docs.searxng.org/src/searx.favicons.html#searx.favicons.resolvers.duckduckgo "searx.favicons.resolvers.duckduckgo")
- [`searx.favicons.resolvers.allesedv`](https://docs.searxng.org/src/searx.favicons.html#searx.favicons.resolvers.allesedv "searx.favicons.resolvers.allesedv")
- [`searx.favicons.resolvers.google`](https://docs.searxng.org/src/searx.favicons.html#searx.favicons.resolvers.google "searx.favicons.resolvers.google")
- [`searx.favicons.resolvers.yandex`](https://docs.searxng.org/src/searx.favicons.html#searx.favicons.resolvers.yandex "searx.favicons.resolvers.yandex")