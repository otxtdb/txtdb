---
title: "llama.cpp功能矩阵"
source: "https://github.com/ggml-org/llama.cpp/wiki/Feature-matrix"
author:
  - "[[GitHub]]"
published:
created: 2026-02-26
description: "LLM inference in C/C++. Contribute to ggml-org/llama.cpp development by creating an account on GitHub."
tags:
  - "clippings"
taxonomy: { doc_category: [llama.cpp] }
---


|  | **CPU (AVX/AVX2)** | **CPU (ARM NEON)** | **Metal** | **CUDA** | **ROCm** | **SYCL** | **Vulkan** | **Kompute** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| **K-quants** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ 🐢⁵ | 🚫 |
| **I-quants** | ✅ 🐢⁴ | ✅ 🐢⁴ | ✅ 🐢⁴ | ✅ | ✅ | 部分¹ | ✅ 🐢⁴ | 🚫 |
| **并行多 GPU⁶** | N/A | N/A | N/A | ✅ | ✅ | 仅顺序 | 仅顺序 | ❓ |
| **K 缓存量化** | ✅ | ✅ | ✅ | ✅ | ✅ | ❓ | ✅ | 🚫 |
| **MoE 架构** | ✅ | ✅ | ✅ | ✅ | ✅ | ❓ | ✅ | 🚫 |
| **Flash Attention** | ✅ | ✅ | ✅ | ✅ | ✅ | ❓ | ✅ | 🚫 |

- ✅: 功能正常
- 🚫: 功能无法正常工作
- ❓: 未知，如果你能自行测试，请贡献
- 🐢: 功能运行缓慢
- ¹: IQ3\_S 和 IQ1\_S，参见 #5886
- ²: 仅使用 `-ngl 0`
- ³: 推理速度慢50%
- ⁴: 比同等大小的 K-quants 慢
- ⁵: 通常 CUDA 或 ROCM 后端更快，尽管在某些情况下 Vulkan 的文本生成更快。有关基准测试，请参阅#10879。
- ⁶: 默认情况下，所有 GPU 后端可以通过依次运行来利用多个设备。CUDA 代码（也通过 HIP 用于 ROCm）还包含通过 `--split-mode row` 并行运行 GPU 的代码。然而，这种优化相对较差，并且只有在互连速度比单个 GPU 速度快时才会更快。
