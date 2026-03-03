---
title: "SearXNG：从服务器的 IP 地址回答验证码"
source: "https://docs.searxng.org/admin/answer-captcha.html"
author:
published:
created: 2026-03-01
description:
tags:
  - "clippings"
taxonomy: { doc_category: [searxng] }
---

通过 SSH 隧道，我们可以从服务器的 IP 地址发送请求并解决一个验证码， 阻止此 IP 的请求。如果您的 SearXNG 实例托管在 `example.org`，并且你的登录名是 `user`，你可以简单地设置代理 [ssh](https://manpages.debian.org/jump?q=ssh):

\# SOCKS server: socks://127.0.0.1:8080

$ ssh \-q \-N \-D 8080 user@example.org

上述的 `socks://localhost:8080` 可以通过以下方式测试：

$ curl \-x socks://127.0.0.1:8080 http://ipecho.net/plain
n.n.n.n

$ curl http://ipecho.net/plain
x.x.x.x

在 WEB 浏览器的设置中打开 *"网络设置"*，并在 `SOCKS5 127.0.0.1:8080` 上设置代理（见下图）。在 WEB 浏览器中检查服务器使用的 IP：

- [http://ipecho.net/plain](http://ipecho.net/plain)

现在打开屏蔽你服务器 IP 请求的搜索引擎。如果你在使用 [qwant 引擎](https://github.com/searxng/searxng/issues/2011#issuecomment-1553317619)时遇到问题，请从 [qwant.com](https://www.qwant.com/) 解决验证码。

---

![FFox proxy on SOCKS5, 127.0.0.1:8080](https://docs.searxng.org/_images/ffox-setting-proxy-socks.png)

图 1 Firefox 的网络设置 [¶](https://docs.searxng.org/admin/#id1 "Link to this image")

[ssh](https://manpages.debian.org/jump?q=ssh) 手册：

\-D \[bind\_address:\]port

指定本地“动态”应用级端口转发。它通过在本地侧分配一个套接字来监听端口来实现。每当有连接建立到这个端口时，连接将通过安全通道转发，然后使用应用协议来确定从远程机器连接到何处。ssh 将充当 SOCKS 服务器。

\-N

不要执行远程命令。这对于仅转发端口很有用。