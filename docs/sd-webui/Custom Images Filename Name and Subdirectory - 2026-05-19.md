---
title: "自定义文件名及子目录"
source: "https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Custom-Images-Filename-Name-and-Subdirectory"
author:
published:
created: 2026-05-19
description: "Stable Diffusion web UI. Contribute to AUTOMATIC1111/stable-diffusion-webui development by creating an account on GitHub."
tags:
  - "clippings"
taxonomy: { doc_category: [sd-webui] }
---
> 以下信息涉及图像文件名和子目录名称，而非 `Paths for saving \ Output directories`

### 默认情况下，当“图像文件名模式”为空时，Web UI 会将图像保存至输出目录及输出归档中，其文件名结构为

Images: `[number]-[seed]` 或 `[number]-[seed]-[prompt_spaces]`

> 启用“保存时给文件名添加编号”（默认开启）时，会自动添加 `[number]-` 前缀，它本身并非一种模式。

```basic
01234-987654321-((masterpiece)), ((best quality)), ((illustration)), extremely detailed,style girl.png
```

压缩包： `[datetime]_[[model_name]]_[seed]-[seed_last]`

```apache
20230530133149_[v1-5-pruned-emaonly]_987654321-987654329.zip
```

如果用户希望使用不同的图像文件名、可选的子目录以及压缩包文件名，也可以进行设置。

图像文件名模式可在以下位置配置。

`settings tab` > `Saving images/grids` > `Images filename pattern`

子目录可在设置中配置。

`settings tab` > `Saving to a directory` > `Directory name pattern`

ZIP 压缩包可在设置中配置。

`settings tab` > `Saving images/grids` > `Archive filename pattern`

## 模式

Web-Ui 提供了多种可作为占位符的模式，用于将信息插入文件名或子目录中，用户可以将这些模式组合使用，从而生成符合其使用需求的文件名。

| 模式 | 描述 | 示例 |
| --- | --- | --- |
| `[seed]` | 种子 | 1234567890 |
| `[seed_first]` | 批次的首个种子或单张图像的种子 | \[1234567890,1234567891,1234567892,1234567893\] -> 1234567890   \[1234567891\] -> 1234567891 |
| `[seed_last]` | 批次的首个种子 | \[1234567890,1234567891,1234567892,1234567893\] -> 1234567893 |
| `[steps]` | 步数 | 20 |
| `[cfg]` | CFG 比例 | 7 |
| `[sampler]` | 采样方法 | 欧拉 A |
| `[model_name]` | 模型名称 | sd-v1-4 |
| `[model_hash]` | 提示词 SHA-256 哈希值的前 8 个字符 | 7460a6fa |
| `[width]` | 图像宽度 | 512 |
| `[height]` | 图像高度 | 512 |
| `[styles]` | 所选风格的名称 | 我的风格名称 |
| `[date]` | 计算机日期的 ISO 格式 | 2022-10-24 |
| `[datetime]` | 以"%Y%m%d%H%M%S"格式表示的日期时间 | 20221025013106 |
| `[datetime<Format>]` | 以指定<Format>格式表示的日期时间 | \[datetime<%Y%m%d\_%H%M%S\_%f>\]   20221025\_014350\_733877 |
| `[datetime<Format><TimeZone>]` | 指定时区 <Time Zone> 下的特定日期时间，格式为 <Format> | \[datetime<%Y%m%d\_%H%M%S\_%f><Asia/Tokyo>\]\`   20221025\_014350\_733877 |
| `[job_timestamp]` | 任务开始时间为 "%Y%m%d%H%M%S" | 20221025013106 |
| `[prompt_no_styles]` | 不带风格的提示词 | 1girl, 白色空间，((非常重要)), \[不重要\], (某些值\_1.5), (随便什么), 结束 |
| `[prompt_spaces]` | 带风格的提示词 | 1girl, 白色空间，((非常重要)), \[不重要\], (某些值\_1.5), (随便什么), 结束   , (((水晶纹理头发)))，((( |
| `[prompt]` | 带样式的提示词， `Space bar` 替换为 `_` | 1girl,\_\_\_白色空间，\_((非常重要)),\_\[不重要\],\_(某些数值 1.5),\_(随便),\_结尾，\_(((水晶纹理头发)))，((( |
| `[prompt_words]` | 带样式的提示词，已移除括号和逗号 | 1 gir 白色空间非常重要，不重要，某些值 1 5 无论结局如何，水晶纹理头发，极其详细 |
| `[prompt_hash]`   `[prompt_hash<N>]` | 提示词 SHA-256 哈希值的前 8 位或 `N` 个字符 | 1girl -> 6362d0d2   (1girl:1.1) -> 0102e068 |
| `[negative_prompt_hash]`   `[negative_prompt_hash<N>]` | 负面提示词 SHA-256 哈希值的前 8 位或 `N` 个字符 | 1girl -> 6362d0d2   (1girl:1.1) -> 0102e068 |
| `[full_prompt_hash]`   `[full_prompt_hash<N>]` | 前 8 个或 `N` 个字符为 `<prompt> <negative_prompt>` 's SHA-256 哈希值 | 1girl -> 6362d0d2   (1girl:1.1) -> 0102e068 |
| `[clip_skip]` | CLIP 在最后一层停止 | 1 |
| `[randn_source]` | 随机数生成器来源 | CPU |
| `denoising` | 去噪强度（如适用） | 0.5 |
| `[batch_number]` | 单个批量任务中的第 N 张图片 | BatchNo\_\[batch\_number\] -> BatchNo\_3 |
| `[batch_size]` | 批量大小 | \[1234567890,1234567891,1234567892,1234567893\] -> 4 |
| `[generation_number]` | 整个任务中的第 N 张图片 | GenNo\_\[生成次数\] -> GenNo\_9 |
| `[hasprompt<prompt1\|default><prompt2>...]` | 如果提示中指定了 `prompt` ，则会将 `prompt` 添加到文件名中；否则将 `default` 添加到文件名中（ `default` 可以为空） | \[hasprompt\] -> girl   \[hasprompt<女孩 \| 无女孩><男孩 \| 无男孩>\] -> 女孩无男孩 |
| `[user]` | 用于在使用 `--gradio-auth username:pass 时登录 WebUI 的用户名` | 用户名 |
| `[image_hash]`   `[image_hash<N>]` | 图像的前 `N` 个字符或完整的 SHA-256 哈希值（指图像本身，而非文件） | 484a1e7a07e7573a9081ab6a527990bb4d410dc3 |
| `[none]` | 覆盖默认设置，因此您可以仅获取序列号 |  |

如果 `<Format>` 为空或无效，将使用默认时间格式"%Y%m%d%H%M%S"提示：您可以在 `<Format>` 中使用额外字符作为标点符号，例如 `_ -`

如果 `<TimeZone>` 为空或无效，将使用默认的系统时区

如果 `batch size` 为 1，则 `[batch_number]` 、 `[seed_last]` 以及前一段文本将不会被添加到文件名中。

如果 `batch size` x `batch count` 为 1，则 \[generation\_number\] 以及前一段文本将不会被添加到文件名中。

`[batch_number]` 和 `[generation_number]` 以及前一段文本将不会被添加到 zip 归档的文件名中。

上述 `[prompt]` 示例所使用的提示词和风格：

```scss
1girl,   white space, ((very important)), [not important], (some value:1.5), (whatever), the end
```

已选风格：

```bash
(((crystals texture Hair)))，(((((extremely detailed CG))))),((8k_wallpaper))
```

注意：上述提到的 `Styles` 指的是生成按钮下方的两个下拉菜单

### 日期时间格式化详情

参考 Python 文档以获取更多有关格式代码的详细信息

### 时区详细信息

有效时区的参考列表

### 如果提示过长，将会被截断

这是由于您的计算机具有最大文件长度限制

## 保存时添加/删除文件名中的数字

您可以通过取消勾选下方的复选框来移除前缀数字

`Settings` > `Saving images/grids` > `Add number to filename when saving`

带前缀数字

```scss
00123-\`987654321-((masterpiece)).png
```

不带前缀数字

```scss
987654321-((masterpiece)).png
```

### 注意

前缀数字的作用是确保保存的图像文件名具有唯一性。如果您决定不使用前缀数字，请确保您的模式能够生成唯一的文件名，否则文件可能会被覆盖。

通常，精确到秒的时间戳能够保证文件名唯一。

```mel
[datetime<%Y%m%d_%H%M%S>]-[seed]
```

```apache
20221025_014350-281391998.png
```

但某些自定义脚本可能会在同一批次中使用相同的种子生成多张图片，

在这种情况下，同时使用 `%f` 和 `Microsecond as a decimal number, zero-padded to 6 digits. 会更安全。`

```mel
[datetime<%Y%m%d_%H%M%S_%f>]-[seed]
```

```dns
20221025_014350_733877-281391998.png
```

## 文件名模式示例

如果您在多台机器上运行 Web-Ui（例如 Google Colab 和您自己的电脑），您可能希望使用时间作为文件名前缀。这样在下载文件时，可以将它们放入同一个文件夹中。

此外，由于您不知道 Google Colab 使用的是哪个时区，因此需要指定时区。

```mel
[datetime<%Y%m%d_%H%M%S_%f><Asia/Tokyo>]-[seed]-[prompt_words]
```

```apache
20221025_032649_058536-3822510847-1girl.png
```

设置子目录的日期也可能很有用，这样就不会让一个文件夹包含过多的图像

```cos
[datetime<%Y-%m-%d><Asia/Tokyo>]
```

```apache
2022-10-25
```