---
title: "用户界面自定义"
source: "https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/User-Interface-Customizations"
author:
published:
created: 2026-05-19
description: "Stable Diffusion web UI. Contribute to AUTOMATIC1111/stable-diffusion-webui development by creating an account on GitHub."
tags:
  - "clippings"
taxonomy: { doc_category: [sd-webui] }
---
## 快速设置

网页顶部的快速设置可根据您的需求进行配置

`Setting` -> `User interface` -> `Quick settings list` 任何设置都可以放置在 `Quick Settings` 中，在此处对设置的更改将立即保存并应用，同时保存到配置文件中。

![quick-settings-list-1](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/images/quick-settings-list-1.png) ![quick-settings-list-2](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/images/quick-settings-list-2.png)

在示例截图中， ``` Stable Diffusion checkpoint 和 ``SD VAE 被放置在 `Show live preview for the created images` 中。`` ```

默认情况下，只有 `Stable Diffusion checkpoint` 位于 `Quick Settings` 中。

> 尽管从技术上讲所有设置都可以移至 `Quick Settings` ，但将需要重新加载或重启才能生效的设置放在 `Quick Settings 中是没有意义的。`

## txt2img / img2img 的额外选项

如何找回 `Face Restore` 或 `Tiling`

可以为 txt2img 或 img2img 添加额外的设置

我们允许用户向图像生成界面添加额外设置，这些设置可在以下位置找到：

`Setting` -> `Settings in UI` -> `Settings for txt2img/img2img`

> 在 WebUI 1.6 版本中，设置项为 `Setting` -> `interface` -> `Options in main UI - txt2img/img2img`
> 
> > 此功能是通过内置扩展 `extra-options-section` 添加的；如果您看不到相关设置选项，请检查“扩展”标签页中是否已启用该扩展。

大多数（如果不是全部）设置均可在此处按需添加

此前， `Face Restoration` 和 `Tiling` 已内置于界面中且无法修改，若用户发现它们有用，可手动将其添加回来。

![additional-options-1](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/images/additional-options-1.png) ![additional-options-2](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/images/additional-options-2.png)

此外，我们还支持额外选项来更改选项的显示样式

## Gradio 主题

自定义 WebUI 的基本外观

无需使用如 Lobe Theme 或 Nevysha 的 Cozy Nest 之类的扩展，即可自定义 WebUI 的外观

这可以通过 Gradio 主题来实现。

![gradio-themes](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/images/gradio-themes.png)

我们提供了一些可供选择的选项，但如果您在 gradio/theme-gallery 中发现了喜欢的其他主题，也可以手动输入其 URL 中的对应部分到下拉菜单中。

默认情况下，WebUI 会在本地缓存主题，这样无需每次都下载。但这意味着如果主题更新了，您将不会收到更新；如果您希望更新主题（重新下载），请取消勾选 `Cache gradio themes locally` 或删除对应的主题缓存。

缓存的主题存储在 `stable-diffusion-webui/tmp/gradio_themes/your_selected_theme.json` 目录下（路径中的斜杠已替换为下划线）。

此外，您也可以在本地创建自己的主题或修改缓存的主题

## 用户界面项目顺序

自定义 txt2img/img2img 选项卡的界面元素顺序

生成参数界面元素可以使用默认顺序 `Setting` -> `User interface` -> `UI item order for txt2img/img2img tabs` ![UI-item-order-1](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/images/UI-item-order-1.png) (1.7) ![UI-item-order-2](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/images/UI-item-order-2.png) 自定义顺序 ![UI-item-order-3](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/images/UI-item-order-3.png) 

## 界面元素的默认值及范围限制步长

自定义界面元素数值

Webui 允许用户更改 UI 元素的默认值，包括下拉菜单、单选按钮、滑块和输入框。

1. 刷新 WebUI 网页，使所有 UI 元素恢复为默认值且无任何更改。
2. 找到您希望更改的 UI 元素并将其调整为您期望的默认值。
3. 前往 `Setting > Defaults` 。
4. 点击 `View changes` ，您将看到已更改的元素值列表。
5. 确认您是否满意这些更改，如果是，请点击 `Apply` 。
6. 新值将保存至 `ui-config.json` ，并在下一次 `Reload UI` 或 `Restart` （非网页刷新，而是 WebUI 服务器重载）后作为默认值使用。

---

高级调整（例如更改滑块的最大范围）也可以通过编辑 `ui-config.json` 中的相应值来完成，您必须手动编辑该文件，因为目前尚无在界面中更改这些值的方法。

找到需要修改的正确值可能有些困难，但您可以通过利用 `View changes` 在 `Setting > Defaults` 上定位该正确值。

例如，如果您希望增加 txt2img 中图像宽度滑块的最大限制。

1. 重新加载您的网页，确保所有元素值均处于默认值。
2. 在 txt2img 选项卡中，将图像宽度滑块调整为任何非默认值。
3. 前往 `Setting > Defaults` 点击 `View changes` ，您应该会看到一个条目如下。

| 路径 | 旧值 | 新值 |
| --- | --- | --- |
| txt2img/Width/value | 512 | 1024 |

4. 记下路径 `txt2img/Width` 但不包含类型 `value` 。
5. 打开 `ui-config.json` 并搜索 `txt2img/Width` 。
6. 您将在相同路径下找到其他值，如下所示：
```yaml
"txt2img/Width/visible": true,
"txt2img/Width/value": 512,
"txt2img/Width/minimum": 64,
"txt2img/Width/maximum": 2048,
"txt2img/Width/step": 8,
```
7. 您可以将 `"txt2img/Width/maximum": 2048,` 调整为 `"txt2img/Width/maximum": 4096,` ，以扩大滑块的最大范围限制。
8. 保存 `ui-config.json` 和 `Reload UI` 或 `Restart` 后，WebUI 中的滑块将更新为新的范围。

> 注意：建议在修改前进行备份，尤其是手动编辑文件时，如果语法不正确，文件可能会损坏。

> 提示：某些值存在隐藏的限制。  
> 例如，Stable Diffusion 的图像分辨率必须是 8 的倍数，因此即使你可以将滑块\`step\`的\`size\`自定义为任意值，这样做也是不明智的，因为它可能导致意外错误