---
title: "Stable Diffusion web UI"
source: "https://github.com/AUTOMATIC1111/stable-diffusion-webui"
author:
published:
created: 2026-05-19
description: "Stable Diffusion web UI. Contribute to AUTOMATIC1111/stable-diffusion-webui development by creating an account on GitHub."
tags:
  - "clippings"
taxonomy: { doc_category: [sd-webui] }
---
## Stable Diffusion web UI

这是一个使用 Gradio 库实现的 Stable Diffusion Web 界面。

[![](https://github.com/AUTOMATIC1111/stable-diffusion-webui/raw/master/screenshot.png)](https://github.com/AUTOMATIC1111/stable-diffusion-webui/blob/master/screenshot.png)

## 功能

带有图片的详细功能展示：

- 原始 txt2img 和 img2img 模式
- 一键安装并运行脚本（但仍需安装 Python 和 Git）
- 外绘
- 内绘
- 色彩素描
- 提示词矩阵
- Stable Diffusion 放大
- 注意，指定模型应更加关注的文本部分
	- 穿着 `((tuxedo))` 西装的男子 - 将更关注燕尾服
		- 穿着 `(tuxedo:1.21)` 西装的男子 - 替代语法
		- 选中文本并按下 `Ctrl+Up` 或 `Ctrl+Down` （若您在 MacOS 上，则按 `Command+Up` 或 `Command+Down` ）以自动调整对选定文本的关注度（代码由匿名用户贡献）
- 循环处理，多次运行 img2img
- X/Y/Z 图，一种绘制具有不同参数的图像三维图的方法
- 文本反转
	- 可以拥有任意数量的嵌入，并使用您喜欢的任何名称来命名它们
		- 使用多个嵌入，每个标记具有不同数量的向量
		- 支持半精度浮点数运算
		- 在 8GB 显存上训练嵌入模型（也有 6GB 显存的报告）
- 包含以下内容的“额外”选项卡：
	- GFPGAN，用于修复人脸的神经网络
		- CodeFormer，作为 GFPGAN 的替代方案的人脸修复工具
		- RealESRGAN，神经网络上采样器
		- ESRGAN，拥有大量第三方模型的神经网络上采样器
		- SwinIR 和 Swin2SR（），神经网络上采样器
		- LDSR，潜在扩散超分辨率上采样
- 调整宽高比选项
- 采样方法选择
	- 调整采样器 eta 值（噪声乘数）
		- 更高级的噪声设置选项
- 随时中断处理过程
- 支持 4GB 显存的显卡（也有 2GB 显卡可用的报告）
- 批量作业的种子数正确性验证
- 实时提示词标记长度校验
- 生成参数
	- 用于生成图像的参数将随该图像一同保存
		- PNG 格式存储于 PNG 分块中，JPEG 格式存储于 EXIF 信息内
		- 可以将图像拖拽至 PNG 信息标签页以恢复生成参数，并自动将其复制到界面中
		- 可在设置中禁用
		- 将图像或文本参数拖放到提示框中
- 读取生成参数按钮，将提示框中的参数加载到界面中
- 设置页面
- 从界面运行任意 Python 代码（必须使用 `--allow-code` 启用）
- 为大多数界面元素提供鼠标悬停提示
- 可通过文本配置文件更改界面元素的默认值/混合值/最大值/步长值
- 支持平铺功能，包含一个复选框以创建可像纹理一样平铺的图像
- 进度条与实时图像生成预览
	- 可使用独立的神经网络以几乎零显存或计算需求生成预览图
- 负面提示词，一个额外的文本字段，允许您列出在生成图像中不希望看到的内容。
- 风格，一种保存部分提示词并通过下拉菜单轻松应用它们的方法。
- 变体，一种生成相同但略有差异的图像的方法。
- 种子重缩放，一种生成相同但分辨率略有不同的图像的方法
- CLIP 查询器，一个尝试从图像中猜测提示词的按钮
- 提示编辑，一种在生成过程中修改提示词的方法，例如开始绘制西瓜，中途切换为动漫少女。
- 批量处理，使用 img2img 处理一组文件。
- Img2img 替代方案，反向欧拉法的交叉注意力控制方法。
- 高清修复，一个便捷选项，可一键生成高分辨率图片，且无常规失真
- 重新加载检查点（实时）
- 检查点合并器，一个允许将最多 3 个检查点合并为一个的选项卡
- 带有许多社区扩展的自定义脚本
- 可组合扩散（Composable-Diffusion），一种同时使用多个提示词的方法
	- 使用大写 `AND 分隔提示词`
		- 同时也支持提示词的权重： `a cat :1.2 AND a dog AND a penguin :2.2`
- 提示词无标记数量限制（原始 Stable Diffusion 最多允许使用 75 个标记）
- 集成 DeepDanbooru，为动漫风格提示词生成 Danbooru 风格的标签
- xformers，为特定显卡大幅提升速度：(在命令行参数中添加 `--xformers` )
- 通过扩展程序：历史记录标签页：在界面内方便地查看、直接删除图像
- 生成无限选项
- 训练标签页
	- 超网络与嵌入选项
		- 图像预处理：裁剪、镜像，使用 BLIP 或 deepdanbooru 进行自动标签（适用于动漫）
- Clip skip
- 超网络
- Lora（与超网络类似，但效果更佳）
- 一个独立的界面，您可以在其中选择要添加到提示词中的嵌入模型、超网络或 Lora，并支持预览功能
- 可从设置屏幕中选择加载不同的 VAE
- 进度条中显示预估完成时间
- API
- 支持 RunwayML 专用的重绘模型
- 通过扩展：Aesthetic Gradients，利用 CLIP 图像嵌入生成具有特定美学风格的图像（实现 [https://github.com/vicgalle/stable-diffusion-aesthetic-gradients）](https://github.com/vicgalle/stable-diffusion-aesthetic-gradients）)
- Stable Diffusion 2.0 支持 - 请参阅 Wiki 获取操作说明
- Alt-Diffusion 支持 - 请查看 wiki 获取操作说明
- 现在不再出现任何不良字符！
- 加载 safetensors 格式的检视点
- 放宽分辨率限制：生成图像的维度必须是 8 的倍数，而非 64
- 现在附带许可证！
- 从设置界面重新排列 UI 元素
- 支持 Segmind Stable Diffusion

## 安装与运行

确保满足所需的依赖项，并遵循以下说明：

- NVIDIA（推荐）
- AMD GPU。
- Intel CPU、Intel GPU（包括集成和独立显卡）（外部 Wiki 页面）
- 昇腾 NPU（外部 Wiki 页面）

或者，使用在线服务（如 Google Colab）：

- [在线服务列表](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Online-Services)

### 在 Windows 10/11 上使用 NVIDIA GPU 安装发布版

1. 下载 v1.0.0-pre 版本的 `sd.webui.zip` 并解压其内容。
2. 运行 `update.bat` 。
3. 运行 `run.bat` 。

> 更多详细信息请参见 Install-and-Run-on-NVidia-GPUs

### Windows 自动安装

1. 安装 Python 3.10.6（新版 Python 不支持 torch），并勾选“将 Python 添加到 PATH"。
2. 安装 git。
3. 下载 stable-diffusion-webui 仓库，例如通过运行 `git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui.git` 。
4. 通过 Windows 资源管理器以普通用户（非管理员）身份运行 `webui-user.bat` 。

### Linux 自动安装

1. 安装依赖项：
```bash
# Debian-based:
sudo apt install wget git python3 python3-venv libgl1 libglib2.0-0
# Red Hat-based:
sudo dnf install wget git python3 gperftools-libs libglvnd-glx
# openSUSE-based:
sudo zypper install wget git python3 libtcmalloc4 libglvnd
# Arch-based:
sudo pacman -S wget git python3
```

如果您的系统非常新，需要安装 python3.11 或 python3.10：

```bash
# Ubuntu 24.04
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt update
sudo apt install python3.11

# Manjaro/Arch
sudo pacman -S yay
yay -S python311 # do not confuse with python3.11 package

# Only for 3.11
# Then set up env variable in launch script
export python_cmd="python3.11"
# or in webui-user.sh
python_cmd="python3.11"
```
2. 导航到您希望安装 Web UI 的目录，并执行以下命令：
```awk
wget -q https://raw.githubusercontent.com/AUTOMATIC1111/stable-diffusion-webui/master/webui.sh
```

或者直接在您想要的任何位置克隆该仓库：

```bash
git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui
```
3. 运行 `webui.sh` 。
4. 检查 `webui-user.sh` 中的选项。

### 在 Apple 芯片上的安装

请在此处查找相关说明。

## 贡献代码

以下是向此仓库添加代码的方法：贡献指南

## 文档

文档已从本 README 迁移至项目维基。

为了让 Google 和其他搜索引擎能够抓取维基内容，此处提供（非供人类访问）可被抓取的维基链接。

## 致谢

借用代码的许可证可在 `Settings -> Licenses` 屏幕和 `html/licenses.html` 文件中找到。

- Stable Diffusion - [https://github.com/Stability-AI/stablediffusion](https://github.com/Stability-AI/stablediffusion), [https://github.com/CompVis/taming-transformers](https://github.com/CompVis/taming-transformers), [https://github.com/mcmonkey4eva/sd3-ref](https://github.com/mcmonkey4eva/sd3-ref)
- k-diffusion - [https://github.com/crowsonkb/k-diffusion.git](https://github.com/crowsonkb/k-diffusion.git)
- Spandrel - [https://github.com/chaiNNer-org/spandrel](https://github.com/chaiNNer-org/spandrel) 实现
	- GFPGAN - [https://github.com/TencentARC/GFPGAN.git](https://github.com/TencentARC/GFPGAN.git)
		- CodeFormer - [https://github.com/sczhou/CodeFormer](https://github.com/sczhou/CodeFormer)
		- ESRGAN - [https://github.com/xinntao/ESRGAN](https://github.com/xinntao/ESRGAN)
		- SwinIR - [https://github.com/JingyunLiang/SwinIR](https://github.com/JingyunLiang/SwinIR)
		- Swin2SR - [https://github.com/mv-lab/swin2sr](https://github.com/mv-lab/swin2sr)
- LDSR - [https://github.com/Hafiidz/latent-diffusion](https://github.com/Hafiidz/latent-diffusion)
- MiDaS - [https://github.com/isl-org/MiDaS](https://github.com/isl-org/MiDaS)
- 优化思路 - [https://github.com/basujindal/stable-diffusion](https://github.com/basujindal/stable-diffusion)
- 交叉注意力层优化 - Doggettx - [https://github.com/Doggettx/stable-diffusion，提示编辑的原始创意。](https://github.com/Doggettx/stable-diffusion，提示编辑的原始创意。)
- 交叉注意力层优化 - InvokeAI, lstein - [https://github.com/invoke-ai/InvokeAI（最初为](https://github.com/invoke-ai/InvokeAI（最初为) [http://github.com/lstein/stable-diffusion）](http://github.com/lstein/stable-diffusion）)
- 亚二次方交叉注意力层优化 - Alex Birch ( [Birch-san/diffusers#1](https://github.com/Birch-san/diffusers/pull/1) )，Amin Rezaei ( [https://github.com/AminRezaei0x443/memory-efficient-attention](https://github.com/AminRezaei0x443/memory-efficient-attention))
- 文本反转 - Rinon Gal - [https://github.com/rinongal/textual\_inversion（我们未使用其代码，但采用了其理念）。](https://github.com/rinongal/textual_inversion（我们未使用其代码，但采用了其理念）。)
- 关于 SD upscale 的构想 - [https://github.com/jquesnelle/txt2imghd](https://github.com/jquesnelle/txt2imghd)
- 用于外绘制的噪声生成 mk2 - [https://github.com/parlance-zz/g-diffuser-bot](https://github.com/parlance-zz/g-diffuser-bot)
- CLIP 查询器构想及借用部分代码 - [https://github.com/pharmapsychotic/clip-interrogator](https://github.com/pharmapsychotic/clip-interrogator)
- 关于可组合扩散的构想 - [https://github.com/energy-based-model/Compositional-Visual-Generation-with-Composable-Diffusion-Models-PyTorch](https://github.com/energy-based-model/Compositional-Visual-Generation-with-Composable-Diffusion-Models-PyTorch)
- xformers - [https://github.com/facebookresearch/xformers](https://github.com/facebookresearch/xformers)
- DeepDanbooru - 动漫扩散模型的询问器 [https://github.com/KichangKim/DeepDanbooru](https://github.com/KichangKim/DeepDanbooru)
- 使用 float32 精度从 float16 UNet 进行采样 - marunine 提供思路，Birch-san 提供示例 Diffusers 实现（[https://github.com/Birch-san/diffusers-play/tree/92feee6）](https://github.com/Birch-san/diffusers-play/tree/92feee6）)
- Instruct pix2pix - Tim Brooks (星标), Aleksander Holynski (星标), Alexei A. Efros (无星标) - [https://github.com/timothybrooks/instruct-pix2pix](https://github.com/timothybrooks/instruct-pix2pix)
- 安全建议 - RyotaK
- UniPC 采样器 - Wenliang Zhao - [https://github.com/wl-zhao/UniPC](https://github.com/wl-zhao/UniPC)
- TAESD - Ollin Boer Bohan - [https://github.com/madebyollin/taesd](https://github.com/madebyollin/taesd)
- LyCORIS - KohakuBlueleaf
- 重启采样 - lambertae - [https://github.com/Newbeeer/diffusion\_restart\_sampling](https://github.com/Newbeeer/diffusion_restart_sampling)
- Hypertile - tfernd - [https://github.com/tfernd/HyperTile](https://github.com/tfernd/HyperTile)
- 初始 Gradio 脚本——由 4chan 上的匿名用户发布。感谢这位匿名用户。