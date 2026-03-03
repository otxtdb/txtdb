---
title: "deepbeepmeep/Wan2GP"
source: "https://github.com/deepbeepmeep/Wan2GP/tree/main"
author:
  - "[[deepbeepmeep]]"
published:
created: 2026-02-27
description: "A fast AI Video Generator for the GPU Poor. Supports Wan 2.1/2.2, Qwen Image, Hunyuan Video, LTX  Video and Flux. - deepbeepmeep/Wan2GP"
tags:
  - "clippings"
taxonomy: { doc_category: [wan2gp] }
---
---

**DeepBeepMeep 的 WanGP：最适合 GPU 资源有限的用户的最佳开源视频生成模型**

WanGP 支持 Wan（及其衍生模型），同时也支持 Hunyuan 视频、Flux、Qwen、Z-图像、LongCat、Kandinsky、LTXV、LTX-2、Qwen3 语音合成、Chatterbox、HearMula、...等：

- 低 VRAM 需求（某些模型仅需 6 GB VRAM 即可）
- 支持老旧 Nvidia 显卡（RTX 10XX、20xx、...）
- 支持 AMD GPU（RDNA 4、3、3.5 和 2），安装部分下有说明。
- 在最新 GPU 上非常快
- 易于使用 全网页界面
- 支持多种检查点量化格式：int8、fp8、gguf、NV FP4、Nunchaku
- 自动下载适配您特定架构的所需模型
- 集成工具以促进视频生成：蒙版编辑器、提示增强器、时序与空间生成、MMAudio、视频浏览器、姿态/深度/流提取器、动作设计师
- 许多现成的插件：图库浏览器、图像增强器、模型/检查点管理器、CivitAI 浏览器和下载器，...
- Loras 支持自定义每个模型
- 排队系统：将您要生成的视频加入购物清单稍后再来
- 无头模式：使用命令行启动多个图像/视频/音频文件的生成

**加入 Discord 服务器，从 WanGP 社区获取帮助并展示你的最佳生成作品：** [https://discord.gg/g7efUW9jGV](https://discord.gg/g7efUW9jGV)

**关注 DeepBeepMeep 的 Twitter/X 获取最新消息** : [https://x.com/deepbeepmeep](https://x.com/deepbeepmeep)

## 📋 目录
- [🚀 快速入门](https://github.com/deepbeepmeep/Wan2GP/tree/#-quick-start)
- [📦 安装](https://github.com/deepbeepmeep/Wan2GP/tree/#-installation)
- [🎯 使用方法](https://github.com/deepbeepmeep/Wan2GP/tree/#-usage)
- [📚 文档](https://github.com/deepbeepmeep/Wan2GP/tree/#-documentation)
- [🔗 相关项目](https://github.com/deepbeepmeep/Wan2GP/tree/#-related-projects)

## 🔥 最新更新 :### 2026 年 2 月 19 日：WanGP v10.951，突破音障，马赫 2这是 WanGP 的*文本转语音*功能中（最后一个？）缺失的部分： **情感**

目前市面上能让您表达情感的 TTS 模型并不多，因此我希望您能原谅我在 WanGP 中加入了一个旧的 TTS 模型（已有 6 个月历史！）：**Index TTS 2**。

但在 WanGP 中，您将不会只获得 Index TTS 的普通版本：

- *两个说话者对话* （自带 2 个克隆声音）
- 每个说话者可以在同一个提示中表达 *多种情绪*
- *两个说话者声音的音量标准化* （没有人会说得更大声）
- 针对 *可以永远持续的对话* 进行优化（新的 *infinitalk* 最佳朋友）
- *GPU Poor 版本* : VRAM，6GB 就足够
- 使用 *vllm* 与 *Cuda 图加速*高度优化：比 vanilla Index TTS 快 *10 倍* 。在高端 GPU 上，生成 1 分钟的对话只需 30 秒！

使用方法如下：默认情况下，Index TTS 会根据文本内容自动检测并应用于文本提示的情绪。但它会对整个提示应用相同情绪。若想每句话使用不同情绪，只需在每句话之间插入空行。

你也可以通过\[\]标签手动设置期望的情绪，这里是一个单角色的示例：

\[fear\] At the very beginning I was so afraid to speak.
\[sadness\] Nobody would talk to me. I felt so alone.
\[disgust\] They would just ignore me and pretend that I didnt exist
\[happy\] By chance I discovered this wonderful App, and now everything is different.
\[anger\] I have a new voice and now everybody will have no choice but to listen to my words !!! 

你可以混合情绪 *\[悲伤,厌恶\]*，或者如果你想要精确指定一个或多个情绪的权重 *\[悲伤=0.7,厌恶\]*（在任何情况下权重的总和为 1）

请记住，双声道模式需要插入 *"说话者 1:"* & *"说话者 2:"* 来指示谁在说话。

只有一个问题：索引 TTS 2 仅支持英语和中文。但别慌！并非一切都已失去。有一个解决方法：

1. 将 *索引 TTS 2* 输入要克隆的声音，并要求它生成带有你期望情绪的英文语音样本
2. 现在请让 *Qwen3TTS* 复制这个新生成的英语语音样本到您想要的其他语言

### 2026 年 2 月 16 日：WanGP v10.9，打破音障通过这个新版本的 WanGP，您将获得最佳的 TTS（文本转语音）体验：

- **Qwen3 TTS 加速升级** ：
	- 使用新的 *Cuda 图* 优化模式，语音生成速度最高可达 *4 倍* 加快，在某些情况下生成 1 秒语音可能只需不到 1 秒！
	- 使用 int8 量化，Qwen3 TTS 只需 6 GB 显存即可全速运行
	- 新增 **双声道模式** ，支持 **双克隆语音** ，生成的对话比使用 *Kugel 音频 时过渡更平滑*
- **Heart Mula 升级** ：
	- 使用新的 *Cuda 图* 优化模式，歌曲生成速度提升高达 6 倍
- **Ace Step 1.5 升级增强** :
	- WanGP 版本为 *vllm* 和 *int8 量化*提供专属支持，用于语言模型（即同时实现快速语言模型和低 VRAM 占用）
	- 你只需要 10GB 的 RAM 和 6GB 的 VRAM，就能运行 Ace Step 的所有功能

此外，现在您可以选择多种 *Prompt Enhancements* 用于 *Qwen3 TTS* & *Kugel Audio*：*Prompt Enhancer* 现在可以为您生成 *独白* 或 *两个说话者之间的对话*

  
请注意，要使用新的 *Cuda Graph* 模式，您需要在 *Configuration / Performance / Language Models Decoder Engine* 中选择 *vllm* 或 *cuda graph*。相应的模型需要启用配置文件 1、3 或 3+。vllm 是 cuda graph 的增强版本，可能不适用于所有显卡。但如果您的显卡不支持，将自动回退到 cuda graph。

### 2026 年 2 月 12 日：WanGP v10.84，Easy Metal- **Ace Step 1.5 Turbo Super Charged**：所有 *Ace Step 1.5* 的最佳功能现在都在 *WanGP* 中，并且是 *快速* & *易于使用* ：
	- 手动选择 *Bpm*、*Keyscale*、*Time Signature* & *Language*
	- 使用 *LM* 自动检测最适合您 *Lyrics* 的 *Bpm*、*Keyscale*、*Time Signature* & *Language*
	- 使用 *LM* 优化 *Music Caption* 或自动检测 *Song Duration*
	- 选择 *vllm* 引擎用于 *LM*，可高达 *10 倍* 更快的 *LM* 生成速度！！！。此外，作为 WanGP 的独家功能，*vllm* 提供 *INT8 量化* 格式，以降低 VRAM 需求。请注意，您需要安装 *Triton* 和 *Flash Attention 2*（请查看 INSTALLATION.Md 以获取简易安装方法）
	- 使用 *LM* 来优化 *音乐描述* （通常这是获得你期望的歌曲主题的关键）
	- UI 改造以更好地匹配原 Ace Step 应用中使用的词汇（但无需其复杂性...)
	- 在 *提示增强器* 中使用的优化 *系统提示* 来生成 *歌词* （我推荐使用 *LLama Joy 提示增强器* ）
- **LoKr 支持** ：这种类似 "Lora" 的格式已与 *Flux Klein 9B 进行过测试*
- **优化的 Int8 内核** ：所有与 WanGP 一起使用的 *量化的 INT8 检查点* （大多数量化的检查点）现在应该 *快了 10% !!!*。您需要安装 *Triton*。这是实验性的，所以目前需要在 *配置 / 性能* 选项卡中手动启用。请在 *discord* 上分享您的反馈，并提及您的 GPU，以便我知道它是否正常工作。
- **生成错误时自动保存队列** ：如果您在生成过程中遇到任何错误，队列现在将自动保存。因此您可以稍后尝试这个队列（使用不同的配置或当相关错误被修复时，如果有的话 ...）。
- **UI 更新** （谢谢 *Tophness!*）：将 *自检定器 UI* 更新为动态的、基于滑块的界面（不再需要手动文本输入）。改进了队列重新排序：在重新排序队列时，项目现在可以直接拖放到 Top 和 Bottom 按钮上，以便在滚动条自动吸附到顶部和底部。
- **Kugel 音频音频分割** : Kugel 音频是一个很棒的模型，但奇怪的是它倾向于在长篇演讲中加速。为了避免这种效果，我们需要分割音频演讲。你可以手动插入一个 *空行* 来完成，或者通过指定一个 *自动音频分割时长* （不用担心 WanGP 会尝试在行或句子之间进行分割）。

*更新 10.81*: 修复  
*更新 10.82*: UI 更新  
*更新 10.83*: Kugel 音频分割  
*更新 10.84*: Ace Step RAM 优化（修复内存泄漏并减少 RAM 需求）

**RTX 50xx 用户注意** : 您需要升级到 *pytorch 2.10*（见下方升级步骤）才能使用 *Triton*

### 2026 年 2 月 4 日：WanGP v10.70，准备就绪，即将开始！*开源与闭源的竞争从未如此激烈！*

- **Ace Step 1.5 Turbo**：这个长期期待的开放源码项目声称已经超越了 *Suno 5*。它允许你生成高质量的多分钟歌曲。它有四种版本：*Vanilla*（无语言模型预处理， **生成时间只需 4 秒！！！**）& *3 级 LM 预处理* ，以获得更高质量（但会增加 VRAM 需求）

请注意，在使用 *Ace Step LM* 变体时，由于语言模型是*自回归模型* ，可能会在*内存配置文件 2 或 4* 上变得非常慢。这就是为什么我建议坚持使用*内存配置文件 1/3/3+*，除非你的 VRAM 非常少。

- **Kugel Audio 0**：另一个具有*语音克隆*功能的*语音合成* ，这个版本声称优于 *ElevenLabs*！！！Kugel Audio 的亮点在于它可以用两个克隆的语音创建对话。祝你玩得开心！

Kugel Audio 完全是*自回归模型* ，并且非常消耗 VRAM。所以要么你有 16GB VRAM，可以用*内存配置文件 1/3/3+* 运行它，要么你将不得不使用其他配置文件以较慢的方式运行。

- **LTX-2 自我优化器** ：WanGP 独有的 *自我优化器* 已添加到 *精炼/非精炼* 模型中，希望这将提升我们视频生成器的质量。

### 2026 年 2 月 1 日：WanGP v10.61，升级时间！- **LTX-2 基础优化** ：如果你觉得基础模型速度过快，新增了 *质量* 功能：
	- 新的 *模态引导* 应根据 *LTX-2 团队* 的说法，改善音频/视频（口型同步等），（注意：使用时初始 *去噪阶段* 将会慢 50%，前提是模态引导> 1）
	- *CFG 星* , *自适应项目指导* 应提高质量并更好地遵循提示
	- *跳过层指导* ：在阶段中跳过第 29 层可能会或可能不会提高质量 注意这些功能仅在去噪的第一阶段被触发 因为第二阶段是蒸馏去噪（无论在非蒸馏模型上如何）
- **Flux Klein 4B & 9B 基础模型** ：*Z 图像* 在 WanGP 中有其*基础模型* ，所以 *Flux Klein* 也有其基础模型是公平的。基础模型需要更多步骤（增加 50）和指导 > 1 但它们是微调的良好起点

  
这次新发布的真正创新之处在于它已经过测试和调优，可以与更新的版本 *Python、Pytorch & Cuda* 一起使用。我的最终目标是让所有人都升级到 **Python 3.11、Pytorch 2.10、Cuda 13/13.1**。一旦我们都升级完成，提供 *Nunchaku**NVPF4*、*Sage Attention*、*Flash Attention* 等预编译内核就会变得容易得多。因此，请按照*以下手动升级说明* （目前没有 Pinokio 自动升级）进行操作，并在 Discord 上告诉我它是否适用于所有代 GPU（从 GTX10xx 到 RTX50xx）。你可以在 **guides/INSTALLATION.md** 中找到适用于这个新设置的内核。

- **Wan Motion Self Refiner**：您需要感谢 **Steve Jabz**（*Tophness*）为这个功能，因为他一直是 Self Refiner 的主要赞助者，并进行了深入研究向我展示了它的优点。\*\*Self Refiner\*\* 应该会提高运动质量（在 *Quality Tab* 中找到）。它依赖于一个 *Refiner Plan*，该计划指示哪些步骤需要被优化，例如："2-5:3"（默认计划非常适合 *light2xv* 4 步骤）意味着步骤 2-3 将被优化 3 次（也就是说，每个步骤将进行 3 次去噪尝试，因此如果使用 Self Refiner，生成速度将提高 3 倍）。目前，\*\*Self Refiner\*\* 仅在 Wan t2v & i2v 上启用。如果您对其满意，我们将支持更多模型。

**请注意，PyTorch 2.10 至少代表了一次不错的升级，切换模型时没有内存泄漏（pytorch 2.8），并且 VAE 解码时性能不佳/VRAM 峰值（pytorch 2.9）。**

*更新* ：似乎 GTX10xx 不支持 Cuda 13.0。别担心，我将保持 WanGP 与 Pytorch 2.7.1 / Cuda 12.8 的兼容性。  
*更新 10.61*：增加了 Self Refiner

### 2026 年 1 月 29 日：WanGP v10.56，为你的心奏响音乐  
WanGP 特别版语音合成 （Text To Speech）发布：

- **心之歌** ：*Suno* 品质的歌曲，歌词在你的本地电脑上。你可以生成长达 4 分钟的音乐。
- **王牌步调 v1**：在等待即将发布的王牌步调 v1.5（预计很快就会发布）期间，先享用这个老歌（2025 年！）但依旧精彩的歌生成器作为开胃菜。王牌步调 v1 是一个非常快速的歌生成器。它基于扩散技术，所以不要犹豫开启配置文件 4，以 4B VRAM 的低配置保持快速运行。
- **Qwen 3 TTS**: 你可以选择进行 *声音克隆* 、 *根据提示生成自定义声音* 或使用 *预定义声音*
- **TTS 功能** :
	- **早期停止** : 你可以在生成过程中随时中止，同时保留已生成的内容（仅适用于 *自回归模型* 的 TTS 模型，对于 *扩散模型* 的图像/视频生成无需询问）
	- **专业提示增强器** ：如果你在 Heart Mula 中输入提示 *"一首关于 AI 生成歌曲"*，*WanGP 提示增强器* 将为你生成相应的杰作。类似地，在使用 Qwen3 TTS 或 ChatterBox 时，你也可以增强 "一篇关于 AI 生成演讲" 的提示。
	- **音频生成自定义输出文件夹** ：现在您可以选择不同的文件夹用于*音频输出*
	- **音频模型的默认内存配置** ：如果使用配置 4（作为自回归模型，它们需要逐层加载所有层来生成单个音频标记，然后重复此过程），TTS 模型可能会变得非常慢。另一方面，它们不需要那么多 VRAM，因此现在您可以定义一个更激进的配置（例如 3+）
- **Z 图像基础** ：如果您对 *Z 图像*热潮感兴趣，可以尝试它，但如果您不是研究人员或/或想基于它进行微调，它对您来说可能毫无用处。该模型需要 35 到 50 步（比 *Z 图像 turbo* 慢 4 倍到 6 倍），cfg > 1（额外慢 2 倍），并且没有*强化学习* ，因此输出图像不会那么好。优点是更高的多样性和*原生负面提示* （与使用 *NAG* 的 Z 图像虚拟负面提示相反）。

请注意，Z Image Base 对 *Attention Mode* 非常敏感：它不兼容 *Sage 1*，因为 Sage 1 会产生黑色帧。因此，我已经为 RTX 30xx 禁用了 Sage。此外，有报告称它在使用 *Sage 2 时会产生一些垂直条纹伪影。*

- **Flux 1/2 NAG** : *Flux 2 Klein* 是你的新最佳朋友，但你可能会想念 *Negative Prompts*，*NAG* 对蒸馏模型的支持将使你永远成为最佳拍档，因为 NAG 模拟了 Negative Prompts。
- **多项改进** ：
	- 视频/音频库现在支持删除在 WanGP 外生成的 gens
	- 为音频输出添加了 *MP3 支持*
	- *插件*中的*检查更新*按钮，可一目了然地查看是否有任何插件可以更新
	- *提示增强器*每次点击时都会生成不同的增强提示。您可以在配置选项卡中定义其生成参数（top k、温度）
	- 新 *Root Loras* 文件夹可以在配置选项卡中定义。如果你有多个 WanGP 实例或想将所有 LoRA 存储在不同的硬盘上，这会很有用
	- 在 *Misc* 选项卡中添加了新的设置 *Attention Mode Override*
	- 实验性功能：允许在 *Generation* 过程中更改 *Configuration*

*更新 10.51*：新的 Heart Mula 微调在遵循指令方面表现更好，TTS 模型的额外设置（cfg, top k），Rife v4  
*更新 10.52*: 更新了插件列表并添加了版本跟踪  
*更新 10.53*: 视频音频画廊现在支持删除  
*更新 10.54*: 添加了 Z 图像基础，改进了提示增强器，可配置的 loras 根目录  
*更新 10.55*: 在 RTX30xx 上阻止了 Sage 与 Z 图像，添加了覆盖注意力模式设置，允许在生成过程中更改配置  
*更新 10.56*: 为 Flux 1/2 和 Ace Step v1 添加了 NAG

### 2026 年 1 月 20 日：WanGP v10.43，省钱版*GPU 很贵，RAM 很贵，SSD 很贵，可惜我们现在生活在 GPU 和 RAM 都匮乏的时代。*

WanGP 再次来帮忙：

- **GGUF 支持** ：正如一些人所知，我不太喜欢这种格式，因为在使用图像/视频生成模型时我们无法获得任何速度提升（矩阵乘法仍在 16 位进行），显存节省不多，且质量不如 int8/fp8。不过 gguf 有一个优势：它占用的 RAM 和硬盘空间更少。所以享受 gguf 支持吧。我已为 LTX-2 添加了现成的 *Kijai gguf 微调* 。
- **模型管理插件** ：使用这个*插件*来识别每个*模型* / *微调*占用的空间，并删除不再使用的。尽量避免删除共享文件，否则它们将被重新下载。
- **LTX-2 双重视频与音频控制** ：如果你还想使用*控制视频*的音频轨道来驱动视频生成，则不再需要提取音频轨道。新模式将允许你同时使用视频控制中的运动和音频。
- **LTX-2 - 自定义 VAE URL**: 一些用户询问是否可以使用旧的 *Distiller VAE* 而不是新的。要实现这一点，基于现有的模型定义创建一个 *finetune* 定义，并将其保存在 *finetunes/* 文件夹中，使用此条目（请查看 *docs/FINETUNES.md* 文档）：

```
"VAE_URLs": ["https://huggingface.co/DeepBeepMeep/LTX-2/resolve/main/ltx-2-19b_vae_old.safetensors"]
```

- **Flux 2 Klein 4B & 9B**：尝试这些蒸馏模型，速度与 Z\_Image 一样快甚至更快，但具有开箱即用的图像编辑功能
- **Flux 2 & Qwen Outpainting + Lanpaint**: 这些模型的 inpaint 模式现在支持 outpainting + 与 Lanpaint 有更多组合可能
- **多分钟视频的 RAM 优化** : 处理、保存、空间和时间上采样非常长的视频应该需要更少的 RAM。
- **文本编码器缓存** : 如果你询问一个最近已使用当前模型的文本提示，它将直接从缓存中获取。缓存经过优化以消耗较少的 RAM。它不适用于某些模型，例如 Qwen，其中文本提示在内部与图像组合。

*更新 10.41*: 添加了 Flux 2 klein  
*更新 10.42*: 添加了 RAM 优化 & 文本编码器缓存  
*更新 10.43*: 添加了 Qwen & Flux 2 的扩展绘制功能，以及 Flux 2 的 Lanpaint 功能

### 2026 年 1 月 15 日：WanGP v10.30，速度至上...- **LTX 精炼 VAE 升级** : *Kijai* 发现精炼 VAE 生成的图像清晰度不如非精炼模型的 VAE。我借此机会重新打包了所有 LTX-2 检查点，并减少了它们的整体高清占用空间，因为它们都共享约 5GB。

  
**如果旧检查点被删除并下载新检查点，那就不要惊讶了！！！**

- **LTX-2 多遍 Loras 乘数** ： *LTX-2* 现在支持依赖于遍数的 Loras 乘数。例如 "1;0.5" 表示 1 是第一个 LTX-2 遍数的强度，0.5 是第二个遍数的强度。
- **新配置 3.5**：这是 *配置 3* & *配置 5* 的遗失孩子，你拥有大量的 VRAM，但 RAM 很少？配置 3.5 将成为你的新朋友，因为它将不再使用保留 RAM 来加速传输。只有当你能在 VRAM 中完全容纳一个 *扩散 / Transformer* 模型时，才使用配置 3.5，否则生成速度可能会慢很多。
- **LTX-2 & Flux 2 的 NVFP4 量化** ：你现在将能够加载 *NV FP4* 模型检查点。在最近添加的 *Wan NV4* 之上，我们现在支持 *LTX-2 (非蒸馏)* & *Flux 2*。NV FP4 使用略少的 VRAM，且 RAM 最多减少 30%。

要完全享受 NV FP4 检查点（ **生成速度至少快 30%**），你需要一台 RTX 50xx 显卡，并升级到 *Pytorch 2.9.1 / Cuda 13*，同时使用最新版本的 *lightx2v 内核* （请查看 *docs/INSTALLATION.md*）。要观察到速度提升，你必须确保工作负载相当高（高分辨率、长视频）。

### 2026 年 1 月 13 日：WanGP v10.24，当 VRAM 用完时，仍然还有一些 VRAM...- **LTX-2 - 超级 VRAM 优化**

*使用 WanGP 10.21，720p 高清视频生成仅需 8GB VRAM！*

LTX 团队表示这个视频生成是为 4K 设计的。因此我不得不通过进一步优化来压缩更多 VRAM。

经过很多努力，我成功将 LTX-2 的 VRAM 需求降低了至少 1/3，这意味着：

- 10 秒 720p 只需 8GB VRAM
- 10 秒 1080p 只需 12GB VRAM
- 20 秒 1080p 只需 16GB VRAM
- 全高清 4k（3840 x 2176 !!!）使用 24 GB 显存的 10 秒。但坏消息是 LTX-2 视频不适合 4K，因为 4K 输出可能会让您噩梦连连...

3K/4K 分辨率仅在您在*配置* / *常规*选项卡中启用时可用。

- **Ic Loras 支持** ：使用*控制视频*传输*姿态* 、 *深度* 、*Canny 边缘* 。我增加了一些额外调整：使用 WanGP 可以将传输限制在*掩码区域* ，定义*去噪强度* （控制视频将遵循的程度）和*掩码强度* （未掩码区域受影响程度）
- **起始图像强度** ：此新滑块将出现在*起始图像*或源*视频*下方。如果您将其设置为低于 1 的值，则可以减少静态图像效果，有时在使用 LTX-2 i2v 时会遇到这种情况
- **为 LTX-2 的自定义 Gemma 文本编码器** ：作为一个实际案例， *异端*文本编码器现在由 WanGP 支持。查看*微调*文档，但简而言之，创建一个*微调* ，它具有一个包含一个或多个文件路径或 URL 列表的 *text\_encoder\_URLS* 键。
- **实验性自动恢复失败 Lora 引脚** ：一些用户（通常使用 RAM 小于 64 GB 的 PC）报告在启动带有 Loras 的生成时出现内存不足，尽管模型似乎加载正常。这有时与 WanGP 尝试（但因预留 RAM 不足而失败）将 Loras 固定到预留内存以加快生成有关。我尝试了一种恢复模式，该模式应释放足够的资源以继续视频生成。这可能解决与 *LTX-2 默认（非蒸馏） 相关的内存不足崩溃问题。*
- **最大 Loras 固定滑块** ：如果自动恢复模式仍不足够，我在 *配置* / *性能* 选项卡底部添加了一个滑块，您可以使用它来阻止 WanGP 固定 Loras（要这样做，请将其设置为 0）。如果没有加载尝试，就不会有崩溃...

*更新 10.21*: 添加了滑块 Loras 最大固定滑块  
*更新 10.22*: 添加了对自定义 LTX-2 文本编码器的支持 + 如果 Lora Pinning 失败则自动恢复模式  
*更新 10.23*: 修复了在配置文件 1 & 2 中忽略文本提示的问题（这会导致生成随机输出视频）

### 2026 年 1 月 9 日：WanGP v10.11，再次被破坏- **LTX-2**: 这里是期待已久的 *Ovi Challenger*，LTX-2 可以生成视频和音频音轨。一如既往，这个 WanGP 版本具有 *低 VRAM* 特性。你应该能够用 10 GB 的 VRAM 来运行它。如果你有至少 24 GB 的 VRAM，你将能够在单个窗口中仅用 2 分钟，使用精简模型生成 20 秒的 720p 视频。WanGP LTX-2 版本支持第一天就有的 *开始/结束关键帧* 、 *滑动窗口* / *视频延续* 和 *生成预览* 。包中包含一个 *LTX-2 精简* 版本，以实现非常快速的生成。

使用 WanGP v10.11，你现在可以强制设置你的音轨，它的工作方式类似于 *Multitalk* / *Avatar*，但在理论上，它应该适用于任何类型的音频（而不仅仅是人声）。感谢 *Kijai* 展示了这是可能的。

- **Z 图像双文件夹加速** ：Z 图像更快，因为这个变体可以仅用 1 步（推荐 3 步）生成图像。
- **Qwen 画中画** ：非常精确的 *画中画* ，提供更好的嵌入区域与图像其他部分的整合。注意它可能慢 5 倍，因为它在“搜索”最佳替换。
- **优化后的 Pytorch 编译器** : *耐心是美德之母* 。我终于（或者可能没有）修复了与 Wan 模型相关的 PyTorch 编译器问题。它应该能在更多样化的情况下工作，并且所需时间大大减少。
- **LongCat Video**: 实验性支持，包括 *LongCat Avatar* 一个会说话的头部模型。目前它主要适用于模型收藏者，因为它非常慢。它需要 40+ 步，每步包含高达 3 次的遍历。
- **MMaudio NSFW**: 用于替代音频背景


*更新 v10.11*: LTX-2，使用您自己的音轨

查看完整变更日志: **[变更日志](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/CHANGELOG.md)**

## 🚀 快速入门
**一键安装：** 立即使用 [Pinokio App](https://pinokio.computer/)  
建议使用 Pinokio 中的社区脚本 *wan2gp* 或 *wan2gp-amd*（由 **Morpheus** 提供），而不是官方的 Pinokio 安装程序。

**手动安装：(旧版 python 3.10，即将弃用)**

git clone https://github.com/deepbeepmeep/Wan2GP.git
cd Wan2GP
conda create -n wan2gp python=3.10.9
conda activate wan2gp
pip install torch==2.7.1 torchvision torchaudio --index-url https://download.pytorch.org/whl/test/cu128
pip install -r requirements.txt

**手动安装：(新版 python 3.11 setup)**

git clone https://github.com/deepbeepmeep/Wan2GP.git
cd Wan2GP
conda create -n wan2gp python=3.11.14
conda activate wan2gp
pip install torch==2.10.0 torchvision torchaudio --index-url https://download.pytorch.org/whl/cu130
pip install -r requirements.txt

**运行应用程序：**

python wgp.py

第一次使用 WanGP 吗？只需查看 *指南* 标签，你就能找到一系列推荐的模型供使用。

**更新应用程序（保持旧的 Python/PyTorch 版本）：** 如果使用 Pinokio，请使用 Pinokio 更新，否则： 进入 WanGP 安装的目录并：

git pull
conda activate wan2gp
pip install -r requirements.txt

**升级到 3.11，PyTorch 2.10，Cuda 13/13.1**（非 GTX10xx 用户适用）我建议为 Python 3.11 创建一个新的 conda 环境以避免意外情况。让我们将新的 conda 环境命名为 *wangp*（而不是 *wan2gp*，这是该项目旧的名称）进入 WanGP 安装的目录并：

git pull
conda create -n wangp python=3.11.9
conda activate wangp
pip install torch==2.10.0 torchvision torchaudio --index-url https://download.pytorch.org/whl/cu130
pip install -r requirements.txt

**Git 错误** 完成后，您需要重新安装 *Sage Attention*、*Triton*、*Flash Attention*。请查看 **[安装指南](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/INSTALLATION.md)** \-

如果您遇到与 git 相关的错误消息，可以尝试以下方法（注意：这将覆盖对 WanGP 源代码的本地修改）：

git fetch origin && git reset --hard origin/main
conda activate wangp
pip install -r requirements.txt

当你确认它运行良好后，可以删除旧的 conda 环境：

conda uninstall -n wan2gp --all  

**以无头模式运行（批量处理）：**

无需启动 Web UI 即可处理保存的队列：

 # Process a saved queue
python wgp.py --process my\_queue.zip

在 Web UI 中创建您的队列，使用"保存队列"保存它，然后无头方式处理。详情请参阅 [CLI 文档](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/CLI.md) 。

## 🐳 Docker:
**对于基于 Debian 的系统（如 Ubuntu、Debian 等）：**

./run-docker-cuda-deb.sh

此自动脚本将：

- 自动检测您的 GPU 型号和显存
- 为您的 GPU 选择最佳 CUDA 架构
- 如果需要，安装 NVIDIA Docker 运行时
- 构建包含所有依赖的 Docker 镜像
- 使用针对您的硬件的最佳设置运行 WanGP

**Docker 环境包括：**

- NVIDIA CUDA 12.4.1，支持 cuDNN
- PyTorch 2.6.0 支持 CUDA 12.4
- 针对您的特定 GPU 架构编译的 SageAttention
- 为性能优化的环境变量（TF32、线程等）
- 自动缓存目录挂载以加快后续运行
- 当前目录已挂载在容器中 - 所有下载的模型、loras、生成的视频和文件都保存在本地

**支持的 GPU：** RTX 40XX, RTX 30XX, RTX 20XX, GTX 16XX, GTX 10XX, Tesla V100, A100, H100, 以及更多。

## 📦 安装
### Nvidia针对不同代 GPU 的详细安装说明：

- **[安装指南](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/INSTALLATION.md)** \- RTX 10XX 至 RTX 50XX 的完整设置说明

### AMD针对不同代 GPU 的详细安装说明：

- **[安装指南](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/AMD-INSTALLATION.md)** \- RDNA 4、3、3.5 和 2 的完整设置说明

## 🎯 使用方法
### 基本用法- **[入门指南](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/GETTING_STARTED.md)** \- 首次使用和基本操作
- **[模型概览](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/MODELS.md)** \- 可用模型及其功能

### 高级功能- **[Loras 指南](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/LORAS.md)** \- 使用和管理 Loras 进行定制
- **[微调](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/FINETUNES.md)** \- 手动添加新模型到 WanGP
- **[VACE ControlNet](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/VACE.md)** - 高级视频控制和操作
- **[命令行参考](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/CLI.md)** \- 所有可用的命令行选项

## 📚 文档
- **[变更日志](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/CHANGELOG.md)** \- 最新更新和版本历史
- **[故障排除](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/TROUBLESHOOTING.md)** \- 常见问题和解决方案

## 📚 视频指南
- 一个解释如何使用 Vace 的不错视频：  
	[https://www.youtube.com/watch?v=FMo9oN2EAvE](https://www.youtube.com/watch?v=FMo9oN2EAvE)
- 另一份 Vace 指南：  
	[https://www.youtube.com/watch?v=T5jNiEhf9xk](https://www.youtube.com/watch?v=T5jNiEhf9xk)

## 🔗 相关项目
### 适合 GPU 性能不佳的其他模型- **[华元视频 GP](https://github.com/deepbeepmeep/HunyuanVideoGP)** - 最好的开源文本转视频生成器之一
- **[华元 3D-2GP](https://github.com/deepbeepmeep/Hunyuan3D-2GP)** - 图像转 3D 和文本转 3D 工具
- **[FluxFillGP](https://github.com/deepbeepmeep/FluxFillGP)** - 基于 Flux 的修复/扩展工具
- **[Cosmos1GP](https://github.com/deepbeepmeep/Cosmos1GP)** - 文本到世界生成器和图像/视频到世界
- **[OminiControlGP](https://github.com/deepbeepmeep/OminiControlGP)** - Flux 派生的对象迁移应用
- **[YuE GP](https://github.com/deepbeepmeep/YuEGP)** - 带乐器和歌手声音的曲谱生成器