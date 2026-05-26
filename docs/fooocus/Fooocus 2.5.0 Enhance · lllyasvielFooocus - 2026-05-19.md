---
title: "Fooocus 2.5.0：增强"
source: "https://github.com/lllyasviel/Fooocus/discussions/3281"
author:
published:
created: 2026-05-19
description: "Fooocus 2.5.0: Enhance"
tags:
  - "clippings"
taxonomy: { doc_category: [fooocus] }
---
## Fooocus 2.5.0: 增强

这次发布包含了一个社区多次请求的功能（例如在 [#3113](https://github.com/lllyasviel/Fooocus/issues/3113) 、 [#3089](https://github.com/lllyasviel/Fooocus/discussions/3089) 、 [#3039](https://github.com/lllyasviel/Fooocus/discussions/3039) 以及几个其他地方，也请参见 [#3122](https://github.com/lllyasviel/Fooocus/discussions/3122) ）。该功能由在 [v2.5.0 (分支)](https://github.com/mashb1t/Fooocus/releases/tag/v2.5.0) / [mashb1t#42](https://github.com/mashb1t/Fooocus/discussions/42) 实现，现在已可在主分支中使用。

## 这个功能有什么作用？

Enhance 允许你根据提示或输入图像自动放大和/或改进图像的某些部分。  
它与 ADetailer（ [仓库](https://github.com/Bing-su/adetailer) ）类似，但提供了更好的、更灵活的对象检测和替换功能，使用检测和替换提示代替静态检测模型，每个模型大小约为 140MB。

## 如何使用它？

### Disclaimer

强烈建议使用性能 `  速度  ` 或 `  质量  ` （不加载 LoRA 的性能），因为任何 inpaint 引擎都会使用 LoRA，而与其他性能 LoRAs 结合时可能无法产生最佳效果。  
使用 inpaint 模式 ` 改进细节（面部、手部、眼睛等）` 不会设置 inpaint 引擎，因此与所有性能兼容。有关 inpaint 模式的文档可以在这里找到： [#414](https://github.com/lllyasviel/Fooocus/discussions/414)  
所有这些情况也适用于没有增强的正常 inpainting。

ControlNets (`ImagePrompt`, `PyraCanny`, `CPDS`, `FaceSwap`) 目前不支持用于增强步骤，但可以用于作为增强基础的图像生成。

### With image generation

1. 使用您想要的设置生成任何图像
2. 如果您满意，禁用随机种子并打开增强选项卡  
	2.1. (可选) 启用并定义顺序上采样或变化（默认禁用）  
	2.2. 启用并配置任意数量的其他改进步骤。  
	2.3. 输入检测提示（你想在图像中检测的内容）  
	2.4. 输入正面/负面提示（你想用其替换检测到的蒙版，如果未设置则默认使用你的正常提示）
3. 生成图像

### Based on an existing image

只需打开图像输入，将图像上传到增强选项卡。将跳过提示处理，仅处理增强步骤。按照上述第2+步操作。  
您可以设置 `--enable-auto-describe-image` 在图像上传后自动生成提示。

## 示例

UI

[![screencapture-localhost-7865-2024-06-17-00_13_50](https://private-user-images.githubusercontent.com/9307310/340138566-f2e6f9ac-87e0-46ca-b10e-ba6d67ab8724.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxNzk1MTgsIm5iZiI6MTc3OTE3OTIxOCwicGF0aCI6Ii85MzA3MzEwLzM0MDEzODU2Ni1mMmU2ZjlhYy04N2UwLTQ2Y2EtYjEwZS1iYTZkNjdhYjg3MjQucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI2MDUxOSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNjA1MTlUMDgyNjU4WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9ZjhlNzRjY2FiZjg1NzZmYzNlMGQ5NGIxZDlkMjlmZDU1NTViODRlNGViZmUwNzQyNTk2Mjg3YzRjMjIzZGFhNyZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmcmVzcG9uc2UtY29udGVudC10eXBlPWltYWdlJTJGcG5nIn0.HlP8s4nStbObWpnyxRpl1cJjx-CpIIxuYI3-DMjULW4)](https://private-user-images.githubusercontent.com/9307310/340138566-f2e6f9ac-87e0-46ca-b10e-ba6d67ab8724.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxNzk1MTgsIm5iZiI6MTc3OTE3OTIxOCwicGF0aCI6Ii85MzA3MzEwLzM0MDEzODU2Ni1mMmU2ZjlhYy04N2UwLTQ2Y2EtYjEwZS1iYTZkNjdhYjg3MjQucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI2MDUxOSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNjA1MTlUMDgyNjU4WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9ZjhlNzRjY2FiZjg1NzZmYzNlMGQ5NGIxZDlkMjlmZDU1NTViODRlNGViZmUwNzQyNTk2Mjg3YzRjMjIzZGFhNyZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmcmVzcG9uc2UtY29udGVudC10eXBlPWltYWdlJTJGcG5nIn0.HlP8s4nStbObWpnyxRpl1cJjx-CpIIxuYI3-DMjULW4)

| [原文（生成）](https://gallery.mashb1t.de/gallery/-8ubXvDC-HwkxOv8Oem8cabO/vd1Wm0E8WZdNbimHmVzTXTR_) | 增强 |
| --- | --- |
| [![22732ab04379cb552d97ebf38de6](https://private-user-images.githubusercontent.com/9307310/340138585-06aced0d-a967-4b58-ac5a-ae7fd5fbf62a.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxNzk1MTgsIm5iZiI6MTc3OTE3OTIxOCwicGF0aCI6Ii85MzA3MzEwLzM0MDEzODU4NS0wNmFjZWQwZC1hOTY3LTRiNTgtYWM1YS1hZTdmZDVmYmY2MmEucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI2MDUxOSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNjA1MTlUMDgyNjU4WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9MTgzZWU3YmQzMzlmYjZkMjU2NWIzODk5MjM3NzE5NDkxZGE2NmVkZTFiZWExNzgyMzUxYThiNzlhYjYxMzgxNyZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmcmVzcG9uc2UtY29udGVudC10eXBlPWltYWdlJTJGcG5nIn0.VSP8hm1yDZTBVzhPet-4k7S-jB6q4WbNwN9dCHnyaxE)](https://private-user-images.githubusercontent.com/9307310/340138585-06aced0d-a967-4b58-ac5a-ae7fd5fbf62a.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxNzk1MTgsIm5iZiI6MTc3OTE3OTIxOCwicGF0aCI6Ii85MzA3MzEwLzM0MDEzODU4NS0wNmFjZWQwZC1hOTY3LTRiNTgtYWM1YS1hZTdmZDVmYmY2MmEucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI2MDUxOSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNjA1MTlUMDgyNjU4WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9MTgzZWU3YmQzMzlmYjZkMjU2NWIzODk5MjM3NzE5NDkxZGE2NmVkZTFiZWExNzgyMzUxYThiNzlhYjYxMzgxNyZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmcmVzcG9uc2UtY29udGVudC10eXBlPWltYWdlJTJGcG5nIn0.VSP8hm1yDZTBVzhPet-4k7S-jB6q4WbNwN9dCHnyaxE) | [![image - 2024-06-17T001252 624](https://private-user-images.githubusercontent.com/9307310/340138599-33fd2d83-73c0-4192-b99e-515c39ae853f.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxNzk1MTgsIm5iZiI6MTc3OTE3OTIxOCwicGF0aCI6Ii85MzA3MzEwLzM0MDEzODU5OS0zM2ZkMmQ4My03M2MwLTQxOTItYjk5ZS01MTVjMzlhZTg1M2YucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI2MDUxOSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNjA1MTlUMDgyNjU4WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9YjY2NzlmNjFkNGJmYjI3YzA2ODI4NGZkMWRkZjgzOTEyODJlZWZkMmIxNmM3YWM4ZWEyNjFmMmYxMjhlM2U5ZCZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmcmVzcG9uc2UtY29udGVudC10eXBlPWltYWdlJTJGcG5nIn0.13HWLKmOFHVopaNxp1UTKFHu6VRIzFy-GqvODL1I5IQ)](https://private-user-images.githubusercontent.com/9307310/340138599-33fd2d83-73c0-4192-b99e-515c39ae853f.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxNzk1MTgsIm5iZiI6MTc3OTE3OTIxOCwicGF0aCI6Ii85MzA3MzEwLzM0MDEzODU5OS0zM2ZkMmQ4My03M2MwLTQxOTItYjk5ZS01MTVjMzlhZTg1M2YucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI2MDUxOSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNjA1MTlUMDgyNjU4WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9YjY2NzlmNjFkNGJmYjI3YzA2ODI4NGZkMWRkZjgzOTEyODJlZWZkMmIxNmM3YWM4ZWEyNjFmMmYxMjhlM2U5ZCZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmcmVzcG9uc2UtY29udGVudC10eXBlPWltYWdlJTJGcG5nIn0.13HWLKmOFHVopaNxp1UTKFHu6VRIzFy-GqvODL1I5IQ) |

| 原文（生成） | 放大（之前） | `#1` 黄色连衣裙 | `#2` 手部替换 |
| --- | --- | --- | --- |
| [![342070683-260e6a0b-5f42-47a3-83fd-fc3f4310d3a7](https://private-user-images.githubusercontent.com/9307310/348566079-f273197c-1c12-44a9-b097-ad2e77de643f.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxNzk1MTgsIm5iZiI6MTc3OTE3OTIxOCwicGF0aCI6Ii85MzA3MzEwLzM0ODU2NjA3OS1mMjczMTk3Yy0xYzEyLTQ0YTktYjA5Ny1hZDJlNzdkZTY0M2YucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI2MDUxOSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNjA1MTlUMDgyNjU4WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9YmRjNmY4ZGY4ZDg3MDMxYzVjOTU4N2FjYTk0MTg5MWVmMDA5MGRlZmY5YjU4OTlkNTVhMWI0Zjc1NGFkMGQ3YSZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmcmVzcG9uc2UtY29udGVudC10eXBlPWltYWdlJTJGcG5nIn0.L4wv4WAmT-P93-lHhEHXuCezoIugiKId_GFga91q8l8)](https://private-user-images.githubusercontent.com/9307310/348566079-f273197c-1c12-44a9-b097-ad2e77de643f.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxNzk1MTgsIm5iZiI6MTc3OTE3OTIxOCwicGF0aCI6Ii85MzA3MzEwLzM0ODU2NjA3OS1mMjczMTk3Yy0xYzEyLTQ0YTktYjA5Ny1hZDJlNzdkZTY0M2YucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI2MDUxOSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNjA1MTlUMDgyNjU4WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9YmRjNmY4ZGY4ZDg3MDMxYzVjOTU4N2FjYTk0MTg5MWVmMDA5MGRlZmY5YjU4OTlkNTVhMWI0Zjc1NGFkMGQ3YSZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmcmVzcG9uc2UtY29udGVudC10eXBlPWltYWdlJTJGcG5nIn0.L4wv4WAmT-P93-lHhEHXuCezoIugiKId_GFga91q8l8) | [![image](https://private-user-images.githubusercontent.com/9307310/348566097-41da80f2-7fbe-482a-b4ab-e60cf1c7954a.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxNzk1MTgsIm5iZiI6MTc3OTE3OTIxOCwicGF0aCI6Ii85MzA3MzEwLzM0ODU2NjA5Ny00MWRhODBmMi03ZmJlLTQ4MmEtYjRhYi1lNjBjZjFjNzk1NGEucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI2MDUxOSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNjA1MTlUMDgyNjU4WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9YTRiMzVkYzBlMGJjMTc2NGEwMjk5MmI3MDI1NjNkYzE5MjFjOThjMGY4OWZiZDBjZjY2MzY0OGQ1NWI4ZDAxNiZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmcmVzcG9uc2UtY29udGVudC10eXBlPWltYWdlJTJGcG5nIn0.5eSmx2jm_MsGb12qVgkMFpCBr4O5J3AOQszy6CoijD4)](https://private-user-images.githubusercontent.com/9307310/348566097-41da80f2-7fbe-482a-b4ab-e60cf1c7954a.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxNzk1MTgsIm5iZiI6MTc3OTE3OTIxOCwicGF0aCI6Ii85MzA3MzEwLzM0ODU2NjA5Ny00MWRhODBmMi03ZmJlLTQ4MmEtYjRhYi1lNjBjZjFjNzk1NGEucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI2MDUxOSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNjA1MTlUMDgyNjU4WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9YTRiMzVkYzBlMGJjMTc2NGEwMjk5MmI3MDI1NjNkYzE5MjFjOThjMGY4OWZiZDBjZjY2MzY0OGQ1NWI4ZDAxNiZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmcmVzcG9uc2UtY29udGVudC10eXBlPWltYWdlJTJGcG5nIn0.5eSmx2jm_MsGb12qVgkMFpCBr4O5J3AOQszy6CoijD4) |  |  |

## 放大或变化

在第一次增强之前

- 始终使用原始提示进行放大或变化
- 由于画布尺寸更大，增强时细节得到改善
- 由于使用 1024x1024 进行修复，图像构图背景减少
- 推荐用于增强较小区域（细节、面部、眼睛）

上次增强后

- 可能会对图像应用已被增强修复的更改
- 推荐用于增强大面积（背景、衣服、整个人物）
- 选择用于上采样或变化的提示，使用原始提示或最后填充的非空值增强提示（提高主体识别，防止增强后主体变回原始提示。当大幅改变原始提示中描述的主体时使用）

| 原始（生成） | 放大（之前） | 增强 |
| --- | --- | --- |
|  |  |  |

| 《Fooocus 2.5.0: 增强 · lllyasviel/Fooocus · 讨论 #3281》 | 增强 | 放大（后） |
| --- | --- | --- |
|  |  |  |

## 模型

默认情况下，它使用 SAM（ [网站](https://segment-anything.com/) ， [仓库](https://segment-anything.com/) ）遮罩模型，由 GroundingDINO（ [论文](https://arxiv.org/abs/2303.05499) ， [diffusers 文档](https://huggingface.co/docs/transformers/model_doc/grounding-dino) ）支持，但同时也支持 RemBG（ [仓库](https://github.com/danielgatis/rembg?tab=readme-ov-file#models) ）目前支持的所有其他模型。GroundingDINO + SAM 不使用 RemBG 作为处理器，而是已原生集成到 Fooocus 中，以获得更好的效果和更高的控制级别。

目前支持的模型：

- SAM + GroundingDINO (默认设置): 一种模型组合，允许在检测到的框内进行目标检测提示和分割，有 3 种变体（ [基础（默认）](https://huggingface.co/mashb1t/misc/resolve/main/sam_vit_b_01ec64.pth) 、 [大型](https://huggingface.co/mashb1t/misc/resolve/main/sam_vit_l_0b3195.pth) 、 [巨型](https://huggingface.co/mashb1t/misc/resolve/main/sam_vit_h_4b8939.pth) ）
- u2net ( [下载](https://github.com/danielgatis/rembg/releases/download/v0.0.0/u2net.onnx) , [源代码](https://github.com/xuebinqin/U-2-Net) ): 适用于一般用途的预训练模型。
- u2netp ( [下载](https://github.com/danielgatis/rembg/releases/download/v0.0.0/u2netp.onnx) , [源代码](https://github.com/xuebinqin/U-2-Net) ): u2net 模型的轻量级版本。
- u2net\_human\_seg ( [下载](https://github.com/danielgatis/rembg/releases/download/v0.0.0/u2net_human_seg.onnx) , [源代码](https://github.com/xuebinqin/U-2-Net) ): 用于人体分割的预训练模型。
- u2net\_cloth\_seg ( [下载](https://github.com/danielgatis/rembg/releases/download/v0.0.0/u2net_cloth_seg.onnx) , [源码](https://github.com/levindabhi/cloth-segmentation) ): 一个用于人类肖像布料解析的预训练模型。这里衣服被解析为 3 个类别：上身、下身和全身。
- silueta ( [下载](https://github.com/danielgatis/rembg/releases/download/v0.0.0/silueta.onnx) , [Model size reduced to 43Mb! and new Webapp xuebinqin/U-2-Net#295](https://github.com/xuebinqin/U-2-Net/issues/295)): 与 u2net 相同，但大小减小到 43Mb。
- isnet-general-use ( [下载](https://github.com/danielgatis/rembg/releases/download/v0.0.0/isnet-general-use.onnx) , [源码](https://github.com/xuebinqin/DIS) ): 一个用于通用场景的预训练模型。
- isnet-anime ( [下载](https://github.com/danielgatis/rembg/releases/download/v0.0.0/isnet-anime.onnx) , [源码](https://github.com/SkyTNT/anime-segmentation) ): 一个用于动漫角色的高精度分割模型。

## 技术债务 / 代码改进

在实现增强功能时，引入了多种方法以使代码可重用并支持迭代。  
整个 async\_worker.py 文件已被重构，现在阅读和理解起来更加清晰，使用也更加方便。

## 调试

请查看开发者调试模式 > Inpaint 中的调试选项：

- 调试增强遮罩：输出生成的遮罩，默认禁用
- 调试 GroundingDINO：检测过程中早期返回，使用 GroundingDINO 边框而不是边框内的精细 SAM 检测。当 SAM 无法正确检测 GroundingDINO 边框内部时，这个选项有时能改善结果。注意：GroundingDINO 支持检测提示，SAM 在边框内自动检测对象无需进一步提示。
- GroundingDINO 边框腐蚀或膨胀：通过 GroundingDINO 增加/减少检测框面积。当 GroundingDINO 意外裁剪元素时（非常罕见），这个选项有时能改善 SAM 检测。