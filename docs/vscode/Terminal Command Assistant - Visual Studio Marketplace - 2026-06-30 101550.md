---
title: "Terminal Command Assistant - Visual Studio Marketplace"
source: "https://marketplace.visualstudio.com/items?itemName=duolabmeng6.terminal-helper"
author:
published:
created: 2026-06-30
description: "Extension for Visual Studio Code - 在源代码管理旁边添加终端操作按钮"
tags:
  - "clippings"
taxonomy: { doc_category: [vscode] }
---
## Terminal Command Assistant

## duolabmeng6

|

33 installs

[| (0)](#review-details) | Free

在源代码管理旁边添加终端操作按钮

## Terminal Helper VSCode 插件

这是一个VSCode插件，在Activity Bar中添加了一个终端助手面板，可以快速执行常用的终端命令。

## 功能特性

- 在Activity Bar中添加终端助手图标
- 支持自定义终端命令配置
- 提供可视化的命令管理界面
- 支持添加、编辑、删除自定义命令
- 自动创建和管理终端实例
- 配置可通过VSCode设置界面管理

## 安装和使用

1. 克隆或下载此项目
2. 在项目根目录运行 `npm install` 安装依赖
3. 运行 `npm run compile` 编译TypeScript代码
4. 按 F5 启动调试模式，会打开一个新的VSCode窗口
5. 在新窗口的Activity Bar中找到终端助手图标
6. 点击图标打开面板，然后点击相应按钮执行命令

## 自定义命令配置

### 通过界面配置

1. 在终端助手面板的标题栏中点击 "+" 按钮添加新命令
2. 点击设置按钮可以打开VSCode设置页面进行配置

### 通过设置文件配置

在VSCode设置中搜索 `terminalHelper.customCommands` ，可以直接编辑JSON配置：

```json
{
  "terminalHelper.customCommands": [
    {
      "name": "列出文件",
      "command": "ls"
    },
    {
      "name": "Git状态",
      "command": "git status"
    }
  ]
}
```

## 开发

### 编译

```bash
npm run compile
```

### 监听模式编译

```bash
npm run watch
```

### 调试

按 F5 启动扩展开发主机进行调试

## 文件结构

- `package.json` - 插件清单文件
- `src/extension.ts` - 插件主入口文件
- `src/treeDataProvider.ts` - 树视图数据提供者
- `.vscode/launch.json` - 调试配置

## 安装扩展

### 方法1：从.vsix文件安装

1. 下载 `terminal-helper-0.0.1.vsix` 文件
2. 在VSCode中按 `Ctrl+Shift+P` (Windows/Linux) 或 `Cmd+Shift+P` (Mac)
3. 输入 "Extensions: Install from VSIX..."
4. 选择下载的 `.vsix` 文件
5. 重启VSCode

### 方法2：开发模式安装

1. 克隆或下载此项目
2. 在项目根目录运行 `npm install` 安装依赖
3. 运行 `npm run compile` 编译TypeScript代码
4. 按 F5 启动调试模式，会打开一个新的VSCode窗口

## 打包发布

### 生成.vsix文件

```bash
# 安装vsce工具
npm install -g @vscode/vsce

# 编译项目
npm run compile

# 打包生成.vsix文件
vsce package
```

### 发布到VSCode市场

```bash
# 登录（需要Azure DevOps账号）
vsce login <publisher-name>

# 发布
vsce publish
```

## 贡献

欢迎提交Issue和Pull Request来改进这个插件。