---
title: "Prettier - Code formatter - Visual Studio Marketplace"
source: "https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode"
author:
published:
created: 2026-08-26
description: "Extension for Visual Studio Code - Code formatter using prettier"
tags:
  - "clippings"
taxonomy: { doc_category: [vscode] }
---
[跳转至内容部分](#start-of-content)

## 更美观——代码格式工具

## 更漂亮了

[更漂亮点吧.io](https://prettier.io/)

|

71,082,743 次安装次数

| (492) | 免费

|

使用 \`prettier\` 进行代码格式化工具

## 更美观的 Visual Studio Code 格式化工具

Prettier 是一种具有自己风格的代码格式化工具。它通过解析你的代码，并根据自己的规则来重新格式化代码。这些规则考虑了每行代码的最大长度，并在必要时对代码进行换行处理，从而确保代码风格的一致性。

*JavaScript · TypeScript · Flow · JSX · JSON*  
*CSS · SCSS · Less*  
HTML · Vue · Angular 操作栏 · Ember · Glimmer  
*GraphQL · Markdown · YAML*  
*[你最喜欢的编程语言是什么？](https://prettier.io/docs/en/plugins.html)*

## 安装

通过 VS Code 扩展进行安装。搜索 `Prettier - Code formatter`

[Visual Studio Code 市场平台：Prettier——代码格式化工具](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)

也可以在 VS Code 中安装：启动 VS Code 的快速打开功能（Ctrl+P），粘贴以下命令，然后按回车键即可。

```markdown
ext install esbenp.prettier-vscode
```

### 默认格式器

为了确保这个扩展能够在你已安装的其他扩展中正常使用，请务必在 VS Code 的设置中将其设置为默认格式器。这个设置可以针对所有语言进行设置，也可以针对特定语言进行设置。

```json
{
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  }
}
```

注意：VS Code 不支持 `editor.defaultFormatter` 这种混合语言语法的格式设置。必须分别为每种语言单独设置格式化工具。

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

如果您想要禁用某种语言的 Prettier 功能，可以创建一份 `.prettierignore` 文件，或者使用 VS Code 的 `editor.defaultFormatter` 设置功能来实现这一目的。

以下代码将使用 Prettier 来处理除 JavaScript 之外的所有语言。

```json
{
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "[javascript]": {
    "editor.defaultFormatter": "<another formatter>"
  }
}
```

以下代码将仅使用 Prettier 来处理 JavaScript 代码。

```json
{
  "editor.defaultFormatter": "<another formatter>",
  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  }
}
```

此外，如果你不希望某些语言在保存时自动进行格式处理，你可以禁用这些语言的保存格式功能。

```json
{
  "[javascript]": {
    "editor.formatOnSave": false
  }
}
```

### 更美观的解决方案

此扩展模块会从项目的本地依赖项中引入 prettier 模块（建议如此）。当 `prettier.resolveGlobalModules` 被设置为 `true` 时，该扩展模块还会尝试解析全局模块。如果项目中的依赖库并未在本地安装 prettier 模块，或者机器上并没有预装该模块，那么将会使用随扩展模块一起提供的 prettier 版本。

要在你的项目中安装 prettier，并按照推荐的方式固定其版本，请执行以下操作：

```markdown
npm install prettier -D --save-exact
```

> 注意：系统会提示您确认是否希望该扩展加载 Prettier 模块。这样做是为了确保您不会加载不安全的模块或脚本。

### 更漂亮的版本

该扩展默认会引入 Prettier 3.x 版本。如果您项目的本地环境中已安装了 Prettier，那么将会使用该版本，而不是随扩展一起提供的版本。这样您可以在项目中使用特定版本的 Prettier。

兼容于 Prettier 2.x 版本：使用 Prettier 2.x 版本的项目仍然会得到完全的支持。如果你的项目已经本地安装了 Prettier 2.x 版本，那么插件会自动使用该版本。

### 插件

当使用本地或全局解析的 Prettier 版本时，这个扩展支持 Prettier 插件的使用。如果你已经安装了 Prettier，并且注册了相关插件，那么这个扩展会尝试识别语言类型，并为内置语言及插件语言提供自动代码格式化功能。

## 配置

使用这个扩展来配置 Prettier 有多种选项。你可以使用 VS Code 的设置、Prettier 配置文件，或者 `.editorconfig` 文件来进行配置。VS Code 的设置被设计为备选方案，通常只适用于非项目级别的文件。建议在你的项目中始终包含一个 Prettier 配置文件，从而指定所有相关设置。这样，无论你是通过这个扩展、命令行工具，还是其他支持 Prettier 的 IDE 来运行 Prettier，都会应用相同的设置。

使用 Prettier 配置文件来设置格式选项是一种推荐的方法。这些选项会从被格式化的文件开始递归搜索。因此，如果你希望将 Prettier 的设置应用到整个项目上，只需在根目录中设置一次配置即可。这些设置也可以通过 VS Code 进行配置——不过，这些设置仅会在运行扩展时生效，而不是在通过命令行运行 Prettier 时生效。

### 配置默认选项

一些用户可能不希望为每个项目都创建新的 Prettier 配置，或者不想使用 VS Code 的设置。为了设置默认配置，可以设置 [`prettier.configPath`](https://github.com/prettier/prettier-vscode#prettierconfigpath) 。不过请注意，如果设置了此值，那么它将一直被使用，而本地配置文件将被忽略。

### Visual Studio Code 设置

你可以使用 VS Code 的设置来配置 Prettier 的功能。这些设置将从中读取，并按照优先级顺序排列。

1. [更美观的配置文件](https://prettier.io/docs/en/configuration.html)
2. `.editorconfig`
3. Visual Studio Code 设置（如果存在其他配置，则这些设置会被忽略）

> 注意：如果存在任何本地配置文件（例如 `.prettierrc` ），那么 VS Code 的设置将不会被使用。

## 使用方式

### 使用命令面板（CMD/CTRL + Shift + P）

```markdown
1. CMD + Shift + P -> Format Document
OR
1. Select the text you want to Prettify
2. CMD + Shift + P -> Format Selection
```

### 键盘快捷键

如果你不喜欢当前的默认设置，可以在 VSCode 的快捷键菜单中重新绑定 `editor.action.formatDocument` 和 `editor.action.formatSelection` 这两个键。

### 保存格式

尊重 `editor.formatOnSave` 的设置。

你可以针对每种语言分别启用“保存格式”功能，具体方法은设置该选项即可。

```json
// Set the default
"editor.formatOnSave": false,
// Enable per-language
"[javascript]": {
    "editor.formatOnSave": true
}
```

### 格式选择

格式选择功能支持多种语言，具体取决于 Prettier 本身的支持范围。目前支持的语言包括：

```markdown
javascript
javascriptreact
typescript
typescriptreact
json
graphql
handlebars
```

### 格式化文档（强制方式）

如果您希望将一个被 Prettier 忽略的文档进行格式化，无论该文档位于 `.prettierignore` 文件中，还是属于类似 `node_modules` 这样的特殊位置，都可以运行“Format Document（强制模式）”命令来强制对文档进行格式化。在强制模式下，还会忽略 `requirePragma` 中的任何配置说明，从而可以在没有参数注释的情况下对文档进行格式化。

## Linter 集成

推荐的方式是将代码格式化功能交给 Prettier 来处理，同时配置好 linter 不要处理格式规则相关的工作。你可以在 Prettier 的文档网站上找到关于如何配置各个 linter 的说明。之后，你可以像平常一样使用这些代码检查扩展功能。更多详细信息请参考 Prettier 的文档。

### 在保存时使用代码动作功能

你可以使用 VS Code 的 `editor.codeActionsOnSave` 功能在运行其他格式化工具之前先使用 Prettier 进行代码格式化。当你想先使用 Prettier 进行格式化，然后再应用 ESLint 的修正时，这个功能非常有用。

```markdown
// .vscode/settings.json
{
  "editor.codeActionsOnSave": {
    "source.fixAll.prettier": "explicit",
  },
}
```

你还可以将 Prettier 与 ESLint 结合使用：

```markdown
// .vscode/settings.json
{
  "editor.codeActionsOnSave": {
    "source.fixAll.prettier": "explicit",
    "source.fixAll.eslint": "explicit",
  },
}
```

> 注意： `source.fixAll.prettier` 代码操作会遵循您的 `editor.defaultFormatter` 设置。如果您设置了不同的默认格式化工具（例如，使用 ESLint 并结合 Prettier 插件），那么除非您明确使用 `"source.fixAll.prettier": "explicit"` 或 `"source.fixAll.prettier": "always"` 来启用该功能，否则 Prettier 代码操作将无法运行。这样就能避免在使用如 `eslint-plugin-prettier` 这样的设置时出现重复格式化的情况。

## 工作区信任机制

该扩展利用了 VS Code 的工作空间信任功能。当该扩展在不受信任的工作空间中使用时，它将只使用内置的 Prettier 版本。该扩展不支持任何插件、本地模块或全局模块。此外，某些设置也被限制使用——具体细节请参阅各设置项说明。

## 设置

### 更漂亮的设置

所有更漂亮的格式化选项都可以直接通过此扩展程序进行配置。当项目中没有配置文件时，这些设置将作为备选方案使用。更多详细信息请参阅本文档的配置部分。有关选项的参考说明，请参考 prettier 的文档。

> 这些配置的默认值与 Prettier 3.0 的默认设置相匹配。与 Prettier 2.x 相比，有一个显著的变化：现在默认使用的函数式表达式是 `"all"` ，而不是 `"es5"` 。

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

#### 语言特定的格式设置

上述所有“更美观”的选项都支持针对特定语言的自定义设置。这意味着你可以在 VS Code 的设置中为不同类型的文件设置不同的格式规则，而这些设置可以轻松地在不同的机器和环境之间同步。

要配置特定语言的设置，请在 VS Code 的 `settings.json` 中使用 `[language]` 语法：

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

当处理多语言项目，或者当不同语言具有不同的格式规范时，这个功能非常有用。针对特定语言的设置会在格式化该语言类型的文件时覆盖全局的 Prettier 设置。

### 扩展设置

这些设置是专用于 VS Code 的，需要在 VS Code 的设置文件中进行配置。有关如何操作的详细说明，请参考相关文档。

#### prettier.enable (默认值为 true )

该设置决定了“prettier”功能是否启用。当更改此设置后，必须重新启动 VS Code 才能生效。

#### prettier.requireConfig（默认值为 false ）

需要一个更美观的配置文件来格式化文件。即使将此选项设置为 `true` ，没有标题的文件仍然会使用 VS Code Prettier 进行格式化。

#### 更美观的.prettier.ignorePath 选项（默认值为.prettierignore ）

提供指向一个忽略文件的路径，例如 `.gitignore` 或 `.prettierignore` 。与这些文件匹配的内容将不会被处理。如果设置为 `null` ，则不会读取这些忽略文件。

**请注意，如果设置了此选项，那么将始终使用这个值，而本地忽略的文件将被完全忽略。**

**无法在不可信的工作环境中进行操作**

#### prettier.configPath

为配置文件提供一个更美观的自定义路径。

**请注意，如果设置了此选项，那么将始终使用这个值，而本地配置文件将被忽略。对于全局默认值的设置，更好的方式是在个人目录中创建一个 `~/.prettierrc` 文件。**

**无法在不可信的工作环境中进行操作**

#### 更美观的样式。更美观的路径。

为那个更美观的模块提供一个自定义的路径。这个路径应该指向模块文件夹，而不是脚本或数据文件的路径。例如，应该是 `./node_modules/prettier` ，而不是 `./bin/prettier` 。

**无法在不可信的工作环境中进行操作**

#### prettierResolveGlobalModules（默认值为 false ）

当启用此扩展功能后，如果本地模块无法被解析，系统会尝试使用全局的 npm 或 yarn 模块。

> 注意：此设置可能会对性能产生负面影响，尤其是在使用网络驱动器连接时。只有在必须使用全局模块的情况下才启用此功能。建议尽可能使用本地模块。

**注意：如果禁用父文件夹中某个语言功能，将会阻止格式化的操作，而不是让其他格式化工具运行。**

**无法在不可信的工作环境中进行操作**

#### 更漂亮的文档选择器

需要注册 Prettier 格式器的全局模式列表。这些模式的格式通常为 `**/*.abc` ，表示让该扩展程序作为所有 `abc` 扩展名的文件的格式器来运行。当你的配置文件中设置了自定义扩展名与特定解析器的映射时，这个功能就非常有用。

你可能还需要更新你的 Prettier 配置。例如，如果我只注册了以下文档选择器，Prettier 仍然不知道该如何处理该文件。要么需要有一个能够格式化 `.abc` 文件格式的 Prettier 扩展，要么就需要对 Prettier 进行配置。

```json
{
  "prettier.documentSelectors": ["**/*.abc"]
}
```

为了告诉 Prettier 如何格式化 `.abc` 类型的文件，可以在 Prettier 配置文件中设置一项覆盖选项，使得这种类型的文件能够使用 `babel` 解析器进行处理。

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

**无法在不可信的工作环境中进行操作**

#### prettier.useEditorConfig（默认值为 true）

在解析配置时，是否需要考虑.editorconfig 文件。详情请参阅 prettier.resolveConfig 的相关文档。

**在不可信的工作区中处于禁用状态（始终为 false）**

#### prettier.withNodeModules（默认值为 false）

是否对 `node_modules` 文件夹中的文件进行处理。

**无法在不可信的工作环境中进行操作**

## 故障排除

如需解决常见问题，请参阅《故障排除指南》，其中会提供相关的解决方案，包括：

- 更美观的方式是不要对文件进行格式化处理
- 意外的格式结果
- 性能问题
- 插件问题
- 配置问题

### 常见的错误信息

**加载模块失败。如果\`package.json\`文件中提到了其他更漂亮的模块或插件，请确保已经运行了 `npm install 相关的操作。`**

当你的项目中存在 `package.json` 模块，并且该模块包含了更完善的插件或 Linter 库时，这个扩展会尝试从你的 `node_module` 文件夹中加载这些模块。如果你看到这个错误，那么很可能意味着你需要运行 `npm install` 、 `yarn install` 、 `pnpm install` 等命令来安装 `package.json` 中的相关包。

**您的项目配置中使用了一个过时的版本 của prettier，而这个版本无法被此扩展程序使用。请升级到 của prettier 的最新版本。**

您必须升级到更新版本的 pretty。

**这个工作区不受信任。请使用附带的 Prettier 工具版本。**

您完全可以放心使用这个工作区，因为这里支持使用插件以及本地或全局模块。详情请参阅：工作区信任机制