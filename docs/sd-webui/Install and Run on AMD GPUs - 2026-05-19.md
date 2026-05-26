---
title: "在 AMD GPU 上安装和运行"
source: "https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Install-and-Run-on-AMD-GPUs"
author:
published:
created: 2026-05-19
description: "Stable Diffusion web UI. Contribute to AUTOMATIC1111/stable-diffusion-webui development by creating an account on GitHub."
tags:
  - "clippings"
taxonomy: { doc_category: [sd-webui] }
---
## Windows

Windows 平台对 AMD GPU 的支持尚未在 WebUI 中正式实现，  
但您可以安装使用 DirectML 的 lshqqytiger 开发的 WebUI 分支版本。

目前训练功能尚不可用，但多种功能/扩展程序仍可正常运行，例如 LoRA 和 ControlNet。如有问题，请访问 [https://github.com/lshqqytiger/stable-diffusion-webui-directml/issues](https://github.com/lshqqytiger/stable-diffusion-webui-directml/issues) 提交报告。

1. 安装 Python 3.10.6（勾选“添加到 PATH"），以及 Git。
2. 在命令行/终端中粘贴此行： `git clone https://github.com/lshqqytiger/stable-diffusion-webui-directml && cd stable-diffusion-webui-directml && git submodule init && git submodule update`  
	<sup>(you can move the program folder somewhere else.)</sup>
3. 双击 webui-user.bat
4. 如果在安装或运行时看起来卡住了，请在终端按回车键，它应该会继续运行。

如果您有 4-6GB 显存，请尝试像这样向 `webui-user.bat` 添加这些标志：

`COMMANDLINE_ARGS=--opt-sub-quad-attention --lowvram --disable-nan-check`

（以下内容均为 Linux 系统下使用 ROCm 的安装指南。）

## 自动安装

<sup>(As of <a href="https://github.com/AUTOMATIC1111/stable-diffusion-webui/pull/6709">1/15/23</a> you can just run <code>webui.sh</code> and pytorch+rocm should be automatically installed for you.)</sup>

1. 输入以下命令，将把 WebUI 安装到当前目录：

```bash
sudo apt install git python3.10-venv -y
git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui && cd stable-diffusion-webui
python3.10 -m venv venv
```

2. 使用以下方式安装并运行：
	./webui.sh {你的参数\*}

\*对于许多 AMD GPU，必须添加 `--precision full --no-half` 或 `--upcast-sampling` 参数以避免 NaN 错误或崩溃。如果 `--upcast-sampling` 能作为修复方案在你的显卡上生效，其速度（fp16）将是全精度运行的两倍。

- Some cards like the Radeon RX 6000 Series and the RX 500 Series will already run fp16 perfectly fine (noted [here](https://github.com/AUTOMATIC1111/stable-diffusion-webui/issues/5468).)
- If your card is unable to run SD with the latest pytorch+rocm core package, you can try installing previous versions, by following a more manual installation guide below.

## 原生运行

执行以下操作：

```vim
git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui
cd stable-diffusion-webui
python -m venv venv
source venv/bin/activate
python -m pip install --upgrade pip wheel

# It's possible that you don't need "--precision full", dropping "--no-half" however crashes my drivers
TORCH_COMMAND='pip install torch torchvision --extra-index-url https://download.pytorch.org/whl/rocm5.1.1' python launch.py --precision full --no-half
```

在后续运行中，你只需执行以下内容：

```vim
cd stable-diffusion-webui
# Optional: "git pull" to update the repository
source venv/bin/activate

# It's possible that you don't need "--precision full", dropping "--no-half" however crashes my drivers
TORCH_COMMAND='pip install torch torchvision --extra-index-url https://download.pytorch.org/whl/rocm5.1.1' python launch.py --precision full --no-half
```

启动 WebUI 后的首次生成可能需要很长时间，你可能会看到类似以下的提示信息：

> MIOpen(HIP)：警告 \[SQLiteBase\] 缺少系统数据库文件 gfx1030\_40.kdb，性能可能会下降。请按照以下说明进行安装：[https://github.com/ROCmSoftwarePlatform/MIOpen#installing-miopen-kernels-package](https://github.com/ROCmSoftwarePlatform/MIOpen#installing-miopen-kernels-package)

后续版本将能够以正常性能运行。您可以点击消息中的链接，如果您使用的是相同的操作系统，请按照该处的步骤修复此问题。如果无法明确为您的操作系统编译或安装 MIOpen 内核，请考虑参考下方的“在 Docker 中运行”指南。

## 在 Docker 中运行

拉取最新的 `rocm/pytorch` Docker 镜像，启动该镜像并连接到容器（取自 `rocm/pytorch` 文档）： `docker run -it --network=host --device=/dev/kfd --device=/dev/dri --group-add=video --ipc=host --cap-add=SYS_PTRACE --security-opt seccomp=unconfined -v $HOME/dockerx:/dockerx rocm/pytorch`

在容器内执行以下操作：

```vim
cd /dockerx
git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui
cd stable-diffusion-webui
python -m pip install --upgrade pip wheel

# It's possible that you don't need "--precision full", dropping "--no-half" however crashes my drivers
REQS_FILE='requirements.txt' python launch.py --precision full --no-half
```

后续运行仅需重启容器、重新连接并再次在容器内执行以下操作：从此列表中找到容器名称 `docker container ls --all` ，选择与 `rocm/pytorch` 镜像匹配的那个，重启它： `docker container restart <container-id>` ，然后连接到它： `docker exec -it <container-id> bash` 。

```vim
cd /dockerx/stable-diffusion-webui
# Optional: "git pull" to update the repository

# It's possible that you don't need "--precision full", dropping "--no-half" however crashes my drivers
REQS_FILE='requirements.txt' python launch.py --precision full --no-half
```

容器内的 `/dockerx` 文件夹应在您的主目录下以相同名称可访问。

## 在 Docker 中更新 Python 版本

如果 Web UI 与 Docker 镜像中预装的 Python 3.7 版本不兼容，以下是更新它的说明（假设您已成功按照“在 Docker 内运行”进行操作）：

请在容器内执行以下操作：

```jboss
apt install python3.9-full # Confirm every prompt
update-alternatives --install /usr/local/bin/python python /usr/bin/python3.9 1
echo 'PATH=/usr/local/bin:$PATH' >> ~/.bashrc
```

运行 `source ~/.bashrc` 并继续执行与现有容器相同的命令。

您可能不需要使用"--precision full"，可以删除"--no-half"，但这可能不适用于所有人。某些显卡（如 Radeon RX 6000 系列和 RX 500 系列）在不使用该选项 `--precision full --no-half` 的情况下也能正常运行，从而节省大量显存。（此处有说明。）

## 在 AMD 和 Arch Linux 上安装

**在 Arch Linux 上使用 Arch 专用包安装 WebUI**  
*以及可能的其他基于 Arch 的 Linux 发行版（测试日期：2023 年 2 月 22 日）*

## Arch 专用依赖项

1. 首先安装所需依赖项并执行 `pip`
```bash
sudo pacman -S python-pip
```
2. 使用 ROCm 后端安装 `pytorch`

Arch \[社区\] 仓库提供两个 `pytorch` 软件包，即 `python-pytorch-rocm` 和 `python-pytorch-opt-rocm` 。对于支持 AVX2 指令集的 CPU（即 Haswell（Intel, 2013）或 Excavator（AMD, 2015）之后的微架构），请安装 `python-pytorch-opt-rocm` 以利用性能优化。否则，请安装 `python-pytorch-rocm` ：

```bash
# Install either one:
sudo pacman -S python-pytorch-rocm
sudo pacman -S python-pytorch-opt-rocm   # AVX2 CPUs only
```
3. 使用 ROCm 后端安装 `torchvision`

`python-torchvision-rocm` 软件包位于 AUR。请克隆 Git 仓库并在您的机器上编译该软件包。

```bash
git clone https://aur.archlinux.org/python-torchvision-rocm.git
cd python-torchvision-rocm
makepkg -si
```

确认所有步骤，直到 Pacman 完成 `python-torchvision-rocm` 的安装。

或者，使用 AUR 助手安装 `python-torchvision-rocm` 包。

## 设置 venv 环境

1. 手动创建一个带有系统 site-packages 的 `venv` 环境（这将允许访问系统的 `pytorch` 和 `torchvision` ），然后安装剩余的 Python 依赖项。
```css
python -m venv venv --system-site-packages
source venv/bin/activate
pip install -r requirements.txt
```

## 启动

在项目根目录下运行以下命令以启动 WebUI：

```bash
source venv/bin/activate
./webui.sh
```

根据显卡型号的不同，您可能需要在 `webui-user.sh` 中添加某些命令行参数和优化选项，以确保 WebUI 正常运行。请参阅自动安装部分。

## 局限性

- GPU 模型必须得到 Arch 依赖项的支持

请查看您的 GPU 是否列在 Torchvision 和 PyTorch 的 \` `PYTORCH_ROCM_ARCH` \` 变量中的构建架构中。有关架构的参考资料可在此处找到。如果未列出，请考虑在本地构建这两个包或使用其他安装方法。

- Arch 依赖项（\` `pytorch` \`、\` `torchvision` \`）通过完整的系统更新（\` `pacman -Syu` \`）和编译来保持最新，这在需要固定版本的依赖组合时可能并不理想

*本指南已在配备 Python 3.10.9、ROCm 5.4.3、PyTorch 1.13.1 和 Torchvision 0.14.1 的 AMD Radeon RX6800 显卡上进行测试。*

**设置**

- [在 NVIDIA GPU 上安装和运行](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Install-and-Run-on-NVidia-GPUs)
- [在 AMD GPU 上安装和运行](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Install-and-Run-on-AMD-GPUs)
- [在 Apple Silicon 上安装和运行](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Installation-on-Apple-Silicon)
- [在英特尔芯片上安装和运行（外部 Wiki 页面）](https://github.com/openvinotoolkit/stable-diffusion-webui/wiki/Installation-on-Intel-Silicon)
- [通过容器（即 Docker）安装和运行](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Containers)
- [通过在线服务运行](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Online-Services)

**图像重现/故障排除**

- [Seed 破坏性变更](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Seed-breaking-changes)
	- [仍然无法复现结果？请首先尝试此方法。](https://github.com/AUTOMATIC1111/stable-diffusion-webui/discussions/13093)
- [通用故障排除](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Troubleshooting)

**用法**

- [功能](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Features)
- [命令行参数与设置](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Command-Line-Arguments-and-Settings)
- [优化](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Optimizations)
- [自定义文件名及子目录](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Custom-Images-Filename-Name-and-Subdirectory)
- [更改模型文件夹位置（例如：外部磁盘）](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Change-model-folder-location)
- [用户界面自定义](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/User-Interface-Customizations)
- [指南和教程](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Guides-and-Tutorials)

**开发者**

Obsidian Reader · 1,784 words · par