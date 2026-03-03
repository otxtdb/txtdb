---
title: "将 Perplexica 更新到最新版本"
source: "https://github.com/ItzCrazyKns/Perplexica/blob/master/docs/installation/UPDATING.md"
author:
  - "[[ItzCrazyKns]]"
published:
created: 2026-03-01
description: "Perplexica is an AI-powered answering engine. Contribute to ItzCrazyKns/Perplexica development by creating an account on GitHub."
tags:
  - "clippings"
taxonomy: { doc_category: [perplexica] }
---
要更新 Perplexica 到最新版本，请按照以下步骤操作：

## 对于 Docker 用户（使用预构建镜像）
只需拉取最新镜像并重启你的容器：

docker pull itzcrazykns1337/perplexica:latest
docker stop perplexica
docker rm perplexica
docker run -d -p 3000:3000 -v perplexica-data:/home/perplexica/data --name perplexica itzcrazykns1337/perplexica:latest

对于精简版：

docker pull itzcrazyk
ns1337/perplexica:slim-latest
docker stop perplexica
docker rm perplexica
docker run -d -p 3000:3000 -e SEARXNG\_API\_URL=http://your-searxng-url:8080 -v perplexica-data:/home/perplexica/data --name perplexica itzcrazykns1337/perplexica:slim-latest

更新完成后，请访问 [http://localhost:3000](http://localhost:3000/) 并验证最新更改。您的设置将自动保留。

## 对于 Docker 用户（从源代码构建）
1. 前往你的 Perplexica 目录并拉取最新更改：
	cd Perplexica
	git pull origin master
2. 重新构建 Docker 镜像：
	docker build -t perplexica .
3. 停止并移除旧容器，然后启动新容器：
	docker stop perplexica
	docker rm perplexica
	docker run -p 3000:3000 -p 8080:8080 --name perplexica perplexica
4. 命令完成后，前往 [http://localhost:3000](http://localhost:3000/) 验证最新更改。

## 对于非 Docker 用户
1. 导航到你的 Perplexica 目录并拉取最新更改：
	cd Perplexica
	git pull origin master
2. 安装任何新的依赖项：
	npm i
3. 重新构建应用程序：
	npm run build
4. 重启应用程序：
	npm run start
5. 前往 [http://localhost:3000](http://localhost:3000/) 并验证最新更改。您的设置将自动保留。