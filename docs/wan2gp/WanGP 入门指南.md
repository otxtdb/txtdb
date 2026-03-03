---
title: "WanGP 入门指南"
source: "https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/GETTING_STARTED.md"
author:
  - "[[deepbeepmeep]]"
published:
created: 2026-02-27
description: "A fast AI Video Generator for the GPU Poor. Supports Wan 2.1/2.2, Qwen Image, Hunyuan Video, LTX  Video and Flux. - Wan2GP/docs/GETTING_STARTED.md at main · deepbeepmeep/Wan2GP"
tags:
  - "clippings"
taxonomy: { doc_category: [wan2gp] }
---
本指南将帮助您快速轻松地开始使用 WanGP 视频生成。

## 前提条件
开始前，请确保您已准备好：

- 一台兼容的 GPU（推荐使用 RTX 10XX 或更新的型号）
- 已安装 Python 3.10.9
- 至少 6GB 的 VRAM 用于基本模型
- 互联网连接用于模型下载

## 快速设置
### 选项1：一键安装（推荐）
使用 [Pinokio App](https://pinokio.computer/) 获得最简单的安装体验。

### 选项 2：手动安装
git clone https://github.com/deepbeepmeep/Wan2GP.git
cd Wan2GP
conda create -n wan2gp python=3.10.9
conda activate wan2gp
pip install torch==2.6.0 torchvision torchaudio --index-url https://download.pytorch.org/whl/test/cu124
pip install -r requirements.txt

有关详细的安装说明，请参阅 [INSTALLATION.md](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/INSTALLATION.md)。

## 首次启动
### 基本启动
python wgp.py

这会以默认设置启动 WanGP 生成器。您将能够从下拉菜单中选择要使用的模型。

### 其他模式
python wgp.py --i2v        # Wan Image-to-video mode
python wgp.py --t2v-1-3B   # Wan Smaller, faster model

## 理解界面
当您启动 WanGP 时，您将看到一个包含多个部分的网页界面：

### 主生成面板
- **模型选择** : 下拉菜单用于选择不同模型
- **提示** : 你想要生成的文本描述
- **生成按钮** : 开始视频生成过程

### 高级设置（点击复选框以启用）
- **生成设置** : 步骤、指导、种子
- **Loras**: 额外的样式定制
- **滑动窗口** : 用于更长的视频

## 你的第一个视频让我们生成一个简单的文本到视频：

1. **启动 WanGP**: `python wgp.py`
2. **打开浏览器** : 导航至 `http://localhost:7860`
3. **输入提示** : "一只猫在花园里散步"
4. **点击生成** : 等待视频生成
5. **查看结果** : 视频将出现在输出区域

### 推荐初始设置

- **模型** : Wan 2.1 text2video 1.3B (更快，VRAM 占用更低)
- **帧** : 49 (大约 2 秒)
- **步骤** : 20（速度/质量平衡良好）

## 模型选择
### 文本到视频模型
- **Wan 2.1 T2V 1.3B**: 速度最快，最低 VRAM（6GB），质量良好
- **Wan 2.1 T2V 14B**: 最高质量，需要更多 VRAM（12GB+）
- **Hunyuan Video**: 优秀质量，生成速度较慢
- **LTX Video**: 适合生成较长的视频

### 图像转视频模型
- **Wan Fun InP 1.3B**: 快速图像动画
- **Wan Fun InP 14B**: 更高质量的图像动画
- **VACE**: 对视频生成的高级控制

### 选择合适的模型
- **低 VRAM（6-8GB）**: 使用 1.3B 模型
- **中 VRAM（10-12GB）**: 使用 14B 模型或 Hunyuan
- **高 VRAM（16GB+）**: 任何模型，更长的视频

## 基础设置说明
### 生成设置
- **帧数** : 帧数（更多 = 更长的视频）
	- 25帧 ≈ 1秒
	- 49帧 ≈ 2秒
	- 73帧 ≈ 3秒
- **步骤** ：质量与速度的权衡
	- 15步：快速，质量较低
	- 20步：良好平衡
	- 30+步：高质量，较慢
- **指导比例** ：遵循提示的紧密程度
	- 3-5：更具创意的解读
	- 7-10: 更接近提示描述
	- 12+: 非常字面化的解释

### 种子
- **随机种子** : 每次结果都不同
- **固定种子** : 可重复的结果
- **使用相同的种子+提示** : 生成变体

## 常见的初学者问题
### "内存不足"错误
1. 使用更小的模型（1.3B 而不是 14B）
2. 减少帧数
3. 在高级设置中降低分辨率
4. 启用量化（通常默认开启）

### 慢速生成
1. 使用 1.3B 模型以加快速度
2. 减少步骤数量
3. 安装 Sage 注意力（参见 [INSTALLATION.md](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/INSTALLATION.md)）
4. 启用 TeaCache: `python wgp.py --teacache 2.0`

### 结果质量差
1. 增加步数（25-30）
2. 改进提示描述
3. 如果你有足够的 VRAM，请使用 14B 模型
4. 在高级设置中启用跳过层指导

## 编写良好的提示### 基本结构```
[Subject] [Action] [Setting] [Style/Quality modifiers]
```

### 示例```
A red sports car driving through a mountain road at sunset, cinematic, high quality

A woman with long hair walking on a beach, waves in the background, realistic, detailed

A cat sitting on a windowsill watching rain, cozy atmosphere, soft lighting
```

### 提示
- 明确你想要的内容
- 包含风格描述（电影感、写实等）
- 提及灯光和氛围
- 详细描述设置
- 使用质量修饰词（高质量、详细等）

## 下一步
当你对基本生成感到舒适时：

1. **探索高级功能** :
	- [洛拉斯指南](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/LORAS.md) \- 自定义样式和角色
	- [VACE ControlNet](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/VACE.md) - 高级视频控制
	- [命令行选项](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/CLI.md) \- 优化性能
2. **提升性能** :
	- 安装更好的注意力机制
	- 优化内存设置
	- 使用编译来提升速度
3. **加入社区** ：
	- [Discord 服务器](https://discord.gg/g7efUW9jGV) \- 获取帮助和分享视频
	- 分享你的最佳成果
	- 从其他用户那里学习

## 故障排除第一步
### 安装问题
- 确保使用 Python 3.10.9
- 检查 CUDA 版本兼容性
- 详细步骤请参考 [INSTALLATION.md](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/INSTALLATION.md)

### 生成问题
- 检查 GPU 兼容性
- 验证足够的 VRAM
- 先尝试基本设置
- 具体问题请参考 [TROUBLESHOOTING.md](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/TROUBLESHOOTING.md)

### 性能问题
- 为您的硬件选择合适的模型
- 启用性能优化
- 查阅 [CLI.md](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/CLI.md) 了解优化标志

记住：从简单开始，随着您熟悉基础知识，逐步探索更高级的功能！