---
title: "WordPress 如何获取支付宝接口信息（私钥、公钥）"
source: "https://www.mobantu.com/7731.html"
author:
published: 2019-03-18
created: 2025-12-07
description: "目前模板兔开发的erphpdown集成了支付宝当面付（erphpdown-支付设置 里的第二个接口）、电脑网站支付（第一个接口）、手机网站支付（第一个接口），可是很多用户签约了当面付接口之后，不知道怎么获取接口信息，下面模板兔给大家讲一下。 申请接口： 首先进 b.alipay.com 登录，然后进到产品中心 https://b.alipay.com/page/product-mall/all-product，这些都是支付接口，我们需要"
tags: "clippings"
---


目前[模板兔](https://www.mobantu.com/ "模板兔")开发的erphpdown集成了**支付宝当面付**（erphpdown-支付设置 里的第二个接口）、**电脑网站支付**（第一个接口）、**手机网站支付**（第一个接口），可是很多用户签约了当面付接口之后，不知道怎么获取接口信息，下面[模板兔](https://www.mobantu.com/ "模板兔")给大家讲一下。

### 申请接口：

首先进 b.alipay.com 登录，然后进到产品中心 https://b.alipay.com/page/product-mall/all-product，这些都是支付接口，我们需要用的是当面付、电脑网站支付、手机网站支付，看你能申请哪个就申请哪个。

![](https://img.mobantu.net/uploads/alipay-products.png)

你选择【当面付】点进去，然后立即开通接入，你会看到让你必须选经营内容与上传店铺招牌，经营内容一般选互联网服务，店铺招牌你在你家附近随便拍一个门面招牌（这个你自由发挥），然后申请就行了。

### 接口申请通过后，如何查看接口：

APPID就不用我说了，就是应用ID，这里主要说【商户应用私钥】与【支付宝公钥】。

进入https://openhome.alipay.com/platform/appManage.htm#/apps，看到应用列表与APPID

![](https://img.mobantu.net/uploads/alipay-product-list.png)

找到指定的应用，点击 查看详情，进来后点击左边的 应用信息，先设置**接口加签方式，加签模式为公钥RSA2**。

点击设置，**加签模式选公钥**。注意，下图里的【应用网关】【服务器IP白名单】【接口内容加密方式】【授权回调地址】都不需要设置！

![](https://img.mobantu.net/uploads/erphpdown-alif2f.png)

私钥生成工具：https://opendocs.alipay.com/common/02kipl 进去后有个【获取工具】，你下载windows或者mac版本，安装。

**应用私钥：**

（此截图可能与你使用的工具界面不一样，但是功能一样）

![](https://img.mobantu.net/uploads/erphpdown-alif2f2.png)

密钥格式选非java适用，如果不行可选java适用重新生成接口试试，都不行的话说明主机环境不兼容接口。

**支付宝公钥：**

把上面截图里获取的**商户应用公钥**填到开放平台接口信息 - 设置应用公钥里，然后就可以获取支付宝公钥了。接口需要填的是**支付宝公钥**，不是应用公钥！

![](https://img.mobantu.net/uploads/erphpdown-alif2f3.jpg)

获取了应用私钥与支付宝公钥，填到erphpdown接口里对应的位置就OK了。下面的可以不用看了，除非你需要重新获取接口。

### 重新获取接口：

假如之前设置过，那么请重新设置一遍，一定要重新设置应用公钥，然后再获取新的支付宝公钥！回调地址不用设置！

接口加签方式：已设置  点击**设置/查看，重新设置应用公钥，再重新获取支付宝公钥**

![](https://img.mobantu.net/uploads/f2fpay-5.jpg)

PHP版本请使用5.6以上，确保PHP环境开启了http、curl模块功能，网站不能使用页面缓存或相关CDN缓存或防火墙。

注意：有可能出现接口是对的，可是网站主机的PHP环境的某些模块没有开启也会导致无法显示二维码，目前为止模板兔帮用户调试了部分主机，发现有些主机（cPanel）PHP环境没有开启http模块，经开启后解决了问题，部分windows主机环境不兼容支付宝当面付接口。