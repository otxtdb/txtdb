---
title: "settings.yml — SearXNG 文档"
source: "https://docs.searxng.org/admin/settings/settings.html"
author:
published:
created: 2026-03-01
description:
tags:
  - "clippings"
taxonomy: { doc_category: [searxng] }
---
本页面描述了 [git://searx/settings.yml](https://github.com/searxng/searxng/blob/master/searx/settings.yml) 文件中的选项可能性 。

进一步阅读 ..

- [配置](https://docs.searxng.org/admin/installation-searxng.html#use-default-settings-yml)
- [搜索 API](https://docs.searxng.org/dev/search_api.html#search-api)

- [settings.yml 位置](https://docs.searxng.org/admin/settings/#settings-yml-location)
- [使用默认设置](https://docs.searxng.org/admin/settings/#use-default-settings)

## [settings.yml 位置](https://docs.searxng.org/admin/settings/#id2) [¶](https://docs.searxng.org/admin/settings/#settings-yml-location "Link to this heading")

初始的 `settings.yml` 将从这个位置加载：

1. 在 `SEARXNG_SETTINGS_PATH` 环境变量中指定的完整路径。
2. `/etc/searxng/settings.yml`

如果这些文件不存在（或为空或无法读取），SearXNG 使用 [git://searx/settings.yml](https://github.com/searxng/searxng/blob/master/searx/settings.yml) 文件。阅读 [use\_default\_settings](https://docs.searxng.org/admin/settings/#settings-use-default-settings) 了解如何简化您的 *用户定义* `settings.yml`。

## [use\_default\_settings](https://docs.searxng.org/admin/settings/#id3)[¶](https://docs.searxng.org/admin/settings/#use-default-settings "Link to this heading")

`use_default_settings: true`

- [settings.yml 位置](https://docs.searxng.org/admin/settings/#settings-location)
- [配置](https://docs.searxng.org/admin/installation-searxng.html#use-default-settings-yml)
- [/etc/searxng/settings.yml](https://github.com/searxng/searxng/blob/master/utils/templates/etc/searxng/settings.yml)

  
用户定义的 `settings.yml` 从 [settings.yml 位置](https://docs.searxng.org/admin/settings/#settings-location) 加载 并且可以使用：依赖默认配置 [git://searx/settings.yml](https://github.com/searxng/searxng/blob/master/searx/settings.yml)

> `use_default_settings: true`

`server:`

在以下示例中，实际设置是 [git://searx/settings.yml](https://github.com/searxng/searxng/blob/master/searx/settings.yml) 中定义的默认设置，除了 `secret_key` 和 `bind_address`：

use\_default\_settings: true
server:
    secret\_key: "ultrasecretkey"   \# change this!
    bind\_address: "\[::\]"

`engines:`

  
使用 `use_default_settings: true`，每个设置都可以以类似的方式覆盖，`engines` 部分将根据引擎 `name` 合并 在本示例中，SearXNG 将加载所有默认引擎，将启用 `bing` 引擎，并为 arch linux 引擎定义一个 [token](https://docs.searxng.org/admin/settings/settings_engines.html#private-engines)：

use\_default\_settings: true
server:
  secret\_key: "ultrasecretkey"   \# change this!
engines:
  \- name: arch linux wiki
    tokens: \['$ecretValue'\]
  \- name: bing
    disabled: false

`engines:` / `remove:`

可以从默认设置中移除一些引擎。以下示例与上一个示例类似，但 SearXNG 不会加载谷歌引擎：

use\_default\_settings:
  engines:
    remove:
      \- google
server:
  secret\_key: "ultrasecretkey"   \# change this!
engines:
  \- name: arch linux wiki
    tokens: \['$ecretValue'\]

`engines:` / `keep_only:`

或者，也可以指定要保留的引擎。在以下示例中，SearXNG 只有两个引擎：

use\_default\_settings:
  engines:
    keep\_only:
      \- google
      \- duckduckgo
server:
  secret\_key: "ultrasecretkey"   \# change this!
engines:
  \- name: google
    tokens: \['$ecretValue'\]
  \- name: duckduckgo
    tokens: \['$ecretValue'\]