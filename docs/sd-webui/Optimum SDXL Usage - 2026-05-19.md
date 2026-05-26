---
title: "Optimum SDXL 的使用"
source: "https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Optimum-SDXL-Usage"
author:
published:
created: 2026-05-19
description: "Stable Diffusion web UI. Contribute to AUTOMATIC1111/stable-diffusion-webui development by creating an account on GitHub."
tags:
  - "clippings"
taxonomy: { doc_category: [sd-webui] }
---
以下是针对您配置需要调整的内容清单：

## 命令行参数：

- NVIDIA（12GB 及以上） `--xformers`
- NVIDIA（8GB） `--medvram-sdxl --xformers`
- Nvidia (4gb) `--lowvram --xformers`
- AMD (4GB) `--lowvram --opt-sub-quad-attention` + 在设置中启用 TAESD 无论是 ROCm 还是 DirectML，都会以 fp16 精度生成至少 1024x1024 的图片。如果您的 AMD 显卡需要 --no-half 参数，请尝试启用 --upcast-sampling，因为完整精度的 SDXL 模型对于 4GB 显存来说过大而无法容纳。

## 系统：

- (Windows) 并非所有 NVIDIA 驱动程序都能与 Stable Diffusion 良好兼容。所有版本高于 531 的驱动程序在 Windows 上生成接近或达到显卡最大显存容量的大型图像时，均可能导致极端的性能下降。为缓解这种潜在的速度退化，请遵循 NVIDIA 在其网站上列出的步骤：[https://nvidia.custhelp.com/app/answers/detail/a\_id/5490](https://nvidia.custhelp.com/app/answers/detail/a_id/5490) 相关问题：(vladmandic/automatic/discussions/1285)、(#11063)。
- (Linux) 安装 `tcmalloc` ，可大幅降低内存占用： `sudo apt install --no-install-recommends google-perftools` (#10117)。
- 添加页面文件/交换文件，以防止因内存不足导致权重加载失败。
- 使用 SSD 固态硬盘以加快加载速度，特别是当需要页面文件时。
- Windows 11 系统至少需要 24GB 内存，Windows 10 系统至少需要 16GB 内存

## 模型权重：

- 请使用 sdxl-vae-fp16-fix；这是一种无需在 fp32 精度下运行的 VAE。这将几乎不损失质量的前提下提升速度并降低显存占用。
- 使用 TAESD；这是一种以牺牲部分质量为代价、大幅降低显存占用的 VAE。