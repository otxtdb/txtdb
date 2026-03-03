---
title: "SearXNG：搜索语法"
source: "https://docs.searxng.org/user/search-syntax.html"
author:
published:
created: 2026-03-01
description:
tags:
  - "clippings"
taxonomy: { doc_category: [searxng] }
---
SearXNG 自带搜索语法，你可以通过它来修改分类、搜索引擎、语言等。有关搜索引擎、分类和语言的列表，请查看 `设置 `。

##   `!` 选择引擎和分类¶

要设置类别和/或引擎名称，使用 `!` 前缀。以下是一些示例：

- 在维基百科中搜索 **paris**：
	- `!wp paris`
	- `!wikipedia paris`
- 在 **map** 类别中搜索 **paris**：
	- `!map paris`
- 图像搜索
	- `!images Wau Holland`

引擎和语言的缩写也是被接受的。引擎/类别修饰符是可链接且包含的。例如， `!map !ddg !wp paris` 会在地图类别中搜索，并在 DuckDuckGo 和 Wikipedia 中搜索 **paris**。

##   `:` 选择语言¶

要选择语言过滤器，请使用 `:` 前缀。举个例子：

- 使用自定义语言搜索维基百科：
	- `:fr !wp Wau Holland`

##   `!!<bang>` 外部感叹号¶

SearXNG 支持来自 [DuckDuckGo](https://duckduckgo.com/bang) 的外部感叹号。要直接跳转到外部搜索页面，请使用 `!!` 前缀。例如：

- 使用自定义语言搜索维基百科：
	- `!!wfr Wau Holland`

请注意，您的搜索将直接在外部搜索引擎中执行。SearXNG 无法通过这种方式保护您的隐私。

##   `!!` 自动重定向¶

当在搜索查询中包含 `!!`（用空格分隔）时，您将自动重定向到第一个结果。这种行为与 DuckDuckGo 的“幸运”功能类似。举个例子：

- 搜索查询并重定向到第一个结果
	- `!! Wau Holland`

请注意，您被重定向到的结果可能无法验证其可信度，使用此功能时 SearXNG 也无法保护您的个人隐私。自行承担风险。

## 特殊查询¶

在`设置`页面中，您会找到用于 *特殊查询*的关键词。以下是一些示例：

- 生成一个随机 UUID
	- `random uuid`
- 计算平均值
	- `avg 123 548 2.04 24.2`
- 显示您的浏览器*用户代理* （需要激活）
	- `user-agent`
- 将字符串转换为不同的哈希摘要（需要激活）

	- `md5 lorem ipsum`
	- `sha512 lorem ipsum`