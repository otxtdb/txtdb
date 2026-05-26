---
title: "提示指南 - WanGP 如何解释提示、图像作为提示、增强器和宏"
source: "https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/PROMPTS.md"
author:
published:
created: 2026-05-19
description: "A fast AI Video Generator for the GPU Poor. Supports Wan 2.1/2.2, Qwen Image, Hunyuan Video, LTX  Video and Flux. - Wan2GP/docs/PROMPTS.md at main · deepbeepmeep/Wan2GP"
tags:
  - "clippings"
taxonomy: { doc_category: [wangp] }
---
## 提示指南

本页面解释 WanGP 如何解释主文本提示：多行提示如何被分割或保留，提示行如何与多张图像配对，提示增强器如何改变文本，以及宏如何生成提示变化。

## 提示类型实践

在 WanGP 中，主提示始终是你写在 `prompt` 框中的文本。

根据模型的不同，该文本可以单独使用或与以下内容一起使用：

即使模型也使用图像、音频或视频条件，文本提示仍然告诉模型你想要发生什么。

相同的文本框被用于非常不同种类的模型，因此最佳提示风格取决于你选择的模型。

### 仅文本模型

示例：

实际应用：

- 对于 `Wan2.1 Text2video 14B` ，提示语是你的整个场景描述。
- 对于 `Qwen Image 20B` ，提示语也可以描述海报、标志或包含大量可见文字的图像，因为该模型特别擅长在图像中渲染长文本。
- 对于 `TTS HeartMuLa OSS 3B` ，提示语通常是歌词，而额外的标签字段则引导音乐风格。

### 文本+图像模型

示例：

- `Wan2.1 图像转视频 480p 14B`
- `Wan2.2 图像转视频 增强闪电 v2 14B`

实际应用：

- 图像为模型提供了主题、外观和构图。
- 文本提示应专注于动作、行为、摄像机运动和场景演变。

这就是为什么图像到视频的提示在说诸如：

```livecodeserver
the woman smiles, turns toward the window, and the camera slowly pushes in
```

而不是重新描述图像中已经可见的每个细节时，往往更有用。

### 文本+音频模型

示例：

- `多语言 TTS 闲聊`
- `TTS 索引 TTS 2`
- `TTS Qwen3 Base (12Hz) 1.7B`
- `TTS KugelAudio 0 Open 7B`

实际应用：

- 文本是脚本或语音内容。
- 音频输入通常提供声音身份、情绪或说话风格。

对于能够进行对话的模型，如 `TTS Index TTS 2` 、 `TTS Qwen3 Base (12Hz) 1.7B` 和 `TTS KugelAudio 0 Open 7B` ，提示可以包含如 `Speaker 1:` 和 `Speaker 2:` 的说话人标签。

### 文本+图像+音频模型

示例：

- `混沌视频定制音频 720p 13B`
- `混沌视频头像 720p 13B`

实际应用：

- `混沌视频定制音频 720p 13B` 在你希望从参考图像中的人使用录制的声音或歌曲说话或唱歌时很有用。文本提示仍然有助于描述场景、情绪、构图或动作。
- `Hunyuan Video Avatar 720p 13B` 在音频驱动动画时很有用，但仍然需要提示来引导结果，例如要求特写、逼真的场景或特定的情绪氛围。

### 文本+视频模型

示例：

- `Hunyuan Video 1.5 Upsampler 720p 8B`
- 在 Wan 和 VACE 模型中控制视频工作流程

实际应用：

- 控制或源视频提供了时机和结构。
- 文本提示告诉模型你希望在那种结构之上使用哪种风格、主题或场景方向。

### 指令式编辑模型

有些模型不希望得到一个纯粹的描述性提示。

它们期望提示是一个应用于现有图像或视频的指令。

WanGP 中的实际例子：

- `Qwen 图像编辑 20B`
- `Qwen 图像编辑 Plus (2509) 20B`
- `Qwen 图像编辑 Plus (2511) 20B`
- `Flux 1 开发环境 12B`
- `Wan2.1 Chrono Edit 14B`
- `Ditto 14B`

对于这些模型，输入的图像或视频已经提供了起点。

因此，提示应该说明要做什么改变，而不仅仅是描述最终场景。

好的动作动词有：

- `添加`
- `删除`
- `替换`
- `改变`
- `转动`
- `旋转`
- `重新着色`
- `重新点亮`

编辑模型的弱提示：

```livecodeserver
a woman with a red hat in a rainy street
```

更好的：

```livecodeserver
Add a red wool hat to the woman, keep her face, hairstyle, and the rainy street unchanged.
```

更多实用示例：

```livecodeserver
Remove the people in the background and keep the main subject untouched.
Change the car color to matte black and keep the camera angle the same.
Replace the cloudy sky with a sunset sky, but keep the buildings unchanged.
Rotate the pose of the woman so that she is facing the right.
Render the subjects as classical sculptures carved from single blocks of pristine white marble.
```

这对于 `Qwen Image Edit` 、Flux Kontext、Chrono Edit、Ditto\`、...尤为重要。

对于视频编辑模型如 `Ditto 14B` ，编写适用于整个片段或整个帧的指令，例如：

```livecodeserver
Turn the whole video into a black-and-white film look while keeping the original motion.
Replace the material of all visible statues with polished gold.
```

对于 `Wan2.1 Chrono Edit 14B` ，通常最好启用提示增强器，因为该模型对提示格式的要求比 Qwen Edit 或 Flux Kontext 更严格。

## 文本提示基础

WanGP 在生成之前逐行读取提示。

- 以 `#` 开头的行是注释。
- 以 `!` 开头的行是宏行（见下文宏部分）。
- 其他行是提示内容。

空行通常会被忽略，但有些语音模型会保留它们，因为它们可以用作长语音或对话的手动分割标记。

这在以下情况下尤其实用：

- `TTS Qwen3 Base (12Hz) 1.7B`
- `TTS KugelAudio 0 Open 7B`
- `TTS Index TTS 2`

这些模型通常用于长篇演讲或对话，因此将多行脚本保持在一起通常比将每一行视为单独生成更有用。

## 如何处理文本提示的每一行

下拉菜单 `  如何处理文本提示的每一行  ` 改变了 WanGP 对多行提示的解释方式。

界面显示这些选项：

- `每一行新内容都会在生成队列中添加一个新的视频/图像/音频请求`
- `每一行都将用于同一视频生成的新的滑动窗口`
- `所有行都是同一提示的一部分`

你看到的措辞取决于当前模型以及它是否输出视频、图像或音频。

### 1\. 每个新行添加一个新队列项

当每一行都表示一个独立想法时，这是最实用的选择。

示例：

```livecodeserver
a fox running through snow
a whale breaching at sunset
a drone shot of a neon city in the rain
```

这会创建3个独立的任务。

使用此功能时：

- 你想批量处理多个不相关的想法
- 你想快速测试提示变体
- 你想在一个图像到视频模型中，用多个运动提示重复使用一个 `Start Image`

好的例子：

- `Wan2.1 文本转视频 14B` ：同时尝试多个场景创意
- `Qwen 图像 20B` ：同时尝试多个海报或广告创意
- `Wan2.1 图像转视频 480p 14B` ：从同一张图像尝试多个动态创意

### 2\. 每一行用于同一视频的新滑动窗口

这对于长视频工作流程很有用。

WanGP 不是将每一行视为单独的任务，而是使用：

- 第1行用于第一个窗口
- 第二扇窗的行2
- 第3行用于第三个窗口
- 如果视频需要的窗口比行数多，则最后一行会被重复使用

示例：

```livecodeserver
wide establishing shot of the city at dawn
the camera moves into the crowd and follows the singer
close shot of the singer as the chorus starts
```

当你想要一个包含不断变化情节的长视频时，这种方法很实用。

它特别适用于用于长视频或多窗口视频生成的模型，例如被描述为支持在镜头之间平滑过渡的 `Infinitetalk` 。

使用此方法时：

- 你希望每句台词或情节转折都占一行
- 你希望一个长对话或表演视频随时间发展
- 你希望有一个粗略的故事大纲，而不是写一个长段落

重要的实际限制：

- 在此模式下仅支持一个 `Start Image`

### 3\. 所有行都是同一个提示的一部分

当换行本身就是提示格式的一部分时，这是正确的选择。

在提示是单个结构块时使用，例如：

- 秒秒对应的时序表
- 对话脚本
- 带有如 `[主歌]` 和 `[副歌] 部分的歌词`

示例：时间线提示

```livecodeserver
(at 0 seconds: the man stands in front of the fridge, camera static)
(at 1 second: he opens the fridge and reaches for a can)
(at 2 seconds: the camera shifts to a side angle as he drinks)
```

这对于 `Wan2.2 Image2video Enhanced Lightning v2 14B` 特别有用，因为它的默认提示就使用这种时间线格式。

示例：对话提示

```applescript
Speaker 1: We should leave before the rain gets heavier.
Speaker 2: Give me one minute, I still need my jacket.
Speaker 1: One minute, then we run for the bus.
```

这是实际的选择：

- `TTS 索引 TTS 2`
- `TTS Qwen3 Base (12Hz) 1.7B`
- `TTS KugelAudio 0 Open 7B`

这些模型用于语音和对话，因此将每一行拆分为单独的任务通常会破坏对话结构。

示例：歌词提示

```applescript
[Verse]
Morning light through the window pane
I hum a tune to chase the rain
[Chorus]
Stay with me through every mile
Hold this fire, hold this smile
```

这是实际的选择：

- `TTS HeartMuLa OSS 3B`
- `TTS ACE-Step v1.5 Turbo 2B`

这些音乐模型在歌词作为结构化的提示保持在一起时效果最佳。

## 多张图片作为文本提示

下拉菜单 `Multiple Images as Texts Prompts` 在你同时使用多张图片和多行提示时很重要。

这主要用于图像转视频模型，例如：

- `Wan2.1 Image2video 480p 14B`
- `Wan2.2 Image2video Enhanced Lightning v2 14B`

两种选择是：

- `生成所有图像和文本的组合`
- `匹配图像和文本提示`

在两种模式下，WanGP 都使用当前驱动任务的图像提示字段：

- 如果你提供了 `Start Image` ，这些图像将被使用
- 否则 WanGP 使用 `End Image`
- 如果两者都存在， `Start Image` 是与文本提示配对的那个

所以在正常的图像转视频实践中，这通常意味着 `Start Image` 字段。这并不是关于 `Reference Images` 。

### 生成所有图像和文本的组合

这是探索模式。

WanGP 将每行提示与当前使用的活动图像提示字段中的每张图像进行组合，通常使用 `Start Image` 。

如果你有：

- 3张图像
- 2 行提示

WanGP 将创建 6 个任务。

使用此功能时：

- 你想看看哪种动作提示在哪种图像上效果最好
- 你正在测试多个肖像与多个动作
- 你正在探索，而不是配对

实际例子：

- 3 张肖像
- 提示 1： ` 主体微笑并向相机倾斜`
- 提示 2： ` 主体转身走向窗户`

如果你想要比较所有结果，这会很有用。

### 匹配图像和文本提示

这是配对模式。

当图片1应与提示1搭配，图片2与提示2搭配，以此类推时使用。

这通常是更好的选择，当：

- 每张图片已经具有其自身的预定运动
- 你正在准备一批独立的图像转视频任务
- 你不想让测试所有东西与所有东西的排列组合爆炸

实际例子：

- 肖像 1 + ` 她微笑挥手`
- 肖像 2 + ` 他向左转开始走路`
- 肖像 3 + ` 孩子抬头开始大笑`

如果你使用了 `  生成所有图像和文本的组合  ` ，你会得到很多不想要的交叉组合。 `  匹配图像和文本提示  ` 可以保持批次干净。

## 提示增强器

提示增强最容易想象成一个内置在 WanGP 中的写作助手。

WanGP 有两个级别：

- 一个全局 Prompt 增强器设置在 `Configuration 中`
- 每个生成旁边的 Prompt 增强器控制

如果 `Configuration` 中没有启用 Prompt 增强器，生成界面中不会显示 Prompt 增强器行。

### 在哪里启用

首先在 `配置` 中启用一个提示增强器。

这个全局配置决定：

- WanGP 加载哪个提示增强器系列
- 它在生成期间是否自动工作或按需工作
- 对于基于 Qwen3.5 的增强器，使用的是哪种量化后端
- 采样行为，如 `temperature` 、 `top_p` 和随机种子随机化

一旦启用，生成界面会在主提示字段附近显示提示增强器行。

根据您的配置，它要么：

- 在生成过程中自动运行
- 要么在生成前作为按钮供您手动点击

### 自动模式与按需模式

**自动模式：**

增强的提示将在右侧的生成预览中显示。

- 优点：工作流程最快，无需额外点击，当你总是需要提示重写时很好
- 优点：对于增强器几乎成为工作流程一部分的模型很有用，例如 `Wan2.1 Chrono Edit 14B`
- 缺点：你不会在生成前审查重写的提示
- 缺点：如果增强器过度解读你的想法，你只能在运行开始后或查看保存的元数据时才发现

**按需模式：**

原始提示将被注释，并在下方出现一个增强的提示。如果您对增强的提示不满意，可以请求另一个，它将自动覆盖之前生成的那个。或者您可以修改原始提示（位于注释中），新的指示将被考虑（无需删除 # 注释前缀）。

例如，如果您在第一次请求增强提示后得到：

```livecodeserver
#!PROMPT!: Jensen Huang is talking on stage and says "Welcome guys, we are going to have a lot of fun today."
Jensen Huang steps into the spotlight, black leather jacket creaking slightly as he shifts his weight. His glasses reflect the stage lights ...
```

修改注释中的提示：

```applescript
#!PROMPT!: A woman is talking on stage and says "Welcome guys, we are going to have a lot of fun today."
She steps onto the dimly lit stage, spotlight cutting through haze. "Welcome guys. We're going to have a lot of fun"...
```

- 优点：你可以在生成之前检查和编辑重写的提示
- 优点：最适合严格的提示格式、编辑、歌词或对话，需要手动控制
- 缺点：工作流程中多了一步
- 缺点：当存在多个 `Start Image` 时，只有当 `Multiple Images as Texts Prompts` 设置为 `Match images and text prompts` ，且图像数量与提示行数匹配时才能正常工作

### 提示增强器系列

WanGP 目前支持多个 Prompt Enhancer 后端，您可以在 `配置/扩展` 选项卡中选择：

- `Llama 3.2`
- `Llama Joy`
- `Qwen3.5-4B 精简版`
- `Qwen3.5-9B 简化版`

Qwen 3.5（尤其是 9B / quanto int8 变体）应该是智能提示增强器。此外，它还支持 `Think` 模式，这将迫使提示增强器在您的请求上花费更多时间（Think 模式也需要更多的 VRAM）。

### Qwen3.5 后端选择

基于 Qwen3.5 的增强器，WanGP 可以使用不同的后端。

| 后端 | 最适合 | 优点 | 缺点 |
| --- | --- | --- | --- |
| `Int8` | 默认的 Qwen 设置 | 最简单的选择，最佳质量 | 更依赖 VRAM |
| `GGUF` | 降低内存/磁盘使用量，特别是如果你已经使用 GGUF 工具 | 使用 GGUF CUDA 内核可以非常快，尤其是在 Windows 系统上 | 降低提示合规度 |

如果将 `Config / Performance / Language Models Decoder Engine` 选项设置为 *cg* 或 *vllm* ，Qwen3.5 可以大幅加速。

### 主提示增强器选择

面向用户的下拉菜单通常提供：

- `已禁用`
- `基于文本提示内容`
- `基于图像提示内容（例如起始图像和参考图像）`
- `基于文本提示和图像提示内容`

但并非每个模型都完全显示该集合。

有些模型则提供模型特定的选项。

实用示例：

- `TTS 索引 TTS 2`, `TTS Qwen3 基础（12Hz）1.7B`, 和 `TTS KugelAudio 0 Open 7B` 可以展示：
	- `基于当前提示的语音`
		- `基于当前提示的两人对话`
- `Wan2.1 Chrono 编辑 14B` 将提示增强器限制在文本+图像模式，因为该模型需要同时接收编辑指令和源图像

所以最安全的规则是：

- 当你看到这些选项时，使用通用的 `T` 、 `I` 和 `TI` 逻辑
- 当 WanGP 提供模型特定的标签时，优先使用它们，因为它们是专门为该模型定义的

### 基于文本提示内容

当你的文本想法简短、粗略或细节不足时，这是最佳选择。

实际应用：

- 将一个简单的视频创意转化为更具电影感的段落
- 将一个粗糙的演讲主题转化为正式的演讲稿
- 将一个基本的歌曲创意转化为结构化的歌词

好的例子：

- `Wan2.1 文本转视频 14B`: 如果你想输入一个简短的场景构思并希望获得更丰富的电影细节，则很有用
- `Qwen 图像 20B`: 如果你想获得更精致的图像提示，则很有用
- `TTS Chatterbox 多语言 `: 如果你想让应用程序在生成语音之前起草演讲稿，则很有用

### 基于图像提示内容

这在图像比文本更重要时最有用。

实际应用：

- 从肖像或参考图像开始
- 让增强器读取图像
- 然后让它写一个符合实际可见内容的动作提示

这通常适用于图像到视频的工作流程，其中面部、服装、姿势或构图应忠实于源图像。

### 基于文本提示和图像提示内容

当指令和图像都很重要时，这是最实用的选择。

最明显的例子是 `Qwen Edit 14B` 。

- 图像告诉模型当前存在什么
- 文本告诉它你想改变什么
- 提示增强器将其重写为模型期望的格式

优点：

- 编辑模型和指令跟随工作流程的最佳选择
- 平衡图像保真度与明确用户意图

### 模型专用写作按钮

常见的按钮标签是 `  增强提示  ` 、 `  撰写  ` 、 `  撰写语音  ` 和 `  创作歌词  ` 。

一些模型提供了更具体的提示撰写工作流程。

#### 撰写

用于语音模型，例如：

- `TTS 索引 TTS 2`
- `TTS Qwen3 Base (12Hz) 1.7B`
- `TTS KugelAudio 0 Open 7B`

实际应用：

- 根据一个简短的主题写一篇独白
- 从一个粗略的想法开始写一个两人的对话

这特别有用，因为这些模型通常用于口语内容，其中两个明确支持 `Speaker 1:` / `Speaker 2:` 对话工作流程。

#### 写演讲稿

用于 `TTS Chatterbox Multilingual` 。

实际应用：

- 快速将一个主题转化为口语脚本，然后再生成语音音频

这很有用，因为 Chatterbox 是用于多语言语音生成的，所以许多用户是从一个想法开始的，而不是一个完成的脚本。

#### 创作歌词

用于音乐模型，例如：

- `TTS HeartMuLa OSS 3B`
- `TTS ACE-Step`

实际应用：

- 将一个简短的想法，例如 `一首梦幻合成器流行歌曲，关于思念某人`
- 转化为实际歌词，包含 `[主歌]` 和 `[副歌] 等部分`

这特别有用，因为这些模型由歌词进行条件化训练，而在 HeartMuLa 的情况下，也由风格标签进行条件化训练。

## @ 和 @@ 语法

这两种语法只有在使用提示增强器时才重要。

如果提示增强器被禁用，WanGP 将它们视为普通字符。

### @ 向增强器添加额外指令

格式：

```haxe
your prompt @ extra instructions
```

示例：

```livecodeserver
a serious speech about AI safety @ keep it under 6 sentences, natural spoken English
```

实际应用：

- 保持脚本简短
- 要求特定的语气
- 请求特定的输出形状，但不替换模型的调优增强指令

这是更安全且更实用的日常选项。

### @@ 完全替换增强指令

格式：

```gauss
your prompt @@ full replacement instructions
```

示例：

```livecodeserver
a woman opens a door @@ Output exactly 6 lines. Each line must start with "(at X seconds:" and describe only visible motion.
```

实际应用：

- 强制使用非常特定的输出格式
- 完全覆盖内置增强器行为

仅在你确切知道所需格式时使用。它功能强大，但比 `@` 更容易误用。

## 思考模式

在基于 Qwen3.5 的提示增强器上，WanGP 可以显示一个 `思考` 复选框。

实际应用：

- 当提示模糊、混乱或结构困难时启用它
- 当你想要最快重写时禁用它

它对以下任务最有用：

- 将粗糙的故事想法转化为清晰的逐秒提示
- 将主题转化为可信的两人对话
- 重写困难的编辑指令，使其与输入图像保持一致

思考文本本身并非旨在成为最终增强提示的一部分。

## 宏系统

使用宏从模板创建多个提示。这允许您通过为不同变量定义值列表来生成句子的不同变体。

宏会在 WanGP 应用 `如何处理文本提示的每一行` 中的行处理选项之前展开。实际上这意味着：

- 宏首先生成提示行
- 然后 WanGP 决定这些行是否成为单独的任务、滑动窗口步骤或一个单独的多行提示

### 语法规则

在单行上以 `!` 开头定义你的变量。每个完整的变量定义，包括其名称和值，必须用冒号 `:` 分隔。

### 格式

```nim
! {Variable1}="valueA","valueB" : {Variable2}="valueC","valueD"
This is a template using {Variable1} and {Variable2}.
```

### 工作原理

- 以下提示行中的每个 `{变量}` 都会被替换为其列表中的一个值。
- WanGP 逐行循环遍历这些值。
- 如果两个变量的值数量不同，较短的变量将循环重复使用。

这使得宏实用化：

- 批量测试多个场景创意
- 为图像模型生成多个海报标题
- 从一个可重用模板创建多个提示变体

### 示例

以下宏将通过循环每个变量的值来生成三个不同的提示。

**宏定义：**

```ada
! {Subject}="cat","woman","man" : {Location}="forest","lake","city" : {Possessive}="its","her","his"
In the video, a {Subject} is presented. The {Subject} is in a {Location} and looks at {Possessive} watch.
```

**生成输出：**

```livecodeserver
In the video, a cat is presented. The cat is in a forest and looks at its watch.
In the video, a woman is presented. The woman is in a lake and looks at her watch.
In the video, a man is presented. The man is in a city and looks at his watch.
```

### 实用宏示例

如果你想在一个图像模型中测试多个广告概念，你可以这样做：

```excel
! {Product}="watch","perfume","sneakers" : {Mood}="luxury","minimal","energetic"
Studio advertising photo of a {Product}, {Mood} style, clean background, premium lighting, centered composition
```

如果你的行处理模式设置为将每行新内容作为新的请求添加，WanGP 将为每个生成的提示排队一个图像任务。

## 故障排除

- 如果对话行变成单独的工作项，或者时间线提示分散在多个工作项中，请选择“所有行都是同一提示的一部分”。
- 如果你想要一个故事情节不断变化的视频，请选择 `Each Line Will be used for a new Sliding Window of the same Video Generation` 。
- 如果你想要同时排队多个独立的提示想法，请选择 `Each New Line Will Add a new ... Request to the Generation Queue` 。
- 如果 `Match images and text prompts` 失败，图像和提示的数量必须完全匹配。
- 如果 `@` 或 `@@` 似乎被忽略，提示增强器可能被禁用或未用于该运行。