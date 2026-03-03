---
title: "Windows & Linux 手动安装指南"
source: "https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/INSTALLATION.md"
author:
  - "[[deepbeepmeep]]"
published:
created: 2026-03-01
description: "A fast AI Video Generator for the GPU Poor. Supports Wan 2.1/2.2, Qwen Image, Hunyuan Video, LTX  Video and Flux. - Wan2GP/docs/INSTALLATION.md at main · deepbeepmeep/Wan2GP"
tags:
  - "clippings"
taxonomy: { doc_category: [wan2gp] }
---
本指南涵盖了不同 GPU 代和操作系统的安装。

## 需求
### \- 兼容的 GPU（GTX 10XX - RTX 50XX）- Git [Git 下载](https://github.com/git-for-windows/git/releases/download/v2.51.2.windows.1/Git-2.51.2-64-bit.exe)
- Visual Studio 2022 的 C++ 扩展构建工具 [Vs2022 下载](https://aka.ms/vs/17/release/vs_BuildTools.exe)
- CUDA Toolkit 12.8 或更高版本 [CUDA Toolkit 下载](https://developer.nvidia.com/cuda-downloads)
- Nvidia 驱动程序最新版 [Nvidia Drivers 下载](https://www.nvidia.com/en-us/software/nvidia-app/)
- 已下载、解压的 FFMPEG 及 bin 文件夹在 PATH 中 [FFMPEG 下载](https://github.com/BtbN/FFmpeg-Builds/releases/download/latest/ffmpeg-n8.0-latest-win64-gpl-8.0.zip)
- Python 3.10.9 [Python 下载](https://www.python.org/ftp/python/3.10.9/python-3.10.9-amd64.exe)
- Miniconda [Miniconda 下载](https://repo.anaconda.com/miniconda/Miniconda3-latest-Windows-x86_64.exe) 或 Python venv
	[![miniconda_1234x962](https://github.com/user-attachments/assets/222650d9-77e1-4c9e-8319-dfba9bc409d3)](https://github.com/user-attachments/assets/222650d9-77e1-4c9e-8319-dfba9bc409d3)

## 为 Nvidia GTX 10XX 
- RTX QUADRO - 50XX（稳定版）的安装这个安装使用 PyTorch 2.6.0、Cuda 12.6（适用于 GTX 10XX - RTX 30XX）以及 PyTorch 2.7.1、Cuda 12.8（适用于 RTX 40XX - 50XX），这些版本都经过充分测试且稳定。

不推荐使用 PyTorch 2.8.0，因为在切换模型时观察到一些系统内存泄漏问题，也不推荐使用 2.9.0，因为它存在一些 3D 卷积性能问题（VAE VRAM 需求激增）。

如果你想在 RTX 50xx 上使用 NV FP4 优化的内核，你需要升级到 Python 3.11、PyTorch 2.10 并搭配 Cuda 13.0。

## 下载仓库并设置 Conda 环境### 克隆仓库#### 首先，创建一个名为 Wan2GP 的文件夹，然后打开它，然后右键点击并选择"在终端中打开"，然后逐个复制并粘贴以下命令。```
git clone https://github.com/deepbeepmeep/Wan2GP.git
```

#### 使用 Conda 创建 Python 3.10.9 环境```
conda create -n wan2gp python=3.10.9
```

#### 激活 Conda 环境```
conda activate wan2gp
```

# 现在根据您的 GPU 选择安装方式## 仅限 GTX 10XX -16XX 的 Windows 安装#### Windows 安装 PyTorch 2.6.0 配合 CUDA 12.6（仅限 GTX 10XX -16XX 显卡）pip install torch==2.6.0+cu126 torchvision==0.21.0+cu126 torchaudio==2.6.0+cu126 --index-url https://download.pytorch.org/whl/cu126

#### 仅限 GTX 10XX -16XX 的 Windows 安装 requirements.txt```
pip install -r requirements.txt
```

## Windows 安装教程适用于 RTX QUADRO - 仅限 20XX 型号#### Windows 安装 PyTorch 2.6.0 配合 CUDA 12.6（仅限 RTX QUADRO - 20XX 系列）```
pip install torch==2.6.0+cu126 torchvision==0.21.0+cu126 torchaudio==2.6.0+cu126 --index-url https://download.pytorch.org/whl/cu126
```

#### Windows 安装 Triton（仅限 RTX QUADRO - 20XX 系列）```
pip install -U "triton-windows<3.3"
```

#### Windows 安装 Sage1 注意：仅适用于 RTX QUADRO - 20XX```
pip install sageattention==1.0.6
```

#### Windows 安装 requirements.txt 仅限 RTX QUADRO - 20XX```
pip install -r requirements.txt
```

## Windows 仅限 RTX 30XX 的安装#### Windows 仅限 RTX 30XX 安装 PyTorch 2.6.0 与 CUDA 12.6```
pip install torch==2.6.0+cu126 torchvision==0.21.0+cu126 torchaudio==2.6.0+cu126 --index-url https://download.pytorch.org/whl/cu126
```

#### Windows 安装 Triton 仅限 RTX 30XX```
pip install -U "triton-windows<3.3"
```

#### Windows 安装 Sage2 Attention（仅限 RTX 30XX）```
pip install https://github.com/woct0rdho/SageAttention/releases/download/v2.1.1-windows/sageattention-2.1.1+cu126torch2.6.0-cp310-cp310-win_amd64.whl
```

#### 仅限 RTX 30XX 的 Windows 安装 requirements.txt```
pip install -r requirements.txt
```

## 仅限 RTX 40XX、50XX 的安装#### Windows 安装 PyTorch 2.7.1 配合 CUDA 12.8 仅限 RTX 40XX - 50XX```
pip install torch==2.7.1 torchvision==0.22.1 torchaudio==2.7.1 --index-url https://download.pytorch.org/whl/cu128
```

#### 仅限 Windows 安装 RTX 40XX, 50XX 的 Triton```
pip install -U "triton-windows<3.4"
```

#### Windows 安装 Sage2 Attention 仅限 RTX 40XX, 50XX```
pip install https://github.com/woct0rdho/SageAttention/releases/download/v2.2.0-windows/sageattention-2.2.0+cu128torch2.7.1-cp310-cp310-win_amd64.whl
```

#### 仅限 RTX 40XX、50XX 的 Windows 安装 requirements.txt```
pip install -r requirements.txt
```

## 仅限 50XX 的安装：Python 3.11，PyTorch 2.10.0，Cuda 13。适用于 NVFP4 优化内核#### 使用 Conda 创建 Python 3.11 环境```
conda create -n wan2gp python=3.11.14
```

#### Windows 安装 PyTorch 2.10.0（仅支持 CUDA 13.0，适用于 RTX 50XX）```
pip install torch==2.10.0 torchvision torchaudio --index-url https://download.pytorch.org/whl/cu130
```

#### Windows 安装 Triton 仅限 RTX 50XX```
pip install -U triton-windows
```

#### Windows 安装 Sage2 注意：仅限 RTX 50XX```
pip install https://github.com/woct0rdho/SageAttention/releases/download/v2.2.0-windows.post4/sageattention-2.2.0+cu130torch2.9.0andhigher.post4-cp39-abi3-win_amd64.whl
```

#### Windows 安装 requirements.txt 注意：仅限 RTX 50XX```
pip install -r requirements.txt
```

## 可选### Flash Attention Windows#### Pytorch 2.7.1```
pip install https://github.com/Redtash1/Flash_Attention_2_Windows/releases/download/v2.7.0-v2.7.4/flash_attn-2.7.4.post1+cu128torch2.7.0cxx11abiFALSE-cp310-cp310-win_amd64.whl
```

#### Pytorch 2.10[https://github.com/deepbeepmeep/kernels/releases/download/Flash2/flash\_attn-2.8.3-cp311-cp311-win\_amd64.whl](https://github.com/deepbeepmeep/kernels/releases/download/Flash2/flash_attn-2.8.3-cp311-cp311-win_amd64.whl)

# Linux 安装### 步骤 1：下载仓库并设置 Conda 环境#### 克隆仓库```
git clone https://github.com/deepbeepmeep/Wan2GP.git
```

#### 切换目录```
cd Wan2GP
```

#### 使用 Conda 创建 Python 3.10.9 环境```
conda create -n wan2gp python=3.10.9
```

#### 激活 Conda 环境```
conda activate wan2gp
```

## 仅限 RTX 10XX -16XX 的安装
#### 仅限 RTX 10XX -16XX 安装 PyTorch 2.6.0 与 CUDA 12.6pip install torch==2.6.0+cu126 torchvision==0.21.0+cu126 torchaudio==2.6.0+cu126 --index-url https://download.pytorch.org/whl/cu126

#### 仅适用于 RTX 30XX 安装 requirements.txt```
pip install -r requirements.txt
```

## RTX QUADRO - 20XX 仅限安装#### 为 RTX QUADRO - 20XX 仅限安装 PyTorch 2.6.0 和 CUDA 12.6```
pip install torch==2.6.0+cu126 torchvision==0.21.0+cu126 torchaudio==2.6.0+cu126 --index-url https://download.pytorch.org/whl/cu126
```

#### 为 RTX QUADRO - 20XX 仅限安装 Triton```
pip install -U "triton<3.3"
```

#### 安装 Sage1 注意力模块 - 仅适用于 RTX QUADRO 20XX```
pip install sageattention==1.0.6
```

#### 为 RTX QUADRO - 20XX 仅安装 requirements.txt```
pip install -r requirements.txt
```

## 仅限 RTX 30XX 的安装#### 为 RTX 30XX 仅安装 PyTorch 2.6.0 与 CUDA 12.6```
pip install torch==2.6.0+cu126 torchvision==0.21.0+cu126 torchaudio==2.6.0+cu126 --index-url https://download.pytorch.org/whl/cu126
```

#### 仅适用于 RTX 30XX 安装 Triton```
pip install -U "triton<3.3"
```

#### 仅适用于 RTX 30XX 安装 Sage2 Attention。确保是 Sage 2.1.1。```
python -m pip install "setuptools<=75.8.2" --force-reinstall
git clone https://github.com/thu-ml/SageAttention
cd SageAttention 
pip install -e .
```

#### 仅适用于 RTX 30XX 安装 requirements.txt```
pip install -r requirements.txt
```

## 仅限 RTX 40XX、50XX 的安装#### 仅限 RTX 40XX - 50XX 安装 PyTorch 2.7.1 与 CUDA 12.8```
pip install torch==2.7.1 torchvision==0.22.1 torchaudio==2.7.1 --index-url https://download.pytorch.org/whl/cu128
```

#### 仅限 RTX 40XX、50XX 安装 Triton```
pip install -U "triton<3.4"
```

#### 仅适用于 RTX 40XX、50XX 安装 Sage Attention。确保是 Sage 2.2.0 版本。```
python -m pip install "setuptools<=75.8.2" --force-reinstall
git clone https://github.com/thu-ml/SageAttention
cd SageAttention 
pip install -e .
```

#### 仅适用于 RTX 40XX、50XX 安装 requirements.txt```
pip install -r requirements.txt
```

## 可选### Flash Attention#### Linux```
pip install flash-attn==2.7.2.post1
```

## 注意模式### WanGP 支持多种注意力实现：- **SDPA**（默认）：默认支持 PyTorch
- **Sage**：提升 30% 速度，但有小质量损失
- **Sage2**: 40% 速度提升
- **闪存** : 性能良好，但在 Windows 上安装可能较为复杂

### 注意 GPU 兼容性- RTX 10XX: SDPA
- RTX 20XX: SPDA, Sage1
- RTX 30XX, 40XX: SDPA, Flash Attention, Xformers, Sage1, Sage2/Sage2++
- RTX 50XX: SDPA, Flash Attention, Xformers, Sage2/Sage2++ / Sage3

## 性能配置文件根据您的硬件选择一个配置：

- **配置 3（LowRAM\_HighVRAM）**：将整个模型加载到 VRAM 中，8 位量化 14B 模型需要 24GB VRAM
- **配置文件 4（LowRAM\_LowVRAM）**：默认设置，按需加载模型部分，速度较慢但 VRAM 需求较低

## 故障排除### Sage 注意力问题如果 Sage 注意力不起作用：

1. 检查 Triton 是否正确安装
2. 清除 Triton 缓存
3. 回退到 SDPA 注意力：
	```
	python wgp.py --attention sdpa
	```

### 内存问题- 使用较低分辨率或较短的视频
- 启用量化（默认）
- 使用配置文件 4 以减少 VRAM 使用
- 考虑使用 1.3B 模型而不是 14B 模型

对于更多故障排除，请参阅 [TROUBLESHOOTING.md](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/TROUBLESHOOTING.md)

## 可选的 INT4 / FP4 量化支持内核这些内核将提供优化的 INT4 / FP4 反量化。

**请注意，FP4 支持取决于硬件，并且仅在 RTX 50xx / sm120+显卡上才能工作**

### Light2xv NVP4 内核 Python 3.11 / Pytorch 2.10 / Cuda 13 (仅限 RTX 50xx / sm120+) 的轮子- Windows
	```
	pip install https://github.com/deepbeepmeep/kernels/releases/download/Light2xv/lightx2v_kernel-0.0.2+torch2.10.0-cp311-abi3-win_amd64.whl
	```
- Linux
	```
	pip install https://github.com/deepbeepmeep/kernels/releases/download/Light2xv/lightx2v_kernel-0.0.2+torch2.10.0-cp311-abi3-linux_x86_64.whl
	```

### Nunchaku INT4/FP4 内核轮子适用于 Python 3.10 / Pytorch 2.7.1 / Cuda 12.8- Windows ()
	```
	pip install https://github.com/deepbeepmeep/kernels/releases/download/v1.2.0_Nunchaku/nunchaku-1.2.0+torch2.7-cp310-cp310-win_amd64.whl
	```
- Linux (Pytorch 2.7.1 / Cuda 12.8)
	```
	pip install https://github.com/deepbeepmeep/kernels/releases/download/v1.2.0_Nunchaku/nunchaku-1.2.0+torch2.7-cp310-cp310-linux_x86_64.whl
	```

### Nunchaku INT4/FP4 内核的 Python 3.11 / Pytorch 2.10 / Cuda 13 轮子- Windows
	```
	pip install https://github.com/nunchaku-ai/nunchaku/releases/download/v1.2.1/nunchaku-1.2.1+cu13.0torch2.10-cp311-cp311-win_amd64.whl
	```
- Linux
	```
	pip install https://github.com/nunchaku-ai/nunchaku/releases/download/v1.2.1/nunchaku-1.2.1+cu13.0torch2.10-cp311-cp311-linux_x86_64.whl
	```