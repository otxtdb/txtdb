---
title: "SearXNG：架构"
source: "https://docs.searxng.org/admin/architecture.html"
author:
published:
created: 2026-03-01
description:
tags:
  - "clippings"
taxonomy: { doc_category: [searxng] }
---

进一步阅读

- 反向代理：[Apache](https://docs.searxng.org/admin/installation-apache.html#apache-searxng-site) & [nginx](https://docs.searxng.org/admin/installation-nginx.html#nginx-searxng-site)
- uWSGI：[uWSGI](https://docs.searxng.org/admin/installation-uwsgi.html#searxng-uwsgi)
- SearXNG: [逐步安装](https://docs.searxng.org/admin/installation-searxng.html#installation-basic)

这里你将找到一些关于 SearXNG 基础设施典型架构的提示和建议。

## uWSGI 设置¶

我们从公共 SearXNG 实例的*参考*设置开始，该设置可以通过我们 [DevOps 工具箱](https://docs.searxng.org/utils/index.html#toolboxing)中的脚本进行构建和维护。

digraph G {

  node \[style\=filled, shape\=box, fillcolor\="#ffffcc", fontname\=Sans\];
  edge \[fontname\="Sans"\];

  browser \[label\="browser", shape\=tab, fillcolor\=aliceblue\];
  rp      \[label\="reverse proxy"\];
  static  \[label\="static files", shape\=folder, href\="url to configure static files", fillcolor\=lightgray\];
  uwsgi   \[label\="uwsgi", shape\=parallelogram href\="https://docs.searxng.org/utils/searxng.sh.html"\]
  valkey  \[label\="valkey DB", shape\=cylinder\];

  searxng1  \[label\="SearXNG #1", fontcolor\=blue3\];
  searxng2  \[label\="SearXNG #2", fontcolor\=blue3\];
  searxng3  \[label\="SearXNG #3", fontcolor\=blue3\];
  searxng4  \[label\="SearXNG #4", fontcolor\=blue3\];

  browser \-> rp \[label\="HTTPS"\]

  subgraph cluster\_searxng {
      label \= "SearXNG instance" fontname\=Sans;
      bgcolor\="#fafafa";
      { rank\=same; static rp };
      rp \-> static  \[label\="optional: reverse proxy serves static files", fillcolor\=slategray, fontcolor\=slategray\];
      rp \-> uwsgi \[label\="http:// (tcp) or unix:// (socket)"\];
      uwsgi \-> searxng1 \-> valkey;
      uwsgi \-> searxng2 \-> valkey;
      uwsgi \-> searxng3 \-> valkey;
      uwsgi \-> searxng4 \-> valkey;
  }

}

图 2 公共 SearXNG 设置的参考架构。[¶](https://docs.searxng.org/admin/#id2 "Link to this image")

参考安装激活了 `server.limiter` 和 `server.image_proxy` ([/etc/searxng/settings.yml](https://github.com/searxng/searxng/blob/master/utils/templates/etc/searxng/settings.yml))

\# SearXNG settings

use\_default\_settings: true

general:
  debug: false
  instance\_name: "SearXNG"

search:
  safe\_search: 2
  autocomplete: 'duckduckgo'
  formats:
    \- html

server:
  \# Is overwritten by ${SEARXNG\_SECRET}
  secret\_key: "ultrasecretkey"
  limiter: true
  image\_proxy: true
  \# public URL of the instance, to ensure correct inbound links. Is overwritten
  \# by ${SEARXNG\_BASE\_URL}.
  \# base\_url: http://example.com/location

valkey:
  \# URL to connect valkey database. Is overwritten by ${SEARXNG\_VALKEY\_URL}.
  url: valkey://localhost:6379/0