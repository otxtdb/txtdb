---
title: "在 NVIDIA GPU 上安装和运行"
source: "https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Install-and-Run-on-NVidia-GPUs"
author:
published:
created: 2026-05-19
description: "Stable Diffusion web UI. Contribute to AUTOMATIC1111/stable-diffusion-webui development by creating an account on GitHub."
tags:
  - "clippings"
taxonomy: { doc_category: [sd-webui] }
---
## 自动安装

## Windows（方法 1）

> 在 Windows 10/11 的 NVIDIA GPU 上运行 Stable Diffusion Web UI 的基础指南。

1. 从此处下载 `sd.webui.zip` ，该包来自 `v1.0.0-pre` ，我们将在第 3 步将其更新为最新的 Web UI 版本。
2. 在您希望的位置解压 zip 文件。
3. 双击 `update.bat` 将 Web UI 更新至最新版本，等待完成然后关闭窗口。
- 可选（50 系列 GPU 必需）使用 `switch-branch-toole.bat` 切换到 `dev` 分支。
4. 双击 `run.bat` 以启动 Web UI，首次启动时将下载大量文件。待所有文件下载并安装完成后，您应会看到消息“ `Running on local URL:  http://127.0.0.1:7860` ”，打开该链接即可呈现 Web UI 界面。

> 您应该能够开始生成图像

> 目前 50 系列 GPU 需要使用 `PyTorch 2.7` ，该功能尚未合并到 master 分支  
> 请使用 `switch-branch-toole.bat` 切换到 `dev` 分支以讨论英伟达 Blackwell 50XX GPU 的指令

### 通过 COMMANDLINE\_ARGS 进行额外配置

有一些配置选项您可能希望应用于 Web UI，若要配置这些选项，您需要编辑位于 `sd.webui\webui\webui-user.bat` 的启动脚本，在 `set COMMANDLINE_ARGS=` 之后添加所选参数，如下所示：

```routeros
set COMMANDLINE_ARGS=--autolaunch --update-check
```

> 每个参数之间需要用空格分隔，上述示例将配置 Web UI 在加载完成后自动启动浏览器页面，并在启动时检查是否有新版本。

### 故障排除

Web UI 的默认配置应在大多数现代 GPU 上运行，但在某些情况下，您可能需要一些额外的参数来使其正常工作。

1. 对于显存（VRAM）较少的 GPU，您可能需要使用 `--medvram` 或 `--lowvram` ，这些优化会降低显存需求但会牺牲性能。如果您没有足够的显存，Web UI 可能会因内存不足错误而拒绝启动或无法生成图像。所需的显存量很大程度上取决于您期望的图像分辨率，更多详情请参见故障排除部分。

> Tiled VAE 扩展有助于降低显存需求。

2. 如果生成的图像呈现黑色或绿色，请尝试添加 `--precision full` 和 `--no-half` 。
3. 某些模型与 VAE 的组合容易产生 `NansException: A tensor with all NaNs was produced in VAE` ，导致图像变黑；使用选项 `--no-half-vae` 可能有助于缓解此问题。

### 其他选项

1. 存在多种交叉注意力优化方法，例如 `--xformers` 或 `--opt-sdp-attention` ，这些方法可大幅提升性能，详见“优化”部分；请尝试不同的选项，因为不同的硬件适合不同的优化方案。若需衡量系统性能，可使用 sd-extension-system-info 扩展，该扩展具备基准测试工具和用户提交结果数据库。
2. 添加 `--autolaunch` 可在 Web UI 启动后自动打开网页浏览器。
3. 添加 `--update-check` 将在有新版本发布时通知您。
4. 有关更多配置选项，请参阅“命令行参数和设置”。

### 提示

如果您已经下载了 Stable Diffusion 模型，可以在第 3 步运行 `run.bat` 之前将模型移至 `sd.webui\webui\models\Stable-diffusion\` ，这样即可跳过自动下载 vanilla stable-diffusion-v1-5 模型。

## 重要步骤（若不使用 dev 分支或 method 1）

[详见该讨论线程](https://github.com/AUTOMATIC1111/stable-diffusion-webui/discussions/17212)

对于 Windows 用户，请将以下内容添加到 webui-user.bat

```routeros
set STABLE_DIFFUSION_REPO=https://github.com/w-e-w/stablediffusion.git
```

对于 Linux 和 Mac，请将此内容添加到 webui-user.sh 中

```routeros
export STABLE_DIFFUSION_REPO="https://github.com/w-e-w/stablediffusion.git"
```

> 开发分支以及 sd.webui.zip 已包含此修复

## Windows（方法 2）

1. 安装 Python 3.10.6（64 位）（勾选“添加到 PATH"），以及 git
2. 从搜索栏打开命令提示符，并输入 `git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui`
3. 在 webui-user.bat 中添加以下行，然后保存文件，详见此帖

```routeros
set STABLE_DIFFUSION_REPO=https://github.com/w-e-w/stablediffusion.git
```

4. 双击 `webui-user.bat`

如果安装过程中遇到问题，可观看安装视频：  
<sup>solves <a href="https://github.com/AUTOMATIC1111/stable-diffusion-webui/issues/8229">#8229</a></sup>

视频：（点击展开） webui\_h264.mp4 <video src="https://private-user-images.githubusercontent.com/98228077/223032534-c5dd5b13-a4b6-47a7-995c-27ed8ba8b3e7.mp4?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkyMDM3ODIsIm5iZiI6MTc3OTIwMzQ4MiwicGF0aCI6Ii85ODIyODA3Ny8yMjMwMzI1MzQtYzVkZDViMTMtYTRiNi00N2E3LTk5NWMtMjdlZDhiYThiM2U3Lm1wND9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA1MTklMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNTE5VDE1MTEyMlomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWI5MTg1YmU2YWY3MTBjOGQ5Y2I2MTM5MTNkOTljNjQ0NWNjNjkxMjM4ZDE3ODI4OWQ4ZDVhYzNiYTA4ZjYzZDEmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT12aWRlbyUyRm1wNCJ9.O3yhvLexptcy8By-6iEg6C_MPS3Aias6YgI_vD7LYpo" controls="controls"></video> 替代的 PowerShell 启动脚本：

**webui.ps1**

```powershell
if ($env:PYTHON -eq "" -or $env:PYTHON -eq $null) {
    $PYTHON = "Python.exe"
} else {
    $PYTHON = $env:PYTHON
}

if ($env:VENV_DIR -eq "" -or $env:VENV_DIR -eq $null) {
    $VENV_DIR = "$PSScriptRoot\venv"
} else {
    $VENV_DIR = $env:VENV_DIR
}

if ($env:LAUNCH_SCRIPT -eq "" -or $env:LAUNCH_SCRIPT -eq $null) {
    $LAUNCH_SCRIPT = "$PSScriptRoot\launch.py"
} else {
    $LAUNCH_SCRIPT = $env:LAUNCH_SCRIPT
}

$ERROR_REPORTING = $false

mkdir tmp 2>$null

function Start-Venv {
    if ($VENV_DIR -eq '-') {
        Skip-Venv
    }

    if (Test-Path -Path "$VENV_DIR\Scripts\$python") {
        Activate-Venv
    } else {
        $PYTHON_FULLNAME = & $PYTHON -c "import sys; print(sys.executable)"
        Write-Output "Creating venv in directory $VENV_DIR using python $PYTHON_FULLNAME"
        Invoke-Expression "$PYTHON_FULLNAME -m venv $VENV_DIR > tmp/stdout.txt 2> tmp/stderr.txt"
        if ($LASTEXITCODE -eq 0) {
            Activate-Venv
        } else {
            Write-Output "Unable to create venv in directory $VENV_DIR"
        }
    }
}

function Activate-Venv {
    $PYTHON = "$VENV_DIR\Scripts\Python.exe"
    $ACTIVATE = "$VENV_DIR\Scripts\activate.bat"
    Invoke-Expression "cmd.exe /c $ACTIVATE"
    Write-Output "Venv set to $VENV_DIR."
    if ($ACCELERATE -eq 'True') {
        Check-Accelerate
    } else {
        Launch-App
    }
}

function Skip-Venv {
    Write-Output "Venv set to $VENV_DIR."
    if ($ACCELERATE -eq 'True') {
        Check-Accelerate
    } else {
        Launch-App
    }
}

function Check-Accelerate {
    Write-Output 'Checking for accelerate'
    $ACCELERATE = "$VENV_DIR\Scripts\accelerate.exe"
    if (Test-Path -Path $ACCELERATE) {
        Accelerate-Launch
    } else {
        Launch-App
    }
}

function Launch-App {
    Write-Output "Launching with python"
    Invoke-Expression "$PYTHON $LAUNCH_SCRIPT"
    #pause
    exit
}

function Accelerate-Launch {
    Write-Output 'Accelerating'
    Invoke-Expression "$ACCELERATE launch --num_cpu_threads_per_process=6 $LAUNCH_SCRIPT"
    #pause
    exit
}

try {
    if(Get-Command $PYTHON){
        Start-Venv
    }
} Catch {
    Write-Output "Couldn't launch python."
}
```

**webui-user.ps1**

```autoit
[Environment]::SetEnvironmentVariable("PYTHON", "")
[Environment]::SetEnvironmentVariable("GIT", "")
[Environment]::SetEnvironmentVariable("VENV_DIR","")

# Commandline arguments for webui.py, for example: [Environment]::SetEnvironmentVariable("COMMANDLINE_ARGS", "--medvram --opt-split-attention")
[Environment]::SetEnvironmentVariable("COMMANDLINE_ARGS", "")

# script to launch to start the app
# [Environment]::SetEnvironmentVariable("LAUNCH_SCRIPT", "launch.py")

# install command for torch
# [Environment]::SetEnvironmentVariable("TORCH_COMMAND", "pip install torch==1.12.1+cu113 torchvision==0.13.1+cu113 --extra-index-url https://download.pytorch.org/whl/cu113")

# Requirements file to use for stable-diffusion-webui
# [Environment]::SetEnvironmentVariable("REQS_FILE", "requirements_versions.txt")

# [Environment]::SetEnvironmentVariable("GFPGAN_PACKAGE", "")
# [Environment]::SetEnvironmentVariable("CLIP_PACKAGE", "")
# [Environment]::SetEnvironmentVariable("OPENCLIP_PACKAGE", "")

# URL to a WHL if you wish to override default xformers windows
# [Environment]::SetEnvironmentVariable("XFORMERS_WINDOWS_PACKAGE", "")

# Uncomment and set to enable an alternate repository URL
# [Environment]::SetEnvironmentVariable("STABLE_DIFFUSION_REPO", "")
# [Environment]::SetEnvironmentVariable("TAMING_TRANSFORMERS_REPO", "")
# [Environment]::SetEnvironmentVariable("K_DIFFUSION_REPO", "")
# [Environment]::SetEnvironmentVariable("CODEFORMER_REPO", "")
# [Environment]::SetEnvironmentVariable("BLIP_REPO", "")

# Uncomment and set to enable a specific revision of a repository
# [Environment]::SetEnvironmentVariable("STABLE_DIFFUSION_COMMIT_HASH", "")
# [Environment]::SetEnvironmentVariable("TAMING_TRANSFORMERS_COMMIT_HASH", "")
# [Environment]::SetEnvironmentVariable("K_DIFFUSION_COMMIT_HASH", "")
# [Environment]::SetEnvironmentVariable("CODEFORMER_COMMIT_HASH", "")
# [Environment]::SetEnvironmentVariable("BLIP_COMMIT_HASH", "")

# Uncomment to enable accelerated launch
# [Environment]::SetEnvironmentVariable("ACCELERATE", "True")

$SCRIPT = "$PSScriptRoot\webui.ps1"
Invoke-Expression "$SCRIPT"
```

请参阅“故障排除”部分，了解出现问题时应采取的措施。

## Linux

列出的命令将把 WebUI 安装到您的当前目录。

> ℹ️ 注意：如果您想使用系统中已安装的其他 Python 版本，请取消 `webui-user.sh` 中第 16 行的注释，并添加现有的 Python 版本：

```ini
python_cmd="python3.10"
# Or path:
python_cmd="/home/$USER/.pyenv/versions/3.10.6/bin/python3.10"
```

**Ubuntu 24.04**

```smali
sudo apt install git software-properties-common -y
sudo add-apt-repository ppa:deadsnakes/ppa -y
sudo apt install python3.10-venv -y
git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui && cd stable-diffusion-webui
python3.10 -m venv venv
./webui.sh
```

**Fedora 40**

```bash
sudo dnf install git python310 -y
git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui && cd stable-diffusion-webui 
python3.10 -m venv venv
./webui.sh
```

**Arch Linux**

```bash
sudo pacman -S git -y
git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui && cd stable-diffusion-webui
```

通过 AUR 包安装 python3.10：

```vim
yay -S python310
python3.10 -m venv venv
./webui.sh
```

或者，通过 pyenv 安装。（点击展开）

在 Arch Linux 上，大多数 `pyenv` 所需的依赖项应该都已满足，但您可能仍然需要运行：

```bash
sudo pacman -S gcc make -y
```

然后按照以下方式安装 `pyenv` 和您选择的 Python 版本：

```apache
sudo pacman -S pyenv -y
pyenv install 3.10.6
```

现在，您只需运行以下命令来创建具有特定 Python 版本的虚拟环境（venv）：

```awk
~/.pyenv/versions/3.10.6/bin/python3.10 -m venv venv
```

然后开始安装过程。

```bash
./webui.sh
```

## 第三方安装指南/脚本：

- NixOS：[https://github.com/virchau13/automatic1111-webui-nix](https://github.com/virchau13/automatic1111-webui-nix)
- Fedora：[https://github.com/OttCS/automatic1111-webui-fedora](https://github.com/OttCS/automatic1111-webui-fedora)

## 无需虚拟环境即可安装和运行

通过 pip 安装所需包而不创建虚拟环境，请运行：

```mel
python launch.py
```

命令行参数可直接传入，例如：

```vim
python launch.py --opt-split-attention --ckpt ../secret/anime9999.ckpt
```

## 手动安装

手动安装已非常过时，可能无法正常工作。请在仓库的 README 中查看 colab 部分的说明以获取操作指南。

以下过程将在 Windows 或 Linux（后者需将 `dir` 替换为 `ls` ）上手动安装所有组件：

```awk
# install torch with CUDA support. See https://pytorch.org/get-started/locally/ for more instructions if this fails.
pip install torch --extra-index-url https://download.pytorch.org/whl/cu113

# check if torch supports GPU; this must output "True". You need CUDA 11. installed for this. You might be able to use
# a different version, but this is what I tested.
python -c "import torch; print(torch.cuda.is_available())"

# clone web ui and go into its directory
git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui.git
cd stable-diffusion-webui

# clone repositories for Stable Diffusion and (optionally) CodeFormer
mkdir repositories
git clone https://github.com/CompVis/stable-diffusion.git repositories/stable-diffusion-stability-ai
git clone https://github.com/CompVis/taming-transformers.git repositories/taming-transformers
git clone https://github.com/sczhou/CodeFormer.git repositories/CodeFormer
git clone https://github.com/salesforce/BLIP.git repositories/BLIP

# install requirements of Stable Diffusion
pip install transformers==4.19.2 diffusers invisible-watermark --prefer-binary

# install k-diffusion
pip install git+https://github.com/crowsonkb/k-diffusion.git --prefer-binary

# (optional) install GFPGAN (face restoration)
pip install git+https://github.com/TencentARC/GFPGAN.git --prefer-binary

# (optional) install requirements for CodeFormer (face restoration)
pip install -r repositories/CodeFormer/requirements.txt --prefer-binary

# install requirements of web ui
pip install -r requirements.txt  --prefer-binary

# update numpy to latest version
pip install -U numpy  --prefer-binary

# (outside of command line) put stable diffusion model into web ui directory
# the command below must output something like: 1 File(s) 4,265,380,512 bytes
dir model.ckpt
```

安装已完成，要启动 Web UI，请运行：

```vim
python webui.py
```

## Windows 11 WSL2 安装指南

要在 Windows 11 的 WSL2 下安装 Linux 发行版：

```bash
# install conda (if not already done)
wget https://repo.anaconda.com/archive/Anaconda3-2022.05-Linux-x86_64.sh
chmod +x Anaconda3-2022.05-Linux-x86_64.sh
./Anaconda3-2022.05-Linux-x86_64.sh

# Clone webui repo
git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui.git
cd stable-diffusion-webui

# Create and activate conda env
conda env create -f environment-wsl2.yaml
conda activate automatic
```

此时，可以自步骤 `# clone repositories for Stable Diffusion and (optionally) CodeFormer` 开始应用手动安装的说明。

## 使用 Conda 在 Windows 上的替代安装方式

- 先决条件（仅在你没有这些工具时才需要）。假设已安装 Chocolatey。
	```cmake
	# install git
	choco install git
	# install conda
	choco install anaconda3
	```
	可选参数：git、conda
- 安装（警告：部分文件超过多个 GB，请先确保有足够的磁盘空间）
	1. 下载为.zip 格式并解压，或使用 git 进行克隆。
		```bash
		git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui.git
		```
		2. 启动 Anaconda 提示符。需要注意的是，您可以使用较旧版本的 Python，但您可能被迫手动移除诸如缓存优化之类的功能，这将降低您的性能。
		```apache
		# Navigate to the git directory
		cd "GIT\StableDiffusion"
		# Create environment
		conda create -n StableDiffusion python=3.10.6
		# Activate environment
		conda activate StableDiffusion
		# Validate environment is selected
		conda env list
		# Start local webserver
		webui-user.bat
		# Wait for "Running on local URL:  http://127.0.0.1:7860" and open that URI.
		```
		3. （可选）前往 CompVis 并下载最新模型，例如 1.4，然后将其解压到 ex：
		```moonscript
		GIT\StableDiffusion\models\Stable-diffusion
		```
		之后，通过重新启动 Anaconda 提示符来重启服务器，并
		```dockerfile
		webui-user.bat
		```
- 值得尝试的替代默认设置：
	1. 尝试使用 Euler a（祖传欧拉）采样器，并设置较高的采样步数，例如 40 或 100。
		2. 将“设置 > 用户界面 > 每隔 N 个采样步骤显示图像生成进度”设置为 1，并选择一个确定性的种子值。这样可以直观地观察图像扩散过程，并使用 ScreenToGif 录制.gif 文件。
		3. 启用“修复人脸”。通常能获得更好的效果，但高质量是以牺牲速度为代价的。

**设置**

- [在 NVIDIA GPU 上安装和运行](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Install-and-Run-on-NVidia-GPUs)
- [在 AMD GPU 上安装和运行](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Install-and-Run-on-AMD-GPUs)
- [在 Apple 芯片上安装和运行](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Installation-on-Apple-Silicon)
- [在 Intel 芯片上安装和运行（外部 Wiki 页面）](https://github.com/openvinotoolkit/stable-diffusion-webui/wiki/Installation-on-Intel-Silicon)
- [通过容器（即 Docker）安装和运行](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Containers)
- [通过在线服务运行](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Online-Services)

**图像生成/故障排除**

- [种子值变更](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Seed-breaking-changes)
	- [仍然无法复现结果？请首先尝试此方法。](https://github.com/AUTOMATIC1111/stable-diffusion-webui/discussions/13093)
- [通用故障排除](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Troubleshooting)

**用法**

- [功能特性](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Features)
- [命令行参数与设置](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Command-Line-Arguments-and-Settings)
- [优化选项](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Optimizations)
- [自定义文件名和子目录](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Custom-Images-Filename-Name-and-Subdirectory)
- [更改模型文件夹位置，例如外部磁盘](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Change-model-folder-location)
- [用户界面自定义](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/User-Interface-Customizations)
- [指南和教程](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Guides-and-Tutorials)

**开发者**

Obsidian Reader · 2,675 words · parsed in 600 ms