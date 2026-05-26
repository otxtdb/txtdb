---
title: "Deepy Assistant - 启用 Deepy，配置其工具预设，使用选定媒体和帧，并从 CLI 运行 Deepy"
source: "https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/DEEPY.md"
author:
published:
created: 2026-05-19
description: "A fast AI Video Generator for the GPU Poor. Supports Wan 2.1/2.2, Qwen Image, Hunyuan Video, LTX  Video and Flux. - Wan2GP/docs/DEEPY.md at main · deepbeepmeep/Wan2GP"
tags:
  - "clippings"
taxonomy: { doc_category: [wangp] }
---
## Deepy

Deepy 是 WanGP 的多步媒体工作的助手。它可以生成、检查、编辑、提取、转录、合并和转换图像、视频和音频，同时保持对话上下文。

本指南涵盖：

- 一般指南
- 启用 Deepy
- 在 Web 界面中配置 Deepy
- 将 WanGP 设置文件链接到 Deepy 生成工具
- 自然地使用选定和之前的媒体
- 了解 Deepy 可以直接覆盖哪些生成设置
- 询问 Deepy 关于可用的 LoRAs 和当前默认设置
- 从 CLI 使用 Deepy

**请注意 Deepy 可能会出错，所以务必验证 Deep 的工作**

## 一般指南

一旦启用（见下文），Deepy 通过点击左侧停靠栏中的 `Ask Deepy 打开 Deepy 聊天窗口即可访问。`

Deepy 能够生成图像、视频和音频，并将它们组合起来制作新的媒体。Deepy 所产生的所有内容都将位于 WanGP `Video Generator` 标签页右上角的 `Image / Video Gallery` 和 `Audio Gallery` 中。

Deepy 还可以与用户导入的媒体协同工作：

1. 展开 `Media Info / Late Post Processing / Import Media 部分`
2. 切换到 `  导入媒体到图库  ` 选项卡
3. 选择要导入的文件
4. 点击 ` 导入视频/图片/音频文件`

一旦媒体文件出现在图库中，您可以使用诸如 `  最后一个音频文件  ` 、 `  选定的视频  ` 或描述其内容等措辞来引用它们（如果存在，Deepy 将查询生成元数据中存储的提示）。

Deepy 无法根据您的请求推断出最佳生成设置，因为组合方式太多且取决于您想要使用的生成模型。因此，Deepy 依赖于预定义的模板设置来使用其主要的 6 个生成工具（ `  生成图像  ` ， `  生成视频  ` ， `  编辑图像  ` ， `  带画外音生成视频  ` ， `  根据描述生成音频  ` ， `  根据样本生成音频  ` ）。

WanGP 内置了可立即使用的模板，但您也可以链接已保存的设置。您可以通过点击 Deepy 聊天窗口右侧的 `设置` 控件来访问 Deepy 设置。

在 Web 界面中，Deepy 设置更改会立即对当前 Deepy 会话生效。当您想要将这些设置写入磁盘以供未来的 WanGP 会话使用时，请点击设置面板底部的 `保存 Deepy 设置 ` 。

您也可以在 Deepy 设置窗口中定义默认的宽度和高度，用于所有生成工具。这些设置仅在使用模板文件时生效，前提是未勾选复选框 `在模板文件中使用设置中定义的属性 ` 。如果您想覆盖模板中定义的值，而无需修改模板本身，这将非常方便。

最后但同样重要的是，您可以直接要求 Deepy 覆盖以下模板设置： `width` 、 `height` 、 `  帧数  ` 、 `fps` 、 `loras` 或 `推理步数 ` 。

## 启用 Deepy

Deepy 仅在满足以下两个条件时可用：

1. `启用 Deepy` 已开启。
2. Prompt Enhancer 设置为支持 Qwen3.5VL 模式。

打开配置插件，然后进入 `Prompt Enhancer / Deepy` 标签页。

所需的 Prompt Enhancer 模式：

- `Qwen3.5VL Abliterated 4B`
- `Qwen3.5VL Abliterated 9B`

Deepy 设置在该选项卡中：

- `启用 Deepy` ：打开或关闭 Deepy
- `Deepy VRAM 加载模式 ` ：控制 Deepy 是否保持在 VRAM 中，空闲时卸载，或仅在另一个 WanGP 组件需要 VRAM 时卸载。Deepy 保持在 VRAM 中的时间越长，响应速度越快。
- `上下文窗口令牌 ` ：Deepy 尝试保持多少对话和工具历史记录活跃
- `自定义系统提示 `: 在用户下一条消息时附加到 Deepy 的额外指令

当需求满足时， `Ask Deepy` 启动器会在 WanGP 网页 UI 中显示。

## Deepy 网页设置

打开 `Ask Deepy` ，然后打开 `设置` 面板。

设置面板包含两个展开部分：

- `生成属性`
- `工具使用的模板设置`

此面板中的所有更改将立即用于当前的 Deepy 网络会话。若要保留这些设置以供未来会话使用，请点击面板底部的 `保存 Deepy 设置 ` 。

### 生成属性

- `在停止/重置时自动中止或移除 Deepy 启动的生成。`  
	控制当您停止/重置 Deepy 时，Deepy 创建的队列工作是否被取消或删除。
- `使用 Templates Settings 文件中定义的属性。`  
	启用时，Deepy 使用所选工具模板原样。禁用时，Deepy 仍然从模板开始，但仅用下方面板默认值替换宽度、高度、视频帧数和种子。
- `宽度 ` 和 ` 高度`  
	默认尺寸仅在使用时禁用模板属性时覆盖。
- `帧数`  
	为 `生成视频` 设置的默认帧数覆盖，仅在使用时禁用模板属性时生效。
- `种子（-1为随机）`  
	默认种子覆盖，仅在模板属性禁用时使用。 `-1` 表示随机。

推理步骤、FPS、LoRAs 和其他模型特定值保持由模板驱动，除非您请求本指南后面描述的受支持的按请求覆盖之一。

### 工具模板

Deepy 有 6 个生成工具模板选择器：

- `视频生成器`
- `视频带语音`
- `图像生成器`
- `图像编辑器`
- `从描述生成语音`
- `从样本中获取的语音`

每一行包含：

- 一个下拉菜单，用于选择该工具的当前模板
- `+` 将该工具链接到当前选择的 WanGP 用户设置文件（在视频生成选项卡左上角的下拉菜单中）
- `trash` 用于删除当前的实时链接并返回到之前的或默认模板

更改模板选择器会立即更新活动的 Deepy 网页会话。如果你希望在下次启动 WanGP 时重用相同的选项器，请点击 `Save Deepy Settings` 。

Deepy 在生成工具的聊天记录中显示所选模板，例如：

```css
Generate Image [Z Image Turbo]
Generate Video [LTX-2 2.3 Distilled]
Edit Image [Flux Klein 9B]
```

### 保存 Deepy 设置

点击 Deepy 设置面板底部的 `  保存 Deepy 设置  ` 以将当前网络设置持久化到磁盘。

该保存包括：

- 生成属性值，如自动中止行为、模板属性使用、宽度、高度、帧数和种子
- 每个生成工具当前选择的 Deepy 模板

## 将 WanGP 设置与 Deepy 工具关联

Deepy 模板要么是：

- 随 WanGP 一起提供的内置 Deepy 模板
- 指向 WanGP 用户设置文件的实时链接

### 从 UI 中链接一个工具

实用工作流程：

1. 按你想要的方式配置一个常规的 WanGP 生成
2. 将其保存为 WanGP 用户设置文件
3. 在 WanGP 的 `Lora / 设置` 下拉菜单中选择该用户设置 JSON
4. 打开 Deepy 设置
5. 点击 Deepy 工具旁的 `+`
6. 确认链接

当你以后使用该工具时，Deepy 会直接读取链接的 WanGP 设置文件，因此该文件中的更改将自动生效。

### 重要行为

- 只有从 `Lora / 设置 ` 下拉菜单中选择的 WanGP 用户设置才能以这种方式链接。
- 系统配置文件和 LoRA 预设被拒绝。
- 如果链接的 WanGP 设置文件后来发生变化，Deepy 会自动看到更新后的内容。
- 如果链接的文件消失，Deepy 会回退到该工具的默认模板。
- 如果链接的文件仍然存在但不再适用于该工具，该工具会返回一个资格错误。
- 内置模板无法从界面中删除。
- 链接模板是 Deepy 未直接暴露的特定模型设置的合适位置。Deepy 仍然可以在支持的工具上覆盖宽度、高度、帧数、FPS、推理步数和 LoRAs。

## Deepy 如何解释媒体引用

Deepy 的设计目的是让你能够自然地引用现有媒体。

在实践中，Deepy 通常会：

- 当你说 `selected` 、 `current` 、 `this image` 、 `this video` 、 `this audio` 或 `this frame 时，优先选择当前选中的图片、视频或音频项`
- 使用所选视频的当前播放时间，当您提到 `所选帧` 或 `当前帧时`
- 解决诸如 `上一张图片 ` 、 ` 上一个视频` 或 `最后一段音频等简短引用`
- 在描述先前结果时，解决较旧的输出
- 当引用不明确时，请求澄清而不是编造结果

您仍然可以使用内部媒体 ID，例如 `image_1` 或 `video_3` ，但通常您不需要这样做。

## 使用选定媒体

### 在 Web 界面

对于图像：

1. 点击您想要查看的图片
2. 向 Deepy 询问一些类似的问题：
	- `编辑这张图片，让天空看起来像暴风雨`
		- `检查选定的图片，告诉我手部是否看起来正确`
		- `使用选定的图片作为短视频的起始帧`
		- `使用这张图片和最后一个音频片段制作一个说话视频`

对于视频：

1. 选择视频
2. 将播放器拖动到你感兴趣的时刻
3. 向 Deepy 询问一些类似的问题：
	- `检查这个框架，并告诉我脸是否清晰`
		- `提取选定的帧作为图像`
		- `剪切从选定时间开始的3秒片段`
		- `转录此视频`
		- `静音此视频`
		- `用最后提取的音频替换选定视频的音频`

对于音频：

1. 选择或导入一个音频文件
2. 向 Deepy 询问类似：
	- `转录这个音频`
		- `将此音频转录并标注单词时间戳`
		- `使用此样本生成语音："欢迎来到 WanGP"`
		- `使用此音频和选定的图片制作说话视频`

如果你的语音样本在视频中，Deepy 可以首先提取音频。

### 之前的输出

Deepy 还可以解析如下引用：

- `上一张图片`
- `上一个视频`
- `上一段音频`
- `机器人跳舞的图片`
- `image_2`
- `video_3`

## 你可以让 Deepy 做什么

- 生成图片，编辑图片，生成视频，从静态图片和语音音频生成对话视频，以及从语音描述或语音样本创建语音音频
- 为过渡创建实色边框，空白边框或色卡
- 检查图像和视频帧，并读取本地图像、视频或音频的详细信息，如尺寸、时长、帧率、帧数或音频轨道数
- 提取图片、视频片段或音频片段；转录音频或视频；静音视频；替换音频；调整大小/裁剪媒体；以及合并视频
- 告诉您当前一代工具可用哪些 LoRAs，以及当前一代工具将使用哪些默认设置
- 通过搜索捆绑的文档来回答 WanGP 特定的使用问题

## 音频转录

Deepy 可以转录音频或视频。

- 默认情况下返回分段时间戳。
- 如果您需要更详细的计时，请询问单词时间戳。
- 如果来源有多个音频轨道，请说明您想要哪个轨道。

示例请求：

```css
Transcribe the selected video.
```

```css
Transcribe audio track 2 from the selected video.
```

```applescript
Extract the video excerpt that starts with 'I will be back'.
```

## 示例请求

```css
Generate a cinematic image of a robot violinist on a rainy Paris rooftop at night.
```

```livecodeserver
Edit the selected image so the background becomes a neon alley while keeping the character identity, and use 8 inference steps.
```

```livecodeserver
Generate a short video of a paper boat floating through a glowing cave river at 24 fps with 97 frames and 8 inference steps.
```

```livecodeserver
Generate a video of a dog playing under the rain using the Lego lora
```

```css
Use the selected portrait and the last audio clip to make a talking video.
```

```n1ql
Create speech from this sample saying: Welcome to WanGP.
```

```rust
How do I use VACE for outpainting?
```

多步请求：

```livecodeserver
1) Generate an image of a robot disco dancing on top of a horse in a nightclub.
2) Edit the image so the setting stays the same, but the robot has gotten off the horse and the horse is standing next to the robot.
3) Verify that the edited image matches the description; if it does not, generate another one.
4) Generate a transition between the two images.
```

```livecodeserver
Create a high quality portrait that represents you well. Then create a speech sample in which you introduce your capabilities. When done generate a talking video from the portrait and the generated speech.
```

## Deepy 命令行模式

在命令行模式下启动 Deepy：

```stylus
python wgp.py --ask-deepy
```

启动时，命令行会打印 Deepy 的标志并预加载提示增强器运行时，以便 Deepy 在第一个提示之前就准备好。

### 提示输入

交互式多行输入：

- `Enter`: 发送当前提示
- `Ctrl+Enter`: 在支持该功能的终端上插入换行
- `Alt+Enter`: 插入换行
- `Ctrl+J`: 换行备选方案
- `Ctrl+S`: 在运行时停止当前的 Deepy 回合
- `Shift+Enter`: 在此处不可用，因为控制台将其报告为普通的 `Enter`

### CLI 媒体选择

CLI 拥有自己的虚拟画廊。向其中添加文件，选择一个，并可选择为选定的视频设置播放时间或帧。

示例：

```applescript
/video E:\media\my_clip.mp4
/frame 120
inspect the selected frame and tell me whether the subject is centered
```

```livecodeserver
/audio E:\media\voice.wav
transcribe the selected audio with word timestamps
```

当 Deepy 工具在 CLI 模式下生成媒体时，CLI 会打印生成的输出路径。

### CLI 命令

媒体：

- `/add <path>` ：添加并选择一个图像、视频或音频文件
- `/image <path>`: 添加并选择一个图像文件
- `/video <path>`: 添加并选择一个视频文件
- `/audio <path>`: 添加并选择一个音频文件
- `/list [scope]`: 列出已知的媒体； `scope` 可以是 `all` 、 `media` 、 `image` 、 `video` 或 `audio`
- `/media [scope]`: `/list 的别名`
- `/clear-media`: 删除所有虚拟画廊媒体

选择：

- `/select <ref>`: 通过 id、列表索引或名称片段选择媒体
- `/select-video <media_id>`: 通过媒体 ID 选择视频
- `/selected`: 显示当前选中的媒体
- `/selected-video`: 显示选中视频媒体的 ID
- `/time <secs>`: 设置选中视频的播放时间
- `/frame [index]`: 显示或设置选中视频的帧，从 0 开始

Deepy 设置：

- `/settings`: 显示当前的 CLI Deepy 设置
- `/size [WxH]`: 显示或设置默认生成尺寸并禁用模板属性
- `/frames [count]`: 显示或设置默认 `gen_video` 帧数并禁用模板属性
- `/seed [值]`: 显示或设置默认生成种子并禁用模板属性
- `/template <tool> <variant>`: 设置任何 Deepy 生成工具的模板
- `/templates [工具]`: 列出可用的模板变体
- `/template-props [开|关]`: 显示或切换 Deepy 是否使用模板中的分辨率、帧和种子属性

会话：

- `/help`: 打印 CLI 命令摘要
- `/reset`: 清除 Deepy 对话但保留虚拟画廊媒体
- `/quit`: 退出 CLI 会话

示例：

```bash
/template gen_image "Z Image Turbo"
/template gen_video "LTX-2 2.3 Distilled"
/size 1280x720
/frames 97
/seed -1
```

## 实用技巧

- Deepy 在您明确说明目标以及如何重用当前媒体时效果最佳。
- 对于多步骤任务，请按顺序列出步骤。
- 如果您需要 Deepy 无法直接覆盖的特定模型设置，请将其存储在链接的模板中。
- 在切换模板并希望确认设置时，请询问 Deepy 可用的 LoRAs 或当前默认值。
- 对于图像和视频请求，需明确说明必须保留的细节，如主体身份、构图或氛围。
- 如果你希望 Deepy 使用当前的视频时刻，请先滚动选择好的视频，然后参考 `这个帧` 或 `选定的帧 ` 。
- 对于转录，请说明你是否需要单词时间戳或特定的音频轨道。
- 如果某个工具失败，Deepy 会告诉你而不是编造结果。
- 对于 WanGP 特定的疑问，你可以直接询问 Deepy，而不是手动搜索文档。
- 安装 GGUF 内核以实现快速推理和低 VRAM。