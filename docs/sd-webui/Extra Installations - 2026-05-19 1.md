---
title: "推理参考"
source: "https://github.com/Haoming02/sd-webui-forge-classic/wiki/Inference-References"
author:
published: 2026-05-18
created: 2026-05-19
description: "The good ol' Forge WebUI, now updated with new features~ - Extra Installations · Haoming02/sd-webui-forge-classic Wiki"
tags:
  - "clippings"
taxonomy: { doc_category: [sd-webui] }
---
> [!tip] Tip
> 下方所有截图均包含信息文本（Infotext），其中记录了所使用的模型、提示词以及参数。

## SD1

![](https://github.com/Haoming02/sd-webui-forge-classic/wiki/assets/ref/SD1.jpeg)

- [Realistic Vision](https://civitai.com/models/4201/realistic-vision-v60-b1?modelVersionId=130072)
- [EasyNegative](https://civitai.com/models/7808/easynegative)

## SDXL

![](https://github.com/Haoming02/sd-webui-forge-classic/wiki/assets/ref/SDXL.jpeg)

- [均匀混合](https://civitai.com/models/1568837/evenly-mix?modelVersionId=2099823)

## Flux.1-Dev

![](https://github.com/Haoming02/sd-webui-forge-classic/wiki/assets/ref/Flux.jpeg)

- [Flux.1-Krea-Dev（Nunchaku）](https://huggingface.co/nunchaku-ai/nunchaku-flux.1-krea-dev/tree/main)

## Flux.1-Kontext-Dev

![](https://github.com/Haoming02/sd-webui-forge-classic/wiki/assets/ref/Kontext.jpeg)

- [Flux.1-Kontext-Dev (Nunchaku)](https://huggingface.co/nunchaku-ai/nunchaku-flux.1-kontext-dev/tree/main)

## Flux.2-Klein

##### 文生图

![](https://github.com/Haoming02/sd-webui-forge-classic/wiki/assets/ref/Klein9B.jpeg)

- [Flux.2-Klein-9B-fp8](https://huggingface.co/black-forest-labs/FLUX.2-klein-9b-fp8)

##### 编辑

![](https://github.com/Haoming02/sd-webui-forge-classic/wiki/assets/ref/Klein4B.jpeg)

- [Flux.2-Klein-4B](https://huggingface.co/black-forest-labs/FLUX.2-klein-4B)

## Qwen-Image-Edit

##### 多图像输入

![](https://github.com/Haoming02/sd-webui-forge-classic/wiki/assets/ref/Qwen-Edit.jpeg)

- [Qwen 图像编辑（双截棍）（251115 闪电）](https://huggingface.co/nunchaku-ai/nunchaku-qwen-image-edit-2509/tree/main/lightning-251115)

## Z-Image-Turbo

![](https://github.com/Haoming02/sd-webui-forge-classic/wiki/assets/ref/ZIT.jpeg)

- [Z 图像加速 (fp8\_scaled)](https://huggingface.co/Kijai/Z-Image_comfy_fp8_scaled/tree/main)

## Anima

![](https://github.com/Haoming02/sd-webui-forge-classic/wiki/assets/ref/Anima.jpeg)

- [Anima-Base-v1.0](https://huggingface.co/circlestone-labs/Anima/tree/main/split_files/diffusion_models)

## Ernie-Image-Turbo

![](https://github.com/Haoming02/sd-webui-forge-classic/wiki/assets/ref/Ernie.jpeg)

- [Ernie Image Turbo (nvfp4)](https://huggingface.co/Bedovyy/ERNIE-Image-Quantized/tree/main)

## Wan 2.2

##### 文生图

![](https://github.com/Haoming02/sd-webui-forge-classic/wiki/assets/ref/Wan.jpeg)

- [Wan 2.2 T2V (fp8\_scaled)](https://huggingface.co/Comfy-Org/Wan_2.2_ComfyUI_Repackaged/tree/main/split_files/diffusion_models)

---

> [!tip] Tip
> 对于模块（即文本编码器与 VAE），请参阅下载模型

> [!important] Important
> 使用蒸馏模型时（例如 `Flux-Dev` 、 `Lightning` 、 `Lightx2v` ），请将 CFG 设置为 `1.0`

> [!caution] Caution
> 除非您清楚自己在做什么，否则请勿将 Diffusion 的低位模式设置为 `Automatic`

请给我买杯咖啡~ ☕