---
title: "Perplexica 搜索 API 文档"
source: "https://github.com/ItzCrazyKns/Perplexica/blob/master/docs/API/SEARCH.md"
author:
  - "[[ItzCrazyKns]]"
published:
created: 2026-03-01
description: "Perplexica is an AI-powered answering engine. Contribute to ItzCrazyKns/Perplexica development by creating an account on GitHub."
tags:
  - "clippings"
taxonomy: { doc_category: [perplexica] }
---
## 概述
Perplexica 的搜索 API 使您能够轻松使用我们的 AI 驱动搜索引擎。您可以运行不同类型的搜索，选择您想要使用的模型，并获取最新信息。请按照以下标题了解更多关于 Perplexica 的搜索 API。

## 端点
### 获取可用提供者和模型
在进行搜索请求之前，您需要获取可用的提供者及其模型。

#### **GET** `/api/providers`
**完整 URL**: `http://localhost:3000/api/providers`

返回所有活跃提供者的列表及其可用的聊天和嵌入模型。

**响应示例：**

{
  "providers": \[
    {
      "id": "550e8400-e29b-41d4-a716-446655440000",
      "name": "OpenAI",
      "chatModels": \[
        {
          "name": "GPT 4 Omni Mini",
          "key": "gpt-4o-mini"
        },
        {
          "name": "GPT 4 Omni",
          "key": "gpt-4o"
        }
      \],
      "embeddingModels": \[
        {
          "name": "Text Embedding 3 Large",
          "key": "text-embedding-3-large"
        }
      \]
    }
  \]
}

在进行搜索请求时，使用 `id` 字段作为 `providerId`，并使用模型数组中的 `key` 字段。

### 搜索查询

#### **POST** `/api/search`
**完整 URL**: `http://localhost:3000/api/search`

**注意** ：如果运行在不同的主机或端口上，请将 `localhost:3000` 替换为您的 Perplexica 实例 URL

### 请求该 API 在请求体中接受一个 JSON 对象，其中定义了启用的搜索 `sources`、聊天模型、嵌入模型以及您的查询。

#### 请求体结构
{
  "chatModel": {
    "providerId": "550e8400-e29b-41d4-a716-446655440000",
    "key": "gpt-4o-mini"
  },
  "embeddingModel": {
    "providerId": "550e8400-e29b-41d4-a716-446655440000",
    "key": "text-embedding-3-large"
  },
  "optimizationMode": "speed",
  "sources": \["web"\],
  "query": "What is Perplexica",
  "history": \[
    \["human", "Hi, how are you?"\],
    \["assistant", "I am doing well, how can I help you today?"\]
  \],
  "systemInstructions": "Focus on providing technical details about Perplexica's architecture.",
  "stream": false
}

**注意** : `providerId` 必须是从 `/api/providers` 端点获取的有效 UUID。上述示例使用了一个示例 UUID 进行演示。

### 请求参数
- **`chatModel`** (对象, 必填): 定义用于查询的聊天模型。要获取可用的提供者和模型，请向 `http://localhost:3000/api/providers` 发送 GET 请求。
	- `providerId` (字符串): 提供者的 UUID。您可以从 `/api/providers` 端点响应中获取此值。
	- `key` (字符串): 模型键/标识符（例如，`gpt-4o-mini`、`llama3.1:latest`）。使用提供者的 `chatModels` 数组中的 `key` 值，而不是显示名称。
- **`embeddingModel`** (对象, 必填): 定义用于基于相似性搜索的嵌入模型。要获取可用的提供者和模型，请向 `http://localhost:3000/api/providers` 发送 GET 请求。
	- `providerId` (string): 嵌入提供者的 UUID。您可以从 `/api/providers` 端点响应中获取此值。
	- `key` (字符串): 嵌入模型的键（例如，`text-embedding-3-large`, `nomic-embed-text`）。请使用提供者 `embeddingModels` 数组中的 `key` 值，而不是显示名称。
- **`sources`** (数组，必填): 启用哪些搜索源。可用值：
	- `web`, `academic`, `discussions`.
- **`optimizationMode`** (字符串，可选): 指定优化模式以控制性能和质量的平衡。可用模式：
	- `speed`: 优先考虑速度并返回最快的答案。
	- `balanced`: 提供一个平衡的答案，兼顾速度和合理质量。
	- `quality`: 优先考虑答案质量（可能较慢）。
- **`query`** (字符串, 必填): 搜索查询或问题。
- **`systemInstructions`** (字符串, 可选): 用户提供的自定义指令，用于指导 AI 的回应。这些指令被视为用户偏好，优先级低于系统的核心指令。例如，您可以指定特定的写作风格、格式或关注领域。
- **`history`** (数组, 可选): 代表对话历史的消息对数组。每对消息由一个角色（'human' 或 'assistant'）和消息内容组成。这允许系统使用对话的上下文来优化结果。示例：
	\[
	  \["human", "What is Perplexica?"\],
	  \["assistant", "Perplexica is an AI-powered search engine..."\]
	\]
- **`stream`** (布尔值, 可选): 当设置为 `true` 时，启用流式响应。默认为 `false`。

### 响应
API 响应包括最终消息以及生成该消息所使用的来源。

#### 标准响应（stream: false）
{
  "message": "Perplexica is an innovative, open-source AI-powered search engine designed to enhance the way users search for information online. Here are some key features and characteristics of Perplexica:\\n\\n\- \*\*AI-Powered Technology\*\*: It utilizes advanced machine learning algorithms to not only retrieve information but also to understand the context and intent behind user queries, providing more relevant results \[1\]\[5\].\\n\\n\- \*\*Open-Source\*\*: Being open-source, Perplexica offers flexibility and transparency, allowing users to explore its functionalities without the constraints of proprietary software \[3\]\[10\].",
  "sources": \[
    {
      "content": "Perplexica is an innovative, open-source AI-powered search engine designed to enhance the way users search for information online.",
      "metadata": {
        "title": "What is Perplexica, and how does it function as an AI-powered search ...",
        "url": "https://askai.glarity.app/search/What-is-Perplexica--and-how-does-it-function-as-an-AI-powered-search-engine"
      }
    },
    {
      "content": "Perplexica is an open-source AI-powered search tool that dives deep into the internet to find precise answers.",
      "metadata": {
        "title": "Sahar Mor's Post",
        "url": "https://www.linkedin.com/posts/sahar-mor\_a-new-open-source-project-called-perplexica-activity-7204489745668694016-ncja"
      }
    }
        ....
  \]
}

#### 流式响应（stream: true）
当启用流式传输时，API 使用服务器发送事件（SSE）返回一系列由换行符分隔的 JSON 对象。每一行包含一个完整的、有效的 JSON 对象。响应具有 `Content-Type: text/event-stream` 。

流式响应对象的示例：

```
{"type":"init","data":"Stream connected"}
{"type":"sources","data":[{"content":"...","metadata":{"title":"...","url":"..."}},...]}
{"type":"response","data":"Perplexica is an "}
{"type":"response","data":"innovative, open-source "}
{"type":"response","data":"AI-powered search engine..."}
{"type":"done"}
```

客户端应将每一行处理为独立的 JSON 对象。不同的消息类型包括：

- **`init`**：初始连接消息
- **`sources`**：用于响应的所有来源
- **`response`**：生成的答案文本的片段
- **`done`**: 表示流已完成

### 响应中的字段
- **`message`** (字符串): 搜索结果，基于查询和启用的 `sources` 生成。
- **`sources`** (数组): 用于生成搜索结果的来源列表。每个来源包括：
	- `content`: 从源中提取的相关内容片段。
	- `metadata`: 关于源的元数据，包括：
		- `title`: 网页标题。
		- `url`: 网页 URL。

### 错误处理
如果在搜索过程中发生错误，API 将返回适当的错误消息和 HTTP 状态码。

- **400**: 如果请求格式错误或缺少必填字段（例如，没有 `sources` 或 `query`）。
- **500**: 如果在搜索过程中发生内部服务器错误。
