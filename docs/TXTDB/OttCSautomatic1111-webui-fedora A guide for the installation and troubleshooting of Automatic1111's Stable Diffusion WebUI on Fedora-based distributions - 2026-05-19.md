---
title: "在基于 Fedora 的发行版上的安装与故障排除"
source: "https://github.com/OttCS/automatic1111-webui-fedora"
author:
published:
created: 2026-05-19
description: "A guide for the installation and troubleshooting of Automatic1111's Stable Diffusion WebUI on Fedora-based distributions - OttCS/automatic1111-webui-fedora"
tags:
  - "clippings"
taxonomy: { doc_category: [TXTDB] }
---
## AUTOMATIC1111/stable-diffusion-webui 用于基于 Fedora 的发行版

**NVIDIA 和 AMD GPU 安装指南**

Fedora 更侧重于开源软件，因此在涉及 NVIDIA 时可能会出现一些问题。我个人使用 Nobara，因为它在 Fedora 的基础上提供了大量的兼容性修复。在本指南中，我将使用"Nobara"而非"Fedora"，因为我在该版本上对这些更改进行了更彻底的测试。

## Fedora 上的 NVIDIA

在软件中心中启用 rpmfusion-nonfree，然后安装最新的专有 NVIDIA 驱动程序。本指南是基于 555.52.04 版本的驱动程序创建的。

## 依赖项

Stable Diffusion 需要 Python 3.10，而 Nobara 已超越此版本。请使用以下命令在您的系统上获取正确的版本。

```apache
sudo dnf install python3.10
```

Minimal Fedora 可能未包含某些必需的包。请确保您也安装了 `pciutils` 和 `gperftools` 。如果您拥有 AMD GPU，还应安装 `lspci` 。

为了方便安装和更新，请确保已安装 `git` 。

## Git 克隆与设置

克隆仓库，使用官方仓库提供的 URL 或以下命令。请确保您处于希望安装该程序的目录（文件夹）中。这将占用大量空间，因此请预留充足的空间：

```bash
git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui.git
```

默认情况下， `webui-user.sh` 文件假设最新版本 Python 可以正常工作，但事实并非如此。请打开并修改第 16 行，将 `#python_cmd="python3"` 更改为以下内容，并确保保存。

```ini
python_cmd="python3.10"
```

注意。这仅指示程序在任何原本会尝试使用 `python` 的地方改用 `python3.10` 。

## 用法

在克隆的 `stable-diffusion-webui` 文件夹内，运行以下命令以启动程序：

```bash
./webui.sh
```

它已经运行起来了！

不过，它将开始下载默认使用的各种模型。这可能需要一些时间，因此您可以在等待时阅读下一节内容，完成后程序将自动启动。顺便一提，下次无需再次执行此操作，且启动速度相当快。

完成后，请尝试以下提示词！它有点像图像生成的“Hello world！”

```livecodeserver
photograph of an astronaut riding a horse
```