---
title: "Fooocus 2.1.60: 官方动漫 和 真实支持"
source: "https://github.com/lllyasviel/Fooocus/discussions/679"
author:
published:
created: 2026-05-19
description: "Fooocus 2.1.60: Official Anime and Realistic Support"
tags:
  - "clippings"
taxonomy: { doc_category: [fooocus] }
---
在 2.1.60 版本之后，Fooocus 开始正式支持动漫和写实模型。（此前这是由用户实现的，但相对较难获得最佳效果，现在只需一键即可。）

现在我们将拥有3个启动器：  
[![image](https://private-user-images.githubusercontent.com/19834515/275099514-577a03bc-53d3-4f15-a160-e48996c9efbd.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxODA4MzMsIm5iZiI6MTc3OTE4MDUzMywicGF0aCI6Ii8xOTgzNDUxNS8yNzUwOTk1MTQtNTc3YTAzYmMtNTNkMy00ZjE1LWExNjAtZTQ4OTk2YzllZmJkLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA1MTklMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNTE5VDA4NDg1M1omWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTFmODQ0MGRmNWE5MjczNGZjMDEzYTkxYWQ1ZDBiMjA1YTMzZjc0OTRjNjUxYmMxNzg5MmJmMmRkZDc2ZjNjMWImWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.C2vdlzYI3yZFAgpDALt4HR4k74cIH5LP9YsPQkS-Mjs)](https://private-user-images.githubusercontent.com/19834515/275099514-577a03bc-53d3-4f15-a160-e48996c9efbd.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzkxODA4MzMsIm5iZiI6MTc3OTE4MDUzMywicGF0aCI6Ii8xOTgzNDUxNS8yNzUwOTk1MTQtNTc3YTAzYmMtNTNkMy00ZjE1LWExNjAtZTQ4OTk2YzllZmJkLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA1MTklMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNTE5VDA4NDg1M1omWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTFmODQ0MGRmNWE5MjczNGZjMDEzYTkxYWQ1ZDBiMjA1YTMzZjc0OTRjNjUxYmMxNzg5MmJmMmRkZDc2ZjNjMWImWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.C2vdlzYI3yZFAgpDALt4HR4k74cIH5LP9YsPQkS-Mjs)

如果你仍然只有一个启动器，可以运行“run.bat”，它会自动更新并为你提供所有三个启动器。

## 以下所有结果均使用种子12345和默认设置

**以下是实际性能。种子并非经过挑选。****下面的图片具有相似性（例如相同的人物、相同的姿势等），因为它们使用了相同的种子。这不是一个模型问题。**

## Fooocus 动画

### 1girl, garden    ### 1girl, dragon    ### 1girl, in classroom    ### 1girl, dark magic    ### 1girl, princess in the castle    ## Fooocus 真实

### portrait of old man in the room, closeup    ### a woman, New York city    ### a girl with beautiful eyes, closeup    ### The man in the forest, portrait## Linux 或纯 Python

如果你不用 bat，可以使用这些命令行：

```stylus
python entry_with_update.py --preset anime
python entry_with_update.py --preset realistic
```

如果你不想让脚本为你下载模型，模型的 URL 在这里：

Fooocus 动漫使用 SD1.5（DreamShaper\_8）来优化 SDXL（bluePencilXL），请注意"sd1.5-as-xl-refiner 算法"与其他软件不同——这是 Fooocus 独有的。以下是模型 URL：

```json
"checkpoint_downloads": {
    "bluePencilXL_v050.safetensors": "https://huggingface.co/lllyasviel/fav_models/resolve/main/fav/bluePencilXL_v050.safetensors",
    "DreamShaper_8_pruned.safetensors": "https://huggingface.co/Lykon/DreamShaper/resolve/main/DreamShaper_8_pruned.safetensors"
},
"embeddings_downloads": {
    "unaestheticXLv31.safetensors": "https://huggingface.co/lllyasviel/fav_models/resolve/main/fav/unaestheticXLv31.safetensors"
},
"lora_downloads": {
    "sd_xl_offset_example-lora_1.0.safetensors": "https://huggingface.co/stabilityai/stable-diffusion-xl-base-1.0/resolve/main/sd_xl_offset_example-lora_1.0.safetensors"
}
```

Fooocus 写实使用 Fooocus 锐化功能来增强 SDXL（realisticStockPhoto）：

```json
"checkpoint_downloads": {
    "realisticStockPhoto_v10.safetensors": "https://huggingface.co/lllyasviel/fav_models/resolve/main/fav/realisticStockPhoto_v10.safetensors"
},
"lora_downloads": {
    "SDXL_FILM_PHOTOGRAPHY_STYLE_BetaV0.4.safetensors": "https://huggingface.co/lllyasviel/fav_models/resolve/main/fav/SDXL_FILM_PHOTOGRAPHY_STYLE_BetaV0.4.safetensors"
}
```