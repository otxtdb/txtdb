---
title: "使用 WebDriver 获取页面"
source: "https://github.com/dgtlmoon/changedetection.io/wiki/Fetching-pages-with-WebDriver"
author:
  - "[[GitHub]]"
published:
created: 2025-12-01
description: "Best and simplest tool for website change detection, web page monitoring, and website change alerts. Perfect for tracking content changes, price drops, restock alerts, and website defacement monitoring—all for free or enjoy our SaaS plan! - Fetching pages with WebDriver · dgtlmoon/changedetection.io Wiki"
tags:
  - "clippings"
---


  
许多现代网页使用 JavaScript 来填充内容，它们更具动态性，有时需要真正的 Chrome 浏览器来获取内容，尽管许多网页会使用我们内置的“获取器”

  
后端可以通过内置[的 WebDriver](https://www.selenium.dev/documentation/webdriver/) 网络接口通过 Chrome（ChromeDriver）获取页面，这主要用于你观看的页面使用 JavaScript 渲染页面内容（基本的 fetcher 不执行任何 JS！）。最简单的方法是启用它，在本地[docker-compose.yml](https://github.com/dgtlmoon/changedetection.io/blob/master/docker-compose.yml)取消注释并重启 docker-compose。

  
**注意：**RaspberryPi 需要一个不同的 selenium/webdriver 运行器，请编辑你的`docker-compose.yml`并使用推荐的 RaspberryPi 镜像， [更多信息请见此处](https://github.com/dgtlmoon/changedetection.io/blob/271181968f4a303041164b719d3affbe2d1a5181/docker-compose.yml#L47) ——使用 `seleniarm/standalone-chromium:4.0.0-20211213` 代替 `selenium/standalone-chrome-debug:3.141.59`

```
browser-chrome:
        hostname: browser-chrome
        image: selenium/standalone-chrome-debug:3.141.59
        volumes:
            # Workaround to avoid the browser crashing inside a docker container
            # See https://github.com/SeleniumHQ/docker-selenium#quick-start
            - /dev/shm:/dev/shm
        restart: unless-stopped
```

  
如果使用 docker（而非 docker-compose），以下作将使 ChangeDetection.io chromium WebDriver 运行：

```
docker run -d \
  --name selenium \
  --restart unless-stopped \
  -p 4444:4444 \
  --shm-size="2g" \
  selenium/standalone-chrome-debug:3.141.59

docker run -d \
  --name changedetectionio \
  --restart unless-stopped \
  --link selenium \
  -p 5000:5000 \
  -e WEBDRIVER_URL="http://selenium:4444/wd/hub" \
  -v datastore-volume:/datastore \
  dgtlmoon/changedetection.io
```

  
然后访问 `/settings` 和 `[获取]` 标签，启用 WebDriver/Chrome 选项

![image](https://user-images.githubusercontent.com/275001/160246012-a9e886fd-d1ff-4038-9598-231cebb5d930.png)

  
WebDriver 接口的 URL 默认设置为 `WEBDRIVER_URL` 环境变量 `http://browser-chrome:4444/wd/hub`

### 树莓派笔记  
已知支持 RaspberryPi-4，使用 `seleniarm/standalone-chromium:4.0.0-20211213` 图片格式 `：` 请注意，目前该系统仅支持 64 位版本的 Raspbian OS。

- 把 ENV 变量 `FETCH_WORKERS` 设在低值，比如 2 或 3，因为开 10 个 Chrome 会话可能会对你的 rPi 负担太大

#   
Microsoft Windows - 原生运行 ChromeDriver（无 Docker）  
你需要安装 Chrome 的 WebDriver/ChromeDriver，这样会“监听”你的changedetection.py指令，并驱动浏览器获取结果。

  
这个配方最适合用 python/pip 安装程序安装软件 [https://github.com/dgtlmoon/changedetection.io/wiki/Microsoft-Windows#method-1-with-python-pip-install](https://github.com/dgtlmoon/changedetection.io/wiki/Microsoft-Windows#method-1-with-python-pip-install)——请有人帮忙添加基于 docker-compose 的安装说明:)

  
用 Chrome 99.0 版本测试

1. 安装 Chrome 浏览器 [https://www.google.com/chrome/](https://www.google.com/chrome/)
2. 安装正确的 Chromium WebDriver [https://chromedriver.chromium.org/下载](https://chromedriver.chromium.org/downloads) ，针对你安装的 Chrome 版本。
3. 解包并运行 WebDriver，它会运行/运行 Chrome 获取结果 ![image](https://user-images.githubusercontent.com/275001/160232808-9796464b-197d-4b09-8e31-61c43ab618da.png)
4. 设置系统范围或`命令`级别的环境变量，Changedetection.io 以便知道 ChromeDriver 的位置，从命令行 `set WEBDRIVER_URL=http://localhost:9515` 中获取
5. 用`changedetection.py` ![image](https://user-images.githubusercontent.com/275001/160232891-51c69279-8e2e-40d7-a0ef-56f495cf2bdf.png)
6. 别忘了为需要 Javascript 的网站或你喜欢用 Chrome 抓取的网站启用 Chrome 取材功能，如果环境变量设置正确，用户界面应该会显示“`http://localhost:9515`”。 ![image](https://user-images.githubusercontent.com/275001/160232926-70fee16f-634b-42cd-86c3-0ffaa5a0aa22.png)

  
你本不应该用浏览器访问这个功能，这只是让你的变更检测安装系统与 Chromedriver 通信时用的