---
title: "brand: — SearXNG 文档"
source: https://docs.searxng.org/admin/settings/settings_brand.html
author:
published:
created: 2026-03-01
description:
tags:
  - clippings
taxonomy:
  doc_category:
    - searxng
---
*class* searx.brand.SettingsBrand(*\**, *issue\_url: str \= 'https://github.com/searxng/searxng/issues'*, *docs\_url: str \= 'https://docs.searxng.org'*, *public\_instances: str \= 'https://searx.space'*, *wiki\_url: str \= 'https://github.com/searxng/searxng/wiki'*, *custom: ~searx.brand.BrandCustom \= <factory>*, *new\_issue\_url: str \= 'https://github.com/searxng/searxng/issues/new'*)[\[source\]](https://docs.searxng.org/_modules/searx/brand.html#SettingsBrand)[¶](https://docs.searxng.org/admin/settings/#searx.brand.SettingsBrand "Link to this definition")

配置品牌属性的选项。

brand:
  issue\_url: https://github.com/searxng/searxng/issues
  docs\_url: https://docs.searxng.org
  public\_instances: https://searx.space
  wiki\_url: https://github.com/searxng/searxng/wiki

  custom:
    links:
      Uptime: https://uptime.searxng.org/history/example-org
      About: https://example.org/user/about.html

issue\_url*: [str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")*[¶](https://docs.searxng.org/admin/settings/#searx.brand.SettingsBrand.issue_url "Link to this definition")

如果你托管自己的问题追踪器，请更改此 URL。

docs\_url*: [str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")*[¶](https://docs.searxng.org/admin/settings/#searx.brand.SettingsBrand.docs_url "Link to this definition")

如果你托管自己的文档，请更改此 URL。

public\_instances*: [str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")*[¶](https://docs.searxng.org/admin/settings/#searx.brand.SettingsBrand.public_instances "Link to this definition")

如果你托管自己的 [https://searx.space](https://searx.space/)，请更改此 URL。

wiki\_url*: [str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")*[¶](https://docs.searxng.org/admin/settings/#searx.brand.SettingsBrand.wiki_url "Link to this definition")

链接到你的维基（或 `false`）

custom*: BrandCustom*[¶](https://docs.searxng.org/admin/settings/#searx.brand.SettingsBrand.custom "Link to this definition")

可选的自定义设置。

*class* BrandCustom(*\**, *links: dict\[str*, *str\] \= <factory>*)[¶](https://docs.searxng.org/admin/settings/#searx.brand.SettingsBrand.BrandCustom "Link to this definition")

品牌部分的定制设置。

BrandCustom.links*: [dict](https://docs.python.org/3/library/stdtypes.html#dict "(in Python v3.14)")\[[str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)"), [str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")\]*[¶](https://docs.searxng.org/admin/settings/#searx.brand.SettingsBrand.BrandCustom.BrandCustom.links "Link to this definition")

WEB 页面页脚的自定义条目：`[标题]： [链接]`

new\_issue\_url*: [str](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.14)")*[¶](https://docs.searxng.org/admin/settings/#searx.brand.SettingsBrand.new_issue_url "Link to this definition")

如果你不在 GitHub 上托管自己的问题追踪器，则取消设置此 URL。

注意：此 URL 将为引擎创建一个预填写的 GitHub 问题报告