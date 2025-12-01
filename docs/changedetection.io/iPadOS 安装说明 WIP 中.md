---
title: "iPadOS 安装说明 WIP 中"
source: "https://github.com/dgtlmoon/changedetection.io/wiki/iPadOS-Install-Notes---WIP"
author:
  - "[[GitHub]]"
published:
created: 2025-12-01
description: "Best and simplest tool for website change detection, web page monitoring, and website change alerts. Perfect for tracking content changes, price drops, restock alerts, and website defacement monitoring—all for free or enjoy our SaaS plan! - iPadOS Install Notes   WIP · dgtlmoon/changedetection.io Wiki"
tags:
  - "clippings"
---


  
版本：[https://github.com/dgtlmoon/changedetection.io/tree/0.39.22.1](https://github.com/dgtlmoon/changedetection.io/tree/0.39.22.1)

  
在 iPad（iPadOS 16.1）上使用 iSH 通过 PIP 安装。

  
构建失败，缺少多个依赖：

1. 请确保 libxml2 和 libxslt 开发包已安装 ✅
2. 密码学构建轮（pyproject.toml）......错误 ✅ — 错误：找不到 Rust 编译器（该包需要 Rust >=1.41.0.）
3. 关于密码学的额外错误——id 未成功运行。❌│ 退出码：1 ╰─> \[160 行输出\]

  
错误：命令“/usr/bin/gcc”失败，出口代码 1 \[输出结束\]

  
错误：密码学构建轮失败 无法构建密码学 错误：无法构建密码学轮，而密码学是安装pyproject.toml-based项目所必需的

  
build/temp.linux-i686-cpython-310/\_openssl.c：575：10：致命错误：openssl/opensslv.h：无此类文件或目录 575 |#include < openssl/opensslv.h> |^~~~~~~~~~~~~~~~~~~~ 合辑已终止。

  
建议调试协助：• 确保你安装了最新的 Rust 工具链：[https://cryptography.io/en/latest/installation.html#rust](https://cryptography.io/en/latest/installation.html#rust) • 如果你在本*版本*中遇到 Rust 问题，可以设置环境变量 `CRYPTOGRAPHY_DONT_BUILD_RUST=1` 。

  
\*\* 解决措施 \*\* 1： apk add libxslt-dev libxml2-dev ✅ 2： export CRYPTOGRAPHY\_DONT\_BUILD\_RUST=1 ✅ 3： a） apk 获取 python3-dev（不确定这是否解决了问题） ❌ b） apk 添加 rust ❌（大失败 - 导致 iSH 崩溃）[  
网页变更检测与通知](https://changedetection.io/)