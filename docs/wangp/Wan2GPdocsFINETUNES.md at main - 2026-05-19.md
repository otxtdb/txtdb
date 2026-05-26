---
title: "Finetunes - 手动向 WanGP 添加新模型"
source: "https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/FINETUNES.md"
author:
published:
created: 2026-05-19
description: "A fast AI Video Generator for the GPU Poor. Supports Wan 2.1/2.2, Qwen Image, Hunyuan Video, LTX  Video and Flux. - Wan2GP/docs/FINETUNES.md at main · deepbeepmeep/Wan2GP"
tags:
  - "clippings"
taxonomy: { doc_category: [wangp] }
---
## FINETUNES

微调模型是指与某一特定模型共享相同架构，但权重由该模型派生的模型。一些微调模型是通过组合多个微调模型创建的。

由于潜在的微调数量可能是无限的，WanGP 默认情况下并不知道特定的微调模型。但是，您可以创建一个微调模型定义，这将告诉 WanGP 该微调模型的存在，WanGP 将为您完成所有常规工作：自动下载模型并构建用户界面。

WanGP 微调系统也可以用来调整默认模型：例如，你可以在现有模型之上添加一些 loras，这些 loras 将始终透明地应用。

微调模型定义是轻量级的 JSON 文件，可以轻松共享。你可以在 WanGP 的 *discord* 服务器上找到一些这样的文件 [https://discord.gg/g7efUW9jGV](https://discord.gg/g7efUW9jGV)

所有微调定义文件都应该存储在 *finetunes/* 子文件夹中。

目前，已对 Wan2.1 文本转视频、Wan2.1 图像转视频、Hunyuan 视频文本转视频的微调模型进行了测试。目前还没有支持 LTX 视频微调。

## 创建一个新的 Finetune 模型定义

所有的 Finetune 模型定义都是存储在 **finetunes/** 子文件夹中的 json 文件。当下载时，所有对应的 Finetune 模型权重将被存储在 *ckpts/* 子文件夹中，并与基础模型相邻。

WanGP 使用的所有模型也使用 Finetunes json 格式进行描述，并可以在 **defaults/** 子文件夹中找到。请不要修改 **defaults/** 文件夹中的任何文件。

但是你可以将这些文件用作新定义文件的起点，以了解定义文件的结构。如果你想改变基础模型的处理方式（标题、默认设置、模型权重路径等），你可以通过在 finetunes 文件夹中创建一个同名的新文件来覆盖默认 Finetunes 定义文件的任何属性。一切都将像两个模型按属性逐项合并一样进行，而 Finetunes 模型定义将具有更高的优先级。

一个定义是由一个 *设置文件* 构建的，该文件可以包含视频生成的所有默认参数。在这个文件之上，一个名为 **模型** 的子树包含所有与微调相关的信息（下载模型的 URL、相应的基准模型 ID 等）。

您可以通过多种方式获取设置文件：

- 在 **设置** 子文件夹中，获取与您的微调基准模型对应的 json 文件（有关基准模型 ID 列表，请参阅下一节）
- 从用户界面中，选择您想要创建微调的基准模型，然后点击 **导出设置**

以下是步骤：

1. 创建一个 *设置文件*
2. 添加一个 **模型** 子树，其中包含微调描述
3. 将此文件保存在 **finetunes** 子文件夹中。文件名将用作其 ID。建议在文件名前加上基础模型的名称。例如，对于基于 Hunyuan Text 2 Video 模型的微调 **Fast** \*，文件名为 *hunyuan\_t2v\_fast.json* 。在此示例中，ID 是 *hunyuan\_t2v\_fast* 。
4. 重启 WanGP

## 架构模型 ID

微调是从基础模型派生出来的，并将继承所有用户界面和相应的模型功能，以下是一些架构 ID：

- *t2v* ：Wan 2.1 视频文本到视频
- *i2v*: Wan 2.1 视频图像 2 视频 480p 和 720p
- *vace\_14B*: Wan 2.1 Vace 14B
- *hunyuan*: Hunyuan 视频文本 2 视频
- *hunyuan\_i2v*: Hunyuan 视频图像 2 视频

defaults 子文件夹中的任何文件名（不带.json 扩展名）都对应一个架构 ID。

请注意，某些架构的权重对应于一个架构的权重组合，该组合由一个或多个模块的权重补充完成。

模块是一组权重，这些权重本身不足以构成一个模型，但可以添加到现有模型中以扩展其功能。

例如，如果在一个具有架构 *t2v* 的模型上添加模块 *vace\_14B* ，就会得到一个具有 *vace\_14B* 架构的模型。这里 *vace\_14B* 既代表一个架构名称，也代表一个模块名称。模块系统允许你在模型之间重用共享权重。

## 模型子树

- *name*: 用于选择的微调名称
- *architecture*: 微调的基础模型的架构 ID（见前文）
- *描述* : 将在顶部显示的微调描述
- *URLs*: 所有微调版本的 URL（量化 / 非量化）。WanGP 将选择最接近用户偏好的版本。您需要遵循命名规范，以帮助 WanGP 识别每个版本的内容（见下一节）。WanGP 支持使用 **quanto** 量化的 8 位模型和缩放 FP8 模型。WanGP 提供了一个命令开关，可以轻松构建此类量化模型（见下文）。 *URLs* 还可以包含本地文件的路径，以允许测试。
- *URLs2*: 用于模型第二阶段的权重（量化 / 非量化）的所有微调版本的 URL。例如，在 Wan 2.2 中，第一阶段包含高噪声模型权重，第二阶段包含低噪声模型权重。此功能可用于 Wan 2.2 以外的其他模型，以在相同视频生成过程中组合不同的模型权重。
- *text\_encoder\_URLs*: 文本编码器版本（量化或非量化）的 URL，如果指定，将覆盖默认文本编码器
- *VAE\_URLs*: VAE 的 URL（在一个列表中），如果指定将覆盖默认的 VAE（目前仅支持 Wan 和 LTX2 模型）
- *模块* ：这是一个要与其他 URL 引用的模型结合使用的模块列表。模块是模型的扩展，与模型合并以扩展其功能。目前支持的模型有： *vace\_14B* 和 *multitalk* 。例如，完整的 Vace 模型是 Wan 文本到视频模型与 Vace 模块的融合。
- *preload\_URLs*: 无论什么情况都要下载的文件 URL（例如用于加载量化映射）
- *loras*: 将在用户指定的任何其他 LoRA 之前应用的 LoRA 的 URL。这些 LoRA 通常是 LoRA 加速器。例如，如果你在这里指定 FusioniX LoRA，你将能够将生成步骤数减少到 10。
- *loras\_multipliers*: 一系列浮点数或字符串，用于定义在 *Loras* 中提到的每个 LoRa 的权重。如果希望 LoRa 权重在步骤间变化，或者希望对 Wan 2.2 模型的特定高噪声阶段或低噪声阶段应用权重，则使用字符串语法（请查阅 LoRa 文档）。例如，在此示例中，权重仅在噪声阶段应用，且在该阶段的前一半步骤中权重为 1，后一半步骤中权重为 1.1。

```prolog
"loras" : [ "my_lora.safetensors"],
"loras_multipliers" : [ "1,1.1;0"]
```

- *auto\_quantize*: 如果设置为 True 且未提供量化模型 URL，WanGP 将根据用户期望对模型进行实时量化
- *可见* : 默认假设为 true。如果设置为 false，模型将不再可见。如果你创建一个微调来覆盖默认模型并隐藏它，这会很有用。
- *image\_outputs*: 将任何生成视频的模型转换为生成图像的模型。实际上，它会调整用户界面以生成图像，并要求模型生成单帧视频。
- *text\_prompt\_enhancer\_instructions*: 这允许您在仅请求关于文本的提示时，覆盖提示增强器使用的系统提示
- *video\_prompt\_enhancer\_instructions*: 这允许您在生成此微调视频时，覆盖提示增强器使用的系统提示
- *image\_prompt\_enhancer\_instructions*: 这允许您在生成此微调图像时，覆盖提示增强器使用的系统提示
- *text\_prompt\_enhancer\_max\_tokens*: 如果仅请求关于文本的提示，则用于覆盖提示增强器生成的最大令牌数（默认为 256）
- *video\_prompt\_enhancer\_max\_tokens*: 覆盖生成视频时提示增强器生成的最大令牌数（默认为 256）
- *image\_prompt\_enhancer\_max\_tokens*: 覆盖生成图像时提示增强器生成的最大令牌数（默认为 256）

为了提高可重用性， *URLs* 、 *modules* 、 *loras* 和 *preload\_URLs* 的属性可以包含单个文本，而不是 URL 列表，该文本对应于要重用的微调或默认模型的 ID。而不是：

```prolog
"URLs": [
  "https://huggingface.co/DeepBeepMeep/Wan2.2/resolve/main/wan2.2_text2video_14B_high_mbf16.safetensors",
  "https://huggingface.co/DeepBeepMeep/Wan2.2/resolve/main/wan2.2_text2video_14B_high_quanto_mbf16_int8.safetensors",
  "https://huggingface.co/DeepBeepMeep/Wan2.2/resolve/main/wan2.2_text2video_14B_high_quanto_mfp16_int8.safetensors"
],
"URLs2": [
  "https://huggingface.co/DeepBeepMeep/Wan2.2/resolve/main/wan2.2_text2video_14B_low_mbf16.safetensors",
  "https://huggingface.co/DeepBeepMeep/Wan2.2/resolve/main/wan2.2_text2video_14B_low_quanto_mbf16_int8.safetensors",
  "https://huggingface.co/DeepBeepMeep/Wan2.2/resolve/main/wan2.2_text2video_14B_low_quanto_mfp16_int8.safetensors"
],
```

您可以这样写：

```json
"URLs":  "t2v_2_2",
"URLs2":  "t2v_2_2",
```

**模型** 子树示例

```smalltalk
"model":
{
        "name": "Wan text2video FusioniX 14B",
        "architecture" : "t2v",
        "description": "A powerful merged text-to-video model based on the original WAN 2.1 T2V model, enhanced using multiple open-source components and LoRAs to boost motion realism, temporal consistency, and expressive detail. multiple open-source models and LoRAs to boost temporal quality, expressiveness, and motion realism.",
        "URLs": [
                "https://huggingface.co/DeepBeepMeep/Wan2.1/resolve/main/Wan14BT2VFusioniX_fp16.safetensors",
                "https://huggingface.co/DeepBeepMeep/Wan2.1/resolve/main/Wan14BT2VFusioniX_quanto_fp16_int8.safetensors",
                "https://huggingface.co/DeepBeepMeep/Wan2.1/resolve/main/Wan14BT2VFusioniX_quanto_bf16_int8.safetensors"
        ],
"preload_URLs": [
],
        "auto_quantize": true
},
```

## 微调模型命名规范

如果模型没有量化，则假定它主要是 16 位的（可能有一些 32 位权重），因此 *bf16* 或 *fp16* 应该出现在名称中。如果你需要示例，只需查看 **ckpts** 子文件夹，基础模型的命名规则是相同的。

如果一个模型被量化，也应该包含术语 *quanto* ，因为 WanGP 目前仅支持 *quanto* 量化的模型，具体来说，你应该将 *fp16* 替换为 *quanto\_fp16\_int8* 或 *bf6* 替换为 *quanto\_bf16\_int8* 。

请注意， *bf16* 、 *fp16* 和 quanto 都必须使用小写字母。

## 创建一个 Quanto 量化文件

如果你使用 *\--save-quantized* 选项启动应用程序，WanGP 将在模型加载后立即在 **ckpts** 子文件夹中创建一个量化文件。请注意，模型将根据你在配置菜单中的选择被量化为 *bf16* 或 *fp16* 。

1. 确保在微调定义的 json 文件中只有一个 URL 或文件路径指向未量化的模型
2. 启动 WanGP *python wgp.py --save-quantized*
3. 在配置菜单中， *Transformer 数据类型* 属性选择 *BF16* 或 *FP16*
4. 启动视频生成（使用的设置无关紧要）。一旦模型加载完成，如果 ckpts 子文件夹中不存在，将创建一个新的量化模型。
5. WanGP 将自动更新 finetune 定义文件，将新创建的量化文件的本地路径添加进去（"URLs"列表将多出一个值，例如 *"ckpts/finetune\_quanto\_fp16\_int8.safetensors"）。*
6. 移除 *\--save-quantized* ，重启 WanGP，并在 *Transformer Model Quantization* 属性中选择 *Scaled Int8 Quantization* 。
7. 启动新的生成，并在终端窗口中验证是否加载了正确的量化模型。
8. 为了共享微调定义文件，您需要将微调模型权重存储在云端。您可以将它们上传到例如 *Huggingface* 。现在您可以在微调定义文件中用 URL 替换本地路径（要在 Huggingface 上获取模型文件的 URL，在访问模型属性时点击 *复制下载链接* ）。

您需要为 *bf16* 或 *fp16* 创建一个量化模型，因为它们不能动态转换。然而，对于非量化模型则无需这样做，因为它们在加载时可以动态转换。

Wan 模型支持 *fp16* 和 *bf16* 数据类型，尽管理论上 *fp16* 能提供更好的质量。相反，Hunyuan 和 LTXV 仅支持 *bf16* 。