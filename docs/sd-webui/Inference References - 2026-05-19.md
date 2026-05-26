---
title: "Unix"
source: "https://github.com/Haoming02/sd-webui-forge-classic/wiki/Unix"
author:
published:
created: 2026-05-19
description: "The good ol' Forge WebUI, now updated with new features~ - Inference References · Haoming02/sd-webui-forge-classic Wiki"
tags:
  - "clippings"
taxonomy: { doc_category: [sd-webui] }
---
### Linux 与 macOS 安装指南

0. 准备包管理器
	- 对于 Linux，请使用您发行版自带的包管理器
		- 对于 macOS，可以参考 Homebrew 进行安装
1. 安装 git
	- **例如**
	```mipsasm
	brew install git
	```
2. 安装 FFmpeg
	- **例如**
	```mipsasm
	brew install ffmpeg
	```
3. 安装 uv
	- **例如**
	```mipsasm
	brew install uv
	```

> [!tip] Tip
> 您可能需要在此处重启终端

4. 克隆仓库
```bash
git clone https://github.com/Haoming02/sd-webui-forge-classic sd-webui-forge-neo --branch neo
```
5. 设置 Python 虚拟环境
```jboss
cd sd-webui-forge-neo
uv venv venv --python 3.13 --seed
```
6. 授予启动脚本执行权限
```bash
chmod +x ./webui.sh
chmod +x ./webui-user.sh
```
7. （可选）修改 `COMMANDLINE_ARGS` 为 `webui-user.sh`
8. 通过以下方式启动 WebUI：
```bash
./webui-user.sh
```

---

> [!note] Note
> 对于 Linux 系统，您可能需要安装额外的开发工具（例如 `gcc` ）

> [!tip] Tip
> 如果您遇到错误 `Cannot locate TCMalloc`  
> 请运行 `sudo apt install google-perftools`

> [!important] Important
> macOS 上没有任何注意力包可用...

