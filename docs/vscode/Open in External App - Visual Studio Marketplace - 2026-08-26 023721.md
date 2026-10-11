---
title: "Open in External App - Visual Studio Marketplace"
source: "https://marketplace.visualstudio.com/items?itemName=YuTengjing.open-in-external-app"
author:
published:
created: 2026-08-26
description: "Extension for Visual Studio Code - Open file with external application in VSCode"
tags:
  - "clippings"
taxonomy: { doc_category: [vscode] }
---
## 在外部应用中打开

在 VSCode 中打开包含外部应用程序的文件。

## 💡 动力

VSCode 确实是一个非常出色的编辑器，但有时候我还是更喜欢使用外部应用程序来处理某些文件。例如，我喜欢使用 Typora 来编辑 Markdown 文件。通常，我会右键点击文件，然后选择“ `Reveal in File Explorer` ”，这样就能通过外部应用程序来打开该文件了。

不过，通过这种扩展方式，操作会更加简单。只需右键点击该文件，然后选择 `Open in External App` 选项，系统就会自动打开该文件对应的默认应用程序。你也可以使用这种方式来打开 `.psd` 格式的 Photoshop 文件、 `.html` 格式的浏览器文件等等……

## 🔌 安装过程

1. 从命令面板中执行 `Extensions: Install Extensions` 命令。
2. 在搜索框中输入 `YuTengjing.open-in-external-app` ，然后执行安装操作。

如需了解更多详细信息，请阅读扩展程序的安装指南。

## 🔧 配置

通过自定义配置，你可以让扩展功能更加强大。例如，为了体验渲染效果的差异，你可以同时在 Chrome 和 Firefox 浏览器中打开同一个 HTML 页面。

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

在 VSCode 中，右键点击的方式与按住 `alt` 键时右键点击的方式是不同的。如果你在按住 `alt` 键的情况下右键点击文件，你会看到命令 `Open in External App` ；而如果你在按住 `alt` 键的情况下右键点击文件，则会看到命令 Open in Multiple External Apps 。

![usage](https://github.com/tjx666/open-in-external-app/blob/master/images/usage.gif?raw=true)

## :扬声器: 限制

该扩展程序采用两种方式来在外部应用程序中打开文件。

### 1\. 节点包：已打开

该插件有一个限制，即无法打开由 Electron 生成的文件。例如，你无法使用这个插件在 `typora` 文件中打开 `md` 文件。此外，该插件还支持 `openCommand` 和 `args` 配置项。当设置为 `isElectronApp: false` 时，扩展会使用这种格式来处理文件。

### 2\. VSCode 扩展 API：vscode.env.openExternal(target: Uri)

该 API 支持在应用中打开由 Electron 框架构建的文件。不过，该接口有一个限制：无法打开包含 `Non-ascii` 字符的文件路径。该接口只能传递一个参数 `target` ，而 `openCommand` 和 `args` 参数则无法使用。

如果您希望在由 Electron 开发的应用程序中打开文件，可以选择以下两种方式中的任何一种：

1. 请不要在中在 VSCode 的设置中进行相关配置，同时请确保你的操作系统将那种文件格式作为默认打开方式来识别。
2. 使用 `isElectronApp` 选项：
	```javascript
	{
	     "extensionName": "md",
	     "isElectronApp": true,
	}
	```
	多个应用程序的例子：
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

## ❓ 常见问题解答

### 我可以配置多个文件扩展名，以便使用同一个应用程序吗？

是的，将 `extensionName` 设置为一个字符串数组：

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

### 我可以在\`args\`和\`shellCommand\`中使用变量吗？

是的。你可以使用在“预定义变量”部分中描述的变量占位符。除此之外，你还可以使用其他相关的内容。

- ${cursorLineNumber} 行
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

### 我可以向 shellCommand 添加环境变量吗？

是的，你可以使用 shellEnv 来设置额外的环境变量。

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

或者，您可以為 Windows、Linux 和 macOS 分别设置环境变量：

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

### 如何在 Windows Linux 子系统中使用它？

在 WSL 远程模式下使用 VSCode 时，如果文件是在 Windows 应用程序还是 WSL 应用程序中打开，那么文件路径需要在 WSL 和 Windows 格式之间进行转换。

默认情况下，该扩展会将 WSL 路径转换为 Windows 路径（例如， `/home/user/file.pdf` 转换为 `C:\Users\user\file.pdf` ），从而支持在 WSL 中的 Windows 应用程序中打开文件。

不过，如果您想要打开包含 WSL 应用程序的文件（比如 `evince` 、 `xdg-open` ），则需要设置 `wslConvertWindowsPath: false` 以保留 WSL 原有的路径结构。

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

- #16 – 在 WSL 中的 Windows 应用程序中打开文件
- #74 – 在 WSL 应用程序中打开文件

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

## 我的扩展程序

- [在外部应用中打开](https://github.com/tjx666/open-in-external-app)
- [包管理器增强工具](https://github.com/tjx666/package-manager-enhancer)
- [新版本的文件工具类函数](https://github.com/tjx666/vscode-neo-file-utils)
- [重新加载应该能解决所有问题。](https://github.com/tjx666/reload-can-solve-any-problems)
- [VSCode FE 辅助工具](https://github.com/tjx666/vscode-fe-helper)
- [VSCode 文件](https://github.com/tjx666/vscode-archive)
- [更好的色彩增强工具](https://github.com/tjx666/better-colorizer/tree/main)
- [修改文件前的警告信息](https://github.com/tjx666/modify-file-warning)
- [权力编辑](https://github.com/tjx666/power-edit)

请查看以下信息：发行商/云腾景

## 🧡 支持者们

感谢 `JiangShiqi` 设计了该扩展程序的标志。