---
title: "SearXNG：NGINX"
source: "https://docs.searxng.org/admin/installation-nginx.html"
author:
published:
created: 2026-03-01
description:
tags:
  - "clippings"
taxonomy: { doc_category: [searxng] }
---

本节将说明如何使用 HTTP 服务器 [nginx](https://docs.nginx.com/nginx/admin-guide/) 设置 SearXNG 实例。如果你已经使用了[安装脚本](https://docs.searxng.org/admin/installation-scripts.html#installation-scripts)并且没有特殊的偏好，你可以使用 [searxng.sh](https://docs.searxng.org/utils/searxng.sh.html#searxng-sh-overview):

$ sudo \-H ./utils/searxng.sh install nginx

如果你对设置 nginx 有特殊兴趣或问题，下一节可能会给你一些指导。

进一步阅读

- [nginx](https://docs.nginx.com/nginx/admin-guide/)
- [nginx 初学者指南](https://nginx.org/en/docs/beginners_guide.html)
- [nginx 服务器配置](https://docs.nginx.com/nginx/admin-guide/web-server/web-server/#setting-up-virtual-servers)
- [入门指南](https://www.nginx.com/resources/wiki/start/)
- [nginx 的 uWSGI 支持](https://uwsgi-docs.readthedocs.io/en/latest/Nginx.html)

- [nginx HTTP 服务器](https://docs.searxng.org/admin/#the-nginx-http-server)
- [NGINX 的 SearXNG 站点](https://docs.searxng.org/admin/#nginx-s-searxng-site)
- [禁用日志](https://docs.searxng.org/admin/#disable-logs)

## [nginx HTTP 服务器](https://docs.searxng.org/admin/#id2) [¶](https://docs.searxng.org/admin/#the-nginx-http-server "Link to this heading")

如果 [nginx](https://docs.nginx.com/nginx/admin-guide/) 没有安装，请立即安装。

sudo \-H apt-get install nginx

sudo \-H pacman \-S nginx-mainline
sudo \-H systemctl enable nginx
sudo \-H systemctl start nginx

sudo \-H dnf install nginx
sudo \-H systemctl enable nginx
sudo \-H systemctl start nginx

现在在 [http://localhost](http://localhost/) 你应该能看到一个 *Welcome to nginx!* 页面，在 Fedora 上你看到的是一个 *Fedora Webserver - Test Page*。这个测试页面来自默认的 [nginx 服务器配置](https://docs.nginx.com/nginx/admin-guide/web-server/web-server/#setting-up-virtual-servers) 。这个默认站点是如何配置的，取决于 Linux 发行版：

less /etc/nginx/nginx.conf

有一条行包含来自：

include /etc/nginx/sites-enabled/\*;

less /etc/nginx/nginx.conf

There is a configuration section named `server`:

server {
    listen       80;
    server\_name  localhost;
    \# ...
}

less /etc/nginx/nginx.conf

There is one line that includes site configurations from:

include /etc/nginx/conf.d/\*.conf;

## [NGINX 的 SearXNG 站点](https://docs.searxng.org/admin/#id3) [¶](https://docs.searxng.org/admin/#nginx-s-searxng-site "Link to this heading")

现在你需要为 SearXNG 站点创建一个配置文件（`searxng.conf`）。如果你对 [nginx](https://docs.nginx.com/nginx/admin-guide/) 不熟悉，[nginx 初学者指南](https://nginx.org/en/docs/beginners_guide.html)是一个很好的起点，而 [入门维基](https://www.nginx.com/resources/wiki/start/)始终是一个很好的资源*随时可以参考* 。

根据你的 SearXNG 安装监听的内容，你需要使用 http 或 socket 通信与上游通信。

location /searxng {

    uwsgi\_pass unix:///usr/local/searxng/run/socket;

    include uwsgi\_params;

    uwsgi\_param    HTTP\_HOST             $host;
    uwsgi\_param    HTTP\_CONNECTION       $http\_connection;

    \# see flaskfix.py
    uwsgi\_param    HTTP\_X\_FORWARDED\_PROTO  $scheme;
    uwsgi\_param    HTTP\_X\_SCRIPT\_NAME    /searxng;

    \# see botdetection/trusted\_proxies.py
    uwsgi\_param    HTTP\_X\_REAL\_IP        $remote\_addr;
    uwsgi\_param    HTTP\_X\_FORWARDED\_FOR  $proxy\_add\_x\_forwarded\_for;
}

\# To serve the static files via the HTTP server
#
\# location /searxng/static/ {
\#     alias /usr/local/searxng/searxng-src/searx/static/;
\# }

location /searxng {

    proxy\_pass http://127.0.0.1:8888;

    proxy\_set\_header   Host             $host;
    proxy\_set\_header   Connection       $http\_connection;

    \# see flaskfix.py
    proxy\_set\_header   X-Forwarded-Proto $scheme;
    proxy\_set\_header   X-Script-Name    /searxng;

    \# see botdetection/trusted\_proxies.py
    proxy\_set\_header   X-Real-IP        $remote\_addr;
    proxy\_set\_header   X-Forwarded-For  $proxy\_add\_x\_forwarded\_for;

    \# proxy\_buffering  off;
    \# proxy\_request\_buffering off;
    \# proxy\_buffer\_size 8k;

}

\# To serve the static files via the HTTP server
#
\# location /searxng/static/ {
\#     alias /usr/local/searxng/searxng-src/searx/static/;
\# }

  
[安装脚本](https://docs.searxng.org/admin/installation-scripts.html#installation-scripts)安装了[参考配置](https://docs.searxng.org/admin/installation-searxng.html#use-default-settings-yml)和一个默认监听 socket 的 [uWSGI 配置](https://docs.searxng.org/admin/installation-uwsgi.html#uwsgi-setup) 。

在 `/etc/nginx/sites-available/` 创建配置文件，并创建一个指向 `sites-enabled` 的软链接：

sudo \-H ln \-s /etc/nginx/sites-available/searxng.conf \\
              /etc/nginx/sites-enabled/searxng.conf

In the `/etc/nginx/nginx.conf` file, in the `server` section add a [include](https://nginx.org/en/docs/ngx_core_module.html#include) directive:

server {
    \# ...
    include /etc/nginx/default.d/\*.conf;
    \# ...
}

Create two folders, one for the *available sites* and one for the *enabled sites*:

mkdir \-p /etc/nginx/default.d
mkdir \-p /etc/nginx/default.apps-available

Create configuration at `/etc/nginx/default.apps-available` and place a symlink to `default.d`:

sudo \-H ln \-s /etc/nginx/default.apps-available/searxng.conf \\
              /etc/nginx/default.d/searxng.conf

Create a folder for the *available sites*:

mkdir \-p /etc/nginx/default.apps-available

Create configuration at `/etc/nginx/default.apps-available` and place a symlink to `conf.d`:

sudo \-H ln \-s /etc/nginx/default.apps-available/searxng.conf \\
              /etc/nginx/conf.d/searxng.conf

重启服务：

sudo \-H systemctl restart nginx
sudo \-H service uwsgi restart searxng

sudo \-H systemctl restart nginx
sudo \-H systemctl restart uwsgi@searxng

sudo \-H systemctl restart nginx
sudo \-H touch /etc/uwsgi.d/searxng.ini

## [禁用日志](https://docs.searxng.org/admin/#id4) [¶](https://docs.searxng.org/admin/#disable-logs "Link to this heading")

为了更好的隐私保护，您可以在 `/etc/nginx/nginx.conf` 中禁用 nginx 日志。

http {
    \# ...
    access\_log /dev/null;
    error\_log  /dev/null;
    \# ...
}