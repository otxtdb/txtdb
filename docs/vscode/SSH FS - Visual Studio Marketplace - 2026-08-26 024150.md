---
title: "SSH FS - Visual Studio Marketplace"
source: "https://marketplace.visualstudio.com/items?itemName=Kelvin.vscode-sshfs"
author:
published:
created: 2026-08-26
description: "Extension for Visual Studio Code - File system, terminal and task provider using SSH"
tags:
  - "clippings"
taxonomy: { doc_category: [vscode] }
---
[跳转至内容部分](#start-of-content)

## SSH 文件系统

## 凯尔文·舒夫斯

|

781,811 用户安装次数

| (111) | 免费

|

文件系统、终端界面以及通过 SSH 实现的任务管理工具

## SSH 文件系统

![Logo](https://github.com/SchoofsKelvin/vscode-sshfs/raw/HEAD/resources/Logo.png)

此扩展功能允许将远程文件夹作为本地工作区文件夹来使用，启动集成式远程终端，并运行 `ssh-shell` 任务。

## 特点/特色

### 配置编辑器

内置的配置编辑器使得创建和编辑配置变得非常方便： ![Config editor](https://github.com/SchoofsKelvin/vscode-sshfs/raw/HEAD/media/config-editor.png)

这些配置信息默认被存储在用户的设置中（ `settings.json` ）。

```json
"sshfs.configs": [
    {
        "name": "hetzner",
        "putty": "Hetzner",
        "label": "Hetzner",
        "hop": "hetzner2",
        "root": "/root"
    }
],
```

此配置被设置为复制来自我的 PuTTY 会话中的设置信息，例如用户名、主机等。由于我将私钥加载到了 Pageant 程序中（PuTTY 的代理程序），因此通过这个配置，我可以在不需要输入密码或密码短语的情况下创建连接。此外，该配置还指定了所有文件操作的路径，都是相对于服务器上的 `/root` 目录进行的。

这些配置信息是从全局用户设置、当前工作区的设置，以及所有通过 `sshfs.configpaths` 定义的 JSON 文件中读取的。即使工作区覆盖了这些设置，全局配置的路径仍然会被读取。在工作区版本中，合并或忽略重复项时，当前工作区的设置会具有更高的优先级。

### 终端机

通过一个简单的按钮或命令面板，就可以启动远程终端： ![Terminals](https://github.com/SchoofsKelvin/vscode-sshfs/raw/HEAD/media/terminals.png)

*默认情况下，会使用 `$SHELL` 来启动用户的默认 shell。如果需要更改此设置，可以使用配置选项，例如 `"ksh -"` 或 `"exec .special-profile; $SHELL" 。`*

如果某个配置已经建立了连接，那么就不需要再次进行身份验证了。只要配置没有发生变化，现有的连接（无论是工作区文件夹还是终端）都可以被重复使用。

### 远程 shell 任务

新增了一种新的任务类型 `ssh-shell` ，可以用于远程执行 shell 命令： ![Remote shell tasks](https://github.com/SchoofsKelvin/vscode-sshfs/raw/HEAD/media/shell-tasks.png)

任务终端会在服务器上打开一个完整的 PTY 终端。

### 远程工作区文件夹

通过简单的按钮或命令面板，我们可以将远程工作区文件夹当作普通的本地工作区文件夹来使用： ![Remote workspace folder](https://github.com/SchoofsKelvin/vscode-sshfs/raw/HEAD/media/workspace-folder.png)

*与上文中的配置编辑器中的设置相同。*

这一功能可以与使用 `vscode.workspace.fs` API 的扩展无缝协作（该接口在 VS Code 1.37.0 版本中添加）。不过，并非所有扩展都进行了升级，尤其是那些依赖二进制文件的扩展。

如所示，右键点击远程目录后，可以选择立即在该目录中打开远程终端。

这个扩展功能可以支持任何 `ssh://` URI 格式。实际上，我将其设置为文件夹路径 `ssh://hetzner/ng-ui` ，而在远程服务器上，这个路径对应 `/root/ng-ui` 。默认情况下，这个按钮/命令会打开 `ssh://hetzner/` ，然后会执行 `/root` 的操作，因为我的 `Root` 配置字段被设置为这个值。你可以将其设置为任何其他值，包括 `~/path` 。

### 其他杂项

这个扩展还包含了一系列其他的改进和功能。在内部，使用的是 ssh2 包。原始的配置 JSON 对象（如配置编辑器中所看到的那样）基本上就是该包支持的配置选项的直接映射。高级用户可以修改他们的配置，例如利用 `algorithms.cipher` 字段来指定要使用的加密算法列表。

其他一些值得提及的功能包括：

#### 每个连接都需要提供明确的主机名、用户名或密码等凭据。

![Prompt username](https://github.com/SchoofsKelvin/vscode-sshfs/raw/HEAD/media/prompt-username.png)

活跃的连接会被重复使用，以尽量减少对资源的调用次数。如果某个连接超过 5 秒钟仍然没有被任何终端或文件系统使用，那么该连接会被关闭。

#### 代理设置

支持多种代理类型（如 SSH 代理、HTTP 代理以及 SOCKS 4/5 代理）。

![Proxy settings](https://github.com/SchoofsKelvin/vscode-sshfs/raw/HEAD/media/proxy-settings.png)

`SSH Hop` 指的是使用另一种配置来实现跳转，类似于 OpenSSH 中的 `ProxyJump` ：

![Hop config field](https://github.com/SchoofsKelvin/vscode-sshfs/raw/HEAD/media/hop-config.png)

#### SFTP 命令/Sudo 以及终端命令

![SFTP and Terminal Command config fields](https://github.com/SchoofsKelvin/vscode-sshfs/raw/HEAD/media/sftp-config.png)

该扩展功能支持使用自定义的 `sftp` 子系统命令。默认情况下，它会使用由远程 SSH 服务器指定的 `sftp` 子系统。实际上，这通常会导致使用 `/usr/lib/openssh/sftp-server` 子系统。

`SFTP Command` 选项允许指定使用某个特定的命令而不是默认的子系统。 `SFTP Sudo` 选项则使扩展程序尝试创建一个 sudo shell（针对指定的用户，或者遵循 sudo 的默认设置）。默认情况下， `SFTP Command` 或 `/usr/lib/openssh/sftp-server` 会被用作命令。对于大多数用户来说，将此选项设置为 `<Default>` 应该就能像使用 `root` 一样在远程文件系统中进行操作了。而那些具有特殊配置的高级用户可以将 `SFTP Command` 设置为例如 `sudo /some-sftp-server` ，不过他们可能会遇到密码提示方面的问题。

如《终端》部分所述， `Terminal command` 选项允许我们覆盖用于启动远程 shell 的命令。默认情况下，该扩展会通过 SSH 连接启动远程 shell；在必要时会执行 `cd ...` 命令，之后会执行 `$SHELL` 命令来启动用户的默认 shell。这个配置选项允许我们用自定义的方式来启动 shell，或者配置默认的 SSH shell。

## 链接

- GitHub（问题列表 | 预发布信息 | 路线图 | 赞助商）
- [Visual Studio 市场](https://marketplace.visualstudio.com/items?itemName=Kelvin.vscode-sshfs)
- [打开 VSX 注册表](https://open-vsx.org/extension/Kelvin/vscode-sshfs)