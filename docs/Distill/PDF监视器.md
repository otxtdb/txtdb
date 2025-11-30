---
title: PDF监视器
source: https://distill.io/docs/web-monitor/monitor-pdf-for-changes/
author:
  - "[[Distill]]"
published: 2024-05-27
created: 2025-11-30
description: Monitor PDF documents for changes with Distill. Track updates in PDF files, documents, and reports automatically with change detection.
tags:
  - clippings
---
>   
> 可在 Flexi 和 Enterprise 计划中使用

##   
如何追踪 PDF 文件的更改？

  
Distill 提供监控 PDF 文档更改的功能，前提是该文档可通过公共 URL 访问。要使用此功能，您需要使用 [https://monitor.distill.io](https://monitor.distill.io/) 处的 Web 应用程序。请注意，此功能不受浏览器扩展支持。

  
如果 PDF 文件与网页上的超链接相关联，点击链接获取 PDF 的 URL。获取 URL 后，您可按照以下步骤添加 PDF 监控器：

1. 访问位于 [https://monitor.distill.io](https://monitor.distill.io/) 的网页应用的监控列表。
2. 点击“添加监控”按钮，从列表中选择“PDF”。
	![Button to add PDF monitor](https://distill.io/docs/web-monitor/monitor-pdf-for-changes/images/add-pdf-monitor.png)
3. 在源页面输入 PDF 文件的 URL，然后点击“保存”按钮。![Enter PDF URL](https://distill.io/docs/web-monitor/monitor-pdf-for-changes/images/enter-pdf-url.png "Enter PDF URL")
4. 将打开一个选项窗口。在此页面，您可以配置检查间隔和变更发生时要采取的操作等设置。完成后保存即可。
	![configure actions, check interval for the monitor](https://distill.io/docs/web-monitor/monitor-pdf-for-changes/images/configure-options.png "Options window for a pdf monitor")

  
我们的 PDF 监控器现已设置完成。您可以通过点击监控器的文本预览来查看其内容。如果发现变更，您将通过在选项页面设置的先前操作收到通知。

![version history](https://distill.io/docs/web-monitor/monitor-pdf-for-changes/images/view-change-history-pdf.png "Version history of PDF monitor")

  
您可以通过点击更改历史记录下的“探索差异”选项，进一步比较 PDF 监控的两个版本。

![explore diff](https://distill.io/docs/web-monitor/monitor-pdf-for-changes/images/explore-pdf-diff.png "Compare two versions of a PDF monitor")

##   
如果 PDF 文件在网站上的链接经常变化，我该如何监控该文件的变更？

  
在某些情况下，您可能需要监控网页上链接的 PDF 文件，且该超链接经常发生变化。在这种情况下，您需要创建以下两个监控器：

1. 使用 PDF 的 URL 添加一个 PDF 监控器。
2. 为显示 PDF 链接的网页添加一个网页监控器。您需要监控“href”属性以观察 PDF 的 URL 是否发生变化。

  
当第二个监控器（链接变化）发出警报时，您需要手动[更新第一个监控器（PDF 监控器）的 URL](https://distill.io/docs/web-monitor/monitor-pdf-for-changes/#updating-url-of-the-pdf-monitor)。

  
*示例：* 让我们监控“Form 1040”的 PDF 文件，页面链接为 [https://www.irs.gov/forms-pubs/about-form-1040](https://www.irs.gov/forms-pubs/about-form-1040)。以下是我们需要遵循的步骤：

1. 我们需要为 Form 1040 添加一个 PDF 监控器。通过点击网页上 Form 1040 的超链接，我们将获取 PDF 的 URL：[https://www.irs.gov/pub/irs-pdf/f1040.pdf](https://www.irs.gov/pub/irs-pdf/f1040.pdf)。![pdf monitor](https://distill.io/docs/web-monitor/monitor-pdf-for-changes/images/add-pdf-monitor-step1.png "PDF monitor")
2. 我们需要添加一个监视器来监控 PDF 的 URL 是否发生变化。如果 URL 发生变化，那么我们需要更新在先前步骤中添加的第一个监视器。以下是监控源网页上 PDF URL 的步骤。
	- 为 https://www.irs.gov/forms-pubs/about-form-1040 添加网页监控![monitor pdf's link](https://distill.io/docs/web-monitor/monitor-pdf-for-changes/images/add-page-monitor-for-pdf-link.png)
	- 选择具有指向 PDF 文件超链接的 Form 1040。
	- 展开选择面板以显示选择器和预览。
	- 在属性或属性列表中搜索“href”，并从列表中选择，如下所示： ![attribute value selection](https://distill.io/docs/web-monitor/monitor-pdf-for-changes/images/monitor-href-link-pdf.png "Monitor attribute value") 选中 href 后，您将在预览中看到 PDF 的 URL。
	- 保存选择并在选项页面配置其他设置（检查间隔、操作等），然后保存。
	  
	以上步骤中的网页监控器以文本形式监控 PDF 链接。要详细了解监控的文本，您需要导航到变更历史记录。默认情况下，变更历史记录显示监控的“可视化”视图。监控的链接在页面上并不以可视化形式呈现，因此它不会在可视化视图中显示。您需要切换到“文本”视图才能看到如下所示的内容。
	![Text view of monitor](https://distill.io/docs/web-monitor/monitor-pdf-for-changes/images/text-view.png "Text view")

###   
更新 PDF 监控器的 URL

  
当 PDF 链接如上一步所述发生变化时，您需要更新 PDF 监控器的 URL。以下是执行此操作的步骤：

1. 进入 PDF 监控器的选项页面。 ![Options Page](https://distill.io/docs/web-monitor/monitor-pdf-for-changes/images/edit-options.png "Monitor's Option Settings Page")
2. 从选项页面点击“编辑”，如下所示，将现有 URL 替换为新的 URL。 ![Edit URL](https://distill.io/docs/web-monitor/monitor-pdf-for-changes/images/edit-pdf-url.png "Edit PDF URL")

##### 常见问题解答

**  
1\. 我可以监控 PDF 文档的部分内容吗？**

  
不，PDF 文档默认是全页监控。

**  
2\. 我可以在本地设备上监控 PDF 吗？**

  
不，PDF 监控仅在 Distill 的云服务器上运行，并且仅在 Flexi 和企业版计划中可用。

**  
3\. 监控的 PDF 文件是否有大小限制？**

  
PDF 没有大小限制。但是，如果 PDF 文件因为过大而加载时间过长，监控工具可能会显示解析错误，因为它未能成功加载 PDF。

**  
4\. Distill 能否监控密码保护的 PDF 文件？**

  
不，Distill PDF 监控器不能处理密码保护的 PDF 文件。

**  
5\. 当我监控的 PDF 文件被删除时会发生什么？**

  
如果 PDF 文件已被删除或移除，监控器将显示错误信息。

**  
6\. 如何比较同一 PDF 文件的两个版本？**

  
如果你想要比较同一 PDF 文件的两个版本，而这些版本现在托管在不同的 URL 上，你需要在 Distill 中更新现有监控的 URL。例如，由于两个版本的内容不同，PDF 的 URL 可能已从 [www.somewebsite.com/content/version1doc.pdf](https://www.somewebsite.com/content/version1doc.pdf) 更改为 [www.somewebsite.com/content/version2doc.pdf](https://www.somewebsite.com/content/version2doc.pdf)。

  
要执行此操作：点击相应 PDF 监控的向下箭头图标 -> 选择“编辑选项” -> 在选项页面中，通过用新 URL 替换旧 URL 来编辑源 -> 保存。

  
检查后，PDF 监控器将显示两个版本之间的变更历史。

## 故障排除

  
PDF 的生成方式有多种，有时可能无法与 Distill 兼容。如果无法兼容，你会在检查日志中看到带有错误代码的错误。以下是常见的错误代码及其解决方法。

1. ERR\_PDF\_PARSE 错误通常发生在 Distill 能够下载文件但无法解析文件时。这通常是因为文件不是 PDF 文件，或者文件格式不受 Distill 支持。您可以稍等片刻，看看 Distill 是否能够正确下载并解析文件。
2. E\_DOWNLOAD 表示 PDF 文件下载未成功完成。这通常发生在下载过程中断且无法继续完成时。Distill 将自动重试。
3. 当 Distill 尝试下载文件时遇到 E\_PDF\_UNKNOWN\_TYPE 错误，但网站没有发送文件。这通常意味着文件不是 PDF 文件，或者网站没有发送文件。这可能由多种原因引起。例如，网站可以选择在允许下载文件之前阻止请求或要求使用 cookie。

  
如果经过几次检查后错误仍然存在，请通过 [support@distill.io](https://distill.io/docs/web-monitor/monitor-pdf-for-changes/) 邮箱联系我们。

  
您也可以参考这个逐步视频指南来创建 PDF 监控器。

<iframe src="https://www.youtube-nocookie.com/embed/4lytDwKss5c?rel=0&amp;modestbranding=1" title="How to import and export monitors" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen="" loading="lazy" style="position:absolute;top:0;left:0;width:100%;height:100%;"></iframe>

[Watch on YouTube](https://youtu.be/4lytDwKss5c)

  
对于高级 PDF 监控，例如比较 PDF、追踪变更和识别新的 PDF 链接，请参考[这个视频](https://youtu.be/kb1u5BS_EhY) 。

*  
PDF 文件体积较大，检查和比对它们会消耗更多资源。PDF 监控的成本按检查次数计入账户。1 次 PDF 检查计为 2 次检查。*