---
title: "(rocm) 修复因缺少 miopen 缓存而导致的随机重启问题"
source: "https://github.com/AUTOMATIC1111/stable-diffusion-webui/discussions/13275"
author:
published:
created: 2026-05-19
description: "Wiki: AMDGPU tip to prevent restarts on Linux"
tags:
  - "clippings"
taxonomy: { doc_category: [sd-webui] }
---
你好，

使用 Navi22 显卡时，Stable Diffusion 对我而言大部分运行正常，但生成图像时偶尔出现的随机重启问题一直困扰着我。

经过几个月的摸索，我发现了一个解决方案。

基本原因是：如果系统中没有 miopen 的缓存文件，计算机需要重新生成它们，而在此过程中似乎会导致系统进入某种锁定状态或仅仅是温度过高所致。

我防止生成时随机重启的解决方案是进行几次强制低性能 DPM 的生成。您可能需要根据不同使用场景（如 txt2img、Hires、img2img 等）调整生成次数。

`echo 'low' > /sys/module/amdgpu/drivers/pci\:amdgpu/0000\:03\:00.0/power_dpm_force_performance_level`

一旦您对结果感到满意，请将其恢复为正常设置；此时缓存已存在，不会再触发任何问题。

`echo 'auto' > /sys/module/amdgpu/drivers/pci\:amdgpu/0000\:03\:00.0/power_dpm_force_performance_level`

---

另一个提升生成效果的技巧是将 VAE 默认设置为 TAESD。它运行迅速且不易卡顿，效果远优于 Tiled VAE 扩展。

---

此前我需要使用 --no-half-vae 和 --medvram 参数来防止冻结，但在使用上述技巧后已不再需要。SD 和 SDXL 均能非常流畅地运行。