---
title: "Perplexica 架构"
source: "https://github.com/ItzCrazyKns/Perplexica/blob/master/docs/architecture/README.md"
author:
  - "[[ItzCrazyKns]]"
published:
created: 2026-03-01
description: "Perplexica is an AI-powered answering engine. Contribute to ItzCrazyKns/Perplexica development by creating an account on GitHub."
tags:
  - "clippings"
taxonomy: { doc_category: [perplexica] }
---

Perplexica 是一个 Next.js 应用程序，结合了 AI 聊天体验和搜索功能。

关于高层流程，请参阅 [WORKING.md](https://github.com/ItzCrazyKns/Perplexica/blob/master/docs/architecture/WORKING.md)。关于更深入的实现细节，请参阅 [CONTRIBUTING.md](https://github.com/ItzCrazyKns/Perplexica/blob/master/CONTRIBUTING.md)。

## 关键组件1. **用户界面**
	- 一个基于网络的 UI，允许用户聊天、搜索和查看引用。
2. **API 路由**
	- `POST /api/chat` 驱动聊天界面。
	- `POST /api/search` 提供程序化搜索端点。
	- `GET /api/providers` 列出可用提供者和模型密钥。
3. **代理和编排**
	- 系统首先对问题进行分类。
	- 它可以并行运行研究和组件。
	- 它生成最终答案并包含引用。
4. **搜索后端**
	- 当启用研究功能时，使用元搜索后端来获取相关的网络结果。
5. **LLMs（大型语言模型）**
	- 用于分类、撰写答案和生成引用。
6. **嵌入模型**
	- 用于对用户上传的文件进行语义搜索。
7. **存储**
	- 聊天记录和消息被存储，以便可以重新加载对话。