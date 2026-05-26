---
title: "如何制作自己的重绘模型"
source: "https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/How-to-make-your-own-Inpainting-model"
author:
published:
created: 2026-05-19
description: "Stable Diffusion web UI. Contribute to AUTOMATIC1111/stable-diffusion-webui development by creating an account on GitHub."
tags:
  - "clippings"
taxonomy: { doc_category: [sd-webui] }
---
制作自己的重绘模型非常简单：

![screenshot](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/images/making-your-own-inpainting-model.png)

1. 前往“检查点合并器”
2. 选择“添加差异”
3. 将“乘数”设置为 1.0
4. 将"A"设置为官方的重绘模型（SD-v1.5-Inpainting）
5. 将"B"设置为您的模型
6. 将"C"设置为标准基础模型（SD-v1.5）
7. 名称可随意设置，建议命名为 (your model)\_inpainting
8. 设置其他首选值，即可能选择"Safetensors"和"Save as float16"。
9. 点击合并。
10. 在 img2img 重绘标签页中使用您的新模型。

此方法的工作原理是直接将重绘模型与您的模型的独特数据进行合并。请注意公式为 A + (B - C)，可将其解释为等同于 (A - C) + B。由于'A'代表 1.5-inpaint，'C'代表 1.5，因此 A - C 仅代表重绘逻辑，别无其他。所以公式即为（重绘逻辑）+（您的模型）。

### 更广泛的应用

这种“添加差异”的合并方法几乎适用于 WebUI 可以加载的所有机械结构独特的模型。  
请在功能页面查看它们！

#1 您现有的微调模型需要与独特模型的架构相匹配，即：Stable Diffusion 2 或 1。

#2 你还需要将独特的模型与基础模型进行对比。请从他们的 GitHub 上找出该基础模型是什么。

问：altdiffusion-m9 使用的是哪个基础模型？  
答：Stable Diffusion 1.4 模型

问：instructpix2pix 使用的是哪个基础模型？  
A：Stable Diffusion 1.5 模型

这些模型的神经网络/属性可与任何微调模型配合使用，就像著名的 ControlNet 网络的应用方式一样，只不过它们并未与主模型分离。

备注：

*您可能已经意识到，ControlNet 网络本身就已经能够完成其中许多任务。*

因此，以下是一些或许值得尝试的方法：

\-使用带有噪声偏移模型的更暗或更亮的照明效果  
\-使用 miniSD 模型在较小的 256 或 320 维度下生成与 512x512 相似的图像  
\-使用 altdiffusion-m9 模型使提示词在不同输入语言间更具确定性（该模型会替换 clip 模型）