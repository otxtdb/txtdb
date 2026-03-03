---
title: "SearXNG ：Granian"
source: "https://docs.searxng.org/admin/installation-granian.html"
author:
published:
created: 2026-03-01
description:
tags:
  - "clippings"
taxonomy: { doc_category: [searxng] }
---

进一步阅读

- [选项](https://github.com/emmett-framework/granian/blob/master/README.md#options)
- [工作进程和线程](https://github.com/emmett-framework/granian/blob/master/README.md#workers-and-threads)
- [背压](https://github.com/emmett-framework/granian/blob/master/README.md#backpressure)
- [运行模式](https://github.com/emmett-framework/granian/blob/master/README.md#runtime-mode)

注意

  
Granian 将成为 SearXNG 中的未来替代品。目前，它仅在[安装容器](https://docs.searxng.org/admin/installation-docker.html#installation-container)中正式支持。

## 安装¶

我们只推荐按照官方文档使用 pip 安装 Granian。在 SearXNG 的 Python 环境中运行以下命令：

$ pip install granian

## 配置¶

注意

不建议修改工作进程的数量，除非增加资源使用量并可能引发 [Bot Detection](https://docs.searxng.org/src/searx.botdetection.html#botdetection) 问题。

Granian 可以通过选项参数和环境变量（ `$GRANIAN_*`）进行配置。

我们提供了合理的默认值，应该能满足大多数使用场景，但如果您觉得 应该更改某些内容，Granian 在文档中记录了所有可用参数。 [选项](https://github.com/emmett-framework/granian/blob/master/README.md#options)部分。