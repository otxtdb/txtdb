---
title: "Open in External App - Visual Studio Marketplace"
source: "https://marketplace.visualstudio.com/items?itemName=YuTengjing.open-in-external-app&ssr=false#overview"
author:
published:
created: 2026-06-30
description: "Extension for Visual Studio Code - Open file with external application in VSCode"
tags:
  - "clippings"
taxonomy: { doc_category: [vscode] }
---
## 在外部应用中打开

在 VSCode 中使用外部应用程序打开文件。

## 💡 创作初衷

VSCode 是一款非常优秀的编辑器，但有时我更喜欢使用外部应用程序来处理某些文件。例如，我喜欢用 typora 编辑 markdown 文件。通常，我会右键单击该文件，选择 `Reveal in File Explorer` ，然后通过外部应用程序打开它。

不过，借助此扩展程序，您可以更简单地完成操作。只需右键单击文件并选择 `Open in External App` ，该文件便会由系统默认应用程序打开。您还可以使用此方式通过 photoshop 打开 `.psd` 文件、通过浏览器打开 `.html` 文件，依此类推……

## 🔌 安装

1. 通过命令面板执行 `Extensions: Install Extensions` 命令。
2. 在搜索框中输入 `YuTengjing.open-in-external-app` 并安装。

阅读扩展安装指南以获取更多详细信息。

## 🔧 配置 

通过自定义配置，您可以使扩展功能更加强大。例如，为了查看渲染差异，您可以在 Chrome 和 Firefox 中同时打开同一个 HTML 文件。

示例配置：

```markdown
{
  "openInExternalApp.openMapper": [
    {
      // represent file extension name
      "extensionName": "html",
      // the external applications to open the file which extension name is html
      "apps": [
        // openCommand can be shell command or the complete executable application path
        // title will be shown in the drop list if there are several apps
        {
          "title": "chrome",
          // On MacOS, openCommand should be 'Google Chrome.app'
          "openCommand": "C:\\Program Files (x86)\\Google\\Chrome\\Application\\chrome.exe"
        },
        {
          "title": "firefox",
          // On MacOS, openCommand should be 'Firefox Developer Edition.app'
          "openCommand": "C:\\Program Files\\Firefox Developer Edition\\firefox.exe",
          // open in firefox under private mode
          "args": ["-private-window"]
        }
      ]
    },
    {
      "extensionName": "tsx",
      // apps can be Object array or just the command you can access from shell
      "apps": "code"
    },
    {
      // extensionName can also be an array to share one app config across multiple extensions
      "extensionName": ["pvd", "vtu", "vtk"],
      "apps": [
        {
          "title": "Paraview",
          "openCommand": "paraview.exe"
        }
      ]
    },
    {
      "extensionName": "psd",
      "apps": "/path/to/photoshop.exe"
    },
    // like code-runner, you can custom the shell command to open with file
    {
      "extensionName": "ts",
      "apps": [
        {
          "title": "run ts file",
          "shellCommand": "ts-node ${file}"
        }
      ]
    },
    {
      // shared config, details here: https://github.com/tjx666/open-in-external-app/issues/45
      "extensionName": "__ALL__",
      "apps": "MacVim"
    }
  ]
}
```

![open multiple](https://github.com/tjx666/open-in-external-app/blob/master/images/open-multiple.png?raw=true)

在 VS Code 中，直接右键单击与按住 `alt` 键的同时右键单击是不同的。仅右键单击文件时，会显示命令 `Open in External App` ；但若在按住 `alt` 键的同时右键单击文件，则会显示命令 `Open in Multiple External Apps` 。

![usage](https://github.com/tjx666/open-in-external-app/blob/master/images/usage.gif?raw=true)

## :loudspeaker: 限制 

本扩展提供两种在外部应用中打开文件的方式。

### 1\. Node 包：open 

该包存在一项限制，无法打开由 Electron 生成的文件。例如，您无法使用此包在 `typora` 中打开 `md` 文件。此外，该包也支持 `openCommand` 、 `args` 配置项。当 `isElectronApp: false` （默认情况下）时，扩展将采用此方式。

### 2\. VS Code 扩展 API： vscode.env.openExternal(target: Uri) 

该 API 支持在 Electron 开发的应用中打开文件，但存在一项限制：无法打开包含 `Non-ascii` 字符的文件路径。该 API 仅支持传入单个参数 `target` ，且 `openCommand` 与 `args` 的配置也无法生效。

若需在 Electron 开发的应用中打开文件，您可选择以下两种方式之一：

1. 无需在 VS Code 设置中进行配置，只需将操作系统的默认应用设置为该文件格式的打开方式即可。
2. 使用 `isElectronApp` 选项：
	```javascript
	{
	     "extensionName": "md",
	     "isElectronApp": true,
	}
	```
	多应用示例：
	```javascript
	{
	     "extensionName": "md",
	     "apps": [
	         {
	             "title": "typora",
	             "isElectronApp": true,
	             // following config item is not work
	             // "openCommand": "/path/to/typora.exe",
	             // "args": ["--xxx"]
	         },
	         {
	             "title": "idea",
	             "openCommand": "/path/to/idea.exe",
	             "args": ["--xxx"],
	         }
	     ]
	 }
	```

## ❓ 常见问题

### 是否可以将多个文件扩展名配置为使用同一个应用程序？

可以，将 `extensionName` 设置为字符串数组：

```markdown
{
  "openInExternalApp.openMapper": [
    {
      "extensionName": ["png", "jpg", "jpeg", "gif"],
      "apps": [
        {
          "title": "Paint.NET",
          "openCommand": "C:\\Program Files\\paint.net\\paintdotnet.exe"
        }
      ]
    }
  ]
}
```

### 是否可以在 args 和 shellCommand 中使用变量？

是的，您可以使用在 predefined-variables 中记录的变量占位符。此外，您还可以使用：

- ${cursorLineNumber}
- ${cursorColumnNumber}
```markdown
{
  "extensionName": "ts",
  "apps": [
    {
      "extensionName": "*",
      "apps": [
        {
          "title": "Explorer",
          // shell command combined with placeholder
          "shellCommand": "Explorer.exe /root,${fileDirname}"
        }
      ]
    },
    {
      "title": "run ts file",
      "shellCommand": "ts-node ${file}"
    }
  ]
}
```

### 我可以在 shellCommand 中添加环境变量吗？

是的，你可以使用 shellEnv 来设置额外的环境变量：

```markdown
{
  "extensionName": "ts",
  "apps": [
    {
      "extensionName": "*",
      "apps": [
        {
          "title": "run ts file",
          "shellCommand": "ts-node ${file}",
          "shellEnv": {
            "TOKEN": "tyekjjbqbptcxeycgmwqfepus"
          }
        }
      ]
    }
  ]
}
```

或者您也可以分别为 Windows、Linux 和 macOS 设置独立的环境变量：

```markdown
{
  "extensionName": "ts",
  "apps": [
    {
      "extensionName": "*",
      "apps": [
        {
          "title": "run ts file",
          "shellCommand": "ts-node ${file}",
          "shellEnv": {
            "windows": {
              "PLATFORM": "Windows"
            },
            "linux": {
              "PLATFORM": "GNU/Linux"
            },
            "osx": {
              "PLATFORM": "macOS"
            }
          }
        }
      ]
    }
  ]
}
```

### 如何在 WSL（适用于 Linux 的 Windows 子系统）中使用？

当在 WSL 远程模式下使用 VS Code 时，具体取决于您是在 Windows 应用程序还是 WSL 应用程序中打开该文件，需要将文件路径在 WSL 与 Windows 格式之间进行转换。

默认情况下，该扩展会将 WSL 路径转换为 Windows 路径（例如， `/home/user/file.pdf` → `C:\Users\user\file.pdf` ），以便支持从 WSL 环境在 Windows 应用中打开文件。

然而，如果您希望使用 WSL 应用（如 `evince` 、 `xdg-open` ）打开文件，则需要将 `wslConvertWindowsPath: false` 设置为保留 WSL 原生路径：

```markdown
{
  "openInExternalApp.openMapper": [
    // ✅ Open with Windows application (default behavior)
    {
      "extensionName": "lyx",
      "apps": [
        {
          "title": "Lyx (Windows)",
          "shellCommand": "lyx.exe ${file}"
          // wslConvertWindowsPath defaults to true
          // ${file} will be: C:\Users\username\file.lyx
        }
      ]
    },
    // ✅ Open with WSL application
    {
      "extensionName": "pdf",
      "apps": [
        {
          "title": "Evince (WSL)",
          "shellCommand": "evince ${file}",
          "wslConvertWindowsPath": false
          // ${file} will be: /home/username/file.pdf
        }
      ]
    }
  ]
}
```

**相关问题：**

- #16 - 从 WSL 在 Windows 应用中打开文件
- #74 - 从 WSL 在 WSL 应用中打开文件

### 为特定配置项分配键盘快捷键

`keybindings.json`:

```markdown
{
  "key": "cmd+k cmd+o",
  "command": "openInExternalApp.open",
  "args": {
    // same with following id
    "configItemId": "xxx"
  }
}
```

`settings.json`:

```markdown
{
  "openInExternalApp.openMapper": [
    {
      // extensionName is ignored when set configItemId arg in shortcut
      "extensionName": "",
      "id": "xxx",
      "apps": ""
    }
  ]
}
```

## 我的扩