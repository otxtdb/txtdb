---
title: "如何使用 Visual Selector 监控网页的某些部分？"
source: "https://distill.io/docs/web-monitor/what-is-visual-selector/"
author:
  - "[[Distill]]"
published: 2023-01-10
created: 2025-11-30
description: "Learn how to use Distill's Visual Selector to monitor specific parts of webpages with options for XPath CSS and JavaScript selectors."
tags:
  - "clippings"
---
## 如何使用 Visual Selector 监控网页的某些部分？

  
以下是使用 [Web app](https://distill.io/docs/web-monitor/what-is-visual-selector/%22https://distill.io%22) 在页面上进行选择的步骤。

  
第1步：从监控列表中点击“添加网页”。这将打开源页面。

  
第 2 步：在源页面中输入 URL，然后点击“Go”。 [配置文件](https://distill.io/docs/web-monitor/profiles-for-cloud-monitors/)和[代理](https://distill.io/docs/web-monitor/monitor-webpage-using-proxy-servers/)是可选字段，如有需要，您可以稍后添加。

  
第 3 步：选择器模式默认开启。您可以点击页面部分进行选择。您可以同时选择多个元素， [展开/缩小](https://distill.io/docs/web-monitor/what-is-visual-selector/#how-to-expand-and-narrow-selections)选择范围，如果您不想监控某些元素，还可以[排除](https://distill.io/docs/web-monitor/what-is-visual-selector/#how-to-exclude-elements-from-the-selection-that-you-do-not-want-to-monitor)这些元素。您应该能看到带有文本内容的选择预览。

  
第4步：点击“保存”按钮。

##   
如何扩展和缩小选择？

  
如果你发现直接点击难以选中网页的大片区域，可以尝试先从较小的部分开始选择。然后使用“扩展”图标来增加你的选择范围。类似地，你可以使用“缩小”图标来微调你的选择，并在必要时使用“删除”图标来移除它。

  
如果操作不可见，您可以点击围绕选择范围的右箭头图标，如下所示。 操作出现后，您可以点击它们来使用。![icons for expand, narrow and delete](https://distill.io/docs/web-monitor/what-is-visual-selector/images/d008-expand-narrow-delete.jpg "expand, narrow and delete icon")

##   
如何排除您不想监控的选择元素？

  
您可以在已选择的元素内进行选择以排除元素。被排除的元素不会被监控。

  
如果使用网页应用可视化选择器，您将看到所选元素被蓝色边框框包围，排除的元素在红色框中。如果使用浏览器扩展，所选元素将显示在黑色边框框中。

![selection and de-selection](https://distill.io/docs/web-monitor/what-is-visual-selector/images/d008-de-selection.jpg "de-selected elements")

##   
如何在 Visual Selector 中使用文本过滤器？

  
Distill 支持正则表达式过滤。您可以使用它来提取特定模式的字符，例如数字或短语，从选择中。例如，如果您想从选择中仅提取数字文本，可以使用 `\d+` 作为正则表达式。

  
此功能可在视觉选择面板中使用。如果网页应用中没有显示视觉选择面板，您可以点击“齿轮”图标来展开它。

  
下面的图像展示了一个包含数字和字母数字文本的选择。使用正则表达式，已经对数字内容进行了过滤以进行监控。

![regex filter](https://distill.io/docs/web-monitor/what-is-visual-selector/images/d008-regex-filter.jpg "extract text using regex")

  
请注意，Distill 使用 JavaScript 版本的正则表达式。\``gim`\` 是标志位。你可以根据需要设置标志位。默认情况下，所有标志位都是启用的。

  
旗帜有以下描述：

  
g：执行全局匹配。如果设置，将找到所有匹配项，并且不会在第一个匹配项后停止。如果你有多个选择并且想要对所有应用相同的文本过滤器，可以使用这个选项。

  
i：执行不区分大小写的匹配。

  
m：执行多行匹配。

  
你还可以通过在正则表达式测试网站上进行测试来验证你的 RegEx。其中一些网站是：[https://regex101.com/](https://regex101.com/)，[https://www.regextester.com/](https://www.regextester.com/)。Distill 使用 JavaScript 语言。

##   
如何监控选中元素的属性和属性值？

  
默认情况下，Distill 监控选中元素的文字变化。您也可以监控选中元素的属性和属性值。当您在页面上选中元素时，属性和属性字段会显示出来。您需要检查/选择您想要监控的字段。这些字段的值会作为文本保存，并在选择预览中显示。您可以导航到 [变更历史](https://distill.io/docs/web-monitor/change-history-and-highlighted-changes/) 查看文本变化的详细信息。

![attribute and property value monitoring](https://distill.io/docs/web-monitor/what-is-visual-selector/images/d008-fields-to-monitor.jpg "attribute value monitoring")

##   
如何修改现有监控器的选择？

  
这里列出了您可以遵循的步骤来修改选择：

1. 通过点击显示器左侧的向下箭头图标，进入显示器的选项页面。然后从上下文菜单中选择“编辑选项”。
![Edit Options](https://distill.io/docs/web-monitor/what-is-visual-selector/images/d008-edit-options.png)

2. 在源下点击“打开网页选择器”选项。它将显示带有 URL、配置文件和代理的 URL 栏。
3. 点击“前往”按钮。

![Open Visual Selector](https://distill.io/docs/web-monitor/what-is-visual-selector/images/d008-selector-existing-monitor.png "Open Visual Selector")

4. 它会加载当前已有的选择。你也可以点击齿轮图标左侧的“选择图标”来切换它（开/关）。在选择器模式开启时，你可以在此阶段修改/添加/删除选择。
5. 你可以点击齿轮/设置图标来查看现有的选择器。你可以在选择器视图中手动修改/添加/删除选择器。

##   
云监控的广告和 Cookie 弹窗拦截器

  
默认情况下，云监控器的广告和 Cookie 弹窗拦截功能是开启的。对于全页监控，广告和 Cookie 的内容将被排除在选择范围之外，不会进行监控，从而减少误报数量。您可以在任何监控器的选项页面管理此设置，或者在添加新监控器时，通过在选择视图中选择省略号（三个点）图标来进行设置。

![Ads And Cookies Blocker](https://distill.io/docs/web-monitor/what-is-visual-selector/images/d008-ads-cookies-blocker.jpg)

**  
广告和 Cookie 弹窗处理本地显示器**

  
对于本地显示器，您可以在开始监控前手动关闭 cookie 弹窗。您的偏好设置会保存在浏览器中，并在 cookie 过期前保持有效。要屏蔽广告，您可以在浏览器中使用广告拦截扩展。

## 常见问题解答

  
如何监控图像的变化？

  
在大多数情况下，当图像发生变化时，源链接也会改变。您可以监控图像的源链接。

  
1\. 你可以从网页中选择图片。  
  
2\. 从字段选项中选择 \`src\` 字段。你应该能在选择预览区域看到 src 值。  
  
3\. 保存并完成！

![image src value monitor](https://distill.io/docs/web-monitor/what-is-visual-selector/images/d008-image-src-selection.jpg "image monitoring")

  
如何监控链接或锚标签的 href 变化？

  
你可以选择\`href\`属性来监控链接的变化。你可以按照上述步骤进行图像监控，并从字段中选择\`href\`。

  
如何监控按钮颜色的变化？

  
许多网页使用属性 \`class\` 来显示按钮颜色。例如，当项目不可用时，它们可以添加一个 "disabled" 类来显示禁用按钮。你可以监控 \`class\` 属性以及文本来监控这种情况。

  
如何为加载时间较长的网页添加延迟？

  
1\. 进入显示器选项页面，如图所示：

![Edit Options](https://distill.io/docs/web-monitor/what-is-visual-selector/images/d008-edit-options.png)

  
2\. 点击源中的"齿轮"图标以访问其配置：

![show config](https://distill.io/docs/web-monitor/what-is-visual-selector/images/d008-show-config.png "show configuration")

  
3\. 在配置部分，更新"等待时长"的值。你可以根据需求将其设置为最大30。