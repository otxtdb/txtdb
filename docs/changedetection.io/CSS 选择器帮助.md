---
title: "CSS 选择器帮助"
source: "https://github.com/dgtlmoon/changedetection.io/wiki/CSS-Selector-help"
author:
  - "[[GitHub]]"
published:
created: 2025-12-01
description: "Best and simplest tool for website change detection, web page monitoring, and website change alerts. Perfect for tracking content changes, price drops, restock alerts, and website defacement monitoring—all for free or enjoy our SaaS plan! - CSS Selector help · dgtlmoon/changedetection.io Wiki"
tags:
  - "clippings"
---


  
什么是 CSS 选择器？请阅读 [https://developer.mozilla.org/en-US/docs/Learn/CSS/Building\_blocks/Selectors](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors)

  
在 CSS 选择器过滤器字段中，你输入的是 **CSS 选择器** —— *而不是 HTML。*

  
比如说，如果 HTML 是

<div class\="points"\>
  <span id\="interesting"\>
  57 points
  </span\>
</div\>

  
选择器为 `.点 #interesting`

在这个例子中

<span class\="chapter lastchapter"\>
  Chapter 53
</span\>

  
这三个选择器将匹配：`.chapter`、`.lastchapter`、`.chapter.lastchapter`。最后一个只有当两个 CSS 类别匹配时才会匹配。 .` 章节最后一章`在这里是错误的。

#   
用 xpath 只从 `<A>` 标签中提取/提取 HREF如果你有

```
<h3>
  <a href..></a>
</h3>
```

  
筛选：`H3/parent：：a//@href`

#   
只用 xPath 过滤器选择所有 img“src”标签```
//img//@src
```

  
选择所有 `img``src` 标签，并将其设置为文本列表

```
xpath:string-join(//img/@src, codepoints-to-string(10))
```

#   
只选择某事的第一个实例```
xpath:(//h3[contains(@class, 'PagePromo-title')])[1]
```

  
这只选择包含 PagePromo-title 类的 h3 的第一个实例

#   
按数据选择 `——` 来源```
<div data-test-id="productSizeList"...
```

`//div[@data-test-id = 'productSizeList']`

#   
xPath 和非拉丁文本出现混乱  
这个问题很可能在 [https://github.com/dgtlmoon/changedetection.io/issues/3658](https://github.com/dgtlmoon/changedetection.io/issues/3658) 修复:)

  
`xpath：` 类型过滤器和非 UTF8 无法兼容，如果你发现文本被打乱成 `Нема планираних искључења.` 变成 `Ð�ÐµÐ¼Ð° Ð¿Ð»Ð°Ð½Ð¸Ñ�Ð°Ð½Ð¸Ñ Ð¸Ñ�ÐºÑ�Ñ�Ñ�ÐµÑ�Ð°.` ，那么你应该将 xPath 过滤器转换为 CSS [https://extendsclass.com/xpath-to-css.html](https://extendsclass.com/xpath-to-css.html)

  
例如 [#1546](https://github.com/dgtlmoon/changedetection.io/issues/1546)