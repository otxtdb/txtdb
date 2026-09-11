---
title: "logancyang/obsidian-copilot: THE Copilot in Obsidian"
source: "https://github.com/logancyang/obsidian-copilot"
author:
published:
created: 2026-08-27
description: "THE Copilot in Obsidian. Contribute to logancyang/obsidian-copilot development by creating an account on GitHub."
tags:
  - "clippings"
taxonomy: { doc_category: [obsidian] }
---
## logancyang/obsidian-copilot：Obsidian 中的 Copilot

## Obsidian 的 Copilot 工具

**您的黑曜石保险库中的药剂**

Copilot V4 将 OpenCode、Claude Code 和 Codex 功能引入到 Obsidian 中，使得用户可以在研究、写作和知识管理工作中使用这些工具。

[![Best LLM Integration Award](https://github.com/logancyang/obsidian-copilot/raw/master/images/llm-integration.svg)](https://obsidian.md/blog/2024-goty-winners/)

[**第 1 号黑曜石人工智能插件**](https://obsidian.md/plugins?id=copilot)

[![Copilot V4 agent organizing research into connected Obsidian notes](https://github.com/logancyang/obsidian-copilot/raw/master/images/copilot-v4-agent-mode.png)](https://github.com/logancyang/obsidian-copilot/blob/master/images/copilot-v4-agent-mode.png)

在 Obsidian 系统中安装 · 查看计划 · 开始使用

---

## 选择你自己的代理。

“Agent”是 Copilot 中用于多步骤操作的主要工具。它可以检查笔记、使用各种工具、创建 Obsidian 文件，并能在多个回合中持续运行，而所有权限都由用户掌控。

- opencode（推荐方式）：让 Copilot 负责下载和管理相关文件，然后你可以使用 Copilot 提供的模型、自己的提供商密钥，或者本地保存的模型。
- 克劳德代码：连接现有的安装设备。Copilot 能够自动识别常见的安装位置，并使用您的克劳德代码登录凭证进行连接。
- 代码集：通过 `@agentclientprotocol/codex-acp` 适配器连接代码集，并使用您现有的代码集登录凭证。

是否已经为 Claude 或 ChatGPT 支付了费用，或者已经拥有该模型的 API 访问权限？那么你可以将这些访问权限带入 Copilot 中，而无需购买 Copilot 的套餐。不过，提供商的条款和使用限制仍然适用。

[了解 Agent 的工作原理→](https://github.com/logancyang/obsidian-copilot/blob/master/docs/agent-mode-and-tools.md)

## 设置 Copilot

1. 从 Obsidian 社区插件中安装 Copilot。
2. 打开设置 → 选择 Copilot → 进入基础模式 → 选择代理程序。
3. 请选择“下载 opencode”，或者通过自动识别的方式连接 Claude Code 或 Codex。使用 Codex 之前，需要先安装 `codex-acp` 适配器。
4. 选择“Agent”功能区图标，或者打开“Open Copilot Agent Chat Window”窗口。

入门指南会介绍每一种设置方式，包括 Codex 适配器的命令以及手动执行的路径。

## 围绕你的保险库构建而成

- 项目：为持续进行的任务提供专门的指令、可重复使用的上下文以及聊天记录。项目可以配合 OpenCode、Claude 或 Codex 等工具进行协作。了解更多关于项目的信息。
- 跨代理共享的技能：只需为某个技能添加一次，然后为其启用功能即可。Copilot 还包含了针对 Obsidian Markdown、Bases、Canvas 以及 Obsidian CLI 的技能相关功能。了解更多关于技能的信息。
- 命令：保存可重复的提示信息，在 Agent 中使用 `/` 来运行它们，或者将它们展示在编辑器和命令面板中。创建一条命令。
- 快速提问：在离开备注界面之前就可以提出问题。继续对话吧，可以替换文本、插入答案或复制内容。快速提问功能基于你的快速聊天模式设计。已经设置了快速提问功能。
- 多个会话：为不同的任务分别打开独立的 Agent 标签页。拥有有效的 Plus 访问权限后，可以使用 `@` 来提及多个已安装的 Agent，从而发起只读的调研或审查请求。

对于不需要代理人参与的简短对话，可以使用快速聊天功能。

## 使用托管模型、基于角色的模型，或者本地模型。

- 由 Copilot 托管：首先添加 Copilot 许可证，然后选择适用于 OpenCode 或 Quick Chat 的托管模型。模型选择器和仪表板会显示当前的访问权限情况。
- 请自行携带密钥：在设置菜单中，选择“Copilot”选项，然后选择“BYOK”功能。可以将密钥存储在本设备的 Obsidian 密钥链中，而不是存储在保管库中的 `data.json` 处。
- 克劳德和代码手册的账户：这些代理使用他们自己的命令行界面登录凭证，而不是 Copilot 的 BYOK 设置中的密钥。
- OpenCode 报告的模型信息显示：OpenCode 会将用户引导至他们的托管服务提供商处。那些免费的 OpenCode Zen 模型会显示警告信息，因为该托管服务提供商可能会记录或训练用户的行为；在发送敏感内容之前，请先查看其服务条款。

你选择的路径决定了哪些提示和上下文会被处理。关于设置的相关信息，请参阅《LLM 提供商指南》；关于隐私和路由细节，请参阅《Copilot Plus》和《Self-Host》文档。

## 计划

Copilot 插件是开源软件，当使用自己的代理账户、提供商密钥或本地模型时，无需购买 Copilot 许可证即可使用。免费使用包括普通的单代理聊天、支持 Markdown 格式的项目界面、自定义技能和命令、快速聊天功能、快速提问功能，以及本地 Miyo 搜索功能。

付费访问包括由 Copilot 提供支持的各种模型，以及基于云的工具。而多代理模式则需要活跃的 Plus 会员权限；请查看您的仪表板以获取当前的权限信息。模型的可获得性和服务限制可能会发生变化，因此请参考定价页面和应用程序中的模型选择工具，以获取最新信息。

[**比较各种计划 →**](https://www.obsidiancopilot.com/en/pricing)

## 那些以思考为职业的人信任我。

> “这是第一个真正能够统一我搜索、组织以及获取知识方式的工具，而无需离开 Obsidian 平台。我的工作流程变得更加高效、深入且紧密衔接。我无法想象没有这个工具的情况下如何工作。”
> 
> 杰森·张，投资者与研究分析师

**来自社区更多的消息**

> "I drop meeting transcriptions, personal notes, and architecture ideas into my vault. Copilot gives me a personal assistant that finds missing puzzle pieces and surfaces relevant info during live calls, no manual searches."
> 
> **Brad Decker**, CTO, Concierge Auctions

> "Since discovering Copilot, my writing process has been completely transformed. Conversing with my own articles and thoughts is the most refreshing experience I've had in decades."
> 
> **Mat QV**, Professional Writer

## 常见问题解答

**我可以不使用付费计划就使用 Copilot 吗？**

是的。可以使用现有的账户来连接 Claude Code 或 Codex，或者利用 opencode 和 Quick Chat 功能，结合自己的 API 密钥或本地模型进行连接。不过，你的服务提供商可能会收取相关费用。

**Agent 在移动设备上也能使用吗？**

Agent 是一种桌面应用程序，因为其后端运行在本地进程中。Quick Chat、自定义命令以及快速提问功能在移动设备上仍然可用。

**我的数据是如何被处理的呢？**

您的笔记仍保存在您的存储空间中，而本地版的 Miyo 索引则保留在您的设备上。提示信息以及相关的上下文内容会被传输到您选择的模型或服务上。由 Copilot 托管的模型和服务会将所需的输入数据发送至 Brevilabs 进行处理。请参考下方的隐私政策以获取更多信息。

## 帮助和链接

文档资料 · YouTube · 报告错误 · 请求功能支持 · 隐私问题

## 支持这个项目。

如果 Copilot 对您有所帮助，请考虑在 GitHub 上资助该项目，或者请我们喝杯咖啡作为感谢。

### 感谢我们的 GitHub 赞助商们。

特别感谢我们的主要赞助商：@mikelaaron、@pedramamini、@Arlorean、@dashinja、@azagore、@MTGMAD、@gpythomas、@emaynard、@scmarinelli、@borthwick、@adamhill、@gluecode、@rusi、@timgrote、@JiaruiYu-Consilium、@ddocta、@AMOz1、@chchwy、@pborenstein、@GitTom、@kazukgw、@mjluser1、@joesfer、@rwaal、@turnoutnow-harpreet、@dreznicek、@xrise-informatik、@jeremygentles、@ZhengRui、@bfoujols、@jsmith0475、@pagiaddlemon、@sebbyyyywebbyyy、@royschwartz2、@vikram11、@amiable-dev、@khalidhalim、@DrJsPBs、@chishaku、@Andrea18500、@shayonpal、@rhm2k、@snorcup、@JohnBub、@obstinatelark、@jonashaefele、@vishnu2kmohan

## 付费计划的披露信息

Copilot 是由 Brevilabs LLC 开发的产品，与 Obsidian 并无关联。如需了解当前的计划详情，请访问 obsidiancopilot.com。

- 需要注册并支付费用以获得付费访问权限。
- 托管模型以及基于云的功能都需要网络访问权限。
- **隐私与数据处理：**
	- 免费使用：消息和注释内容将交由 LLM 提供商、本地端点或您配置的 CLI 代理来处理。除非您调用了 Brevilabs 提供的功能，否则 Brevilabs 不会接收这些内容。
		- 付费托管服务：Brevilabs 的后端系统以及那些经过审核的企业级服务提供商会处理所有的请求。而由 Copilot 托管的嵌入模型则负责处理被索引的笔记文本。这些托管服务还会接收各种输入数据，比如搜索查询、URL 地址，以及 Quick Chat 工具或 Agent 项目上下文中的相关文件。隐私政策规定，这些输入数据只会被临时处理，不会被保留或用于训练模型。
		- 用户 ID：托管的功能请求会包含一个随机生成的 UUID，以实现服务交付、防止许可证滥用以及限制访问频率。该 ID 不用于跟踪、分析或统计用途。
- 请查看隐私政策以获取完整的条款内容。
- Copilot 插件的前端界面是完全开源的。而支持托管功能的后端服务则是闭源且属于专有技术。
- 如果您对购买的产品不满意，我们提供 14 天内的全款退款服务。