---
title: "Erphpdown 使用教程"
source: "https://www.mobantu.com/6658.html"
author:
published: 2016-10-18
created: 2025-12-07
description: "在本站购买下载了erphpdown wordpress下载插件之后，解压压缩包，看到一个erphpdown.zip，在网站后台（插件-安装插件）上传erphpdown.zip安装包，或者解压erphpdown.zip通过FTP/SFTP上传到网站目录（/wp-content/plugins/）下，然后启用插件。  以后升级插件是在本站下载最新版后直接FTP覆盖即可，不会影响网站数据。  启用插件后，后台左侧会出现一个Erphpdown菜"
tags: "clippings"
---

在本站购买下载了erphpdown wordpress下载插件之后，解压压缩包，看到一个erphpdown.zip，在网站后台（插件-安装插件）上传erphpdown.zip安装包，或者解压erphpdown.zip通过FTP/SFTP上传到网站目录（/wp-content/plugins/）下，然后启用插件。

以后升级插件是在本站下载最新版后直接FTP覆盖即可，不会影响网站数据。

启用插件后，后台左侧会出现一个Erphpdown菜单，设置下 **基础设置**、**支付设置**、**显示设置**、**VIP设置**，然后发布文章的时候你会在编辑框下面看到Erphpdown属性来设置下载信息的选项。

如果你需要采集，请看https://www.mobantu.com/9107.html

### 具体截图：（看不清楚的可以把图片下载下来看）

图片下载链接: https://pan.baidu.com/s/1Ljz73c10-I3jtrB3aPCXaA?pwd=ivy6 提取码: ivy6

1、基础设置

![](https://img.mobantu.net/uploads/erphpdown-0.png)

2、前端设置

![](https://img.mobantu.net/uploads/erphpdown-2.png)

3、发布文章资源

![](https://img.mobantu.net/uploads/erphpdown-3.png)

支付接口设置与VIP价格设置请基于自己的需要设置即可。

4、发卡功能

发布文章时，收费模式选发卡，然后设置一个价格，最后在erphpdown菜单里添加对应的激活码（卡密）**必须开启插件里的激活码发放扩展（erphpdown-基础设置 里面的免费扩展，勾选激活码发放，然后刷新页面，erphpdown菜单里会出现添加激活码的地方，激活码是绑定给文章ID的）**。

**你还需要安装一个SMTP插件，配置网站发邮件功能，这样才能自动发卡到用户邮箱。**

开启激活码发放扩展：

![](https://img.mobantu.net/uploads/erphpdown-faka2.png)

开启后，左边的erphpdown菜单里会出现一个添加激活码的子菜单，点进来添加激活码：（文章ID就是你要卖发卡而发布的那篇文章的ID）

![](https://img.mobantu.net/uploads/erphpdown-faka3.png)

发布文章：

![](https://img.mobantu.net/uploads/erphpdown-faka1.png)

### 短代码：

\[erphpdown\_sc\_user\] //整个个人中心，你可以直接新建页面，内容填上此短代码，那么就会显示整个个人中心的内容  
\[erphpdown\_sc\_vip\_page\] //独立VIP升级页面，支持弹窗购买  
下面是个人中心里的单个模块  
\[erphpdown\_sc\_order\_down\] //已购商品  
\[erphpdown\_sc\_my\] //我的资产  
\[erphpdown\_sc\_ref\] //我的推广  
\[erphpdown\_sc\_ref\_down\] //推广下载  
\[erphpdown\_sc\_ref\_vip\] //推广vip  
\[erphpdown\_sc\_sell\] //销售订单  
\[erphpdown\_sc\_recharges\] //充值记录  
\[erphpdown\_sc\_recharge\] //充值  
\[erphpdown\_sc\_recharge\_card\] //充值卡  
\[erphpdown\_sc\_mycred\] //mycred积分兑换  
\[erphpdown\_sc\_withdraw\] //取现申请  
\[erphpdown\_sc\_withdraws\] //取现列表  
\[erphpdown\_sc\_order\_vip\] //VIP订单  
\[erphpdown\_sc\_vip\] //余额升级VIP  
\[erphpdown\_sc\_vip\_pay\] //支付升级VIP  
\[erphpdown\_sc\_info\] //个人资料

\[erphpdown\_sc\_tuan\] //团购订单 需安装扩展  
\[erphpdown\_sc\_ad\] //广告订单 需安装扩展

**以上短代码为v15.0+的新短代码**。使用方法：新建页面，在可视化编辑下输入以上短代码即可。例如输入 \[erphpdown\_sc\_order\_down\] 即可是已购商品的页面。