---
title: "AI 变更摘要"
source: "https://distill.io/docs/web-monitor/ai-change-summary/"
author:
  - "[[Distill]]"
published: 2024-04-08
created: 2025-11-30
description: "Learn how to use AI Change Summary in Distill to get concise summaries of website changes available in Enterprise and Flexi plans. Only on Distill web monitoring."
tags:
  - "clippings"
---
>   
> 可在**企业版**和**弹性版**中获取。

  
AI 变更摘要提供网站变更的简明摘要。

##   
为何使用变更摘要

- 它让你能够快速访问重要变更，无需浏览变更历史或探索差异对比。
- 如果你正在监控全页或大章节的变更，且更新量很大，这将非常有用。
- 你可以使用 Distill 的 API 获取摘要数据并集成到其他应用程序中。
- 允许你添加和描述自定义字段，以捕获特定数据用于包含在 AI 摘要中。

##   
启用 AI 摘要的步骤：

1. 在你的监控列表中，点击汉堡图标。
2. 从列表中选择 `AI Summary` 以打开 AI Summary 设置。
![option to enable ai summary](https://distill.io/docs/web-monitor/ai-change-summary/images/option_ai_summary.jpg)

3. 将 `Summarize Changes` 切换到“开启”。
![option to enable ai summary](https://distill.io/docs/web-monitor/ai-change-summary/images/toggle_summarize_changes.jpg)

##   
在哪里查看 AI 变更摘要？

  
摘要可以在监控的变更历史中查看，如下所示。此外，如果设置了邮件操作，您也会通过邮件警报收到它们。

  
在监控列表中，点击监控文本的预览以打开其变更历史。您将看到 AI 变更摘要以蓝色高亮显示。

![change summary of web page changes](https://distill.io/docs/web-monitor/ai-change-summary/images/summary_within_change_history.jpg)

  
您还可以进一步探索变更历史中的差异，以详细了解变更内容。

##   
自定义变更摘要

  
您可以提供自定义提示来定义您希望变更摘要包含的内容。您可以包含尽可能多的细节，并指定您希望忽略的任何文本。

  
这可以在 AI 摘要设置中完成。点击汉堡图标 -> AI 摘要 以查看设置页面。此外，您还可以点击“改进”链接进入 AI 摘要设置。

  
AI 摘要设置对监控列表是全局的。这些提示适用于您监控列表中的所有监控器。

##   
提取自定义字段

  
默认情况下，AI 变更摘要下提供两个字段：`change_summary` 和 `important`。您可以更新这些默认字段的提示以适应您的需求。此外，您还可以创建自定义字段并为它们添加提示。

####   
自定义字段命名和类型

- Custom Field Name: 建议使用不含空格的名称。如果需要多个单词，请用下划线 (\_) 分隔它们。
- 自定义字段类型：自定义字段可以是以下类型之一：
	- `Number` – 如果字段应只包含数值，请使用此类型。
	- `Boolean` – 如果字段应只有两个可能的值：`True` 或 `False`，请使用此类型。
	- `String` – 如果字段应接受任何文本，请使用此类型。

####   
测试更新后的提示和字段

  
在 AI 摘要设置中更新提示和字段后，您可以从 AI 摘要设置的右侧测试它们并预览新的变更摘要。选择一个具有变更历史的监控器，然后点击`测试`按钮。新的变更摘要结果将显示在默认摘要的顶部，并附带测试时的当前日期和时间。

![test results of change summary after prompt update](https://distill.io/docs/web-monitor/ai-change-summary/images/ai_summary_settings.jpg)

  
你可以尝试不同的提示词，并相应地进行调整。如果存在高亮的变化历史记录，`Test` 将会起作用。当你对 AI 变化总结结果满意时，点击 `Save` 保存更新后的提示词和字段，然后退出 AI 总结详情页面。

### 提示示例

####   
申请开放及截止日期

  
为 `change_summary` 提供的提示：\`\`\`总结变更，包括与以下相关的内容 - 截止日期，- 新增拨款，- 更新申请日期，- 申请标准变更，- 任何行动号召\`\`\`

```
do not summarize changes like:
- reordering of texts or elements
- translation or language updates
- changes in website structure
- social media changes
\`\`\`
```

####   
电子商务列表变更：

  
您可以更新 `change_summary` 的默认提示，并添加 `seller_rating`、`price` 等字段，并为它们提供提示。其中之一显示在下图。

![test results of change summary after fields addition](https://distill.io/docs/web-monitor/ai-change-summary/images/ai_summary_test_fields.jpg)

#### 网站篡改

```
You can create custom field for detecting website defacement. 
Create field \`defaced\` of type \`boolean\`. Example prompt:
\`\`\`
the page is defaced if its original content has been replaced or updated with:

1. malicious content such as links to download malicious software
2. threatening messages or blackmails
3. added content contains any of the following keywords:
- keyword1
- keyword2
- etc.
\`\`\`
```

##   
监控器何时记录 AI 摘要？

- 只有当监控的文本超过 200 个字符时才会生成 AI 摘要。否则不会生成摘要。
- 摘要仅针对网页和 PDF 类型的监控器生成。
- AI 摘要可在企业版和云监控器的 Flexi 版计划中使用。

>   
> Distill 使用 LLM 生成 AI 摘要。请注意 LLMs 容易出错。请核实实际数据和变化。