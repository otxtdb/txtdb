---
title: "Perplexica"
source: "https://github.com/ItzCrazyKns/Perplexica"
author:
  - "[[ItzCrazyKns]]"
published:
created: 2026-02-26
description: "Perplexica is an AI-powered answering engine. Contribute to ItzCrazyKns/Perplexica development by creating an account on GitHub."
tags:
  - "clippings"
taxonomy: { doc_category: [perplexica] }
---
Perplexica 是一款 **注重隐私的 AI 答题引擎** ，完全运行在你的自有硬件上。它结合了来自广阔互联网的知识，并支持 **本地 LLMs**（Ollama）和云服务提供商（OpenAI、Claude、Groq），在提供准确答案的同时附上 **引用来源** ，同时确保你的搜索完全私密。


想了解更多关于它的架构和工作原理吗？你可以 [在这里](https://github.com/ItzCrazyKns/Perplexica/tree/master/docs/architecture/README.md)阅读。

## ✨ 功能
🤖 **支持所有主要 AI 提供商** \- 通过 Ollama 使用本地 LLMs，或连接到 OpenAI、Anthropic Claude、Google Gemini、Groq 等。根据你的需求混合搭配模型。

⚡ **智能搜索模式** \- 当你需要快速答案时选择速度模式，日常搜索选择平衡模式，深度研究选择质量模式。

🧭 **选择你的信息来源** \- 搜索网络、讨论或学术论文。更多信息来源和集成正在开发中。

🧩 **小工具** \- 在相关情况下出现的实用 UI 卡片，如天气、计算、股票价格和其他快速查询。

🔍 **由 SearxNG 驱动的网络搜索** \- 访问多个搜索引擎同时保护你的隐私。即将支持 Tavily 和 Exa，以获得更好的搜索结果。

📷 **图像和视频搜索** \- 在文本结果旁边查找视觉内容。搜索不再仅限于文章。

📄 **文件上传** \- 上传文档并询问相关问题。PDF 文件、文本文件、图片——Perplexica 都能理解。

🌐 **搜索特定域名** \- 当你知道查找位置时，可将搜索限制在特定网站。非常适合技术文档或研究论文。

💡 **智能建议** \- 输入时获取智能搜索建议，助您构建更佳查询。

📚 **发现** \- 浏览全天有趣的文章和热门内容。无需搜索即可保持信息更新。

🕒 **搜索历史** \- 每次搜索均本地保存，让您随时回顾发现。研究资料永不丢失。

✨ **即将推出更多** \- 我们正根据社区反馈积极开发新功能。加入我们的 Discord，共同塑造 Perplexica 的未来！


## 安装
主要有两种安装 Perplexica 的方式——使用 Docker、不使用 Docker。强烈推荐使用 Docker。

### 使用 Docker 开始（推荐）
Perplexica 可以轻松使用 Docker 运行。只需运行以下命令：

docker run -d -p 3000:3000 -v perplexica-data:/home/perplexica/data --name perplexica itzcrazykns1337/perplexica:latest

这将拉取并启动捆绑了 SearxNG 搜索引擎的 Perplexica 容器。运行后，打开您的浏览器并导航到 [http://localhost:3000](http://localhost:3000/)。您可以直接在设置屏幕中配置您的设置（API 密钥、模型等）。

  
**注意** ：图像中包含 Perplexica 和 SearxNG，因此无需额外设置。-v 标志为您的数据和上传文件创建持久卷。

#### 使用您自己的 SearxNG 实例与 Perplexica
如果您已经运行了 SearxNG，您可以使用 Perplexica 的精简版：

docker run -d -p 3000:3000 -e SEARXNG\_API\_URL=http://your-searxng-url:8080 -v perplexica-data:/home/perplexica/data --name perplexica itzcrazykns1337/perplexica:slim-latest

**重要** ：确保您的 SearxNG 实例具有：

- 设置中启用了 JSON 格式
- Wolfram Alpha 搜索引擎启用

将 `http://your-searxng-url:8080` 替换为你的实际 SearxNG URL。然后在 [http://localhost:3000](http://localhost:3000/) 的设置屏幕中配置你的 AI 提供者设置。

#### 高级设置（从源代码构建）
如果你希望从源代码构建或需要更多控制：

1. 确保你的系统上安装并运行了 Docker。
2. 克隆 Perplexica 仓库：
	git clone https://github.com/ItzCrazyKns/Perplexica.git
3. 克隆后，导航到包含项目文件的目录。
4. 使用 Docker 构建并运行：
	docker build -t perplexica .
	docker run -d -p 3000:3000 -v perplexica-data:/home/perplexica/data --name perplexica perplexica
5. 访问 Perplexica，请前往 [http://localhost:3000](http://localhost:3000/)，并在设置界面中配置您的设置。

**注意** : 容器构建完成后，您可以直接从 Docker 启动 Perplexica，无需打开终端。

### 非 Docker 安装
1. 安装 SearXNG 并在 SearXNG 设置中允许 `JSON` 格式。确保 Wolfram Alpha 搜索引擎也已启用。
2. 克隆仓库：
	git clone https://github.com/ItzCrazyKns/Perplexica.git
	cd Perplexica
3. 安装依赖项：
	npm i
4. 构建应用程序：
	npm run build
5. 启动应用程序：
	npm run start
6. 打开浏览器并导航至 [http://localhost:3000](http://localhost:3000/) 以完成设置并在设置界面中配置您的设置（API 密钥、模型、SearxNG URL 等）。

**注意** ：推荐使用 Docker，因为它简化了设置过程，尤其是在管理环境变量和依赖项方面。

查看[安装文档](https://github.com/ItzCrazyKns/Perplexica/tree/master/docs/installation)以获取更多关于更新等信息。

### 故障排除
#### 符合 Local OpenAI-API 的本地服务器
如果 Perplexica 告诉你没有配置任何聊天模型提供者，请确保：

1. 您的服务器正在运行在 `0.0.0.0`（而不是 `127.0.0.1`）并且在与您在 API URL 中输入的相同端口上。
2. 您已指定本地 LLM 服务器加载的正确模型名称。
3. 您已指定正确的 API 密钥，或者如果未定义，您已在 API 密钥字段中输入了*某些内容*且未将其留空。

#### Ollama 连接错误
如果您遇到 Ollama 连接错误，这可能是由于后端无法连接到 Ollama 的 API。要解决这个问题，您可以：

1. **检查您的 Ollama API URL：** 确保 API URL 在设置菜单中已正确设置。
2. **根据操作系统更新 API URL：**
	- **Windows:** 使用 `http://host.docker.internal:11434`
	- **Mac:** 使用 `http://host.docker.internal:11434`
	- **Linux:** 使用 `http://<private_ip_of_host>:11434`
	如果你使用的是其他端口，请调整端口号。
3. **Linux 用户 - 暴露 Ollama 到网络：**
	- 在 `/etc/systemd/system/ollama.service` 中，你需要添加 `Environment="OLLAMA_HOST=0.0.0.0:11434"` 。（如果你使用的是不同的端口，请更改端口号。）然后使用 `systemctl daemon-reload` 重新加载 systemd 管理器配置，并通过 `systemctl restart ollama` 重启 Ollama。更多信息请参见 [Ollama 文档](https://github.com/ollama/ollama/blob/main/docs/faq.md#setting-environment-variables-on-linux)
	- 确保端口（默认为11434）没有被你的防火墙封锁。

#### 柠檬水连接错误
如果你遇到柠檬水连接错误，很可能是后端无法连接到柠檬水的 API。要解决这个问题，你可以：

1. **检查你的柠檬水 API URL：** 确保 API URL 在设置菜单中正确设置。
2. **根据操作系统更新 API URL：**
	- **Windows:** 使用 `http://host.docker.internal:8000`
	- **Mac:** 使用 `http://host.docker.internal:8000`
	- **Linux:** 使用 `http://<private_ip_of_host>:8000`
	如果你使用的是不同的端口，请调整端口号码。
3. **确保 Lemonade 服务器正在运行：**
	- 确保你的 Lemonade 服务器在配置的端口（默认为 8000）上正在运行且可访问。
	- 验证 Lemonade 已配置为接受来自所有接口的连接（`0.0.0.0`），而不仅仅是 localhost（`127.0.0.1`）。
	- 确保端口（默认为8000）没有被你的防火墙封锁。

## 用作搜索引擎
如果你希望将 Perplexica 用作传统搜索引擎（如 Google 或 Bing）的替代品，或者如果你想在浏览器的搜索栏中添加一个快捷方式以便快速访问，请按照以下步骤操作：

1. 打开浏览器的设置。
2. 导航到“搜索引擎”部分。
3. 添加一个新的站点搜索，使用以下 URL：`http://localhost:3000/?q=%s`。将 `localhost` 替换为你的 IP 地址或域名，如果 Perplexica 没有在本地托管，请将 `3000` 替换为端口号。
4. 点击添加按钮。现在，你可以直接从浏览器的搜索栏使用 Perplexica。

## 使用 Perplexica 的 APIPerplexica 还为希望将其强大的搜索引擎集成到自己的应用程序中的开发者提供 API。您可以运行搜索、使用多个模型并获得对您查询的答案。

了解更多详情，请查看完整文档 [此处](https://github.com/ItzCrazyKns/Perplexica/tree/master/docs/API/SEARCH.md) 。

## 将 Perplexica 暴露到网络
Perplexica 基于 Next.js 运行，处理所有 API 请求。它可以在同一网络中立即运行，即使使用端口转发也能保持可访问性。

