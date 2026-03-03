---
title: "SearXNG：uWSGI"
source: "https://docs.searxng.org/admin/installation-uwsgi.html"
author:
published:
created: 2026-03-01
description:
tags:
  - "clippings"
taxonomy: { doc_category: [searxng] }
---

进一步阅读

- [systemd.unit](https://www.freedesktop.org/software/systemd/man/systemd.unit.html)
- [uWSGI 帝王](https://uwsgi-docs.readthedocs.io/en/latest/Emperor.html)

- [原始 uWSGI](https://docs.searxng.org/admin/#origin-uwsgi)
- [发行商](https://docs.searxng.org/admin/#distributors)
	- [Debian 的 uWSGI 布局](https://docs.searxng.org/admin/#debian-s-uwsgi-layout)
- [uWSGI 维护](https://docs.searxng.org/admin/#uwsgi-maintenance)
- [uWSGI 设置](https://docs.searxng.org/admin/#uwsgi-setup)
- [暴君模式的陷阱](https://docs.searxng.org/admin/#pitfalls-of-the-tyrant-mode)

## [原始 uWSGI](https://docs.searxng.org/admin/#id7)[¶](https://docs.searxng.org/admin/#origin-uwsgi "Link to this heading")

发行商如何实现 uWSGI 各不相同。uWSGI 项目本身推荐两种方法：

1. [systemd.unit](https://www.freedesktop.org/software/systemd/man/systemd.unit.html) 模板文件，如本文所述 [每个应用一个服务在 systemd 中](https://uwsgi-docs.readthedocs.io/en/latest/Systemd.html#one-service-per-app-in-systemd) ：

> 系统上安装有一个 [systemd 单元模板](http://0pointer.de/blog/projects/instances.html) ，每个 uWSGI 应用一个 [uwsgi ini 文件](https://uwsgi-docs.readthedocs.io/en/latest/Configuration.html#ini-files) 放置在特定位置。以 archlinux 和 a `searxng.ini` 为例：
> 
> systemd template unit: /usr/lib/systemd/system/uwsgi@.service
>         contains: \[Service\]
>                   ExecStart\=/usr/bin/uwsgi \--ini /etc/uwsgi/%I.ini
> 
> SearXNG application:   /etc/uwsgi/searxng.ini
>         links to: /etc/uwsgi/apps\-available/searxng.ini
> 
> SearXNG 应用（模板 `/etc/uwsgi/%I.ini`）可以像常见的 systemd 单元一样进行维护：
> 
> $ systemctl enable  uwsgi@searxng
> $ systemctl start   uwsgi@searxng
> $ systemctl restart uwsgi@searxng
> $ systemctl stop    uwsgi@searxng

2. 适用于维护大量 uWSGI 应用的 ，并且有一个[暴君模式](https://uwsgi-docs.readthedocs.io/en/latest/Emperor.html#tyrant-mode-secure-multi-user-hosting)来保障多用户托管。

> 皇帝模式是一种特殊的 uWSGI 实例，它将监控特定事件。皇帝模式（服务）是由一个（非模板的）systemd 单元启动的。
> 
>   
> 皇帝服务将扫描特定目录以查找 （也称为*属下* ）。如果添加、删除属下或修改时间戳，将执行相应操作：启动新的 uWSGI 实例、重新加载或停止。以 Fedora 和 `searxng.ini 为例：`
> 
> to install & start SearXNG instance create \--> /etc/uwsgi.d/searxng.ini
> to reload the instance edit timestamp      \--> touch /etc/uwsgi.d/searxng.ini
> to stop instance remove ini                \--> rm /etc/uwsgi.d/searxng.ini

## [发行商](https://docs.searxng.org/admin/#id8) [¶](https://docs.searxng.org/admin/#distributors "Link to this heading")

  
发行商主要向用户提供 uWSGI 皇帝模式和 ，尽管它们在实现这两种模式及其默认值的方式上有所不同。它们可能不同的另一个点是插件的打包（如果是这样，请比较[安装包](https://docs.searxng.org/admin/installation-searxng.html#install-packages) ）以及默认的 Python 解释器是什么（python2 与 python3）。

虽然 archlinux 默认不启动 uWSGI 服务，但 Fedora（RHEL）默认以 [暴君模式](https://uwsgi-docs.readthedocs.io/en/latest/Emperor.html#tyrant-mode-secure-multi-user-hosting)启动皇帝（你应该已经阅读了[暴君模式的陷阱](https://docs.searxng.org/admin/#uwsgi-tyrant-mode-pitfalls) ）。值得知道的是；debian（ubuntu）采用完全不同的方法，请阅读 [Debian 的 uWSGI 布局](https://docs.searxng.org/admin/#debian-s-uwsgi-layout) 。

### [Debian 的 uWSGI 布局](https://docs.searxng.org/admin/#id9) [¶](https://docs.searxng.org/admin/#debian-s-uwsgi-layout "Link to this heading")

请注意，Debian 的 uWSGI 布局与标准的 uWSGI 配置有很大不同。您熟悉 [Debian 的 Apache 布局](https://docs.searxng.org/admin/installation-apache.html#debian-s-apache-layout)吗？.. 他们对 uWSGI 基础设施也做了类似的事情。文件夹包括：

/etc/uwsgi/apps\-available/
/etc/uwsgi/apps\-enabled/

  
[uWSGI ini 文件](https://uwsgi-docs.readthedocs.io/en/latest/Configuration.html#ini-files)是通过符号链接启用的：

ln \-s /etc/uwsgi/apps\-available/searxng.ini /etc/uwsgi/apps\-enabled/

更多详细信息可以在 [uwsgi.README.Debian](https://salsa.debian.org/uwsgi-team/uwsgi/-/raw/debian/latest/debian/uwsgi.README.Debian) 中找到。 ( `/usr/share/doc/uwsgi/README.Debian.gz` ). 在 Debian 上你需要知道的某些命令：

Commands recognized by init.d script
====================================

You can issue to init.d script following commands:
  \* start        | starts daemon
  \* stop         | stops daemon
  \* reload       | sends to daemon SIGHUP signal
  \* force-reload | sends to daemon SIGTERM signal
  \* restart      | issues 'stop', then 'start' commands
  \* status       | shows status of daemon instance (running/not running)

'status' command must be issued with exactly one argument: '<confname>'.

Controlling specific instances of uWSGI
=======================================

You could control specific instance(s) by issuing:

    SYSTEMCTL\_SKIP\_REDIRECT=1 service uwsgi <command> <confname> <confname>...

where:
  \* <command> is one of 'start', 'stop' etc.
  \* <confname> is the name of configuration file (without extension)

For example, this is how instance for /etc/uwsgi/apps-enabled/hello.xml is
started:

    SYSTEMCTL\_SKIP\_REDIRECT=1 service uwsgi start hello

## [uWSGI 维护](https://docs.searxng.org/admin/#id10) [¶](https://docs.searxng.org/admin/#uwsgi-maintenance "Link to this heading")

\# init.d --> /usr/share/doc/uwsgi/README.Debian.gz
\# For uWSGI debian uses the LSB init process, this might be changed
\# one day, see https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=833067

create     /etc/uwsgi/apps-available/searxng.ini
enable:    sudo \-H ln \-s /etc/uwsgi/apps-available/searxng.ini /etc/uwsgi/apps-enabled/
start:     sudo \-H service uwsgi start   searxng
restart:   sudo \-H service uwsgi restart searxng
stop:      sudo \-H service uwsgi stop    searxng
disable:   sudo \-H rm /etc/uwsgi/apps-enabled/searxng.ini

\# systemd --> /usr/lib/systemd/system/uwsgi@.service
\# For uWSGI archlinux uses systemd template units, see
\# - http://0pointer.de/blog/projects/instances.html
\# - https://uwsgi-docs.readthedocs.io/en/latest/Systemd.html#one-service-per-app-in-systemd

create:    /etc/uwsgi/searxng.ini
enable:    sudo \-H systemctl enable   uwsgi@searxng
start:     sudo \-H systemctl start    uwsgi@searxng
restart:   sudo \-H systemctl restart  uwsgi@searxng
stop:      sudo \-H systemctl stop     uwsgi@searxng
disable:   sudo \-H systemctl disable  uwsgi@searxng

\# systemd --> /usr/lib/systemd/system/uwsgi.service
\# The unit file starts uWSGI in emperor mode (/etc/uwsgi.ini), see
\# - https://uwsgi-docs.readthedocs.io/en/latest/Emperor.html

create:    /etc/uwsgi.d/searxng.ini
restart:   sudo \-H touch /etc/uwsgi.d/searxng.ini
disable:   sudo \-H rm /etc/uwsgi.d/searxng.ini

## [uWSGI 安装](https://docs.searxng.org/admin/#id11) [¶](https://docs.searxng.org/admin/#uwsgi-setup "Link to this heading")

根据您的发行版创建配置 ini 文件并重启 uwsgi 应用程序。如下所示， [安装脚本](https://docs.searxng.org/admin/installation-scripts.html#installation-scripts) 默认安装一个监听套接字的 uWSGI 配置。

\# -\*- mode: conf; coding: utf-8  -\*-
\[uwsgi\]

\# uWSGI core
\# ----------
#
\# https://uwsgi-docs.readthedocs.io/en/latest/Options.html#uwsgi-core

\# Who will run the code / Hint: in emperor-tyrant mode uid & gid setting will be
\# ignored \[1\].  Mode emperor-tyrant is the default on fedora (/etc/uwsgi.ini).
#
\# \[1\] https://uwsgi-docs.readthedocs.io/en/latest/Emperor.html#tyrant-mode-secure-multi-user-hosting
#
uid \= searxng
gid \= searxng

\# set (python) default encoding UTF-8
env \= LANG\=C.UTF-8
env \= LANGUAGE\=C.UTF-8
env \= LC\_ALL\=C.UTF-8

\# chdir to specified directory before apps loading
chdir \= /usr/local/searxng/searxng-src/searx

\# SearXNG configuration (settings.yml)
env \= SEARXNG\_SETTINGS\_PATH\=/etc/searxng/settings.yml

\# disable logging for privacy
disable-logging \= true

\# The right granted on the created socket
chmod-socket \= 666

\# Plugin to use and interpreter config
single-interpreter \= true

\# enable master process
master \= true

\# load apps in each worker instead of the master
lazy-apps \= true

\# load uWSGI plugins
plugin \= python3,http

\# By default the Python plugin does not initialize the GIL.  This means your
\# app-generated threads will not run.  If you need threads, remember to enable
\# them with enable-threads.  Running uWSGI in multithreading mode (with the
\# threads options) will automatically enable threading support. This \*strange\*
\# default behaviour is for performance reasons.
enable-threads \= true

\# Number of workers (usually CPU count)
workers \= %k
threads \= 4

\# plugin: python
\# --------------
#
\# https://uwsgi-docs.readthedocs.io/en/latest/Options.html#plugin-python

\# load a WSGI module
module \= searx.webapp

\# set PYTHONHOME/virtualenv
virtualenv \= /usr/local/searxng/searx-pyenv

\# add directory (or glob) to pythonpath
pythonpath \= /usr/local/searxng/searxng-src

\# speak to upstream
\# -----------------

socket \= /usr/local/searxng/run/socket
buffer-size \= 8192

offload-threads \= %k

\# -\*- mode: conf; coding: utf-8  -\*-
\[uwsgi\]

\# uWSGI core
\# ----------
#
\# https://uwsgi-docs.readthedocs.io/en/latest/Options.html#uwsgi-core

\# Who will run the code
uid \= searxng
gid \= searxng

\# set (python) default encoding UTF-8
env \= LANG\=C.UTF-8
env \= LANGUAGE\=C.UTF-8
env \= LC\_ALL\=C.UTF-8

\# chdir to specified directory before apps loading
chdir \= /usr/local/searxng/searxng-src/searx

\# SearXNG configuration (settings.yml)
env \= SEARXNG\_SETTINGS\_PATH\=/etc/searxng/settings.yml

\# disable logging for privacy
logger \= systemd
disable-logging \= true

\# The right granted on the created socket
chmod-socket \= 666

\# Plugin to use and interpreter config
single-interpreter \= true

\# enable master process
master \= true

\# load apps in each worker instead of the master
lazy-apps \= true

\# load uWSGI plugins
plugin \= python

\# By default the Python plugin does not initialize the GIL.  This means your
\# app-generated threads will not run.  If you need threads, remember to enable
\# them with enable-threads.  Running uWSGI in multithreading mode (with the
\# threads options) will automatically enable threading support. This \*strange\*
\# default behaviour is for performance reasons.
enable-threads \= true

\# Number of workers (usually CPU count)
workers \= %k
threads \= 4

\# plugin: python
\# --------------
#
\# https://uwsgi-docs.readthedocs.io/en/latest/Options.html#plugin-python

\# load a WSGI module
module \= searx.webapp

\# set PYTHONHOME/virtualenv
virtualenv \= /usr/local/searxng/searx-pyenv

\# add directory (or glob) to pythonpath
pythonpath \= /usr/local/searxng/searxng-src

\# speak to upstream
\# -----------------

socket \= /usr/local/searxng/run/socket
buffer-size \= 8192

offload-threads \= %k

\# -\*- mode: conf; coding: utf-8  -\*-
\[uwsgi\]

\# uWSGI core
\# ----------
#
\# https://uwsgi-docs.readthedocs.io/en/latest/Options.html#uwsgi-core

\# Who will run the code / Hint: in emperor-tyrant mode uid & gid setting will be
\# ignored \[1\].  Mode emperor-tyrant is the default on fedora (/etc/uwsgi.ini).
#
\# \[1\] https://uwsgi-docs.readthedocs.io/en/latest/Emperor.html#tyrant-mode-secure-multi-user-hosting
#
uid \= searxng
gid \= searxng

\# set (python) default encoding UTF-8
env \= LANG\=C.UTF-8
env \= LANGUAGE\=C.UTF-8
env \= LC\_ALL\=C.UTF-8

\# chdir to specified directory before apps loading
chdir \= /usr/local/searxng/searxng-src/searx

\# SearXNG configuration (settings.yml)
env \= SEARXNG\_SETTINGS\_PATH\=/etc/searxng/settings.yml

\# disable logging for privacy
disable-logging \= true

\# The right granted on the created socket
chmod-socket \= 666

\# Plugin to use and interpreter config
single-interpreter \= true

\# enable master process
master \= true

\# load apps in each worker instead of the master
lazy-apps \= true

\# load uWSGI plugins
plugin \= python3,http

\# By default the Python plugin does not initialize the GIL.  This means your
\# app-generated threads will not run.  If you need threads, remember to enable
\# them with enable-threads.  Running uWSGI in multithreading mode (with the
\# threads options) will automatically enable threading support. This \*strange\*
\# default behaviour is for performance reasons.
enable-threads \= true

\# Number of workers (usually CPU count)
workers \= %k
threads \= 4

\# plugin: python
\# --------------
#
\# https://uwsgi-docs.readthedocs.io/en/latest/Options.html#plugin-python

\# load a WSGI module
module \= searx.webapp

\# set PYTHONHOME/virtualenv
virtualenv \= /usr/local/searxng/searx-pyenv

\# add directory (or glob) to pythonpath
pythonpath \= /usr/local/searxng/searxng-src

\# speak to upstream
\# -----------------

socket \= /usr/local/searxng/run/socket
buffer-size \= 8192

offload-threads \= %k

## [暴君模式的陷阱](https://docs.searxng.org/admin/#id12) [¶](https://docs.searxng.org/admin/#pitfalls-of-the-tyrant-mode "Link to this heading")

在[暴君模式](https://uwsgi-docs.readthedocs.io/en/latest/Emperor.html#tyrant-mode-secure-multi-user-hosting)中，进程所有者和组的实现有些不寻常，需要特别考虑。在 [暴君模式](https://uwsgi-docs.readthedocs.io/en/latest/Emperor.html#tyrant-mode-secure-multi-user-hosting)中，皇帝将使用从属配置文件的 UID/GID 来运行从属（即应用的 `.ini` 文件的用户和组）。

  
如果没有在 `/etc/uwsgi.ini` 中设置选项 `emperor-tyrant-initgroups=true` ，进程将不会获得额外的组，但这个选项在 2.0.x 分支中不可用（参见 [#2099@uWSGI](https://github.com/unbit/uwsgi/issues/2099)），功能 [#752@uWSGI](https://github.com/unbit/uwsgi/pull/752) 已于 2014 年 10 月合并到 uWSGI 的主分支，但从未发布；最后一个主要发布版本是 2013 年 12 月发布的，之后只有错误修复版本（参见 [#2425uWSGI](https://github.com/unbit/uwsgi/issues/2425)）。简而言之：

> **在暴君模式下，无法获得额外的组，并且 uWSGI 进程缺少可能需要的额外权限。**

例如在 Fedora（RHEL）上：如果你尝试安装 valkey DB 使用套接字 通信，并且你想从 SearXNG uWSGI 连接到它，你会看到 *权限被拒绝* 在您的实例日志中：

ERROR:searx.valkeydb: \[searxng (993)\] can't connect valkey DB ...
ERROR:searx.valkeydb:   Error 13 connecting to unix socket: /usr/local/searxng-valkey/run/valkey.sock. Permission denied.
ERROR:searx.plugins.limiter: init limiter DB failed!!!

即使将 uWSGI 进程的 *searxng* 用户添加到其他组以获取对 valkey DB 套接字访问权限：

$ groups searxng
searxng : searxng searxng-valkey

要查看 uWSGI 进程的有效组，您需要查看进程状态，例如：

$ ps -aef | grep '/usr/sbin/uwsgi --ini searxng.ini'
searxng       93      92  0 12:43 ?        00:00:00 /usr/sbin/uwsgi --ini searxng.ini
searxng      186      93  0 12:44 ?        00:00:01 /usr/sbin/uwsgi --ini searxng.ini

这里可以看到 PID 186 的附加“组”未设置（缺少 `searxng-valkey` 的 gid）：

$ cat /proc/186/task/186/status
...
Uid:      993     993     993     993
Gid:      993     993     993     993
FDSize:   128
Groups:
...