---
title: "处理被监视 URL 中的变量"
source: "https://github.com/dgtlmoon/changedetection.io/wiki/Handling-variables-in-the-watched-URL"
author:
  - "[[GitHub]]"
published:
created: 2025-12-01
description: "Best and simplest tool for website change detection, web page monitoring, and website change alerts. Perfect for tracking content changes, price drops, restock alerts, and website defacement monitoring—all for free or enjoy our SaaS plan! - Handling variables in the watched URL · dgtlmoon/changedetection.io Wiki"
tags:
  - "clippings"
---


  
在 [1057](https://github.com/dgtlmoon/changedetection.io/pull/1057) 中，我们增加了在 URL 中使用 Jinja2 模板的功能，利用 [Jinja2 时间扩展](https://pypi.org/project/jinja2-time/) ，你可以指定日期（例如根据你的时区的当前日期）或相对日期（例如，昨天日期和一个月后的日期）

  
比如，对于需要在不同日期之间搜索的网站来说，这非常合适。

  
有时你需要在请求的 URL 中插入当前日期，这可以通过 *Jinja2* 模板语法实现，你也可以使用任何其他 Jinja2 语法（例如，如果日期是星期二，可以插入单词“foobar”之类的）。

```
https://changedetection.io/test.txt?date={% now 'Europe/Berlin', '%d' %}.{% now 'Europe/Berlin', '%m' %}.{% now 'Europe/Berlin', '%Y' %}
```

  
我会请求 `（根据欧洲/柏林）时`区

```
https://changedetection.io/test.txt?date=24.10.2022
```

  
公认时区列表 [https://en.wikipedia.org/wiki/List\_of\_tz\_database\_time\_zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)

  
日期格式代码列表（如 `%d` 等）[https://docs.python.org/3/library/datetime.html#strftime-and-strptime-format-codes](https://docs.python.org/3/library/datetime.html#strftime-and-strptime-format-codes)