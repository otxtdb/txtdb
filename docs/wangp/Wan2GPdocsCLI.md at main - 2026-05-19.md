---
title: "命令行参考 - 所有可用的命令行选项"
source: "https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/CLI.md"
author:
published:
created: 2026-05-19
description: "A fast AI Video Generator for the GPU Poor. Supports Wan 2.1/2.2, Qwen Image, Hunyuan Video, LTX  Video and Flux. - Wan2GP/docs/CLI.md at main · deepbeepmeep/Wan2GP"
tags:
  - "clippings"
taxonomy: { doc_category: [wangp] }
---
## 命令行参考

本文档涵盖了 WanGP 所有可用的命令行选项。

## 基本用法

```mel
# Default launch
python wgp.py
```

## CLI 队列处理（无头模式）

在不启动 Web UI 的情况下处理保存的队列。适用于批量处理或自动化工作流。

### 快速入门

```jboss
# Process a saved queue (ZIP with attachments)
python wgp.py --process my_queue.zip

# Process a settings file (JSON)
python wgp.py --process my_settings.json

# Validate without generating (dry-run)
python wgp.py --process my_queue.zip --dry-run

# Process with custom output directory
python wgp.py --process my_queue.zip --output-dir ./batch_outputs
```

### 支持的文件格式

| 格式 | 描述 |
| --- | --- |
| `.zip` | 包含嵌入附件（图片、视频、音频）的完整队列。通过"保存队列"按钮创建。 |
| `.json` | 仅设置文件。媒体路径按原样使用（绝对路径或相对于 WanGP 文件夹）。通过"导出设置"按钮创建。 |

### 工作流程

1. **在 Web 界面中使用常规界面创建您的队列**
2. **保存队列** ，使用"保存队列"按钮（创建.zip 文件）
3. **如需** ， 关闭网页界面
4. **通过命令行** 处理队列：
	```stylus
	python wgp.py --process saved_queue.zip --output-dir ./my_outputs
	```

### CLI 队列选项

```css
--process PATH          # Path to queue (.zip) or settings (.json) file (enables headless mode)
--dry-run               # Validate file without generating (use with --process)
--output-dir PATH       # Override output directory (use with --process)
--verbose LEVEL         # Verbosity level 0-2 for detailed logging
```

### 控制台输出

CLI 模式提供实时反馈：

```nix
WanGP CLI Mode - Processing queue: my_queue.zip
Output directory: ./batch_outputs
Loaded 3 task(s)

[Task 1/3] A beautiful sunset over the ocean...
  [12/30] Prompt 1/3 - Denoising | Phase 2/2 Low Noise
  Video saved
  Task 1 completed

[Task 2/3] A cat playing with yarn...
  [30/30] Prompt 2/3 - VAE Decoding
  Video saved
  Task 2 completed

==================================================
Queue completed: 3/3 tasks in 5m 23s
```

### 退出代码

| 代码 | 含义 |
| --- | --- |
| 0 | 成功（所有任务完成） |
| 1 | 错误（文件未找到、无效队列或任务失败） |
| 130 | 用户中断（Ctrl+C） |

### 示例

```jboss
# Overnight batch processing
python wgp.py --process overnight_jobs.zip --output-dir ./renders

# Quick validation before long run
python wgp.py --process big_queue.zip --dry-run

# Verbose mode for debugging
python wgp.py --process my_queue.zip --verbose 2

# Combined with other options
python wgp.py --process queue.zip --output-dir ./out --attention sage2
```

## 模型和性能选项

### 模型配置

```dsconfig
--quantize-transformer BOOL   # Enable/disable transformer quantization (default: True)
--compile                     # Enable PyTorch compilation (requires Triton)
--attention MODE              # Force attention mode: sdpa, flash, sage, sage2
--profile NUMBER              # Performance profile 1-5 (default: 4)
--preload NUMBER              # Preload N MB of diffusion model in VRAM
--fp16                        # Force fp16 instead of bf16 models
--gpu DEVICE                  # Run on specific GPU device (e.g., "cuda:1")
```

### 性能配置

- **配置 1** ：将当前整个模型加载到 VRAM 中，并将所有未使用的模型保留在保留 RAM 中，以便快速进行 VRAM 传输
- **配置 2** ：按需加载模型部分，并将所有未使用的模型保留在保留 RAM 中，以便快速进行 VRAM 传输
- **配置文件 3** ：将整个当前模型加载到 VRAM 中（14B 模型需要 24GB）
- **配置文件 4** ：默认且推荐，按需加载模型部分，最灵活的选项
- **配置文件 4+** (4.5)：配置文件 4 的变体，可节省高达 1 GB 的 VRAM，但在某些配置下会稍慢
- **配置文件 5** ：最低 RAM 使用量

### 内存管理

```dsconfig
--perc-reserved-mem-max FLOAT # Max percentage of RAM for reserved memory (< 0.5)
```

## Lora 配置

```dsconfig
--loras PATH                 # Root folder for all LoRA subfolders (default: loras)
--lora-dir PATH              # Path to Wan t2v loras directory
--lora-dir-i2v PATH          # Path to Wan i2v loras directory
--lora-dir-hunyuan PATH      # Path to Hunyuan t2v loras directory
--lora-dir-hunyuan-i2v PATH  # Path to Hunyuan i2v loras directory
--lora-dir-hunyuan-1-5 PATH  # Path to Hunyuan 1.5 loras directory
--lora-dir-ltxv PATH         # Path to LTX Video loras directory
--lora-preset PRESET         # Load lora preset file (.lset) on startup
--check-loras                # Filter incompatible loras (slower startup)
```

注意：

- `--loras` 设置所有 LoRA 子文件夹使用的根文件夹（例如 `loras/wan` 、 `loras/flux` 等）。
- 特定的 `--lora-dir-*` 标志仅覆盖该系列的根目录。

## 生成设置

### 基本生成

```dsconfig
--seed NUMBER                # Set default seed value
--frames NUMBER              # Set default number of frames to generate
--steps NUMBER               # Set default number of denoising steps
--advanced                   # Launch with advanced mode enabled
```

### 高级生成

```mipsasm
--teacache MULTIPLIER        # TeaCache speed multiplier: 0, 1.5, 1.75, 2.0, 2.25, 2.5
```

## 接口和服务器选项

### 服务器配置

```dsconfig
--server-port PORT           # Gradio server port (default: 7860)
--server-name NAME           # Gradio server name (default: localhost)
--listen                     # Make server accessible on network
--share                      # Create shareable HuggingFace URL for remote access
--open-browser               # Open browser automatically when launching
```

### 接口选项

```css
--lock-config                # Prevent modifying video engine configuration from interface
--theme THEME_NAME           # UI theme: "default" or "gradio"
```

## 文件和目录选项

```dsconfig
--settings PATH              # Path to folder containing default settings for all models
--config PATH                # Config folder for wgp_config.json and queue.zip
--verbose LEVEL              # Information level 0-2 (default: 1)
```

## 示例

### 基本使用示例

```tcl
# Launch with specific model and loras
python wgp.py ----lora-preset mystyle.lset

# High-performance setup with compilation
python wgp.py --compile --attention sage2 --profile 3

# Low VRAM setup
python wgp.py --profile 4 --attention sdpa
```

### 服务器配置示例

```jboss
# Network accessible server
python wgp.py --listen --server-port 8080

# Shareable server with custom theme
python wgp.py --share --theme gradio --open-browser

# Locked configuration for public use
python wgp.py --lock-config --share
```

### 高级性能示例

```dsconfig
# Maximum performance (requires high-end GPU)
python wgp.py --compile --attention sage2 --profile 3 --preload 2000

# Optimized for RTX 2080Ti
python wgp.py --profile 4 --attention sdpa --teacache 2.0

# Memory-efficient setup
python wgp.py --fp16 --profile 4 --perc-reserved-mem-max 0.3
```

### 茶缓存配置

```apache
# Different speed multipliers
python wgp.py --teacache 1.5   # 1.5x speed, minimal quality loss
python wgp.py --teacache 2.0   # 2x speed, some quality loss
python wgp.py --teacache 2.5   # 2.5x speed, noticeable quality loss
python wgp.py --teacache 0     # Disable TeaCache
```

## 注意模式

### SDPA（默认）

```stylus
python wgp.py --attention sdpa
```
- 默认随 PyTorch 提供
- 与所有 GPU 高度兼容
- 性能中等

### Sage 注意力机制

```stylus
python wgp.py --attention sage
```
- 需要安装 Triton
- 比 SDPA 快 30%
- 小质量成本

### Sage2 注意力

```stylus
python wgp.py --attention sage2
```
- 需要 Triton 和 SageAttention 2.x
- 比 SDPA 快 40%
- 最佳性能选项

### Flash Attention

```stylus
python wgp.py --attention flash
```
- 可能需要 CUDA 内核编译
- 良好性能
- 在 Windows 上安装可能比较复杂

## 故障排除命令行

### 回退到基本设置

```jboss
# If advanced features don't work
python wgp.py --attention sdpa --profile 4 --fp16
```

### 调试模式

```jboss
# Maximum verbosity for troubleshooting
python wgp.py --verbose 2 --check-loras
```

### 内存问题调试

```apache
# Minimal memory usage
python wgp.py --profile 4 --attention sdpa --perc-reserved-mem-max 0.2
```

## 配置文件

### 设置文件

加载自定义设置：

```css
python wgp.py --settings /path/to/settings/folder
```

### 配置文件夹

为 UI 配置和自动保存队列使用单独的文件夹：

```css
python wgp.py --config /path/to/config
```

如果缺失， `wgp_config.json` 或 `queue.zip` 会从 WanGP 根目录加载一次，然后写入配置文件夹。

### Lora 预设

创建和分享 LoRa 配置：

```tcl
# Load specific preset
python wgp.py --lora-preset anime_style.lset

# With custom lora root
python wgp.py --loras /shared/loras --lora-preset mystyle.lset
```

## 环境变量

虽然不是命令行选项，但这些环境变量会影响行为：

- `CUDA_VISIBLE_DEVICES` - 限制可见的 GPU
- `PYTORCH_CUDA_ALLOC_CONF` - CUDA 内存分配设置
- `TRITON_CACHE_DIR` - Triton 缓存目录（用于 Sage 注意力）