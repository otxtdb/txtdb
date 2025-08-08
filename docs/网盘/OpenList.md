# Introduction



------

此页内容

[![img](https://img.shields.io/github/release/OpenListTeam/OpenList?style=flat-square)](https://github.com/OpenListTeam/OpenList/releases/latest)
[![GitHub Discussions](https://cdn.jsdelivr.net/gh/otxtdb/txtdbpic@master/img/23a50be273c82aa3f35b370ac0998d2f.svg%2Bxml%3Bcharset%3Dutf-8)](https://github.com/OpenListTeam/OpenList/discussions)
[![img](https://cdn.jsdelivr.net/gh/otxtdb/txtdbpic@master/img/fa79f819b3f2d080b436af1d97578c76.svg%2Bxml%3Bcharset%3Dutf-8)](https://github.com/OpenListTeam/OpenList/actions?query=workflow%3ABuild)
[![img](https://img.shields.io/github/downloads/OpenListTeam/OpenList/total?style=flat-square&color=%239F7AEA)](https://github.com/OpenListTeam/OpenList/releases)

## [What's this](https://oplist.org/zh/guide/#what-s-this)

一个支持多种存储，支持网页浏览和 WebDAV 的文件列表程序，由 gin 和 Solidjs 驱动。

## [Support storage](https://oplist.org/zh/guide/#support-storage)

- [本机存储](https://oplist.org/zh/guide/drivers/local.html)
- [Crypt](https://oplist.org/zh/guide/drivers/Crypt.html)
- [阿里云盘Open](https://oplist.org/zh/guide/drivers/aliyundrive_open.html)
- [阿里云盘](https://www.alipan.com/)
- [OneDrive](https://oplist.org/zh/guide/drivers/onedrive.html) /[APP](https://oplist.org/zh/guide/drivers/onedrive_app.html)/ SharePoint（[国际版](https://www.office.com/), [世纪互联](https://portal.partner.microsoftonline.cn/),de,us）
- [GoogleDrive](https://drive.google.com/)
- [123云盘/分享/直链](https://www.123pan.com/)
-  FTP / SFTP
- [PikPak / 分享](https://www.mypikpak.com/)
- [S3[对象存储\]](https://oplist.org/zh/guide/drivers/s3.html)
- [多吉云](https://oplist.org/zh/guide/drivers/s3.html#添加对象存储示例及官方文档)
- [又拍云对象存储](https://www.upyun.com/products/file-storage)
-  WebDAV(支持无API的OneDrive/SharePoint)
-  Teambition（[中国](https://www.teambition.com/)，[国际](https://us.teambition.com/)）
- [分秒帧](https://www.mediatrack.cn/)
- [天翼云盘](https://cloud.189.cn/) (个人云, 家庭云)
- [中国移动云盘](https://yun.139.com/) (个人云, 家庭云)
- [中国联通云盘](https://pan.wo.cn/)
- [四川电信魔盘](https://mopan.sc.189.cn/mopan/#/downloadPc)
- [Yandex.Disk](https://disk.yandex.com/)
- [百度网盘](https://pan.baidu.com/)
- [夸克网盘/TV/Open](https://pan.quark.cn/)
- [迅雷网盘 / X / 浏览器](https://oplist.org/zh/guide/drivers/thunder.html)
- [蓝奏云](https://www.lanzou.com/)、[蓝奏云优享版](https://www.ilanzou.com/)
- [小飞机网盘](https://feijipan.com/)
- [阿里云盘分享](https://www.alipan.com/)
- [谷歌相册](https://photos.google.com/)
- [Mega.nz](https://mega.nz/)
- [一刻相册](https://photo.baidu.com/)
- [TeraBox -海外百度](https://www.terabox.com/)
-  SMB
- [别名](https://oplist.org/zh/guide/advanced/alias.html)
- [115](https://115.com/)
- [Seafile](https://www.seafile.com/)
-  Cloudreve
- [Trainbit](https://trainbit.com/)
- [UrlTree](https://oplist.org/zh/guide/drivers/UrlTree.html)
-  IPFS
- [UC网盘/TV](https://drive.uc.cn/)
- [Dropbox](https://www.dropbox.com/)
- [腾讯微云](https://www.weiyun.com/)
- [超星星小组盘](https://oplist.org/zh/guide/drivers/chaoxing.html)
- [网易云音乐云盘](https://oplist.org/zh/guide/drivers/163music.html)
- [6盘](https://oplist.org/zh/guide/drivers/halalcloud.html)
- [联想家庭储存链接分享](https://pc.lenovo.com.cn/)
- [GitHub API](https://oplist.org/zh/guide/drivers/github.html) / [GitHub Release](https://oplist.org/zh/guide/drivers/github_releases.html)
- [Misskey](https://misskey-hub.net/cn/docs/for-users/features/drive/)

## [Discussions](https://oplist.org/zh/guide/#discussions)

一般问题请到 [Discussions](https://github.com/OpenListTeam/OpenList/discussions) ，**Issues 仅针对错误报告和功能请求。**

## [演示](https://oplist.org/zh/guide/#演示)

N/A

## [特别赞助](https://oplist.org/zh/guide/#特别赞助)

N/A

## [许可](https://oplist.org/zh/guide/#许可)

`OpenList` 是在 AGPL-3.0 许可下许可的开源软件。



# 一键脚本

------

此页内容

仅适用于 Linux amd64/arm64 平台。

正式版测试版

**安装**



```bash
curl -fsSL "https://docs.openlist.team/v3.sh" -o v3.sh && bash v3.sh
```

![v3-install](https://cdn.jsdelivr.net/gh/otxtdb/txtdbpic@master/img/043f29d488ca478bf347a2e1311be2db.png)

**面板管理命令**

使用命令：`openlist` 或者 `openlist-manager`
![openlist-manager](https://cdn.jsdelivr.net/gh/otxtdb/txtdbpic@master/img/1f42ac2f4f87c52b9b58309208fb4a68.png)



## [**自定义路径**](https://oplist.org/zh/guide/install/script.html#自定义路径)

默认安装在 `/opt/openlist` 中。 自定义安装路径，将安装路径作为第二个参数添加，必须是绝对路径（如果路径以 openlist 结尾，则直接安装到给定路径，否则会安装在给定路径 openlist 目录下），如 安装到 `/root`：

正式版测试版



```bash
# Install
curl -fsSL "https://docs.openlist.team/v3.sh" -o v3.sh && bash v3.sh install /root
# update
curl -fsSL "https://docs.openlist.team/v3.sh" -o v3.sh && bash v3.sh update /root
# Uninstall
curl -fsSL "https://docs.openlist.team/v3.sh" -o v3.sh && bash v3.sh uninstall /root
```

- 启动: `systemctl start openlist`
- 关闭: `systemctl stop openlist`
- 状态: `systemctl status openlist`
- 重启: `systemctl restart openlist`

## [**获取密码**](https://oplist.org/zh/guide/install/script.html#获取密码)

需要进入脚本安装OpenList的目录文件夹內执行如下命令

#### [低于v3.25.0版本](https://oplist.org/zh/guide/install/script.html#低于v3-25-0版本)



```bash
./openlist admin
```

#### [高于v3.25.0版本](https://oplist.org/zh/guide/install/script.html#高于v3-25-0版本)

3.25.0以上版本将密码改成加密方式存储的hash值，无法直接反算出密码，如果忘记了密码只能通过重新 **`随机生成`** 或者 **`手动设置`**



```bash
# 随机生成一个密码
./openlist admin random
# 手动设置一个密码,`NEW_PASSWORD`是指你需要设置的密码
./openlist admin set NEW_PASSWORD
```

## [**一直在加载怎么办?**](https://oplist.org/zh/guide/install/script.html#一直在加载怎么办)

挂载了一些网盘但是不能用了重启了一下OpenList，发现进不去 网页提示：`获取设置失败：请稍后，正在加载存储`怎么办？

1. 等待几分钟
2. 通过使用命令将`失效的/无法启动的`存储停止运行

LinuxWindowsMacDocker其它

如果通过命令停止 必须先进入你OpenList所在的文件夹输入命令

如果我们不知道是那个存储原因导致的，可以通过命令列出所有的存储



```bash
./openlist storage list
```



```bash
[root@OPSD-g8xXordx3B9f openlist]# ./openlist storage list
INFO[2023-11-23 17:54:10] reading config file: data/config.json
INFO[2023-11-23 17:54:10] load config from env with prefix: OpenList_
INFO[2023-11-23 17:54:10] init logrus...
INFO[2023-11-23 17:54:10] Found 2 storages
┌─────────────────────────────────────────────────────────────────┐
│ ID    Driver            Mount Path                      Enabled │
│─────────────────────────────────────────────────────────────────│
│ 1     S3                /R2                             true    │
│ 2     UrlTree           /233                            true    │
└─────────────────────────────────────────────────────────────────┘
```

输入查询命令后我们会进入另一种模式无法输入，如果添加的存储过多可以通过键盘的 ↑ 和 ↓ 来往下翻，等找到后可以按`Ctrl+C`退出

例如我们是因为 `233` 这个存储停止的，我们就输入命令来停止，然后在 重启一下OpenList就可以了



```bash
./openlist storage disable /233
```



```bash
[root@OPSD-g8xXordx3B9f openlist]# ./openlist storage disable /233
INFO[2023-11-23 17:54:52] reading config file: data/config.json
INFO[2023-11-23 17:54:52] load config from env with prefix: OpenList_
INFO[2023-11-23 17:54:52] init logrus...
INFO[2023-11-23 17:54:52] Storage with mount path [/233] have been disabled
```







# 手动安装

------

此页内容

## [**获取 OpenList**](https://oplist.org/zh/guide/install/manual.html#获取-openlist)

打开 [OpenList Release](https://github.com/OpenListTeam/OpenList/releases) 下载待部署系统对应的文件。最新版的前端已经和后端打包好了，不用再下载前端文件了。

xxxx 指的是不同系统/架构对应的名称，一般 Linux-x86/64 为 openlist-linux-amd64

手动安装如果有如下提示：是因为[你的 GLIBC 版本太低](https://oplist.org/zh/faq/why.html#lib64-libc-so-6-version-glibc-2-28-not-found-required-by-openlist-或者-accept-function-not-implemented)，建议下载 musl 版本



```txt
lib64/libc.so.6: version `GLIBC_2.28' not found (required by ./openlist)  
#或者
accept: function not implemented
```

当你看到 `start server@0.0.0.0:5244` 的输出，之后没有报错，说明操作成功。 第一次运行时会输出初始密码。程序默认监听 5244 端口。 现在打开 `http://ip:5244` 可以看到登录页面，WebDAV 请参阅 [WebDav](https://oplist.org/zh/guide/webdav.html)。

## [**手动运行**](https://oplist.org/zh/guide/install/manual.html#手动运行)

v3.25.0以上版本将密码改成加密方式存储的hash值，无法直接反算出密码，如果忘记了密码只能通过重新 **`随机生成`** 或者 **`手动设置`**

LinuxmacOSWindowswin(scoop)



```bash
# 解压下载的文件，得到可执行文件：
tar -zxvf openlist-xxxx.tar.gz
# 授予程序执行权限：
chmod +x openlist
# 运行程序
./openlist server

# 获得管理员信息 以下两个不同版本，新版本也有随机生成和手动设置
# 低于v3.25.0版本
./openlist admin

# 高于v3.25.0版本
# 随机生成一个密码
./openlist admin random
# 手动设置一个密码 `NEW_PASSWORD`是指你需要设置的密码
./openlist admin set NEW_PASSWORD
```

## [**守护进程**](https://oplist.org/zh/guide/install/manual.html#守护进程)

LinuxmacOSWindows

使用任意方式编辑 `/usr/lib/systemd/system/openlist.service` 并添加如下内容，其中 path_openlist 为 OpenList 所在的路径



```ini
[Unit]
Description=openlist
After=network.target
 
[Service]
Type=simple
WorkingDirectory=path_openlist
ExecStart=path_openlist/openlist server
Restart=on-failure
 
[Install]
WantedBy=multi-user.target
```

然后，执行 `systemctl daemon-reload` 重载配置，现在你可以使用这些命令来管理程序：

- 启动: `systemctl start openlist`
- 关闭: `systemctl stop openlist`
- 配置开机自启: `systemctl enable openlist`
- 取消开机自启: `systemctl disable openlist`
- 状态: `systemctl status openlist`
- 重启: `systemctl restart openlist`

守护进程不配置? [**视频教程**](https://www.bilibili.com/video/BV1rF41197Qv?t=187.0)

相关信息

对于所有平台，您可以使用以下命令来静默启动、停止和重新启动。 （v3.4.0 及更高版本）



```bash
# 携带`--force-bin-dir`参数启动服务
openlist start
# 通过pid停止服务
openlist stop
# 通过pid重启服务
openlist restart
```

## [**如何更新**](https://oplist.org/zh/guide/install/manual.html#如何更新)

下载新版Alist，把之前的替换了即可。

- 启动: `systemctl start openlist`
- 关闭: `systemctl stop openlist`
- 状态: `systemctl status openlist`
- 重启: `systemctl restart openlist`

## [**获取密码**](https://oplist.org/zh/guide/install/manual.html#获取密码)

需要进入脚本安装OpenList的目录文件夹內执行如下命令

#### [低于v3.25.0版本](https://oplist.org/zh/guide/install/manual.html#低于v3-25-0版本)



```bash
./openlist admin
```

#### [高于v3.25.0版本](https://oplist.org/zh/guide/install/manual.html#高于v3-25-0版本)

3.25.0以上版本将密码改成加密方式存储的hash值，无法直接反算出密码，如果忘记了密码只能通过重新 **`随机生成`** 或者 **`手动设置`**



```bash
# 随机生成一个密码
./openlist admin random
# 手动设置一个密码,`NEW_PASSWORD`是指你需要设置的密码
./openlist admin set NEW_PASSWORD
```

## [**一直在加载怎么办?**](https://oplist.org/zh/guide/install/manual.html#一直在加载怎么办)

挂载了一些网盘但是不能用了重启了一下OpenList，发现进不去 网页提示：`获取设置失败：请稍后，正在加载存储`怎么办？

1. 等待几分钟
2. 通过使用命令将`失效的/无法启动的`存储停止运行

LinuxWindowsMacDocker

如果通过命令停止 必须先进入你OpenList所在的文件夹输入命令

如果我们不知道是那个存储原因导致的，可以通过命令列出所有的存储



```bash
./openlist storage list
```



```bash
[root@OPSD-g8xXordx3B9f openlist]# ./openlist storage list
INFO[2023-11-23 17:54:10] reading config file: data/config.json
INFO[2023-11-23 17:54:10] load config from env with prefix: OpenList_
INFO[2023-11-23 17:54:10] init logrus...
INFO[2023-11-23 17:54:10] Found 2 storages
┌─────────────────────────────────────────────────────────────────┐
│ ID    Driver            Mount Path                      Enabled │
│─────────────────────────────────────────────────────────────────│
│ 1     S3                /R2                             true    │
│ 2     UrlTree           /233                            true    │
└─────────────────────────────────────────────────────────────────┘
```

输入查询命令后我们会进入另一种模式无法输入，如果添加的存储过多可以通过键盘的 ↑ 和 ↓ 来往下翻，等找到后可以按`Ctrl+C`退出

例如我们是因为 `233` 这个存储停止的，我们就输入命令来停止，然后在 重启一下OpenList就可以了



```bash
./openlist storage disable /233
```



```bash
[root@OPSD-g8xXordx3B9f openlist]# ./openlist storage disable /233
INFO[2023-11-23 17:54:52] reading config file: data/config.json
INFO[2023-11-23 17:54:52] load config from env with prefix: OpenList_
INFO[2023-11-23 17:54:52] init logrus...
INFO[2023-11-23 17:54:52] Storage with mount path [/233] have been disabled
```







# 使用 Docker

------

此页内容

注意：OpenList 官方 Docker 镜像尚未发布。此处 Docker 镜像地址尚未更新。

## [**安装**](https://oplist.org/zh/guide/install/docker.html#安装)

#### [**docker cli**](https://oplist.org/zh/guide/install/docker.html#docker-cli)



```bash
docker run -d --restart=unless-stopped -v /etc/openlist:/opt/openlist/data -p 5244:5244 -e PUID=0 -e PGID=0 -e UMASK=022 --name="openlist" openlistteam/openlist:latest
```

#### [**docker compose**](https://oplist.org/zh/guide/install/docker.html#docker-compose)



```yaml
version: '3.3'
services:
  openlist:
    image: 'openlistteam/openlist:latest'
    container_name: openlist
    volumes:
      - '/etc/openlist:/opt/openlist/data'
    ports:
      - '5244:5244'
    environment:
      - PUID=0
      - PGID=0
      - UMASK=022
    restart: unless-stopped
```

#### [**环境变量**](https://oplist.org/zh/guide/install/docker.html#环境变量)

| 名称        | 默认值 | 说明                                                         |
| :---------- | :----- | ------------------------------------------------------------ |
| `PUID`      | `0`    | 运行身份 UID                                                 |
| `PGID`      | `0`    | 运行身份 GID                                                 |
| `UMASK`     | `022`  | https://en.wikipedia.org/wiki/Umask                          |
| `RUN_ARIA2` |        | 是否同时运行 ARIA2，当镜像含有 aria2 环境时默认为 `true`，否则为 `false` |
| `TZ`        |        | 默认为 UTC 时区，如果你想指定时区，则可以设置此变量，例如：`Asia/Shanghai` |

#### [**镜像版本**](https://oplist.org/zh/guide/install/docker.html#镜像版本)

稳定版：`openlistteam/openlist:latest` 或指定本版，如 `openlistteam/openlist:beta`(Latest暂未上线)

最新镜像版本，请参阅 https://hub.docker.com/r/openlistteam/openlist/tags

开发版：`openlistteam/openlist:beta`

预装环境镜像后缀:

| 后缀     | 说明                                   |
| :------- | -------------------------------------- |
| `aio`    | 同时包含下列所有预装环境的镜像         |
| `ffmpeg` | 预装 ffmpeg 的镜像，用于本地存储缩略图 |
| `aria2`  | 预装 aria2 的镜像，用于离线下载        |

你可以在上述任意镜像标签后面，使用 `-` 符号附加后缀以切换到附带环境的镜像。如 `openlistteam/openlist:latest-aio` `openlistteam/openlist:latest-aria2` `openlistteam/openlist:latest-ffmpeg`(Latest暂未上线)

如果使用预装 ffmpeg 镜像缩略图功能仍无法使用，请确认:

- 使用的是本地存储
- 切换到网格视图
- 本地存储的缩略图开关开启
- 本地存储的缩略图缓存文件夹配置路径正确，例如 `data/thumbnail`

当使用预装 aria2 镜像时，可能会在 openlist 的日志中看到类似错误：



```
ERRO[2022-11-20 12:05:19] error [unaligned 64-bit atomic operation] while run task  [download http://xxx.com/xxx.png to [/ftp](/)]
```

解决方法是，如果是 CPU 架构是 64 位，可以尝试手动拉取 64 位镜像或重新构建容器。 如果是 CPU 架构是 32 位，目前尚无可用方案。

## [**查看管理员信息：**](https://oplist.org/zh/guide/install/docker.html#查看管理员信息)

#### [**低于v3.25.0版本**](https://oplist.org/zh/guide/install/docker.html#低于v3-25-0版本)



```bash
docker exec -it openlist ./openlist admin
```

#### [**高于v3.25.0版本**](https://oplist.org/zh/guide/install/docker.html#高于v3-25-0版本)

3.25.0以上版本将密码改成加密方式存储的hash值，无法直接反算出密码，如果忘记了密码只能通过重新 **`随机生成`** 或者 **`手动设置`**



```bash
# 随机生成一个密码
docker exec -it openlist ./openlist admin random
# 手动设置一个密码,`NEW_PASSWORD`是指你需要设置的密码
docker exec -it openlist ./openlist admin set NEW_PASSWORD
```

## [**更新**](https://oplist.org/zh/guide/install/docker.html#更新)

<details class="hint-container details" style="background: var(--detail-c-bg); transition: background var(--vp-t-transform),color var(--vp-t-transform); display: block; margin-block: 0.75rem; padding: 1.25rem 1rem; border-radius: 0.5rem; scroll-behavior: auto !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important;"><summary style="background-attachment: initial !important; scroll-behavior: auto !important; transition-delay: 0s !important; transition-duration: 0s !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important; position: relative; margin: -1rem; padding-block: 1em; padding-inline: 3em 1.5em; list-style: none; font-size: var(--hint-font-size); cursor: pointer;">docker-cli 更新</summary><ol style="background-attachment: initial !important; scroll-behavior: auto !important; transition-delay: 0s !important; transition-duration: 0s !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important; line-height: 1.6; overflow-wrap: break-word; padding-inline-start: 1.2em;"><li style="background-attachment: initial !important; scroll-behavior: auto !important; transition-delay: 0s !important; transition-duration: 0s !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important;"><p style="background-attachment: initial !important; scroll-behavior: auto !important; transition-delay: 0s !important; transition-duration: 0s !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important; line-height: 1.6; overflow-wrap: break-word; margin-bottom: 0px; padding-bottom: 0px;"></p></li><li style="background-attachment: initial !important; scroll-behavior: auto !important; transition-delay: 0s !important; transition-duration: 0s !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important;"><p style="background-attachment: initial !important; scroll-behavior: auto !important; transition-delay: 0s !important; transition-duration: 0s !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important; line-height: 1.6; overflow-wrap: break-word; margin-bottom: 0px; padding-bottom: 0px;"></p></li><li style="background-attachment: initial !important; scroll-behavior: auto !important; transition-delay: 0s !important; transition-duration: 0s !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important;"><p style="background-attachment: initial !important; scroll-behavior: auto !important; transition-delay: 0s !important; transition-duration: 0s !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important; line-height: 1.6; overflow-wrap: break-word; margin-bottom: 0px; padding-bottom: 0px;"></p></li><li style="background-attachment: initial !important; scroll-behavior: auto !important; transition-delay: 0s !important; transition-duration: 0s !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important;"><p style="background-attachment: initial !important; scroll-behavior: auto !important; transition-delay: 0s !important; transition-duration: 0s !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important; line-height: 1.6; overflow-wrap: break-word; margin-bottom: 0px; padding-bottom: 0px;"></p></li><li style="background-attachment: initial !important; scroll-behavior: auto !important; transition-delay: 0s !important; transition-duration: 0s !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important;"><p style="background-attachment: initial !important; scroll-behavior: auto !important; transition-delay: 0s !important; transition-duration: 0s !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important; line-height: 1.6; overflow-wrap: break-word; margin-bottom: 0px; padding-bottom: 0px;"><a href="https://oplist.org/zh/guide/install/docker.html#docker-cli" style="background-attachment: initial !important; scroll-behavior: auto !important; transition-delay: 0s !important; transition-duration: 0s !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important; color: var(--vp-c-accent); font-weight: 500; text-decoration: none; overflow-wrap: break-word;"></a></p></li><li style="background-attachment: initial !important; scroll-behavior: auto !important; transition-delay: 0s !important; transition-duration: 0s !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important;"><p style="background-attachment: initial !important; scroll-behavior: auto !important; transition-delay: 0s !important; transition-duration: 0s !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important; line-height: 1.6; overflow-wrap: break-word; margin-bottom: 0px; padding-bottom: 0px;"></p></li></ol><p style="background-attachment: initial !important; scroll-behavior: auto !important; transition-delay: 0s !important; transition-duration: 0s !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important; line-height: 1.6; overflow-wrap: break-word; margin-bottom: 0px; padding-bottom: 0px;"><strong style="background-attachment: initial !important; scroll-behavior: auto !important; transition-delay: 0s !important; transition-duration: 0s !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important; font-weight: 600;"></strong><br style="background-attachment: initial !important; scroll-behavior: auto !important; transition-delay: 0s !important; transition-duration: 0s !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important;"><img src="https://oplist.org/img/faq/updocker.png" alt="docker" loading="lazy" style="background-attachment: initial !important; scroll-behavior: auto !important; transition-delay: 0s !important; transition-duration: 0s !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important; max-width: 100%;"></p></details>

<details class="hint-container details" style="background: var(--detail-c-bg); transition: background var(--vp-t-transform),color var(--vp-t-transform); display: block; margin-block: 0.75rem; padding: 1.25rem 1rem; border-radius: 0.5rem; scroll-behavior: auto !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important;"><summary style="background-attachment: initial !important; scroll-behavior: auto !important; transition-delay: 0s !important; transition-duration: 0s !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important; position: relative; margin: -1rem; padding-block: 1em; padding-inline: 3em 1.5em; list-style: none; font-size: var(--hint-font-size); cursor: pointer;">docker-compose 更新</summary><ol style="background-attachment: initial !important; scroll-behavior: auto !important; transition-delay: 0s !important; transition-duration: 0s !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important; line-height: 1.6; overflow-wrap: break-word; padding-inline-start: 1.2em;"><li style="background-attachment: initial !important; scroll-behavior: auto !important; transition-delay: 0s !important; transition-duration: 0s !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important;"></li><li style="background-attachment: initial !important; scroll-behavior: auto !important; transition-delay: 0s !important; transition-duration: 0s !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important;"></li></ol></details>

Q：我的版本是v3.x.x 怎么也升级不到最新版 `docker pull openlistteam/openlist:beta`拉取最新不行 改成docker-compose安装还是3.x.x版本

A：原因是你的docker设置了镜像，从镜像更新不到最新版本，改一下/etc/docker/daemon.json，删除"registry-mirrors": ["镜像加速器地址"]

- 删除若不行，可以考虑更换一个`镜像加速地址`
- 或者简单粗暴：下载时将`openlistteam/openlist:beta` 替换为`openlistteam/openlist:v4.0.0`（指定版本，写教程时最新的是4.0.0）

### [**编译镜像**](https://oplist.org/zh/guide/install/docker.html#编译镜像)

安装 docker，克隆仓库后进入仓库根目录，无需其他准备

basicbuild-arg



```bash
docker build -t openlistteam/openlist:beta .
```

可用 build args：

|                       | 说明        |
| :-------------------- | ----------- |
| `INSTALL_FFMPEG=true` | 安装 ffmpeg |
| `INSTALL_ARIA2=true`  | 安装 aria2  |







# 从源码运行

[The OpenList Projects Contributors](https://github.com/OpenListTeam)2025/7/7**Guide****Install****Guide**大约 1 分钟

------

此页内容

警告

此步骤仅适用于需要自行修改源代码的用户。 不明白的请跳过。

## [**环境准备**](https://oplist.org/zh/guide/install/source.html#环境准备)

首先，你需要一个有`git`，`nodejs`，`pnpm`，`golang>=1.20`，`gcc`的环境

## [**构建前端**](https://oplist.org/zh/guide/install/source.html#构建前端)

使用 `git clone --recurse-submodules https://github.com/OpenListTeam/OpenList-Frontend.git` 克隆前端 ，执行 `pnpm install && pnpm build` 得到 dist 目录下的目标文件

## [**构建后端**](https://oplist.org/zh/guide/install/source.html#构建后端)

克隆 https://github.com/OpenListTeam/OpenList ，将上一步的 `dist` 目录复制到项目下的 `public` 目录下，然后执行：



```bash
appName="openlist"
builtAt="$(date +'%F %T %z')"
goVersion=$(go version | sed 's/go version //')
gitAuthor=$(git show -s --format='format:%aN <%ae>' HEAD)
gitCommit=$(git log --pretty=format:"%h" -1)
version=$(git describe --long --tags --dirty --always)
webVersion=$(curl -s --max-time 5 "https://api.github.com/repos/OpenListTeam/OpenList-Frontend/releases/latest" -L | grep '"tag_name":' | sed -E 's/.*"([^"]+)".*/\1/' | sed 's/^v//')
if [ -z "$webVersion" ]; then
    webVersion="0.0.0"
fi
ldflags="\
-w -s \
-X 'github.com/OpenListTeam/OpenList/internal/conf.BuiltAt=$builtAt' \
-X 'github.com/OpenListTeam/OpenList/internal/conf.GoVersion=$goVersion' \
-X 'github.com/OpenListTeam/OpenList/internal/conf.GitAuthor=$gitAuthor' \
-X 'github.com/OpenListTeam/OpenList/internal/conf.GitCommit=$gitCommit' \
-X 'github.com/OpenListTeam/OpenList/internal/conf.Version=$version' \
-X 'github.com/OpenListTeam/OpenList/internal/conf.WebVersion=$webVersion' \
"
go build -ldflags="$ldflags" .
```

<details class="hint-container details" style="background: var(--detail-c-bg); transition: background var(--vp-t-transform),color var(--vp-t-transform); display: block; margin-block: 0.75rem; padding: 1.25rem 1rem; border-radius: 0.5rem; scroll-behavior: auto !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important;"><summary style="background-attachment: initial !important; scroll-behavior: auto !important; transition-delay: 0s !important; transition-duration: 0s !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important; position: relative; margin: -1rem; padding-block: 1em; padding-inline: 3em 1.5em; list-style: none; font-size: var(--hint-font-size); cursor: pointer;">你可能需要的编译教程视频</summary><p style="background-attachment: initial !important; scroll-behavior: auto !important; transition-delay: 0s !important; transition-duration: 0s !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important; line-height: 1.6; overflow-wrap: break-word;"><strong style="background-attachment: initial !important; scroll-behavior: auto !important; transition-delay: 0s !important; transition-duration: 0s !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important; font-weight: 600;"><a href="https://www.bilibili.com/video/BV1Xr4y1z723" target="_blank" rel="noopener noreferrer" style="background-attachment: initial !important; scroll-behavior: auto !important; transition-delay: 0s !important; transition-duration: 0s !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important; color: var(--vp-c-accent); font-weight: 500; text-decoration: none; overflow-wrap: break-word;"></a></strong><br style="background-attachment: initial !important; scroll-behavior: auto !important; transition-delay: 0s !important; transition-duration: 0s !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important;"></p><p style="background-attachment: initial !important; scroll-behavior: auto !important; transition-delay: 0s !important; transition-duration: 0s !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important; line-height: 1.6; overflow-wrap: break-word;"><strong style="background-attachment: initial !important; scroll-behavior: auto !important; transition-delay: 0s !important; transition-duration: 0s !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important; font-weight: 600;"><a href="https://www.bilibili.com/video/BV1GW4y1s742" target="_blank" rel="noopener noreferrer" style="background-attachment: initial !important; scroll-behavior: auto !important; transition-delay: 0s !important; transition-duration: 0s !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important; color: var(--vp-c-accent); font-weight: 500; text-decoration: none; overflow-wrap: break-word;"></a></strong></p><p style="background-attachment: initial !important; scroll-behavior: auto !important; transition-delay: 0s !important; transition-duration: 0s !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important; line-height: 1.6; overflow-wrap: break-word; margin-bottom: 0px; padding-bottom: 0px;"><strong style="background-attachment: initial !important; scroll-behavior: auto !important; transition-delay: 0s !important; transition-duration: 0s !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important; font-weight: 600;"><a href="https://www.yuque.com/anwenya/alist/glqlhu" target="_blank" rel="noopener noreferrer" style="background-attachment: initial !important; scroll-behavior: auto !important; transition-delay: 0s !important; transition-duration: 0s !important; animation-duration: 1ms !important; animation-delay: -1ms !important; animation-iteration-count: 1 !important; color: var(--vp-c-accent); font-weight: 500; text-decoration: none; overflow-wrap: break-word;"></a></strong></p></details>





# 反向代理

[The OpenList Projects Contributors](https://github.com/OpenListTeam)2025/7/7**Guide****Install****Guide**大约 2 分钟

------

此页内容

程序默认监听 5244 端口。如有修改，请一并修改下列配置中的端口号。如果你使用反向代理，建议你设置[site_url](https://oplist.org/zh/config/configuration.html#site_url)，以帮助alist更好的工作。

> 如果你想使用子目录，参考[这里](https://oplist.org/zh/faq/howto.html#如何对子目录进行反向代理)

反向代理非标准端口或启用https后丢失https或端口号/无法播放视频?

你需要通过正确的Host头,请参考 [#726](https://github.com/alist-org/alist/issues/726) [#1159](https://github.com/alist-org/alist/issues/1159) [#2429](https://github.com/alist-org/alist/issues/2429) [#3644](https://github.com/alist-org/alist/issues/3644) [#4181](https://github.com/alist-org/alist/issues/4181) [#4719](https://github.com/alist-org/alist/issues/4719)

## [**nginx**](https://oplist.org/zh/guide/install/reverse-proxy.html#nginx)

在网站配置文件的 server 字段中添加

conf



```bash
location / {
  proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  proxy_set_header X-Forwarded-Proto $scheme;
  proxy_set_header Host $http_host;
  proxy_set_header X-Real-IP $remote_addr;
  proxy_set_header Range $http_range;
	proxy_set_header If-Range $http_if_range;
  proxy_redirect off;
  proxy_pass http://127.0.0.1:5244;
  # the max size of file to upload
  client_max_body_size 20000m;
}
```

如果需要使用HTTP/3，需要将对应`HOST`行修改为：

conf



```bash
proxy_set_header Host $host:$server_port;
```

这样修改后的配置同时也可以兼容HTTP/2及更低版本的请求。

注意

如果使用宝塔面板，请务必删除以下默认配置

conf



```bash
- location ~ ^/(\.user.ini|\.htaccess|\.git|\.svn|\.project|LICENSE|README.md
- location ~ .\*\.(gif|jpg|jpeg|png|bmp|swf)$
- location ~ .\*\.(js|css)?$
```

并在`/www/server/nginx/conf/proxy.conf`中或对应网站配置文件中设置禁用Nginx缓存，否则默认配置下访问较大文件时Nginx会先尝试将远程文件缓存至本机，导致播放失败

conf



```bash
proxy_cache cache_one; # 删除这一行
proxy_max_temp_file_size 0; #加上这一行
```

## [**Apache**](https://oplist.org/zh/guide/install/reverse-proxy.html#apache)

在 VirtualHost 字段下添加配置项 ProxyPass，如：



```xml
<VirtualHost *:80>
    ServerName myapp.example.com
    ServerAdmin webmaster@example.com
    DocumentRoot /www/myapp/public

    AllowEncodedSlashes NoDecode
    ProxyPreserveHost On
    ProxyPass "/" "http://127.0.0.1:5244/" nocanon
    ProxyPassReverse "/" "http://127.0.0.1:5244/" nocanon
</VirtualHost>
```

## [**Caddy**](https://oplist.org/zh/guide/install/reverse-proxy.html#caddy)

在 Caddyfile 文件下添加 reverse_proxy，如：



```
:80 {
  reverse_proxy 127.0.0.1:5244
}
```

如果部署在 443 端口正常使用的服务器上且使用域名进行访问，建议使用这种配置让 Caddy 自动申请证书：



```
example.com {
  reverse_proxy 127.0.0.1:5244
}

将 `example.com` 替换为你自己解析后的域名。
```

## [**宝塔设置反向代理示范**](https://oplist.org/zh/guide/install/reverse-proxy.html#宝塔设置反向代理示范)

#### [1.登录宝塔面板，添加站点；](https://oplist.org/zh/guide/install/reverse-proxy.html#_1-登录宝塔面板-添加站点)

![bt_new_website](https://cdn.jsdelivr.net/gh/otxtdb/txtdbpic@master/img/006d4bf79df20c89a3a065d146a6a02a.png)

#### [2.修改站点设置；](https://oplist.org/zh/guide/install/reverse-proxy.html#_2-修改站点设置)

![bt_new_website_01](https://cdn.jsdelivr.net/gh/otxtdb/txtdbpic@master/img/5334442b06881d88c723e5bf9e0cfc45.png)

#### [3.删除面板默认代码；](https://oplist.org/zh/guide/install/reverse-proxy.html#_3-删除面板默认代码)

![bt_delete_default_config_01](https://oplist.org/img/guide/reverse_proxy/bt_delete_default_config_01.png)

![bt_delete_default_config_02](https://oplist.org/img/guide/reverse_proxy/bt_delete_default_config_02.png)

#### [4.添加反向代理；](https://oplist.org/zh/guide/install/reverse-proxy.html#_4-添加反向代理)

![bt_reverse_proxy](https://cdn.jsdelivr.net/gh/otxtdb/txtdbpic@master/img/5eead835d05893b1c32506580734a859.png)

> 如需申请`SSL`证书，可先在`SSL`选项中申请证书，然后在设置反向代理。或者设置反向代理之后，关闭反向代理功能，申请`SSL`证书后再次开启代理。













