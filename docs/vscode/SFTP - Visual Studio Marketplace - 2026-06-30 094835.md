---
title: "SFTP - Visual Studio Marketplace"
source: "https://marketplace.visualstudio.com/items?itemName=Natizyskunk.sftp"
author:
published:
created: 2026-06-30
description: "Extension for Visual Studio Code - SFTP/FTP sync"
tags:
  - "clippings"
taxonomy: { doc_category: [vscode] }
---
## 适用于 VS Code 的 SFTP 同步扩展

由 @Natizyskunk 维护并更新的版本 😀  
（由已停止维护的 liximomo 的 SFTP 插件分叉而来）

---

VSCode-SFTP 允许你在本地目录中添加、编辑或删除文件，并通过 FTP 或 SSH 等传输协议将其同步至远程服务器目录。基础配置仅需数行设置，同时提供丰富的特定选项以满足各类用户的需求。该插件功能强大且运行迅速，通过支持使用熟悉的编辑器和工作环境，帮助开发者节省时间。

- 功能特性
	- [通过远程资源管理器浏览远程文件](#remote-explorer)
		- 本地与远程对比
		- 同步目录
		- 上传/下载
		- 保存时自动上传
		- 文件监听器
		- 多配置
		- 可切换的配置
		- 临时文件支持
- [命令](https://github.com/Natizyskunk/vscode-sftp/wiki/Commands)
- [调试](#debug)
- [常见问题](#FAQ)

## 安装

### 方法一（推荐：自动更新）

1. 选择“扩展”（Ctrl + Shift + X）。
2. 卸载来自 @liximomo 的当前 sftp 扩展。
3. 直接从 VS Code 扩展市场安装新扩展：[https://marketplace.visualstudio.com/items?itemName=Natizyskunk.sftp。](https://marketplace.visualstudio.com/items?itemName=Natizyskunk.sftp。)
4. 搞定！

### 方法二（手动更新）

安装时，只需在 VSCode 中按照以下步骤操作：

1. 选择“扩展”（Ctrl + Shift + X）。
2. 卸载来自 @liximomo 的当前 SFTP 扩展。
3. 打开“更多操作”菜单（顶部的省略号），然后单击“从 VSIX 安装…”。
4. 找到 VSIX 文件并选中。
5. 重新加载 VS Code。
6. 好了！

## 文档

- [主页](https://github.com/Natizyskunk/vscode-sftp/wiki)
- [设置](https://github.com/Natizyskunk/vscode-sftp/wiki/Setting)
- [常用配置](https://github.com/Natizyskunk/vscode-sftp/wiki/Common-Configuration)
- [SFTP 配置](https://github.com/Natizyskunk/vscode-sftp/wiki/SFTP-only-Configuration)
- [FTP 配置](https://github.com/Natizyskunk/vscode-sftp/wiki/FTP%28s%29-only-Configuration)
- [命令](https://github.com/Natizyskunk/vscode-sftp/wiki/Commands)

## 用法

若最新文件已位于远程服务器，你可先创建一个空的本地文件夹，随后下载该项目，此后即可开始同步。

1. 在 `VS Code` 中，打开你希望与远程服务器同步的本地目录（或创建一个空目录，以便先下载远程服务器文件夹的内容，从而在本地进行编辑）。
2. 在 Windows/Linux 上按 `Ctrl+Shift+P` ，或在 Mac 上按 `Cmd+Shift+P` 打开命令面板，然后运行 `SFTP: config` 命令。
3. 在 `.vscode` 目录下会出现一个名为 `sftp.json` 的基础配置文件，请打开它并使用你的远程服务器信息编辑配置参数。

例如：  

```json
{
    "name": "Profile Name",
    "host": "name_of_remote_host",
    "protocol": "ftp",
    "port": 21,
    "secure": true,
    "username": "username",
    "remotePath": "/public_html/project", // <--- This is the path which will be downloaded if you "Download Project"
    "password": "password",
    "uploadOnSave": false
}
```

`sftp.json` 中的密码参数为可选项，若未填写，同步时将提示输入密码。注意：反斜杠及其他特殊字符必须使用反斜杠进行转义。

4. 保存并关闭 `sftp.json` 文件。
5. 在 Windows/Linux 上使用 `Ctrl+Shift+P` ，或在 Mac 上使用 `Cmd+Shift+P` 打开命令面板。
6. 输入 `sftp` ，你将看到许多其他命令。你也可以通过项目的文件资源管理器上下文菜单访问其中许多命令。
7. 如果你想与远程文件夹同步，可以从 `SFTP: Download Project` 开始。这会将 `sftp.json` 中的 `remotePath` 设置所显示的目录下载到你当前打开的本地文件夹中。
8. 完成——你现在可以在本地进行编辑了，每次保存后都会自动上传以同步你的远程文件和本地副本。
9. 祝你使用愉快！

如需详细说明，请访问 Wiki。

## 配置示例

您可以在此查看完整的配置选项列表。

- [VS Code 的 SFTP 同步扩展](#sftp-sync-extension-for-vs-code)
	- [安装](#installation)
		- [方法一（推荐：自动更新）](#method-1-recommended--auto-update)
				- [方法二（手动更新）](#method-2-manual-update)
		- [文档](#documentation)
		- [用法](#usage)
		- [示例配置](#example-configurations)
		- [简单](#simple)
				- [配置文件](#profiles)
				- [多上下文](#multiple-context)
				- [连接跳转](#connection-hopping)
			- [单跳](#single-hop)
						- [多跳](#multiple-hop)
				- [用户设置中的配置](#configuration-in-user-setting)
		- [远程资源管理器](#remote-explorer)
		- [多选](#multiple-select)
				- [排序](#order)
		- [调试](#debug)
		- [常见问题](#faq)
		- [捐赠](#donation) 
		- [请我喝杯咖啡](#buy-me-a-coffee)
				- [PayPal](#paypal)

### 简单

```json
{
  "host": "host",
  "username": "username",
  "remotePath": "/remote/workspace"
}
```

### 配置文件

```json
{
  "username": "username",
  "password": "password",
  "remotePath": "/remote/workspace/a",
  "watcher": {
    "files": "dist/*.{js,css}",
    "autoUpload": false,
    "autoDelete": false
  },
  "profiles": {
    "dev": {
      "host": "dev-host",
      "remotePath": "/dev",
      "uploadOnSave": true
    },
    "prod": {
      "host": "prod-host",
      "remotePath": "/prod"
    }
  },
  "defaultProfile": "dev"
}
```

*注意：* `watcher` context `  和  ` 仅在根级别可用。

使用 `SFTP: Set Profile` 切换配置文件。

### 多上下文

上下文必须互不相同。

```json
[
  {
    "name": "server1",
    "context": "project/build",
    "host": "host",
    "username": "username",
    "password": "password",
    "remotePath": "/remote/project/build"
  },
  {
    "name": "server2",
    "context": "project/src",
    "host": "host",
    "username": "username",
    "password": "password",
    "remotePath": "/remote/project/src"
  }
]
```

*注意：在此模式下，* `name` 为必填项。

### 连接跳转

您可以通过 SSH 协议使用代理连接到目标服务器。

注意：在跳转配置中，变量替换功能不可用。

#### 单跳连接

本地 -> 跳板 -> 目标

```json
{
  "name": "target",
  "remotePath": "/path/in/target",

  // hop
  "host": "hopHost",
  "username": "hopUsername",
  "privateKeyPath": "/Users/localUser/.ssh/id_rsa", // <-- The key file is assumed on the local.

  "hop": {
    // target
    "host": "targetHost",
    "username": "targetUsername",
    "privateKeyPath": "/Users/hopUser/.ssh/id_rsa", // <-- The key file is assumed on the hop.
  }
}
```

#### 多跳

local -> hopa -> hopb -> target 

```json
{
  "name": "target",
  "remotePath": "/path/in/target",

  // hopa
  "host": "hopAHost",
  "username": "hopAUsername",
  "privateKeyPath": "/Users/hopAUsername/.ssh/id_rsa" // <-- The key file is assumed on the local.

  "hop": [
    // hopb
    {
      "host": "hopBHost",
      "username": "hopBUsername",
      "privateKeyPath": "/Users/hopaUser/.ssh/id_rsa" // <-- The key file is assumed on the hopa.
    },

    // target
    {
      "host": "targetHost",
      "username": "targetUsername",
      "privateKeyPath": "/Users/hopbUser/.ssh/id_rsa", // <-- The key file is assumed on the hopb.
    }
  ]
}
```

### 用户设置中的配置

您可以使用 `remote` 让 SFTP 从 remote-fs 获取配置。

在用户设置中：

```json
"remotefs.remote": {
  "dev": {
    "scheme": "sftp",
    "host": "host",
    "username": "username",
    "rootPath": "/path/to/somewhere"
  },
  "projectX": {
    "scheme": "sftp",
    "host": "host",
    "username": "username",
    "privateKeyPath": "/Users/xx/.ssh/id_rsa",
    "rootPath": "/home/foo/some/projectx"
  }
}
```

在 sftp.json 中： 

```json
{
  "remote": "dev",
  "remotePath": "/home/xx/",
  "uploadOnSave": false,
  "ignore": [".vscode", ".git", ".DS_Store"]
}
```

## 远程资源管理器

![remote-explorer-preview](https://raw.githubusercontent.com/Natizyskunk/vscode-sftp/master/assets/showcase/remote-explorer.png)

Remote Explorer 允许你浏览远程文件。你可以通过以下方式打开 Remote Explorer：

1. 运行命令 `View: Show SFTP` 。
2. 在活动栏中单击 SFTP 视图。

您只能通过远程资源管理器查看文件内容。运行命令 `SFTP: Edit in Local` 在本地进行编辑。

### 多选

您可以在远程服务器上一次性选择多个文件/文件夹进行下载和上传。只需在选择所有所需文件时按住 Ctrl 或 Shift 键即可，操作方式与常规资源管理器视图完全相同。

注意：删除文件后，如果资源管理器未正确更新，请手动刷新父文件夹。

### 排序

您可以通过在 `sftp.json` 配置文件中添加 `remoteExplorer.order` 参数来调整远程资源管理器的排序顺序。

在 sftp.json 中： 

```json
{
  "remoteExplorer": {
    "order": 1 // <-- Default value is 0.
  }
}
```

## 调试

1. 打开用户设置。
- 在 Windows/Linux 上 - `File > Preferences > Settings`
- 在 macOS 上 - `Code > Preferences > Settings`
2. 将 `sftp.debug` 设置为 `true` ，然后重新加载 vscode。
3. 在 `View > Output > sftp` 中查看日志。

## 常见问题解答

您可以在这里查看所有常见问题解答。