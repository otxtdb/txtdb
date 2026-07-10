---
title: "raulvidis/hermes-android: Android device control for hermes-agent — bridge app + Python toolset"
source: "https://github.com/raulvidis/hermes-android"
author:
published:
created: 2026-07-11
description: "Android device control for hermes-agent — bridge app + Python toolset - raulvidis/hermes-android"
tags:
  - "clippings"
taxonomy: { doc_category: [hermes] }
---
## raulvidis/hermes-android：用于控制 hermes-agent 的 Android 设备管理工具——包含桥接应用程序和 Python 工具集

## hermes-android

给你的 AI 智能体“双手”吧。现在可以远程控制 Hermes-agent 所连接的安卓设备了。

## 它是如何运作的

```
Phone (home WiFi)  ──WebSocket──>  Hermes Server (cloud)  <──HTTP──  AI Agent
                                   relay on port 8766
```

该手机通过 Hermes 服务器来建立连接——无论处于何种 NAT 环境下都能正常使用，无需端口转发、VPN 或 USB 连接。只需要一个 6 位的配对码即可。

## 仓库结构

该代码库包含两个组成部分：

| 组件/组成部分 | 路径 | 语言 | 目的/用途 |
| --- | --- | --- | --- |
| **Android 桥接应用** | `hermes-android-bridge/` | Kotlin | 在手机上运行。通过 WebSocket 与服务器连接，再利用 AccessibilityService 来执行各种命令。 |
| **Python 工具集** | `tools/`, `tests/` | Python | 在服务器上运行。包含 36 个 `android_*` 工具以及 WebSocket 中继功能。同时，该程序也作为正式版本存储在 Hermes-Agent 中。 |

> 注意：这里的 Python 代码仅用于独立开发和测试用途（ `pip install -e .` 、 `pytest` ）。正式环境中的代码则保存在 hermes-agent 仓库中。该 Android 应用程序并不使用或依赖这些 Python 文件。

## 作为 hermes-agent 插件进行安装（版本 0.3.0 及以上）

```
curl -sSL https://raw.githubusercontent.com/raulvidis/hermes-android/main/install.sh | bash
```

或者手动操作：

```bash
mkdir -p ~/.hermes/plugins
cp -r hermes-android-plugin ~/.hermes/plugins/hermes-android
```

重新启动 Hermes——运行 `/plugins` 以进行验证。应显示： `✓ hermes-android v0.3.0 (38 tools)`

## 快速入门

### 1\. 在手机上安装该桥接应用程序。

选项 A——下载预先编译好的 APK 文件（最简单的方法）。每当 `main` 有新版本发布时，系统会自动将新的调试版 APK 上传到“最新版本”目录中。你可以从那里下载 `hermes-android-<version>.apk` 文件并安装它：要么在设备上直接打开该文件进行安装（在系统提示时，需开启浏览器的“安装未知应用”功能）；要么通过 `adb install hermes-android-*.apk` 来安装。

**选项 B——从源代码开始构建：**

```bash
cd hermes-android-bridge
./gradlew assembleDebug
adb install app/build/outputs/apk/debug/hermes-android-*.apk
```

> 该 APK 属于未签名的调试版本，因此 Android/Play Protect 在安装时可能会发出警告。该应用尚未在 Play Store 或 F-Droid 上发布。

### 2\. 在手机上授予相应权限

- 打开 Hermes Bridge 应用程序
- 点击“启用无障碍服务”→找到“Hermes Bridge”→将其切换为“开启”状态
- 点击“启用状态叠加”→授予权限
- 点击“授予屏幕录制权限”→确认系统提示框中的内容（这是 `android_screen_record` 操作所必需的）
- 在“设置”>“应用”>“Hermes Bridge”>“权限”中，授予额外的运行时权限：
	- 位置——属于 `android_location`
		- 联系人 —— 用于 `android_search_contacts`
		- 短信——发送给 `android_send_sms`
		- 电话——拨打 `android_call` 即可直接接通
- 在“设置”>“应用程序”>“特殊应用权限”>“通知权限”中启用通知监听器。同时，需为 `android_notifications` / `android_events` 启用 Hermes Bridge 功能。

### 3\. 连接到您的 Hermes 服务器

告诉赫尔墨斯（通过 Telegram、Discord 等渠道）：

```applescript
Connect to my phone, code is <CODE>
```

其中， `<CODE>` 指的是应用程序中显示的 6 位配对码。

Hermes 会回复服务器地址。将该地址输入到应用程序中，然后点击“连接”。

### 4\. 完成。

该智能体现在可以控制你的手机了。试试看：“打开 Instagram”、“截屏”、“我安装了哪些应用程序？”

## 安卓汽车操作系统（车载中控系统）

该桥接应用程序可以在 Android Automotive OS 系统中运行的汽车主机上运行。当相关硬件不可用时，那些与手机相关的功能（如短信、通话、联系人管理）会妥善处理错误并给出相应的提示。

### 安装

1. 获取 APK 文件：请从最新版本中下载 `hermes-android-<version>.apk` ，或者使用 `cd hermes-android-bridge && ./gradlew assembleDebug 来自行编译该文件。`
2. 通过 ADB 进行侧载： `adb install hermes-android-*.apk`
	- USB 接口：直接连接到主机上的 USB 端口即可。
		- WiFi：先输入 `adb connect <head-unit-ip>:5555` ，然后再进行安装。
3. 启用无障碍功能服务：设置 > 无障碍功能 > Hermes Bridge > 启用
4. 授予覆盖权限：设置 > 应用程序 > 特殊权限 > 在应用程序上绘制 > Hermes Bridge
5. 跳过与手机相关的权限设置（短信、通话、联系人）——不适用

### 连接/连通性

汽车主机需要接入网络才能与中继服务器相连：

- USB 连接模式（推荐）：先输入 `adb forward tcp:8766 tcp:8766` ，然后在应用程序中输入 `http://localhost:8766` 。
- WiFi：在应用程序中输入中继服务器的 `http://<ip>:8766` 地址（两台设备必须处于同一网络中）

### 限制/局限性

| 工具 | AAOS 的最新动态/情况 |
| --- | --- |
| `android_send_sms` | 不可用——会返回错误信息。 |
| `android_call` | 不可用——会返回错误信息。 |
| `android_search_contacts` | 不可用——会返回错误信息。 |
| `android_location` | 这取决于汽车上的 GPS 系统的配置。 |
| `android_screen_record` | 表现可能有所不同（某些原厂设备上，MediaProjection 功能受到限制） |

其他所有工具（点击、滑动、输入、截图、屏幕阅读、打开应用程序等）都能正常使用。

## 工具（38）

| 工具 | 描述 |
| --- | --- |
| `android_setup` | 启动中继设备并设置配对代码 |
| `android_ping` | 检查手机是否已连接。 |
| `android_read_screen` | 获取当前屏幕的可用性树结构（默认不包含系统用户界面；如需包含，请使用 `include_system_ui=true` ） |
| `android_screenshot` | 截取屏幕截图并发送给用户 |
| `android_tap` | 通过坐标或节点 ID 进行点击操作 |
| `android_tap_text` | 通过可见文本来点击相应元素 |
| `android_type` | 在输入框中输入内容 |
| `android_swipe` | 向上/向下/向左/向右滑动 |
| `android_scroll` | 滚动屏幕或相关元素 |
| `android_open_app` | 通过包名来启动应用程序 |
| `android_press_key` | 按回退键、主页键、最近使用的选项等。 |
| `android_wait` | 等待该元素出现 |
| `android_get_apps` | 已安装的应用程序列表 |
| `android_current_app` | 获取前台应用程序信息 |
| `android_long_press` | 通过坐标或节点 ID 进行长按操作 |
| `android_drag` | 从一个点拖动到另一个点 |
| `android_pinch` | 在指定坐标处进行 pinch 缩放操作 |
| `android_find_nodes` | 通过文本/类别/可点击元素来搜索无障碍相关节点 |
| `android_describe_node` | 获取关于某个特定节点的详细信息 |
| `android_screen_hash` | 获取当前屏幕的哈希值，以便进行变更检测 |
| `android_diff_screen` | 将当前屏幕内容与之前的哈希值进行比较 |
| `android_location` | 获取手机的 GPS 位置信息 |
| `android_search_contacts` | 按姓名搜索联系人 |
| `android_send_sms` | 向某个电话号码发送短信 |
| `android_call` | 打电话或打开拨号器 |
| `android_media` | 控制媒体播放功能（播放、暂停、下一首、上一首） |
| `android_send_intent` | 发送 Android Intent 消息 |
| `android_broadcast` | 发送广播意图 |
| `android_clipboard_read` | 读取剪贴板内容 |
| `android_clipboard_write` | 将文本复制到剪贴板 |
| `android_notifications` | 阅读当前的通知 |
| `android_events` | 阅读最新的无障碍相关资讯/活动报道 |
| `android_event_stream` | 实时直播无障碍相关活动 |
| `android_screen_record` | 录制指定时长的屏幕视频 |
| `android_read_widgets` | 阅读主屏幕上的小部件信息 |
| `android_speak` | 文本转语音输出 |
| `android_speak_stop` | 停止文本转语音功能 |

## 权限/许可

| 许可/批准 | 如何授予/如何给予 | 必需品/不可或缺的物品 |
| --- | --- | --- |
| 无障碍服务 | 应用按钮 → 设置 > 辅助功能 | 所有工具（核心要求） |
| 系统警报窗口（叠加显示） | 应用按钮 → 设置 > 在应用上绘制 | 状态叠加显示 |
| 屏幕录制（媒体投影） | 应用按钮 → 确认系统提示框 | `android_screen_record` |
| 位置/地点 | 设置 > 应用 > 权限 > 位置 | `android_location` |
| 读取联系人信息 | 设置 > 应用程序 > 权限 > 联系人 | `android_search_contacts` |
| 发送短信 | 设置 > 应用程序 > 权限 > 短信 | `android_send_sms` |
| 拨打电话 | 设置 > 应用 > 权限 > 电话 | `android_call` （自动拨号） |
| 通知监听器 | 设置 > 特定应用权限 > 通知权限 | `android_notifications`, `android_events` |

## 建筑风格/建筑结构

**Android 应用程序（Kotlin 语言编写）：**

- AccessibilityService 会读取用户界面结构，并执行点击、触摸或滑动等操作。
- WebSocket 客户端（OkHttp）与 Hermes 服务器建立连接
- 用于本地/USB 开发的 HTTP 服务器
- 配对码认证
- 通过 AccessibilityService API 截取屏幕截图
- 以终端为主题的用户界面

**服务器端（Python）：**

- 在 8766 端口上使用 WebSocket 与 HTTP 中继功能（通过 aiohttp 实现）
- 这些工具被注册到了 Hermes-Agent 的工具注册表中。
- 速率限制认证机制：每 60 秒内可尝试 5 次登录，超过限制后将无法登录 5 分钟。
- 自动检测服务器的公网 IP 地址，以便获取设置指南。

## 安全性

详情请参阅 SECURITY.md。要点如下：

- 将代码认证与速率限制相结合
- 电话线是外接的（从不直接暴露在外）
- 当前未加密（ `ws://` ）——在生产环境中请使用 TLS 代理。
- 配对成功后即可完全控制设备——仅连接可信赖的服务器

## 发展/进步

```bash
# Python tests
pip install -e ".[dev]"
python -m pytest tests/

# Android build
cd hermes-android-bridge
./gradlew assembleDebug
```

## 路线图/规划方案

这只是一个可用的原型产品。其愿景是：为爱马仕打造属于自己的手机——一款完全具备自主功能的移动设备。

### v0.2 — 优化与稳定性改进

- 支持 TLS/WSS 协议，实现电话与服务器之间的加密通信
- 持续中继服务（systemd 单元，与网关一起自动启动）
- 服务器端调用计数器，用于防止工具调用产生的循环现象。
- 更完善的错误报告功能（包含故障时的截图及详细说明）
- 网关重启时自动重新连接继电器

### v0.3 — 更丰富的手机交互体验

- 通知监听器——代理程序会实时读取收到的通知。
- 剪贴板桥接功能——实现服务器与手机之间的复制/粘贴操作
- 文件传输——在手机和服务器之间发送文件/照片
- 直接发送短信/拨打电话——无需通过用户界面即可发送短信和拨打电话
- 位置共享——代理能够知道手机的具体位置，从而更好地完成各项任务。

### v0.4 — 多设备支持与自动化功能

- 多部手机——可将多台设备连接到同一个中继设备上
- 定时自动化任务——“每天早上，查看 Bolt 上的通勤费用”
- 事件触发条件——“当该应用发送通知时，执行 X 操作”
- 宏记录功能——只需观看一次操作流程，之后随时可以重新播放。

### v0.5 — 赫尔墨斯终于有了自己的声音

- 电话通话功能——客服人员可以利用文本转语音/语音转文本技术来接听和进行电话通话。
- 语音助手模式——手机始终处于监听状态，通过扬声器进行回应
- 电话接听——“接我的电话，记下留言，告诉他们我会回电”

### v0.6 — 设备端智能处理功能

- 本地模型运行——直接在手机上运行小型模型（如 Qwen 0.5B、Gemma 2B）
- 离线模式——即使没有服务器连接，也可以利用设备上的模型来执行基本命令。
- 混合路由机制：简单的任务在本地处理，复杂的任务则由服务器来处理。
- 设备端应用适配器——无需与服务器往返传输即可实现快速、结构化的数据解析

### 未来的构想/未来的想法

- 通过快捷指令/无障碍功能支持 iOS 系统
- 用于监控手机活动的网页控制面板
- 跨应用工作流程（“在地图上查找餐厅，通过 WhatsApp 分享信息，然后预订 Uber 前往该餐厅”）
- 专为特定用途而设计的“爱马仕手机”——这款手机开机后可直接进入专用模式。