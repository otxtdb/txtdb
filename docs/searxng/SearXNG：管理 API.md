---
title: "SearXNG：管理 API"
source: "https://docs.searxng.org/admin/api.html"
author:
published:
created: 2026-03-01
description:
tags:
  - "clippings"
taxonomy: { doc_category: [searxng] }
---

## 获取配置数据¶

GET /config  HTTP/1.1

### 示例响应¶

{
  "autocomplete": "",
  "categories": \[
    "map",
    "it",
    "images",
  \],
  "default\_locale": "",
  "default\_theme": "simple",
  "engines": \[
    {
      "categories": \[
        "map"
      \],
      "enabled": true,
      "name": "openstreetmap",
      "shortcut": "osm"
    },
    {
      "categories": \[
        "it"
      \],
      "enabled": true,
      "name": "arch linux wiki",
      "shortcut": "al"
    },
    {
      "categories": \[
        "images"
      \],
      "enabled": true,
      "name": "google images",
      "shortcut": "goi"
    },
    {
      "categories": \[
        "it"
      \],
      "enabled": false,
      "name": "bitbucket",
      "shortcut": "bb"
    },
  \],
  "instance\_name": "SearXNG",
  "locales": {
    "de": "Deutsch (German)",
    "en": "English",
    "eo": "Esperanto (Esperanto)",
  },
  "plugins": \[
    {
      "enabled": true,
      "name": "HTTPS rewrite"
    }
  \],
  "safe\_search": 0
}

## 嵌入搜索栏¶

搜索栏可以嵌入到网站中。只需将示例粘贴到网站的 HTML 中。SearXNG 实例的 URL 和值是可定制的。

<form method\="post" action\="https://example.org/"\>
  <!-- search      --> <input type\="text" name\="q"\>
  <!-- categories  --> <input type\="hidden" name\="categories" value\="general,social media"\>
  <!-- language    --> <input type\="hidden" name\="lang" value\="all"\>
  <!-- locale      --> <input type\="hidden" name\="locale" value\="en"\>
  <!-- date filter --> <input type\="hidden" name\="time\_range" value\="month"\>
</form\>