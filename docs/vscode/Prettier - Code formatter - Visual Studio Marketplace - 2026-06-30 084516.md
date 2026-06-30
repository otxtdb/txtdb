---
title: "Prettier - Code formatter - Visual Studio Marketplace"
source: "https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode"
author:
published:
created: 2026-06-30
description: "Extension for Visual Studio Code - Code formatter using prettier"
tags:
  - "clippings"
taxonomy: { doc_category: [vscode] }
---
## Prettier 代码格式化工具（Visual Studio Code）

Prettier 是一款自带严格规范的代码格式化工具。它通过解析您的代码，并依据其内置规则（充分考虑最大行长度限制）进行重新格式化，在必要时自动换行，从而强制执行一致的代码风格。

*JavaScript · TypeScript · Flow · JSX · JSON*  
*CSS · SCSS · Less*   
*HTML · Vue · Angular* *HANDLEBARS · Ember · Glimmer*  
*GraphQL · Markdown · YAML*  
*[你最喜欢的语言？](https://prettier.io/docs/en/plugins.html)*

## 安装

通过 VS Code 扩展安装。搜索 `Prettier - Code formatter`

[Visual Studio Code 扩展商店：Prettier - 代码格式化程序](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)

也可以在 VS Code 中安装：按下 Ctrl+P 打开“快速打开”面板，粘贴以下命令并按回车键。

```markdown
ext install esbenp.prettier-vscode
```

### 默认格式化程序

为确保优先使用该扩展而非您已安装的其他扩展，请务必在 VS Code 设置中将其设为默认格式化程序。您可以针对所有语言统一配置，也可以为特定语言单独设置。

```json
{
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  }
}
```

注意：VS Code 不支持针对 `editor.defaultFormatter` 的组合语言语法。您必须为每种语言分别设置格式化工具：

```json
// ❌ This will NOT work
{
  "[javascript][typescript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  }
}

// ✅ Use separate blocks instead
{
  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[typescript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  }
}
```

若要在特定语言中禁用 Prettier，您可以创建 `.prettierignore` 文件，或者使用 VS Code 的 `editor.defaultFormatter` 设置。

以下配置将对除 JavaScript 之外的所有语言启用 Prettier。

```json
{
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "[javascript]": {
    "editor.defaultFormatter": "<another formatter>"
  }
}
```

以下内容将仅针对 JavaScript 使用 Prettier。

```json
{
  "editor.defaultFormatter": "<another formatter>",
  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  }
}
```

此外，如果您不希望特定语言被自动格式化，可以为这些语言禁用保存时格式化的功能。

```json
{
  "[javascript]": {
    "editor.formatOnSave": false
  }
}
```

### Prettier 解析 

此扩展将使用您项目本地依赖中的 Prettier（推荐）。当 `prettier.resolveGlobalModules` 设置为 `true` 时，该扩展也会尝试解析全局模块。若未在项目依赖中本地安装 Prettier，也未在机器上全局安装，则将使用扩展内置的 Prettier 版本。

按照推荐方式在您的项目中安装 Prettier 并锁定其版本，请运行：

```markdown
npm install prettier -D --save-exact
```

> 注意：系统会提示您确认是否允许扩展加载 Prettier 模块。此举旨在确保您不会加载任何不受信任的模块或脚本。

### Prettier 版本 

本扩展默认内置了 Prettier 3.x。如果您的项目在 `node_modules` 处本地安装了 Prettier，则系统将优先使用该版本而非内置版本。这使得您能够在项目中指定并使用特定版本的 Prettier。

Prettier 2.x 兼容性：使用 Prettier 2.x 的项目仍完全受支持。若您的项目已本地安装 Prettier 2.x，扩展将自动使用该版本。

### 插件

当您在项目中使用本地或全局安装的 Prettier 版本时，本扩展支持加载 Prettier 插件。若您的 `package.json` 中已配置 Prettier 及插件，本扩展将尝试注册相应语言支持，并为内置和插件所涵盖的语言提供自动代码格式化功能。

## 配置 

使用此扩展配置 Prettier 有多种选项。您可以使用 VS Code 设置、Prettier 配置文件或 `.editorconfig` 文件。VS Code 设置通常作为后备方案，一般仅建议用于非项目文件。建议在项目中始终包含一个 Prettier 配置文件，以指定该项目的所有设置。这样可以确保无论您如何运行 Prettier——是通过此扩展、命令行（CLI）还是其他集成了 Prettier 的 IDE——都会应用相同的设置。

使用 Prettier 配置文件来设置格式化选项是推荐的做法。配置项会从正在格式化的文件开始向下递归查找，因此如果您希望将 Prettier 设置应用于整个项目，只需在根目录中设置一个配置文件即可。您也可以通过 VS Code 进行设置——不过，这些设置仅在运行扩展时生效，通过命令行运行 Prettier 时则不会应用。

### 配置默认选项

部分用户可能不想为每个项目单独创建 Prettier 配置文件，也不愿使用 VS Code 的设置。若要设置默认配置，请将 [`prettier.configPath`](https://github.com/prettier/prettier-vscode#prettierconfigpath) 设为相应值。但请注意，一旦设置该选项，此值将始终生效，且本地配置文件将被忽略。

### Visual Studio Code 设置 

您可以使用 VS Code 设置来配置 Prettier。设置将从以下位置读取（按优先级列出）：

1. [Prettier 配置文件](https://prettier.io/docs/en/configuration.html)
2. `.editorconfig`
3. Visual Studio Code 设置（若存在其他配置，则此项将被忽略）

> 注意：若已存在任何本地配置文件（即 `.prettierrc` ），将不会使用 VS Code 的设置。

## 用法 

### 使用命令面板（CMD/CTRL + Shift + P）

```markdown
1. CMD + Shift + P -> Format Document
OR
1. Select the text you want to Prettify
2. CMD + Shift + P -> Format Selection
```

### 键盘快捷键

Visual Studio Code 为代码格式化提供了默认的键盘快捷键。您可以在 VS Code 文档中查阅各平台的具体说明。

如果您不喜欢默认设置，可以在 vscode 的键盘快捷键菜单中重新绑定 `editor.action.formatDocument` 和 `editor.action.formatSelection` 。

### 保存时格式化

遵循 `editor.formatOnSave` 设置。

您可以通过为设置指定语言作用域，按语言单独开启“保存时格式化”功能：

```json
// Set the default
"editor.formatOnSave": false,
// Enable per-language
"[javascript]": {
    "editor.formatOnSave": true
}
```

### 格式选择

格式选择功能适用于多种语言，具体取决于 Prettier 本身所支持的语言。目前支持以下语言：

```markdown
javascript
javascriptreact
typescript
typescriptreact
json
graphql
handlebars
```

### 格式化文档（强制）

如果您希望格式化被 Prettier 配置为忽略的文档（无论是因为它位于 `.prettierignore` 文件中，还是属于通常被排除的路径如 `node_modules` ），您可以运行“格式化文档（强制）”命令来强制执行格式化。该强制模式还会忽略针对 `requirePragma` 的任何配置，从而允许您格式化缺少 pragma 注释的文件。

## Linter 集成 

与 Linter 集成的推荐做法是让 Prettier 负责代码格式化，并将 Linter 配置为不处理格式化相关规则。有关如何配置各款 Linter 的具体说明，请参阅 Prettier 官方文档网站。之后，你就可以照常使用各项代码检查（Lint）插件了。更多详情请参阅 Prettier 官方文档。

### 使用保存时代码操作

你可以利用 VS Code 的 `editor.codeActionsOnSave` 功能，在 ESLint 等其他格式化工具之前优先运行 Prettier。如果你希望先由 Prettier 进行格式化，再执行 ESLint 的代码修复，该设置将非常有用。

```markdown
// .vscode/settings.json
{
  "editor.codeActionsOnSave": {
    "source.fixAll.prettier": "explicit",
  },
}
```

你还可以将 Prettier 与 ESLint 配合使用：

```markdown
// .vscode/settings.json
{
  "editor.codeActionsOnSave": {
    "source.fixAll.prettier": "explicit",
    "source.fixAll.eslint": "explicit",
  },
}
```

> 注意： `source.fixAll.prettier` 代码操作会遵循您的 `editor.defaultFormatter` 设置。如果您设置了不同的默认格式化工具（例如带有 Prettier 插件的 ESLint），除非您通过 `"source.fixAll.prettier": "explicit"` 或 `"source.fixAll.prettier": "always"` 显式启用它，否则 Prettier 代码操作将不会运行。这可以防止在使用如 `eslint-plugin-prettier` 之类的配置时出现双重格式化问题。

## 工作区信任

此扩展使用 VS Code 的工作区信任功能。当在不受信任的工作区中运行此扩展时，它将仅使用内置版本的 Prettier。不支持任何插件、本地或全局模块。此外，部分设置也会受到限制——详细信息请参阅各项设置的说明。

## 设置 

### Prettier 设置 

所有 Prettier 选项均可在此扩展中直接配置。当项目中不存在配置文件时，这些设置将作为后备值生效；更多详情请参阅本文档的配置章节。有关各选项的说明，请参阅 Prettier 官方文档。

> 这些配置的默认值与 Prettier 3.0 保持一致。相较于 Prettier 2.x 的显著变更： `trailingComma` 现在默认为 `"all"` ，而非 `"es5"` 。

```markdown
prettier.arrowParens
prettier.bracketSpacing
prettier.endOfLine
prettier.htmlWhitespaceSensitivity
prettier.insertPragma
prettier.singleAttributePerLine
prettier.bracketSameLine
prettier.jsxBracketSameLine
prettier.jsxSingleQuote
prettier.printWidth
prettier.proseWrap
prettier.quoteProps
prettier.requirePragma
prettier.semi
prettier.singleQuote
prettier.tabWidth
prettier.trailingComma
prettier.useTabs
prettier.vueIndentScriptAndStyle
prettier.embeddedLanguageFormatting
prettier.experimentalTernaries
prettier.objectWrap
prettier.experimentalOperatorPosition
```

#### 语言特定格式化

上述所有 Prettier 选项均支持语言特定的覆盖设置。这使您能够直接在 VS Code 设置中为不同文件类型配置不同的格式化规则，且这些设置可轻松跨设备与环境同步。

要在您的 VS Code `settings.json` 中使用 `[language]` 语法：

```json
{
  "[html]": {
    "prettier.printWidth": 180
  },
  "[typescript]": {
    "prettier.printWidth": 120,
    "prettier.tabWidth": 4,
    "prettier.semi": false
  },
  "[json]": {
    "prettier.printWidth": 80,
    "prettier.tabWidth": 2
  }
}
```

在处理多语言项目或不同语言遵循不同格式化规范时，此功能尤为实用。当格式化特定语言的文件时，针对该语言的设置将会覆盖全局的 Prettier 配置。

### 扩展设置

这些设置仅适用于 VS Code，需在 VS Code 的设置文件中进行配置。有关具体操作，请参阅相关文档。

#### prettier.enable（默认值： true ） 

控制是否启用 Prettier。更改此设置后，必须重启 VS Code。

#### prettier.requireConfig（默认值： false ） 

要求提供 Prettier 配置文件以格式化文件。即使将此选项设置为 `true` ，未命名文件仍会使用 VS Code 的 Prettier 配置进行格式化。

#### prettier.ignorePath（默认值：.prettierignore ） 

指定忽略文件的路径，例如 `.gitignore` 或 `.prettierignore` 。匹配的文件将不会被格式化。设置为 `null` 可禁止读取忽略文件。

**注意：若已设置此项，系统将始终使用该值，并忽略本地忽略文件。**

**在未受信任的工作区中禁用**

#### prettier.configPath 

指定自定义的 Prettier 配置文件路径。

**注意，若已设置此项，系统将始终使用该值并忽略本地配置文件。若要设置全局默认值，更推荐的做法是在主目录中放置一个 `~/.prettierrc` 文件。**

**在未受信任的工作区中禁用**

#### prettier.prettierPath 

指定 Prettier 模块的自定义路径。该路径应指向模块文件夹，而非 bin/脚本路径。即 `./node_modules/prettier` ，而不是 `./bin/prettier` 。

**在不受信任的工作区中禁用**

#### prettier.resolveGlobalModules (默认值： false ) 

启用后，若无法解析本地模块，该扩展将尝试使用全局的 npm 或 yarn 模块。

> 注意：此设置可能会对性能产生负面影响，特别是在 Windows 系统上且已挂载网络驱动器时。仅在必须使用全局模块时才启用此项。建议尽可能始终使用本地模块。

**注意：禁用父文件夹中已启用的语言将阻止格式化操作，而不会交由其他任何格式化器运行。**

**在未受信任的工作区中将禁用**

#### prettier.documentSelectors 

用于注册 Prettier 格式化程序的 Glob 模式列表。通常这些模式的格式为 `**/*.abc` ，用于告知该扩展程序将自己注册为所有具有 `abc` 扩展名文件的格式化程序。当您在配置文件中设置了覆盖规则以将自定义文件扩展名映射到指定解析器时，此功能将十分有用。

您可能还需要更新 Prettier 的配置。例如，如果仅单独注册以下文档选择器，Prettier 依然不知道该如何处理该文件。我需要一个能够格式化 `.abc` 文件格式的 Prettier 扩展，或者需要配置 Prettier。

```json
{
  "prettier.documentSelectors": ["**/*.abc"]
}
```

若要告知 Prettier 如何格式化 `.abc` 类型的文件，我可以在 prettier 配置中设置一项覆盖规则，使该文件类型使用 `babel` 解析器。

```json
{
  "overrides": [
    {
      "files": "*.abc",
      "options": {
        "parser": "babel"
      }
    }
  ]
}
```

**在未受信任的工作区中禁用**

#### prettier.useEditorConfig（默认值： true ） 

是否在解析配置时将.editorconfig 纳入考量。详情请参阅 prettier.resolveConfig 文档。

**在未受信任的工作区中禁用（始终为 false）**

#### prettier.withNodeModules（默认值： false ） 

是否处理 `node_modules` 文件夹中的文件。

**在未受信任的工作区中禁用**

## 疑难解答

请参阅《疑难解答指南》以获取以下常见问题的帮助：

- Prettier 无法格式化文件
- 格式化结果不符合预期
- 性能问题
- 插件问题
- 配置问题

### 常见错误信息

**模块加载失败。如果您的 package.json 中引用了 Prettier 或插件，请确保您已运行 `npm install`**

当您的项目中存在 `package.json` 且其中包含 Prettier、插件或 linter 库时，该扩展将尝试从您的 `node_module` 文件夹加载这些模块。如果看到此错误，通常意味着您需要运行 `npm install` 、 `yarn install` 、 `pnpm install` 等命令来安装 `package.json` 中的依赖包。

**您的项目配置为使用旧版本的 Prettier，此扩展无法使用该版本。请升级到最新版本的 Prettier。**

您必须升级到更新版本的 Prettier。

**此工作区不受信任。正在使用内置的 Prettier 版本。**

必须信任此工作区才能使用插件和本地/全局模块。参见：工作区信任