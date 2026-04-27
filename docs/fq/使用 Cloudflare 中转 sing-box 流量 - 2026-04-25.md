---
title: 使用 Cloudflare 中转 sing-box 流量
source: https://233boy.com/sing-box/sing-box-cloudflare/
author:
published: 2024-05-22
created: 2026-04-25
description: 使用 Cloudflare 中转 sing-box 流量可以避免 IP 被墙，也可以拯救被封的 IP。
tags:
  - clippings
taxonomy:
  doc_category:
    - fq
---


使用 Cloudflare 中转 sing-box 流量可以避免 IP 被墙，也可以拯救被封的 IP。

## 前言

一般而言，除非真的有需求，要不然不建议套 CF，因为套 CF 中转速度太慢了

使用 Cloudflare 中转的速度相对来说是比较慢的，这个是因为线路的问题，无解。

但是使用移动网络的话，可能会使用 Cloudflare 香港节点，理论上会有不错的速度

只有担心 IP 被墙或者 IP 已经被封了，才建议套 CF 中转流量。

## 安装脚本

如果已安装，跳过此部分

登录你的 VPS；执行下面的命令：

```
bash <(wget -qO- -o- https://github.com/233boy/sing-box/raw/main/install.sh)
```

如果安装成功，继续

## 准备

必须拥有一个域名。

打开：[https://dash.cloudflare.com/sign-up](https://dash.cloudflare.com/sign-up)

注册一个 Cloudflare 账号，有账号的话你就登录啊

## 添加域名

注册成功后，登录

为方便理解，可以在 Cloudflare 后台将语言切换成简体中文；并点击添加站点

![切换中文](https://vip2.loli.io/2023/05/25/yQ3WcnV7HfXN1uL.png)

然后，输入你的域名，添加站点

![添加站点](https://vip2.loli.io/2023/05/25/feBEkxsCNRGm3Sq.png)

选择 Free 计划，继续

![Free 计划](https://vip2.loli.io/2023/05/25/LSWA1ilDhjBy5ce.png)

我们现在就添加一个 DNS 记录，名称：`ai`，IPv4 地址：`写你的 VPS IP`，代理状态必须关闭，云朵图标为灰色。

提示：你可以使用 `sing-box ip` 查看你的 VPS IP。

![添加 DNS 记录](https://vip2.loli.io/2023/05/25/OcZ4aVfLtkC8KH1.png)

Cloudflare 会自动扫描域名的 DNS，此处可能会不同的显示，反正确保刚才添加的记录，代理状态为关闭即可，继续

![查看 DNS 记录](https://vip2.loli.io/2023/05/25/AqHRkfBl7gICzZ1.png)

更改域名的 Name Servers 服务器为 Cloudflare 给出两组服务器，不同的域名服务商的操作会有一些不同，此处自己弄

![更改 Name Servers](https://vip2.loli.io/2023/05/25/BKMxYOgku7v2PLV.png)

改完域名的 Name Servers 就点击，`完成，检查名称服务器`

## 等待生效

更改域名的 Name Servers 服务器生效的时间会有延迟的，耐心等待即可

![等待域名生效](https://vip2.loli.io/2023/05/25/TuaQI4LnlFO3DGB.png)

在 Cloudflare 后台主页，如果能看到域名下面显示有 `有效`，那就是生效了

域名生效了，那就是域名正式托管在 Cloudflare 管理。

## 添加中转配置

登录你的 VPS

使用 `sing-box add wss ai.233boy.com` 添加一个 vmess-ws-tls 配置；记得把 `ai.233boy.com` 改成你的域名

就是刚才添加记录的那个域名，假设你的域名是 233boy.com ，添加的名称是 ai，域名就是 ai.233boy.com

![添加中转配置](https://vip2.loli.io/2023/05/25/dheFzQmofSw7i1A.png)

添加成功的话，会显示类似图片的配置

## 开启中转

在 Cloudflare 后台主页，点击你的域名进去，在左侧选项菜单选择 `SSL/TLS`

![设置SSL/TLS：完全](https://vip2.loli.io/2023/05/25/tsxw6HpD2r7ZR1c.png)

将 SSL/TLS 加密模式更改为 `完全`

然后在左侧选项菜单选择 `DNS`

![打开代理状态](https://vip2.loli.io/2023/05/25/AZ89f3BYdKMJ2uX.png)

编辑添加的那个记录，把代理状态打开，即是 `已代理`，云朵图标为点亮状态，然后保存

![代理状态已打开](https://vip2.loli.io/2023/05/25/W1MmVt69sZvQzAu.png)

这是更改后的样子，代理状态，已代理，云朵图标点亮。

## 好了

把云朵点亮之后，流量就是走的 Cloudflare 中转了。

提醒，把云朵点亮就是流量通过 Cloudflare 中转，点灰云朵图标就是直连，不走 Cloudflare 中转。

## 获取真实客户端IP

考虑到有些人会有某些特殊需求，因为套 CF 了默认情况在查看日志的时候会显示客户端 IP 是 CF 的。

如果你需要获取真实的客户端IP，得更改一下 Caddy 的配置

在 /etc/caddy/233boy/xxx.conf 找到你的 caddy 配置文件，（xxx 指的是你的域名）

默认配置类似如下：

```
xxx:443 {
    reverse_proxy /56f7be67-809f-4f47-8cae-9bffa908adf5 127.0.0.1:2333
    import /etc/caddy/233boy/xxx.conf.add
}
```

最终更改的配置如下：

```
xxx:443 {
    reverse_proxy /56f7be67-809f
-4f47-8cae-9bffa908adf5 127.0.0.1:2333 {
        header_up X-Real-IP {header.CF-Connecting-IP}
        header_up X-Forwarded-For {header.CF-Connecting-IP}
    }
    import /etc/caddy/233boy/xxx.conf.add
}
```

原则上，你仅需要更改增加一下 header\_up 选项指定 IP 为 CF 转发就好了，

记得不要瞎改别的啊！

改好了要重启一下 Caddy：`sing-box restart caddy`

## 测速

你看这速度还行吧

![测试中转速度](https://vip2.loli.io/2023/05/25/5QGRJ4qPmOk9nsE.jpg)

不可能，绝对不可能（假的

## 备注

如果你的 VPS 位置是在美国西海岸的话，速度应该还算可以吧，如果不是在美国西海岸，那么也许速度会很慢

不过好在能防止 IP 被墙，或者让 IP 起死回生，也挺好的，难道不是么？

如果你使用移动网络的话，那么 Cloudflare 的中转节点可能会在香港，速度也许会不错 (不完全保证)。

## 其他

添加 DNS 记录的时候，那个名称你可以随便起的，只要解析到你的 VPS IP，添加中转配置时写上你的域名即可

我们只是用了 ai 名称做为示例

## 懂的都懂

文章只是示例了使用 vmess-ws-tls 中转，其他 \*TLS 协议也可以中转的，但是我不想写了，拜托兄弟你头脑灵光一点！星不星呀

提示：记得要在左侧选项菜单 `网络` 里面把所有的选项都打开，比如说 `gRPC`

你也可以换成 vless-ws-tls 协议，可能速度会快一亿亿点哦！

不懂就算了！真是的

## 优化速度

你可以弄优选 Cloudflare IP 啊，我没弄过，也不需要弄，毕竟你看我测速也还行，够用了。

## sing-box 脚本说明

请看：[最好用的 sing-box 一键安装脚本](https://233boy.com/sing-box/sing-box-script/)

哎呀，虽然脚本很好用，但是为了你能更加了解掌握各种使用技巧，还是建议看一虾吧！

## 结束

明明这么简单的东西，看不懂的建议把电脑砸了，然后去报读幼儿园。

复制粘贴我文章的抄袭狗没鸡鸡！