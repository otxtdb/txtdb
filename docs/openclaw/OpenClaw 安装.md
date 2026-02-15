---
title: "OpenClaw 安装"
source: "https://openclaws.io/zh/install"
author:
  - "[[OpenClaws.io]]"
published:
created: 2026-02-15
description: "多种安装方式任你选，殊途同归。"
tags:
  - "clippings"
taxonomy: { doc_category: [openclaw] }
---
## 系统要求

Node.js

Node.js 22 或更高版本（推荐 LTS）


OS

Windows 10+、macOS 12+ 或 Linux（Ubuntu 20.04+、Debian 11+）


RAM

最低 2 GB 内存，推荐 4 GB


Disk

安装和依赖大约需要 ~500 MB 磁盘空间


Optional

可选：Python 3.10+（部分技能需要）、Git（源码编译需要）


Network

调用 AI API 需要联网。通过 Ollama 跑本地模型可以离线使用。


## 一键安装


复制粘贴一行命令就完事。大多数人选这个。

### Windows (PowerShell)

建议用管理员权限运行 PowerShell。

PS>`curl -fsSL https://openclaw.ai/install.cmd -o install.cmd && install.cmd --tag beta && del install.cmd`


### macOS / Linux

macOS 和主流 Linux 发行版都能用。

$`curl -fsSL https://openclaw.ai/install.sh | bash -s -- --install-method git`



## 验证安装

运行以下命令确认 OpenClaw 安装正确。

$ `openclaw --version` 

应该输出已安装的版本号（如 v2026.2.13）。



$ `openclaw doctor` 

对你的环境做一次诊断检查：Node.js 版本、依赖、配置文件和网络连接。


$ `openclaw onboard` 

交互式配置向导，带你设置 API Key、连接聊天平台和初始配置。

## settings 初始配置

安装完成后，onboard 向导会引导你完成配置。每一步的作用如下。


### 选择 AI 供应商

选 Anthropic (Claude)、OpenAI (GPT)、Google (Gemini) 或通过 Ollama 跑本地模型。随时可以在配置里切换。



### 添加 API Key

从供应商后台粘贴你的 API Key。Key 存在本地 .env 文件里——除了 AI 供应商，不会发到任何地方。



### 连接聊天平台

接入 WhatsApp（扫二维码）、Telegram（粘贴 @BotFather 的 Bot Token）、Discord（粘贴 Bot Token）或其他支持的平台。


### 发条测试消息

通过已连接的聊天软件给 OpenClaw 发条消息。如果它回复了，就说明一切就绪。试试发：'你能做什么？'

.env — 所有配置存储在 ~/.openclaw/.env。你可以直接编辑这个文件来切换供应商、添加 API Key 或调整设置。完整参考见 docs.openclaw.ai/configuration。

## system\_update\_alt 升级 OpenClaw

保持 OpenClaw 最新版本，获取最新功能、集成和安全补丁。

npm

$ `npm update -g openclaw@latest` 

pnpm

$ `pnpm update -g openclaw@latest` 

Git

$ `cd openclaw && git pull && pnpm install && pnpm run build` 

Docker

$ `docker pull openclaw/openclaw:latest && docker restart openclaw` 

在 github.com/openclaw/openclaw/releases 查看更新日志，了解每个版本的新内容。


## 故障排查

### 安装时提示权限不足

macOS/Linux 上在安装命令前加 sudo，或者用 nvm 等 Node 版本管理器免 root 安装。Windows 上以管理员身份运行 PowerShell（右键 → 以管理员身份运行）。

### Node.js 版本太旧

OpenClaw 需要 Node.js 22+。用 'node --version' 检查版本。用 nvm（macOS/Linux）或 nvm-windows 安装最新 LTS 版本：'nvm install --lts && nvm use --lts'。

### 端口被占用 (EADDRINUSE)

OpenClaw 的 Web UI 默认用 3000 端口。如果被其他应用占了，在 .env 文件里设置自定义端口：'PORT=3001'。或者找到并关掉占用端口的进程。

### WhatsApp 二维码不显示

确保在支持二维码渲染的终端里运行 'openclaw onboard'。如果二维码显示不出来，换个终端模拟器试试。无头服务器上可以用 WebChat 界面扫码。

### API Key 无法识别或认证错误

仔细检查 API Key 是否正确且未过期。确认在 ~/.openclaw/.env 里用了正确的变量名（如 ANTHROPIC_API_KEY、OPENAI_API_KEY）。改完 Key 后重启 OpenClaw。

### Docker 容器启动失败或崩溃

用 'docker logs openclaw' 查看日志。常见原因：缺少环境变量（用 -e 参数传 API Key）、内存不足（至少分配 512MB）、端口冲突。确保安装了 Docker Engine 20+。

### Windows 上 WSL2 相关问题

OpenClaw 在 Windows 上推荐通过 WSL2 使用。先安装 WSL2：在 PowerShell 里运行 'wsl --install'。然后在 WSL2 Linux 环境里安装 OpenClaw，不要在原生 Windows 里装。WSL2 的网络访问和文件系统性能更好。