---
title: "sing-box 脚本 DNS 设置"
source: "https://233boy.com/sing-box/sing-box-dns/"
author:
published: 2024-05-22
created: 2026-04-25
description: "sing-box 脚本可以非常快速设置DNS，一键配置 DNS DOH 加密以及屏蔽色情网站，或者自定义DNS。"
tags:
  - "clippings"
taxonomy: { doc_category: [fq] }
---
sing-box 脚本可以非常快速设置DNS，一键配置 DNS DOH 加密以及屏蔽色情网站，或者自定义DNS。

## 前言

DNS 是联网的开始，有些时候上网不了，或许就是你的 DNS 崩了，不过我们现在暂不讨论客户端DNS

默认情况下，DNS 是通过 53 端口 UDP 协议出去查询的，简单说就是，查询的过程中是透明的，没有加密的，VPS 服务商或者网络提供者是可以看到你查询了什么域名的，所以如果在乎隐私的，那么使用 DNS DOH 方式来查询是非常有必要的。

使用 DNS DOH 方式就不用担心别人能看到你查询了哪些域名了。

当然，其实加密查询比较适合强迫症选手，但是考虑到保护隐私，个人是推荐大家优先使用 dns doh 方式的

sing-box 脚本同时提供 DNS IP 方式，或者 DNS DOH (HTTP/3)方式，你也可以自定义 DNS。

## 设置DNS

输入 `sing-box dns` 即可选择相关 DNS

![sing-box DNS 设置](https://cdn.sa.net/2024/05/22/Kc4de8movHfONPX.png)

set 选项是可以自定义 DNS，

none 选项是不配置任何 DNS

## google

快速设置 Google DNS: `sing-box dns 88`

快速设置 Google DNS DOH: `sing-box dns gg`

## cloudflare

快速设置 Cloudflare DNS: `sing-box dns 11`

快速设置 Cloudflare DNS DOH: `sing-box dns cf`

## nosex

快速设置 Cloudflare Family DNS DOH: `sing-box dns nosex`

备注，使用此方式，将无法打开小电影网站（提供给有特殊需求的时候使用

## set

快速自定义 DNS 使用 9.9.9.9：`sing-box dns set 9.9.9.9`

快速自定义使用 ADGUARD DNS DOH：`sing-box dns set https://dns.adguard-dns.com/dns-query`

使用 `sing-box dns set` 可以手动输入 DNS 值，

或者 `sing-box dns set 1.1.1.1` 直接指定使用 1.1.1.1 作为 DNS，后面的 1.1.1.1 可以自定义成任何你喜欢的 DNS

## none

如果你出现任何问题，请使用 `sing-box dns none` 来重置 DNS 配置

或者如果你想要 sing-box 走系统 DNS，也使用此命令

## 结束

理论上只要记得 `sing-box dns nosex` 这个命令就行（戒色第一天，day1 day1

啊这，别手残自定义使用国内的 DNS。
