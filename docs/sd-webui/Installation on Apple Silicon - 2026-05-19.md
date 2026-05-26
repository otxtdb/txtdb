---
title: "在 Apple 芯片上安装和运行"
source: "https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Installation-on-Apple-Silicon"
author:
published:
created: 2026-05-19
description: "Stable Diffusion web UI. Contribute to AUTOMATIC1111/stable-diffusion-webui development by creating an account on GitHub."
tags:
  - "clippings"
taxonomy: { doc_category: [sd-webui] }
---
Mac 用户：请反馈这些说明对您是否有效，以及是否有内容不清楚，或存在当前未提及的安装问题。

## 重要提示

目前 Web UI 中的大多数功能在 macOS 上运行正常，最显著的例外是 CLIP 查询器和训练功能。尽管训练似乎可以运行，但其速度极慢且占用大量内存。CLIP 查询器可以使用，但由于无法正确利用 macOS 的 GPU 加速，默认配置会将其完全通过 CPU 运行（因此速度较慢）。

大多数采样器均已知可用，唯一的例外是在使用 Stable Diffusion 2.0 模型时，PLMS 采样器不可用。在 macOS 上使用 GPU 加速生成的图像，通常应与相同设置和种子下通过 CPU 生成的图像相匹配或几乎匹配。

## 自动安装

### 新安装：

1. 如果未安装 Homebrew，请按照 [https://brew.sh](https://brew.sh) 上的说明进行安装。保持终端窗口打开，并按照“下一步”中的说明将 Homebrew 添加到您的 PATH。
2. 打开一个新的终端窗口并运行 `brew install cmake protobuf rust python@3.10 git wget`
3. 通过运行 `git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui 克隆 Web UI 仓库`
4. 将您想要使用的 Stable Diffusion 模型/检查点放入 `stable-diffusion-webui/models/Stable-diffusion` 。如果您没有任何模型，请参阅下方的“下载 Stable Diffusion 模型”。
5. 然后运行 `cd stable-diffusion-webui` 再运行 `./webui.sh` 以启动 Web UI。系统将使用 venv 创建并激活 Python 虚拟环境，同时自动下载并安装任何缺失的依赖项。
6. 若要稍后重新启动 Web UI 进程，请再次运行 `./webui.sh` 。请注意，该操作不会自动更新 Web UI；如需更新，请在运行 `./webui.sh` 之前先运行 `git pull` 。

### 现有安装：

如果您已使用 `setup_mac.sh` 创建了现有的 Web UI 安装，请从您的 `stable-diffusion-webui` 文件夹中删除 `run_webui_mac.sh` 文件和 `repositories` 文件夹。然后运行 `git pull` 以更新 Web UI，再运行 `./webui.sh` 来启动它。

## 下载 Stable Diffusion 模型

如果您没有任何可用的模型，可以从 Hugging Face 下载 Stable Diffusion 模型。要下载模型，请点击某个模型，然后点击 `Files and versions` 标题。查找带有".ckpt"或".safetensors"扩展名的文件，然后点击下载文件大小右侧的下箭头以进行下载。

一些流行的官方 Stable Diffusion 模型包括：

- Stable Diffusion 1.4 (sd-v1-4.ckpt)
- Stable Diffusion 1.5 (v1-5-pruned-emaonly.safetensors)
- Stable Diffusion 1.5 重绘（sd-v1-5-inpainting.ckpt）

Stable Diffusion 2.0 和 2.1 需要同时提供模型文件和配置文件，且在生成图像时，需要将图像宽度与高度设置为 768 或更高：

- Stable Diffusion 2.0 (768-v-ema.ckpt)
- Stable Diffusion 2.1 (v2-1\_768-ema-pruned.ckpt)

对于配置文件，请在键盘上按住 Option 键并点击此处下载 `v2-inference-v.yaml` （可能会以 `v2-inference-v.yaml.yml` 的形式下载）。在 Finder 中选中该文件，然后进入菜单并选择 `File` > `Get Info` 。在弹出的窗口中选中文件名，将其更改为模型的文件名，但将文件扩展名从 `.ckpt` 改为 `.yaml` ，按键盘上的回车键（如果提示更改文件扩展名则确认），并将其放置在与模型相同的文件夹中（例如，如果您下载了 `768-v-ema.ckpt` 模型，请将其重命名为 `768-v-ema.yaml` 并放入 `stable-diffusion-webui/models/Stable-diffusion` 中与模型一起）。

此外，还提供 Stable Diffusion 2.0 深度模型 (512-depth-ema.ckpt)。按住键盘上的 Option 键并点击此处下载 `v2-midas-inference.yaml` 配置文件，然后按照上述方法将其重命名为 `.yaml` 扩展名，并将其放入 `stable-diffusion-webui/models/Stable-diffusion` 中与模型一起。请注意，该模型适用于 512 宽度/高度或更高的图像尺寸，而不是 768。

## 故障排除

### Web UI 无法启动：

如果在使用 `./webui.sh` 启动 Web UI 时遇到错误，请尝试从您的 `stable-diffusion-webui` 文件夹中删除 `repositories` 和 `venv` 文件夹，然后使用 `git pull` 更新 Web UI，再次运行 `./webui.sh` 。

### 性能不佳：

目前 macOS 上的 GPU 加速会占用大量内存。如果性能较差（例如，使用任何采样器生成一张 512x512 的图像需要超过一分钟，且步数为 20）

- 请尝试使用 `--opt-split-attention-v1` 命令行选项启动（即 `./webui.sh --opt-split-attention-v1` ），看看是否有所帮助。
- 差别不大吗？
	- 打开位于 /Applications/Utilities 中的活动监视器应用程序，并在“内存”选项卡下检查内存压力图表。生成图像时，内存压力会显示为红色。
		- 关闭 Web UI 进程，然后添加 `--medvram` 命令行选项（即 `./webui.sh --opt-split-attention-v1 --medvram` ）。
- 即使添加了该选项，性能仍然不佳且内存压力仍为红色？
	- 尝试 `--lowvram` （即 `./webui.sh --opt-split-attention-v1 --lowvram` ）。
- 使用任何采样器生成一张 512x512 的图像，即使只有 20 步，仍然需要几分钟以上？
	- 您可能需要关闭 GPU 加速。
		- 在 Xcode 中打开 `webui-user.sh`
				- 将 `#export COMMANDLINE_ARGS=""` 改为 `export COMMANDLINE_ARGS="--skip-torch-cuda-test --no-half --use-cpu all"` 。