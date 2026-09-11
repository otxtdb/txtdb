---
title: "ESLint - Visual Studio Marketplace"
source: "https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint"
author:
published:
created: 2026-08-26
description: "Extension for Visual Studio Code - Integrates ESLint JavaScript into VS Code."
tags:
  - "clippings"
taxonomy: { doc_category: [vscode] }
---
[跳转至内容部分](#start-of-content)

## ESLint

## 微软

[microsoft.com](https://microsoft.com/)

|

52,429,414 次安装次数

将 ESLint JavaScript 工具集成到 VS Code 中。

## VS Code ESLint 扩展程序

该扩展模块使用了在已打开的工作空间文件夹中安装的 ESLint 库。如果文件夹中没有该库，扩展模块会尝试查找全局的 ESLint 安装版本。如果你既没有本地安装 ESLint，也没有在全局范围内安装它，请通过运行相关命令来进行安装：

**本地安装（推荐方式）：**

```bash
# npm
npm install --save-dev eslint

# yarn
yarn add --dev eslint

# pnpm
pnpm add --save-dev eslint

# bun
bun add --dev eslint
```

**全球安装：**

```bash
# npm
npm install -g eslint

# yarn
yarn global add eslint

# pnpm
pnpm add -g eslint

# bun
bun add -g eslint
```

在新的项目中，你可能需要创建一个 ESLint 配置文件。对于 ESLint 9 版本及更高版本（或者使用扁平化配置方式的 ESLint 8.57 及更高版本），你应该选择以下其中一个配置文件：

- eslint.config.js（最常见的情况）
- eslint.config.mjs
- eslint.config.cjs
- eslint.config.ts
- eslint.config.mts

你可以通过运行以下命令来生成一个初始配置：

`npx eslint --init`

示例全球启动器设置.json 文件：

```json
{
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": "explicit"
  }
}
```

工作区设置在不同项目中可能会有所不同，这是为了进行特定的验证而需要的。

```json
{
 "eslint.validate": [
    "javascript",
    "typescript",
    "vue"
  ]
}
```

对于使用旧版本 ESLint 的项目（低于 8.57 版本），需要使用旧的 `.eslintrc` 文件（如 `.eslintrc.json` 、 `.eslintrc.js` 等）。

## 索引

## 发布说明

本节介绍了主要版本及其改进之处。如需详细的变化列表，请参考变更日志。

从版本 2.2.3 开始，前导的“奇数”或“补数”版本号表示内部使用或预发布版本。因此， `2.2.3` 、 `2.2.5` 和 `2.3.1` 版本都属于预发布版本。而 `2.2.10` 、 `2.4.10` 和 `3.0.0` 则属于正式发布的版本。

### 版本 3.0.34 - 发布版本

- 添加对批量抑制功能的支持（请参阅新的设置选项 eslint.bulkSuppression.）
- 移动到最新的 LSP 库版本
- [漏洞修复](https://github.com/microsoft/vscode-eslint/issues?q=is:issue%20state:closed%20milestone:3.0.34)
- [公关人员](https://github.com/microsoft/vscode-eslint/pulls?q=is:pr+milestone:3.0.34+is:closed)

### 版本 3.0.33——预发布版本

- 移动到最新的 LSP 库版本

### 版本 3.0.31——预发布版本

- 移动到最新的 LSP 库版本

### 版本 3.0.29——预发布版本

- 移动到最新的 LSP 库版本

### 版本 3.0.27——预发布版本

- 移动到最新的 LSP 库版本

### 版本 3.0.25——预发布版本

- 添加对批量抑制功能的支持（请参阅新的设置选项 eslint.bulkSuppression.）
- 移动到最新的 LSP 库版本
- [漏洞修复](https://github.com/microsoft/vscode-eslint/issues?q=is:issue%20state:closed%20milestone:3.0.25)
- [公关人员](https://github.com/microsoft/vscode-eslint/pulls?q=is:pr+milestone:3.0.25+is:closed)

### 版本 3.0.24 - 发布

- [漏洞修复](https://github.com/microsoft/vscode-eslint/issues?q=is:issue%20state:closed%20milestone:3.24.0)

### 版本 3.0.22 - 发布

- 发布编号有缺失

### 版本 3.0.21——预发布版本

- 移动到最新的 LSP 库版本
- `eslint.quiet` 也阻止了信息提示的显示。

### 版本 3.0.20 - 发布

- [漏洞修复](https://github.com/microsoft/vscode-eslint/issues?q=is:issue%20state:closed%20milestone:3.20.0)
- [公关人员](https://github.com/microsoft/vscode-eslint/pulls?q=is:pr+milestone:3.20.0+is:closed)

### 版本 3.0.19——预发布版本

- 移动到最新的 LSP 库版本

### 版本 3.0.17——预发布版本

- 添加对 CSS 的探测支持

### 版本 3.0.16 - 发布

- [漏洞修复](https://github.com/microsoft/vscode-eslint/issues?q=is:issue%20state:closed%20milestone:3.16.0)

### 版本 3.0.15——预发布版本

- 移动到最新的 LSP 库版本

### 版本 3.0.13——预发布版本

- 移动到最新的 LSP 库版本

### 版本 3.0.11——预发布版本

- 生效验证设置。如果指定了 `eslint.validate` 设置，那么只有该列表中的文件才会进行验证。例如，形式为这样的设置：
	```markdown
	"eslint.validate": [
	    "javascript"
	]
	```
	只会验证 JavaScript 文件。这相当于在命令行中提供了扩展名。

### 版本 3.0.10 - 发布版本

- 将 VS Code 的版本更新到 1.90，以确保能够使用 NodeJS 20。

### 版本 3.0.8 - 发布版本

- 与发布前的情况相同

### 版本 3.0.5——预发布版本

- 对新的 ESLint 扁平化配置文件的支持得到了改进。已经实施了以下变更：
	- 要使用扁平化的配置文件，建议使用 ESLint 8.57.0 及以上版本。
		- 实验性配置 `eslint.experimental.useFlatConfig` 已经不再被推荐使用，仅适用于 ESLint 版本为 8.21 到 8.57.0 的版本。
- 已将服务器配置改为使用诊断级别的拉取操作，而非推式操作。
- 这些文件将在重点审核环节再次进行有效性验证。
- 添加一条命令 `ESLint: Revalidate all open files` ，用于重新验证所有打开的文件。
- 为 Astro、MDX 和 JSON 提供技术支持
- 各种漏洞修复工作已完成

### 版本 2.4.4

- 与 2.4.3 相同——在发布之前使用

### 版本 2.4.3——预发布版本

- 各种漏洞修复工作

### 版本 2.4.2

- 与 2.4.1 版本发布前的情况相同。

### 版本 2.4.1——预发布版本

- 各种漏洞修复工作

### 版本 2.4.0（与 2.3.5 相同——预发布版本）

- 增加了一些设置选项，可以用来控制在出现警告或错误之前进行验证和修复的工作时间预算。这些设置分别位于 `eslint.timeBudget.onValidation` 和 `eslint.timeBudget.onFixes 位置。`
- 创建服务器 `untitled` 不可知的
- 这个扩展现在使用了 VS Code 的语言状态指示器。
- 语言状态指示器现在可以显示代码是否经过长时间编译，以及在保存文件时的处理时间情况。
- 该环境设置已被移除，因为现在该设置被显示为一种语言状态指示器。
- 支持扁平化的配置文件格式
- 对单一问题的支持被强调出来。
- 各种漏洞修复工作

### 版本 2.3.5——预发布版本

- 增加了一些设置选项，可以用来控制在出现警告或错误之前进行验证和修复的工作时间预算。这些设置分别位于 `eslint.timeBudget.onValidation` 和 `eslint.timeBudget.onFixes 位置。`

### 版本 2.3.3——预发布版本

- 创建服务器 `untitled` 不可知的

### 版本 2.3.1——预发布版本（仅内部使用）

- 这个扩展现在使用了 VS Code 的语言状态指示器。
- 语言状态指示器现在可以显示代码是否经过长时间编译，以及在保存文件时的处理时间情况。

### 版本 2.3.0——预发布版本

- 支持扁平化的配置文件格式
- 对单一问题的支持被强调出来。

### 版本 2.2.6（与 2.2.5 的预发布版本相同）

- 增加了对单个笔记本文档单元格进行验证的支持，前提是该语言被 ESLint 所支持。

### 版本 2.2.5——预发布版本

- 增加了对单个笔记本文档单元格进行验证的支持，前提是该语言被 ESLint 所支持。

### 版本 2.2.0

### 版本 2.1.22

采用了与 VS Code 的工作区信任模型相适配的方式。因此，在 `2.1.7` 版本中引入的自定义对话框功能被移除了。此外， `off` 值也被添加到了 eslint 规则的自定义功能中。

### 版本 2.1.20

增加了对调整 ESLint 规则严格度的自定义功能。请参考新的设置 `eslint.rules.customizations` 。

### 版本 2.1.18

请求确认 `eslint.nodePath` 的值后，发现该值是在工作区文件夹级别单独定义的。不过，当涉及到多工作区文件夹组合时（例如代码工作区文件），这种设置需要确保在相应的 `code-workspace` 文件中定义 `eslint.nodePath` 值。现在，扩展功能会提醒用户注意这一点。下面是一个这样的 `code-workspace` 文件的示例。

```json
{
        "folders": [
                {
                        "path": "project-a"
                },
                {
                        "path": "project-b"
                }
        ],
        "settings": {
                "eslint.nodePath": "myCustomNodePath"
        }
}
```

### 版本 2.1.17

为了遵循 VS Code 的模式，确认那些会影响代码执行的 workspace 本地设置，现在有两个设置 `eslint.runtime` 和 `eslint.nodePath` 需要用户的确认，这些设置是存在于工作区文件夹还是工作区文件中。在使用这些设置的用户中，会收到通知提醒他们需要进行确认操作。

该版本还增加了一个命令，用于重新启动 ESLint 服务器。

### 版本 2.1.10

用于批准执行 ESLint 库的流程已经进行了修改。目前的体验如下：

- 当 ESLint 扩展程序首次尝试加载某个 ESLint 库时，如果没有获得许可，就不会显示任何模态对话框。相反，ESLint 的状态栏项会变为 ，表示当前执行处于阻塞状态。
- 如果活跃的文本编辑器内容需要使用 ESLint 进行验证，那么文件中出现的任何问题都会被显示出来。

可以通过以下手势来批准或拒绝执行 ESLint 库的相关操作：

- 点击状态栏中的图标
- 使用了针对相应 ESLint 问题的快速修复方案

所有的操作都会打开下一个对话框：

![ESLint Dialog](https://github.com/Microsoft/vscode-eslint/raw/HEAD/images/2_1_10/eslint-dialog.png)

所选的操作会反映在 ESLint 的状态栏项中，表现形式如下：

- `Allow` 会将状态栏项的名称前面加上一个复选标记。
- `Allow Everywhere` 会将状态栏项的名称前面加上一个双勾号。
- `Deny` 和 `Disable` 将会在状态栏项的名称前加上“被封锁”的标志。

你可以使用以下命令来管理我们的决策：

- `ESLint: Manage Library Execution` 将会重新打开上述对话框
- `ESLint: Reset Library Decisions` 你可以重置之前做出的决定。

### 版本 2.0.4

该扩展程序的 2.0.4 版本包含以下主要改进：

- 改进的 TypeScript 检测功能——一旦在 ESLint 中正确配置了 TypeScript，就无需再通过 VS Code 的 `eslint.validate` 设置进行额外配置了。对于 HTML 和 Vue.js 文件来说也是如此。
- 格式化器支持：ESLint 现在可以用作格式化工具。要启用此功能，请使用 `eslint.format.enable` 设置。
- 改进的保存时自动修复功能——现在，保存时自动修复功能已成为 VS Code 的“代码动作”的一部分，能够一次性计算出所有可能的修复方案。该功能可以通过 `editor.codeActionsOnSave` 设置进行自定义。该设置支持 ESLint 特定的属性 `source.fixAll.eslint` ，同时该扩展也遵循通用的属性 `source.fixAll` 。

下方的设置会为所有插件启用自动修复功能，包括 ESLint：

```json
"editor.codeActionsOnSave": {
    "source.fixAll": "explicit"
}
```

相比之下，这种配置只会在使用 ESLint 时才会激活该功能：

```json
"editor.codeActionsOnSave": {
    "source.fixAll.eslint": "explicit"
}
```

您还可以选择禁用 ESLint：

```json
"editor.codeActionsOnSave": {
    "source.fixAll": "explicit",
    "source.fixAll.eslint": "never"
}
```

请注意，执行代码操作的时长为 750 毫秒，这对于大型的 JavaScript/TypeScript 文件来说可能不够用。你可以使用 `editor.codeActionsOnSaveTimeout` 设置来延长这个时间预算。

旧的 `eslint.autoFixOnSave` 设置已经不再适用，可以安全地将其移除。

## 设置选项

- `eslint.enable` ：用于启用/禁用工作区文件夹中的 ESLint 检查。默认是启用的状态。
- `eslint.debug` ：启用 ESLint 的调试模式（相当于命令行选项--debug）。有关调试输出的详细信息，请查看 ESLint 的输出通道。这个选项非常有助于追踪 ESLint 在验证文件时出现的配置和安装问题，因为它会提供详细的信息来说明 ESLint 是如何处理文件的。
- `eslint.lintTask.enable` ：该扩展功能是否能为整个工作区文件夹的代码进行静态分析检查。
- ```json
	{
	  "eslint.lintTask.options": "-c C:/mydirectory/.eslintrc.json --ignore-path C:/mydirectory/.eslintignore ."
	}
	```
- 旧的 `eslint.packageManager` 设置已经不再被推荐使用，可以安全地将其移除。这一设置原本用于控制包管理器来解析 ESLint 库。不过，这种影响仅发生在 ESLint 库在全球范围内被解析的情况下。有效的值有 `"npm"` 、 `"yarn"` 或 `"pnpm"` 。
- ```json
	{
	  "eslint.options": { "overrideConfigFile": "C:/mydirectory/.eslintrc.json" }
	}
	```
	请注意，如果您覆盖了配置文件的位置并使用了相对路径，那么您可能需要指定一个工作目录，以确保配置文件能够按照该目录的关联方式被定位到。
	```json
	{
	  "eslint.options": { "configFile": "C:/mydirectory/.eslintrc.json" }
	}
	```
- `eslint.useESLintClass` (@从 2.2.0 版本开始) – 即使存在 CLIEngine API，是否仍然使用 ESLint 的类 API。此设置仅在使用 ESLint 7.x 版本时才生效。
- `eslint.run` - 请运行 Linter `onSave` 或 `onType` ，默认为 `onType` 。
- `eslint.quiet` – 忽略警告，默认值为 `false` 。
- - 注意：如果您使用的是远程连接（例如 WSL、Remote SSH、DevContainer 等），并且不想修改整个工作区的设置，那么您需要通过命令面板运行“偏好设置：打开远程设置（JSON 格式）”命令。在设置面板中配置所需的选项，然后重新加载编辑器，以确保 Linter 服务器能够应用这些更改。
- `eslint.execArgv` - 使用此设置可以向节点运行时传递额外的参数，例如 `--max-old-space-size=4096`
	- 注意：如果您使用的是远程连接（例如 WSL、Remote SSH、DevContainer 等），并且不想修改整个工作区的设置，那么您需要通过命令面板运行“偏好设置：打开远程设置（JSON 格式）”命令。在设置面板中配置所需的选项，然后重新加载编辑器，以确保 Linter 服务器能够应用这些更改。
- `eslint.nodeEnv` – 如果某个 ESLint 插件或配置需要定义 `process.env.NODE_ENV` ，则使用此设置。
- `eslint.nodePath` – 如果检测不到已安装的 ESLint 插件，可以使用此设置，例如 `/myGlobalNodePackages/node_modules` 。
- `eslint.probe` - 这是一个用于标识语言的数组，需要激活 ESLint 扩展功能来尝试对文件进行验证。如果针对这些语言进行验证失败，扩展会显示“无操作”的提示。默认值为 `["astro", "civet", "javascript", "javascriptreact", "typescript", "typescriptreact", "html", "mdx", "vue", "markdown", "json", "jsonc"]` 。
- `eslint.validate` ——这是一个语言标识符数组，用于指定需要执行验证的文件。如果仅指定了这些文件，那么只有这些文件才会被验证。这相当于 `--ext` 命令行选项的功能。默认值为 `null` 。
- `eslint.format.enable` ：启用 ESLint 作为已验证文件的格式化工具。虽然也可以使用 `editor.formatOnSave` 设置在保存时进行格式化，但建议使用 `editor.codeActionsOnSave` 功能，因为它能提供更灵活的配置选项。
- `eslint.workingDirectories` - 指定了 ESLint 用于计算工作目录的方式。ESLint 会相对于工作目录来解析配置文件（例如 `eslintrc` 、 `.eslintignore` ），因此正确配置这一参数非常重要。如果要在终端中执行 ESLint 时，需要将工作目录切换到子文件夹，那么通常需要调整这个设置。（参见 ESLint 类选项#cwd）。另外，请注意 `.eslintrc*` 文件是相对于父目录来解析的，而 `.eslintignore` 文件仅在当前工作目录中生效。可以使用以下值：
	- `[{ "mode": "location" }]` (@since 2.0.0)：此选项指示 ESLint 使用工作区文件夹的路径或文件所在的路径作为当前工作目录。这是默认设置，与 ESLint 扩展程序的旧版本（1.9.x 系列）使用的策略相同。
		- `[{ "mode": "auto" }]` （自 2.0.0 版本起）：指示 ESLint 根据 `package.json` 、 `eslint.config.js` 、 `.eslintignore` 和 `.eslintrc*` 文件的路径来推断当前的工作目录。这种方法在许多情况下都是有效的，但也可能会导致意外的结果。
		- `string[]` ：这是一个用于存放工作目录的数组。可以考虑使用如下的目录结构：
		```markdown
		root/
		  client/
		    .eslintrc.json
		    client.js
		  server/
		    .eslintignore
		    .eslintrc.json
		    server.js
		```
		然后使用这个设置：
		```javascript
		"eslint.workingDirectories": [ "./client", "./server" ]
		```
		该工具会将服务器目录中的文件与服务器目录本身作为 ESLint 工作目录进行格式化检查。客户端目录中的文件也会遵循同样的处理方式。此外，ESLint 扩展模块还会将进程的工作目录设置为所提供的目录路径。如果不需要这种效果，可以使用带 `!cwd` 属性的字面量来表示（例如 `{ "directory": "./client", "!cwd": true }` ）。这样就能让客户端目录作为 ESLint 的工作目录，而不会改变进程本身的工作目录。
		- `[{ "pattern": glob pattern }]` （自 2.0.0 版本起）：允许指定用于检测工作目录的模式。这实际上是一种快速列出所有目录的方法。如果你有一个包含多个项目的单一仓库，且所有项目都位于一个名为“packages”的文件夹下，那么可以使用 `{ "pattern": "./packages/*/" }` 来将这些文件夹设置为工作目录。
- `eslint.codeAction.disableRuleComment` – 具有以下属性的对象：
	- `enable` – 在快速修复菜单中禁用代码检查规则。 `true` 默认情况下如此设置。
		- `location` - 可以选择在 `separateLine` 或 `sameLine` 上添加 `eslint-disable` 评论。 `separateLine` 是默认选项。例如：
		```json
		{ "enable": true, "location": "sameLine" }
		```
- `eslint.codeAction.showDocumentation` – 具有以下属性的对象：
	- `enable` – 在快速修复菜单中显示有关开放 Lint 规则的文档页面。默认情况下， `true` 会显示该内容。
- `eslint.codeActionsOnSave.mode` (@从 2.0.12 版本开始) – 用于控制在执行代码动作时，哪些问题会被修复。
	- `all` ：通过重新验证文件的内容来解决所有可能的问题。这一操作执行的代码与在终端中使用 `--fix` 选项运行 eslint 相同，因此可能会花费一些时间。这是默认值。
		- `problems` ：这种模式只修复那些目前已知且可解决的漏洞，前提是这些漏洞的文本描述不会冲突。这种方式的速度会快很多，但很可能只能解决部分问题。
	请注意，如果 `eslint.codeActionsOnSave.mode` 被设置为 `problems` ，那么 `eslint.codeActionsOnSave.rules` 将被忽略。
- `eslint.codeActionsOnSave.rules` (@从 2.2.0 版本开始) - 用于控制在执行代码保存操作时所考虑的规则。如果未指定此选项，则会考虑通过常规 ESLint 配置机制指定的所有规则。如果数组为空，则表示不会考虑任何规则。如果数组中包含多个条目，那么它们的顺序很重要，第一个匹配的规则将决定该规则的启用或禁用状态。只有在以下情况下才会执行此设置：
	- `eslint.codeActionsOnSave.mode` 的值与 `problems 的值不同。`
		- 当前使用的 ESLint 版本为 8 版或更高版本；或者版本为 7.x 版，且设置 `eslint.useESLintClass` 被设置为 true（版本大于等于 8 版，或者版本为 7.x 版且 eslint.useESLintClass 被设置为 true）。
	在这个示例中，我们只考虑了与分号相关的规则：
	```json
	"eslint.codeActionsOnSave.rules": [
	  "*semi*"
	]
	```
	这个示例在保存时从代码操作中移除了所有与 TypeScript ESLint 相关的规则，同时保留了其他所有规则：
	```json
	"eslint.codeActionsOnSave.rules": [
	  "!@typescript-eslint/*",
	  "*"
	]
	```
	这个示例保留了 TypeScript ESLint 中的缩进和半角字符规则，同时禁用所有其他 TypeScript ESLint 规则，而保留了其余的规则：
	```json
	"eslint.codeActionsOnSave.rules": [
	    "@typescript-eslint/semi",
	    "@typescript-eslint/indent",
	    "!@typescript-eslint/*",
	    "*"
	]
	```
- `eslint.rules.customizations` (@since 2.1.20) - 强制在 VS Code 中使用的规则报告的严重性与项目实际的 ESLint 配置不一致。包含以下属性：
	- `"rule` ：根据名称匹配的规则来选择元素，其中星号表示通配符： `{ "rule": "no-*", "severity": "warn" }`
		- 在名称前加上 `"!"` 前缀，这样可以匹配所有与名称不匹配的规则： `{ "rule": "!no-*", "severity": "info" }`
		- `"severity"` ：为匹配的规则设置新的严重性等级。 `"downgrade"` ：将它们调整为较低的严重性等级； `"upgrade"` ：将它们调整为较高的严重性等级； `"default"` ：将它们恢复至原来的严重性等级。
		- `"fixable"` ：只选择那些可以自动修复的规则： `{ "rule": "no-*", "fixable": true, "severity": "info" }`
	在这个示例中，所有的规则都被修改为警告级别：
	```json
	"eslint.rules.customizations": [
	  { "rule": "*", "severity": "warn" }
	]
	```
	在这个示例中， `no-` 的规则属于信息性规则，其他规则被降级处理，而 `"radix"` 则恢复为默认设置。
	```json
	"eslint.rules.customizations": [
	  { "rule": "no-*", "severity": "info" },
	  { "rule": "!no-*", "severity": "downgrade" },
	  { "rule": "radix", "severity": "default" }
	]
	```
	在这个示例中，所有可以自动修复的规则都被覆盖，转而执行信息相关的处理。
	```json
	"eslint.rules.customizations": [
	  { "rule": "*", "fixable": true, "severity": "info" }
	]
	```
- `eslint.bulkSuppression.enable` （自 3.0.26 版本起）– 启用 ESLint 的批量代码检查功能。更多配置选项请参考 `eslint.bulkSuppression.location` 和 `eslint.bulkSuppression.severity` 。
- `eslint.onIgnoredFiles` （自 2.0.10 版本起生效）：用于控制在处理被忽略文件的时是否需要生成警告。默认值为 `off` 。可以设置为 `warn` 。
- `editor.codeActionsOnSave` （自 2.0.0 版本起生效）：此设置现在支持 `source.fixAll.eslint` 这样的条目。如果设置为 true，那么在保存时，所有来自所有插件的 ESLint 错误都会被修复。你还可以使用 VS Code 的语言范围设置来选择性地启用或禁用特定语言的支持。如果要禁用 `codeActionsOnSave` 对于 HTML 文件的支持，可以使用以下设置：
	```json
	"[html]": {
	  "editor.codeActionsOnSave": {
	    "source.fixAll.eslint": false
	  }
	}
	```
	旧的 `eslint.autoFixOnSave` 设置已经过时了，可以安全地将其移除。请注意，如果您使用 ESLint 作为默认格式化工具，那么在启用 `editor.codeActionsOnSave` 的同时，也应该关闭 `editor.formatOnSave` 。否则，您的代码会被重复处理两次，这是不必要的操作。
- `eslint.problems.shortenToSingleLine`: (自 2.3.0 版本起) – 将下划线的问题文本范围缩短到仅包含与其相关的一行内容。
- `eslint.experimental.useFlatConfig` ：（自 2.3.0 版本起）– 支持实验性的扁平化配置格式（也称为 eslint.config.js 格式），该格式在 ESLint 8.21 或更高版本中得到了支持。
- `eslint.timeBudget.onValidation` （自 2.3.5 版本起）用于控制在显示警告或错误之前可用于验证的时间预算。
- `eslint.timeBudget.onFixes` （自 2.3.5 版本起）用于控制在计算修复方案之前可以使用的计算时间预算，以避免在出现警告或错误时继续操作。

## 设置迁移

如果设置为 true，ESLint 会提示你将旧格式 `eslint.autoFixOnSave` 转换为新格式 `editor.codeActionsOnSave` 。如果你不想进行迁移，可以在对话框中以以下方式回应：

- 现在不行：这个环境不会被迁移。下次你再次打开工作区时，ESLint 就不会提示进行迁移了。
- 禁止迁移设置：通过将用户设置 `eslint.migration.2_x` 更改为 `off ，可以禁用设置的迁移功能。`

这个迁移操作可以随时通过命令 `ESLint: Migrate Settings 来手动触发。`

## 命令：

这个扩展为命令面板增加了以下命令。

- `Create '.eslintrc.json' file` ：创建一个新的 `.eslintrc.json` 文件。
- `Fix all auto-fixable problems` ：对所有可修复的问题都应用 ESLint 的自动修复功能进行优化。

## 使用与 VS Code 的任务运行功能相结合的扩展功能。

该扩展功能仅在输入特定文件时才会对文件进行语法检查。如果您想对整个工作区进行语法检查，可以设置 `eslint.lintTask.enable` 到 `true` 范围内的文件进行检查，同时扩展功能还会自动处理 `eslint: lint whole folder` 任务。因此，无需在 `tasks.json` 中再定义任何自定义任务了。

## 使用 ESLint 来验证 TypeScript 文件的正确性

在 TypeScript - ESLint 文档中，有关于如何使用 ESlint 来检查 TypeScript 代码的详细介绍。在在使用 VS Code 的 ESLint 扩展进行 TypeScript 开发之前，建议先熟悉一下这部分内容。特别是要确保能够使用 `eslint` 命令在终端中成功验证 TypeScript 文件的正确性。

这个项目本身就使用了 ESLint 来验证其 TypeScript 文件的正确性。因此，它可以作为一个入门模板来使用。

为了避免受到任何 TSLint 版本的影响，建议使用 `"tslint.enable": false` 来禁用 TSLint。

### 单一存储库设置

在单仓库环境中对 TypeScript 进行 JavaScript 验证时，需要告诉 VS Code 的 ESLint 扩展当前的工作目录信息。可以使用 `eslint.workingDirectories` 设置来实现这一点。对于这个仓库来说，工作目录的配置如下：

```json
"eslint.workingDirectories": [ "./client", "./server" ]
```

## ESLint 6.x

从 ESLint 5.x 升级到 ESLint 6.x 可能需要做一些调整（详情请参阅 ESLint 升级指南）。在提交关于 VS Code ESLint 扩展的问题之前，请确保能够使用\`eslint\`命令在终端中成功验证您的文件。