---
title: "SearXNG：安装步骤"
source: "https://docs.searxng.org/admin/installation-searxng.html"
author:
published:
created: 2026-02-27
description:
tags:
  - "clippings"
taxonomy: { doc_category: [searxng] }
---
- [安装软件包](https://docs.searxng.org/admin/#install-packages)
- [创建用户](https://docs.searxng.org/admin/#create-user)
- [安装 SearXNG 及依赖项](https://docs.searxng.org/admin/#install-searxng-dependencies)
- [配置](https://docs.searxng.org/admin/#configuration)
- [检查](https://docs.searxng.org/admin/#check)

在本节中，我们将展示 SearXNG 实例的设置，该实例将由 [安装脚本](https://docs.searxng.org/admin/installation-scripts.html#installation-scripts)安装。

## [安装软件包](https://docs.searxng.org/admin/#id2) [¶](https://docs.searxng.org/admin/#install-packages "Link to this heading")

$ sudo \-H apt-get install \-y \\
    python3-dev python3-babel python3-venv python-is-python3 \\
    uwsgi uwsgi-plugin-python3 \\
    git build-essential libxslt-dev zlib1g-dev libffi-dev libssl-dev

$ sudo \-H pacman \-S \--noconfirm \\
    python python-pip python-lxml python-babel \\
    uwsgi uwsgi-plugin-python \\
    git base-devel libxml2

$ sudo \-H dnf install \-y \\
    python python-pip python-lxml python-babel python3-devel \\
    uwsgi uwsgi-plugin-python3 \\
    git @development-tools libxml2 openssl

提示

  
这也安装了 [uWSGI 所需的软件包](https://docs.searxng.org/admin/installation-uwsgi.html#searxng-uwsgi)

## [创建用户](https://docs.searxng.org/admin/#id3) [¶](https://docs.searxng.org/admin/#create-user "Link to this heading")

$ sudo \-H useradd \--shell /bin/bash \--system \\
    \--home-dir "/usr/local/searxng" \\
    \--comment 'Privacy-respecting metasearch engine' \\
    searxng

$ sudo \-H mkdir "/usr/local/searxng"
$ sudo \-H chown \-R "searxng:searxng" "/usr/local/searxng"

## [安装 SearXNG 及依赖](https://docs.searxng.org/admin/#id4) [¶](https://docs.searxng.org/admin/#install-searxng-dependencies "Link to this heading")

从新创建的用户启动交互式 shell 并克隆 SearXNG：

$ sudo \-H \-u searxng \-i
(searxng)$ git clone "https://github.com/searxng/searxng" \\
                   "/usr/local/searxng/searxng-src"

在同一个 shell 中创建*虚拟环境* ：

(searxng)$ python3 \-m venv "/usr/local/searxng/searx-pyenv"
(searxng)$ echo ". /usr/local/searxng/searx-pyenv/bin/activate" \\
                   \>>  "/usr/local/searxng/.profile"

要安装 SearXNG 的依赖项，退出上面打开的 SearXNG *bash* 会话，并启动一个新的会话。在安装之前，检查你的 *虚拟环境*是否从登录配置（ *~/.profile*）中源化：

$ sudo \-H \-u searxng \-i

(searxng)$ command \-v python && python \--version
/usr/local/searxng/searx-pyenv/bin/python
Python 3.11.10

\# update pip's boilerplate ..
pip install \-U pip
pip install \-U setuptools
pip install \-U wheel
pip install \-U pyyaml
pip install \-U msgspec

\# jump to SearXNG's working tree and install SearXNG into virtualenv
(searxng)$ cd "/usr/local/searxng/searxng-src"
(searxng)$ pip install \--use-pep517 \--no-build-isolation \-e .

提示

为配置任务打开第二个终端，并保留 `(searx)$` 下方任务所需的终端打开状态。

## [配置](https://docs.searxng.org/admin/#id5) [¶](https://docs.searxng.org/admin/#configuration "Link to this heading")

`use_default_settings: True`

- [settings.yml](https://docs.searxng.org/admin/settings/settings.html#settings-yml)
- [settings.yml 位置](https://docs.searxng.org/admin/settings/settings.html#settings-location)
- [使用默认设置](https://docs.searxng.org/admin/settings/settings.html#settings-use-default-settings)
- [/etc/searxng/settings.yml](https://github.com/searxng/searxng/blob/master/utils/templates/etc/searxng/settings.yml)

  
要创建初始的 `/etc/searxng/settings.yml`，我们建议从文件 [git://utils/templates/etc/searxng/settings.yml](https://github.com/searxng/searxng/blob/master/utils/templates/etc/searxng/settings.yml) 复制一份开始。这个设置 [使用默认设置](https://docs.searxng.org/admin/settings/settings.html#settings-use-default-settings) 来自 [git://searx/settings.yml](https://github.com/searxng/searxng/blob/master/searx/settings.yml)，并在 *“使用默认设置”* 标签页中显示 以下是。这个设置：

- 启用 [limiter](https://docs.searxng.org/admin/searx.limiter.html#limiter) 来防范机器人
- 启用 [image proxy](https://docs.searxng.org/admin/settings/settings_server.html#image-proxy) 以增强隐私保护

根据你的需求修改 `/etc/searxng/settings.yml`：

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

要查看整个文件，请跳转到 [git://utils/templates/etc/searxng/settings.yml](https://github.com/searxng/searxng/blob/master/utils/templates/etc/searxng/settings.yml)

general:
  \# Debug mode, only for development. Is overwritten by ${SEARXNG\_DEBUG}
  debug: false
  \# displayed name
  instance\_name: "SearXNG"
  \# For example: https://example.com/privacy
  privacypolicy\_url: false
  \# use true to use your own donation page written in searx/info/en/donate.md
  \# use false to disable the donation link
  donation\_url: false
  \# mailto:contact@example.com
  contact\_url: false
  \# record stats
  enable\_metrics: true
  \# expose stats in open metrics format at /metrics
  \# leave empty to disable (no password set)
  \# open\_metrics: <password>
  open\_metrics: ''

brand:
  new\_issue\_url: https://github.com/searxng/searxng/issues/new
  docs\_url: https://docs.searxng.org/
  public\_instances: https://searx.space
  wiki\_url: https://github.com/searxng/searxng/wiki
  issue\_url: https://github.com/searxng/searxng/issues
  \# custom:
  \#   # Custom entries in the footer: \[title\]: \[link\]
  \#   links:
  \#     Uptime: https://uptime.searxng.org/history/darmarit-org
  \#     About: "https://searxng.org"

search:
  \# Filter results. 0: None, 1: Moderate, 2: Strict
  safe\_search: 0
  \# Existing autocomplete backends: "360search", "baidu", "brave", "dbpedia", "duckduckgo", "google", "yandex",
  \# "mwmbl", "naver", "seznam", "sogou", "startpage", "stract", "swisscows", "quark", "qwant", "wikipedia" -
  \# leave blank to turn it off by default.
  autocomplete: ""
  \# minimun characters to type before autocompleter starts
  autocomplete\_min: 4
  \# backend for the favicon near URL in search results.
  \# Available resolvers: "allesedv", "duckduckgo", "google", "yandex" - leave blank to turn it off by default.
  favicon\_resolver: ""
  \# Default search language - leave blank to detect from browser information or
  \# use codes from 'languages.py'
  default\_lang: "auto"
  \# max\_page: 0  # if engine supports paging, 0 means unlimited numbers of pages
  \# Available languages
  \# languages:
  \#   - all
  \#   - en
  \#   - en-US
  \#   - de
  \#   - it-IT
  \#   - fr
  \#   - fr-BE
  \# ban time in seconds after engine errors
  ban\_time\_on\_fail: 5
  \# max ban time in seconds after engine errors
  max\_ban\_time\_on\_fail: 120
  suspended\_times:
    \# Engine suspension time after error (in seconds; set to 0 to disable)
    \# For error "Access denied" and "HTTP error \[402, 403\]"
    SearxEngineAccessDenied: 180
    \# For error "CAPTCHA"
    SearxEngineCaptcha: 3600
    \# For error "Too many request" and "HTTP error 429"
    SearxEngineTooManyRequests: 180
    \# Cloudflare CAPTCHA
    cf\_SearxEngineCaptcha: 1296000
    cf\_SearxEngineAccessDenied: 86400
    \# ReCAPTCHA
    recaptcha\_SearxEngineCaptcha: 604800

  \# remove format to deny access, use lower case.
  \# formats: \[html, csv, json, rss\]
  formats:
    \- html

server:
  \# Is overwritten by ${SEARXNG\_PORT} and ${SEARXNG\_BIND\_ADDRESS}
  port: 8888
  bind\_address: "127.0.0.1"
  \# public URL of the instance, to ensure correct inbound links. Is overwritten
  \# by ${SEARXNG\_BASE\_URL}.
  base\_url: false  \# "http://example.com/location"
  \# rate limit the number of request on the instance, block some bots.
  \# Is overwritten by ${SEARXNG\_LIMITER}
  limiter: false
  \# enable features designed only for public instances.
  \# Is overwritten by ${SEARXNG\_PUBLIC\_INSTANCE}
  public\_instance: false

  \# If your instance owns a /etc/searxng/settings.yml file, then set the following
  \# values there.

  secret\_key: "ultrasecretkey"  \# Is overwritten by ${SEARXNG\_SECRET}
  \# Proxy image results through SearXNG. Is overwritten by ${SEARXNG\_IMAGE\_PROXY}
  image\_proxy: false
  \# 1.0 and 1.1 are supported
  http\_protocol\_version: "1.0"
  \# POST queries are "more secure!" but are also the source of hard-to-locate
  \# annoyances, which is why GET may be better for end users and their browsers.
  \# see https://github.com/searxng/searxng/pull/3619
  \# Is overwritten by ${SEARXNG\_METHOD}
  method: "POST"
  default\_http\_headers:
    X-Content-Type-Options: nosniff
    X-Download-Options: noopen
    X-Robots-Tag: noindex, nofollow
    Referrer-Policy: no-referrer

valkey:
  \# URL to connect valkey database. Is overwritten by ${SEARXNG\_VALKEY\_URL}.
  \# https://docs.searxng.org/admin/settings/settings\_valkey.html#settings-valkey
  \# url: valkey://localhost:6379/0
  url: false

ui:
  \# Custom static path - leave it blank if you didn't change
  static\_path: ""
  \# Custom templates path - leave it blank if you didn't change
  templates\_path: ""
  \# query\_in\_title: When true, the result page's titles contains the query
  \# it decreases the privacy, since the browser can records the page titles.
  query\_in\_title: false
  \# ui theme
  default\_theme: simple
  \# center the results ?
  center\_alignment: false
  \# URL prefix of the internet archive, don't forget trailing slash (if needed).
  \# cache\_url: "https://webcache.googleusercontent.com/search?q=cache:"
  \# Default interface locale - leave blank to detect from browser information or
  \# use codes from the 'locales' config section
  default\_locale: ""
  \# Open result links in a new tab by default
  \# results\_on\_new\_tab: false
  theme\_args:
    \# style of simple theme: auto, light, dark, black
    simple\_style: auto
  \# Perform search immediately if a category selected.
  \# Disable to select multiple categories at once and start the search manually.
  search\_on\_category\_select: true
  \# Hotkeys: default or vim
  hotkeys: default
  \# URL formatting: pretty, full or host
  url\_formatting: pretty

\# Lock arbitrary settings on the preferences page.
#
\# preferences:
\#   lock:
\#     - categories
\#     - language
\#     - autocomplete
\#     - favicon
\#     - safesearch
\#     - method
\#     - doi\_resolver
\#     - locale
\#     - theme
\#     - results\_on\_new\_tab
\#     - search\_on\_category\_select
\#     - method
\#     - image\_proxy
\#     - query\_in\_title

\# communication with search engines
#
outgoing:
  \# default timeout in seconds, can be override by engine
  request\_timeout: 3.0
  \# the maximum timeout in seconds
  \# max\_request\_timeout: 10.0
  \# suffix of searxng\_useragent, could contain information like an email address
  \# to the administrator
  useragent\_suffix: ""
  \# The maximum number of concurrent connections that may be established.
  pool\_connections: 100
  \# Allow the connection pool to maintain keep-alive connections below this
  \# point.
  pool\_maxsize: 20
  \# See https://www.python-httpx.org/http2/
  enable\_http2: true
  \# uncomment below section if you want to use a custom server certificate
  \# see https://www.python-httpx.org/advanced/#changing-the-verification-defaults
  \# and https://www.python-httpx.org/compatibility/#ssl-configuration
  \#  verify: ~/.mitmproxy/mitmproxy-ca-cert.cer
  #
  \# uncomment below section if you want to use a proxyq see: SOCKS proxies
  \#   https://2.python-requests.org/en/latest/user/advanced/#proxies
  \# are also supported: see
  \#   https://2.python-requests.org/en/latest/user/advanced/#socks
  #
  \#  proxies:
  \#    all://:
  \#      - http://proxy1:8080
  \#      - http://proxy2:8080
  #
  \#  using\_tor\_proxy: true
  #
  \# Extra seconds to add in order to account for the time taken by the proxy
  #
  \#  extra\_proxy\_timeout: 10
  #
  \# uncomment below section only if you have more than one network interface
  \# which can be the source of outgoing search requests
  #
  \#  source\_ips:
  \#    - 1.1.1.1
  \#    - 1.1.1.2
  \#    - fe80::/126

\# Plugin configuration, for more details see
\#   https://docs.searxng.org/admin/settings/settings\_plugins.html
#
plugins:

  searx.plugins.calculator.SXNGPlugin:
    active: true

  searx.plugins.infinite\_scroll.SXNGPlugin:
    active: false

  searx.plugins.hash\_plugin.SXNGPlugin:
    active: true

  searx.plugins.self\_info.SXNGPlugin:
    active: true

  searx.plugins.unit\_converter.SXNGPlugin:
    active: true

  searx.plugins.ahmia\_filter.SXNGPlugin:
    active: true

  searx.plugins.hostnames.SXNGPlugin:
    active: true

  searx.plugins.time\_zone.SXNGPlugin:
    active: true

  searx.plugins.oa\_doi\_rewrite.SXNGPlugin:
    active: false

  searx.plugins.tor\_check.SXNGPlugin:
    active: false

  searx.plugins.tracker\_url\_remover.SXNGPlugin:
    active: true

\# Configuration of the "Hostnames plugin":
#

To see the entire file jump to [git://searx/settings.yml](https://github.com/searxng/searxng/blob/master/searx/settings.yml)

对于 *最小化配置* ，你需要设置 `server:secret_key`。

$ sudo \-H mkdir \-p "/etc/searxng"
$ sudo \-H cp "/usr/local/searxng/searxng-src/utils/templates/etc/searxng/settings.yml" \\
             "/etc/searxng/settings.yml"

$ sudo \-H sed \-i \-e "s/ultrasecretkey/$(openssl rand \-hex 16)/g" \\
              "/etc/searxng/settings.yml"

## [检查](https://docs.searxng.org/admin/#id6) [¶](https://docs.searxng.org/admin/#check "Link to this heading")

要检查您的 SearXNG 设置，可以选择启用调试并启动 *webapp*。SearXNG 会查看导出的环境 `$SEARXNG_SETTINGS_PATH` 以寻找配置文件。

\# enable debug ..
$ sudo \-H sed \-i \-e "s/debug : False/debug : True/g" "/etc/searxng/settings.yml"

\# start webapp
$ sudo \-H \-u searxng \-i
(searxng)$ cd /usr/local/searxng/searxng-src
(searxng)$ export SEARXNG\_SETTINGS\_PATH\="/etc/searxng/settings.yml"
(searxng)$ python searx/webapp.py

\# disable debug
$ sudo \-H sed \-i \-e "s/debug : True/debug : False/g" "/etc/searxng/settings.yml"

打开 WEB 浏览器并访问 [http://127.0.0.1:8888](http://127.0.0.1:8888/)。如果你在容器内或使用脚本，请用 curl 进行测试：

$ xdg-open http://127.0.0.1:8888

$ curl --location --verbose --head --insecure 127.0.0.1:8888

\*   Trying 127.0.0.1:8888...
\* TCP\_NODELAY set
\* Connected to 127.0.0.1 (127.0.0.1) port 8888 (#0)
> HEAD / HTTP/1.1
> Host: 127.0.0.1:8888
> User-Agent: curl/7.68.0
> Accept: \*/\*
>
\* Mark bundle as not supporting multiuse
\* HTTP 1.0, assume close after body
< HTTP/1.0 200 OK
HTTP/1.0 200 OK
...

如果一切运行正常，请按 `[CTRL-C]` 停止 *webapp* 并在 `settings.yml` 中禁用调试选项。现在您可以退出 SearXNG 用户 bash 会话（输入两次 exit 命令）。此时 SearXNG 没有作为守护进程运行；uwsgi 允许这样做。