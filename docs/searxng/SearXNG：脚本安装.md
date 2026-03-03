---
title: "SearXNG：脚本安装"
source: "https://docs.searxng.org/admin/installation-scripts.html"
author:
published:
created: 2026-02-27
description:
tags:
  - "clippings"
taxonomy: { doc_category: [searxng] }
---
首先更新操作系统！

为了避免不期望的副作用，在安装 SearXNG 之前请先更新您的操作系统。

以下将安装参考架构[中所示](https://docs.searxng.org/admin/architecture.html#arch-public)的配置。首先您需要获取仓库的克隆。克隆仅在安装过程和一些维护任务中需要。

继续阅读

- [DevOps 工具箱](https://docs.searxng.org/utils/index.html#toolboxing)

跳转到可被*其他人*读取的文件夹，开始克隆 SearXNG，或者你可以创建自己的分支并从那里克隆。

$ cd ~/Downloads
$ git clone https://github.com/searxng/searxng.git searxng
$ cd searxng

继续阅读

- [如何检查和调试](https://docs.searxng.org/admin/update-searxng.html#inspect-searxng)

要安装一个 SearXNG [参考设置](https://docs.searxng.org/admin/installation-searxng.html#use-default-settings-yml) 包括如 [uWSGI 设置](https://docs.searxng.org/admin/architecture.html#architecture-uwsgi)中所述的 [逐步安装](https://docs.searxng.org/admin/installation-searxng.html#installation-basic)并在 [uWSGI](https://docs.searxng.org/admin/installation-uwsgi.html#searxng-uwsgi) 部分输入：

$ sudo \-H ./utils/searxng.sh install all

注意

在安装过程中，请使用 *sudoer* 账户登录来运行脚本。如果你从 `root` 安装，请注意脚本会创建一个 `searxng` 用户。在安装过程中，这个新创建的用户需要能够读取克隆的 SearXNG 仓库，如果你将其克隆到 `/root` 以下的文件夹中，这是不可能的！

进一步阅读

- [如何更新](https://docs.searxng.org/admin/update-searxng.html#update-searxng)

当所有服务都已安装并运行良好时，您可以将 SearXNG 添加到您的 HTTP 服务器。我们对 HTTP 服务器没有任何偏好，您可以使用任何您喜欢的。

我们实现了以下安装步骤：

- [NGINX](https://docs.searxng.org/admin/installation-nginx.html#installation-nginx)
- [Apache](https://docs.searxng.org/admin/installation-apache.html#installation-apache)