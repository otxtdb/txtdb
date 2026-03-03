---
title: "SearXNG 维护"
source: "https://docs.searxng.org/admin/update-searxng.html"
author:
published:
created: 2026-03-01
description:
tags:
  - "clippings"
taxonomy: { doc_category: [searxng] }
---

进一步阅读

- [DevOps 工具箱](https://docs.searxng.org/utils/index.html#toolboxing)
- [uWSGI 维护](https://docs.searxng.org/admin/installation-uwsgi.html#uwsgi-maintenance)

- [如何更新](https://docs.searxng.org/admin/#how-to-update)
- [如何检查和调试](https://docs.searxng.org/admin/#how-to-inspect-debug)
- [迁移并保持关注！](https://docs.searxng.org/admin/#migrate-and-stay-tuned)
	- [安装后检查](https://docs.searxng.org/admin/#check-after-installation)

## [如何更新](https://docs.searxng.org/admin/#id3) [¶](https://docs.searxng.org/admin/#how-to-update "Link to this heading")

  
如何更新取决于[安装](https://docs.searxng.org/admin/installation.html#installation)方法。如果你使用的是 [安装脚本](https://docs.searxng.org/admin/installation-scripts.html#installation-scripts) ，使用来自 [utils/searxng.sh](https://docs.searxng.org/utils/searxng.sh.html#searxng-sh) 的 update 命令 script.

sudo \-H ./utils/searxng.sh instance update

## [如何检查和调试](https://docs.searxng.org/admin/#id4) [¶](https://docs.searxng.org/admin/#how-to-inspect-debug "Link to this heading")

  
如何调试取决于[安装](https://docs.searxng.org/admin/installation.html#installation)方法。如果你使用的是 [安装脚本](https://docs.searxng.org/admin/installation-scripts.html#installation-scripts) ，使用来自 [utils/searxng.sh](https://docs.searxng.org/utils/searxng.sh.html#searxng-sh) 的 inspect 命令 script.

sudo \-H ./utils/searxng.sh instance inspect

## [迁移并保持关注！](https://docs.searxng.org/admin/#id5)[¶](https://docs.searxng.org/admin/#migrate-and-stay-tuned "Link to this heading")

info

- [PR 1332](https://github.com/searxng/searxng/pull/1332)
- [PR 456](https://github.com/searxng/searxng/pull/456)
- [关于滚动发布](https://github.com/searxng/searxng/pull/446#issuecomment-954730358)

SearXNG 是一个*滚动发布*项目；对主分支的每次提交都会产生一个新版本。SearXNG 发展迅速，服务和机会不断变化，例如：

- Bot 防护已从 filtron 切换到 SearXNG 的 [limiter](https://docs.searxng.org/admin/searx.limiter.html#limiter)，这需要使用 [Valkey](https://docs.searxng.org/admin/settings/settings_valkey.html#settings-valkey) 数据库。

为了及时了解并使用新功能，实例维护者需要定期更新 SearXNG 代码（参见 [如何更新](https://docs.searxng.org/admin/#update-searxng) ）。正如上述例子所示，这并不总是足够的，有时需要设置或重新配置服务，有时也需要卸载不再需要的服务。

在这里，您将找到一份影响基础设施的变更列表。请检查更新您的安装的必要性：

[PR 1595](https://github.com/searxng/searxng/pull/1595): `[fix] uWSGI: increase buffer-size`

重新安装 uWSGI ([utils/searxng.sh](https://docs.searxng.org/utils/searxng.sh.html#searxng-sh)) 或手动修复您的 uWSGI `searxng.ini` 文件。

### [安装后检查](https://docs.searxng.org/admin/#id6) [¶](https://docs.searxng.org/admin/#check-after-installation "Link to this heading")

完成安装后，你可以运行 SearXNG 的 *检查* 程序，查看是否有残留的文件。在这个例子中存在一个 *旧的* `/etc/searx/settings.yml`：

$ sudo -H ./utils/searxng.sh instance check

SearXNG checks
--------------
ERROR: settings.yml in /etc/searx/ is deprecated, move file to folder /etc/searxng/
...
INFO    searx.valkeydb                 : connecting to Valkey db=0 path='/usr/local/searxng-valkey/run/valkey.sock'
INFO    searx.valkeydb                 : connected to Valkey