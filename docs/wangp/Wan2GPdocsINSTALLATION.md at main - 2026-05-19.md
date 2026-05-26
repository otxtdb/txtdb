---
title: "安装指南 - RTX 10XX 至 RTX 50XX 的完整设置说明"
source: "https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/INSTALLATION.md"
author:
published:
created: 2026-05-19
description: "A fast AI Video Generator for the GPU Poor. Supports Wan 2.1/2.2, Qwen Image, Hunyuan Video, LTX  Video and Flux. - Wan2GP/docs/INSTALLATION.md at main · deepbeepmeep/Wan2GP"
tags:
  - "clippings"
taxonomy: { doc_category: [wangp] }
---
## Windows & Linux 的手动安装指南

本指南涵盖了不同 GPU 代次和操作系统的手动安装。或者您可以使用一键安装/更新脚本（请查看仓库 readme 获取说明）。

建议使用 Python 3.10.9、PyTorch 2.7.1 配合 Cuda 12.8（适用于 GTX 10XX 系列），或使用 Python 3.11.14、PyTorch 2.10 配合 Cuda 13.0/13.1（适用于 RTX 30XX - RTX 50XX 系列），因为这两种配置都经过充分测试且稳定。

不推荐使用 PyTorch 2.8.0，因为在切换模型时观察到一些系统 RAM 内存泄漏问题，也不推荐使用 2.9.0，因为它存在一些 3D 卷积性能问题（导致 VAE VRAM 需求激增）。

如果您想使用为 RTX 50xx 优化的 NV FP4 内核，如果您仍在使用基于 cuda 12.8 的旧安装设置，则需要升级到 Python 3.11、PyTorch 2.10 以及 Cuda 13.0。

## 安装 Conda

您需要先安装 anaconda 或 miniconda（ [https://www.anaconda.com/download/success?reg=skipped](https://www.anaconda.com/download/success?reg=skipped) ）

## WanGP 最小安装

### RTX 20xx - RTX 50xx 安装

你必须安装 CUDA 13.1： [https://developer.nvidia.com/cuda-13-1-0-download-archive](https://developer.nvidia.com/cuda-13-1-0-download-archive)

然后打开一个终端窗口，进入你打算安装 WanGP 的父文件夹，然后输入：

```apache
git clone https://github.com/deepbeepmeep/Wan2GP.git
cd Wan2GP
conda create -n wan2gp python=3.11.14
conda activate wan2gp
pip install torch==2.10.0 torchvision==0.25.0 torchaudio==2.10.0 --index-url https://download.pytorch.org/whl/cu130
pip install -r requirements.txt
```

### GTX 10xx 安装

你必须安装 Cuda 12.8： [https://developer.nvidia.com/cuda-12-8-0-download-archive](https://developer.nvidia.com/cuda-12-8-0-download-archive)

然后打开一个终端窗口，进入你打算安装 WanGP 的父文件夹，然后输入：

```apache
git clone https://github.com/deepbeepmeep/Wan2GP.git
cd Wan2GP
conda create -n wan2gp python=3.10.9
conda activate wan2gp
pip install torch==2.7.1 torchvision==0.22.1 torchaudio==2.7.1 --index-url https://download.pytorch.org/whl/test/cu128
pip install -r requirements.txt
```

## Triton 安装

Triton 库是 Pytorch 编译和 Sage Attention 所必需的，同时它也通过多种内核来加速张量处理。

### Windows RTX 20XX -RTX 30xx

```cmake
pip install -U "triton-windows<3.3"
```

### Windows RTX 40XX -RTX 50xx

```cmake
pip install triton-windows
```

### Linux

Triton 库在安装 pytorch 时应自动安装。

## Sage Attention

Sage Attention 可在几乎不损失质量的情况下将视频/图像生成速度提升高达 2 倍。Sage 不支持 GTX 10xx 显卡。

#### Windows 仅支持为 RTX 30XX 显卡安装 Sage Attention

这些显卡仅支持 Sage attention 1 版本

```apache
pip install sageattention==1.0.6
```

#### Windows 安装 Sage2 Attention for RTX 40XX-50xx

```apache
pip install https://github.com/woct0rdho/SageAttention/releases/download/v2.2.0-windows.post4/sageattention-2.2.0+cu130torch2.9.0andhigher.post4-cp39-abi3-win_amd64.whl
```

#### Linux 安装 Sage Attention（仅限 RTX 30XX）

仅支持这些 GPU 的 Sage 注意力 1

```apache
pip install sageattention==1.0.6
```

#### Linux 安装仅支持 RTX 40XX, 50XX 的 Sage 注意力。确保是 Sage 2.2.0

```bash
python -m pip install "setuptools<=75.8.2" --force-reinstall
git clone https://github.com/thu-ml/SageAttention
cd SageAttention 
pip install -e .
```

## 吸引注意力

Sparge Attention (`spas_sage_attn`) 提供了 FlashVSR 使用的优化稀疏注意力内核。在安装 Pytorch 和 Triton 之后安装它。

#### Windows 安装 Sparge Attention 用于 Pytorch 2.10 / Python 3.11 / Cuda 13

```apache
pip install https://github.com/woct0rdho/SpargeAttn/releases/download/v0.1.0-windows.post4/spas_sage_attn-0.1.0%2Bcu130torch2.9.0andhigher.post4-cp39-abi3-win_amd64.whl
```

#### Windows 安装 Sparge Attention 用于 Pytorch 2.7.1 / Python 3.10 / Cuda 12.8

```apache
pip install https://github.com/woct0rdho/SpargeAttn/releases/download/v0.1.0-windows.post3/spas_sage_attn-0.1.0%2Bcu128torch2.7.1.post3-cp39-abi3-win_amd64.whl
```

#### Linux 安装 Sparge 注意事项

```vim
python -m pip install ninja wheel packaging
python -m pip install --no-build-isolation git+https://github.com/woct0rdho/SpargeAttn.git
```

## Flash Attention

Flash Attention 在生成视频或图像时不如 Sage 快，但它能保持质量。然而，当与语言模型（提示增强器、文本到语音、Deepy）一起使用时，它可以显著提高速度。

### Flash Attention 窗口

#### 窗口 Pytorch 2.10 / Python 3.11

```awk
pip install https://github.com/deepbeepmeep/kernels/releases/download/Flash2/flash_attn-2.8.3-cp311-cp311-win_amd64.whl
```

#### Windows Pytorch 2.7.1 / Python 3.10

```apache
pip install https://github.com/Redtash1/Flash_Attention_2_Windows/releases/download/v2.7.0-v2.7.4/flash_attn-2.7.4.post1+cu128torch2.7.0cxx11abiFALSE-cp310-cp310-win_amd64.whl
```

#### Linux

```apache
pip install flash-attn==2.7.2.post1
```

## GGUF llama.cpp CUDA 内核

这些内核用于加速 GGUF 模型。

### 适用于 Python 3.11 / Pytorch 2.10 / CUDA 13 的 GGUF 内核轮

- Windows
	```awk
	pip install https://github.com/deepbeepmeep/kernels/releases/download/GGUF_Kernels/llamacpp_gguf_cuda-1.0.2+torch210cu13py311-cp311-cp311-win_amd64.whl
	```
- Linux
	```awk
	pip install https://github.com/deepbeepmeep/kernels/releases/download/GGUF_Kernels/llamacpp_gguf_cuda-1.0.2+torch210cu13py311-cp311-cp311-linux_x86_64.whl
	```

### GGUF 内核轮子适用于 Python 3.10 / Pytorch 2.7.1 / Cuda 12.8

- Windows
	```awk
	pip install https://github.com/deepbeepmeep/kernels/releases/download/GGUF_Kernels/llamacpp_gguf_cuda-1.0.2+torch271cu128py310-cp310-cp310-win_amd64.whl
	```
- Linux
	```awk
	pip install https://github.com/deepbeepmeep/kernels/releases/download/GGUF_Kernels/llamacpp_gguf_cuda-1.0.2+torch271cu128py310-cp310-cp310-linux_x86_64.whl
	```

## INT4 / FP4 量化支持

这些内核将提供优化的 INT4 / FP4 解量化功能。

**请注意，FP4 支持取决于硬件，并且仅适用于 RTX 50xx / sm120+ 显卡**

### Lightx2v NVP4 内核轮子适用于 Python 3.11 / Pytorch 2.10 / Cuda 13（仅限 RTX 50xx / sm120+！）

- Windows
	```apache
	pip install https://github.com/deepbeepmeep/kernels/releases/download/Light2xv/lightx2v_kernel-0.0.2+torch2.10.0-cp311-abi3-win_amd64.whl
	```
- Linux
	```apache
	pip install https://github.com/deepbeepmeep/kernels/releases/download/Light2xv/lightx2v_kernel-0.0.2+torch2.10.0-cp311-abi3-linux_x86_64.whl
	```

### Nunchaku INT4/FP4 内核的 Python 3.11 / Pytorch 2.10 / Cuda 13 轮子

- Windows
	```apache
	pip install https://github.com/nunchaku-ai/nunchaku/releases/download/v1.2.1/nunchaku-1.2.1+cu13.0torch2.10-cp311-cp311-win_amd64.whl
	```
- Linux
	```apache
	pip install https://github.com/nunchaku-ai/nunchaku/releases/download/v1.2.1/nunchaku-1.2.1+cu13.0torch2.10-cp311-cp311-linux_x86_64.whl
	```

### Nunchaku INT4/FP4 内核的 Python 3.10 / Pytorch 2.7.1 / Cuda 12.8 轮子

- Windows
	```apache
	pip install https://github.com/deepbeepmeep/kernels/releases/download/v1.2.0_Nunchaku/nunchaku-1.2.0+torch2.7-cp310-cp310-win_amd64.whl
	```
- Linux (Pytorch 2.7.1 / Cuda 12.8)
	```apache
	pip install https://github.com/deepbeepmeep/kernels/releases/download/v1.2.0_Nunchaku/nunchaku-1.2.0+torch2.7-cp310-cp310-linux_x86_64.whl
	```