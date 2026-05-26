---
title: "WanGP"
source: "https://github.com/deepbeepmeep/Wan2GP"
author:
published:
created: 2026-05-19
description: "A fast AI Video Generator for the GPU Poor. Supports Wan 2.1/2.2, Qwen Image, Hunyuan Video, LTX  Video and Flux. - deepbeepmeep/Wan2GP"
tags:
  - "clippings"
taxonomy: { doc_category: [wangp] }
---
## WanGP

---

**DeepBeepMeep 的 WanGP：最适合 GPU 资源有限的用户的最佳开源视频生成模型**

WanGP 支持 Wan（及其衍生模型），同时也支持 Hunyuan 视频、Flux、Qwen、Z-Image、LongCat、Kandinsky、LTXV、LTX-2、Qwen3 TTS、Chatterbox、HearMula、...等：

- 低 VRAM 需求（某些模型仅需 6 GB VRAM 即可）
- 支持旧款 Nvidia 显卡（RTX 10XX、20xx 等）
- 支持 AMD 显卡（RDNA 4、3、3.5 和 2），安装部分有详细说明。
- 在最新显卡上运行极快
- 易于使用，全网页界面
- 支持多种检查点量化格式：int8、fp8、gguf、NV FP4、Nunchaku
- 自动下载适配您特定架构的所需模型
- 集成工具以简化视频生成：Mask 编辑器、Prompt 增强器、时域和空域生成、MMAudio、视频浏览器、姿态/深度/流提取器、动作设计器
- 大量即用型插件：画廊浏览器、上采样器、模型/检查点管理器、CivitAI 浏览器和下载器、...
- 对每个模型进行定制支持 Loras
- 排队系统：将您要生成的视频加入购物清单稍后处理
- 无头模式：使用命令行启动多个图像/视频/音频文件的生成

**加入 WanGP 社区获取帮助并展示您的最佳作品：** [https://discord.gg/g7efUW9jGV](https://discord.gg/g7efUW9jGV)

**关注 DeepBeepMeep 的 Twitter/X 获取最新消息** : [https://x.com/deepbeepmeep](https://x.com/deepbeepmeep)

## 📋 目录

## 🔥 最新更新:

### 2026 年 5 月 12 日：WanGP v11.66，你能跟上吗？

- **HiDreamO1** ：具有编辑功能的新图像模型在保留识别和书写文本方面表现相当不错。WanGP 版本对 VRAM 的需求非常低，并原生支持 *Control Image* & *Preview* 。
- **Omnivoice** ：这个 *文本转语音模型* （TTS）速度快，支持 100 种语言并具有语音克隆功能。WanGP 额外提供了一个实验性对话模式（由于难以预测 Omnivoice 何时完成生成，这个模式不是最好的）。
- **ScenemeAI**: 一个基于 LTX2.3 的语音合成系统，它利用了 LTX-2 的领域知识：通过描述说话者正在做什么/说什么，你可以控制音频生成，从而产生逼真的音频。我在其基础上实现了一个对话模式，支持任意数量的说话者（前两个说话者支持声音克隆），并且在说话者之间有非常平滑的过渡，尤其是在生成英语时。你可以在语音合成模型中找到 ScenemeAI，但请注意它默认会使用一个视频内存配置文件 ，因为它背后使用了 LTX2 引擎。不要犹豫使用 WanGP 的提示增强器来生成生动的对话。
- **苹果早期支持** : Mac 用户即将发现 WanGP 的世界，尽管起步时它不会很快，优化也不是很好，而且并非所有模型都会得到支持。非常感谢 *huangyebiaoke* （负责移植）、 *cn0ss* & *SquishedSquirrel* （负责测试）。如果您是 Mac 用户，请在新 *MPS* Discord 频道中毫不犹豫地报告您的反馈。

### 2026 年 5 月 9 日：WanGP v11.61，最后一段路

经过轻微（半年）的延迟，WanGP 现在正式支持 *FlashVSR* ，这是一种非常高质量的 *空间上采样器* ，可以将您的视频上采样高达 4 倍。由于 FlashVSR 几乎完全为 WanGP 重新编写，因此可以将其称为 *GPU 差用户的终极上采样器* ，请查看这些数据：

- x2 空间上采样只需要 6GB 显存
- x4 空间上采样只需要 10GB 的 VRAM（见下方的 5k 示例）

上述 VRAM 需求与视频长度无关（视频越长，需要的 RAM 越多）

您首先需要安装 *Triton* ，并根据需要安装 *SpargeAttention* 以获得最佳质量（请查看 INSTALLATION.md 获取下载链接），并在 *Configuration > Extensions* 选项卡中启用 *FlashVSR* 。

FlashVSR 可在以下环境中使用：

- 一个在 *高级选项 > 后处理中的后处理选项*
- 一个可以应用于已生成视频的 *后期后处理*
- 在 *处理完整视频* 插件的 *WanGP 系统后处理* 模型中，您可以放大几个小时的视频！

请注意，由于 FlashVSR 现在已由 WanGP 原生支持并高度优化，您可能不再需要@h4k4z3 开发的 *FlashVSR 插件* 。无论如何，非常感谢@h4k4z3 开发这个插件，它非常有用。

### 2026 年 5 月 2 日：WanGP v11.52，一种魔法

- **Vista 4D** ：Vista4D 允许从新颖的相机轨迹和视角对动态场景进行 *视频重拍* 。换句话说，这个 Wan 2.1 模型将让你从一个不同的（移动的）视角重温一个有移动人物或物体的场景。这些序列相当短（通常 49 帧，最多约 97 帧），但很有趣，因为终于有一次它真的有效了。

在现实生活中，你本不可能运行这个模型（它需要的显存是同等输出分辨率所需的三倍，而预处理需要 24GB 显存来构建一个四维地图）。但再次感谢 WanGP 的魔法，显存需求已经降低到 10GB 或更少。

强烈建议应用 *Lightx2v 4 步骤* lora 配置文件。此外，为了最佳效率，你必须将所有动态物体/人物列在 *动态物体关键词* 输入框中。

- **魔法蒙版** ：生成视频蒙版或图像蒙版从未如此简单快捷。无需进入视频蒙版生成器标签页，只需点击蒙版字段旁边的魔法棒 ，输入几个关键词如蓝色汽车或右侧女士 ，由 SAM3 驱动的优质蒙版将自动生成。您将欣赏到 SAM3 带来的极佳时间一致性 。
- **支持 SAM3 的视频遮罩生成器** ：如果你仍然需要生成复杂的遮罩，可以将传统的点选遮罩与 SAM3/Magic Mask 遮罩结合使用。你需要在 *配置/扩展* 选项卡中启用此功能。
- **LTX-2 视频转音频** ：这基本上已经可以实现，但新的控制视频处理将更快，输出视频将保持未更改。

*更新 11.51* ：多项修复  
*更新 11.52* ：LTX 视频转音频，修复了滑动窗口音频延续中的错误

### 2026 年 4 月 25 日：WanGP v11.41，LTX-2 Mega Mix Part 2

为 **LTX-2** 带来更多精彩功能：

- **HDR 控制视频支持** ：现在您可以提供 HDR 控制视频，如果模型不支持 HDR，它将自动转换为 SDR
- **LTX 2.3 SDR 转 HDR** ：得益于新的 HDR Ic lora，现在您可以使用 LTX 2.3 将 SDR 视频转换为 HDR。此功能可作为新的 *控制视频处理* 使用，也包含在 *处理完整视频* 插件中。请注意，嵌入的 Gradio Gallery 视频播放器会自动将任何 HDR 内容转换为 SDR，因此如果您想体验完整的 HDR 内容，您需要使用外部媒体播放器（例如 *MPC-BE* ）
- **LTX 2.3 控制视频在第二阶段注入** ：到目前为止，即使你选择了两个阶段， *控制视频* 也只在第一阶段注入（第二阶段仅用于上采样）。现在如果你至少选择了一个 Ic Lora，并且为第二阶段设置了非零倍数，控制视频也将为第二阶段注入。这将提高使用两个阶段的输出质量，但会需要更多 VRAM 用于第二阶段。
- **处理完整视频自定义设置** ：现在您可以在插件中重用您自己的预设设置。当您将插件链接到设置时，对保存设置的任何更改将立即在插件中可用。如果您发现一些与该插件配合使用的优秀 loras/模型/设置组合，请在 Discord 服务器上分享，以便我将其添加到官方列表中。

*更新 11.41*: 添加了处理完整视频的自定义设置

### 2026 年 4 月 21 日: WanGP v11.35, LTX-2 巨大混合

为 **LTX-2** 带来了许多精彩的功能：

- **LTX-2.3 精炼版 1.1**: 由 *LTX 团队* 发布的 *精炼模型* 的新版本，应该能提供更好的音频和视觉效果。你还会找到一个 Dev 1.1 版本，该版本在第二阶段使用精炼版 1.1。
- **VBVR LoRA 预设** ：这个 LoRA 增强了基础 LTX-2 的复杂提示理解能力、运动动态和时序一致性。您可以在顶部的 *设置列表* 中选择它。
- **阶段 1/2 选择** ：现在你可以选择传统的 *两阶段生成* （第一阶段低分辨率，第二阶段较短的高分辨率）或直接选择单一高分辨率阶段（需要更多 VRAM 且较慢，但可能质量更高）。请注意，Outpainting 模式和 Pose/Edge/Depth 提取器始终使用单阶段。
- **改进的滑动窗口** ：窗口之间的过渡应该更不明显， *滑动窗口重叠帧* 现在也包含重叠帧的音频，因此重叠帧的数量越多，之前窗口中使用的声音/语音被用于新窗口的可能性就越大。
- **视频长度不受音频限制** ：如果你提供音频输入，WanGP 将不再在音频消耗完毕时停止。它会根据你的文本提示继续生成视频/音频，猜猜看？它可能会重复使用到目前为止已经使用的相同声音！这是一个选项，你需要勾选 *视频长度不受音频限制* 复选框。
- **无声电影模式** : 如果你因为某些原因想要视频不仅没有声音，而且还要考虑到没有声音（例如，你不想让观众张嘴），那么现在请将 *控制音频* 留空

~~ - LTX2/2.3 Loras Split: 由于 LTX2.0 Loras 与 LTX2-3 配合效果不佳且正在改进中，现在每个 LTX2 版本都有自己的 lora 文件夹。Loras 将在启动时自动通过 lora 迁移脚本移动。我邀请你验证 loras 是否已正确放置在相应的文件夹中。~~

- **系统 LoRA 乘数覆盖** ：WanGP 会根据功能需求（蒸馏 LoRA、ID LoRA、Outpaint LoRA、联合控制 LoRA）自动且透明地添加 LoRA（即使它们不可见也会被加载）。现在您可以通过在 *已激活的 LoRA* 输入中选择目标 LoRA，并指定相应的 *LoRA 乘数* 来覆盖 WanGP 使用的默认乘数。
- **通过姿态对齐转移人体动作** ：你试图从控制视频中转移人体动作，但你使用的起始图像中的人体体型不同（更大、更高、...），并且站在画面的不同位置。这样将无法很好地工作，因为起始图像最终会变得失真。这是一个过去的问题，因为现在如果你选择“ *通过姿态对齐转移人体动作* ”，控制视频的姿态就可以与起始图像对齐。这个功能也由 *Wan Vace* 支持，起始图像必须是 *背景参考图像* 。
- **注入帧与滑动窗口** ：从第 2 个窗口开始，注入帧未能正确注入。现在已支持。
- **全视频处理插件** ：这个需要先在插件选项卡中启用的捆绑插件 ，目前仅支持 Outpainting。它依赖于 LTX2 Lora Outpainting。它大致是一种超级滑动窗口模式，但不受 RAM 限制 ，且不会因大文件导致视频库崩溃。如果你足够耐心，可以调整几小时电影的长宽比（下方有 1 分钟样本可供参考）。见证滑动窗口过渡几乎难以察觉！
- **全视频插件的新处理功能** ：新增了 Refocus（去除模糊）、Ungrade（去除风格化调色）和 Uncompress（去除压缩伪影）。感谢 Oumoumad Mohamed 创建了这些功能所需的 Ic Loras（包括 Outpainting Lora）。如果你发现一些有用的 Ic Loras 且不会与滑动窗口产生冲突，请告诉我，我会将它们添加进来。
- **WanGP API 视频生成** : *插件开发者* 现在可以直接从插件中 *排队生成* 。这为插件提供了可能，即插件可以放置各种生成订单，然后将结果组合（提示：我们可以在 WanGP 内部拥有我们自己的 *LTX-Destop* 版本）。
- **全新一键安装/更新脚本** ：我们要感谢 **Tophness / @steve\_Jabz** 为此做出的贡献。 *向他致以崇高敬意！* 这些脚本不仅能安装 WanGP，还能安装所有内核 （包括 Trition、Sage、Flash、GGuf、Lightx2v、Nunchaku 等）——这些内核都由您的 GPU 支持。请查看下方的说明。欢迎分享反馈或报告任何问题。

*更新 11.31* ：修复了在某些情况下强制执行阶段 1 的错误  
*更新 11.32* ：修复了错误，Process Full Video 现在支持 Distilled 1.1 并接受无音频的视频  
*更新 11.33* ：将 LTX2 和 LTX2.3 的 loras 分别放在不同文件夹，添加了简单的 loras 乘数覆盖功能  
*更新 11.34*: 撤回拆分，因不受欢迎  
*更新 11.35*: 添加了 Aligned Pose Transfer、注入帧 & 滑动窗口支持，Process Full Video 插件的新流程

### 2026 年 4 月 11 日：WanGP v11.26，现在我能看见了

- **LTX-2 Ic Lora 重启** ： *Ic Loras* 行为如同 *Control Nets* ，可通过应用特定于 Ic Lora 的效果（例如 *姿态提取* 、 *上采样* 、 *转移相机运动* 、...）进行 *视频到视频* 处理。如今越来越多的 Ic Loras 可用。迄今为止，WanGP Ic Lora 的实现基于官方 LTX-2 github 实现（这是一个两阶段过程，其中 Ic Lora 仅在第一低分辨率阶段应用）。但我刚刚发现，所有 Ic Loras 实际上期望的是 ComfyUI 实现，这是一个仅在一阶段全分辨率过程中完成的流程。

从那时起，WanGP Ic Lora 也将以这种方式工作。缺点是单次全分辨率渲染会消耗更多的 GPU 资源。但在 WanGP 的世界里一切顺利，因为 LTX2 的 VRAM 优化将允许你在其他任何地方都无法达到的分辨率使用 Ic Lora。

作为额外福利，我已经为 Ic Lora 调整了 *滑动窗口* ，如果你将 *重叠大小* 设置为单帧，在使用 Ic Lora 时窗口之间的过渡将几乎不可见。

- **Outpaint Ic Lora** ：如果你选择 *Control Video for Ic Lora* 选项并启用 *Outpainting* ，这个新的令人印象深刻的 Ic Lora 将会自动加载。如果你使用带 Outpainting 的滑动窗口，你将能够 outpaint 一整部电影（假设你有足够的 RAM）。
- **新绘制自动调整宽高比** ：作为提醒，WanGP 允许你手动定义绘制区域的位置。或者，你现在可以要求 WanGP 使用绘制功能来改变控制视频的 *宽高比* 。例如，你可以将任何 16:9 视频转换为 4:3 视频通过生成新细节而不是添加黑边。在这个新模式中的 *上下左右滑块* 将用于定义优先扩展哪个区域以满足所需的宽高比。

*更新 11.26*: 修复了当选择手动扩展时忽略外绘的问题

### 2026 年 4 月 8 日：WanGP v11.22，自毁模型

- **Magi Human** ：这是一个新的口播模型，可以接受自定义的音轨 ，或者生成与视频配套的音频语音 。
	- *坏消息* ：它对显存需求很大（目标 RTX 5090+），并且对分辨率非常挑剔，输出分辨率必须是 256p 或 1080p（使用两阶段管道并进行上采样）。还有一个 540p 版本（也使用上采样器），但我不包括它，因为我发现它不太实用（如果输出不是精确的宽高比，肯定会出现重影）。
		- *好消息* ：现在它是 WanGP 优化的，1080p 的 101 帧只需要“仅”16GB 的显存。如果你没有那么多显存，我建议仍然选择 1080p，但设置一个 45 帧的滑动窗口 （不要太低以避免伪影），因为滑动窗口有时与这个模型配合效果很好。

**我花了很多时间优化 Magi Human，但在所有运行这个模型的限制下，我还不确定是否值得保留它。所以这就是我需要你的地方。请在 Discord 服务器上分享你使用 Magi Human 的经验，你来决定它的命运。我们应该保留它还是把它送到模型墓地？**

- **Ace 1.5 Turbo XL** ：最好的开源歌曲生成器现在有了强大的兄弟 *XL* ，它提供更好的音频质量，更贴近请求的歌词。
- **LTX 2 Id Lora** ：由于巨大的需求，我添加了这一个（它是一个新的 *生成视频* 选项）。你可以提供语音音频样本、起始图像和文本脚本，它将 LTX 2/2.3 变成会说话的人头。获取这个功能的成本很高，因为 **Id Lora 只与 LTX2/2.3 DEV** 工作。偶然间似乎它只需要 10 个推理步骤就能产生不错的结果。为了获得最佳结果，建议使用前缀标签\[VISUAL\]、\[SPEECH\] & \[SOUND\]。或者你可以使用 WanGP *Prompt Enhancer* ，它已被调校以生成符合此语法的提示。
- **LTX 2 NAG**: 即使使用蒸馏模型，你也能通过支持 LTX 2 的 *NAG* 功能注入 *负面提示*
- **LTX 2 DEV HQ 模式** : 这个高质量模式应在更高分辨率下产生更好的输出。你可以使用新的 *HQ (res2s)* 采样器将其开启，并将步数设置为 15，指导分辨率缩放器设为 0.45。它兼容 *Id Loras* 。请注意，HQ 步数比普通 Dev 步数慢一倍，因此如果未变慢，其速度将与 Dev 相同。
- **LTX2 DEV 预设** : 普通 Dev 模式和 HQ 模式都有许多可调节设置。为了方便使用，我在 *设置下拉框中添加了可选的预设*
- **更深层次** :
	- *UI 改进* ：你可以通过在两个请求之间插入空行来 *排队* 请求，通过点击 *向下箭头获取最后一步*
		- *响应更快* ：Deepy 应该能更快地执行连续操作
		- *更可靠* ：快速全上下文压缩（当 deepy 用完 token 时），Deepy 会记住你停止/中止的操作
		- *更多功能* : 你可以要求 Deepy 指定一个 *指导* 、 *去噪强度* 、...值（ *工具模板* 中定义的值将被覆盖）

除了撰写大量关于你有多厉害的论文之外，Deepy 还可以生成视频、图像和音频，提取/转录/剪辑/调整大小（在适用的情况下）视频或音频片段，检查图像或视频帧的内容，生成黑帧等等。Deepy 使用工具模板，但你可以为单个任务指定 loras、帧数、尺寸等等。Deepy 还有一个 CLI 版本，对于远程使用相当有用。请查看完整文档 *docs/DEEPY.md* 。

- **多行多行提示** : 检查 *"如何处理文本提示的每一行"* 中的新选项，现在您可以拥有多个多行提示。它们只需要用空行隔开。

*更新 11.21*: 添加了 Ace Step 1.5 Turbo XL  
*更新 11.22*: 添加了 LTX2 NAG

### 2026 年 3 月 30 日：WanGP v11.13，机器中的机器

遇见 **Deepy** ，你友好的 *WanGP 代理* 。

你可以让 Deepy 为你执行繁琐的任务，例如：

```css
generate a black frame, crop a  video, extract a specific frame from a video, trim an audio, ...
```

Deepy 还可以执行完整的工作流程：

```livecodeserver
1) Generate an image of a robot disco dancing on top of a horse in a nightclub.
2) Now edit the image so the setting stays the same, but the robot has gotten off the horse and the horse is standing next to the robot.
3) Verify that the edited image matches the description; if it does not, generate another one.
4) Generate a transition between the two images.
```

或

```livecodeserver
Create a high quality image portrait that you think represents you best in your favorite setting. Then create an audio sample in which you will introduce the users to your capabilities. When done generate a video based on these two files.
```

Deepy 还能转录视频中的音频内容（ *新功能，适用于 WanGP 11.11* ）

```livecodeserver
extract the video from the moment it says "Deepy changed my life"
```

*Deepy* 重用了 *Qwen3VL Abliterated* 检查点，强烈建议安装 *GGUF 内核* （查看文档/INSTALLATION.md）以实现低 VRAM / 快速推理。 **现在支持 Linux！**

请安装 *flash attention 2* 和 *triton* 以启用 *vllm* 并获得 x2/x3 的速度提升和更低的 VRAM 使用。

在生成视频、图像等时，您可以自定义 Deepy 以使用您选择的设置（请查看文档/DEEPY.Md）。

*前往配置 > 提示增强器 / Deep 选项卡以启用 Deepy（您必须首先选择一个 Qwen3.5VL 提示增强器）*

**重要** ：为了节省 Deepy 学习每个模型生成图像、视频或音频的具体细节的时间，Deepy 使用 *预定义设置模板* 为其六个主要工具（ *生成视频* 、 *生成图像* 、...）进行操作。您可以在会话中更改所使用的模板，甚至可以添加自己的设置。只需查看文档即可。

使用 WanGP 11.11，您可以 *要求 Deepy 在特定尺寸下生成视频或图像，并指定视频的帧数* 。您还可以指定可选的 *推理步数* 或 *loras* ，并使用 *乘数* 。如果您没有向 Deepy 提及这些内容，Deepy 将使用默认设置或当前的模板设置。

WanGP 11 解决了 Gradio 长期以来存在的问题： *即使您的网络浏览器处于后台，队列仍然会继续处理* 。请注意此功能可能会消耗更多电量，因此您可以在 *配置/常规选项卡* 中禁用它。

您可能也注意到了 *Config / Outputs* 选项卡中新增的 *Keep Intermediate Sliding Windows* 选项，它允许您丢弃中间的 *Sliding Windows*

查看完整变更日志： **[Changelog](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/CHANGELOG.md)**

## 🚀 快速入门

### 一键式 Bat/SH 脚本自动安装程序：

为 **Windows (`.bat`)** 和 **Linux/macOS (`.sh`)** 提供的 1 键自动化脚本，使安装、环境管理和更新尽可能无缝。这些脚本不仅会安装 WanGP，还会根据您的配置安装最佳加速内核（Triton、Sage、Flash、GGuf、Lightx2v、Nunchaku）。

*👉 **Windows 用户：** 双击 `.bat` 文件。 **Linux 用户：** 在终端中运行 `.sh` 文件。*

#### 1️⃣ 安装 (scripts\\install.bat | scripts/install.sh)

**选择安装类型**

- **自动安装**
- **手动安装**

**手动安装**

如果你选择了手动安装，你将会被引导完成以下步骤：

1. **选择你的包管理器**
2. **命名你的环境**
3. **选择您的安装模式**

#### 2️⃣ 启动应用（scripts\\run.bat | scripts/run.sh）

安装完成后，使用此脚本启动应用。它将使用您的当前环境运行 WAN2GP。

- **⚙️ 自定义启动参数（ `args.txt` ）**
	- 如果您想向启动器传递额外的命令行标志（例如启用高级 UI 功能或自动打开您的浏览器），请在您的 `scripts` 文件夹中创建一个 `args.txt` 文件。
		- **示例 `args.txt`:**
		```brainfuck
		--advanced --open-browser
		```

#### 3️⃣ 更新与升级 (scripts\\update.bat | scripts/update.sh)

使用此脚本获取 WAN2GP 的最新更新并升级依赖项。

- **1\. 更新:** 从 GitHub 获取最新代码并更新依赖项。
- **2\. 升级:** 允许您手动逐个升级重型后端组件（如 PyTorch、Triton、Sage Attention）。

#### 4️⃣ 管理环境 (scripts\\manage.bat | scripts/manage.sh)

使用此脚本安全地管理和切换您的沙盒环境。

- **示例场景1：迁移现有设置**
	- 如果你有一个名为 `venv` 且运行完美的文件夹，并想用新的单击脚本使用它，请运行 `manage.bat` 并选择 **添加现有环境** 。
		- 复制粘贴文件夹路径（例如： `C:\WAN2GP\venv` ），选择类型 `venv` ，然后使用 **设置活动环境** 将其设为默认。现在 `run.bat` 和 `update.bat` 将针对您的现有设置。
- **示例场景2：测试新配置**
	- 假设你有一个名为 `env_stable` 的环境运行得非常完美，但你想尝试新的"使用最新版"组合。为了避免影响你的工作环境，运行 `install.bat` ，创建一个 *新的* 环境，命名为 `env_testing` ，并选择 **使用最新版** 。
		- 如果测试环境崩溃了，只需打开 `manage.bat` ，选择 **设置活动环境** ，然后切换回 `env_stable` 。你立刻就能恢复运行。

---

### 一键（Pinokio）安装程序：

立即开始使用 [Pinokio App](https://pinokio.computer/)  
建议使用由 **Morpheus** 提供的社区脚本 wan2gp 或 wan2gp-amd 而不是官方的 Pinokio 安装版。

---

### 手动安装：(适用于 RTX20xx - RTX50xx)

```apache
git clone https://github.com/deepbeepmeep/Wan2GP.git
cd Wan2GP
conda create -n wan2gp python=3.11.14
conda activate wan2gp
pip install torch==2.10.0 torchvision==0.25.0 torchaudio==2.10.0 --index-url https://download.pytorch.org/whl/cu130
pip install -r requirements.txt
```

### 手动安装：(适用于 GTX 10xx)

```apache
git clone https://github.com/deepbeepmeep/Wan2GP.git
cd Wan2GP
conda create -n wan2gp python=3.10.9
conda activate wan2gp
pip install torch==2.7.1 torchvision==0.22.1 torchaudio==2.7.1 --index-url https://download.pytorch.org/whl/test/cu128
pip install -r requirements.txt
```

#### 运行应用程序：

```vim
python wgp.py
```

第一次使用 WanGP？只需查看 *指南* 标签，你就会找到推荐的模型选择。

#### 更新应用程序（保持当前 python / pytorch 版本）：

如果使用 Pinokio，请使用 Pinokio 更新，否则：进入 WanGP 安装目录并：

```applescript
git pull
conda activate wan2gp
pip install -r requirements.txt
```

#### 从 Python 3.10、Pytorch 2.7.1、Cuda 12.8 升级到 Python 3.11、Pytorch 2.10、Cuda 13/13.1（非 GTX10xx 用户适用）

我建议先将旧的 conda 环境重命名，以避免在安装不同配置时出现意外情况。

```powershell
conda rename -n wan2gp  old_wan2gp
```

进入 WanGP 安装目录并：

```apache
git pull
conda create -n wan2gp python=3.11.9
conda activate wan2gp
pip install torch==2.10.0 torchvision==0.25.0 torchaudio==2.10.0 --index-url https://download.pytorch.org/whl/cu130
pip install -r requirements.txt
```

完成后，你需要重新安装 *Sage Attention* 、 *Triton* 、 *Flash Attention* 。请查看 **[安装指南](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/INSTALLATION.md)** \-

如果你遇到与 git 相关的错误信息，可以尝试以下方法（注意：这将覆盖 WanGP 源代码的本地修改）：

```maxima
git fetch origin && git reset --hard origin/main
conda activate wan2gp
pip install -r requirements.txt
```

当你确认它运行良好后，可以删除旧的 conda 环境：

```ada
conda uninstall -n old_wan2gp --all
```

#### 以无头模式运行（批量处理）：

在不启动 Web UI 的情况下处理保存的队列：

```applescript
# Process a saved queue
python wgp.py --process my_queue.zip
```

在网页界面中创建你的队列，使用"保存队列"保存，然后无头方式处理。详情请参阅 [CLI 文档](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/CLI.md) 。

## 🐳 Docker:

**对于基于 Debian 的系统（Ubuntu、Debian 等）：**

```stata
./run-docker-cuda-deb.sh
```

此自动脚本将：

- 自动检测您的 GPU 型号和显存
- 为您的 GPU 选择最佳 CUDA 架构
- 如需安装 NVIDIA Docker 运行时
- 构建包含所有依赖的 Docker 镜像
- 使用针对您硬件的最佳设置运行 WanGP

**Docker 环境包括：**

- NVIDIA CUDA 12.4.1，支持 cuDNN
- PyTorch 2.6.0，支持 CUDA 12.4
- 为您的特定 GPU 架构编译的 SageAttention
- 为性能优化的环境变量（TF32、线程等）
- 自动缓存目录挂载以加快后续运行
- 当前目录在容器中挂载 - 所有下载的模型、loras、生成的视频和文件都保存在本地

**支持的 GPU：** RTX 40XX, RTX 30XX, RTX 20XX, GTX 16XX, GTX 10XX, Tesla V100, A100, H100, 以及更多。

## 📦 安装

### Nvidia

不同 GPU 代数的详细安装说明：

- **[安装指南](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/INSTALLATION.md)** \- RTX 10XX 至 RTX 50XX 的完整设置说明

### AMD

不同 GPU 代数的详细安装说明：

- **[安装指南](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/AMD-INSTALLATION.md)** \- RDNA 4、3、3.5 和 2 的完整设置说明

## 🎯 使用方法

### 基本用法

- **[入门指南](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/GETTING_STARTED.md)** \- 首次使用和基本操作
- **[模型概览](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/MODELS.md)** \- 可用模型及其功能
- **[提示指南](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/PROMPTS.md)** \- WanGP 如何解释提示、图像作为提示、增强器和宏

### 高级功能

- **[Deepy Assistant](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/DEEPY.md)** - 启用 Deepy，配置其工具预设，使用选定媒体和帧，并从 CLI 运行 Deepy
- **[Loras Guide](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/LORAS.md)** - 使用和管理 Loras 进行定制
- **[Finetunes](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/FINETUNES.md)** - 手动向 WanGP 添加新模型
- **[VACE ControlNet](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/VACE.md)** - 高级视频控制和操作
- **[命令行参考](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/CLI.md)** \- 所有可用的命令行选项

## 📚 文档

- **[变更日志](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/CHANGELOG.md)** \- 最新更新和版本历史
- **[故障排除](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/TROUBLESHOOTING.md)** \- 常见问题和解决方案

## 📚 视频指南

- 一个很棒的 Vace 使用教程视频：  
	[https://www.youtube.com/watch?v=FMo9oN2EAvE](https://www.youtube.com/watch?v=FMo9oN2EAvE)
- 另一个 Vace 指南：  
	[https://www.youtube.com/watch?v=T5jNiEhf9xk](https://www.youtube.com/watch?v=T5jNiEhf9xk)

## 🔗 相关项目

### 其他适合 GPU 性能不足的模型

- **[HuanyuanVideoGP](https://github.com/deepbeepmeep/HunyuanVideoGP)** - 最好的开源文本转视频生成器之一
- **[Hunyuan3D-2GP](https://github.com/deepbeepmeep/Hunyuan3D-2GP)** - 图像转 3D 和文本转 3D 工具
- **[FluxFillGP](https://github.com/deepbeepmeep/FluxFillGP)** - 基于 Flux 的修复/扩展工具
- **[Cosmos1GP](https://github.com/deepbeepmeep/Cosmos1GP)** - 文本生成世界和图像/视频生成世界
- **[OminiControlGP](https://github.com/deepbeepmeep/OminiControlGP)** - 基于 Flux 的对象迁移应用
- **[YuE GP](https://github.com/deepbeepmeep/YuEGP)** - 带乐器和歌手声音的曲子生成器