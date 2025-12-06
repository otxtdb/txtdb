---
title: "Erphplogin Pro 连接QQ/微博/微信登录/弹窗登录"
source: "https://www.mobantu.com/7548.html"
author:
published: 2018-10-31
created: 2025-12-07
description: "Erphplogin Pro是一款由模板兔开发的wordpress网站用户通过QQ、微博、微信扫码以及弹窗来进行登录的wordpress中文插件。微信登录的接口是微信开发者平台的接口，扫码登录。  本插件不仅实现了社交登录功能，还有弹窗登录功能（由于弹窗是js触发，所以需要绑定class有erphp-login-must的元素），如果需要显示用户社交头像，请获取用户user_meta为avatar的值即可。需要深度集成到主题里或者修改U"
tags: "clippings"
---

![](https://img.mobantu.net/uploads/erphplogin.png)

Erphplogin Pro是一款由[模板兔](https://www.mobantu.com/ "模板兔")开发的wordpress网站用户通过QQ、微博、微信扫码以及弹窗来进行登录的wordpress中文插件。微信登录的接口是微信开发者平台的接口，扫码登录。

本插件不仅实现了社交登录功能，还有**弹窗登录**功能（由于弹窗是js触发，所以需要绑定class有erphp-login-must的元素），如果需要显示用户社交头像，请获取用户user\_meta为avatar的值即可。需要深度集成到主题里或者修改UI界面请联系我们二次开发。如果想在其他地方显示社交登录图标，可在源码里把以下PHP代码加在需要调用社交登录的地方：  
<?php echo get\_erphplogin();?>

我们不免费提供帮忙修改主题集成弹窗登录，请自行加对应的class即可。

**此插件可直接让erphpdown未登录状态时的登录按钮实现弹窗登录。**

### 使用说明：

在QQ互联那边有个回调地址需要填写：http(s)//域名/wp-content/plugins/erphplogin/auth/qq-callback.php

微博开发平台那边也需要填写回调地址：http(s)//域名/wp-content/plugins/erphplogin/auth/sina-callback.php

不是插件设置的返回页面，而是申请接口时需要填写的。

前台调用绑定：

<?php if(function\_exists('get\_erphplogin\_bind')) echo get\_erphplogin\_bind();?>