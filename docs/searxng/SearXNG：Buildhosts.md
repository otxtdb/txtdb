---
title: "SearXNG：Buildhosts"
source: "https://docs.searxng.org/admin/buildhosts.html"
author:
published:
created: 2026-03-01
description:
tags:
  - "clippings"
taxonomy: { doc_category: [searxng] }
---

- [构建和开发工具](https://docs.searxng.org/admin/#build-and-development-tools)
- [构建文档](https://docs.searxng.org/admin/#build-docs)
- [检查 shell 脚本](https://docs.searxng.org/admin/#lint-shell-scripts)

从构建中获得最佳结果，建议在构建主机上安装额外的软件包（参见 [utils/searxng.sh](https://docs.searxng.org/utils/searxng.sh.html#searxng-sh)）。

## [构建和开发工具](https://docs.searxng.org/admin/#id2) [¶](https://docs.searxng.org/admin/#build-and-development-tools "Link to this heading")

一次性安装用于构建和开发任务的工具：

$ sudo \-H ./utils/searxng.sh install buildhost

这将安装 SearXNG 所需的软件包：

$ sudo \-H apt-get install \-y \\
    python3-dev python3-babel python3-venv python-is-python3 \\
    uwsgi uwsgi-plugin-python3 \\
    git build-essential libxslt-dev zlib1g-dev libffi-dev libssl-dev

$ sudo \-H pacman \-S \--noconfirm \\
    python python-pip python-lxml python-babel \\
    uwsgi uwsgi-plugin-python \\
    git base-devel libxml2

$ sudo \-H dnf install \-y \\
    python python-pip python-lxml python-babel python3-devel \\
    uwsgi uwsgi-plugin-python3 \\
    git @development-tools libxml2 openssl

以及构建文档和运行测试所需的软件包：

$ sudo \-H apt-get install \-y \\
    graphviz imagemagick texlive-xetex librsvg2-bin \\
    texlive-latex-recommended texlive-extra-utils fonts-dejavu \\
    latexmk shellcheck

$ sudo \-H pacman \-S \--noconfirm \\
    graphviz imagemagick texlive-bin extra/librsvg \\
    texlive-core texlive-latexextra ttf-dejavu shellcheck

$ sudo \-H dnf install \-y \\
    graphviz graphviz-gd ImageMagick librsvg2-tools \\
    texlive-xetex-bin texlive-collection-fontsrecommended \\
    texlive-collection-latex dejavu-sans-fonts dejavu-serif-fonts \\
    dejavu-sans-mono-fonts ShellCheck

## [构建文档](https://docs.searxng.org/admin/#id3) [¶](https://docs.searxng.org/admin/#build-docs "Link to this heading")

Sphinx 构建需要

- [ImageMagick](https://www.imagemagick.org/)
- [Graphviz](https://graphviz.gitlab.io/)
- [XeTeX](https://tug.org/xetex/)
- [dvisvgm](https://dvisvgm.de/)

大部分 Sphinx 需求是从 [git://setup.py](https://github.com/searxng/searxng/blob/master/setup.py) 安装的，文档可以从头开始使用 `make docs.html` 构建。为了更好的数学公式和图像处理，需要额外的软件包。所需的 [XeTeX](https://tug.org/xetex/) 不仅用于 PDF 创建，在构建 HTML 输出时也用于 [数学公式](https://docs.searxng.org/dev/reST.html#math) 。

  
为了能够在 Sphinx 中为 HTML 输出提供数学支持而不依赖 CDN，数学公式会被渲染为图像（`sphinx.ext.imgmath` 扩展）。

以下是 [git://docs/conf.py](https://github.com/searxng/searxng/blob/master/docs/conf.py) 文件中设置数学渲染器为 `imgmath` 的摘录：

html\_math\_renderer \= 'imgmath'
imgmath\_image\_format \= 'svg'
imgmath\_font\_size \= 14

如果你的文档构建（`make docs.html`）显示类似这样的警告：

WARNING: dot(1) not found, for better output quality install \\
         graphviz from https://www.graphviz.org
..
WARNING: LaTeX command 'latex' cannot be run (needed for math \\
         display), check the imgmath\_latex setting

你需要在你构建主机上安装额外的软件包，以获得更好的 HTML 输出（ [安装构建主机](https://docs.searxng.org/admin/#searxng-sh-install-buildhost) ）。

$ sudo apt install graphviz imagemagick texlive-xetex librsvg2-bin

$ sudo pacman \-S graphviz imagemagick texlive-bin extra/librsvg

$ sudo dnf install graphviz graphviz-gd ImageMagick texlive-xetex-bin librsvg2-tools

生成 PDF 输出还需要：

$ sudo apt texlive-latex-recommended texlive-extra-utils ttf-dejavu

$ sudo pacman \-S texlive-core texlive-latexextra ttf-dejavu

$ sudo dnf install \\
    texlive-collection-fontsrecommended texlive-collection-latex \\
    dejavu-sans-fonts dejavu-serif-fonts dejavu-sans-mono-fonts

## [检查 shell 脚本](https://docs.searxng.org/admin/#id4) [¶](https://docs.searxng.org/admin/#lint-shell-scripts "Link to this heading")

要检查 shell 脚本，我们使用 [ShellCheck](https://github.com/koalaman/shellcheck)——一个 shell 脚本静态分析工具（ [安装 buildhost](https://docs.searxng.org/admin/#searxng-sh-install-buildhost)）。

$ sudo apt install shellcheck