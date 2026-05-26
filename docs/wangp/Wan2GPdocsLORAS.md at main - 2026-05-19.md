---
title: "Loras Guide - 使用和管理 Loras 进行定制"
source: "https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/LORAS.md"
author:
published:
created: 2026-05-19
description: "A fast AI Video Generator for the GPU Poor. Supports Wan 2.1/2.2, Qwen Image, Hunyuan Video, LTX  Video and Flux. - Wan2GP/docs/LORAS.md at main · deepbeepmeep/Wan2GP"
tags:
  - "clippings"
taxonomy: { doc_category: [wangp] }
---
## Loras 指南

Loras（低秩适配）允许你通过为视频添加特定的风格、角色或效果来定制视频生成模型。

## 目录结构

LoRA 根据其设计的模型类型组织在不同的文件夹中：

所有 LoRA 现在都位于单个 `loras/` 根目录下：

### Wan 模型

- `loras/wan/` - Wan t2v (14B / 通用) loras
- `loras/wan_5B/` - Wan 5B loras
- `loras/wan_1.3B/` - Wan 1.3B loras
- `loras/wan_i2v/` - Wan i2v loras

### 其他模型

- `loras/hunyuan/` - Hunyuan Video t2v loras
- `loras/hunyuan/1.5/` - 专门为 Hunyuan 1.5 模型设计的 LoRA
- `loras/hunyuan_i2v/` - Hunyuan 视频 i2v Loras
- `loras/ltxv/` - LTX 视频 Loras
- `loras/flux/` 和 `loras/flux2/` - Flux Loras
- `loras/qwen/` - Qwen loras
- `loras/z_image/` - Z-Image loras
- `loras/tts/` - Chatterbox / TTS presets

## 自定义 Lora 目录

启动应用时可以指定自定义的 lora 目录：

```css
# Use shared lora directory for Wan t2v and i2v
python wgp.py --lora-dir /path/to/loras/wan --lora-dir-i2v /path/to/loras/wan_i2v

# Specify different directories for different models
python wgp.py --lora-dir-hunyuan /path/to/loras/hunyuan --lora-dir-ltxv /path/to/loras/ltxv
```

## 使用 Loras

### 基本用法

1. 将你的 lora 文件放在正确的目录
2. 启动 WanGP
3. 在高级选项卡中，选择“Loras”部分
4. 勾选你想要激活的 lora
5. 为每个 lora 设置乘数（如果未提及乘数，默认为 1.0）

一旦 WanGP 启动后，如果你将 loras 存储在 loras 文件夹中，请点击顶部的 *刷新* 按钮，以便使其可选。

### Loras 自动下载

WanGP 将尝试记住 lora 的获取位置，并将相应的下载 URL 存储在嵌入在生成视频中的生成设置中。这对于共享信息或在重新安装后轻松恢复丢失的 loras 很有用。

如果 Loras 存储在像 *Hugging Face* 这样的仓库中，这可以很好地工作，但对于需要登录（如 *CivitAi* ）才能下载的 Loras，目前还无法使用。

WanGP 将在以下事件发生时更新其内部 URL Lora 缓存：

- 在应用或导入包含完整 URL Loras 的 *加速器配置文件* 、 *设置* 或 *Lset* 文件时（不仅仅是本地路径）
- 在提取使用 Loras 生成的视频的设置，且该视频包含完整 Loras URL 时
- 在手动使用底部的 *下载 Lora* 按钮下载 Lora 时

所以你使用 WanGP 越多，URL 缓存文件就会越更新。该文件是 *loras\_url\_cache.json* ，位于 WanGP 的根目录。

如果需要，你可以删除这个文件，但会有风险，或者与朋友分享以节省他们定位 Loras 的时间。如果你手动修改或删除这个文件，需要重启 WanGP。

### Lora Multipliers

乘数控制每个 Lora 效果的强度：

#### Simple Multipliers

```apache
1.2 0.8
```

- 第一个 lora：1.2 强度
- 第二个 lora：0.8 强度

#### 基于时间和基于相位的乘法器

对于在生成步骤中的动态效果，使用逗号分隔的值：

```apache
0.9,0.8,0.7
1.2,1.1,1.0
```

- 对于30个步骤：0-9步使用第一个值，10-19步使用第二个值，20-29步使用第三个值
- 第一个 lora：0.9 → 0.8 → 0.7
- 第二个 lora：1.2 → 1.1 → 1.0

对于使用内部两个扩散模型（ *高噪声* / *低噪声* ）的模型（如 Wan 2.2），您可以通过用";"分隔每个阶段来指定要应用于特定阶段的 Loras。

像 LTX 2 模型有两个阶段，";"可用于指定每个阶段的乘数。

例如，如果您想禁用 *高噪声* 阶段的 Lora，仅在 *低噪声* 阶段启用它：

```abnf
0;1
```

此外，在 Wan 2.2 版本中，如果你有两个 loras，并希望第一个 loras 仅在噪声较高时应用，而第二个 loras 在噪声较低时应用：

```apache
1;0 0;1
```

通常情况下，你可以使用任何浮点数作为乘数，并且让一个 Lora 在单个阶段内的乘数发生变化：

```apache
0.9,0.8;1.2,1.1,1
```

在这个例子中， *高噪声* 阶段将使用乘数 0.9 和 0.8，而 *低噪声* 阶段将使用 1.2、1.1 和 1。

这里还有一个两个 Lora 的例子：

```apache
0.9,0.8;1.2,1.1,1
0.5;0,0.7
```

如果你的多个 Lora 乘数中有基于阶段的（即带有";"），同时也有仅基于时间的 Lora 乘数（没有";"但有","），那么仅基于时间的乘数将忽略阶段。例如，假设我们在以下示例中有一个 6 步去噪过程：

```apache
1;0
0;1 
0.8,0.7,0.5
```

这里第一个 lora 将按预期使用，仅与高噪声模型配合，而第二个 lora 仅与低噪声模型配合。但对于第三个 Lora：在步骤 1-2 中，乘数将是 0.8（无论相位如何），然后在步骤 3-4 中，乘数将是 0.7，最后在步骤 5-6 中，乘数将是 0.5。

即使只有一个模型（即没有高/低模型），你也可以使用分阶段的 Lora 乘数，因为 Lora 乘数阶段与引导阶段对齐。假设你定义了 3 个引导阶段（例如引导=3，然后引导=1.5，最后引导=1）：

```apache
0;1;0 
0;0;1
```

在这种情况下，当引导为 3 时，不会应用任何 Lora。然后第一个 Lora 仅在引导为 1.5 时使用，第二个 Lora 仅在引导为 1 时使用。

最好的是，你可以将 3 个引导阶段与高/低模型结合使用。让我们以 *Wan 2.2 的闪电 4/8 步 Lora 加速器* 为例，我们希望在非常开始时增加一些引导（在这种情况下，一个仅持续 1 步的第一阶段就足够了）：

```apache
Guidances: 3.5, 1 and 1
Model transition: Phase 2-3
Loras Multipliers: 0;1;0 0;0;1
```

在此第一阶段使用指导 3.5 时，将使用高模型，但完全不使用 lora。然后在第二阶段仅使用高 lora（这需要将指导设置为 1）。最后在第三阶段 WanGP 将切换到低模型，然后仅使用低 lora。

*注意，用于倍数的语法也可以在 Finetune 模型定义文件中使用（只是每个倍数定义在 JSON 列表中是一个字符串）*

## Lora 预设 (.Lset 文件)

Lora 预设包含使用 Lora 或 Lora 组合所需的所有信息：

- Lora 的完整下载 URL
- 默认 Loras 倍数
- 使用 Loras 时对应的 *触发词* 的示例提示（通常作为注释），可选地，它们可能包含使用宏自动生成提示的高级提示。

一个 Lora 预设是一个只有几 KB 大小的文本文件，用户之间可以轻松共享。如果你创建了一个 Lora，不要犹豫使用这种格式。

### 创建预设

1. 配置你的 loras 和倍数
2. 写一个带有以 # 开头的注释行的提示，其中包含指令

### 示例 Lora 预设提示

```applescript
# Use the keyword "ohnvx" to trigger the lora
A ohnvx character is driving a car through the city
```

使用宏（查看下方文档），用户只需输入两个词，提示就会自动生成：

```coffeescript
! {Person}="man" : {Object}="car"
This {Person} is cleaning his {Object}.
```

### 管理 Loras 预设（.lset 文件）

- 直接从网页界面编辑、保存或删除预设
- 预设包含使用说明的注释
- 与其他用户共享 `.lset` 文件（确保其中包含完整的 Loras URL）

如果 WanGP 不知道你从哪里获取 Loras，*.lset* 文件可能只包含本地路径。你可以使用文本编辑器编辑.lset 文件，并将本地路径替换为其 URL。如果你将 Lora 存储在 Hugging Face 上，可以通过选择文件并点击 *复制下载链接* 轻松获取其 URL。

要分享一个 *.Lset* 文件，目前你需要直接在存储该文件的 Lora 文件夹中获取它。

## 支持的格式

WanGP 支持多种 LoRA 格式：

- **Safetensors** (.safetensors)
- **Replicate** 格式
- ...

## LoRA 加速器

大多数 Loras 用于应用特定风格或修改生成视频的输出内容。然而，有些 Loras 被设计为将模型转化为精炼模型，这种模型生成视频所需的步骤更少。Loras 加速器通常需要将引导（Guidance）设置为 1。别忘了这样做，否则不仅生成视频的质量会差，而且速度会慢两倍。

您可以在下方找到大多数 *Loras 加速器* ：

- Wan 2.1 [https://huggingface.co/DeepBeepMeep/Wan2.1/tree/main/loras\_accelerators](https://huggingface.co/DeepBeepMeep/Wan2.1/tree/main/loras_accelerators)
- Wan 2.2 [https://huggingface.co/DeepBeepMeep/Wan2.2/tree/main/loras\_accelerators](https://huggingface.co/DeepBeepMeep/Wan2.2/tree/main/loras_accelerators)
- Qwen: [https://huggingface.co/DeepBeepMeep/Qwen\_image/tree/main/loras\_accelerators](https://huggingface.co/DeepBeepMeep/Qwen_image/tree/main/loras_accelerators)

### 设置说明

设置 Loras 加速器有三种方法：

1. **使用嵌入式 Loras 加速器微调** 某些模型如 *Vace FusioniX* 或 *Vace Coctail* 的 Loras 加速器已经在自身定义中设置好了，您无需进行任何操作，它们将随微调过程一同下载。
2. **加速器配置文件** 您可以通过顶部的 *设置* 下拉框选择预定义的 *加速器配置文件* 。可用的加速器选项将取决于模型。如果微调/模型已经加速，则不会提供任何加速器。只需点击 *应用* ，加速器 Loras 将在底部的 Loras 选项卡中设置。任何缺失的 Lora 将在您第一次尝试生成视频时自动下载。请注意，当应用 *加速器配置文件* 时，输入（如 *已激活的 Loras* 、 *推理步数* 等）将被更新。但是，如果您已经设置了现有的 Loras（这些是非 Loras 加速器），它们将被保留，以便您可以轻松地在加速器配置文件之间切换。

您会在与 Loras 加速器相关的乘数文本输入框的末尾看到 "|" 字符。它和空格字符的作用相同，用于分隔乘数，但它会告诉 WanGP Loras 加速器乘数在哪里结束，以便它可以将 Loras 加速器与 Non Loras 加速器合并。

3. **手动安装**
- 下载 Lora
- 将其放置在相应模型的 Lora 目录中
- 按照后文部分所述配置 Loras 乘数，CFG

## FusioniX（或 FusionX）Lora 用于 Wan 2.1 / Wan 2.2

如果你只需要一个 Lora 加速器，可以使用这个。它是由多个 Lora 加速器（包括下方的 Causvid）和风格 Loras 组合而成。它不仅能加速视频生成，还能提高质量。这个 Lora 有两个版本，无论是用于 t2v 还是 i2v

### 使用方法

1. 选择一个 Wan t2v 模型（例如，Wan 2.1 text2video 13B 或 Vace 13B）
2. 启用高级模式
3. 在高级生成选项卡中：
	- 设置引导尺度 = 1
		- 设置偏移尺度 = 2
4. 在高级 Lora 选项卡中：
	- 选择 CausVid Lora
		- 将乘数设置为1
5. 将生成步数设置为8-10
6. 生成！

## 自驱动光 x2v Lora（视频生成加速器）适用于 Wan 2.1 / Wan 2.2

Selg 强制 Lora 由 Kijai 基于 Self-Forcing lightx2v 蒸馏 Wan 模型创建，仅需 2 步即可生成视频，并且由于无需分类器自由引导，速度提升了 2 倍。它适用于 t2v 和 i2v 模型。您可以在名称 *Wan21\_T2V\_14B\_lightx2v\_cfg\_step\_distill\_lora\_rank32.safetensors 下找到它。*

### 使用方法

1. 选择一个 Wan t2v 或 i2v 模型（例如，Wan 2.1 text2video 13B 或 Vace 13B）
2. 启用高级模式
3. 在高级生成选项卡中：
	- 设置引导尺度 = 1
		- 设置偏移尺度 = 5
4. 在高级 Lora 选项卡中：
	- 选择上方的 Lora
		- 将乘数设置为 1
5. 将生成步骤设置为2-8
6. 生成！

## CausVid Lora（视频生成加速器）适用于 Wan 2.1 / Wan 2.2

CausVid 是一个精炼的 Wan 模型，能够在 4-12 步内生成视频，速度提升 2 倍。

### 使用方法

1. 选择一个 Wan t2v 模型（例如，Wan 2.1 text2video 13B 或 Vace 13B）
2. 启用高级模式
3. 在高级生成选项卡中：
	- 设置引导尺度为1
		- 设置偏移尺度为7
4. 在高级 Lora 选项卡中：
	- 选择 CausVid Lora
		- 设置乘数为0.3
5. 设置生成步数为12
6. 生成！

### CausVid 步骤/倍数关系

- **12 步骤** : 0.3 倍数（推荐）
- **8 个步骤** : 0.5-0.7 倍数
- **4 个步骤** : 0.8-1.0 倍速

*注意：步骤越低 = 质量越低（尤其是动态画面）*

## AccVid Lora（视频生成加速器）适用于 Wan 2.1 / Wan 2.2

AccVid 是一个精炼的 Wan 模型，通过不再需要分类器自由引导（即 cfg=1），视频生成速度提升 2 倍。

### 使用方法

1. 选择一个 Wan t2v 模型（例如，Wan 2.1 text2video 13B 或 Vace 13B）或 Wan i2v 模型
2. 启用高级模式
3. 在高级生成选项卡中：
	- 设置引导尺度 = 1
		- 设置偏移尺度 = 5
4. 与原始模型相比，步数保持不变，但由于无需使用分类器自由引导，速度将提高两倍

## Lightx2v 4 步 Lora（视频生成加速器）用于 Wan 2.2

实际上，这个 Lora 由两个 Lora 组成，一个用于 High 模型，一个用于 Low Wan 2.2 模型。

您需要选择这两个 Lora，并设置以下 Lora 乘数：

```abnf
1;0 0;1  (the High lora should be only enabled when only the High model is loaded, same for the Low lora)
```

别忘了将引导设置为1！

## Qwen 图像闪电 4 步 / 闪电 8 步

非常强大的 lora，你可以用它将步数从 30 减少到仅 4 步！只需将 lora 安装在 *lora\_qwen* 文件夹中，选择 lora 并将 Guidance 设置为 1，然后将步数设置为 4 或 8

[https://huggingface.co/Kijai/WanVideo\_comfy/blob/main/Wan21\_T2V\_14B\_lightx2v\_cfg\_step\_distill\_lora\_rank32.safetensors](https://huggingface.co/Kijai/WanVideo_comfy/blob/main/Wan21_T2V_14B_lightx2v_cfg_step_distill_lora_rank32.safetensors)

## 性能技巧

### 快速加载/卸载

- 无需重启应用程序即可添加/删除 Loras
- 使用"刷新"按钮检测新的 Loras
- 启用 `--check-loras` 以过滤不兼容的 Loras（启动速度较慢）

### 内存管理

- LoRA 模型按需加载以节省 VRAM
- 可同时使用多个 LoRA 模型
- 基于时间的乘数不会使用额外内存
- Loras 的顺序并不重要（当然，只要 loras 乘数是正确的顺序！）

## 寻找 Loras

### 来源

- **[Civitai](https://civitai.com/)** - 大型社区收藏
- **HuggingFace** - 官方和社区 loras
- **Discord 服务器** - 社区推荐

### 创建 Loras

- **Kohya** - 流行的训练工具
- **OneTrainer** - 可替代的训练方案
- **自定义数据集** - 使用您自己的内容进行训练

### Lora 无法工作

0. 如果是 Lora 加速器，应将 Guidance 设置为 1
1. 检查 Lora 是否与您的模型大小兼容（1.3B 与 14B）
2. 验证 Lora 格式是否受支持
3. 尝试不同的乘数值
4. 检查 lora 是否针对您的模型类型（t2v vs i2v）进行了训练

### 性能问题

1. 减少活跃 lora 的数量
2. 降低乘数值
3. 使用 `--check-loras` 来过滤不兼容的文件
4. 清除 lora 缓存如果问题仍然存在

### 内存错误

1. 同时使用更少的 loras
2. 减小模型大小（使用 1.3B 而不是 14B）
3. 降低视频分辨率或帧数
4. 如果尚未启用，则启用量化

## 命令行选项

```css
# Lora-related command line options
--lora-dir path                   # Path to Wan t2v loras (default loras/wan)
--lora-dir-wan-5b path            # Path to Wan 5B loras (default loras/wan_5B)
--lora-dir-wan-1-3b path          # Path to Wan 1.3B loras (default loras/wan_1.3B)
--lora-dir-i2v path               # Path to Wan i2v loras (default loras/wan_i2v)
--lora-dir-wan-i2v path           # Alias for Wan i2v loras
--lora-dir-hunyuan path           # Path to Hunyuan t2v loras (default loras/hunyuan)
--lora-dir-hunyuan-i2v path       # Path to Hunyuan i2v loras (default loras/hunyuan_i2v)
--lora-dir-ltxv path              # Path to LTX Video loras (default loras/ltxv)
--lora-dir-flux path              # Path to Flux loras (default loras/flux)
--lora-dir-flux2 path             # Path to Flux2 loras (default loras/flux2)
--lora-dir-qwen path              # Path to Qwen loras (default loras/qwen)
--lora-dir-z-image path           # Path to Z-Image loras (default loras/z_image)
--lora-dir-tts path               # Path to TTS presets (default loras/tts)
--lora-preset preset              # Load preset on startup
--check-loras                     # Filter incompatible loras
```