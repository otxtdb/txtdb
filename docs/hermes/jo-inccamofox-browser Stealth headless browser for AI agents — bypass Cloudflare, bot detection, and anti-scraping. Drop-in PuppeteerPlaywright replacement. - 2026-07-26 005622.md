---
title: "jo-inc/camofox-browser: Stealth headless browser for AI agents — bypass Cloudflare, bot detection, and anti-scraping. Drop-in Puppeteer/Playwright replacement."
source: "https://github.com/jo-inc/camofox-browser"
author:
published:
created: 2026-07-26
description: "Stealth headless browser for AI agents — bypass Cloudflare, bot detection, and anti-scraping. Drop-in Puppeteer/Playwright replacement. - jo-inc/camofox-browser"
tags:
  - "clippings"
taxonomy: { doc_category: [hermes] }
---
## jo-inc/camofox-browser：专为人工智能应用设计的隐形无头浏览器——能够绕过 Cloudflare 的过滤、机器人检测以及反爬虫机制。可直接替代 Puppeteer/Playwright 工具使用。

[![camofox-browser](https://github.com/jo-inc/camofox-browser/raw/master/fox.png)](https://github.com/jo-inc/camofox-browser/blob/master/fox.png)

## camofox 浏览器

**专为人工智能代理设计的反检测浏览器服务器，由 Camoufox 提供技术支持。**

建立在 Camoufox 的基础上——Camoufox 是一款基于 Firefox 开发的软件，具有在 C++层面实现指纹识别欺骗的功能。

> [![Jo](https://github.com/jo-inc/camofox-browser/raw/master/jo-logo.png)](https://askjo.ai/?ref=camofox)
> 
> 该产品由开发了 jo 的团队打造。jo 是一种个人 AI 助手：它一部分在用户的 Mac 电脑上运行，另一部分则运行在专为你准备的云端服务器上——而且完全无需任何维护工作。该产品可在 macOS、Telegram、WhatsApp 和电子邮件平台上使用。快来免费试用吧！

```
git clone https://github.com/jo-inc/camofox-browser && cd camofox-browser
npm install && npm start
# -> http://localhost:9377
```

---

## 为什么

AI 智能体需要能够浏览真实的网页。Playwright 浏览器会被封锁。无头 Chrome 浏览器也会被识别出来。那些用于隐藏身份的插件，其实也相当于一种“指纹识别手段”。

Camoufox 在 C++实现层面对 Firefox 进行了修改—— `navigator.hardwareConcurrency` 、WebGL 渲染器、AudioContext、屏幕几何信息、WebRTC 等功能，都在 JavaScript 能够感知到之前就被伪装起来了。没有任何额外的插件或封装层，完全不会被察觉。

该项目将那个引擎封装在一个为各种代理程序而设计的 REST API 中：使用易于理解的格式来呈现信息，而非冗长的 HTML 代码；提供稳定的元素引用，方便用户进行点击操作；同时还提供了针对常见网站的搜索功能。

## 特点/特色

- C++反检测功能——能够绕过 Google、Cloudflare 以及大多数机器人检测系统。
- 元素引用—— `e1` 、 `e2` 、 `e3` 这些稳定的标识符，可确保可靠的交互效果。
- 高效利用存储空间——与原始 HTML 格式相比，可访问性快照的体积缩小了~90%
- 可以在任何设备上运行——由于采用了懒加载的浏览器机制以及自动关闭功能，因此在空闲状态下，内存使用量可保持在 1001#40MB 左右。该系统旨在与其他设备共享硬件资源——比如树莓派、5 美元级的 VPS 服务器或共享基础设施。
- 会话隔离——为每位用户单独存储 Cookie/数据
- Cookie 导入——导入 Netscape 格式的 Cookie 文件，以便进行身份验证后的浏览操作
- 代理服务器与地理 IP 技术——通过位于居民区的代理服务器来传输流量，同时自动适配相应的地区/时区设置
- 结构化日志记录——包含请求 ID 的 JSON 格式日志记录，有助于实现生产环境中的可观测性分析
- YouTube 文字记录功能——利用 yt-dlp 工具，可以从任何 YouTube 视频中提取文字内容，无需 API 密钥。
- 搜索宏： `@google_search` 、 `@youtube_search` 、 `@amazon_search` 、 `@reddit_subreddit` ，以及另外 10 个宏。
- 快照截图——除了无障碍功能相关的截图外，还需附上经过 Base64 编码的 PNG 格式截图。
- 大页面处理——基于偏移量的自动快照截断与分页功能
- 下载捕获功能——可以捕获浏览器的下载内容，并通过 API 将其获取出来（可选择以 base64 格式进行编码）。
- DOM 图像提取——列出 `<img>` 的 src/alt 属性值，同时可选择性地返回内嵌数据 URL。
- 可部署在任何地方——Docker、Fly.io、Railway 均可支持。
- VNC 交互式登录——通过 noVNC 以可视化方式登录各个网站；同时可导出存储状态，以便后续重复使用。
- OpenAPI 文档——在 `/openapi.json` 处可查看自动生成的规范文档，在 `/docs 处可查看交互式文档。`
- 结构化提取——使用 JSON 模式进行提取，该模式通过 `x-ref` 将各属性与对应的快照引用关联起来。
- 会话追踪——用户可在每次会话中选择是否启用该功能。Playwright 会捕获相关数据，包括屏幕截图、DOM 结构信息以及网络请求数据。同时，还提供了 API 接口，用于列出、获取和删除这些追踪数据。
- 遥测功能——通过 GitHub Issues 实现自动化的、匿名化的崩溃/挂机情况报告。该功能有助于确定导致故障的网站以及常见的故障模式。对于私有域名，系统会对其进行 HMAC 哈希处理；同时，路径和参数会被删除，令牌和 IP 地址也会被遮盖。如需取消该功能，请使用 `CAMOFOX_CRASH_REPORT_ENABLED=false` 进行操作。

## 可选的依赖项/可选择的依赖关系

| 依赖关系 | 目的/用途 | 安装 |
| --- | --- | --- |
| [yt-dlp](https://github.com/yt-dlp/yt-dlp) | YouTube 视频文字转录功能（快速模式） | `pip install yt-dlp` 或 `brew install yt-dlp` |

该 Docker 镜像中包含了 yt-dlp 工具。在本地开发环境中，需要为 `/youtube/transcript` 端点安装该工具。如果不安装该工具，该端点将不得不使用较慢的浏览器-based 解决方案来处理请求。

## 快速入门

### OpenClaw 插件

```nginx
openclaw plugins install @askjo/camofox-browser
```

**工具：** `camofox_snapshot` camofox\_create\_tab `camofox_click` | `camofox_type` | `camofox_navigate` | `camofox_scroll` | `camofox_screenshot` | `camofox_close_tab` | `camofox_list_tabs` | `camofox_import_cookies` | `  |  `

### 独立运行/独立使用

从 npm 运行：

```nginx
npx @askjo/camofox-browser
```

或者直接从来源获取：

```
git clone https://github.com/jo-inc/camofox-browser
cd camofox-browser
npm install
npm start  # downloads Camoufox on first run (~300MB)
```

默认端口为 `9377` 。有关所有选项的详细信息，请参阅“环境变量”部分。

> 注意：在下载 Camoufox 二进制文件之前，安装后的脚本会先将自己对应的 `PLAYWRIGHT_SKIP_BROWSER_DOWNLOAD` 值重置为默认值。如果不进行这种重置操作，那么由 Playwright 配置为使用系统自带的 Chrome 浏览器时所导出的 `PLAYWRIGHT_SKIP_BROWSER_DOWNLOAD=1` 值，将会导致二进制文件无法被正确下载，进而使服务器在运行时崩溃。
> 
> 外部 Camoufox 可执行文件：请在 `npm install` 之前设置 `CAMOUFOX_EXECUTABLE=/path/to/camoufox-bin` 的值。在启动服务器时，这样就可以跳过捆绑包的下载过程，直接运行该可执行文件。兼容性相关的别名分别为 `CAMOUFOX_EXECUTABLE_PATH` 和 `CAMOFOX_EXECUTABLE_PATH` 。此功能对于 NixOS 系统特别有用，因为相关路径可能为 `/nix/store/.../camoufox-bin` ；该可执行文件必须来自包含 `properties.json` 、 `version.json` 和 `fontconfig/` 的 Camoufox 捆绑包中。
> 
> 采用物理隔离或自定义的二进制文件管理方式：如果你已经使用了 Camoufox 软件包，建议使用 `CAMOUFOX_EXECUTABLE` 。否则，请使用 `npm install --ignore-scripts` 来禁用自动下载功能（这样会跳过所有依赖项的生命周期处理流程——这是最简单的解决方案）。或者，你也可以使用 `npm install --omit=optional` ，再手动执行 `npx camoufox-js fetch` 操作来处理相关文件。请注意， `PLAYWRIGHT_SKIP_BROWSER_DOWNLOAD=1 npm install` 不再能跳过 Camoufox 的下载过程（安装完成后，系统会自动清理相关环境变量）；如需跳过该步骤，请使用 `--ignore-scripts` 或 `CAMOUFOX_EXECUTABLE` 。

### Docker

附带的 `Makefile` 工具能够自动检测你的 CPU 架构，并在 Docker 构建过程之外预先下载 Camoufox 和 yt-dlp 所需的二进制文件。因此，重新构建的过程非常迅速（大约 30 秒，而~则需要 3 分钟）。

```
# Build and start (auto-detects arch: aarch64 on M1/M2, x86_64 on Intel)
make up

# Stop and remove the container
make down

# Force a clean rebuild (e.g. after upgrading VERSION/RELEASE)
make reset

# Just download binaries (without building)
make fetch

# Override arch or version explicitly
make up ARCH=x86_64
make up VERSION=135.0.1 RELEASE=beta.24
```

#### Windows

在 Windows 系统中， `make` 不可用。请使用附带的 `build.ps1` PowerShell 脚本来替代。

```
# Build and start
.\build.ps1 up

# Stop and remove the container
.\build.ps1 down

# Build image only
.\build.ps1 build

# Force a clean rebuild
.\build.ps1 reset

# Download binaries only (without building)
.\build.ps1 fetch

# Override architecture
.\build.ps1 up -Arch x86_64
.\build.ps1 up -Arch aarch64
```

> 注意：建议使用 PowerShell 7+版本中的 `pwsh` 语法，不过 Windows PowerShell 5.1 中的 `powershell.exe` 语法也可以使用。该脚本需要安装了 WSL2 后端的 Docker Desktop for Windows。
> 
> 行尾格式：该项目包含一个 `.gitattributes` 文件，该文件会强制让 `.sh` 文件使用 Unix 系统的 `LF` 行尾格式。如果你已经克隆了该代码库，但在 `docker build` 过程中出现了 `sh: not found` 或 `set: Illegal option -` 错误，请运行以下命令：
> 
> ```powershell
> Get-ChildItem -Recurse *.sh | ForEach-Object { (Get-Content $_) -join "\`n" + "\`n" | Set-Content $_ -NoNewline }
> ```
> 
> 这将把 shell 脚本中的换行符转换为 LF 格式。得益于 `.gitattributes` ，未来的版本将自动处理这一转换。

> 警告：请勿直接运行 `docker build` 。Dockerfile 使用绑定挂载的方式，从 `dist/` 中获取预先下载好的二进制文件。请务必使用 `make up` （或者先使用 `make fetch` ，再使用 `make build` ）——这样系统会先下载这些二进制文件。

### Fly.io

对于 Fly.io 或其他远程持续集成系统，你需要使用 Dockerfile 来在构建过程中下载二进制文件，而不要使用绑定挂载的方式。

### 铁路

其中包含了一个 `railway.toml` 。该组件使用了 `Dockerfile.ci` （在构建过程中会下载二进制文件），同时会自动将 Railway 的 `PORT` 环境变量映射到 `CAMOFOX_PORT` 。

```bash
# Install Railway CLI, then:
railway link
railway up
```

通过 Railway 控制面板或 CLI 来设置密钥：

```
railway variables set CAMOFOX_API_KEY="your-generated-key"
```

## 使用方法/用途

将浏览器中的 Cookie 导入 Camoufox，从而无需在 LinkedIn、Amazon 等网站上进行交互式登录。

#### 设置/配置

**1\. 生成密钥：**

```perl
# macOS / Linux
openssl rand -hex 32
```

**2\. 在启动 OpenClaw 之前，请先设置好环境变量：**

```
export CAMOFOX_API_KEY="your-generated-key"
openclaw start
```

该密钥既被插件用于请求的认证，也被服务器用于请求的验证。两者都在同一个环境中运行——只需设置一次即可。

> 为什么要使用环境变量呢？因为这些敏感信息属于机密内容。在 `openclaw.json` 中配置的插件相关参数都是以明文形式存储的，因此机密信息不应该存储在那里。请将 `CAMOFOX_API_KEY` 的值设置在 shell 配置文件、systemd 单元配置、Docker 环境变量或 Fly.io 的机密信息存储中。

> 默认情况下，Cookie 导入功能是禁用的。如果未设置 `CAMOFOX_API_KEY` ，服务器会以 403 错误拒绝所有与 Cookie 相关的请求。

**3\. 从浏览器中导出 Cookie：**

安装一个能够导出 Netscape 格式的 Cookie 文件的浏览器插件（例如，适用于 Chrome/Firefox 的“cookies.txt”插件）。将你想要验证的网站的 Cookie 文件导出来。

**4\. 保存饼干文件：**

```bash
mkdir -p ~/.camofox/cookies
cp ~/Downloads/linkedin_cookies.txt ~/.camofox/cookies/linkedin.txt
```

默认目录为 `~/.camofox/cookies/` 。如需更改，请使用 `CAMOFOX_COOKIES_DIR` 。

**5\. 请您的代理来负责进口这些商品：**

> 从 linkedin.txt 文件中导入我的 LinkedIn Cookie 数据

该代理会调用 `camofox_import_cookies` ，读取相关文件，然后使用 Bearer 令牌将数据发送到服务器。之后，浏览器会自动保存这些 Cookie。此后，对 linkedin.com 的任何调用都将经过身份验证。

#### 它是如何运作的

```
~/.camofox/cookies/linkedin.txt          (Netscape format, on disk)
        |
        v
camofox_import_cookies tool              (parses file, filters by domain)
        |
        v  POST /sessions/:userId/cookies
        |  Authorization: Bearer <CAMOFOX_API_KEY>
        |  Body: { cookies: [Playwright cookie objects] }
        v
camofox server                           (validates, sanitizes, injects)
        |
        v  context.addCookies(...)
        |
Camoufox browser session                 (authenticated browsing)
```

- `cookiesPath` 的解析是相对于 cookies 目录来进行的——超出该目录范围的路径遍历会被阻止。
- 每次请求最多可上传 500 个 Cookie，文件大小上限为 5MB。
- Cookie 对象会被过滤处理，只保留 Playwright 框架所允许的字段。

### 会话持久化

默认情况下，camofox 会将每个用户的 Cookie 和 localStorage 数据保存在 `~/.camofox/profiles/` 中。即使浏览器重新启动，这些数据也会被保留下来。用户只需登录一次（通过 Cookie 或 VNC），后续的登录过程就会自动恢复之前的登录状态。

```nix
~/.camofox/
|-- cookies/          # Bootstrap cookie files (Netscape format)
\-- profiles/         # Persisted session state (auto-managed)
    \-- <hashed-userId>/
        \-- storage_state.json
```

可以用 `CAMOFOX_PROFILE_DIR` 来覆盖该目录，或者在持久化插件配置中设置 `"profileDir"` 。若要禁用持久化功能，请在 `camofox.config.json` 中设置 `"persistence": { "enabled": false }` 。

默认情况下，存储状态仅包含 Cookie 和 localStorage 中的数据。如果想同时保存 IndexedDB 中的数据，请在持久化插件配置中设置相关参数。这样，所有可序列化的 IndexedDB 数据都会被保存下来——而不仅仅是认证相关的数据。不过，这种方式会导致快照的体积变大，检查点的生成速度变慢。

### 会话追踪

记录会话中发生的每一个操作：页面截图、DOM 结构快照、网络请求信息以及控制台输出内容。所有记录会被保存为一个 `.zip` 文件，你可以用 Playwright 自带的 Trace Viewer 来查看该文件。

在打开第一个标签页时，通过输入 `trace: true` 即可选择加入该功能。

```rust
curl -X POST http://localhost:9377/tabs \
  -H 'Content-Type: application/json' \
  -d '{"userId":"agent1","sessionKey":"task1","url":"https://example.com","trace":true}'
```

该记录会在会话结束时被写入。请先关闭会话以将其刷新，之后才能进行列表显示、数据获取和查看操作。

```
# Close the session to flush the trace
curl -X DELETE http://localhost:9377/sessions/agent1

# List trace files
curl http://localhost:9377/sessions/agent1/traces
# {"traces":[{"filename":"trace-2026-04-18T04-05-00-...zip","sizeBytes":42810,"createdAt":...}]}

# Download (Content-Type: application/zip)
curl http://localhost:9377/sessions/agent1/traces/trace-2026-04-18T04-05-00-abc.zip > session.zip

# View it in Playwright's Trace Viewer
npx playwright show-trace session.zip

# Delete
curl -X DELETE http://localhost:9377/sessions/agent1/traces/trace-2026-04-18T04-05-00-abc.zip
```

为何选择“轨迹数据”而非视频：Camoufox 基于 Firefox 开发，而 Playwright 的 `recordVideo` 功能则仅适用于 Chromium 浏览器。 “轨迹数据”在 Firefox 上也能正常使用，而且能提供比视频更丰富的信息（包括网络数据、DOM 结构、控制台输出以及屏幕截图等）。

无法在现有的会话中切换此功能。如果需要更改该设置，请先关闭当前会话。 `DELETE /sessions/:userId`

存储位置默认为 `~/.camofox/traces/<hashed-userId>/` ，在服务器启动时会被自动清除。

- `CAMOFOX_TRACES_DIR` - 基目录（默认值： `~/.camofox/traces` ）
- `CAMOFOX_TRACES_MAX_BYTES` —— 每条跟踪记录的最大大小。如果超过此限制，该跟踪记录将在下次启动时被删除（默认值：50MB）
- `CAMOFOX_TRACES_TTL_HOURS` – 比此时间更早的记录将在下一次启动时被删除（默认值为 24 小时）。

#### 独立服务器的使用情况

```rust
curl -X POST http://localhost:9377/sessions/agent1/cookies \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer YOUR_CAMOFOX_API_KEY' \
  -d '{"cookies":[{"name":"foo","value":"bar","domain":"example.com","path":"/","expires":-1,"httpOnly":false,"secure":false}]}'
```

#### Docker / Fly.io / Railway

```ruby
docker run -p 9377:9377 \
  -e CAMOFOX_API_KEY="your-generated-key" \
  -v ~/.camofox/cookies:/home/node/.camofox/cookies:ro \
  camofox-browser
```

对于 Fly.io 来说：

```
fly secrets set CAMOFOX_API_KEY="your-generated-key"
```

对于铁路运输而言：

```
railway variables set CAMOFOX_API_KEY="your-generated-key"
```

### 代理服务器 + 地理 IP 地址过滤

让所有浏览器流量都通过代理服务器进行传输。该代理服务器能根据 Camoufox 内置的 GeoIP 功能，自动获取与代理服务器 IP 地址相关的地区信息、时区以及地理位置数据。

**简单代理（单个端点）：**

```
export PROXY_HOST=166.88.179.132
export PROXY_PORT=46040
export PROXY_USERNAME=myuser
export PROXY_PASSWORD=mypass
npm start
```

**后端连接代理（循环使用粘性会话）：**

对于 Decodo、Bright Data 或 Oxylabs 这类提供基于会话的粘性 IP 地址的单一网关端点的服务提供商来说：

```
export PROXY_STRATEGY=backconnect
export PROXY_BACKCONNECT_HOST=gate.provider.com
export PROXY_BACKCONNECT_PORT=7000
export PROXY_USERNAME=myuser
export PROXY_PASSWORD=mypass
npm start
```

每个浏览器会话都有一个唯一的标识符，因此不同用户会拥有不同的 IP 地址。如果出现代理服务器故障或被谷歌屏蔽，会话标识符会自动更替。

或者在 Docker 中：

```
docker run -p 9377:9377 \
  -e PROXY_HOST=166.88.179.132 \
  -e PROXY_PORT=46040 \
  -e PROXY_USERNAME=myuser \
  -e PROXY_PASSWORD=mypass \
  camofox-browser
```

当配置了代理服务器时：

- 所有通过该代理服务器的流量路径
- Camoufox 的 GeoIP 功能会自动将 `locale` 、 `timezone` 和 `geolocation` 的值设置为与代理服务器的出口 IP 地址相匹配。
- 浏览器指纹信息（语言、时区、坐标）与代理服务器的位置一致。
- 如果没有代理服务器，将默认使用 `en-US` 、 `America/Los_Angeles` 以及旧金山的坐标。

### 遥测技术

浏览器自动化过程中会出现各种难以预测的故障——Cloudflare 带来的挑战、网站重新设计导致的选集器失效、重定向循环、大量弹窗的出现、渲染器崩溃等等。故障的种类繁多，且难以预测。如果没有遥测数据，我们只能得到“操作失败”这一结果。

遥测功能为我们提供了关于哪些站点出现了故障、故障的具体原因以及故障发生的频率等结构化数据。这样，我们就能优先处理那些真正会影响用户使用的故障问题。当出现以下情况时，该功能会自动在 GitHub 上创建问题记录：

- 未捕获的异常会导致程序崩溃。
- 事件循环停滞时间超过 5 秒（看门狗检测触发）
- 失败模式——在同一标签页上连续出现 3 次或更多次失败情况（超时、上下文丢失、导航中断）

每份报告都包含故障类型、堆栈跟踪信息、各标签页的运行状况数据（HTTP 状态统计图、控制台错误信息、请求失败情况、重定向次数），以及目标 URL。所有这些信息都经过匿名处理。

#### 它是如何运作的

遥测数据会被发送到位于 `https://camofox-telemetry.askjo.workers.dev` 的 Cloudflare Worker 端点。该端点将 GitHub 应用的凭证作为环境机密信息进行存储——该包中不包含任何机密信息。

```
lib/reporter.js (client, no secrets)
    |  anonymize -> POST https://camofox-telemetry.askjo.workers.dev/report
    v
Cloudflare Worker (holds GitHub App key)
    |  validate -> rate-limit -> dedup -> create GitHub Issue
    v
GitHub Issue created
```

该端点的源代码保存在这个仓库的 [`workers/crash-reporter/index.ts`](https://github.com/jo-inc/camofox-browser/blob/master/workers/crash-reporter/index.ts) 位置。

#### 验证

您不必信任我们——可以直接查看实时端点正在运行什么内容来验证即可：

```
# 1. Ask the endpoint what code it's running
curl https://camofox-telemetry.askjo.workers.dev/source
# -> { "commit": "abc1234", "sha256": "e3b0c44...", "source": "https://github.com/..." }

# 2. Compare the sha256 against the source in this repo
sha256sum workers/crash-reporter/index.ts

# 3. Check the commit matches what CI deployed
#    https://github.com/jo-inc/camofox-browser/actions/workflows/telemetry-deploy.yml
git log --oneline workers/crash-reporter/index.ts | head -1
```

如果哈希值不匹配，说明该端点实际运行的代码与代码仓库中保存的代码不一致。在部署过程中， `.github/workflows/telemetry-deploy.yml` 会自动将提交的哈希值和源代码的哈希值记录下来——因此，每次部署过程都可以在 GitHub Actions 中被追溯记录。

或者完全跳过验证步骤：使用 `CAMOFOX_CRASH_REPORT_ENABLED=false` 可以关闭所有遥测功能；或者使用 `CAMOFOX_CRASH_REPORT_URL` 来指定自己的端点。

#### 隐私

所有报告的数据在离开处理流程之前，都会经过严格的匿名处理程序（ `lib/reporter.js` L28-290）。

- URL 方面：那些属于知名公共域名的网站（如 Google、Amazon、Reddit、Cloudflare 等），其 URL 会以原样显示，这样我们就能确定是哪些网站导致了问题。至于那些属于私有或未知域名的网站，其 URL 则会被替换为稳定的 HMAC 哈希值（ `site-a1b2c3d4` ）。所有报告中的哈希值都是一样的，便于进行数据关联分析；不过，这些哈希值无法还原为原来的域名。路径中的各个部分会被标记为 `*/*/*` ，仅显示路径的深度信息。查询参数则会被标记为 `?[3]` ，仅显示查询参数的数量。无论是什么键、值或路径内容，都不会被包含在最终的报告中。
- 文件路径 -> 仅保留文件名部分（ `<path>/server.js` ）
- 令牌、密钥、API 密钥 -> `<token>`
- IP 地址、电子邮件地址、环境变量 → 已被屏蔽/隐藏
- Docker/Fly 机器 ID -> `<id>`
- 标签页健康状况——仅包含各种计数数据（崩溃次数、错误次数、状态码分布图）。不包含任何页面内容、URL 或用户数据。

重复的问题会通过堆栈签名被识别出来，系统会为这些问题添加 `+1` 注释，而不会将其视为新的问题来处理。

```
# Disable telemetry
export CAMOFOX_CRASH_REPORT_ENABLED=false

# Point to your own endpoint (see below)
export CAMOFOX_CRASH_REPORT_URL=https://your-endpoint.example.com/report

# Adjust rate limit (default: 10 per hour)
export CAMOFOX_CRASH_REPORT_RATE_LIMIT=5
```

#### 自托管的遥测端点

若想在自己的 GitHub 仓库中提交遥测数据报告，而非通过 `jo-inc/camofox-browser` 来提交：

1. 创建一个 GitHub 应用——设置 -> 开发者设置 -> GitHub 应用 -> 新建
	- 权限：代码库 -> 问题记录 -> 读取与写入
		- 取消选中“Webhook -> Active”选项（无需启用）
		- 点击“生成密钥”——会下载一个 `.pem` 格式的文件。
		- 在目标仓库中安装该应用（点击“安装应用”->选择相应的仓库）
		- 请记下您的应用 ID（位于应用“通用”页面上的数字）以及安装 ID（在安装完成后，从 URL 中可以获取： `github.com/settings/installations/{id}` ）
2. 部署该端点——克隆此代码库并部署相关工作进程：
	```
	cd workers/crash-reporter
	# Edit wrangler.toml: set account_id to your Cloudflare account ID
	npx wrangler deploy
	```
	该工具实际上是一个单独的 TypeScript 文件，不依赖任何 npm 包。它可以在 Deno、Bun 或任何支持 Web Crypto API 的运行环境中运行。
3. **设置工作者机密信息：**
	```
	cd workers/crash-reporter
	echo "YOUR_APP_ID" | npx wrangler secret put GH_APP_ID
	echo "YOUR_INSTALL_ID" | npx wrangler secret put GH_INSTALL_ID
	# Key must be PKCS#8 DER base64 (not raw PEM)
	openssl pkcs8 -topk8 -inform PEM -outform DER -nocrypt -in your-app.pem | \
	  base64 | tr -d '\n' | npx wrangler secret put GH_PRIVATE_KEY
	# File issues in your repo
	echo "your-org/your-repo" | npx wrangler secret put GH_REPO
	```
4. **将 camofox-browser 的指向指向你的终端设备：**
	```
	export CAMOFOX_CRASH_REPORT_URL=https://your-worker.your-subdomain.workers.dev/report
	```
5. **验证：**
	```
	curl https://your-worker.your-subdomain.workers.dev/health
	# -> {"status":"ok"}
	```

### 结构化日志记录

所有的日志输出均为 JSON 格式（每行一个对象），这样便于日志聚合工具进行解析：

```json
{"ts":"2026-02-11T23:45:01.234Z","level":"info","msg":"req","reqId":"a1b2c3d4","method":"POST","path":"/tabs","userId":"agent1"}
{"ts":"2026-02-11T23:45:01.567Z","level":"info","msg":"res","reqId":"a1b2c3d4","status":200,"ms":333}
```

为了减少不必要的日志记录，健康检查请求（ `/health` ）被排除在日志记录范围之外。

### 基本浏览功能

```
# Create a tab
curl -X POST http://localhost:9377/tabs \
  -H 'Content-Type: application/json' \
  -d '{"userId": "agent1", "sessionKey": "task1", "url": "https://example.com"}'

# Get accessibility snapshot with element refs
curl "http://localhost:9377/tabs/TAB_ID/snapshot?userId=agent1"
# -> { "snapshot": "[button e1] Submit  [link e2] Learn more", ... }

# Click by ref
curl -X POST http://localhost:9377/tabs/TAB_ID/click \
  -H 'Content-Type: application/json' \
  -d '{"userId": "agent1", "ref": "e1"}'

# Type into an element
curl -X POST http://localhost:9377/tabs/TAB_ID/type \
  -H 'Content-Type: application/json' \
  -d '{"userId": "agent1", "ref": "e2", "text": "hello", "pressEnter": true}'

# Navigate with a search macro
curl -X POST http://localhost:9377/tabs/TAB_ID/navigate \
  -H 'Content-Type: application/json' \
  -d '{"userId": "agent1", "macro": "@google_search", "query": "best coffee beans"}'
```

## API

### 标签生命周期

| 方法/途径 | 端点 | 描述 |
| --- | --- | --- |
| `POST` | `/tabs` | 创建一个包含初始 URL 的标签页 |
| `GET` | `/tabs?userId=X` | 列出所有打开的标签页 |
| `GET` | `/tabs/:id/stats` | 标签统计信息（工具调用次数、访问的 URL 地址） |
| `DELETE` | `/tabs/:id` | 关闭标签页 |
| `DELETE` | `/tabs/group/:groupId` | 关闭组中的所有标签页 |
| `DELETE` | `/sessions/:userId` | 关闭该用户的所有标签页 |

### 页面交互

| 方法/途径 | 端点 | 描述 |
| --- | --- | --- |
| `GET` | `/tabs/:id/snapshot` | 包含元素引用信息的无障碍访问功能快照。查询参数： `includeScreenshot=true` （用于添加 Base64 编码的 PNG 图片）， `offset=N` （用于分页显示大型快照） |
| `POST` | `/tabs/:id/click` | 通过引用或 CSS 选择器来点击某个元素 |
| `POST` | `/tabs/:id/type` | 在相应元素中输入文本 |
| `POST` | `/tabs/:id/press` | 按下一个键盘键 |
| `POST` | `/tabs/:id/scroll` | 页面滚动（上/下/左/右） |
| `POST` | `/tabs/:id/navigate` | 导航至该网址或使用搜索宏 |
| `POST` | `/tabs/:id/wait` | 等待选择器响应或超时处理 |
| `GET` | `/tabs/:id/links` | 提取页面上的所有链接 |
| `GET` | `/tabs/:id/images` | 列出 `<img>` 个元素。查询参数： `includeData=true` （返回内嵌数据 URL）、 `maxBytes=N` 、 `limit=N` |
| `GET` | `/tabs/:id/downloads` | 列出已下载的文件列表。查询参数： `includeData=true` （Base64 编码的文件数据）， `consume=true` （读取后清除）， `maxBytes=N` |
| `GET` | `/tabs/:id/screenshot` | 截屏 |
| `POST` | `/tabs/:id/back` | 回去吧。 |
| `POST` | `/tabs/:id/forward` | 向前前进吧。 |
| `POST` | `/tabs/:id/refresh` | 刷新页面 |

### YouTube 视频文字记录/YouTube 视频的文字内容

| 方法/途径 | 端点 | 描述 |
| --- | --- | --- |
| `POST` | `/youtube/transcript` | 从 YouTube 视频中提取字幕 |

```
curl -X POST http://localhost:9377/youtube/transcript \
  -H 'Content-Type: application/json' \
  -d '{"url": "https://www.youtube.com/watch?v=dQw4w9WgXcQ", "languages": ["en"]}'
# -> { "status": "ok", "transcript": "[00:18] [music] We're no strangers to love [music]\n...", "video_title": "...", "total_words": 548 }
```

如果可用的话，会使用 yt-dlp 来下载视频（速度很快，且无需使用浏览器）。如果未安装 yt-dlp，则会转而使用基于浏览器的下载方式。不过，这种方式速度较慢，而且由于 YouTube 的广告插播，可靠性也较差。

### 服务器

| 方法/途径 | 端点 | 描述 |
| --- | --- | --- |
| `GET` | `/health` | 健康检查 |
| `POST` | `/start` | 启动浏览器引擎 |
| `POST` | `/stop` | 停止浏览器引擎运行 |

### 会议/会谈

| 方法/途径 | 端点 | 描述 |
| --- | --- | --- |
| `POST` | `/sessions/:userId/cookies` | 将 Cookie 添加到用户会话中（Playwright 的 Cookie 对象） |
| `GET` | `/sessions/:userId/storage_state` | 导出浏览器缓存数据（VNC 插件相关） |
| `DELETE` | `/sessions/:userId/storage_state` | 重置当前会话，并删除其中保存在浏览器中的数据（包括由持久化插件所保存的信息）。 |

## 搜索宏指令

`@google_search` | `@youtube_search` | `@amazon_search` | `@reddit_search` | `@reddit_subreddit` | `@wikipedia_search` | `@twitter_search` | `@yelp_search` | `@spotify_search` | `@netflix_search` | `@linkedin_search` | `@instagram_search` | `@tiktok_search` | `@twitch_search`

Reddit 的宏指令会直接返回 JSON 格式的数据（无需进行 HTML 解析）：

- `@reddit_search` – 搜索整个 Reddit 平台，返回包含 25 条结果的 JSON 数据
- `@reddit_subreddit` - 浏览某个子版块（例如，查询 `"programming"` -> `/r/programming.json` ）

## 浏览器设置

可以在 `camofox.config.json` 中调整浏览器的行为：

```json
{
  "newPageTimeoutMs": 10000
}
```

`newPageTimeoutMs` 用于控制 Firefox 在创建新标签页时需要等待的时间。如果相关页面无响应，Camofox 只会替换该用户的页面，然后重新尝试一次。默认值为 10 秒。

## 环境变量

| 变量 | 描述 | 默认值 |
| --- | --- | --- |
| `CAMOFOX_PORT` | 服务器端口 | `9377` |
| `PORT` | 服务器端口（备用方案，适用于 Fly.io、Railway 等平台） | `9377` |
| `CAMOFOX_BIND_HOST` | 可选的服务器绑定主机地址。设置为 `127.0.0.1` 可仅允许本地访问；设置为 `0.0.0.0` 则允许所有接口上的 IPv4 访问。如果未进行设置，Node 将使用其默认的所有接口绑定设置。 | \- |
| `CAMOFOX_API_KEY` | 启用 Cookie 导入接口（如果未设置，则该功能处于禁用状态） | \- |
| `CAMOFOX_ADMIN_KEY` | `POST /stop 所需的内容/条件` | \- |
| `CAMOFOX_ACCESS_KEY` | 如果该选项被启用，那么所有路由（ `/health` 、Cookie 导入以及 `/stop` 除外）都必需使用 `Authorization: Bearer <key>` 。这样一来，就可以安全地将服务器暴露在环回地址之外了。 | \- |
| `CAMOUFOX_EXECUTABLE` | 外部 Camoufox 可执行文件，可用于替代下载/启动捆绑包中的缓存文件。该文件必须指向包含所有相关资源的 Camoufox 捆绑包。 | \- |
| `CAMOUFOX_EXECUTABLE_PATH` | `CAMOUFOX_EXECUTABLE 的兼容性别名` | \- |
| `CAMOFOX_EXECUTABLE_PATH` | `CAMOUFOX_EXECUTABLE 的兼容性别名` | \- |
| `CAMOFOX_DISABLE_DEFAULT_ADDONS` | 将设置值设为 `1` / `true` ，即可跳过默认的 uBlock Origin（UBO）插件的下载和安装过程。这一设置非常有用，尤其是在那些无法从 addons.mozilla.org 可靠地下载该插件，或者不希望下载该插件的情况下。如果不慎下载失败，会导致插件缓存损坏，进而影响系统的正常启动。 | `0` |
| `CAMOFOX_COOKIES_DIR` | Cookie 文件存储目录 | `~/.camofox/cookies` |
| `CAMOFOX_PROFILE_DIR` | 持久化会话配置文件的目录 | `~/.camofox/profiles` |
| `CAMOFOX_TRACES_DIR` | 会话跟踪记录的压缩文件目录 | `~/.camofox/traces` |
| `CAMOFOX_TRACES_MAX_BYTES` | 每条跟踪记录的最大大小限制：如果超过该限制，该记录将在下次启动时被删除。 | `52428800` (50MB) |
| `CAMOFOX_TRACES_TTL_HOURS` | 比这更早的记录会在启动时被清除。 | `24` |
| `MAX_SESSIONS` | 最大并发浏览器会话数 | `50` |
| `MAX_TABS_PER_SESSION` | 每次会话的最大标签数 | `10` |
| `SESSION_TIMEOUT_MS` | 会话空闲超时时间 | `1800000` (30 分钟) |
| `BROWSER_IDLE_TIMEOUT_MS` | 浏览器空闲时自动关闭（0 表示从不自动关闭） | `300000` (5 分钟) |
| `HANDLER_TIMEOUT_MS` | 任何处理程序的最大处理时间 | `30000` (30 秒) |
| `MAX_CONCURRENT_PER_USER` | 每位用户的并发请求上限 | `3` |
| `MAX_OLD_SPACE_SIZE` | Node.js V8 堆内存限制（MB） | `128` |
| `PROXY_STRATEGY` | 代理模式： `backconnect` （循环使用粘性会话）或空白（单一端点） | \- |
| `PROXY_PROVIDER` | 会话格式的提供者名称（例如： `decodo` ） | `decodo` |
| `PROXY_HOST` | 代理主机名或 IP 地址（简单模式） | \- |
| `PROXY_PORT` | 代理端口（简单模式） | \- |
| `PROXY_USERNAME` | 代理认证用户名 | \- |
| `PROXY_PASSWORD` | 代理认证密码 | \- |
| `PROXY_BACKCONNECT_HOST` | 回连网关的主机名 | \- |
| `PROXY_BACKCONNECT_PORT` | 回连网关端口 | `7000` |
| `PROXY_COUNTRY` | 用于代理地理定位的目标国家/地区 | \- |
| `PROXY_STATE` | 用于代理地理定位的目标州/地区 | \- |
| `TAB_INACTIVITY_MS` | 关闭那些空闲时间超过此时间的标签页。 | `300000` (5 分钟) |
| `CAMOFOX_CRASH_REPORT_ENABLED` | 启用匿名化的崩溃/挂机数据传输功能（ `false` 可关闭该功能） | `true` |
| `CAMOFOX_CRASH_REPORT_URL` | 遥测端点（自托管端点） | `https://camofox-telemetry.askjo.workers.dev/report` |
| `CAMOFOX_CRASH_REPORT_REPO` | 用于处理遥测相关问题的 GitHub 仓库 | `jo-inc/camofox-browser` |
| `CAMOFOX_CRASH_REPORT_RATE_LIMIT` | 每小时的最大遥测报告数量 | `10` |
| `ENABLE_VNC` | 启用 VNC 插件，以便通过浏览器进行交互式操作（ `1` ） | \- |
| `VNC_PASSWORD` | 用于 VNC 连接的密码（在生产环境中推荐使用） | \- |
| `NOVNC_PORT` | noVNC 网络 UI 端口 | `6080` |

## 建筑风格/建筑结构

```
Browser Instance (Camoufox)
\-- User Session (BrowserContext) - isolated cookies/storage
    |-- Tab Group (sessionKey: "conv1")
    |   |-- Tab (google.com)
    |   \-- Tab (github.com)
    \-- Tab Group (sessionKey: "conv2")
        \-- Tab (amazon.com)
```

如果 30 分钟内没有用户活动，会话将会自动失效。如果 5 分钟内没有任何活跃的会话，浏览器本身也会关闭，下次有请求时才会重新启动。

当某个会话的标签页数量达到上限时，系统会自动回收使用最久/最不常被使用的标签页，而不会报错。这样一来，那些持续运行的代理会话就不会陷入僵局。

## 安全模型

本文档旨在向用户和自动安全审查人员说明 camofox-browser 的安全边界情况。

### 代码隔离

所有 `process.env` 相关的操作都集中在 `lib/config.js` 中进行。所有与 `child_process` 相关的操作则发生在 `lib/launcher.js` （服务器子进程）和 `plugins/youtube/youtube.js` （yt-dlp）中。主 `server.js` 节点虽然具备路由处理功能，但实际上并不涉及任何 `process.env` 相关的操作，也没有进行任何 `child_process` 相关的导入操作。没有任何一个文件同时具备处理环境/凭证信息以及进行网络传输的功能。

### 没有隐藏的秘密/没有任何隐蔽的内容

该软件包中不包含任何凭证、私钥、API 令牌或签名密钥。所有的敏感信息都是在运行时通过环境变量来提供的（如 `CAMOFOX_API_KEY` 、 `CAMOFOX_ACCESS_KEY` ），或者作为 Cloudflare Worker 的环境密钥来存储（如遥测端点的 GitHub 应用密钥）。

Cookie 导入接口（ `POST /sessions/:userId/cookies` ）受到 `CAMOFOX_API_KEY` 的访问控制。如果该环境变量未设置，服务器会以 HTTP 403 错误拒绝所有 Cookie 导入请求。Cookie 文件存储在经过安全隔离的目录中（ `~/.camofox/cookies/` ），该目录具有路径遍历保护机制，任何试图绕过该目录结构的尝试都会被阻止。每次请求最多可导入 500 个 Cookie，文件大小不得超过 5MB。

### 访问控制

`CAMOFOX_ACCESS_KEY` 为所有路由提供全局令牌验证功能（ `/health` 除外）。一旦启用该功能，所有请求都必须包含 `Authorization: Bearer <key>` 。建议在本地主机以外的环境中使用该功能。

### 二进制文件下载

Camoufox 浏览器引擎的文件大小约为 300MB。该引擎由 Camoufox 项目维护，通过 npm 包的形式进行分发。其下载内容均来自 GitHub 上的官方版本，且下载过程的完整性由 `camoufox-js` 负责验证。该引擎不使用任何自定义的下载地址，也不经过任何网址缩短服务或直接使用原始 IP 地址来下载。

### 遥测技术

经过匿名处理的崩溃/挂机相关数据会被发送到 Cloudflare Worker 端点。该端点的代码存储在这个代码库中，因此可以被审计。验证方式如下：在端点上输入 `GET /source` ，即可获取到相关的哈希值和 sha256 值，从而与代码库中的数据进行比对。数据报告者( `lib/reporter.js` L28-290)采用了严格的匿名处理措施：私有域名会被进行 HMAC 哈希处理（该过程不可逆），路径信息会被删除，令牌、IP 地址和电子邮件地址也会被遮盖。任何页面内容、Cookie 或用户数据都不会被发送出去。如需禁用此功能，请使用 `CAMOFOX_CRASH_REPORT_ENABLED=false` ；如需使用自己的端点，请使用 `CAMOFOX_CRASH_REPORT_URL` 。

### 会话持久化

该持久化插件会将 Cookie 和 localStorage 数据保存在 `~/.camofox/profiles/<hashed-userId>/` 中，从而确保用户在浏览器重启后仍能保持登录状态。用户 ID 会被转换成哈希值后用于作为目录名称。如需禁用该功能，请从插件数组中删除 `persistence` 。

### 网络访问权限

出站连接的目标包括：(1) 代理程序所访问的 URL 地址（属于核心功能）；(2) 遥测数据端点（数据会经过匿名处理，用户可选择不参与数据传输）。入站连接则指向端口 9377 上的 REST API。该 API 默认与所有接口相连；如果进行了配置，则与 `CAMOFOX_BIND_HOST` 相连。此外，该 API 还可以通过 `CAMOFOX_ACCESS_KEY` 进行保护。

### 子进程使用情况

可能会生成两个子进程：(1) Camoufox 浏览器引擎（核心功能， `lib/launcher.js` ）；(2) 用于提取 YouTube 视频字幕的 yt-dlp 工具（可选， `plugins/youtube/youtube.js` ）。这两个子进程都独立存在于专门的文件中，与路由处理程序相互分离。

## 测试中

```dockerfile
npm test              # all tests
npm run test:e2e      # e2e tests only
npm run test:live     # live site tests (Google, macros)
npm run test:debug    # with server output
```

## npm

```coffeescript
npm install @askjo/camofox-browser
```

## 致谢/鸣谢

- Camoufox——基于 Firefox 的浏览器，配备了 C++语言编写的反检测功能。
- [向 Camoufox 的原创者 daijro 捐款吧。](https://camoufox.com/about/)
- OpenClaw——开源人工智能代理框架

## 加密货币诈骗警告

既然这个项目引起了人们的关注，那些不可靠的人就开始利用名为“Camofox”的加密货币来搞些不可告人的把戏。其实，Camofox 根本算不上什么加密货币项目。任何使用“Camofox”这个名字的代币、硬币或 NFT 都与我们毫无关系。