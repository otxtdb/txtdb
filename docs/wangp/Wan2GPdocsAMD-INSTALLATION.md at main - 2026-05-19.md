---
title: "安装指南 - RDNA 4、3、3.5 和 2 的完整设置说明"
source: "https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/AMD-INSTALLATION.md"
author:
published:
created: 2026-05-19
description: "A fast AI Video Generator for the GPU Poor. Supports Wan 2.1/2.2, Qwen Image, Hunyuan Video, LTX  Video and Flux. - Wan2GP/docs/AMD-INSTALLATION.md at main · deepbeepmeep/Wan2GP"
tags:
  - "clippings"
taxonomy: { doc_category: [wangp] }
---
## AMD Windows 安装指南（TheRock）

本指南涵盖在 Windows 下使用 TheRock 的官方 PyTorch 轮安装 AMD GPU。

## 支持的 GPU

根据 [TheRock 的官方支持矩阵](https://github.com/ROCm/TheRock/blob/main/SUPPORTED_GPUS.md) ，以下 GPU 在 Windows 下得到支持：

### gfx110X-all (RDNA 3):

- AMD RX 7900 XTX (gfx1100)
- AMD RX 7800 XT (gfx1101)
- AMD RX 7700 XT (gfx1101)
- AMD RX 7700S / Framework Laptop 16 (gfx1102)
- AMD Radeon 780M 笔记本电脑集成显卡 (gfx1103)

### gfx120X-all (RDNA 4):

- AMD RX 9060 XT (gfx1200)
- AMD RX 9060 (gfx1200)
- AMD RX 9070 XT (gfx1201)
- AMD RX 9070 (gfx1201)

### gfx1151 (RDNA 3.5 APU):

- AMD Strix Halo APUs

### gfx1150 (RDNA 3.5 APU):

- AMD Radeon 890M (Ryzen AI 9 HX 370 - Strix Point)

### 也支持:

### gfx103X-dgpu: (RDNA 2)

> **注意：** 如果您的 GPU 未列于上方，则可能无法在 Windows 上通过 TheRock 获得支持。支持状态和未来更新可在 [官方文档](https://github.com/ROCm/TheRock/blob/main/SUPPORTED_GPUS.md) 中找到。

## 要求

- Python 3.11（推荐用于 Wan2GP - TheRock 目前支持 Python 3.11、3.12 和 3.13）。
- Windows 10/11

## 安装环境

此安装使用 TheRock 构建的 PyTorch 轮子。

### 安装 Python

从 [python.org/downloads/windows](https://www.python.org/downloads/windows/) 下载 Python 3.11。按 Ctrl+F 并搜索"3.11."以找到可安装的最新版本。

或者，您可以使用这个直接链接： [Python 3.11.9 (64 位)](https://www.python.org/ftp/python/3.11.9/python-3.11.9-amd64.exe) 。

安装后，确保在您的终端中 `python --version` 可以正常工作并返回 `3.11.9。`

如果不行，您需要将 Python 添加到您的 PATH：

- 按下 `Windows` 键，输入 `环境变量 ` ，并选择 `编辑系统环境变量 ` 。
- 在 `系统属性` 窗口中，点击 `环境变量…` 。
- 在 `用户变量` 下，找到 `路径 ` ，然后点击 `编辑 ` → ` 新建` 并添加以下条目（将 `<username>` 替换为你的 Windows 用户名）：
```moonscript
C:\Users\<username>\AppData\Local\Programs\Python\Launcher\
C:\Users\<username>\AppData\Local\Programs\Python\Python311\Scripts\
C:\Users\<username>\AppData\Local\Programs\Python\Python311\
```

> **注意：** 如果更新 PATH 后 Python 仍然没有显示正确的版本，尝试注销并重新登录 Windows 以应用更改。

### 安装 Git

从 [git-scm.com/downloads/windows](https://git-scm.com/install/windows) 下载 Git 并安装。默认的安装选项即可。

## 安装步骤（Windows，使用 Python venv）

> **注意：** 以下命令适用于 Windows 命令提示符 (CMD)。  
> 如果你使用的是 PowerShell，某些命令（如注释和激活虚拟环境）可能会有所不同。

### 第一步：下载并设置 Wan2GP 环境

```crmsh
:: Navigate to your desired install directory
cd \your-path-to-wan2gp

:: Clone the repository
git clone https://github.com/deepbeepmeep/Wan2GP.git
cd Wan2GP

:: Create virtual environment
python -m venv wan2gp-env

:: Activate the virtual environment
wan2gp-env\Scripts\activate
```

> **注意：** 如果你安装了多个版本的 Python，请使用 `py -3.11 -m venv wan2gp-env` 而不是 `python -m venv wan2gp-env` 来确保使用正确的版本。

### 第二步：由 TheRock 安装 ROCm/PyTorch

**重要提示：** 为您的 GPU 系列选择正确的索引 URL！

#### 对于 gfx110X-all（RX 7900 XTX、RX 7800 XT 等）：

```stylus
pip install --pre torch torchaudio torchvision rocm[devel] --index-url https://rocm.nightlies.amd.com/v2/gfx110X-all/
```

#### 对于 gfx120X-all（RX 9060、RX 9070 等）：

```stylus
pip install --pre torch torchaudio torchvision rocm[devel] --index-url https://rocm.nightlies.amd.com/v2/gfx120X-all/
```

#### 对于 gfx1151（Strix Halo 集成显卡）：

```stylus
pip install --pre torch torchaudio torchvision rocm[devel] --index-url https://rocm.nightlies.amd.com/v2/gfx1151/
```

#### 对于 gfx1150（Radeon 890M - Strix Point）：

```stylus
pip install --pre torch torchaudio torchvision rocm[devel] --index-url https://rocm.nightlies.amd.com/v2-staging/gfx1150/
```

#### 对于 gfx103X-dgpu（RDNA 2）：

```stylus
pip install --pre torch torchaudio torchvision rocm[devel] --index-url https://rocm.nightlies.amd.com/v2-staging/gfx103X-dgpu/
```

这将自动安装带有 ROCm 支持的最新 PyTorch、torchaudio 和 torchvision 轮。

### 第 3 步：安装 Wan2GP 依赖项

```cmake
:: Install core dependencies
pip install -r requirements.txt
```

### 步骤 4：验证安装

```csp
python -c "import torch; print('PyTorch:', torch.__version__); print('ROCm available:', torch.cuda.is_available()); print('Device:', torch.cuda.get_device_name(0) if torch.cuda.is_available() else 'No GPU')"
```

预期输出示例：

```apache
PyTorch: 2.11.0+rocm7.12.0
ROCm available: True
Device: AMD Radeon RX 9070 XT
```

## 注意模式

WanGP 通过 [triton-windows](https://github.com/woct0rdho/triton-windows/) 支持多种注意力实现。

首先，在你的虚拟环境中安装 `triton-windows` 。如果你安装了旧版本的 Triton，请先卸载它。需要初始化 ROCm SDK。同时，也应激活 Visual Studio 环境。

```nix
pip uninstall triton
pip install triton-windows
rocm-sdk init
"C:\Program Files\Microsoft Visual Studio\2022\Community\VC\Auxiliary\Build\vcvars64.bat" >nul 2>&1
```

### 支持的关注实现

- **SageAttention V1** （需要 `.post26` 轮或更新版本以解决 Triton 编译问题，无需非官方补丁。从 [这个](https://github.com/Comfy-Org/wheels/actions/runs/21343435018) URL 下载）
```cmake
pip install "sageattention <2"
```
- **FlashAttention-2** （仅支持 Triton 后端）：
```bash
git clone https://github.com/Dao-AILab/flash-attention.git
cd flash-attention
pip install ninja
pip install packaging
set FLASH_ATTENTION_TRITON_AMD_ENABLE=TRUE && python setup.py install
```
- **SDPA Flash**: 默认情况下在 PyTorch 中通过 AOTriton 在 post-RDNA2 GPU 上可用。

## 运行 Wan2GP

对于未来的会话，如果环境尚未激活，每次都要激活环境，然后运行 `python wgp.py` ：

```vim
cd \path-to\Wan2GP
wan2gp-env\Scripts\activate
:: Add the AMD-specific environment variables mentioned below here
python wgp.py
```

建议在每个新会话开始时设置以下环境变量（您可以创建一个 `.bat` 文件，用于激活您的 venv，设置这些变量，然后启动 `wgp.py` ）：

```routeros
set ROCM_HOME=%ROCM_ROOT%
set PATH=%ROCM_ROOT%\lib\llvm\bin;%ROCM_BIN%;%PATH%
set CC=clang-cl
set CXX=clang-cl
set DISTUTILS_USE_SDK=1
set FLASH_ATTENTION_TRITON_AMD_ENABLE=TRUE
set TORCH_ROCM_AOTRITON_ENABLE_EXPERIMENTAL=1
```

MIOpen（AMD 的 NVIDIA cuDNN 对应产品）在多种架构上尚未完全稳定；它可能导致内存不足错误（OOM），崩溃显示驱动程序，或显著增加生成时间。目前，建议通过设置启用快速模式：

```routeros
set MIOPEN_FIND_MODE=FAST
```

或者，你可以通过编辑 `wgp.py` 并在 `import torch` 下方添加以下行（大约在第 51 行）来完全禁用 MIOpen：

```elixir
...
:: /lines already in the file/
:: ...
:: import torch
torch.backends.cudnn.enabled = False # <-- Add this here
:: import gc
:: ...
...
```

要验证它是否已禁用，或启用详细日志记录，您可以设置：

```routeros
set MIOPEN_ENABLE_LOGGING=1
set MIOPEN_ENABLE_LOGGING_CMD=1
set MIOPEN_LOG_LEVEL=5
```

## 故障排除

### GPU 未检测到

如果 `torch.cuda.is_available()` 返回 `False`:

1. **验证您的 GPU 是否受支持** - 检查上面 [受支持的 GPU](#supported-gpus) 列表
2. **检查 AMD 驱动** - 确保已安装最新的 AMD Adrenalin 驱动
3. **验证正确的索引 URL** - 确保使用了正确的 GPU 系列索引 URL

### 安装错误

**"找不到满足要求的版本"**

- 再次确认你正在使用适合你 GPU 系列的正确 `--index-url` 。你也可以尝试添加 `--pre` 标志，或者将 URL 中的 `/v2/` 替换为 `/v2/staging/`
- 确保你使用的是 Python 3.11，而不是 3.10

**"No matching distribution found":**

- 你的 GPU 架构可能不受支持
- 确认已激活虚拟环境

### 性能问题

- **监控 VRAM 使用情况** - 如果内存不足，请减小批处理大小或分辨率
- **关闭 GPU 密集型应用** - 已启用硬件加速的应用（如浏览器、Discord 等）

### 已知问题

Windows 软件包是新的，可能不稳定。

已知问题在 [ROCm/TheRock#808 处进行跟踪](https://github.com/ROCm/TheRock/issues/808)

## 其他资源

- [TheRock 代码库](https://github.com/ROCm/TheRock/)
- [发布文档](https://github.com/ROCm/TheRock/blob/main/RELEASES.md)
- [支持的 GPU 架构](https://github.com/ROCm/TheRock/blob/main/SUPPORTED_GPUS.md)
- [路线图](https://github.com/ROCm/TheRock/blob/main/ROADMAP.md)
- [ROCm 文档](https://rocm.docs.amd.com/)

如需更多关于 Wan2GP 的故障排除指南，请参阅 [TROUBLESHOOTING.md](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/TROUBLESHOOTING.md).

