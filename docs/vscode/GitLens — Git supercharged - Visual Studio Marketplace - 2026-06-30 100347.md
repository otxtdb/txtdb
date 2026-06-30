---
title: "GitLens — Git supercharged - Visual Studio Marketplace"
source: "https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens"
author:
published:
created: 2026-06-30
description: "Extension for Visual Studio Code - Supercharge Git within VS Code — Visualize code authorship at a glance via Git blame annotations and CodeLens, seamlessly navigate and explore Git repositories, gain valuable insights via rich visualizations and powerful comparison commands, and so much more"
tags:
  - "clippings"
taxonomy: { doc_category: [vscode] }
---
## GitLens——让 VS Code 中的 Git 功能更加强大

> 全面提升 Git 的功能，充分挖掘代码库中隐藏的知识，从而更有效地理解、编写和审查代码。专注工作、高效协作、加速开发进程。

GitLens 是一款功能强大的开源插件，专为 Visual Studio Code 设计。该插件由 GitKraken 开发和维护。

利用 VS Code 中强大的 Git 功能来提升您的工作效率吧。这些功能包括在编辑器中直接查看代码的修改历史、代码悬停提示、CodeLens 等。所有这些功能都完全可以自定义。试试 GitLens Pro 的先进功能吧：它能显著提升代码审查的效率，提供丰富的交互式 Git 操作功能，从而帮助您和您的团队更高效地协作。

## 入门指南

可以通过点击上方横幅中的 `Install` 来安装 GitLens，或者直接在 VS Code 的扩展侧边栏中搜索“GitLens”进行安装。

[![Watch the GitLens Getting Started video](https://raw.githubusercontent.com/gitkraken/vscode-gitlens/main/images/docs/get-started-video.png)](https://www.youtube.com/watch?v=UQPb73Zz9qk "Watch the GitLens Getting Started video")

- 在扩展栏中使用 `Switch to Pre-Release Version` ，即可率先体验各项新功能。

> 有疑问或顾虑吗？请通过我们的 GitHub Discussions 页面直接与我们的工程团队联系。如果您对 GitLens 的使用体验满意，请随时留下评价。

## GitLens 版本：社区版与专业版

GitLens Community 是完全免费的，它提供了强大的工具，帮助你管理 Git 代码，了解代码的演变过程以及哪些人参与了代码的修改。该工具还具有诸如在编辑器中直接显示代码修改者信息、悬停提示等功能。你还可以通过“版本导航”功能来查看某个文件的完整历史记录，从而更深入地了解代码的变更情况。

GitLens Pro 通过提供各种高级功能以及无缝的集成体验，将您的工作流程提升到新的水平：

- 通过直接集成在 VS Code 中的简洁且实用的功能界面，您可以快速处理 PR 请求，同时轻松管理整个工作流程。
- 利用提交图，您可以轻松管理各种提交操作。在提交图中，您可以执行各种高级操作，如重新基址调整、合并等。此外，强大的搜索和过滤功能有助于您快速找到所需的提交记录、分支或文件。
- 通过与 GitHub、GitLab 和 Bitbucket 等平台的集成，可以提升协作效率，同时减少不必要的操作流程。用户还可以通过 Launchpad 在 VS Code 中直接查看和管理 PR 请求。

你可以通过注册 GitKraken 账户来免费试用 GitLens Pro。在公共代码库中，部分 Pro 功能可以免费使用。而某些 `Preview` 功能则需要 GitKraken 账户才能使用，这些功能未来也可能会成为 Pro 功能。

工作流程 | 更多功能 | 实验室功能 | 专业版 | 技术支持与社区交流 | 贡献代码 | 贡献者名单 | 许可协议

## 探索强大的工作流程

GitLens 提供了众多功能。以下是用户们最常使用的三种功能，这些功能有助于提升用户的工作效率：

- 交互式代码历史记录——在包含多个分支和贡献者的代码库中，理解代码的逻辑往往相当困难。GitLens 提供了必要的辅助工具，比如代码归属分析、悬停显示功能以及文件注释功能，帮助用户更好地理解代码。不仅如此，其交互式的提交图表功能还允许用户创建分支、重新应用提交记录、撤销更改等操作，同时还具备强大的搜索功能。
- 加快 PR 审核流程——减少上下文切换的麻烦，只需在一个地方即可管理所有的 PR。当与 Github 或其他代码托管平台集成后，可以利用 Launchpad 在 VS Code 中直接对任务进行优先级排序并识别潜在的瓶颈。通过 Worktrees 功能，可以同时处理多个分支，而不会干扰主工作区。
- 提升协作效率——GitLens 并非仅为个人开发者设计，其核心目的是提升团队协作效率。借助“云补丁”和“代码建议”功能，你可以与任何使用 GitLens 或 GitKraken 的用户分享和讨论对多个文件或提交请求所做的修改建议。

## 主视图——你的 VS Code 工作流程中心

Home View 功能简洁而强大：你可以在同一个界面中处理与代码相关的各种任务和问题。只需在一个界面内即可开始处理问题并创建 PR。对于那些希望减少繁琐的操作、专注于 VS Code 中工作的开发者来说，这无疑是个绝佳的工具。

## 利用人工智能加速您的工作流程（预览版）

GitLens 利用人工智能来简化那些繁琐的任务，比如编写提交信息、撰写拉取请求的描述、生成变更日志等。这样一来，你就可以把精力集中在代码本身上。

- 生成提交和暂存信息：能够根据代码的更改情况，快速生成恰当的提交或暂存信息。
- 解释提交记录：在“检查”视图中，通过人工智能生成的简明解释，即可立即了解某次提交记录的背景信息。
- 开放拉取请求：系统会直接根据您在分支上所做的更改来自动生成清晰的拉取请求标题和描述，从而加快审核流程。
- 生成变更日志：轻松汇总代码库中的各项变更，以便用于发布说明或文档更新。
- 更多内容即将推出！

社区功能：如果社区用户使用 GitHub Copilot，或者拥有免费的 GitKraken 账户，并且该账户拥有与 OpenAI、Anthropic、DeepSeek、Gemini 等平台相连的 API 密钥，那么他们就可以免费生成提交信息。

Pro 版功能：订阅 GitLens Pro 即可使用 GitKraken AI 的所有人工智能功能——无需手动管理密钥。

## 交互式代码历史记录

要弄清楚是谁在何时、出于何种原因对代码进行了修改，其实相当困难。GitLens 通过“提交图表”、“代码检查”、“错误追溯”等工具，简化了这一过程，帮助用户更清晰地了解代码的变更历史。利用这些直观的可视化工具和实用的功能，用户可以快速了解代码库的完整历史记录。

## Blame、CodeLens 和 Hovers 功能

通过编辑器内的代码注释和丰富的悬浮提示信息，更深入地了解代码是如何被修改的，以及是由谁进行修改的。

### 内联文本和状态栏中的错误提示/说明

通过在当前行末尾以及状态栏上添加相应的提示信息，来提供关于行号变更的历史背景信息。

![Inline Line Blame](https://raw.githubusercontent.com/gitkraken/vscode-gitlens/main/images/docs/current-line-blame.png)

内嵌的责备注释/内含的批评性说明

![Status Bar Blame](https://raw.githubusercontent.com/gitkraken/vscode-gitlens/main/images/docs/status-bar.png)

状态栏中的错误提示/注释

💡 可以使用命令面板中的 `Toggle Line Blame` 和 `Toggle Git CodeLens` 命令来切换注释的显示状态。

### Git 代码提示

在每个文件的顶部以及每段代码的开头，都会添加与上下文相关的、具有实用价值的作者信息。

- 最近更改——该文件或代码块最近一次被修改的作者及日期
- 作者——该文件或代码块的作者人数，以及其中最主要的作者（如果有多位作者的话）。

### 里奇·霍弗斯

将鼠标悬停在“责任归属”注释上，即可查看详细的说明和可执行的操作。

![Current Line Hovers](https://raw.githubusercontent.com/gitkraken/vscode-gitlens/main/images/docs/hovers-current-line.png)

当前线路处于悬停状态

## 文件注释

使用按需显示的完整文件注释功能，可以查看文件的作者信息、最近的修改内容以及文件内容的分布情况。这些注释会以可视化形式直接显示在编辑器中。

![File Blame](https://raw.githubusercontent.com/gitkraken/vscode-gitlens/main/images/docs/gutter-blame.png)

文件缺陷注释/备注

![File Changes](https://raw.githubusercontent.com/gitkraken/vscode-gitlens/main/images/docs/gutter-changes.png)

文件更改注释

![File Heatmap](https://raw.githubusercontent.com/gitkraken/vscode-gitlens/main/images/docs/gutter-heatmap.png)

文件热力图注释

💡 对于正在编辑的文件，可以使用命令面板中的 `Toggle File Blame` 、 `Toggle File Changes` 和 `Toggle File Heatmap` 命令来切换注释的显示状态。

## 提交图 Pro

可以轻松地查看代码库的概览，同时随时掌握所有正在进行中的工作进度。

利用强大的提交记录搜索功能，轻松找到你想要的内容。该功能具备多种筛选条件：你可以按具体的提交记录、消息内容、提交者、被修改的文件来搜索，甚至还可以按具体的代码更改来查找。了解更多信息。

![Commit Graph](https://raw.githubusercontent.com/gitkraken/vscode-gitlens/main/images/docs/commit-graph.png)

Commit Graph

💡可以通过 `Toggle Commit Graph` 命令快速切换图表显示。

💡使用 `Toggle Maximized Commit Graph` 命令来最大化该图表。

## 修订记录/导航

只需点击一下按钮，你就可以轻松地回顾或浏览任何文件的修改历史。你可以比较不同时期的文件变化情况，查看整个文件或其中某一行内容的修改记录。

![Revision Navigation](https://raw.githubusercontent.com/gitkraken/vscode-gitlens/main/images/docs/revision-navigation.gif)

Revision Navigation

## 加快公关审核流程

在处理 PR 时，通常需要在这三个平台之间来回切换：GitHub、电子邮件和集成开发环境。Launchpad 则是 VS Code 中的集中式 PR 管理工具，借助它，你可以轻松发现各种瓶颈、确定审查的优先级，从而帮助团队更高效地工作。通过 Worktrees 功能，你可以在多个分支上同时进行工作——无论是处理紧急修复、开发新功能，还是进行各种实验——而不会干扰到整个工作空间。

## Launchpad Pro 

Launchpad 将你在 GitHub 上提交的所有拉取请求整合成一个统一的、便于处理的列表。你可以专注于处理那些最重要的请求，从而确保团队的工作能够顺利进行。了解更多信息。

![Launchpad](https://raw.githubusercontent.com/gitkraken/vscode-gitlens/main/images/docs/launchpad.png)

## 工作树 Pro 

工作树使得高效的多任务处理成为可能：你可以在多个分支上同时进行工作，而无需先保存更改或离开当前分支。工作树能保持你的工作流程的连贯性，同时让你能在需要时灵活切换焦点。例如，你可以使用 GitLens，在 VS Code 的另一个窗口中轻松查看工作树上的拉取请求。

![Worktrees view](https://raw.githubusercontent.com/gitkraken/vscode-gitlens/main/images/docs/worktrees.png)

Worktrees view

## 简化协作流程

GitLens 并非仅适用于个人开发者——它的设计初衷就是为了提升团队协作效率。在没有额外提交或创建分支的情况下共享代码其实相当困难。GitLens 通过“云补丁”和“代码建议”功能简化了这一过程：用户可以直接共享或提出对仓库中任何文件的修改意见，而无需进行提交或推送到远程服务器。

## 云补丁 Preview

您可以通过从正在处理的代码、已提交的代码或暂存区中创建“云补丁”，来安全地与他人共享代码更改。只需将相应的链接分享给特定的团队成员和其他开发者即可。云补丁有助于提前获得他人的反馈意见，从而避免重复工作、简化工作流程，同时不会给代码仓库带来不必要的混乱。了解更多信息。

## 代码建议 Preview

摆脱 GitHub 那种仅限于评论形式的有限反馈机制吧。使用 GitLens，你可以直接在集成开发环境中提出代码修改建议，就像编辑 Google 文档一样简单。在代码审查过程中，你可以对项目的任何部分提出反馈——而不仅仅是那些在拉取请求中被修改的代码行。了解更多信息。

![Code Suggest](https://raw.githubusercontent.com/gitkraken/vscode-gitlens/main/images/docs/code-suggest.png)

Code Suggest

## 更多功能

## 侧边栏视图

这些视图的设计旨在提升专注度和工作效率，不过您也可以根据需要自由拖动它们来调整布局。

![Side Bar views](https://raw.githubusercontent.com/gitkraken/vscode-gitlens/main/images/docs/side-bar-views.png)

如上所示，GitLens Inspect 已被手动移至“辅助侧边栏”中。

💡 使用 `Reset Views Layout` 命令可以快速恢复到默认布局。

### GitLens 检查 

X 射线或代码分析工具能够深入检查你的代码，帮助你了解当前正在处理的代码的上下文信息及各种细节。

- 检查——查看某次提交或暂存操作的详细信息。
- 行历史记录——可以查看所选行的所有修改记录。
- 文件历史记录——查看某个文件、文件夹或所选内容的修改历史。
- [**文件版本历史记录 `Pro`**](#visual-file-history-pro) — 可以快速了解文件的变更情况，包括更改的时间、更改的幅度以及具体是谁进行了更改。
- 搜索与比较——可以搜索和查找特定的提交记录、消息、提交者、被修改的文件等。还可以查看不同分支、标签、提交记录之间的差异。

### GitLens 

可以快速使用 GitLens 的各类功能。这里也是 GitKraken 团队及相关协作服务（如 Cloud Patches、Cloud Workspaces）的所在地，同时还能获取各种帮助和支持。

- 主页——可快速访问各种功能。
- [**Cloud Patches `Preview`**](#cloud-patches-preview) — 与特定的团队成员安全、私密地共享代码
- [**Cloud Workspaces `Preview`**](#gitkraken-workspaces-preview) — 可轻松地将多个代码库进行分组和管理。无论身处何地，都能访问这些代码库，从而大大简化了工作流程。

### 源代码控制

提供了一些额外的视图，这些视图有助于用户更好地管理和查看自己的代码库。

- 提交记录——全面展示当前分支的提交历史，包括那些尚未被推送的更改、上游仓库的状态、各种对比数据等。
- 分支——管理和操作各个分支。
- 远程仓库——管理和操作远程仓库及分支。
- 暂存——保存那些你还不想提交的更改，以便日后再处理。
- 标签——管理和操作各种标签。
- [**Worktrees `Pro`**](#worktrees-pro) — 可以同时处理代码仓库中的不同分支。
- 贡献者——按顺序列出的所有贡献者，详细介绍了每个人的贡献和参与情况。
- 仓库管理——将上述各种管理方式整合在一起，从而更高效地管理多个仓库。

### （底部）面板

可以通过专门的详细视图，方便地查看 Commit Graph 的相关信息。

## 云工作空间 Preview

云工作空间让你能够轻松地对多个代码库进行管理。无论身处何地，都能访问这些代码库，从而大大简化了工作流程。你可以为自己创建工作空间，也可以与团队共享工作空间（GitLens 即将支持此功能）。这样就能更快地让新成员上手，提升团队协作效率。了解更多信息。

## 可视化文件历史记录 Pro

可以快速了解文件的变更情况，包括变更发生的时间、变更的幅度以及具体是谁进行了这些变更。利用该功能，可以轻松找出对文件影响最大的变更内容，或者确定应该与谁沟通有关文件变更的问题。

![Visual File History view](https://raw.githubusercontent.com/gitkraken/vscode-gitlens/main/images/docs/visual-file-history-illustrated.png)

Visual File History view

## 交互式重置编辑器

利用这款直观易用的交互式重排编辑器，您可以轻松地可视化并配置各种重排操作。只需通过拖放操作来重新排列提交记录，然后选择需要编辑、合并或删除的提交记录即可。

![Interactive Rebase Editor](https://raw.githubusercontent.com/gitkraken/vscode-gitlens/main/images/docs/rebase.gif)

Interactive Rebase Editor

## 综合命令/全方位指令

不必再担心记忆 Git 命令了；GitLens 提供了丰富的命令功能，能帮助你完成所有需要做的事情。

### Git 命令面板

这是一种循序渐进的指导方式，有助于用户快速、安全地执行 Git 命令。

![Git Command Palette](https://raw.githubusercontent.com/gitkraken/vscode-gitlens/main/images/docs/git-command-palette.png)

Git Command Palette

### 快速访问命令

使用一系列新命令来：

- 查看各分支和文件的提交历史记录
- 快速搜索并定位到相应的提交记录，然后对其执行相应操作。
- 查看某次提交的文件内容
- 查看和浏览你的收藏品吧。
- 查看当前仓库的状态

## 集成/整合

上下文切换会降低工作效率。GitLens 不仅能帮助你发现代码库中那些被忽视的知识点，还能从各种问题记录和拉取请求中获取更多相关信息。这样一来，你就能轻松获得大量有用的信息和洞察力。

通过自动连接 GitHub、GitHub Enterprise `Pro` 、GitLab、GitLab Self-Managed `Pro` 、Jira、Gitea、Gerrit、Google Source、Bitbucket、Bitbucket Server、Azure DevOps 以及各种自定义服务器上的问题与拉取请求，您可以简化工作流程，更快地获取所需信息。

所有集成都支持自动链接功能。而与 GitHub、GitLab 和 Jira 的深度集成则提供了更详细的悬停信息，有助于实现自动链接。此外，这些集成还展示了拉取请求、分支和提交记录之间的关联关系，同时显示了用户头像，从而提供了更完整的上下文信息。

## 定义你自己的自动链接功能

在提交信息中，可以使用自动链接功能来引用外部资源，比如 Jira 任务或 Zendesk 工单。

## 准备好使用 GitLens Pro 了吗？

当您准备充分，想要充分发挥 GitLens 的强大功能并享受其带来的种种好处时，建议您升级到 GitLens Pro 版本。使用 GitLens Pro，您将能够使用私有托管代码库中的 Pro 级功能。

如需了解 Pro 版所具备的更多功能，请访问 GitLens 社区版与 GitLens Pro 版的对比页面。

## 支持与社区互动

相关支持文档可以在 GitLens 帮助中心找到。如果您需要进一步的帮助或有任何疑问，GitLens 还提供了多种支持渠道和社区论坛供您使用：

## 问题报告与功能需求提交

发现漏洞了吗？有功能需求吗？请在我们的 GitHub Issues 页面上与我们联系。

## 讨论/交流 

请加入 GitHub Discussions 上的 GitLens 社区，与其他用户交流、分享您的使用经验，并探讨与 GitLens 相关的各种话题。

## GitKraken 客服支持

如果您在使用 GitLens 时遇到任何问题或需要咨询，请通过官方支持页面联系 GitKraken 的支持团队。他们会很高兴地帮助您解决所遇到的各种问题。

使用 GitLens Pro，您可以获得我们客户成功团队的优先级电子邮件支持，从而确保更快的响应速度和更高效的售后服务。此外，我们还提供个性化的培训和服务，帮助您和您的团队更快地上手使用 GitLens Pro。

## 做出贡献/有所贡献

GitLens 是一个开源项目，它之所以能够取得如此出色的成果，离不开社区成员的贡献和反馈。

您对 GitLens 社区的贡献、反馈以及积极参与，都具有重要意义。这些努力有助于塑造 GitLens 的未来。感谢您的支持！

## 代码贡献情况

想要为 GitLens 做出贡献吗？请按照《贡献指南》来开始吧。

## 文档贡献

非常感谢大家对文档的贡献。如果您发现有任何需要改进的地方，或者有新的文档编写建议，您可以将其作为拉取请求提交到 GitLens Docs 仓库中。