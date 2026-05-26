---
title: "故障排除 - 常见问题和解决方案"
source: "https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/TROUBLESHOOTING.md"
author:
published:
created: 2026-05-19
description: "A fast AI Video Generator for the GPU Poor. Supports Wan 2.1/2.2, Qwen Image, Hunyuan Video, LTX  Video and Flux. - Wan2GP/docs/TROUBLESHOOTING.md at main · deepbeepmeep/Wan2GP"
tags:
  - "clippings"
taxonomy: { doc_category: [wangp] }
---
## 故障排除指南

本指南涵盖了使用 WanGP 时常见的问题及其解决方案。

## 安装问题

### PyTorch 安装问题

#### CUDA 版本不匹配

**问题** : PyTorch 无法检测到 GPU 或 CUDA 错误 **解决方案** :

```apache
# Check your CUDA version
nvidia-smi

# Install matching PyTorch version
# For CUDA 13.0/13.1 (RTX 20XX-50XX)
pip install torch==2.10.0 torchvision==0.25.0 torchaudio==2.10.0 --index-url https://download.pytorch.org/whl/cu130

# For CUDA 12.8 (GTX 10XX)
pip install torch==2.7.1 torchvision==0.22.1 torchaudio==2.7.1 --index-url https://download.pytorch.org/whl/test/cu128
```

#### Python 版本问题

**问题** : 包兼容性错误 **解决方案** ：确保你使用的是与你的 PyTorch 设置匹配的 Python 版本

```apache
python --version  # Should show 3.11.14 for PyTorch 2.10, or 3.10.9 for PyTorch 2.7.1
conda create -n wan2gp python=3.11.14
```

### 依赖安装失败

#### Windows 系统下的 Triton 安装

**问题** ： `pip install triton-windows` 安装失败 **解决方案** :

1. 更新 pip: `pip install --upgrade pip`
2. 尝试预编译的 wheel
3. 回退到 SDPA 注意力: `python wgp.py --attention sdpa`

#### SageAttention 编译问题

**问题** ：SageAttention 安装失败 **解决方案** ：

1. 安装 Visual Studio Build Tools (Windows)
2. 使用可用的预编译轮子
3. 回退到基本注意力模式

## 内存问题

### CUDA 内存不足

#### 在模型加载期间

**问题** ：加载模型时出现"CUDA 内存不足" **解决方案** ：

```vim
# Use smaller model
python wgp.py --t2v-1-3B

# Enable quantization (usually default)
python wgp.py --quantize-transformer True

# Use memory-efficient profile
python wgp.py --profile 4

# Reduce preloaded model size
python wgp.py --preload 0
```

#### 在视频生成期间

**问题** : 生成过程中出现内存错误 **解决方案** :

1. 减少帧数（制作更短的视频）
2. 在高级设置中降低分辨率
3. 使用较小的批量大小
4. 每代之间清除 GPU 缓存

### 系统 RAM 问题

#### 高 RAM 使用率

**问题** : 系统内存不足 **解决方案** :

```apache
# Limit reserved memory
python wgp.py --perc-reserved-mem-max 0.3

# Use minimal RAM profile
python wgp.py --profile 5

# Enable swap file (OS level)
```

## 性能问题

### 生成速度慢

#### 通用优化

```vim
# Enable compilation (requires Triton)
python wgp.py --compile

# Use faster attention
python wgp.py --attention sage2

# Enable TeaCache
python wgp.py --teacache 2.0

# Use high-performance profile
python wgp.py --profile 3
```

#### GPU 特定优化

**RTX 10XX/20XX 系列** :

```stylus
python wgp.py --attention sdpa --profile 4 --teacache 1.5
```

**RTX 30XX/40XX 系列** :

```stylus
python wgp.py --compile --attention sage --profile 3 --teacache 2.0
```

**RTX 50XX 系列** :

```stylus
python wgp.py --attention sage --profile 4 --fp16
```

### 注意力机制问题

#### Sage 注意力机制无法工作

**问题** ：Sage 注意力机制无法编译或运行 **诊断步骤** ：

1. 检查 Triton 安装：
	```stylus
	import triton
	print(triton.__version__)
	```
2. 清除 Triton 缓存：
	```bash
	# Windows
	rmdir /s %USERPROFILE%\.triton
	# Linux
	rm -rf ~/.triton
	```
3. 备用解决方案：
	```stylus
	python wgp.py --attention sdpa
	```

#### 闪存注意力问题

**问题** ：闪存注意力编译失败 **解决方案** ：

- Windows: 通常需要手动编译 CUDA 内核
- Linux: 通常可以使用 `pip install flash-attn`
- 备用方案：使用 Sage 或 SDPA 注意力机制

## 模型特定问题

### Lora 问题

#### Loras 无法加载

**问题** ：Loras 没有出现在界面上 **解决方案** ：

1. 检查文件格式（应为.safetensors、.pt 或.pth）
2. 验证正确目录：
	```nix
	loras/          # For t2v models
	loras_i2v/      # For i2v models
	loras_hunyuan/  # For Hunyuan models
	```
3. 点击界面中的"刷新"按钮
4. 使用 `--check-loras` 过滤不兼容文件

#### Lora 兼容性问题

**问题** ：Lora 导致错误或结果不佳 **解决方案** ：

1. 检查模型大小兼容性（1.3B vs 14B）
2. 验证 lora 是否针对您的模型类型进行训练
3. 尝试不同的乘数值
4. 使用 `--check-loras` 标志自动过滤

### VACE 特定问题

#### VACE 结果不佳

**问题** ：VACE 生成质量差或意外的结果 **解决方案** ：

1. 启用跳过层引导
2. 使用详细提示描述所有元素
3. 确保使用 Matanyone 正确创建遮罩
4. 检查参考图像质量
5. 至少使用15步，最好30步以上

#### Matanyone 工具问题

**问题** : 掩码创建困难 **解决方案** :

1. 使用负点提示来细化选择
2. 创建多个子掩码并将它们组合在一起
3. 尝试不同的背景移除选项
4. 确保源视频具有足够的对比度

## 网络和服务器问题

### Gradio 界面问题

#### 端口已被使用

**问题** ："端口 7860 已被使用" **解决方案** :

```nix
# Use different port
python wgp.py --server-port 7861

# Or kill existing process
# Windows
netstat -ano | findstr :7860
taskkill /PID <PID> /F

# Linux
lsof -i :7860
kill <PID>
```

#### 接口未加载

**问题** : 浏览器显示"连接被拒绝" **解决方案** :

1. 检查服务器是否成功启动
2. 尝试使用 `http://127.0.0.1:7860` 而不是 `localhost:7860`
3. 暂时禁用防火墙
4. 使用 `--listen` 标志进行网络访问

### 远程访问问题

#### 共享功能无法使用

**问题** : `--share` 标志无法创建公共 URL **解决方案** :

1. 检查网络连接
2. 尝试不同的网络
3. 使用 `--listen` 与端口转发
4. 检查防火墙设置

## 质量问题

### 视频质量差

#### 总体质量改进

1. 增加步数（25-30+）
2. 使用更大的模型（14B 而不是 1.3B）
3. 启用跳过层引导
4. 改进提示描述
5. 使用更高分辨率的设置

#### 具体的质量问题

**模糊视频** :

- 增加步数
- 检查源图像质量 (i2v)
- 减少 TeaCache 乘数
- 使用更高的引导尺度

**运动不一致** :

- 在滑动窗口中使用更长的重叠
- 减小窗口大小
- 提升提示一致性
- 检查控制视频质量（VACE）

**颜色问题** ：

- 检查模型兼容性
- 调整指导比例
- 验证输入图像色彩空间
- 尝试不同的 VAE 设置

## 高级调试

### 启用详细输出

```vim
# Maximum verbosity
python wgp.py --verbose 2

# Check lora compatibility
python wgp.py --check-loras --verbose 2
```

### 内存调试

```apache
# Monitor GPU memory
nvidia-smi -l 1

# Reduce memory usage
python wgp.py --profile 4 --perc-reserved-mem-max 0.2
```

### 性能分析

```dsconfig
# Test different configurations
python wgp.py --attention sdpa --profile 4  # Baseline
python wgp.py --attention sage --profile 3  # Performance
python wgp.py --compile --teacache 2.0      # Maximum speed
```

## 获取帮助

### 在请求帮助之前

1. 检查此故障排除指南
2. 阅读相关文档：
3. 尝试基本回退配置：
	```stylus
	python wgp.py --attention sdpa --profile 4
	```

### 社区支持

- **Discord 服务器** : [https://discord.gg/g7efUW9jGV](https://discord.gg/g7efUW9jGV)
- 提供相关信息：
	- GPU 型号和显存容量
		- Python 和 PyTorch 版本
		- 完整的错误消息
		- 启动 WanGP 所使用的命令
		- 操作系统

### 报告错误

报告问题时：

1. 包含系统规格
2. 提供完整的错误日志
3. 列出重现的确切步骤
4. 提及对默认设置的任何修改
5. 包含使用的命令行参数

## 紧急回退

如果都不起作用，尝试这个最小配置：

```apache
# Absolute minimum setup
python wgp.py --t2v-1-3B --attention sdpa --profile 4 --teacache 0 --fp16

# If that fails, check basic PyTorch installation
python -c "import torch; print(torch.cuda.is_available())"
```