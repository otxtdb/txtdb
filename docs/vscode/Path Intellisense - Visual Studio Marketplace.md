---
title: "Path Intellisense - Visual Studio Marketplace"
source: "https://marketplace.visualstudio.com/items?itemName=christian-kohler.path-intellisense"
author:
published:
created: 2026-08-26
description: "Extension for Visual Studio Code - Visual Studio Code plugin that autocompletes filenames"
tags:
  - "clippings"
taxonomy: { doc_category: [vscode] }
---
## 路径智能提示功能

一个能够自动补全文件名的 Visual Studio Code 插件。

## 安装

在命令面板中（按 Cmd+Shift+P），选择“安装扩展”，然后选择“Path Intellisense”。

若要使用“路径智能补全”功能来替代默认的自动补全功能，必须将以下配置选项添加到您的设置中：

```javascript
{ "typescript.suggest.paths": false }
{ "javascript.suggest.paths": false }
```

## 使用方式

![IDE](https://i.giphy.com/iaHeUiDeTUZuo.gif)

## 节点包：智能感知功能

使用 npm 智能提示功能

## 做出贡献/有所贡献

有什么遗漏吗？发现了错误吗？——请创建一个拉取请求或提交问题报告吧。Github

[在 Gitpod 中打开](https://gitpod.io/#https://github.com/ChristianKohler/PathIntellisense)

## 你是 Windows 系统的用户吗？

在 Windows 系统中，句点键存在问题。详情请参见该问题链接： [https://github.com/ChristianKohler/NpmIntellisense/issues/12](https://github.com/ChristianKohler/NpmIntellisense/issues/12)

将此添加到按键绑定设置中：

```javascript
{ "key": ".", "command": "" }
```

## 支持 TsConfig 配置功能

### BaseUrl

Pathintellisense 会使用 ts.config.compilerOptions.baseUrl 作为映射依据。因此，无需重复定义该值。

例如：

```markdown
# Folderstructure

src/
module-a
foo.ts
module-b
```
```javascript
// tsconfig

{
    "baseUrl": "src",
}
```

允许输入的内容如下：

```javascript
{
  import {} from "module-a/foo.ts";
}
```

你可以通过将其设置为“true”来禁用此功能。

```javascript
{
    "path-intellisense.ignoreTsConfigBaseUrl": true,
}
```

### 路径/路线

Pathintellisense 将 ts.config.compilerOptions.paths 作为映射关系来使用。

例如：

```json
{
  "compilerOptions": {
    "paths": {
      "@/*": ["src/*"]
    }
  }
}
```

注意：不支持备用方案。

## 设置

### 导入语句中的文件扩展名

在 Path Intellisense 中，如果语句是导入语句，那么默认情况下会省略文件扩展名。若要保留文件扩展名，请将以下设置设置为“true”：

```javascript
{
    "path-intellisense.extensionOnImport": true,
}
```

### 显示隐藏文件

默认情况下，隐藏文件不会显示。将此选项设置为“true”即可显示隐藏文件。

```javascript
{
    "path-intellisense.showHiddenFiles": true,
}
```

如果将该参数设置为“false”，PathIntellisense 还会忽略默认的“files.exclude”设置。

```javascript
{
    "files.exclude": {
        "**/*.map.js": true
    }
}
```

### 在导航到文件夹时自动切换到相应目录

默认情况下，自动补全功能不会在目录名称后添加斜杠。

```javascript
{
    "path-intellisense.autoSlashAfterDirectory": false,
}
```

### 自动触发下一个建议/自动推进到下一个选项

当某个建议被选中后，下一个建议会自动显示出来。

此设置将覆盖 `autoSlashAfterDirectory` 的设置。

```javascript
{
    "path-intellisense.autoTriggerNextSuggestion": false,
}
```

### 绝对路径

默认情况下，绝对路径会在当前工作区的根目录下进行解析。如果将此选项设置为“false”，则绝对路径将相对于磁盘的根目录来解析。

```javascript
{
    "path-intellisense.absolutePathToWorkspace": true,
}
```

### 映射关系/对应关系

可以定义自定义的映射规则，这些规则在需要使用绝对路径时，或与 Webpack 的解析选项结合使用时非常有用。

```javascript
{
    "path-intellisense.mappings": {
        "/": "${workspaceFolder}",
        "lib": "${workspaceFolder}/lib",
        "global": "/Users/dummy/globalLibs"
    },
}
```

当路径需要相对于当前项目的根目录来指定时，请使用${workspaceFolder}。V2.2.1 及更早的版本则使用${workspaceRoot}。较新版本则同时支持这两种占位符。

