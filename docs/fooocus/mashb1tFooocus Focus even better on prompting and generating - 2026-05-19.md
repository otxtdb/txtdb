---
title: "Fooocus - mashb1t 的 1-Up 版本"
source: "https://github.com/mashb1t/Fooocus"
author:
published:
created: 2026-05-19
description: "Focus even better on prompting and generating. Contribute to mashb1t/Fooocus development by creating an account on GitHub."
tags:
  - "clippings"
taxonomy: { doc_category: [fooocus] }
---
## Fooocus - mashb1t 的 1-Up 版本

这个分支的目的是添加新功能/修复错误，并将贡献回馈给 [Fooocus](https://github.com/lllyasviel/Fooocus) 。

作为 Fooocus 仓库的合作者与贡献者，你几乎可以在每一个 [问题](https://github.com/lllyasviel/Fooocus/issues) 、 [拉取请求](https://github.com/lllyasviel/Fooocus/pulls) 、 [讨论](https://github.com/lllyasviel/Fooocus/discussions) 等中找到我。

不幸的是，Fooocus 的创建者多次长时间消失，因此我决定亲自处理这件事。

## 本分支包含的附加功能：

（主要反映了我提交的 [拉取请求](https://github.com/lllyasviel/Fooocus/pulls/mashb1t) ）

- ✨ ~~[lllyasviel#958](https://github.com/lllyasviel/Fooocus/pull/958) - NSFW 图片审查（配置和界面）~~
- 🐛 ~~[lllyasviel#981](https://github.com/lllyasviel/Fooocus/pull/981) - 防止用户跳过/停止队列中其他用户任务（多用户功能）+ 重新设计高级参数（移除+PID 处理）~~
- ✨ ~~[lllyasviel#985](https://github.com/lllyasviel/Fooocus/pull/985) - 添加 100 种动物到通配符列表~~
- ✨ ~~[lllyasviel#1013](https://github.com/lllyasviel/Fooocus/pull/1013) - 添加高级参数以禁用中间结果（进度画廊，防止生成速度过快时 UI 卡顿）~~
- ✨ [lllyasviel#1039](https://github.com/lllyasviel/Fooocus/pull/1039) - 添加提示翻译
- ✨ [lllyasviel#1043](https://github.com/lllyasviel/Fooocus/pull/1043) - 添加 LCM 实时画布绘画（此代码库中未合并到主分支）
- ✨ ~~[lllyasviel#1167](https://github.com/lllyasviel/Fooocus/pull/1167) - 将模型 BluePencil XL v0.5 更新至 v3.1.0~~
- ✨ ~~[lllyasviel#1570](https://github.com/lllyasviel/Fooocus/pull/1570) - 在 Gradio UI 中添加预设选择（基于会话）~~
- 🐛 ~~[lllyasviel#1578](https://github.com/lllyasviel/Fooocus/pull/1578) - 添加在生成过程中更改提示的解决方案~~
- ✨ [lllyasviel#1580](https://github.com/lllyasviel/Fooocus/pull/1580) - 添加 SDXL Turbo 的预设（模型 DreamShaperXL\_Turbo）
- ✨ ~~[lllyasviel#1616](https://github.com/lllyasviel/Fooocus/pull/1616) - 添加默认最大图像数量的配置设置~~
- 🐛 ~~[lllyasviel#1668](https://github.com/lllyasviel/Fooocus/pull/1668) - 修复如果不存在则创建 path\_outputs 目录的问题~~
- ✨ 为每个性能设置显示更多详细信息，例如步骤
- ✨ ~~为元数据和 gradio 添加默认覆盖步骤的处理（允许切换到 turbo 预设以正确设置 default\_overwrite\_step）~~
- ✨ ~~[lllyasviel#1762](https://github.com/lllyasviel/Fooocus/pull/1762) - 鼠标悬停时添加样式预览~~
- 🐛 ~~[lllyasviel#1784](https://github.com/lllyasviel/Fooocus/pull/1784) - 正确排序文件，首先显示最深层目录~~
- ✨ ~~[lllyasviel#1785](https://github.com/lllyasviel/Fooocus/pull/1785) - 将模型 Juggernaut XL v6 更新到 v8~~
- ✨ [lllyasviel#1809](https://github.com/lllyasviel/Fooocus/pull/1809) - 减小预览图片的文件大小
- ✨ ~~[lllyasviel#1932](https://github.com/lllyasviel/Fooocus/pull/1932) - 在 gradio 中使用一致的文件名~~
- ✨ ~~[lllyasviel#1863](https://github.com/lllyasviel/Fooocus/pull/1863) - 支持图像扩展名（png、jpg、webp）~~
- ✨ ~~[lllyasviel#1938](https://github.com/lllyasviel/Fooocus/pull/1938) - 如果提示为空，则在 uov 图像上传时自动描述图像~~
- ✨ ~~[lllyasviel#1940](https://github.com/lllyasviel/Fooocus/pull/1940) - 元数据处理，方案：Fooocus（json）和 A1111（纯文本）。与 Civitai 兼容。~~
- ✨ ~~[lllyasviel#1979](https://github.com/lllyasviel/Fooocus/pull/1979) - 防止午夜后过时的历史日志链接~~
- ✨ [lllyasviel#2032](https://github.com/lllyasviel/Fooocus/pull/2032) - 添加使用 rembg 的 inpaint mask 生成功能，包括分割支持
- 🐛 ~~[lllyasviel#2332](https://github.com/lllyasviel/Fooocus/pull/2332) - 允许 path\_outputs 位于根目录之外~~
- ✨ ~~[lllyasviel#2415](https://github.com/lllyasviel/Fooocus/pull/2415) - 添加性能优化的 sdxl 闪电模式（4 步）~~
- 还有更多（90 多个）已经合并，请查看 [我的 PR](https://github.com/lllyasviel/Fooocus/pulls/mashb1t)

✨ = 新功能  
🐛 = 修复 bug  
~~abc~~ = 合并

---

## 功能展示

### 增强 - 自动图像放大 + 增强

与 adetailer 类似，但基于动态图像检测而非特定掩码检测模型。一键完成所有操作！

查看。

| 原始（生成） | 放大（之前） | `#1` 黄色连衣裙 | `#2` 手部替换 |
| --- | --- | --- | --- |
| [![image - 2024-06-23T154659 098](https://private-user-images.githubusercontent.com/9307310/342070683-260e6a0b-5f42-47a3-83fd-fc3f4310d3a7.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxNzgxNTAsIm5iZiI6MTc3OTE3Nzg1MCwicGF0aCI6Ii85MzA3MzEwLzM0MjA3MDY4My0yNjBlNmEwYi01ZjQyLTQ3YTMtODNmZC1mYzNmNDMxMGQzYTcucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI2MDUxOSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNjA1MTlUMDgwNDEwWiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9ZjI0NWY2ZWQwYmVmYWY5ZGUzNTI5MmE4YTQyNDhkYTIyMTMxMDVjMWY1ODFhZmU1YzAwMjE5NmQ5N2QyNDc3NCZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmcmVzcG9uc2UtY29udGVudC10eXBlPWltYWdlJTJGcG5nIn0.m5Mhk6pqlOyYD4NDNPCKxWPibrlqoPozlEfThTcdTB0)](https://private-user-images.githubusercontent.com/9307310/342070683-260e6a0b-5f42-47a3-83fd-fc3f4310d3a7.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxNzgxNTAsIm5iZiI6MTc3OTE3Nzg1MCwicGF0aCI6Ii85MzA3MzEwLzM0MjA3MDY4My0yNjBlNmEwYi01ZjQyLTQ3YTMtODNmZC1mYzNmNDMxMGQzYTcucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI2MDUxOSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNjA1MTlUMDgwNDEwWiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9ZjI0NWY2ZWQwYmVmYWY5ZGUzNTI5MmE4YTQyNDhkYTIyMTMxMDVjMWY1ODFhZmU1YzAwMjE5NmQ5N2QyNDc3NCZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmcmVzcG9uc2UtY29udGVudC10eXBlPWltYWdlJTJGcG5nIn0.m5Mhk6pqlOyYD4NDNPCKxWPibrlqoPozlEfThTcdTB0) | [![image - 2024-06-23T155614 010](https://private-user-images.githubusercontent.com/9307310/342070703-09c9d620-08d8-4a3f-b99e-dddf9b653234.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxNzgxNTAsIm5iZiI6MTc3OTE3Nzg1MCwicGF0aCI6Ii85MzA3MzEwLzM0MjA3MDcwMy0wOWM5ZDYyMC0wOGQ4LTRhM2YtYjk5ZS1kZGRmOWI2NTMyMzQucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI2MDUxOSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNjA1MTlUMDgwNDEwWiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9MTVlODdhMmRkMGRmYmM5MTJhNjkxZWYyYWFhYjcxN2MzNGQ1ZDY0MjAyNjE0NzgyNzQ0NTI5NGQ4M2FhYmJkNSZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmcmVzcG9uc2UtY29udGVudC10eXBlPWltYWdlJTJGcG5nIn0.DxswCYWuAd6zDZuh0HRG9CcKDznOBw_BjNBXJnQRJJU)](https://private-user-images.githubusercontent.com/9307310/342070703-09c9d620-08d8-4a3f-b99e-dddf9b653234.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxNzgxNTAsIm5iZiI6MTc3OTE3Nzg1MCwicGF0aCI6Ii85MzA3MzEwLzM0MjA3MDcwMy0wOWM5ZDYyMC0wOGQ4LTRhM2YtYjk5ZS1kZGRmOWI2NTMyMzQucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI2MDUxOSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNjA1MTlUMDgwNDEwWiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9MTVlODdhMmRkMGRmYmM5MTJhNjkxZWYyYWFhYjcxN2MzNGQ1ZDY0MjAyNjE0NzgyNzQ0NTI5NGQ4M2FhYmJkNSZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmcmVzcG9uc2UtY29udGVudC10eXBlPWltYWdlJTJGcG5nIn0.DxswCYWuAd6zDZuh0HRG9CcKDznOBw_BjNBXJnQRJJU) | [![image - 2024-06-23T155852 562](https://private-user-images.githubusercontent.com/9307310/342070743-c31b210c-b846-47c2-a3f6-db4e3241401f.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxNzgxNTAsIm5iZiI6MTc3OTE3Nzg1MCwicGF0aCI6Ii85MzA3MzEwLzM0MjA3MDc0My1jMzFiMjEwYy1iODQ2LTQ3YzItYTNmNi1kYjRlMzI0MTQwMWYucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI2MDUxOSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNjA1MTlUMDgwNDEwWiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9MzQwNTU3NDVjMTU5YWZlZDBhZTY0NTA4YTBkOWVkNjNlNmNhMmZlYjYzN2VlMTIyZjBhOTVjMzQwYjM0YzEzNyZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmcmVzcG9uc2UtY29udGVudC10eXBlPWltYWdlJTJGcG5nIn0.t32nzwY_R9IaXZK5gMBh2LF8jjKqpTfJ2-erJ0Da-UY)](https://private-user-images.githubusercontent.com/9307310/342070743-c31b210c-b846-47c2-a3f6-db4e3241401f.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxNzgxNTAsIm5iZiI6MTc3OTE3Nzg1MCwicGF0aCI6Ii85MzA3MzEwLzM0MjA3MDc0My1jMzFiMjEwYy1iODQ2LTQ3YzItYTNmNi1kYjRlMzI0MTQwMWYucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI2MDUxOSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNjA1MTlUMDgwNDEwWiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9MzQwNTU3NDVjMTU5YWZlZDBhZTY0NTA4YTBkOWVkNjNlNmNhMmZlYjYzN2VlMTIyZjBhOTVjMzQwYjM0YzEzNyZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmcmVzcG9uc2UtY29udGVudC10eXBlPWltYWdlJTJGcG5nIn0.t32nzwY_R9IaXZK5gMBh2LF8jjKqpTfJ2-erJ0Da-UY) | [![image - 2024-06-23T161011 491](https://private-user-images.githubusercontent.com/9307310/342070782-8a5d1ff8-cf60-4cf2-85f7-065cf5ccaf8d.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxNzgxNTAsIm5iZiI6MTc3OTE3Nzg1MCwicGF0aCI6Ii85MzA3MzEwLzM0MjA3MDc4Mi04YTVkMWZmOC1jZjYwLTRjZjItODVmNy0wNjVjZjVjY2FmOGQucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI2MDUxOSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNjA1MTlUMDgwNDEwWiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9ZTIyMmMxNjhlYmM3ZWZiODRjNjQ1NTg3ZTI5NTQ3ZWZkY2IwNmFmZWM4MDRiNDVlM2UxYmRhODZiODM3ZGIwZSZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmcmVzcG9uc2UtY29udGVudC10eXBlPWltYWdlJTJGcG5nIn0.-hYiNZlDRKIf-pc2Z5WRdC_hAOqkVm4-Delvc666Nhs)](https://private-user-images.githubusercontent.com/9307310/342070782-8a5d1ff8-cf60-4cf2-85f7-065cf5ccaf8d.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxNzgxNTAsIm5iZiI6MTc3OTE3Nzg1MCwicGF0aCI6Ii85MzA3MzEwLzM0MjA3MDc4Mi04YTVkMWZmOC1jZjYwLTRjZjItODVmNy0wNjVjZjVjY2FmOGQucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI2MDUxOSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNjA1MTlUMDgwNDEwWiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9ZTIyMmMxNjhlYmM3ZWZiODRjNjQ1NTg3ZTI5NTQ3ZWZkY2IwNmFmZWM4MDRiNDVlM2UxYmRhODZiODM3ZGIwZSZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmcmVzcG9uc2UtY29udGVudC10eXBlPWltYWdlJTJGcG5nIn0.-hYiNZlDRKIf-pc2Z5WRdC_hAOqkVm4-Delvc666Nhs) |

---

### lllyasviel#2032 - 自动遮罩生成 + 遮罩提示

由 [@rayronvictor 制作的视频](https://github.com/rayronvictor)

---

### lllyasviel#1940 - 元数据处理 - 兼容 Civitai & A1111

此功能为 Fooocus（json）和 A1111（纯文本）元数据方案提供可激活的元数据持久性，后者与 A1111 和 Civitai 完全兼容，但无法在 Fooocus 之外重现图像，因为 Fooocus 中有许多改进和特殊功能，其他地方并不适用。

- 支持 PNG（PngInfo）+ JPG 和 WebP（两者均为 EXIF）的元数据。
- 直接从图像保存和恢复配置
- 您还可以配置版权/创作者标签

[![Screenshot 2024-01-29 at 15 13 17](https://private-user-images.githubusercontent.com/9307310/300489868-6b7df4eb-feb3-46ee-bf09-f336be63b625.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxNzgxNTAsIm5iZiI6MTc3OTE3Nzg1MCwicGF0aCI6Ii85MzA3MzEwLzMwMDQ4OTg2OC02YjdkZjRlYi1mZWIzLTQ2ZWUtYmYwOS1mMzM2YmU2M2I2MjUucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI2MDUxOSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNjA1MTlUMDgwNDEwWiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9MWJhNDQ5ZmIyMzlkODA5YTgxMDk1NTAzOGZlMTQ4M2I2MDA0NzBjMGY4ODFhNDRiZWY3MjljMjhlMzQ5OGY0NyZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmcmVzcG9uc2UtY29udGVudC10eXBlPWltYWdlJTJGcG5nIn0.dU63PQbAZ5L7-U922Z9Oi4o0TbLo5KNV8H50VAgqoV0)](https://private-user-images.githubusercontent.com/9307310/300489868-6b7df4eb-feb3-46ee-bf09-f336be63b625.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxNzgxNTAsIm5iZiI6MTc3OTE3Nzg1MCwicGF0aCI6Ii85MzA3MzEwLzMwMDQ4OTg2OC02YjdkZjRlYi1mZWIzLTQ2ZWUtYmYwOS1mMzM2YmU2M2I2MjUucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI2MDUxOSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNjA1MTlUMDgwNDEwWiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9MWJhNDQ5ZmIyMzlkODA5YTgxMDk1NTAzOGZlMTQ4M2I2MDA0NzBjMGY4ODFhNDRiZWY3MjljMjhlMzQ5OGY0NyZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmcmVzcG9uc2UtY29udGVudC10eXBlPWltYWdlJTJGcG5nIn0.dU63PQbAZ5L7-U922Z9Oi4o0TbLo5KNV8H50VAgqoV0)

Gradio（设置在开发者调试模式）

默认为 Fooocus 方案 [![image](https://private-user-images.githubusercontent.com/9307310/296883336-ae529db2-f5d1-4725-9735-3036b50020b7.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxNzgxNTAsIm5iZiI6MTc3OTE3Nzg1MCwicGF0aCI6Ii85MzA3MzEwLzI5Njg4MzMzNi1hZTUyOWRiMi1mNWQxLTQ3MjUtOTczNS0zMDM2YjUwMDIwYjcucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI2MDUxOSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNjA1MTlUMDgwNDEwWiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9YWQwNGEzNGI4Y2UwMTBlMzk2YTI1ZWI3M2Q5NDgwMjRhM2RmMDIyYjFkNzg5NTYwM2Q4ZTI2OTk1YTdhMTc1MyZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmcmVzcG9uc2UtY29udGVudC10eXBlPWltYWdlJTJGcG5nIn0.neTU9BzAdsdfDc4hgwB8mMevOAkW-U2LmfB235qdoPA)](https://private-user-images.githubusercontent.com/9307310/296883336-ae529db2-f5d1-4725-9735-3036b50020b7.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxNzgxNTAsIm5iZiI6MTc3OTE3Nzg1MCwicGF0aCI6Ii85MzA3MzEwLzI5Njg4MzMzNi1hZTUyOWRiMi1mNWQxLTQ3MjUtOTczNS0zMDM2YjUwMDIwYjcucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI2MDUxOSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNjA1MTlUMDgwNDEwWiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9YWQwNGEzNGI4Y2UwMTBlMzk2YTI1ZWI3M2Q5NDgwMjRhM2RmMDIyYjFkNzg5NTYwM2Q4ZTI2OTk1YTdhMTc1MyZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmcmVzcG9uc2UtY29udGVudC10eXBlPWltYWdlJTJGcG5nIn0.neTU9BzAdsdfDc4hgwB8mMevOAkW-U2LmfB235qdoPA) 配置选项

```json
"default_save_metadata_to_images": true,
"default_metadata_scheme": "a1111",
"metadata_created_by": "mashb1t"
```

参数 --disable-metadata

`--disable-metadata` 完全阻止 Gradio 中的元数据处理和输出

元数据读取器
1. 打开图像输入 > 元数据标签页
2. 将图像拖拽到图像上传区域
3. 自动预览图像元数据
4. 在按钮点击时将元数据应用于 Gradio 输入

Fooocus 方案 [![Screenshot 2024-01-29 at 15 13 17](https://private-user-images.githubusercontent.com/9307310/300489868-6b7df4eb-feb3-46ee-bf09-f336be63b625.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxNzgxNTAsIm5iZiI6MTc3OTE3Nzg1MCwicGF0aCI6Ii85MzA3MzEwLzMwMDQ4OTg2OC02YjdkZjRlYi1mZWIzLTQ2ZWUtYmYwOS1mMzM2YmU2M2I2MjUucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI2MDUxOSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNjA1MTlUMDgwNDEwWiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9MWJhNDQ5ZmIyMzlkODA5YTgxMDk1NTAzOGZlMTQ4M2I2MDA0NzBjMGY4ODFhNDRiZWY3MjljMjhlMzQ5OGY0NyZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmcmVzcG9uc2UtY29udGVudC10eXBlPWltYWdlJTJGcG5nIn0.dU63PQbAZ5L7-U922Z9Oi4o0TbLo5KNV8H50VAgqoV0)](https://private-user-images.githubusercontent.com/9307310/300489868-6b7df4eb-feb3-46ee-bf09-f336be63b625.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxNzgxNTAsIm5iZiI6MTc3OTE3Nzg1MCwicGF0aCI6Ii85MzA3MzEwLzMwMDQ4OTg2OC02YjdkZjRlYi1mZWIzLTQ2ZWUtYmYwOS1mMzM2YmU2M2I2MjUucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI2MDUxOSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNjA1MTlUMDgwNDEwWiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9MWJhNDQ5ZmIyMzlkODA5YTgxMDk1NTAzOGZlMTQ4M2I2MDA0NzBjMGY4ODFhNDRiZWY3MjljMjhlMzQ5OGY0NyZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmcmVzcG9uc2UtY29udGVudC10eXBlPWltYWdlJTJGcG5nIn0.dU63PQbAZ5L7-U922Z9Oi4o0TbLo5KNV8H50VAgqoV0)

A1111 方案 [![Screenshot 2024-01-29 at 15 09 52](https://private-user-images.githubusercontent.com/9307310/300488844-1ee3c030-2b6d-41cb-9f88-40df6452df15.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxNzgxNTAsIm5iZiI6MTc3OTE3Nzg1MCwicGF0aCI6Ii85MzA3MzEwLzMwMDQ4ODg0NC0xZWUzYzAzMC0yYjZkLTQxY2ItOWY4OC00MGRmNjQ1MmRmMTUucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI2MDUxOSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNjA1MTlUMDgwNDEwWiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9NmM1NmI4NjVkOTJlMmMwNDdiZjcxNzJmY2UzOWRjZDg3ZjIxMDFhNjVkOWQyYzE3NmYwNTIzMzg1Nzg2MTdjZCZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmcmVzcG9uc2UtY29udGVudC10eXBlPWltYWdlJTJGcG5nIn0.o_Uk1ZYkBWIzoMKPxE3HyQZGulOPL0i5rYFGs3WGXoU)](https://private-user-images.githubusercontent.com/9307310/300488844-1ee3c030-2b6d-41cb-9f88-40df6452df15.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxNzgxNTAsIm5iZiI6MTc3OTE3Nzg1MCwicGF0aCI6Ii85MzA3MzEwLzMwMDQ4ODg0NC0xZWUzYzAzMC0yYjZkLTQxY2ItOWY4OC00MGRmNjQ1MmRmMTUucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI2MDUxOSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNjA1MTlUMDgwNDEwWiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9NmM1NmI4NjVkOTJlMmMwNDdiZjcxNzJmY2UzOWRjZDg3ZjIxMDFhNjVkOWQyYzE3NmYwNTIzMzg1Nzg2MTdjZCZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmcmVzcG9uc2UtY29udGVudC10eXBlPWltYWdlJTJGcG5nIn0.o_Uk1ZYkBWIzoMKPxE3HyQZGulOPL0i5rYFGs3WGXoU) 文件中的元数据

Fooocus 方案速度 [![image](https://private-user-images.githubusercontent.com/9307310/296881746-c556b2ed-0e0b-4117-9bda-9508fb3e0d96.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxNzgxNTAsIm5iZiI6MTc3OTE3Nzg1MCwicGF0aCI6Ii85MzA3MzEwLzI5Njg4MTc0Ni1jNTU2YjJlZC0wZTBiLTQxMTctOWJkYS05NTA4ZmIzZTBkOTYucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI2MDUxOSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNjA1MTlUMDgwNDEwWiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9NjhjZWI1OThhNzdiMTQ4MDlmMmJlNTQzOWE3ZDM1MmQ4NWE3Y2RkZDJmNmNlYWUwOTc0MDU2MDI2OTgzOTc4NSZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmcmVzcG9uc2UtY29udGVudC10eXBlPWltYWdlJTJGcG5nIn0.KiSxU2zz0TWS6Ona3typxTe_tjeuPWObHJJ7wTOyqpE)](https://private-user-images.githubusercontent.com/9307310/296881746-c556b2ed-0e0b-4117-9bda-9508fb3e0d96.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxNzgxNTAsIm5iZiI6MTc3OTE3Nzg1MCwicGF0aCI6Ii85MzA3MzEwLzI5Njg4MTc0Ni1jNTU2YjJlZC0wZTBiLTQxMTctOWJkYS05NTA4ZmIzZTBkOTYucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI2MDUxOSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNjA1MTlUMDgwNDEwWiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9NjhjZWI1OThhNzdiMTQ4MDlmMmJlNTQzOWE3ZDM1MmQ4NWE3Y2RkZDJmNmNlYWUwOTc0MDU2MDI2OTgzOTc4NSZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmcmVzcG9uc2UtY29udGVudC10eXBlPWltYWdlJTJGcG5nIn0.KiSxU2zz0TWS6Ona3typxTe_tjeuPWObHJJ7wTOyqpE)

LCM A1111 方案（是的，包含负面提示，因为它在技术上存在但不会产生影响）速度 A1111 方案Civitai

Speed Fooocus 方案LCM A1111 方案速度 A1111 方案---

[![](https://private-user-images.githubusercontent.com/19834515/278888447-483fb86d-c9a2-4c20-997c-46dafc124f25.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxNzgxNTAsIm5iZiI6MTc3OTE3Nzg1MCwicGF0aCI6Ii8xOTgzNDUxNS8yNzg4ODg0NDctNDgzZmI4NmQtYzlhMi00YzIwLTk5N2MtNDZkYWZjMTI0ZjI1LnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA1MTklMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNTE5VDA4MDQxMFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTcwMjMxMGViODBhZjgwYzg5ZGJjYjBiZWI4ZTBhNDFmMGY5MDA0ZWJjNTU4NDA0NGQ0NTBhYzRjODI5OTkzYmQmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.Moj-ZqTYePOKaJNHMugwDxktLPJnLp54D6VTGTShBy8)](https://private-user-images.githubusercontent.com/19834515/278888447-483fb86d-c9a2-4c20-997c-46dafc124f25.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxNzgxNTAsIm5iZiI6MTc3OTE3Nzg1MCwicGF0aCI6Ii8xOTgzNDUxNS8yNzg4ODg0NDctNDgzZmI4NmQtYzlhMi00YzIwLTk5N2MtNDZkYWZjMTI0ZjI1LnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA1MTklMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNTE5VDA4MDQxMFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTcwMjMxMGViODBhZjgwYzg5ZGJjYjBiZWI4ZTBhNDFmMGY5MDA0ZWJjNTU4NDA0NGQ0NTBhYzRjODI5OTkzYmQmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.Moj-ZqTYePOKaJNHMugwDxktLPJnLp54D6VTGTShBy8)

## Fooocus

[\>>> 点击此处安装 Fooocus <<<](#download)

Fooocus 是一款图像生成软件（基于 [Gradio](https://www.gradio.app/) ）。

Fooocus 重新思考了图像生成器的设计。该软件是离线、开源且免费的，同时与许多在线图像生成器（如 Midjourney）类似，无需手动调整，用户只需专注于提示和图像。Fooocus 还简化了安装流程：从点击“下载”到生成第一张图像，所需的鼠标点击次数严格限制在 3 次以下。最低 GPU 内存要求为 4GB（Nvidia）。

**最近在搜索“fooocus”时，谷歌上存在许多假冒网站，不要相信那些——这是 Fooocus 唯一的官方来源。**

## 项目状态：仅限有限长期支持（LTS）及错误修复

Fooocus 项目完全基于 **Stable Diffusion XL** 架构构建，目前处于仅提供错误修复的有限长期支持（LTS）状态。由于现有功能被认为几乎不存在程序性问题（感谢 [mashb1t](https://github.com/mashb1t) 的巨大努力），未来的更新将专注于解决可能出现的任何错误。

**目前没有计划迁移到或整合更新的模型架构。** 然而，随着开源社区的发展，这种情况可能会改变。例如，如果社区最终形成了一种单一的、主导的图像生成方法（考虑到当前状况，这种情况可能在半年或一年内真的发生），Fooocus 也可能会迁移到那种精确的方法。

对于有兴趣使用 **Flux** 等更新模型的人来说，我们建议探索其他平台，例如 [WebUI Forge](https://github.com/lllyasviel/stable-diffusion-webui-forge) （同样来自我们）， [ComfyUI/SwarmUI](https://github.com/comfyanonymous/ComfyUI) 。此外，还有几个 [优秀的 Fooocus 分叉版本](https://github.com/lllyasviel/Fooocus?tab=readme-ov-file#forks) 可以用于实验。

再次强调，最近在 Google 上搜索“fooocus”时存在许多假冒网站。请 **不要** 从这些网站获取 Fooocus——本页面是 Fooocus 的唯一官方来源。我们从未有过任何类似“fooocus.com”、“fooocus.net”、“fooocus.co”、“fooocus.ai”、“fooocus.org”、“fooocus.pro”、“fooocus.one”的网站。这些网站全部是假的。它们与我们 **完全没有关系 。Fooocus 是一款 100%非商业、离线开源软件。**

## 功能

以下是使用 Midjourney 示例的快速列表：

| Midjourney | Fooocus |
| --- | --- |
| 无需大量提示工程或参数调整的高质量文生图。   (未知方法) | 高质量的文本到图像转换，无需复杂的提示工程或参数调整。   （Fooocus 拥有基于 GPT-2 的离线提示处理引擎和许多采样改进，因此无论您的提示是简短的“花园中的房子”还是长达 1000 个字，结果始终都很美观） |
| V1 V2 V3 V4 | 输入图像 -> 放大或变异 -> 变异（微妙）/ 变异（强烈） |
| U1 U2 U3 U4 | 输入图像 -> 放大或变化 -> 放大（1.5倍）/ 放大（2倍） |
| 修复/上/下/左/右（平移） | 输入图像 -> 修复或外绘 -> 修复/上/下/左/右   (Fooocus 采用其特有的 inpaint 算法和 inpaint 模型，因此结果比所有使用标准 SDXL inpaint 方法/模型的软件更令人满意) |
| 图像提示 | 输入图像 -> 图像提示   (Fooocus 采用其特有的图像提示算法，因此结果质量和提示理解比所有使用标准 SDXL 方法（如标准 IP-Adapters 或 Revisions）的软件更令人满意) |
| \--style | 高级 -> 样式 |
| \--stylize | 高级 -> 高级 -> 指导 |
| \--niji | [Multiple launchers: "run.bat", "run\_anime.bat", and "run\_realistic.bat".](https://github.com/lllyasviel/Fooocus/discussions/679)   Fooocus 支持在 Civitai 上使用 SDXL 模型   （如果您不了解 Civitai，可以在谷歌搜索“Civitai”） |
| \--quality | 高级 -> 质量 |
| \--重复 | 高级 -> 图像数量 |
| 多提示(::) | 只需使用多行提示 |
| 提示权重 | 您可以使用 " I am (happy:1.5)"。   Fooocus 使用 A1111 的重新加权算法，因此如果用户直接从 Civitai 复制提示，结果会比 ComfyUI 更好。（因为如果提示在 ComfyUI 的重新加权中编写，用户不太可能复制提示文本，因为他们更喜欢拖拽文件）   要使用嵌入，您可以使用 "(embedding:file\_name:1.1)" |
| \--no | 高级 -> 负面提示 |
| \--ar | 高级 -> 纵横比 |
| InsightFace | 输入图像 -> 图像提示 -> 高级 -> 人脸交换 |
| 描述 | 输入图像 -> 描述 |

以下是使用 LeonardoAI 示例的快速列表：

| LeonardoAI | Fooocus |
| --- | --- |
| 提示魔法 | 高级 -> 风格 -> Fooocus V2 |
| 高级采样参数（如对比度/清晰度等） | 高级 -> 高级 -> 采样锐度 / 等 |
| 用户友好控制网 | 输入图像 -> 图像提示 -> 高级 |

此外， [click here to browse the advanced features.](https://github.com/lllyasviel/Fooocus/discussions/117)

## 下载

### Windows

您可以直接使用以下方式下载 Fooocus：

**[\>>> 点击此处下载 <<<](https://github.com/mashb1t/Fooocus/releases/download/v2.6.0/Fooocus_win64_2-6-0.7z)**

下载文件后，请解压缩，然后运行"run.bat"。

[![image](https://private-user-images.githubusercontent.com/19834515/260325783-c49269c4-c274-4893-b368-047c401cc58c.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxNzgxNTAsIm5iZiI6MTc3OTE3Nzg1MCwicGF0aCI6Ii8xOTgzNDUxNS8yNjAzMjU3ODMtYzQ5MjY5YzQtYzI3NC00ODkzLWIzNjgtMDQ3YzQwMWNjNThjLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA1MTklMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNTE5VDA4MDQxMFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWEzZDM1MDNkMTE3MGYxY2VjZGJmMjUzZTNjZjk1NDJiYjMwMmZmYmZiM2NiZTBlN2JmZjQxY2YyZjRmZGU3ZWYmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.6s3fvghHvgAAqJ5i1-TBi_CeDIoemd-oQlxGLu1KpYs)](https://private-user-images.githubusercontent.com/19834515/260325783-c49269c4-c274-4893-b368-047c401cc58c.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxNzgxNTAsIm5iZiI6MTc3OTE3Nzg1MCwicGF0aCI6Ii8xOTgzNDUxNS8yNjAzMjU3ODMtYzQ5MjY5YzQtYzI3NC00ODkzLWIzNjgtMDQ3YzQwMWNjNThjLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA1MTklMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNTE5VDA4MDQxMFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWEzZDM1MDNkMTE3MGYxY2VjZGJmMjUzZTNjZjk1NDJiYjMwMmZmYmZiM2NiZTBlN2JmZjQxY2YyZjRmZGU3ZWYmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.6s3fvghHvgAAqJ5i1-TBi_CeDIoemd-oQlxGLu1KpYs)

第一次启动软件时，它会自动下载模型：

1. 它将根据不同的预设下载 [默认模型](#models) 到"Fooocus\\models\\checkpoints"文件夹中。如果你不想自动下载，可以提前下载它们。
2. 请注意，如果你使用 inpaint 功能，第一次对图像进行 inpaint 时，它会从 [这里下载 Fooocus 自带的 inpaint 控制模型](https://huggingface.co/lllyasviel/fooocus_inpaint/resolve/main/inpaint_v26.fooocus.patch) ，作为文件"Fooocus\\models\\inpaint\\inpaint\_v26.fooocus.patch"（该文件大小为 1.28GB）。

从 Fooocus 2.1.60 版本开始，你还将拥有 `run_anime.bat` 和 `run_realistic.bat` 。它们是不同的模型预设（需要不同的模型，但会自动下载）。

从 Fooocus 2.3.0 版本开始，你可以在浏览器中直接切换预设。如果你想要改变默认行为，请记住添加这些参数：

- 使用 `--disable-preset-selection` 来禁用浏览器中的预设选择。
- 使用 `--always-download-new-model` 在切换预设时下载缺失的模型。默认是回退到预设中定义的 `previous_default_models` ，也请参考终端输出。如果你已经拥有这些文件，你可以将它们复制到上述位置以加快安装速度。

注意，如果你看到 **"MetadataIncompleteBuffer"或"PytorchStreamReader"** ，那么你的模型文件已损坏。请重新下载模型。

下面是在一台配置相对较低的笔记本电脑上进行的测试，该电脑拥有 **16GB 系统内存** 和 **6GB 显存** （Nvidia 3060 笔记本电脑）。这台机器的迭代速度约为每轮 1.35 秒。相当令人印象深刻——如今配备 3060 的笔记本电脑通常价格非常合理。此外，最近许多其他软件报告称，Nvidia 驱动程序高于 532 版本有时会比 Nvidia 驱动程序 531 版本慢 10 倍。如果你的生成时间非常长，可以考虑下载 [Nvidia Driver 531 Laptop](https://www.nvidia.com/download/driverResults.aspx/199991/en-us/) 或 [Nvidia Driver 531 Desktop](https://www.nvidia.com/download/driverResults.aspx/199990/en-us/) 。

请注意，最低要求是 **4GB Nvidia GPU 显存（4GB VRAM）** 和 **8GB 系统内存（8GB RAM）** 。这需要使用微软的虚拟交换技术，在大多数情况下，Windows 安装会自动启用该功能，因此您通常无需对此进行任何操作。但是，如果您不确定，或者您手动关闭了它（谁会真的这么做呢？），或者 **如果您看到任何"RuntimeError: CPUAllocator"** ，您可以在此处启用它：

点击此处查看图片说明。**并且确保每个驱动器上至少有 40GB 的可用空间，如果你仍然看到"RuntimeError: CPUAllocator"！**

如果您使用类似的设备但仍无法达到可接受的性能，请打开一个问题。

请注意不同平台的 [最低要求](#minimal-requirement) 是不同的。

也请参阅常见问题和故障排除 [此处](https://github.com/mashb1t/Fooocus/blob/main/troubleshoot.md) 。

### 从 Fooocus 切换到这个分支

1. 在你的 Fooocus 文件夹中打开终端（包含 config.txt 的那个文件夹）
2. 执行 `git status` 。你应该看到以下内容：
	```pgsql
	On branch main
	Your branch is up to date with 'origin/main'.
	nothing to commit, working tree clean
	```
	如果不行，执行 `git reset --hard origin/main` 并再次检查 `git status` 。
3. 执行
	```dsconfig
	git remote set-url origin https://github.com/mashb1t/Fooocus.git
	git reset --hard origin/main
	git pull
	```
4. 激活你的虚拟环境（从 7z 安装时无需激活），并更新你的 Python 包，具体取决于你的环境（7z、venv、conda 等）
	Windows（7z）示例：`..\python_embeded\python.exe -m pip install -r "requirements_versions.txt"`
5. 通过打开 run.bat 或相应的入口点（与之前相同）来启动 Fooocus

或者

Windows：下载 [7z 文件](#download) ，解压它并运行 `run.bat` 。你可能需要复制已下载的检查点 / LoRAs / 等等。

### Colab

(最后测试 - 2024 年 8 月 12 日由 [mashb1t](https://github.com/mashb1t) 测试)

| Colab | Info |
| --- | --- |
|  | Fooocus 官方 |

在 Colab 中，你可以将最后一行修改为\`!python entry\_with\_update.py --share --always-high-vram\`或\`!python entry\_with\_update.py --share --always-high-vram --preset anime\`或\`!python entry\_with\_update.py --share --always-high-vram --preset realistic\`，以使用 Fooocus 默认版/动漫版/写实版。

你也可以在界面中更改预设。请注意，这可能导致60秒后超时。如果出现这种情况，请等待下载完成，将预设更改为初始状态，然后切换回你选择的预设或重新加载页面。

请注意，这个 Colab 默认会禁用精炼功能，因为 Colab 免费版的资源相对有限（一些“大”功能如图像提示可能会导致免费版 Colab 断开连接）。我们确保基本文本到图像功能在免费版 Colab 上始终可用。

使用\`--always-high-vram\`将资源分配从 RAM 转移到 VRAM，并在默认的 T4 实例上实现性能、灵活性和稳定性之间的最佳平衡。请查看更多信息。

感谢 [camenduru](https://github.com/camenduru) 提供的模板！

### Linux (使用 Anaconda)

如果你想要使用 Anaconda/Miniconda，你可以

```bash
git clone https://github.com/lllyasviel/Fooocus.git
cd Fooocus
conda env create -f environment.yaml
conda activate fooocus
pip install -r requirements_versions.txt
```

然后下载模型：将 [默认模型](#models) 下载到 "Fooocus\\models\\checkpoints" 文件夹。 **或者使用启动器让 Fooocus 自动下载模型** ：

```vim
conda activate fooocus
python entry_with_update.py
```

或者，如果你想打开一个远程端口，使用

```applescript
conda activate fooocus
python entry_with_update.py --listen
```

使用 `python entry_with_update.py --preset anime` 或 `python entry_with_update.py --preset realistic` 用于 Fooocus Anime/Realistic 版本。

### Linux (使用 Python Venv)

你的 Linux 需要安装 **Python 3.10** ，假设你的 Python 可以通过 **python3** 命令调用，并且你的 venv 系统可以正常工作；你可以

```bash
git clone https://github.com/lllyasviel/Fooocus.git
cd Fooocus
python3 -m venv fooocus_env
source fooocus_env/bin/activate
pip install -r requirements_versions.txt
```

参见上文关于模型下载的部分。您可以通过以下方式启动软件：

```vim
source fooocus_env/bin/activate
python entry_with_update.py
```

或者，如果您想打开一个远程端口，请使用

```stylus
source fooocus_env/bin/activate
python entry_with_update.py --listen
```

使用 `python entry_with_update.py --preset anime` 或 `python entry_with_update.py --preset realistic` 来启动 Fooocus Anime/Realistic 版本。

### Linux (使用原生系统 Python)

如果你知道自己在做什么，并且你的 Linux 系统已经安装了 **Python 3.10** ，并且可以通过 **python3** 命令调用 Python（以及使用 **pip3** 调用 Pip），那么你可以

```bash
git clone https://github.com/lllyasviel/Fooocus.git
cd Fooocus
pip3 install -r requirements_versions.txt
```

请参考上述部分进行模型下载。您可以通过以下方式启动软件：

```vim
python3 entry_with_update.py
```

或者，如果你想打开一个远程端口，请使用

```stylus
python3 entry_with_update.py --listen
```

使用 `python entry_with_update.py --preset anime` 或 `python entry_with_update.py --preset realistic` 来启动 Fooocus Anime/Realistic 版本。

### Linux (AMD 显卡)

请注意不同平台的 [最低要求](#minimal-requirement) 是不同的。

与上述说明相同。您需要将 torch 更改为 AMD 版本

```awk
pip uninstall torch torchvision torchaudio torchtext functorch xformers 
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/rocm5.6
```

不过 AMD 尚未经过充分测试，AMD 支持目前处于测试阶段。

使用 `python entry_with_update.py --preset anime` 或 `python entry_with_update.py --preset realistic` 来启动 Fooocus Anime/Realistic 版本。

### Windows (AMD 显卡)

请注意，不同平台的 [最低要求](#minimal-requirement) 是不同的。

Windows 也是一样。下载软件并编辑 `run.bat` 的内容如下：

```stylus
.\python_embeded\python.exe -m pip uninstall torch torchvision torchaudio torchtext functorch xformers -y
.\python_embeded\python.exe -m pip install torch-directml
.\python_embeded\python.exe -s Fooocus\entry_with_update.py --directml
pause
```

然后运行 `run.bat` 。

不过，AMD 并未经过密集测试。AMD 支持目前处于测试阶段。

对于 AMD，使用 `.\python_embeded\python.exe entry_with_update.py --directml --preset anime` 或 `.\python_embeded\python.exe entry_with_update.py --directml --preset realistic` 来启动 Fooocus Anime/Realistic Edition。

### Mac

请注意不同平台的 [最低要求](#minimal-requirement) 是不同的。

Mac 系统未进行充分测试。以下是为 Mac 使用提供的不官方指南。您可以讨论遇到的问题。

您可以在 Apple Mac silicon（M1 或 M2）的 macOS 'Catalina'或更高版本上安装 Fooocus。Fooocus 通过 [PyTorch](https://pytorch.org/get-started/locally/) MPS 设备加速在 Apple silicon 计算机上运行。Mac Silicon 计算机没有专用显卡，导致图像处理时间显著长于配备专用显卡的计算机。

1. 安装 conda 包管理器和 pytorch nightly 版本。阅读 [Mac 上的加速 PyTorch 训练](https://developer.apple.com/metal/pytorch/) Apple Developer 指南获取说明。确保 pytorch 能够识别您的 MPS 设备。
2. 打开 macOS 终端应用，使用 `git clone https://github.com/lllyasviel/Fooocus.git` 克隆此仓库。
3. 切换到新的 Fooocus 目录， `cd Fooocus` 。
4. 创建一个新的 conda 环境， `conda env create -f environment.yaml` 。
5. 激活你的新 conda 环境， `conda activate fooocus` 。
6. 安装 Fooocus 所需的包， `pip install -r requirements_versions.txt` 。
7. 通过运行 `python entry_with_update.py` 启动 Fooocus。（一些 Mac M2 用户可能需要 `python entry_with_update.py --disable-offload-from-vram` 来加快模型加载/卸载速度。）首次运行 Fooocus 时，它会自动下载 Stable Diffusion SDXL 模型，并根据您的网络连接速度需要相当长的时间。

使用 `python entry_with_update.py --preset anime` 或 `python entry_with_update.py --preset realistic` 来使用 Fooocus Anime/Realistic 版本。

### Docker

查看 [docker.md](https://github.com/mashb1t/Fooocus/blob/main/docker.md)

### 下载上一个版本

查看指南。

## 最低要求

以下是运行 Fooocus 的最低要求。如果您的设备性能低于此规格，您可能无法在本地使用 Fooocus。（无论如何，如果您的设备性能低于此规格但 Fooocus 仍然可以运行，请告诉我们。）

| 操作系统 | GPU | 最低 GPU 内存 | 最低系统内存 | [系统切换](https://github.com/mashb1t/Fooocus/blob/main/troubleshoot.md) | 注意 |
| --- | --- | --- | --- | --- | --- |
| Windows/Linux | Nvidia RTX 4XXX | 4GB | 8GB | 必需 | 最快 |
| Windows/Linux | Nvidia RTX 3XXX | 4GB | 8GB | 必需 | 通常比 RTX 2XXX 更快 |
| Windows/Linux | Nvidia RTX 2XXX | 4GB | 8GB | 必需 | 通常比 GTX 1XXX 更快 |
| Windows/Linux | Nvidia GTX 1XXX | 8GB (\* 6GB 不确定) | 8GB | 必需 | 仅比 CPU 稍快 |
| Windows/Linux | Nvidia GTX 9XX | 8GB | 8GB | 必需 | 比 CPU 快或慢 |
| Windows/Linux | Nvidia GTX < 9XX | 不支持 | / | / | / |
| Windows | AMD GPU | 8GB (更新于 2023 年 12 月 30 日) | 8GB | 必需 | 通过 DirectML (\* ROCm 暂缓)，比 Nvidia RTX 3XXX 慢约 3 倍 |
| Linux | AMD GPU | 8GB | 8GB | 必需 | 通过 ROCm，比 Nvidia RTX 3XXX 慢约 1.5 倍 |
| Mac | M1/M2 MPS | 共享 | 共享 | 共享 | 比 Nvidia RTX 3XXX 慢约 9 倍 |
| Windows/Linux/Mac | 仅使用 CPU | 0GB | 32GB | 必需 | 比 Nvidia RTX 3XXX 慢约 17 倍 |

\* AMD GPU ROCm (暂停中)：AMD 仍在努力支持 Windows 上的 ROCm。

\* Nvidia GTX 1XXX 6GB 不确定：有些人报告在 GTX 10XX 上成功使用 6GB，但其他人报告失败案例。

*注意 Fooocus 仅用于生成极高画质的图像。我们将不支持较小模型以降低要求并牺牲结果质量。*

## 故障排除

查看常见问题 [这里](https://github.com/mashb1t/Fooocus/blob/main/troubleshoot.md) 。

## 默认模型

根据不同的目标，Fooocus 的默认模型和配置是不同的：

| 任务 | Windows | Linux 参数 | 主模型 | 精炼器 | 配置 |
| --- | --- | --- | --- | --- | --- |
| 通用 | run.bat |  | juggernautXL\_v8Rundiffusion | 未使用 | [此处](https://github.com/lllyasviel/Fooocus/blob/main/presets/default.json) |
| 逼真 | run\_realistic.bat | \--preset 真实 | realisticStockPhoto\_v20 | 未使用 | [此处](https://github.com/lllyasviel/Fooocus/blob/main/presets/realistic.json) |
| 动漫 | run\_anime.bat | \--preset 动漫 | animaPencilXL\_v500 | 未使用 | [此处](https://github.com/lllyasviel/Fooocus/blob/main/presets/anime.json) |

请注意下载是 **自动** 的——如果网络连接正常，您无需做任何操作。但是，如果您（或从其他地方移动）有自己的准备，可以手动下载它们。

## UI 访问和身份验证

除了在本地运行外，Fooocus 还可以通过两种方式暴露其 UI：

- 本地 UI 监听器：使用 `--listen` （例如通过 `--port 8888` 指定端口）。
- API 访问：使用 `--share` （在 `.gradio.live` 注册一个端点）。

这两种方式默认情况下都不需要身份验证。您可以通过在主目录中创建一个名为 `auth.json` 的文件来添加基本身份验证，该文件包含一个 JSON 对象列表，其中包含 `user` 和 `pass` 的键（参见 [auth-example.json](https://github.com/mashb1t/Fooocus/blob/main/auth-example.json) 中的示例）。

## "隐藏"技巧列表

点击查看技巧列表。这些技巧基于 SDXL，且与最新模型不太同步。
1. 基于 GPT2（类似于 Midjourney 的隐藏预处理和"原始"模式，或 LeonardoAI 的提示魔法）。
2. 在单个 k-sampler 内部进行原生精炼器切换。优点是精炼器模型现在可以重用基础模型从 k 采样中收集的动量（或 ODE 的历史参数），以实现更连贯的采样。在 Automatic1111 的高分辨率修复和 ComfyUI 的节点系统中，基础模型和精炼器使用两个独立的 k-sampler，这意味着动量大部分被浪费，采样连续性被破坏。Fooocus 使用其先进的 k-diffusion 采样，确保在精炼器设置中无缝、原生且连续地切换。（更新于 8 月 13 日：实际上，几天前我和 Automatic1111 讨论过这个问题，看来“在单个 k-sampler 内部进行原生精炼器切换”已经进入 webui 的开发分支。太棒了！）
3. 负面的 ADM 指导。由于 XL Base 的最高分辨率级别没有交叉注意力，XL 最高分辨率级别的正负信号在 CFG 采样期间无法获得足够的对比度，导致在某些情况下结果看起来有些塑料感或过于平滑。幸运的是，由于 XL 的最高分辨率级别仍然受图像宽高比（ADM）的调节，我们可以修改正负侧的 adm 来补偿最高分辨率级别中 CFG 对比度的不足。（更新于 8 月 16 日，iOS 应用 [Draw Things](https://apps.apple.com/us/app/draw-things-ai-generation/id6444050820) 将支持 Negative ADM Guidance。太棒了！）
4. 我们实现了一个经过精心调整的《使用自注意力引导改进扩散模型样本质量》第 5.1 节的变体。权重设置得非常低，但这是 Fooocus 的最终保证，以确保 XL 永远不会呈现出过于平滑或塑料的外观（示例）。这几乎可以消除所有 XL 在负 ADM 引导下偶尔仍会产生过于平滑结果的情况。（更新 2023 年 8 月 18 日，SAG 的高斯核已更改为各向异性核，以更好地保留结构并减少伪影。）
5. 我们稍微修改了风格模板，并添加了"cinematic-default"。
6. 我们测试了"sd\_xl\_offset\_example-lora\_1.0.safetensors"，似乎当 lora 权重低于 0.5 时，结果总是比没有 lora 的 XL 更好。
7. 采样器的参数经过精心调整。
8. 因为 XL 使用位置编码进行生成分辨率，所以使用几个固定分辨率生成的图像比任意分辨率生成的图像看起来稍好一些（因为位置编码不太擅长处理训练过程中未见过的整数）。这表明 UI 中的分辨率可能是为了最佳效果而硬编码的。
9. 为两个不同的文本编码器分离提示似乎没有必要。为基础模型和细化器分离提示可能有效，但效果是随机的，我们避免实现这一点。
10. DPM 系列似乎很适合 XL，因为 XL 有时会生成过于平滑的纹理，但 DPM 系列有时会在纹理中生成过于密集的细节。它们的联合效果看起来对人类感知是中性和吸引人的。
11. 一个精心设计的系统，用于平衡多种风格以及提示扩展。
12. 使用自动 1111 的方法来规范化提示词强调。当用户直接从 civitai 复制提示词时，这会显著提高结果。
13. 精炼器的联合交换系统现在也无缝支持 img2img 和放大。
14. 当 CFG 大于 10 时，进行 CFG Scale 和 TSNR 校正（针对 SDXL 进行调优）。

## 定制化

第一次运行 Fooocus 后，会在 `Fooocus\config.txt` 生成配置文件。该文件可以编辑以更改模型路径或默认参数。

例如，一个编辑后的 `Fooocus\config.txt` （该文件在首次启动后生成）可能如下所示：

```nix
{
    "path_checkpoints": "D:\\Fooocus\\models\\checkpoints",
    "path_loras": "D:\\Fooocus\\models\\loras",
    "path_embeddings": "D:\\Fooocus\\models\\embeddings",
    "path_vae_approx": "D:\\Fooocus\\models\\vae_approx",
    "path_upscale_models": "D:\\Fooocus\\models\\upscale_models",
    "path_inpaint": "D:\\Fooocus\\models\\inpaint",
    "path_controlnet": "D:\\Fooocus\\models\\controlnet",
    "path_clip_vision": "D:\\Fooocus\\models\\clip_vision",
    "path_fooocus_expansion": "D:\\Fooocus\\models\\prompt_expansion\\fooocus_expansion",
    "path_outputs": "D:\\Fooocus\\outputs",
    "default_model": "realisticStockPhoto_v10.safetensors",
    "default_refiner": "",
    "default_loras": [["lora_filename_1.safetensors", 0.5], ["lora_filename_2.safetensors", 0.5]],
    "default_cfg_scale": 3.0,
    "default_sampler": "dpmpp_2m",
    "default_scheduler": "karras",
    "default_negative_prompt": "low quality",
    "default_positive_prompt": "",
    "default_styles": [
        "Fooocus V2",
        "Fooocus Photograph",
        "Fooocus Negative"
    ]
}
```

许多其他键、格式和示例都在 `Fooocus\config_modification_tutorial.txt` （该文件在首次启动后生成）中。

在真正修改配置前请三思。如果你发现自己在破坏东西，只需删除 `Fooocus\config.txt` 。Fooocus 将恢复默认设置。

一种更安全的方法是直接尝试运行 "run\_anime.bat" 或 "run\_realistic.bat" —— 它们应该已经足够好地适用于不同的任务。

~~请注意 `user_path_config.txt` 已被弃用，即将被移除。~~ (编辑：它已经被移除了。)

### 所有 CMD 参数

```jboss
entry_with_update.py  [-h] [--listen [IP]] [--port PORT]
                      [--disable-header-check [ORIGIN]]
                      [--web-upload-size WEB_UPLOAD_SIZE]
                      [--hf-mirror HF_MIRROR]
                      [--external-working-path PATH [PATH ...]]
                      [--output-path OUTPUT_PATH]
                      [--temp-path TEMP_PATH] [--cache-path CACHE_PATH]
                      [--in-browser] [--disable-in-browser]
                      [--gpu-device-id DEVICE_ID]
                      [--async-cuda-allocation | --disable-async-cuda-allocation]
                      [--disable-attention-upcast]
                      [--all-in-fp32 | --all-in-fp16]
                      [--unet-in-bf16 | --unet-in-fp16 | --unet-in-fp8-e4m3fn | --unet-in-fp8-e5m2]
                      [--vae-in-fp16 | --vae-in-fp32 | --vae-in-bf16]
                      [--vae-in-cpu]
                      [--clip-in-fp8-e4m3fn | --clip-in-fp8-e5m2 | --clip-in-fp16 | --clip-in-fp32]
                      [--directml [DIRECTML_DEVICE]]
                      [--disable-ipex-hijack]
                      [--preview-option [none,auto,fast,taesd]]
                      [--attention-split | --attention-quad | --attention-pytorch]
                      [--disable-xformers]
                      [--always-gpu | --always-high-vram | --always-normal-vram | --always-low-vram | --always-no-vram | --always-cpu [CPU_NUM_THREADS]]
                      [--always-offload-from-vram]
                      [--pytorch-deterministic] [--disable-server-log]
                      [--debug-mode] [--is-windows-embedded-python]
                      [--disable-server-info] [--multi-user] [--share]
                      [--preset PRESET] [--disable-preset-selection]
                      [--language LANGUAGE]
                      [--disable-offload-from-vram] [--theme THEME]
                      [--disable-image-log] [--disable-analytics]
                      [--disable-metadata] [--disable-preset-download]
                      [--disable-enhance-output-sorting]
                      [--enable-auto-describe-image]
                      [--always-download-new-model]
                      [--rebuild-hash-cache [CPU_NUM_THREADS]]
```

## 内联提示功能

### 通配符

示例提示： `__color__ flower`

已处理正面和负面提示。

从预定义选项列表中随机选择一个通配符，在这种情况下是 `wildcards/color.txt` 文件。通配符将被随机颜色替换（随机性基于种子）。您也可以禁用随机性，并通过在开发者调试模式中启用 `  按顺序读取通配符  ` 复选框，从上到下处理通配符文件。

通配符可以嵌套和组合，并且可以在同一个提示中使用多个通配符（示例见 `wildcards/color_flower.txt` ）。

### 数组处理

示例提示： `[[红, 绿, 蓝]]花`

仅处理正面提示。

从左到右处理数组，为数组中的每个元素生成单独的图像。在这种情况下会生成3张图像，每张对应一种颜色。将图像数量增加到3以生成所有3个变体。

数组不能嵌套，但可以在同一个提示中使用多个数组。支持将 LoRA 作为数组元素直接嵌入！

### 内联 LoRAs

示例提示： `flower <lora:sunflowers:1.2>`

仅对正面提示进行处理。

将 LoRA 应用于提示。LoRA 文件必须位于 `models/loras` 目录中。

## 高级功能

[Click here to browse the advanced features.](https://github.com/lllyasviel/Fooocus/discussions/117)

## 分支

以下是一些 Fooocus 的分支：

| Fooocus 的分支 |
| --- |
| [fenneishi/Fooocus-Control](https://github.com/fenneishi/Fooocus-Control)   [runew0lf/RuinedFooocus](https://github.com/runew0lf/RuinedFooocus)   [MoonRide303/Fooocus-MRE](https://github.com/MoonRide303/Fooocus-MRE)   [metercai/SimpleSDXL](https://github.com/metercai/SimpleSDXL)   [mashb1t/Fooocus](https://github.com/mashb1t/Fooocus)   等等... |

## 谢谢

感谢 [twri](https://github.com/twri) 、 [3Diva](https://github.com/3Diva) 和 [Marc K3nt3L](https://github.com/K3nt3L) 创建了 Fooocus 中可用的额外 SDXL 风格。

该项目始于 [Stable Diffusion WebUI](https://github.com/AUTOMATIC1111/stable-diffusion-webui) 和 [ComfyUI](https://github.com/comfyanonymous/ComfyUI) 代码库的混合。

此外，感谢 [daswer123](https://github.com/daswer123) 贡献了 Canvas 缩放功能！

## 更新日志

日志 [在此](https://github.com/mashb1t/Fooocus/blob/main/update_log.md) 。

## 本地化/翻译/I18N

您可以将 json 文件放在 `language` 文件夹中，以翻译用户界面。

例如，下面是 `Fooocus/language/example.json` 的内容：

```json
{
  "Generate": "生成",
  "Input Image": "入力画像",
  "Advanced": "고급",
  "SAI 3D Model": "SAI 3D Modèle"
}
```

如果你添加 `--language example` 参数，Fooocus 将读取 `Fooocus/language/example.json` 来翻译界面。

例如，你可以编辑 Windows `run.bat` 的结尾行

```vim
.\python_embeded\python.exe -s Fooocus\entry_with_update.py --language example
```

或者运行 `run_anime.bat`

```stylus
.\python_embeded\python.exe -s Fooocus\entry_with_update.py --language example --preset anime
```

或者运行 `run_realistic.bat`

```stylus
.\python_embeded\python.exe -s Fooocus\entry_with_update.py --language example --preset realistic
```

为了实际翻译，你可以创建自己的文件，例如 `Fooocus/language/jp.json` 或 `Fooocus/language/cn.json` ，然后使用标志 `--language jp` 或 `--language cn` 。显然，这些文件目前不存在。 **我们需要你的帮助来创建这些文件！**

请注意，如果未给出 `--language` 并且同时存在 `Fooocus/language/default.json` ，Fooocus 将始终加载 `Fooocus/language/default.json` 进行翻译。默认情况下，文件 `Fooocus/language/default.json` 不存在。