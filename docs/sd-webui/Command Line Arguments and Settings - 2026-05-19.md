---
title: "命令行参数与设置"
source: "https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Command-Line-Arguments-and-Settings"
author:
published:
created: 2026-05-19
description: "Stable Diffusion web UI. Contribute to AUTOMATIC1111/stable-diffusion-webui development by creating an account on GitHub."
tags:
  - "clippings"
taxonomy: { doc_category: [sd-webui] }
---
## 环境变量

| 名称 | 描述 |
| --- | --- |
| PYTHON | 设置 Python 可执行文件的自定义路径。 |
| VENV\_DIR | 指定虚拟环境的路径。默认为 `venv` 。特殊值 `-` 在不创建虚拟环境的情况下运行脚本。 |
| COMMANDLINE\_ARGS | 主程序的额外命令行参数。 |
| IGNORE\_CMD\_ARGS\_ERRORS | 设置为任意值，以便在遇到意外的命令行参数时程序不会报错退出。 |
| REQS\_FILE | 运行 `launch.py` 时将安装依赖的 `requirements.txt` 文件名，默认为 `requirements_versions.txt` 。 |
| TORCH\_COMMAND | 安装 PyTorch 的命令。 |
| INDEX\_URL | pip 的 `--index-url` 参数。 |
| TRANSFORMERS\_CACHE | transformers 库下载并保存与 CLIP 模型相关文件的目录路径。 |
| CUDA\_VISIBLE\_DEVICES | 在多显卡系统中，选择用于当前实例的 GPU。例如，若希望使用次要 GPU，请输入"1"。   （在 webui-user.bat 中 COMMANDLINE\_ARGS 之外添加新行）： `set CUDA_VISIBLE_DEVICES=0`   或者，直接在 `COMMANDLINE_ARGS` 中使用 `--device-id` 标志。 |
| SD\_WEBUI\_LOG\_LEVEL | 日志详细程度。支持 Python 内置的 `logging` 模块所支持的任意有效日志级别。若未设置，默认为 `INFO` 。 |
| SD\_WEBUI\_CACHE\_FILE | 缓存文件路径。如果未设置，则默认为根目录下的 `cache.json` 。 |
| SD\_WEBUI\_RESTAR | 由 `launcher script` （如 webui.bat、webui.sh）设置的值，用于通知 WebUI 重启功能可用 |
| SD\_WEBUI\_RESTARTING | 一个内部值，用于指示 WebUI 当前是否正在重启或重新加载，可用于禁用某些操作，例如自动启动浏览器。   设置为 `1` 可禁用自动启动浏览器   设置为 `0` 即使在重启时也会启用自动启动   某些扩展程序可能会使用此值实现类似功能。 |

### webui 用户

推荐设置环境变量是通过编辑 `webui-user.bat` （Windows）和 `webui-user.sh` （Linux）来实现：

- Windows 系统下的 \`--listen\`
- Linux 系统下的 \`--listen\`

例如，在 Windows 中：

```jboss
set COMMANDLINE_ARGS=--xformers --skip-torch-cuda-test --no-half-vae --api --ckpt-dir A:\\stable-diffusion-checkpoints
```

### 在线运行

使用 \`--listen\` 选项运行在线服务，您将获得一个 xxx.app.gradio 链接。这是在 Google Colab 中使用该程序的预期方式。您可以使用 \`--auth\` 标志为上述 Gradio 共享实例设置身份验证，并可选地提供多组以逗号分隔的用户名和密码。

### 在局域网内运行

使用 `--listen` 让服务器监听网络连接。这将允许局域网内的计算机访问界面，如果您配置了端口转发，互联网上的计算机也可以访问。示例地址： `http://192.168.1.3:7860` 其中"192.168.1.3"是本地 IP 地址。

使用 `--port xxxx` 让服务器监听特定端口，xxxx 为所需端口。请注意，所有低于 1024 的端口都需要 root/admin 权限，因此建议使用高于 1024 的端口。如果可用，默认端口为 7860。

### 在 CPU 上运行

仅使用 CPU 运行是可行的，但不推荐。速度非常慢，且没有 fp16 实现。

要运行，必须启用所有这些标志： `--use-cpu all --precision full --no-half --skip-torch-cuda-test`

尽管这是一种运行 WebUI 的可疑方式，由于生成速度极慢；但对于某些人来说，使用各种 AI 上采样工具和描述工具可能仍是有用的。

附加功能：

For the technically inclined, here are some steps a user provided to boost CPU performance:

[https://github.com/AUTOMATIC1111/stable-diffusion-webui/issues/10514](https://github.com/AUTOMATIC1111/stable-diffusion-webui/issues/10514)

[https://github.com/AUTOMATIC1111/stable-diffusion-webui/issues/10516](https://github.com/AUTOMATIC1111/stable-diffusion-webui/issues/10516)

## 所有命令行参数

| 命令行参数 | 值 | 默认值 | 描述 |
| --- | --- | --- | --- |
| **CONFIGURATION** |  |  |  |
| \-h, --help | 无 | 否 | 显示此帮助信息并退出。 |
| \--exit |  |  | 安装完成后终止 |
| \--data-dir | DATA\_DIR | ./ | 存储所有用户数据的基础路径 |
| \--models-dir | MODELS | 无 | 模型存储的基础路径；覆盖 --data-dir |
| \--config | CONFIG | configs/stable-diffusion/v1-inference.yaml | 构建模型的配置文件路径。 |
| \--ckpt | CKPT | model.ckpt | Stable Diffusion 模型检查点的路径；如果指定，该检查点将被添加到检查点列表中并加载。 |
| \--ckpt-dir | CKPT\_DIR | 无 | 存放 Stable Diffusion 检查点的目录路径。 |
| \--no-download-sd-model | 无 | 否 | 即使未找到模型，也不下载 SD1.5 模型。 |
| \--do-not-download-clip | 无 | 否 | 即使检查点不包含 CLIP 模型，也不下载 CLIP 模型。 |
| \--vae-dir | VAE\_PATH | 无 | 变分自编码器模型的路径 |
| \--vae-path | VAE\_PATH | 无 | 用作 VAE 的检查点；设置此参数 |
| \--gfpgan-dir | GFPGAN\_DIR | GFPGAN/ | GFPGAN 目录。 |
| \--gfpgan-model | GFPGAN\_MODEL | GFPGAN 模型文件名。 |  |
| \--codeformer-models-path | CODEFORMER\_MODELS\_PATH | models/Codeformer/ | 包含 CodeFormer 模型文件的目录路径。 |
| \--gfpgan-models-path | GFPGAN\_MODELS\_PATH | models/GFPGAN | 包含 GFPGAN 模型文件的目录路径。 |
| \--esrgan-models-path | ESRGAN\_MODELS\_PATH | models/ESRGAN | 包含 ESRGAN 模型文件的目录路径。 |
| \--bsrgan-models-path | BSRGAN\_MODELS\_PATH | models/BSRGAN | 包含 BSRGAN 模型文件的目录路径。 |
| \--realesrgan-models-path | REALESRGAN\_MODELS\_PATH | models/RealESRGAN | 包含 RealESRGAN 模型文件的目录路径。 |
| \--scunet-models-path | SCUNET\_MODELS\_PATH | models/ScuNET | 包含 ScuNET 模型文件的目录路径。 |
| \--swinir-models-path | SWINIR\_MODELS\_PATH | models/SwinIR | 包含 SwinIR 和 SwinIR v2 模型文件的目录路径。 |
| \--ldsr-models-path | LDSR\_MODELS\_PATH | models/LDSR | 包含 LDSR 模型文件的目录路径。 |
| \--dat-models-path | DAT\_\_MODELS\_PATH | models/DAT | 存放 DAT 模型文件的目录路径。 |
| \--lora-dir | LORA\_DIR | models/Lora | 存放 LoRA 网络的目录路径。 |
| \--clip-models-path | CLIP\_MODELS\_PATH | 无 | 存放 CLIP 模型文件的目录路径。 |
| \--embeddings-dir | EMBEDDINGS\_DIR | embeddings/ | 文本反转的嵌入目录（默认：embeddings）。 |
| \--textual-inversion-templates-dir | TEXTUAL\_INVERSION\_TEMPLATES\_DIR | textual\_inversion\_templates | 存放文本反转模板的目录。 |
| \--hypernetwork-dir | HYPERNETWORK\_DIR | models/hypernetworks/ | 超网络目录。 |
| \--localizations-dir | LOCALIZATIONS\_DIR | localizations/ | 本地化目录。 |
| \--styles-file | STYLES\_FILE | styles.csv | 样式文件的路径或通配符路径，允许多个条目。 |
| \--ui-config-file | UI\_CONFIG\_FILE | ui-config.json | 用于存储界面配置的文件名。 |
| \--no-progressbar-hiding | 无 | 否 | 不要在 Gradio 用户界面中隐藏进度条（如果在浏览器中使用硬件加速，隐藏它会降低机器学习性能）。 |
| \--ui-settings-file | UI\_SETTINGS\_FILE | config.json | 用于存储界面设置的文件名。 |
| \--allow-code | 无 | 否 | 允许从 Web UI 执行自定义脚本。 |
| \--share | 无 | 否 | 使用 `share=True` 以启用 Gradio，并通过其网站访问用户界面。 |
| \--listen | 无 | 否 | 使用 0.0.0.0 作为服务器名称启动 Gradio，允许响应网络请求。 |
| \--端口 | PORT | 7860 | 使用给定的服务器端口启动 Gradio；若端口号小于 1024，则需要 root/admin 权限；如果可用，默认值为 7860。 |
| \--hide-ui-dir-config | 无 | 否 | 隐藏 Web 界面中的目录配置。 |
| \--freeze-settings | 无 | 否 | 禁用所有设置的编辑功能 |
| \--freeze-settings-in-sections | 无 | 否 | 通过指定逗号分隔的列表（例如"保存图像、超分辨率”）来禁用对设置页面特定部分的编辑。设置名称列表可在 modules/shared\_options.py 文件中找到。 |
| \--freeze-specific-settings | 无 | 否 | 通过指定逗号分隔的列表（如"samples\_save,samples\_format"）来禁用对各个设置的编辑。设置名称列表可在 config.json 文件中找到。 |
| \--enable-insecure-extension-access | 无 | 否 | 无论其他选项如何，始终启用扩展程序标签页。 |
| \--gradio-debug | 无 | 否 | 使用 `--debug` 选项启动 gradio。 |
| \--gradio-auth | GRADIO\_AUTH | 无 | 设置 Gradio 的认证方式，例如 `username:password` ；或者用逗号分隔多个，如 `u1:p1,u2:p2,u3:p3` 。 |
| \--gradio-auth-path | GRADIO\_AUTH\_PATH | 无 | 设置 Gradio 认证文件路径，例如 `/path/to/auth/file` ，与 `--gradio-auth` 的相同认证格式。 |
| \--disable-console-progressbars | 无 | 否 | 不要向控制台输出进度条。 |
| \--enable-console-prompts | 无 | 否 | 生成时向控制台打印提示词（适用于 txt2img 和 img2img）。 |
| \--api | 无 | 否 | 使用 API 启动 Web 界面。 |
| \--api-auth | API\_AUTH | 无 | 设置 API 的认证方式，如 `username:password` ；或像 `u1:p1,u2:p2,u3:p3` 那样用逗号分隔多个。 |
| \--api-log | 无 | 否 | 启用所有 API 请求的日志记录。 |
| \--nowebui | 无 | 否 | 仅启动 API，不启动用户界面。 |
| \--ui-debug-mode | 无 | 否 | 不要加载模型以快速启动界面。 |
| \--device-id | DEVICE\_ID | 无 | 选择要使用的默认 CUDA 设备（可能需要先导出 `CUDA_VISIBLE_DEVICES=0,1` 等）。 |
| \--administrator | 无 | 否 | 管理员权限。 |
| \--cors-allow-origins | CORS\_ALLOW\_ORIGINS | 无 | 以逗号分隔列表形式允许的跨域源（不含空格）。 |
| \--cors-allow-origins-regex | CORS\_ALLOW\_ORIGINS\_REGEX | 无 | 允许跨域资源共享（CORS）的源，格式为单个正则表达式。 |
| \--tls-keyfile | TLS\_KEYFILE | 无 | 部分启用 TLS，需要 `--tls-certfile` 才能完全运行。 |
| \--tls-certfile | TLS\_CERTFILE | 无 | 部分启用 TLS，需要 `--tls-keyfile` 才能完全运行。 |
| \--disable-tls-verify | 无 | 否 | 启用时，允许使用自签名证书。 |
| \--subpath | SERVER\_SUB\_PATH | 自定义 Gradio 的子路径，需配合反向代理使用。 |  |
| \--server-name | SERVER\_NAME | 无 | 设置服务器的主机名。 |
| \--no-gradio-queue | 无 | 否 | 禁用 Gradio 队列；导致网页使用 HTTP 请求而非 WebSocket；这是早期版本的默认设置。 |
| \--gradio-allowed-path | 无 | 无 | 添加路径到 Gradio 的 `allowed_paths` ；使其能够从此处提供文件。 |
| \--no-hashing | 无 | 否 | 禁用检查点的 SHA-256 哈希计算，以提升加载性能。 |
| \--skip-version-check | 无 | 否 | 不检查 torch 和 xformers 的版本。 |
| \--skip-python-version-check | 无 | 否 | 不检查 Python 版本。 |
| \--skip-torch-cuda-test | 无 | 否 | 不检查 CUDA 是否能正常工作。 |
| \--skip-install | 无 | 否 | 跳过软件包的安装。 |
| \--loglevel | 无 | 无 | 日志级别；选项之一：CRITICAL、ERROR、WARNING、INFO、DEBUG |
| \--log-startup | 无 | 否 | launch.py 参数：打印启动时的详细日志 |
| \--api-server-stop | 无 | 否 | 通过 API 启用服务器停止/重启/终止功能 |
| \--timeout-keep-alive | int | 30 | 设置 uvicorn 的 timeout\_keep\_alive |
| **PERFORMANCE** |  |  |  |
| \--xformers | 无 | 否 | 启用 xformers 以处理交叉注意力层。 |
| \--force-enable-xformers | 无 | 否 | 无论检查代码是否认为可以运行，都启用 xformers 以处理交叉注意力层；如果此功能无法正常工作，请勿提交错误报告。 |
| \--xformers-flash-attention | 无 | 否 | 启用 xformers 与 Flash Attention 以提高可复现性（仅支持 SD2.x 或其变体）。 |
| \--opt-sdp-attention | 无 | 否 | 启用缩放点积交叉注意力层优化；需要 PyTorch 2.\* |
| \--opt-sdp-no-mem-attention | False | None | 启用缩放点积交叉注意力层优化（不使用内存高效注意力），使图像生成具有确定性；需要 PyTorch 2.\* |
| \--opt-split-attention | 无 | 否 | 强制启用 Doggettx 的交叉注意力层优化。默认情况下，CUDA 支持的系统会开启此功能。 |
| \--opt-split-attention-invokeai | 无 | 否 | 强制启用 InvokeAI 的交叉注意力层优化。默认情况下，当 CUDA 不可用时该功能处于开启状态。 |
| \--opt-split-attention-v1 | 无 | 否 | 启用旧版本的分割注意力优化，该版本不会消耗所有可用的显存。 |
| \--opt-sub-quad-attention | 无 | 否 | 启用内存高效的次二次交叉注意力层优化。 |
| \--sub-quad-q-chunk-size | SUB\_QUAD\_Q\_CHUNK\_SIZE | 1024 | 用于子二次交叉注意力层优化的查询块大小。 |
| \--sub-quad-kv-chunk-size | SUB\_QUAD\_KV\_CHUNK\_SIZE | 无 | 用于子二次交叉注意力层优化的 KV 块大小。 |
| \--sub-quad-chunk-threshold | SUB\_QUAD\_CHUNK\_THRESHOLD | 无 | 用于次二次方交叉注意力层优化中分块处理的显存阈值百分比。 |
| \--opt-channelslast | 无 | 否 | 启用针对 4D 张量的替代布局，可能仅在配备 Tensor Core 的 Nvidia 显卡（16xx 及更高版本）上提升推理速度。 |
| \--disable-opt-split-attention | 无 | 否 | 强制禁用交叉注意力层优化。 |
| \--disable-nan-check | 无 | 否 | 不检查生成的图像或潜在空间是否包含 NaN；在 CI 中无检查点运行时很有用。 |
| \--use-cpu | {all, sd, interrogate, gfpgan, bsrgan, esrgan, scunet, codeformer} | 无 | 为指定模块使用 CPU 作为 PyTorch 设备。 |
| \--use-ipex | 无 | 否 | 使用 Intel XPU 作为 PyTorch 设备 |
| \--no-half | 无 | 否 | 不将模型切换至 16 位浮点数。 |
| \--precision | {full, half, autocast} | autocast | 在此精度下进行评估。 |
| \--no-half-vae | 无 | 否 | 不要将 VAE 模型切换为 16 位浮点数。 |
| \--upcast-sampling | 无 | 否 | 提升采样精度。在 `--no-half` 下无效。通常会产生与 `--no-half` 相似的结果，但性能更好且占用内存更少。 |
| \--medvram | 无 | 否 | 启用 Stable Diffusion 模型优化，以牺牲部分性能为代价换取较低的显存占用。 |
| \--medvram-sdxl | 无 | 否 | 仅针对 SDXL 模型启用 `--medvram` 优化 |
| \--lowvram | 无 | 否 | 启用 Stable Diffusion 模型优化，以大幅降低速度为代价换取极低的显存占用。 |
| \--lowram | 无 | 否 | 将 Stable Diffusion 检查点权重加载到显存而非内存中。 |
| \--disable-model-loading-ram-optimization | 无 | 否 | 禁用一种在加载模型时减少内存使用的优化功能 |
| **FEATURES** |  |  |  |
| \--自动启动 | 无 | 否 | 启动时在系统默认浏览器中打开 Web UI 网址。 |
| \--theme | 无 | 未设置 | 使用指定的主题打开 Web UI（ `light` 或 `dark` ）。如果未指定，则使用浏览器的默认主题。 |
| \--use-textbox-seed | 无 | 否 | 在用户界面中使用文本框输入种子（不支持上下调整，但可输入长种子）。 |
| \--disable-safe-unpickle | 无 | 否 | 禁用对 PyTorch 模型进行恶意代码检查。 |
| \--ngrok | NGROK | 无 | ngrok 认证令牌，作为 gradio `--share` 的替代方案。 |
| \--ngrok-region | NGROK\_REGION | us | ngrok 启动所在的区域。 |
| \--ngrok-options | NGROK\_OPTIONS | 无 | 以 JSON 格式传递给 ngrok 的选项，例如： `{"authtoken_from_env":true, "basic_auth":"user:password", "oauth_provider":"google", "oauth_allow_emails":"user@asdf.com"}` |
| \--update-check | 无 | 无 | 启动时，通知您的 Web UI 版本（提交记录）是否与当前主分支保持最新。 |
| \--update-all-extensions | 无 | 无 | 启动时，它会拉取您已安装的所有扩展的最新更新。 |
| \--reinstall-xformers | 无 | 否 | 强制重新安装 xformers。升级时很有用，但升级后请将其移除，否则将无限循环重装 xformers。 |
| \--reinstall-torch | 无 | 否 | 强制重新安装 PyTorch。可用于升级，但升级后请移除该选项，否则将永久重复安装 PyTorch。 |
| \--tests | TESTS | 否 | 运行测试以验证 Web UI 功能，详见 Wiki 主题获取更多信息。 |
| \--no-tests | 无 | 否 | 即使指定了 `--tests` 选项，也不要运行测试。 |
| \--dump-sysinfo | 无 | 否 | launch.py 参数：将受限的系统信息文件（不包含扩展程序和选项的信息）写入磁盘并退出。 |
| \--disable-all-extensions | 无 | 否 | 禁用所有扩展程序的运行 |
| \--disable-extra-extensions | 无 | 否 | 禁用所有非内置扩展程序的运行 |
| \--skip-load-model-at-start | 无 | 否 | 如果在 Web 启动时加载模型，仅在 --nowebui 参数下生效 |
| \--unix-filenames-sanitization | 无 | 否 | 允许文件名中包含除 '/' 以外的任何符号。可能与浏览器和文件系统发生冲突 |
| \--filenames-max-length | 整数 | 128 | 保存图像的文件名最大长度，更长的文件名将被截断。如果覆盖此设置，可能会引发文件系统问题 |
| \--no-prompt-history | 无 | 否 | 禁用从上次生成读取提示的功能；禁用 `--data-path/params.txt` |
| **已废弃选项** |  |  |  |
| \--show-negative-prompt | 无 | 否 | 已不再有效。 |
| \--deepdanbooru | 无 | 否 | 已不再有效。 |
| \--unload-gfpgan | 无 | 否 | 不再有效。 |
| \--gradio-img2img-tool | GRADIO\_IMG2IMG\_TOOL | 无 | 不再有效。 |
| \--gradio-inpaint-tool | GRADIO\_INPAINT\_TOOL | 无 | 不再有效。 |
| \--gradio-queue | 无 | 否 | 不再有效。 |
| \--add-stop-route | 无 | 否 | 已不再有效。 |
| \--always-batch-cond-uncond | 无 | 否 | 已不再有效，请移至 UI 下的 `Setting > Optimizations` |
| \--max-batch-count | MAX\_BATCH\_COUNT | 16 | 已不再有效。已移至 `ui-config.json` `txt2img/Batch count/maximum` `img2img/Batch count/maximum` [用户界面自定义](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/User-Interface-Customizations#ui-element-dafault-value-and-range-limit-step-size) |