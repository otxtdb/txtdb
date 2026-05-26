---
title: "优化"
source: "https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Optimizations"
author:
published:
created: 2026-05-19
description: "Stable Diffusion web UI. Contribute to AUTOMATIC1111/stable-diffusion-webui development by creating an account on GitHub."
tags:
  - "clippings"
taxonomy: { doc_category: [sd-webui] }
---

| 命令行参数                           | 说明                                                                                                                                                                                                                         |
| ------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `--opt-sdp-attention`           | 在某些系统上，这可能导致比使用 xFormers 更快的速度，但需要更多的显存。（非确定性）                                                                                                                                                                             |
| `--opt-sdp-no-mem-attention`    | 在某些系统上，May 的生成速度可能快于使用 xFormers，但需要更多显存。（确定性模式，略慢于 `--opt-sdp-attention` ，且占用更多显存）                                                                                                                                         |
| `--xformers`                    |                                                                                                                                                                                                                            |
| `--force-enable-xformers`       | 无论程序是否认为可以运行，均启用 xFormers。请勿报告由此引发的任何错误。                                                                                                                                                                                   |
| `--opt-split-attention`         | 交叉注意力层优化可显著降低内存占用，几乎无需额外成本（部分用户反馈性能有所提升）。堪称“黑魔法”。   默认开启 `torch.cuda` ，适用于 NVIDIA 和 AMD 显卡。                                                                                                                                |
| `--disable-opt-split-attention` | 禁用上述优化。                                                                                                                                                                                                                    |
| `--opt-sub-quad-attention`      | 次二次方注意力机制：一种内存高效的交叉注意力层优化，可显著降低所需显存，有时会以轻微的性能损失为代价。若在使用 xFormers 无法支持的硬件/软件配置下出现性能不佳或生成失败的情况，建议开启此选项。在 macOS 系统上，开启此项还可支持生成更大尺寸的图像。                                                                                        |
| `--opt-split-attention-v1`      | 使用上述优化的旧版本，该版本对显存占用更低（会消耗更少 VRAM，但会对可生成的图片最大尺寸施加更严格的限制）。                                                                                                                                                                   |
| `--medvram`                     | 通过将模型拆分为三个部分——cond（用于将文本转换为数值表示）、first\_stage（用于将图片转换为潜在空间并还原）和 unet（用于对潜在空间进行实际去噪），使 Stable Diffusion 模型在 VRAM 中的占用量减少，同时确保同一时间仅有一个部分位于 VRAM 中，其余部分则移至 CPU 内存。这会降低性能，但降幅很小——除非启用了实时预览。                                    |
| `--lowvram`                     | 这是对上述优化的更彻底版本，将 unet 拆分为多个模块，并仅保留一个模块在 VRAM 中。对性能影响巨大。                                                                                                                                                                     |
| `*do-not-batch-cond-uncond`     | 仅在 1.6.0 版本之前有效：防止在采样过程中对正向和反向提示词进行批处理，这实际上允许以 0.5 的批次大小运行，从而节省大量内存。会降低性能。这不是一个命令行选项，而是通过使用 `--medvram` 或 `--lowvram` 隐式启用的优化。在 1.6.0 版本中，此优化不再通过任何命令行标志启用，而是默认启用。它可以在设置中的 `Batch cond/uncond` 类别下的 `Optimizations` 选项中禁用。 |
| `--always-batch-cond-uncond`    | 仅在 1.6.0 版本之前有效：禁用上述优化。仅在与 `--medvram` 或 `--lowvram` 一起使用时才有意义。在 1.6.0 版本中，此命令行标志无效。                                                                                                                                       |
| `--opt-channelslast`            | 将 Stable Diffusion 的 PyTorch 内存类型更改为通道最后（channels last）。效果尚未得到充分研究。                                                                                                                                                        |
| `--upcast-sampling`             | 对于 NVIDIA 和 AMD 显卡，通常强制以 `--no-half` 模式运行，应能提高生成速度。                                                                                                                                                                        |

自版本 1.3.0 起，可在设置中选择 `Cross attention optimization` 。xFormers 仍需通过 `COMMANDLINE_ARGS` 启用。 ![change-cross-attention-optimization](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/images/change-cross-attention-optimization.png) 

额外提示（Windows）：

- [https://github.com/AUTOMATIC1111/stable-diffusion-webui/discussions/3889](https://github.com/AUTOMATIC1111/stable-diffusion-webui/discussions/3889) 禁用硬件 GPU 调度。
- 禁用浏览器硬件加速
- 进入 NVIDIA 控制面板，在“3D 设置”中将电源管理模式更改为“最高性能”

## 优化器与标志对内存及性能的影响

*这是一个使用特定硬件和配置进行的示例测试，您的结果可能有所不同。*  
*使用 nVidia RTX3060 和 CUDA 11.7 进行测试。*

| 交叉注意力 | 批处理大小为 1/2/4/8/16 时的峰值内存 | 初始推理速度（次/秒） | 峰值推理速度（次/秒） | 备注 |
| --- | --- | --- | --- | --- |
| 无 | 4.1 / 6.2 / OOM / OOM / OOM | 4.2 | 4.6 | 缓慢且早期出现内存溢出 |
| 版本 v1 | 2.8 / 2.8 / 2.8 / 3.1 / 4.1 | 4.1 | 4.7 | 速度较慢但内存占用最低，且不依赖有时会出现问题的 xFormers |
| InvokeAI | 3.1 / 4.2 / 6.3 / 6.6 / 7.0 | 5.5 | 6.6 | 几乎与默认优化器相同 |
| Doggetx | 3.1 / 4.2 / 6.3 / 6.6 / 7.1 | 5.4 | 6.6 | 默认 |
| Doggetx | 2.2 / 2.7 / 3.8 / 5.9 / 6.2 | 4.1 | 6.3 | 使用 `medvram` 预设可在节省可观内存的同时，避免性能大幅下降 |
| Doggetx | 0.9 / 1.1 / 2.2 / 4.3 / 6.4 | 1.0 | 6.3 | 使用 `lowvram` 预设速度极慢，因为频繁发生交换 |
| xFormers | 2.8 / 2.8 / 2.8 / 3.1 / 4.1 | 6.5 | 7.5 | 最快且占用内存最低 |
| xFormers | 2.9 / 2.9 / 2.9 / 3.6 / 4.1 | 6.4 | 7.6 | 配合 `cuda_alloc_conf` 和 `opt-channelslast 使用` |

备注：

- 批量大小为 1 时的性能约为峰值性能的 ~70%
- 峰值性能通常出现在批量大小约为 8 时  
	在此之后，若拥有额外的显存，性能会增长数个百分点，直到因垃圾回收（GC）介入而开始下降
- 使用 `lowvram` 预设的性能在批量大小低于 8 时非常低，而此时的内存节省效果也不显著。

其他可能的优化方案：

- 在 `webui-user.bat` 中添加 `set PYTORCH_CUDA_ALLOC_CONF=garbage_collection_threshold:0.9,max_split_size_mb:512`  
	此举不会对性能产生影响，虽然会略微增加初始内存占用，但能减少长时间运行时的内存碎片化问题
- `opt-channelslast`  
	Hit-and-miss：看起来随着批量大小增加会有轻微的性能提升，而小批量时则较慢，但差异在误差范围内。