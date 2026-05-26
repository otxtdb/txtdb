---
title: "额外安装"
source: "https://github.com/Haoming02/sd-webui-forge-classic/wiki/Extra-Installations"
author:
published:
created: 2026-05-19
description: "The good ol' Forge WebUI, now updated with new features~ - Extra Installations · Haoming02/sd-webui-forge-classic Wiki"
tags:
  - "clippings"
taxonomy: { doc_category: [sd-webui] }
---
> *如果不理解，直接去问一个 LLM 之类的东西……*

## Github Desktop

> `Github Desktop` 为 `git` 仓库提供了一个简单的图形用户界面，方便进行克隆/更新/降级/切换分支等操作

- 从官方网站下载并安装

![](https://github.com/Haoming02/sd-webui-forge-classic/wiki/assets/tutorials/desktop.png)

- 界面将显示已修改的文件及其差异；非开发人员可以直接忽略它们。

#### 添加

- 如果您已经克隆了仓库，请前往 `File/Add local repository...` ，并指定文件夹路径。
- 您可以点击 `Current repository` 来切换需要管理的仓库。

#### 克隆

- 要克隆（即下载）一个新的仓库，请前往 `File/Clone repository...` ，选择 URL 选项，并输入该仓库的 URL。
- 您可以点击 `Current repository` 来切换需要管理的仓库。

#### 更新

- 要更新当前仓库，请先点击 `Fetch origin` 。如果有新的提交可用，按钮将变为 `Pull origin` 。再次点击即可更新至最新提交。

#### 降级

- 如果更新导致某个功能失效，请点击 `History` ，找到最后一个可用的提交，右键点击，然后选择 `Checkout commit`
- 若要重新接收更新，请点击 `Current branch` ，并再次选择原始分支

#### 切换

- 当存在开发分支时，请先点击 `Fetch origin` ，然后点击 `Current branch` 以查看所有分支列表。只需点击您想要参与的分支即可加入测试。

> [!tip] Tip
> 如果您修改了 `webui-user.bat` ，请记得选择“带入我的更改”选项

> [!warning] Warning
> 请勿在经典版与新版分支之间切换

## Insightface

- [https://github.com/Gourieff/Assets/tree/main/Insightface](https://github.com/Gourieff/Assets/tree/main/Insightface)

## 智者注意力

- **Windows:**
	- [https://github.com/woct0rdho/SageAttention/releases](https://github.com/woct0rdho/SageAttention/releases)
- **Linux:**
```bash
cd sd-webui-forge-neo
source venv/bin/activate
cd ..
git clone https://github.com/thu-ml/sageattention
cd SageAttention
python setup.py install
```

## 海王星

- **Windows:**
```cmake
pip install triton-windows
```
- **Linux:**
```cmake
pip install triton
```

## Flash Attention

- [https://github.com/mjun0812/flash-attention-prebuild-wheels/releases](https://github.com/mjun0812/flash-attention-prebuild-wheels/releases)

## Radial Attention

- **Windows:**
	- [https://github.com/woct0rdho/SpargeAttn/releases](https://github.com/woct0rdho/SpargeAttn/releases)
- **Linux:**
	- [https://github.com/thu-ml/SpargeAttn](https://github.com/thu-ml/SpargeAttn)

## 旧版 PyTorch

1. 进入 WebUI 目录
2. 编辑 `webui-user.bat` 文件
3. 添加以下命令（单行；位于 `call webui.bat` 行上方）以指定旧版本：
```apache
set TORCH_COMMAND=pip install torch==2.10.0+cu126 torchvision==0.25.0+cu126 --extra-index-url https://download.pytorch.org/whl/cu126
```

## Git

1. 前往 Git 的安装页面
2. 点击 `Git for Windows/x64 Setup` 下载 `.exe`
3. 安装（您可以将所有选项保留为默认值）
4. 通过在控制台运行 `git` 进行验证
	- 搜索 `cmd`
		- 在 `git` 中输入；按回车键

![](https://github.com/Haoming02/sd-webui-forge-classic/wiki/assets/tutorials/git.png)

## UV

0. 准备系统路径
1. 前往 UV 的发布页面
2. 下载适用于 x64 Windows 的 `.zip` 文件
3. 将 `uv.exe` 提取到您的 `System Path` 文件夹中
4. 通过在控制台运行 `uv` 进行验证
	- 搜索 `cmd`
		- 在 `uv` 中输入；按回车键

![](https://github.com/Haoming02/sd-webui-forge-classic/wiki/assets/tutorials/uv.png)

## FFmpeg

0. 准备系统路径
1. 前往 FFmpeg 的下载页面
2. 点击 `Windows builds from gyan.dev`

![](https://github.com/Haoming02/sd-webui-forge-classic/wiki/assets/tutorials/gyan.png)

3. 下载 `.7z` 文件的精简版

![](https://github.com/Haoming02/sd-webui-forge-classic/wiki/assets/tutorials/essential.png)

4. 将 `bin` 文件夹内的 3 个 `.exe` 文件提取到您的 `System Path` 文件夹中
5. 通过在控制台运行 `ffmpeg` 进行验证
	- 搜索 `cmd`
		- 在 `ffmpeg` 中输入；按回车键

![](https://github.com/Haoming02/sd-webui-forge-classic/wiki/assets/tutorials/ffmpeg.png)

## PATH

> `PATH` 指的是系统搜索可执行文件的文件夹，这意味着可以使用文件名而非完整绝对路径来启动这些文件夹中的软件。

1. 创建新文件夹
	- **例如** `~\Documents\bin`
2. 打开系统属性
	- 搜索 `env`

![](https://github.com/Haoming02/sd-webui-forge-classic/wiki/assets/tutorials/env.png)

3. 打开环境变量

![](https://github.com/Haoming02/sd-webui-forge-classic/wiki/assets/tutorials/prop.png)

4. 点击路径条目；点击“编辑..."。

![](https://github.com/Haoming02/sd-webui-forge-classic/wiki/assets/tutorials/edit.png)

5. 点击“新建”；在路径框中粘贴文件夹路径

![](https://github.com/Haoming02/sd-webui-forge-classic/wiki/assets/tutorials/path.png)

6. 完成！