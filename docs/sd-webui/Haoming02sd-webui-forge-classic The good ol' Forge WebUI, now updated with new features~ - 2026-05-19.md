---
title: "Stable Diffusion WebUI Forge - Neo"
source: "https://github.com/Haoming02/sd-webui-forge-classic/tree/neo"
author:
published:
created: 2026-05-19
description: "The good ol' Forge WebUI, now updated with new features~ - Haoming02/sd-webui-forge-classic"
tags:
  - "clippings"
taxonomy: { doc_category: [sd-webui] }
---
## Stable Diffusion WebUI Forge - Neo

<sup>[ <b>Neo</b> | <a href="https://github.com/Haoming02/sd-webui-forge-classic/tree/classic#stable-diffusion-webui-forge---classic">Classic</a> ]</sup>

[![UI](https://github.com/Haoming02/sd-webui-forge-classic/raw/neo/html/ui.webp)](https://github.com/Haoming02/sd-webui-forge-classic/blob/neo/html/ui.webp)

> *Stable Diffusion WebUI Forge 是一个建立在 AUTOMATIC1111 原始 Stable Diffusion WebUI 之上的平台，旨在简化开发、优化资源管理、加速推理以及探索实验性功能。  
> “Forge”这个名字灵感源自"Minecraft Forge"。本项目旨在成为 Stable Diffusion WebUI 的“Forge”。  
> 
> \- **lllyasviel**  
> <sup>(paraphrased)</sup>
> 
> *

“Neo”主要作为 Forge 的" `latest` "版本的延续，该版本在 lllyasviel 变得太忙之前是基于 Gradio `4.40.0` 构建的。此外，这个分支专注于优化和易用性，主要目标是通过易于使用的 GUI 运行最新的流行模型。

> [!tip] Tip
> [如何安装](#installation)

## 功能 \[5 月\]

> 原始 Automatic1111 WebUI 的大部分基础功能应仍可正常运行

#### 新功能

- 支持 Anima
- 支持 Flux.2-Klein
	- `4B` / `9B` （非 `FLUX.2-Dev` ）

> [!important] Important
> 若要使用 `Flux.2-Klein` 进行常规 `img2img` 操作，请在“设置/Stable Diffusion”中切换该功能

- 支持 Ernie-Image
	- `ernie-image` / `ernie-image-turbo`
- 支持 Z-Image
	- `z-image` / `z-image-turbo`
- 支持 Wan 2.2
	- 使用 `Refiner` 实现高噪声/低噪声切换
		- 在设置/精修器中启用 `Refiner`

> [!important] Important
> 要导出视频，您需要安装 FFmpeg。

- 支持 Mugen
	- 在“设置/预设/XL"中显示 `Shift` 滑块以选择 `xl` 预设
- 支持高级 SDXL 模型

> [!note] Note
> - **v-prediction:** `v_pred` state\_dict `  必须包含 "  ` "
> - **Zero Terminal SNR：** `ztsnr` state\_dict `  必须包含 "  ` "
> - Rectified Flow：模型路径（例如文件名或文件夹名）必须包含" `rectified` "

- 支持 Qwen-Image / Qwen-Image-Edit

> [!note] Note
> 若要被识别为编辑模型，模型必须在路径（如文件名或文件夹名）中包含" `qwen` "和" `edit` "

- 支持 Flux Kontext

> [!note] Note
> 要被识别为 Kontext 模型，其路径（例如文件名或文件夹名）中必须包含" `kontext` "。

- 实现 `ImageStitch Integrated`
	- 支持为 `flux.2-klein` / `flux-kontext` / `qwen-image-edit 提供多图像输入`
		- 支持为 `wan 2.2 提供首尾帧转视频功能`
- 支持 Nunchaku ( `SVDQ` ) 模型
	- `flux-dev`, `flux-krea`, `flux-kontext`, `qwen-image`, `qwen-image-edit`, `z-image-turbo`
		- 目前只有 `Flux` 和 `Qwen` 支持 LoRA
		- 参见命令行
- 支持 Lumina-Image-2.0
	- `Neta-Lumina` / `NetaYume-Lumina`
- 支持 Chroma1-HD
- 支持混合精度模型
	- `fp4mixed` / `fp8mixed` / `mxfp8` / `nvfp4` / `fp8_scaled`
- 支持 Flux.2-Small-Decoder 与 Qwen2D VAE

> [!tip] Tip
> 查看“下载模型”以获取每个模型及其配套模块的下载地址

> [!tip] Tip
> 查看推理参考以了解如何使用每个模型及推荐的参数

- 重写预设系统
	- 现在会记住每个预设的检查点/模块选择及参数
- 支持 uv 包管理器
	- 大幅加快安装速度
		- 需要手动安装 uv
		- 参见命令行
- 支持 SageAttention、FlashAttention、 `fp16_accumulation` 和 `torch._scaled_mm`
	- 参见命令行
- 为 `matmul` torch.int8 `  实现 Triton 内核以支持  `
	- 量化后加速推理
		- 通过选择 `int8` 中的 `Diffusion in Low Bits 来启用`
- 实现径向注意力机制
	- 加速 `Wan 2.2`
		- 需要手动安装 SpargeAttn
- 为 Refiner 实现快速 `state_dict` 切换
	- 在设置/细化器中启用
- 实现 RescaleCFG
	- 减少烧焦的颜色；主要针对 `v-pred` 检查点
		- 在设置/UI 替代方案中启用
- 实现 MaHiRo
	- 替代的 CFG 计算；提升提示词遵循度
		- 在设置/界面替代方案中启用
- 实现频谱
	- 为所有模型提供无需训练的加速
- 实现 [Epsilon Scaling](https://github.com/comfyanonymous/ComfyUI/pull/10132)
	- 在“设置/Stable Diffusion”中启用
- 实现 `torch.compile`
	- 编译后加速推理
- 实现替代的提示框布局
- 实现 VAE 的瓦片化 `Conv2d`
	- 降低内存占用；降低速度
		- 参见命令行参数
- 为 `Mask blur` 混合实现全精度计算
	- 在设置中启用 img2img
- 支持所有模型的 TAESD 实时预览
- 支持以 `half` 精度加载上采样器
	- 加快速度；降低质量
		- 在“设置/上采样”中启用
- 支持在 GPU 上运行图块合成
	- 在“设置/上采样”中启用
- 在“额外功能”选项卡中支持（短）视频
- 支持 `.heif`.avif`.jxl` 、 `  和  ` 图像格式
- 自动确定 `X/Y/Z Plot 的最佳行数`
- 更新 LLLite Controlnet
	- [SDXL](https://huggingface.co/kohya-ss/controlnet-lllite/tree/main) / [Anima](https://huggingface.co/kohya-ss/Anima-LLLite/tree/main)
- 支持联合 Controlnet
	- [SDXL](https://huggingface.co/xinsir/controlnet-union-sdxl-1.0) / [Chenkin](https://civitai.com/models/2527960/chenkin-unicontrol-xl)

#### 已移除的功能

- SD2
- SD3
- Forge 空间
- 超网络
- CLIP 审问器
- Deepbooru 审问器
- 文本反转训练
- 一些内置扩展
- 一些内置脚本
- 部分采样器与调度器
- 部分兼容性设置
- 隐蔽信息文本

#### 优化

- \[Comfy\] 重写后端（ `memory_management.py` 、 `ModelPatcher` 、 `attention.py` 等）
- 全新安装时不再 `clone` `git` 任何仓库
- 不再安装 `open-clip`
- 修复切换检查点时的内存泄漏问题
- 恢复将图像拖放到已包含图像的 `gr.Image` 上的功能
- 加快启动速度
- 改进计时器日志
- 移除未使用的 `cmd_args`
- 移除未使用的 `args_parser`
- 移除未使用的 `shared_options`
- 移除遗留代码
- 修复一些拼写错误
- 修复自动 `Tiled VAE` 回退问题
- 修复 SD1 和 SDXL 的 `Tiling`
- SDXL 的垫条件处理
- 移除重复的上采样器代码
- 更新 Spandrel
	- 支持新的上采样器架构

> [!important] Important
> 将所有上采样器（ `.pth` / `.safetensors` ）放入 `ESRGAN` 文件夹中

> [!tip] Tip
> 查看 OpenModelDB 以获取上采样器的位置

- 改进 `ForgeCanvas`
	- 画笔调整
		- 自定义
		- 去混淆
		- 橡皮擦
		- 快捷键
- 优化上采样器逻辑
- 优化 `Spandrel 的某些操作`
- 针对 `VAE 优化某些操作`
- 加速模型加载
- 改进内存管理
- 改进色彩校正
- 更新 `X/Y/Z Plot 的实现`
- 更新 `Soft Inpainting 的实现`
- 更新 `MultiDiffusion 的实现`
- 更新 `LCM` uni\_pc `  和  ` 采样器的实现
- 更新 LoRA 的实现
- 重构设置
	- 改进格式排版
		- 更新描述信息
- 并行检查扩展程序更新
- 将 `models` embeddings `  文件夹移至  ` 文件夹
- 信息文本重写
	- 允许切换模型和模块
		- 正确保存 `emphasis`
		- 修正默认值
- ControlNet 重写
	- 将单元更改为 `gr.Tab`
		- 移除多输入，因为它们已""
- 默认禁用 Refiner
	- 在“设置/细化器”中重新启用
- 不再默认安装 `bitsandbytes`
	- 请查看命令行参数
- 改进了对非 NVIDIA 显卡的支持
- Lint 与格式化
- 更新 `Pillow`
	- 更快的图像处理
- 更新 `protobuf`
	- 更快的 `insightface` 加载
- 更新至最新 PyTorch 版本
	- `torch==2.11.0+cu130`

> [!note] Note
> 如果您的 GPU 不支持最新版本的 PyTorch，请手动安装旧版 PyTorch

- 更新部分包至更新版本
- 将推荐的 Python 版本更新至 `3.13.12`
- 更多……™️

## 命令行

> 这些标志可以添加到 `webui-user.bat` 中的 `set COMMANDLINE_ARGS=` *行之后（在同一行；用空格分隔每个标志）*

> [!tip] Tip
> 使用 `python launch.py --help` 查看所有可用标志

- `--xformers` ：安装 `xformers` 包以加快生成速度

> [!warning] Warning
> `xformers` 不支持 `RTX 50s`

- `--port` ：指定要使用的服务器端口
	- 默认为 `7860`
- `--api` ：启用 API 访问

#### 作者：Neo

- `--cuda-malloc` ：改进内存分配
- `--cuda-stream` ：启用异步权重卸载
- `--pin-shared-memory` ：改进 RAM 利用率
- `--expandable-segments` ：启用实验性 PyTorch 内存分配器（可在某些平台上防止出现 `OutOfMemory` 错误）
- `--uv` ：将 `python -m pip` 调用替换为 `uv pip` ，以大幅加快包的安装速度
	- 需要先安装 uv（详见安装部分）
- `--uv-symlink` ：与上述相同；但还需将 `--link-mode symlink` 传递给命令
	- 显著减小安装体积（从 `~7 GB` 到 `~100 MB` ）

> [!important] Important
> 使用 `symlink` 意味着它将直接从缓存文件夹访问包；若使用此选项，请勿清除缓存

- `--model-ref` ：指向包含所有模型的中央 `models` 文件夹
	- 该文件夹应包含名为 `Stable-diffusion` 、 `Lora` 、 `VAE` 、 `ESRGAN` 等的子文件夹。

> [!important] Important
> 此操作将直接替换 `models` 文件夹，而非在其之上追加内容

- `--forge-ref-a1111-home` ：指向一个 Automatic1111 安装目录以加载其 `models` 文件夹
	- **即** `text_encoder` Stable-diffusion `  、  ` 等。
- `--forge-ref-comfy-home`: 指向一个 ComfyUI 安装目录以加载其 `models` 文件夹
	- **即** `clip` diffusion\_models `  、  ` 等。
- `--forge-ref-comfy-yaml`: 指向 ComfyUI `extra_model_paths.yaml` 以加载其配置
	- **即** `checkpoints` base\_path `  、  ` 等。
- `--sage` ：安装 `sageattention` 包以加快生成速度
	- 也将尝试自动安装 `triton`
- `--flash` ：安装 `flash_attn` 包以加快生成速度
- `--nunchaku` ：安装 `nunchaku` 包以推理 SVDQ 模型
- `--bnb` ：安装 `bitsandbytes` 包以进行低精度（ `nf4` ）推理
- `--onnxruntime-gpu` ：安装 `onnxruntime` 以获得最新的 GPU 支持
- `--fast-fp8` ：当模型类型为 `float8_e4m3fn` 时，请使用 `torch._scaled_mm 功能`
- `--fast-fp16` ：启用 `allow_fp16_accumulation` 选项
- `--autotune` ：启用 `torch.backends.cudnn.benchmark` 选项
	- 根据我的经验，这会更慢……
- `--tiled-conv2d` ：将 `Conv2d` 操作替换为分块变体
	- 对 SD1 和 SDXL VAE 的缩减效果更显著；对 Wan VAE 的效果则较弱
		- `64` / `128` / `256` / `512`

## 安装

0. 安装 Git
1. 克隆仓库
	```bash
	git clone https://github.com/Haoming02/sd-webui-forge-classic sd-webui-forge-neo --branch neo
	```
2. 安装 Python
推荐方法
- 安装 uv
- 设置虚拟环境 (venv)
	```jboss
	cd sd-webui-forge-neo
	uv venv venv --python 3.13 --seed
	```
- 在 `webui-user.bat` 中添加 `--uv 标志`
已弃用的方法
- 安装 Python 3.13.12
	- 记得启用 `Add Python to PATH`
3. （可选）配置命令行参数
4. 通过 `webui-user.bat 启动 Web 界面`
5. 首次启动时，将自动安装所有依赖项
6. 安装完成后，WebUI 将在浏览器中自动启动

> [!tip] Tip
> - Linux 和 macOS 用户请参考 Wiki
> - Docker 用户（ `Nvidia` ）请参考 Docker

> [!tip] Tip
> 查看额外安装说明，了解如何安装 `git` 、 `uv` 和 `FFmpeg`

## 注意力函数

> [!important] Important
> `--xformers` 、 `--flash` 和 `--sage` 参数仅负责安装相关包，并不决定是否使用对应的注意力机制（这也意味着在成功安装完这些包后，您可以将它们移除）

> [!caution] Caution
> 请勿盲目地全部安装  
> 如今，原生 PyTorch `scaled_dot_product_attention` 的速度通常同样快，而且也更加稳定。

Forge Neo 会尝试导入这些包，并按照以下顺序自动选择第一个可用的注意力函数：

> [!note] Note
> 若要跳过特定的注意力机制，请添加相应的禁用参数，例如 `--disable-sage`

## 问题与建议

- 关于已移除功能的问题将被直接忽略
- 明显属于用户操作失误的问题将直接忽略
- 关于 AMD GPU 的问题将直接忽略
- 运行非官方模型的问题将直接忽略
	- 请勿随意下载每一个找到的微调版或量化版本
- 关于第三方扩展的问题将直接忽略
	- 扩展程序应适配用户界面，而非相反
- 由 StabilityMatrix 引起的问题将直接忽略
	- 仅当您在按照官方安装说明进行干净安装后仍能复现问题时，才提交 Issue

> [!caution] Caution
> - 如果您发布 NSFW 图片/视频，将立即被禁言
> 	- 最终决定权在我；如果您不确定，只需生成 `cats` 和 `dogs`...

---

> [!tip] Tip
> 查看 Wiki 和常见问题解答