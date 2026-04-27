---
title: "sing-box 脚本 no-auto-tls 参数帮助说明"
source: "https://233boy.com/sing-box/no-auto-tls/"
author:
published: 2024-05-22
created: 2026-04-25
description: "如果你想要手动配置 TLS，请使用 no-auto-tls 参数来添加配置，例如你想要用 NGINX 实现 TLS"
tags:
  - "clippings"
taxonomy: { doc_category: [fq] }
---
2024-05-22 18:13

如果你想要手动配置 TLS，请使用 no-auto-tls 参数来添加配置，例如你想要用 NGINX 实现 TLS

## 前言

考虑到有些人不方便使用 Caddy 实现自动 TLS，比如已使用 NGINX 跑了自己的博客，又或者觉得 Caddy 性能不够好之类等…

sing-box 脚本自带了一个 no-auto-tls 参数可以让你非常方便的让你来手动配置 TLS

## 备注

此处说的手动配置 TLS，指的是使用 WEB 程序转发 ws/h2/htt
pupgrade 流量到 sing-box

## 添加一个配置

使用 `sing-box no-auto-tls` 添加一个配置，会生成类似如下图片所示的内容

![](https://vip2.loli.io/2023/05/11/3LgWH5rEA8t1JXZ.png)

可以在 `no-auto-tls INFO` 找到端口和路径

有了 `端口` 和 `路径` 参数，你就可以自己来手动配置 TLS，将相关的路径流量转发到 `127.0.0.1:端口` 即可

如图片上的 VLESS-WS-TLS 协议可以参考使用 [此 NGINX 配置模板](https://github.com/XTLS/Xray-examples/blob/main/VLESS-WSS-Nginx/nginx.conf)

其他配置模板？都手动了，你手动一下吧

## 提醒

no-auto-tls INFO 这个配置信息可以使用 `sb info tls` 指令查看配置的时候会自动显示

或者你也可以使用 `sb debug tls` 指令来查看，你可以找到 port 和 path 相关的信息

## 缺点

都说了嘛，手动

所以如果你改了路径之类，又得自己来手动配置一次。

## 懂的都懂

不要好奇为什么显示配置的时候端口会是 443，而 no-auto-tls INFO 下面又是不同的端口。

## 结束

我不喜欢用 NGINX，比起性能的差异我更加在乎如何更快的解决问题

可曾几何时，又啃了全套的 NGINX 文档…

人生苦短，省时省力，才是王道！