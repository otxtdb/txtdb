---
title: "SearXNG：容器安装"
source: "https://docs.searxng.org/admin/installation-docker.html"
author:
published:
created: 2026-02-27
description:
tags:
  - "clippings"
taxonomy: { doc_category: [searxng] }
---
info

- [Docker 101](https://docs.docker.com/get-started/docker-overview)
- [Docker 速查表（PDF 文档）](https://docs.docker.com/get-started/docker_cheatsheet.pdf)
- [Podman 无根容器](https://github.com/containers/podman/blob/main/docs/tutorials/rootless_tutorial.md)

重要提示

理解容器架构基础对于正确维护您的 SearXNG 实例至关重要。本指南假设您熟悉容器概念，并提供了高层级的部署步骤。

如果您是容器的新手，我们建议您先学习基础知识。 [Docker 101](https://docs.docker.com/get-started/docker-overview) 在继续之前。

容器镜像是在容器化环境中部署的基础， [Docker compose](https://github.com/searxng/searxng-docker)、Kubernetes 等。

## 安装¶

### 先决条件¶

您需要在系统上安装可用的 Docker 或 Podman。根据您的环境选择最合适的选项：

- [Docker](https://docs.docker.com/get-docker/)（推荐大多数用户使用）
- [Podman](https://podman.io/docs/installation)

在 Docker 的情况下，您需要将运行容器的用户添加到 `docker` 组并重启会话：

$ sudo usermod \-aG docker $USER

在 Podman 的情况下，通常不需要额外的步骤，但在运行 [Podman 无根容器](https://github.com/containers/podman/blob/main/docs/tutorials/rootless_tutorial.md)时有一些注意事项。

### 拉取镜像¶

注意

DockerHub 现在对未认证的镜像拉取应用速率限制。如果你受此影响，可以使用 [GHCR 镜像](https://ghcr.io/searxng/searxng) 代替。

官方镜像位于：

- [DockerHub 镜像](https://hub.docker.com/r/searxng/searxng)
- [GHCR 镜像](https://ghcr.io/searxng/searxng) (GitHub Container Registry)

拉取最新镜像：

$ docker pull docker.io/searxng/searxng:latest

.. 或者如果你想要锁定到特定版本：

$ docker pull docker.io/searxng/searxng:2025.8.1-3d96414

## 实例化¶

本节面向需要自定义部署的高级用户。我们推荐使用 [Docker compose](https://github.com/searxng/searxng-docker)，它提供了一个预配置的环境，并带有合理的默认设置。

基本的容器实例化示例：

\# Create directories for configuration and persistent data
$ mkdir \-p ./searxng/config/ ./searxng/data/
$ cd ./searxng/

\# Run the container
$ docker run \--name searxng \-d \\
    \-p 8888:8080 \\
    \-v "./config/:/etc/searxng/" \\
    \-v "./data/:/var/cache/searxng/" \\
    docker.io/searxng/searxng:latest

这将使 SearXNG 在后台启动，可通过 [http://localhost:8888 访问](http://localhost:8888/)

### 管理¶

列出正在运行的容器：

$ docker container list
CONTAINER ID  IMAGE  ...  CREATED        PORTS                   NAMES
1af574997e63  ...    ...  3 minutes ago  0.0.0.0:8888->8080/tcp  searxng

访问容器 shell（用于故障排除）：

$ docker container exec \-it \--user root searxng /bin/sh \-l
1af574997e63:/usr/local/searxng#

停止并移除容器：

$ docker container stop searxng
$ docker container rm searxng

## 卷

有两个卷暴露出来，应该挂载以保留其内容：

- `/etc/searxng`：配置文件（settings.yml 等）
- `/var/cache/searxng`: 持久化数据 (faviconcache.db 等)

## 环境变量¶

可以配置以下环境变量：

- `$SEARXNG_*`: 控制 SearXNG 的配置选项，注意在 [server:](https://docs.searxng.org/admin/settings/settings_server.html#settings-server) 和 [general:](https://docs.searxng.org/admin/settings/settings_general.html#settings-general) 中查找环境变量 $SEARXNG\_\*。
- `$GRANIAN_*`: 控制着 [Granian 服务器选项](https://docs.searxng.org/admin/installation-granian.html#granian-configuration) 。
- `$FORCE_OWNERSHIP`: 确保挂载的卷/文件由 `searxng:searxng` 用户拥有（默认：`true`）

容器内部路径（除非你知道自己在做什么，否则不要修改）：

- `$CONFIG_PATH`: SearXNG 配置目录的路径（默认：`/etc/searxng`）
- `$SEARXNG_SETTINGS_PATH`: SearXNG 设置文件的路径（默认：`$CONFIG_PATH/settings.yml`）
- `$DATA_PATH`: SearXNG 数据目录的路径（默认：`/var/cache/searxng`）

## 自定义证书¶

您可以将 `/usr/local/share/ca-certificates/` 文件夹挂载以按需添加/删除附加证书。

它们将在容器（重新）启动时或当在容器 shell 中运行 `update-ca-certificates` 时可用。

## 自定义镜像¶

要从源代码构建您自己的 SearXNG 容器镜像（请注意，自定义容器镜像并不官方支持）：

$ git clone https://github.com/searxng/searxng.git
$ cd ./searxng/

\# Run the container build script
$ make container

$ docker images
REPOSITORY                 TAG                 IMAGE ID  CREATED             SIZE
localhost/searxng/searxng  2025.8.1-3d96414    ...       About a minute ago  183 MB
localhost/searxng/searxng  latest              ...       About a minute ago  183 MB
localhost/searxng/searxng  builder             ...       About a minute ago  524 MB
ghcr.io/searxng/base       searxng-builder     ...       2 days ago          378 MB
ghcr.io/searxng/base       searxng             ...       2 days ago          42.2 MB