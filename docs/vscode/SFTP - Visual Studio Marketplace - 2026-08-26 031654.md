---
title: "SFTP - Visual Studio Marketplace"
source: "https://marketplace.visualstudio.com/items?itemName=Natizyskunk.sftp"
author:
published:
created: 2026-08-26
description: "Extension for Visual Studio Code - SFTP/FTP sync"
tags:
  - "clippings"
taxonomy: { doc_category: [vscode] }
---
[跳转至内容部分](#start-of-content)

## SFTP

## 纳提兹克 unk

|

1,522,878 次安装次数

| (89) | 免费

SFTP/FTP 同步

## 适用于 VS Code 的 sftp 同步扩展

由@Natizyskunk 维护并更新的版本 😀  
（基于已不再维护的 liximomo 的 SFTP 插件进行改编）

---

VSCode-SFTP 允许你添加、编辑或删除本地目录中的文件，并可以通过不同的传输协议（如 FTP 或 SSH）将这些文件同步到远程服务器目录。最基本的配置只需要几行配置代码，而且还有多种可自定义的设置，可以满足各种用户的需求。它既强大又高效，能够帮助开发者通过使用熟悉的编辑器和环境来节省时间。

- 特点
	- [通过 Remote Explorer 进行浏览器远程控制](#remote-explorer)
		- 本地和远程差异分析
		- 同步目录
		- 上传/下载
		- 上传文件后保存即可
		- 文件监视器
		- 多种配置选项
		- 可切换的配置文件
		- 临时文件支持
- [命令](https://github.com/Natizyskunk/vscode-sftp/wiki/Commands)
- [调试](#debug)
- [常见问题解答](#FAQ)

## 安装

### 方法 1（推荐：自动更新）

1. 选择扩展功能（Ctrl + Shift + X）。
2. 从@liximomo 中卸载当前的 sftp 扩展程序。
3. 可以直接从 Visual Studio Code 市场下载新的扩展： [https://marketplace.visualstudio.com/items?itemName=Natizyskunk.sftp.](https://marketplace.visualstudio.com/items?itemName=Natizyskunk.sftp.)
4. 好了！

### 方法 2（手动更新）

安装时只需按照在 VSCode 中执行以下步骤即可：

1. 选择扩展功能（Ctrl + Shift + X）。
2. 从@liximomo 中卸载当前的 sftp 扩展程序。
3. 打开“更多操作”菜单（在顶部有省略号标识），然后点击“从 VSIX…安装”。
4. 找到 VSIX 文件后，请选择它。
5. 重新激活 VSCode。
6. 好了！

## 文档资料

- [首页](https://github.com/Natizyskunk/vscode-sftp/wiki)
- [设置](https://github.com/Natizyskunk/vscode-sftp/wiki/Setting)
- [常见的配置方式](https://github.com/Natizyskunk/vscode-sftp/wiki/Common-Configuration)
- [SFTP 配置](https://github.com/Natizyskunk/vscode-sftp/wiki/SFTP-only-Configuration)
- [FTP 配置](https://github.com/Natizyskunk/vscode-sftp/wiki/FTP%28s%29-only-Configuration)
- [命令](https://github.com/Natizyskunk/vscode-sftp/wiki/Commands)

## 使用方式

如果最新的文件已经存储在远程服务器上，你可以从一个空本地文件夹开始操作，然后下载你的项目，之后再进行同步。

1. 在 `VS Code` 中，打开你想要同步到远程服务器的本地目录（或者创建一个空目录，然后先下载远程服务器上的文件夹内容，以便进行本地编辑）。
2. 在 Windows/Linux 系统中，可以使用 `Ctrl+Shift+P` 命令打开命令面板；而在 Mac 系统中，则可以使用 `Cmd+Shift+P` 命令。然后执行 `SFTP: config` 命令即可。
3. 一个名为 `sftp.json` 的基本配置文件会出现在 `.vscode` 目录下。打开该文件后，可以编辑包含远程服务器信息的配置参数。

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

在 `sftp.json` 中，password 参数是一个可选择的参数。如果省略了这个参数，在同步数据时将会被提示输入密码。注意：使用反斜杠或其他特殊字符时，必须先用反斜杠来转义它们。

4. 保存并关闭 `sftp.json` 文件。
5. 在 Windows/Linux 系统中，可以通过 `Ctrl+Shift+P` 打开命令面板；在 Mac 系统中，则可以通过 `Cmd+Shift+P` 打开命令面板。
6. 输入 `sftp` ，你会看到更多的命令选项。你也可以从项目的文件浏览器上下文菜单中访问许多这些命令。
7. 如果你想要与远程文件夹同步文件，那么 `SFTP: Download Project` 是一个很好的选择。它会将 `remotePath` 设置中指定的目录下载到你的本地打开目录中。
8. 完成啦——现在你可以本地进行编辑了。每次保存后，文件都会上传到远程服务器，从而将本地副本与远程文件同步。
9. 享受吧！

如需详细解释，请访问相关维基页面。

## 示例配置

您可以在这里查看完整的配置选项列表。

- [适用于 VS Code 的 sftp 同步扩展](#sftp-sync-extension-for-vs-code)
	- [安装](#installation)
		- [方法 1（推荐：自动更新）](#method-1-recommended--auto-update)
				- [方法 2（手动更新）](#method-2-manual-update)
		- [文档资料](#documentation)
		- [使用方式](#usage)
		- [示例配置](#example-configurations)
		- [简单](#simple)
				- [个人资料](#profiles)
				- [多重上下文](#multiple-context)
				- [连接探测](#connection-hopping)
			- [单跳](#single-hop)
						- [多跳](#multiple-hop)
				- [用户设置中的配置选项](#configuration-in-user-setting)
		- [远程浏览器](#remote-explorer)
		- [多选](#multiple-select)
				- [订购](#order)
		- [调试](#debug)
		- [常见问题解答](#faq)
		- [捐赠](#donation)
		- [请为我买杯咖啡吧。](#buy-me-a-coffee)
				- [贝宝](#paypal)

### 很简单

```json
{
  "host": "host",
  "username": "username",
  "remotePath": "/remote/workspace"
}
```

### 个人资料

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

*注意：* `watcher` context `  和  ` 这些参数仅适用于根级别的操作。

使用 `SFTP: Set Profile` 来切换配置文件。

### 多重背景

上下文必须不同。

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

*注意：在这种模式下，必须包含* `name` 。

### 连接探测

你可以通过 SSH 协议通过代理连接到目标服务器。

注意：在跳跃配置中，变量替换功能无法正常工作。

#### 单跳

局部 -> 跳跃 -> 目标

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

当地 -> 霍帕 -> 霍普布 -> 目标

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

### 用户设置中的配置选项

你可以使用 `remote` 来指示 sftp 从 remote-fs 获取配置数据。

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

在 sftp.json 文件中：

```json
{
  "remote": "dev",
  "remotePath": "/home/xx/",
  "uploadOnSave": false,
  "ignore": [".vscode", ".git", ".DS_Store"]
}
```

## 远程探索者

![remote-explorer-preview](https://raw.githubusercontent.com/Natizyskunk/vscode-sftp/master/assets/showcase/remote-explorer.png)

Remote Explorer 让你能够远程访问和浏览文件。你可以通过以下方式打开 Remote Explorer：

1. 运行命令 `View: Show SFTP` 。
2. 在活动栏中点击 SFTP 查看。

您只能使用远程管理器来查看文件的内容。要在线编辑文件，请运行命令 `SFTP: Edit in Local` 。

### 多选

你可以在远程服务器上同时选择多个文件或文件夹进行下载和上传。只需按住 Ctrl 或 Shift 键，同时选择所有想要下载或上传的文件即可，就像在常规的文件管理器视图中一样。

注意：如果浏览器未能正确更新，那么在删除文件后，您需要手动刷新父文件夹的内容。

### 订单

您可以通过在 `sftp.json` 配置文件中添加 `remoteExplorer.order` 参数来订购遥控器 Explorer。

在 sftp.json 文件中：

```json
{
  "remoteExplorer": {
    "order": 1 // <-- Default value is 0.
  }
}
```

## 调试

1. 打开用户设置。
- 在 Windows/Linux 操作系统上—— `File > Preferences > Settings`
- 在 macOS 操作系统上 – `Code > Preferences > Settings`
2. 将 `sftp.debug` 设置为 `true` ，然后重新加载 vscode。
3. 查看 `View > Output > sftp` 中的日志。

## 常见问题解答

您可以在这里查看所有常见问题解答。

## 捐赠

如果这个项目帮助你减少了开发时间，且你愿意通过捐款来贡献一份力量，那么请随时联系我们。

[![Buy Me A Coffee](https://bmc-cdn.nyc3.digitaloceanspaces.com/BMC-button-images/custom_images/orange_img.png)](https://www.buymeacoffee.com/Natizyskunk)