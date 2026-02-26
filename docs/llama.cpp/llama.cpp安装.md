---
title: "llama.cpp安装"
source: "https://github.com/ggml-org/llama.cpp/wiki#install"
author:
  - "[[GitHub]]"
published:
created: 2026-02-26
description: "LLM inference in C/C++. Contribute to ggml-org/llama.cpp development by creating an account on GitHub."
tags:
  - "clippings"
taxonomy: { doc_category: [llama.cpp] }
---
## 安装

### [ArchLinux](https://aur.archlinux.org/packages/llama-cpp)
yay -S llama.cpp
yay -S llama.cpp-cuda
yay -S llama.cpp-hip
yay -S llama.cpp-vulkan

### Nix
nix run github:ggerganov/llama.cpp
nix run 'github:ggerganov/llama.cpp#opencl'

### NixOS
{ config, pkgs, ... }:
{
  nixpkgs.config.packageOverrides \= pkgs: {
      llama-cpp \= (
        builtins.getFlake "github:ggerganov/llama.cpp"
      ).packages.${builtins.currentSystem}.default;
    };
  };
  environment.systemPackages \= with pkgs; \[ llama-cpp \]
}

### Android Termux
等待 [https://github.com/termux/termux-packages/pull/17457](https://github.com/termux/termux-packages/pull/17457).

apt install llama-cpp

### Windows Msys2
pacman -S llama-cpp

### Debian (Ubuntu)
git clone --depth=1 https://github.com/ggerganov/llama.cpp
cd llama.cpp
cmake -Bbuild
cmake --build build -D...
cd build
cpack -G DEB
dpkg -i \*.deb

### Redhat
git clone --depth=1 https://github.com/ggerganov/llama.cpp
cd llama.cpp
cmake -Bbuild
cmake --build build -D...
cd build
cpack -G RPM
rpm -i \*.rpm
