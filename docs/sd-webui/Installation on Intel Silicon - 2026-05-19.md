---
title: "在 Intel 芯片上安装和运行"
source: "https://github.com/openvinotoolkit/stable-diffusion-webui/wiki/Installation-on-Intel-Silicon"
author:
published:
created: 2026-05-19
description: "Stable Diffusion web UI. Contribute to openvinotoolkit/stable-diffusion-webui development by creating an account on GitHub."
tags:
  - "clippings"
taxonomy: { doc_category: [sd-webui] }
---
## Stable Diffusion WebUI 支持（预览版）

借助 Intel® Distribution of OpenVINO™ Toolkit，现在可以在 Intel CPU 和 GPU（包括集成显卡和独立显卡）等硬件上运行 Stable Diffusion WebUI。此功能为正在积极开发中的预览版支持，我们热烈欢迎社区提供反馈和贡献。

## 重要提示

若要在 Windows 系统上实现 WebUI 的最佳性能，请按以下步骤使用 webui-user.bat 启动界面：

- 以管理员身份启动命令提示符
- 进入 stable-diffusion-webui 目录
- 运行 webui-user.bat

目前，OpenVINO 加速脚本不支持以下功能：

## 使用 OpenVINO 运行 WebUI 的说明：

OpenVINO 支持通过自定义脚本提供。该自定义脚本利用 PyTorch 的 torch.compile 功能和 HuggingFace Diffusers 库以提升性能。以下是开始使用的说明：

- 如果您熟悉 Automatic1111 工作流，请使用来自 OpenVINOToolKit 的这个分支替代 Automatic1111 并按照说明操作。或者，请按照以下说明进行操作：

### Linux

```bash
# Make sure Python version is 3.10+
python -m venv sd_env
source sd_env/bin/activate
git clone https://github.com/openvinotoolkit/stable-diffusion-webui.git
cd stable-diffusion-webui

export PYTORCH_TRACING_MODE=TORCHFX
export COMMANDLINE_ARGS="--skip-torch-cuda-test --precision full --no-half" 

# Launch the WebUI
./webui.sh
```
- 运行 `./webui.sh` 启动 WebUI 后，请按照此处提供的说明使用 OpenVINO 自定义脚本

### Windows

- 下载并安装 git 和 Python 3.10.6（勾选“添加到 PATH"）
```bash
git clone https://github.com/openvinotoolkit/stable-diffusion-webui.git
cd stable-diffusion-webui
webui-user.bat
```
- 按照此处说明使用 OpenVINO 自定义脚本

注意事项：

- 上述步骤将创建虚拟环境并将所需包安装到此环境中。如果您想使用自己的虚拟环境运行 Stable Diffusion WebUI，请更新 `VENV_DIR=` 行中的 `VENV_DIR=-` 至 `first-time-runner.bat` 和 `torch-install.ps1` 文件。
- PyTorch 目前尚未在 Windows 上正式支持 torch.compile。运行 torch-install.bat 可安装 PyTorch 并为 OpenVINO 后端启用 torch.compile。

### 启用公开访问

要启用公开访问，请将"--share --listen"参数添加到 `COMMANLINE_ARGUMENTS` 变量中（在 Windows 上，您可以通过更新 `webui-user.bat` 文件来实现）。

## 安装说明

### 安装 OpenVINO：

#### 从 PyPI 安装：

带有 torch.compile 支持的 OpenVINO 现已在 OpenVINO 预发布包中提供预览版本。请使用命令 `pip install --pre openvino 从该位置安装最新的预发布包。`

#### 构建并从源代码安装：

OpenVINO 也可使用此处提供的说明从源代码构建。

### 已知问题

- 将采样方法更改为 DPM++ 或 Karras 方法时，由于会对图进行某些修改，需要重新编译模型。建议在进行任何性能测量时，排除首张图像生成的时间。
- 目前，常规版 Stable Diffusion 2.1 在离散 GPU 上存在已知问题。请使用 Stable Diffusion 2.1-base 版本。