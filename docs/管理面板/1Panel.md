# 产品介绍

1Panel 是一个现代化、开源的 Linux 服务器运维管理面板。

![UI展示](_txtdbpic/e4056605920c339d32cd15f2f7039c8e_MD5.png)

## 1 产品优势[⚓︎](https://1panel.cn/docs/v2/#1)

- **高效管理**：用户可以通过 Web 图形界面轻松管理 Linux 服务器，实现主机监控、文件管理、数据库管理、容器管理等功能
- **快速建站**：深度集成开源建站软件 WordPress 和 [Halo](https://github.com/halo-dev/halo/)，域名绑定、SSL 证书配置等操作一键搞定
- **应用商店**：精选上架各类高质量的开源工具和应用软件，协助用户轻松安装并升级
- **安全可靠**：基于容器管理并部署应用，实现最小的漏洞暴露面，同时提供防火墙和日志审计等功能
- **一键备份**：支持一键备份和恢复，用户可以将数据备份到各类云端存储介质，永不丢失

## 2 教学视频[⚓︎](https://1panel.cn/docs/v2/#2)

您可以在哔哩哔哩（B 站）上搜索相关教学视频。[点击这里](https://space.bilibili.com/510493147/channel/collectiondetail?sid=1199760)

## 3 致谢贡献者[⚓︎](https://1panel.cn/docs/v2/#3)

[点击获取你的贡献者证书，参与社区回馈活动。](https://www.lxware.cn/1panel-contributors#/)





# 在线安装

## 1 环境要求[⚓︎](https://1panel.cn/docs/v2/installation/online_installation/#1)

**安装前请确保您的系统符合安装条件：**

- 操作系统：支持主流 Linux 发行版本（基于 Debian / RedHat，包括国产操作系统）
- 服务器架构：x86_64、aarch64、armv7l、ppc64le、s390x
- 内存要求：建议可用内存在 1GB 以上
- 浏览器要求：请使用 Chrome、FireFox、IE10+、Edge 等现代浏览器
- **可访问互联网**
- 如果是内网环境，推荐实现 [离线安装包](https://1panel.cn/docs/v2/installation/package_installation/) 方式进行部署



## 2 安装部署[⚓︎](https://1panel.cn/docs/v2/installation/online_installation/#2)

GitHub release 链接: https://github.com/1Panel-dev/1Panel/releases

执行以下安装脚本，根据命令行提示完成安装。

```
bash -c "$(curl -sSL https://resource.fit2cloud.com/1panel/package/v2/quick_start.sh)"
```



如果遇到 Docker 安装失败等问题，可以尝试运行以下脚本：

```
bash <(curl -sSL https://linuxmirrors.cn/docker.sh)
```

了解更多信息，请访问官方网站：[https://linuxmirrors.cn](https://linuxmirrors.cn/)

安装成功后，控制台会打印面板访问信息，可通过浏览器访问 1Panel：

```
http://目标服务器 IP 地址:目标端口/安全入口
```

- **如果使用的是云服务器，请在安全组中开放对应的目标端口**
- **ssh 登录 1Panel 服务器后，执行 `1pctl user-info` 命令可获取安全入口（entrance）**

安装成功后，可使用 [1pctl](https://1panel.cn/docs/v2/installation/cli/) 命令行工具来维护 1Panel







# 在线升级

登录 1Panel Web 控制台，在页面右下角点击 **【检查更新】** 进行在线升级。

![img.png](_txtdbpic/53035faf7322a6e03130ba89357d917b_MD5.png)







# 1Panel 离线版

## 1. 特点[⚓︎](https://1panel.cn/docs/v2/installation/package_installation/#1)

完全独立运行

- 离线版不连接互联网，不发送任何网络请求。
- 集成社区版的全部功能，可在无外网环境中独立运行。
- 尤其适用于企业内网、离线机房及涉密环境的部署场景。

应用商店支持

- 离线包中已预置常用应用的镜像，并会在安装完成后自动导入系统。
  - **OpenResty 版本**：`1.27.1.2-2-3-focal`
  - MySQL 版本：
    - **x86_64 包**：`8.4.6`、`8.0.43`、`5.7.44`、`5.6.51`
    - **arm64 包**：`8.4.6`、`8.0.43`
- 除了内置镜像，用户还可以通过导入外部镜像的方式来安装其他应用。
  - 其他应用需要用户手动导入镜像后才能使用，导入教程参考 [导入应用镜像](https://1panel.cn/docs/v2/installation/package_installation/#6)。
- 镜像一旦导入成功，即可在 1Panel 应用商店中显示并安装，灵活性高。

支持主流信创

- 支持主流信创环境（海光、鲲鹏，麒麟、欧拉），确保在多样化的国产软硬件体系下稳定运行。

自动安装 Docker

- 安装过程中若检测到系统未安装 Docker，脚本将自动完成 Docker 的安装。

## 2. 环境要求[⚓︎](https://1panel.cn/docs/v2/installation/package_installation/#2)

- **操作系统**：支持主流 Linux 发行版本（基于 Debian / RedHat，包括国产操作系统）
- **服务器架构**：支持 `x86_64` 和 `arm64`
- **内存要求**：建议可用内存在 **1GB 以上**
- **浏览器要求**：请使用 **Chrome、Firefox** 等现代浏览器

## 3. 下载离线包[⚓︎](https://1panel.cn/docs/v2/installation/package_installation/#3)

⚠️ **重要提示：请勿从闲鱼等第三方平台购买或下载所谓的“1Panel 离线包”**
🚫 这些来源均为 **未经授权的盗版渠道**，我们无法保证其安全性，极有可能被篡改、植入木马或病毒，存在服务器被入侵或数据泄露风险。

> 

## 4. 安装部署[⚓︎](https://1panel.cn/docs/v2/installation/package_installation/#4)

### 4.1 解压离线包[⚓︎](https://1panel.cn/docs/v2/installation/package_installation/#41)

请下载最新的 1Panel 离线包，上传至服务器 `/tmp` 目录，并以 **root 用户** 执行以下命令进行安装准备：

```
cd /tmp
# 解压离线包（请将示例文件名替换为实际名称）
tar zxvf 1panel-v2.0.11-offline-linux-amd64.tar.gz
```

### 4.2 执行安装脚本[⚓︎](https://1panel.cn/docs/v2/installation/package_installation/#42)

```
# 进入解压目录（请根据实际目录名替换）
cd 1panel-v2.0.11-offline-linux-amd64

# 执行安装脚本
/bin/bash install.sh
```

## 5. 升级版本[⚓︎](https://1panel.cn/docs/v2/installation/package_installation/#5)

### 5.1 解压离线包[⚓︎](https://1panel.cn/docs/v2/installation/package_installation/#51)

请下载最新的 1Panel 离线包，上传至服务器 `/tmp` 目录，并以 **root 用户** 执行以下命令进行升级准备：

```
cd /tmp
# 解压离线包（请将示例文件名替换为实际名称）
tar zxvf 1panel-v2.0.12-offline-linux-amd64.tar.gz
```

### 5.2 执行升级脚本[⚓︎](https://1panel.cn/docs/v2/installation/package_installation/#52)

```
# 进入解压目录（请根据实际目录名替换）
cd 1panel-v2.0.12-offline-linux-amd64

# 执行升级脚本
/bin/bash upgrade.sh
```

## 6. 登录访问[⚓︎](https://1panel.cn/docs/v2/installation/package_installation/#6)

安装成功后，控制台将显示面板访问信息。可通过浏览器访问：

```
http://目标服务器IP地址:目标端口/安全入口
```

- **如使用云服务器，请确保安全组已开放目标端口**
- **执行 `1pctl user-info` 命令可查看安全入口（entrance）**

安装完成后，可使用 [1pctl 命令行工具](https://1panel.cn/docs/v2/installation/cli/) 进行日常维护。

## 7. 导入应用镜像[⚓︎](https://1panel.cn/docs/v2/installation/package_installation/#7)

如需使用其他应用（如 WordPress），可手动导入镜像，具体步骤如下：

1. **在可联网机器上拉取并导出镜像**：

   ```
   docker pull wordpress:6.8.2
   docker save -o /tmp/wordpress_6.8.2.tar wordpress:6.8.2
   ```

2. **上传镜像文件**：将 `wordpress_6.8.2.tar` 上传至 1Panel 服务器的 `/tmp` 目录

   ```
   scp /tmp/wordpress_6.8.2.tar root@<1Panel 离线服务器 IP>:/tmp/
   ```

3. **导入镜像**：在 1Panel 服务器上执行：

   ```
   docker load -i /tmp/wordpress_6.8.2.tar
   ```

完成上述步骤后，即可在应用商店安装 WordPress 应用。

## 8. 应用安装方式说明[⚓︎](https://1panel.cn/docs/v2/installation/package_installation/#8)

在离线版中，安装应用与通过「本地应用」安装应用存在一定差异，主要体现在以下几点：

### 8.1 对比结果[⚓︎](https://1panel.cn/docs/v2/installation/package_installation/#81)

| 方式             | 应用来源       | 是否包含所有应用 | 是否自动集成功能菜单   |
| :--------------- | :------------- | :--------------- | :--------------------- |
| 离线版安装应用   | 离线包中已预置 | ✅ 是             | ✅ 是（如网站、数据库） |
| 本地应用方式安装 | 用户手动上传   | ❌ 否             | ❌ 否                   |

### 8.2 推荐使用场景[⚓︎](https://1panel.cn/docs/v2/installation/package_installation/#82)

- 离线版安装应用

  ：适合无网络环境下快速部署，所有功能完整，体验最佳。

  - 例如：`OpenResty`、`MySQL` 等应用在安装完成后，会自动与 **网站管理**、**数据库管理** 等功能页面集成，用户可直接创建网站和数据库。

- **本地应用方式**：适合测试自定义应用包，或安装不在官方应用商店中的应用。







# 主从节点切换

## 1 安装 1panel-migrator[⚓︎](https://1panel.cn/docs/v2/installation/master_migrate/#1-1panel-migrator)

### 1.1 安装包获取[⚓︎](https://1panel.cn/docs/v2/installation/master_migrate/#11)

请访问 [1PanelGitee 发布页面](https://gitee.com/fit2cloud-feizhiyun/1panel-migrator/releases/)，手动下载适用于您服务器架构的安装包，并将其放置到 `/tmp` 目录：

**提示**：请确保安装包版本 **大于等于 v2.0.8**，该版本及以上才支持主从节点切换功能。

每个版本会提供以下架构的安装包（文件名示例）：

- `1panel-migrator-linux-amd64`
- `1panel-migrator-linux-arm64`
- `1panel-migrator-linux-arm`
- `1panel-migrator-linux-ppc64le`
- `1panel-migrator-linux-s390x`

### 1.2 安装步骤[⚓︎](https://1panel.cn/docs/v2/installation/master_migrate/#12)

以 amd64 架构为例说明 1panel-migrator 的安装步骤：

```
# （1）进入临时目录
cd /tmp

# （2）添加执行权限
chmod +x 1panel-migrator-linux-amd64

# （3）移动至系统 PATH 中并重命名
mv 1panel-migrator-linux-amd64 /usr/local/bin/1panel-migrator
```

## 2 从节点 -> 主节点[⚓︎](https://1panel.cn/docs/v2/installation/master_migrate/#2-)

从节点升级为主节点需要先在原来主节点上设置好主节点备份，仅存在备份文件的主节点支持升级到主节点：

（1）打开节点列表，点击上方主节点备份。

（2）勾选备份节点，设置自动备份频率及保留份数，保存设置。

（3）点击执行备份，查看备份结果。

![img.png](_txtdbpic/44ed8308d3d0bd094e9396dd2d9c30f3_MD5.png)

（4）打开需要升级的从节点，通过安装好的 1panel-migrator 执行升级命令 `1panel-migrator promote` 。

![img.png](_txtdbpic/a54ea410dc82787cd6cf021d5bb4a788_MD5.png)

## 3 主节点 -> 从节点[⚓︎](https://1panel.cn/docs/v2/installation/master_migrate/#3-)

打开需要降级的主节点，通过安装好的 1panel-migrator 执行降级命令 `1panel-migrator demote`。

![img.png](_txtdbpic/18c77375e191ca0e913baaa7dfdfdeac_MD5.png)







# 命令行工具

## 1 1pctl[⚓︎](https://1panel.cn/docs/v2/installation/cli/#1-1pctl)

1Panel 默认内置了命令行运维工具 **1pctl**，通过执行 1pctl help，可以查看相关的命令说明。

```
Usage:
  ./1pctl [COMMAND] [ARGS...]
  ./1pctl --help

Commands:
  status [core|agent]         检查 1Panel 服务状态
  start [core|agent|all]      启动 1Panel 服务
  stop [core|agent|all]       停止 1Panel 服务
  restart [core|agent|all]    重启 1Panel 服务
  uninstall                   卸载 1Panel 服务
  user-info                   获取 1Panel 用户信息
  listen-ip                   切换 1Panel 监听 IP
  version                     查看 1Panel 版本信息
  update                      修改 1Panel 系统信息
  reset                       重置 1Panel 系统信息
  restore                     恢复 1Panel 服务及数据
```

## 2 1pctl 典型应用说明[⚓︎](https://1panel.cn/docs/v2/installation/cli/#2-1pctl)

### 2.1 1pctl reset[⚓︎](https://1panel.cn/docs/v2/installation/cli/#21-1pctl-reset)

**重置 1Panel 系统信息，包括取消安全入口登录，取消两步验证等**

```
Usage:
  1panel reset [command]

Available Commands:

  domain      取消 1Panel 访问域名绑定
  entrance    取消 1Panel 安全入口
  https       取消 1Panel https 方式登录
  ips         取消 1Panel 授权 IP 限制
  mfa         取消 1Panel 两步验证
```

### 2.2 1pctl listen-ip[⚓︎](https://1panel.cn/docs/v2/installation/cli/#22-1pctl-listen-ip)

**修改 1Panel 监听 IP**

```
Usage:
  1pctl listen-ip [COMMAND] [ARGS...]
  1pctl listen-ip --help

Commands: 
  ipv4                监听 IPv4
  ipv6                监听 IPv6
```

### 2.3 1pctl update[⚓︎](https://1panel.cn/docs/v2/installation/cli/#23-1pctl-update)

**修改 1Panel 系统信息**

```
Usage:
  1pctl update [COMMAND] [ARGS...]
  1pctl update --help

Commands: 
  username            修改面板用户
  password            修改面板密码
  port                修改面板端口
```







# 概述

## 1 功能概述[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/appstore/#1)

- **功能概述**

应用商店旨在为用户提供便捷、高效的应用部署和管理体验。通过应用商店，用户可以一键安装多种常见的建站工具、服务和开发环境，如 WordPress、Halo、PHP、Node.js、MySQL 等，不再需要复杂的手动配置。

此外，1Panel 应用商店还提供应用的备份恢复、升级等功能，确保用户的数据安全和应用的持续可用性，为日常运维和站点管理提供了极大便利。

- **本地应用**

添加自己想要的应用，1Panel 应用商店还支持本地应用。制作教程可参考：[提交自定义应用教程](https://github.com/1Panel-dev/appstore/wiki/如何提交自己想要的应用)，也可以参考论坛文章：[1Panel 本地应用创建技巧及第三方应用库举例](https://bbs.fit2cloud.com/t/topic/640/)。

![img.png](_txtdbpic/409aac7f06f406aa15f5208d2ad7c006_MD5.png)







# 安装部署

在应用商店列表中找到并安装目标应用，您可以通过应用分类浏览，或者直接在右上角的搜索框中输入关键字快速查找。

> 本文将以安装 Halo 为例进行演示。

## 1 应用安装[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/install/#1)

（1）点击【安装】按钮进入应用详情页面。

![img.png](_txtdbpic/8b391cf760c9d64d9bc35bc78e13c25e_MD5.png)

（2）填写数据库、端口等参数。

![img.png](_txtdbpic/518593fac58d95820d25f17eb2419095_MD5.png)

（3）配置高级设置选项，例如是否暴露外部端口、资源限制以及编辑 compose文件等。最后，点击【确认】按钮，将弹出应用安装日志界面，等待应用安装完成。

![img.png](_txtdbpic/4a8ed7e551453714702660f81be721bc_MD5.png)

![img.png](_txtdbpic/1bfb79b39d30414cd548b4b17c36ebc4_MD5.png)







# 应用操作

进入已安装列表，用户可以对应用进行同步、升级、重启、启动、停止、删除、备份和恢复等操作。

![img.png](_txtdbpic/240b0e9d06f45b6198439fe4a790e87a_MD5.png)

## 1 同步[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/installed/#1)

点击【同步】按钮，可自动更新应用状态，确保与当前系统状态保持一致。

![img.png](_txtdbpic/77c9baa42474598974d0d77bdf0bf53d_MD5.png)

## 2 重建[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/installed/#2)

点击【重建】按钮，系统会删除现有的应用实例，并基于当前的设置和配置重新安装和启动应用。

![img.png](_txtdbpic/e9714ea56965da59d2fa8642be8610fe_MD5.png)

提示

重建应用会删除应用容器重新创建，配置了持久化的应用数据将会保留，如果有直接修改应用容器内其它文件，对应的修改内容将会被重置。

## 3 启动 / 停止 / 重启[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/installed/#3)

![img.png](_txtdbpic/81bb95d55bf3deb25e472c049404aeb6_MD5.png)

## 4 卸载[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/installed/#4)

点击【卸载】按钮，系统将自动执行卸载过程，删除应用的所有相关资源，包括容器、配置文件等。

- 强制删除：会忽略删除过程中产生的错误并最终删除元数据
- 删除备份：删除备份列表中的备份文件

![img.png](_txtdbpic/c5b6f1f3cff0a02944447fce7d5ef2b7_MD5.png)

## 5 应用详情[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/installed/#5)

点击【参数】按钮，可以查看并修改应用的相关参数。

![img.png](_txtdbpic/a05171a97c1b54083773534cc3b22ed0_MD5.png)

点击参数页面右上角的【编辑】按钮，可以对部分应用参数及应用高级设置进行修改，具体支持修改的参数与应用定义有关。

![img.png](_txtdbpic/c640715dfb685a012154f28e90ad7a6a_MD5.png)

## 6 备份 / 恢复[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/installed/#6)

点击【备份】按钮，进入备份列表。

![img.png](_txtdbpic/7f2ca8cfbfa9e4c7236e73a146232c7a_MD5.png)

点击【备份】按钮可立即备份当前应用。若需恢复应用，点击备份列表中的【恢复】按钮，将根据选定的备份恢复应用到相应状态。

![img.png](_txtdbpic/146a5ce5d935ed028b83a229334324ca_MD5.png)

也可将备份文件下载后，通过导入备份功能上传备份文件并进行恢复。

![img.png](_txtdbpic/1ac8e60ebfbeb173f4d9925471a97da0_MD5.png)

## 7 升级[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/installed/#7)

进入【可升级】页面，可查看当前支持升级的应用。

![img.png](_txtdbpic/1c37c3022aac80889799b239ec6e7ee6_MD5.png)

点击应用卡片上的【忽略升级】按钮，可以不再显示该应用的升级提示。可以通过点击列表上方的【查看忽略应用】查看所有已忽略升级的应用并取消忽略。

![img.png](_txtdbpic/2e95b3078d47f9a9ccada3749633b34a_MD5.png)

点击【升级】按钮后，选择目标版本。可选择在升级前备份应用、自动拉取最新镜像、以及自定义修改 compose.yml 文件等。最后点击【确认】按钮，等待升级完成。

![img.png](_txtdbpic/8f34a10706ace4733f134b889284f838_MD5.png)







# 应用商店设置

在应用商店设置页面，用户可以修改卸载、升级应用时的默认操作。

![img.png](_txtdbpic/4ecc3493538201c57863f5e4234ad86b_MD5.png)







# 概述

- 1Panel 的网站管理功能旨在为用户提供便捷、高效的网站创建与管理体验
- 通过 1Panel，用户可以轻松搭建多种类型的网站，包括静态网站、反向代理站点，以及支持 PHP、Java、Node.js、Go、Python 等运行环境的网站
- 面板提供了全面的管理选项，支持域名绑定、SSL 证书配置、HTTPS 启用、伪静态设置、重定向、防盗链等功能
- 此外，用户还可以通过 1Panel 实现网站数据的自动备份与恢复，确保数据安全。通过这些功能，1Panel 帮助用户轻松管理服务器上的各类网站

![img.png](_txtdbpic/0a6a90bed6d69e29e21afa9be97152c2_MD5.png)







# 创建网站

支持一键部署多种网站创建方式，包括运行环境（PHP、Java、Node.js、Go、Python）、反向代理和静态网站等，满足不同类型网站的快速搭建需求。

## 1 一键部署[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/website_create/#1)

可以通过应用商店中提供的应用，如 WordPress 和 Halo，轻松部署网站。

- **分组**：选择网站所属的分组
- **应用类型**：选择已安装的应用或新安装的应用
- **应用参数**：如果选择新安装应用，请填写相关参数
- **主域名**：输入需要绑定的主要域名及其端口
- **其他域名**：输入需要绑定的其他域名及其端口
- **监听 IPv6**：使服务器能够通过 IPv6 地址接收客户端请求
- **代号**：设定网站目录的文件夹名称
- **启用 HTTPS**：开启 HTTPS 并选择 SSL 证书
- **备注**：填写对该站点作用的描述

![img.png](_txtdbpic/4778961a2caca5bbaa56b2fc44c942a5_MD5.png)

## 2 运行环境[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/website_create/#2)

可以利用已添加的运行环境来创建网站。

- **分组**：选择网站所属的分组
- **类型**：选择运行环境类型及某个已创建的运行环境（目前支持 PHP、Java、Node.js、Go、Python、.NET）
- **端口**：指定网站服务的端口
- **主域名**：填写需要绑定的为站点创建一个数据库
- **启用 HTTPS**：开启 HTTPS 并选择 SSL 证书
- **备注**：提供该站点的功能描述

![img.png](_txtdbpic/0adfd31e391d9898a893847d8aa6471e_MD5.png)

## 3 反向代理[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/website_create/#3)

支持创建反向代理网站，允许用户将请求转发到其他服务。

- **分组**：选择网站所属的分组
- **主域名**：填写要绑定的主要域名及其端口
- **其他域名**：填写需要绑定的其他域名及其端口
- **监听 IPv6**：使服务器能够通过 IPv6 地址接收客户端请求
- **代号**：设定网站目录的文件夹名称
- **代理地址**：输入已有服务的地址，也可以从已安装应用中进行选择
- **启用 HTTPS**：开启 HTTPS 并选择 SSL 证书
- **备注**：描述该站点的功能或用途

![img.png](_txtdbpic/2d91afa36440171d625037273915d378_MD5.png)

## 4 静态网站[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/website_create/#4)

支持快速创建静态网站，提供便捷的部署和管理功能，让用户轻松发布和维护静态内容。

- **分组**：选择网站所属的分组
- **主域名**：填写需要绑定的主要域名及其端口
- **其他域名**：填写需要绑定的其他域名及其端口
- **监听 IPv6**：使服务器能够通过 IPv6 地址接收客户端请求
- **代号**：设置代号，作为网站目录的文件夹名称
- **创建 FTP**：创建站点的同时，为站点创建一个对应 FTP 帐户，并且 FTP 目录指向站点所在目录
- **启用 HTTPS**：开启 HTTPS 并选择 SSL 证书
- **备注**：简要描述该站点的功能或用途

![img.png](_txtdbpic/ffc495e9241ef15f1d7d6f22c3f2f3c5_MD5.png)

## 5 子网站[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/website_create/#5)

为已有的 PHP 或静态页面类型网站创建子网站，子网站可以选择已存在的 PHP 和静态网站的目录作为主目录。

- **分组**：选择网站所属的分组
- **父级网站**：当前子网站的父级网站
- **运行目录**：选择父级网站运行目录下的子目录作为当前网站运行目录
- **主域名**：填写需要绑定的主要域名及其端口
- **其他域名**：填写需要绑定的其他域名及其端口
- **监听 IPv6**：使服务器能够通过 IPv6 地址接收客户端请求
- **代号**：设置代号，作为网站目录的文件夹名称
- **启用 HTTPS**：开启 HTTPS 并选择 SSL 证书
- **备注**：简要描述该站点的功能或用途

![img.png](_txtdbpic/83fbdf8001e7a5803eccf022c309be6b_MD5.png)







# 基本设置

网站设置页面包含多种功能，包括域名设置、网站目录、默认文档、流量限制、反向代理、负载均衡、密码访问、HTTPS 配置、真实 IP、伪静态、防盗链、重定向、关联数据库及其他设置。

## 1 域名设置[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/website_config_basic/#1)

域名设置页面允许用户管理网站的域名和端口配置。

![img.png](_txtdbpic/f2ae1dde96f692e02be6e07aa14f53bf_MD5.png)

## 2 网站目录[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/website_config_basic/#2)

网站目录页面支持查看网站的根目录，设置运行目录，以及配置运行用户和用户组等选项。

![img.png](_txtdbpic/bde1008348bcf5c69086ba40f705baa6_MD5.png)

## 3 默认文档[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/website_config_basic/#3)

配置默认文档，以便在用户访问网站根目录时自动加载指定的文件。

![img_1.png](_txtdbpic/5bd29864a637f00c44ba042ff4dd1774_MD5.png)

## 4 流量限制[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/website_config_basic/#4)

允许用户配置流量限制，通过选择不同的限制方案，控制网站的带宽和访问流量。

![img.png](_txtdbpic/963321565377719d92bdf0c6961dceda_MD5.png)

## 5 反向代理[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/website_config_basic/#5)

反向代理功能允许将网站请求转发到后端服务器，以实现负载均衡、安全控制和内容分发。

![img.png](_txtdbpic/479ab373e4fa4908c47100c322d38fff_MD5.png)

用户也可以在当前页面开启并配置反向代理缓存规则，或者清除当前缓存。

![img.png](_txtdbpic/0ae8d238216a09f8e992333c184878c0_MD5.png)

## 6 负载均衡[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/website_config_basic/#6)

创建负载均衡规则，用于将当前网站请求转发到多个后端服务。当前页面仅创建负载均衡规则，使用负载均衡规则需要在创建反向代理时使用 `http://<负载均衡名称>`。

![img.png](_txtdbpic/cf2172c6d1a7a77e41d30f1ea2f83e94_MD5.png)

## 7 密码访问[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/website_config_basic/#7)

密码访问功能允许用户为网站设置访问密码，以增强网站的安全性，限制未经授权的访问。支持创建全局配置或按路径配置。

![img.png](_txtdbpic/e1bb9f9bcda1a8371ad852dd2e25498f_MD5.png)

## 8 HTTPS[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/website_config_basic/#8-https)

配置网站的 HTTPS 功能时，用户需要填写或选择以下信息：

- HTTP 选项

  ：选择访问方式，包括：

  - 自动将 HTTP 跳转到 HTTPS
  - 允许直接访问 HTTP
  - 禁止 HTTP 访问

- **HSTS**：开启 HSTS，以提升网站安全性

- **HTTP3**：开启 HTTP3，HTTP/3 是 HTTP/2 的升级版本，提供更快的连接速度和更好的性能，但是不是所有浏览器都支持 HTTP/3，开启后可能会导致部分浏览器无法访问

- SSL 选项

  ：选择现有证书或手动导入证书，选择已有证书需通过 1Panel 证书模块申请

  - **Acme 账户（选择已有证书）**：选择已存在的 Acme 账户
  - **证书（选择已有证书）**：选择已存在的证书
  - **导入方式（手动导入证书）**：手动粘贴证书文件内容或者从服务器选择证书文件
  - **私钥（手动导入证书）**：私钥文件内容或文件位置
  - **证书（手动导入证书）**：证书文件内容或文件配置

- **支持的协议版本**：选择 SSL 协议版本

- **加密算法**：指定 SSL 加密算法

通过以上配置，用户可以有效提升网站的安全性和访问性能。

![img.png](_txtdbpic/49f9041b95664eac504fcd6486a12882_MD5.png)

## 9 真实 IP[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/website_config_basic/#9-ip)

配置客户端 IP 获取方式及可信的 IP 来源，OpenResty 会分析 HTTP Header 中的 IP 信息，准确识别并记录访客的真实 IP 地址，包括在访问日志中。

![img.png](_txtdbpic/bfeb60aaa755649d3e1d2a6872d147df_MD5.png)

## 10 伪静态[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/website_config_basic/#10)

伪静态功能通过将动态 URL 转换为更友好的静态 URL，提高网站的可读性和搜索引擎优化效果。

![img.png](_txtdbpic/eae27b4002f46aefa808b5e10ba7836c_MD5.png)

## 11 防盗链[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/website_config_basic/#11)

防盗链功能通过验证请求来源，阻止非授权用户直接链接和下载网站资源，以保护网站内容安全。

![img.png](_txtdbpic/2c9ab8ac658c6bd6e3be33c22415187e_MD5.png)

## 12 重定向[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/website_config_basic/#12)

重定向功能允许将访问特定URL的请求自动转发到另一个URL，以实现链接管理和流量引导。

![img.png](_txtdbpic/f3efd3c7aa903ba5fdfee66c067cde8a_MD5.png)

## 13 PHP[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/website_config_basic/#13-php)

静态页面类型的网站可以在此选择 PHP 运行环境切换为 PHP 类型网站，PHP 类型的网站可以切换不同的 PHP 运行环境。

![img.png](_txtdbpic/116ba297b42daaf617ff6b72ca920f00_MD5.png)

## 14 资源[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/website_config_basic/#14)

将当前网站与某一个数据库进行关联，备份网站时将同时备份关联的数据库。切换其他数据库会导致以前的备份无法恢复。

![img.png](_txtdbpic/ba49bc453b1dce9a35d827c62da0e79d_MD5.png)

## 15 其他[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/website_config_basic/#15)

支持更改主域名、切换分组以及更新备注信息等操作。

![img.png](_txtdbpic/31c7a9468c1c5ebf803d5e8082ff0647_MD5.png)







# 其他设置

## 1 日志[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/website_config_other/#1)

1Panel 的网站日志查看功能支持以下操作：

- 查看正常日志和错误日志
- 开启/关闭日志记录
- 实时追踪日志内容
- 下载日志文件
- 清空日志内容

![img.png](_txtdbpic/35f1b9f9a4367818372135c64d66755e_MD5.png)

## 2 配置文件[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/website_config_other/#2)

- 查看并修改目标网站的 OpenResty 配置文件设置
- PHP 运行环境网站还支持修改 FPM 和 PHP 配置文件

![img.png](_txtdbpic/0b80a56de350c332a65e4919883fb24d_MD5.png)

## 3 默认站点[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/website_config_other/#3)

设置默认站点功能允许用户在未匹配到任何域名时，将请求自动定向到指定的默认网站。

![img.png](_txtdbpic/dc2251acb28e0e9eec88904946fbd7f2_MD5.png)

## 4 默认页面[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/website_config_other/#4)

设置默认页面功能允许用户修改以下部分默认页面的内容。

- **网站 404 错误页**
- **网站不存在页**
- **静态页面默认页**
- **PHP 网站默认页**
- **网站停用页**

![img.png](_txtdbpic/f8b500ebf812b925dd2cc9425015c5ab_MD5.png)

## 5 开启 / 停止网站[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/website_config_other/#5)

点击列表中的【已启动】或【已停止】按钮，可以切换网站的运行状态。

![img.png](_txtdbpic/899c5c1dbc71c816fec69f64060b20b6_MD5.png)

## 6 设置过期时间[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/website_config_other/#6)

设置网站过期时间后，系统将在到期时自动停止该站点，以确保资源的有效管理和使用。

![img.png](_txtdbpic/350806a2180acfa6537c9f0d13f25d31_MD5.png)

## 7 删除网站[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/website_config_other/#7)

在网站列表更多操作中，可以删除指定网站。

- **强制删除**：跳过删除过程中的错误，直接执行删除操作
- **删除应用**：可在删除网站时一并删除与之相关的 1Panel 应用
- **删除备份**：在删除网站的同时，也会删除其备份

![img.png](_txtdbpic/b3c9f13f42c4e41e87f83d0a80d0e29d_MD5.png)









# 网站分组

支持网站设置分组，以便于更好地组织和管理多个网站。

## 1 创建分组[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/website_group/#1)

![img.png](_txtdbpic/4e307da975a304c224c89f146c3dd80d_MD5.png)

## 2 默认分组[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/website_group/#2)

设置网站默认分组后，创建新网站时会自动将其归入该分组。

![img.png](_txtdbpic/710e50c1a2e3d3c1ba2242548e9e8f90_MD5.png)

## 3 修改/删除分组[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/website_group/#3)

![img.png](_txtdbpic/d615c5968a70086e16af1e5b69ac91c9_MD5.png)







# 网站备份

支持备份和恢复网站数据，以及导入现有备份，以确保网站内容的安全和易于管理。

## 1 创建备份[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/website_backup/#1)

点击网站列表【更多】操作中的【备份列表】选项后，系统将在默认备份目录下生成网站的备份文件。

![img.png](_txtdbpic/b5b2a3ae245312dfaed6ce3a9ea8f1ea_MD5.png)

## 2 网站恢复[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/website_backup/#2)

在备份列表中选择目标备份记录，然后点击【恢复】按钮以进行恢复操作。

![img.png](_txtdbpic/bbb88fbbd5634e80ee653668be2f303d_MD5.png)

## 3 备份下载[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/website_backup/#3)

支持将网站备份记录下载到本地，下载后可在上传备份页面使用该文件。

![img.png](_txtdbpic/9358ea8184d9b1728b4cb83f5fc7c50b_MD5.png)

## 4 导入备份[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/website_backup/#4)

选择网站备份文件并进行上传。

![img.png](_txtdbpic/425fb1a02e7d8a3b4c88b2748e83fb40_MD5.png)







# OpenResty 设置

网站列表上方的工具栏可用于查看和配置 OpenResty。

## 1 停止 / 启动 / 重启[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/openresty/#1)

可以通过按钮停止、启动或重启来管理 OpenResty 应用。

![img.png](_txtdbpic/945830c0f89235ba613e453a96d4382c_MD5.png)

## 2 重载[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/openresty/#2)

允许用户在无需停机的情况下快速应用配置更改，确保网站服务的高可用性。

![img.png](_txtdbpic/e6316a6aae94440bff74155017f5ce50_MD5.png)

## 3 设置[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/openresty/#3)

### 3.1 当前状态[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/openresty/#31)

查看当前网站状态，包括活动连接数、总连接数、总握手次数、总请求数、请求数、响应数及驻留进程等信息。

![img.png](_txtdbpic/c31b65f5c3965c6165b2cda73abfb4c6_MD5.png)

### 3.2 配置修改[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/openresty/#32)

- 配置 OpenResty 的配置文件
- 点击【默认配置】按钮可将配置文件恢复到默认状态

![img.png](_txtdbpic/d4cf915f9df58e5b5fddc61d9bfa3df6_MD5.png)

### 3.3 性能调整[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/openresty/#33)

调整 OpenResty 的相关配置参数。

![img.png](_txtdbpic/dbd6c7cb3a5fa1fe15a9e04e618e8423_MD5.png)

### 3.4 日志[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/openresty/#34)

查看 OpenResty 日志，支持实时追踪、下载、清空等操作，并可按指定时间段和行数筛选日志。

![img.png](_txtdbpic/3390b587f0e3f345dff2c821a1761114_MD5.png)

### 3.5 模块[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/openresty/#35)

管理 OpenResty 模块，包括：

- 查看已安装的模块列表
- 启用/禁用指定模块
- 创建、编辑、删除模块

模块配置发生变化后，需要点击【构建】按钮以应用配置，构建成功后会自动重启 OpenResty。

如果自定义构建模块，需要将模块的源码包放在 /opt/1panel/apps/openresty/openresty/build/tmp 目录下 (/opt 是 1Panel 的安装目录)
参数类似 --add-module=/tmp/nginx-rtmp-module （必须是 /tmp）
脚本参考 unzip -o /tmp/nginx-rtmp-module.zip -d /tmp （必须是 /tmp）

![img.png](_txtdbpic/a93be753ef5ce14e798d5a4c3df83501_MD5.png)







# 证书概述

管理证书相关，包括申请证书、续约证书、ACME 账户管理，DNS账户管理等。

![首页](_txtdbpic/d419ca5a1376aee914c9faf4341134b8_MD5.png)





# 申请证书

### 1 前置条件[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/certificate_create/#1)

- 已经创建 Acme 账户
- 如果是 DNS 验证模式，需要提前准备DNS账号

![img.png](_txtdbpic/f4b49a8e845e748eb3f9e936214bd3a2_MD5.png)

### 2 DNS 账号模式申请证书[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/certificate_create/#2-dns)

1. 选择 ACME 账号
2. 选择 DNS 账号
3. 选择是否自动续签
4. 点击确认

### 3 手动解析模式申请证书[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/certificate_create/#3)

1. 选择 ACME 账号
2. 点击确认
3. 等待返回解析内容，然后在 DNS 供应商解析处添加解析内容
4. 点击确认

### 4 HTTP 模式申请证书[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/certificate_create/#4-http)

1. 选择 ACME 账号
2. 选择是否自动续签
3. 点击确认





# 上传证书

## 1 Acme 账户管理[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/certificate_upload/#1-acme)

点击证书列表上方的【上传证书】按钮，用户可以将已有的 SSL 证书上传至 1Panel 中，用于网站的 HTTPS 访问。

![img.png](_txtdbpic/c666dff4cc3f52e6ffd94f8b9293ec88_MD5.png)

上传证书时，用户需要提供证书文件和私钥文件。证书文件和私钥文件需要使用 PEM 格式。

证书文件和私钥文件需要使用 PEM 格式。







# 自签证书

## 1 证书颁发机构[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/certificate_self_sign/#1)

点击证书列表上方的【自签证书】按钮，弹出自签证书管理页面。在该页面中可以创建并管理证书签发机构，用于签发自签证书。

1Panel 默认创建了名为 `1Panel` 的证书颁发机构，如果没有特殊要求，用户可以使用该颁发机构快速创建自签证书。

![img.png](_txtdbpic/2442564503843ac422a32d68bacef518_MD5.png)

## 2 签发证书[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/certificate_self_sign/#2)

在证书颁发机构列表中，点击【签发证书】按钮，弹出签发证书页面。在该页面中可以创建自签证书。

![img.png](_txtdbpic/7ecae158c51334da5f2a8323d4ecea59_MD5.png)







# 续签证书

DNS 账号、HTTP 方式申请的证书支持自动续签，1Panel 会自动在证书到期前进行续签操作。

用户也可以点击证书列表中的【申请】按钮，手动触发证书续签操作。

![img.png](_txtdbpic/190eff412f1fd1e1ed6de30704bb7d09_MD5.png)









# Acme 账户

点击证书列表上方的【Acme 账户】按钮，弹出 Acme 账户管理页面。在该页面中可以创建 Acme 账户或删除已有的 Acme 账户。

目前支持的账户类型有 Let's Encrypt 、 ZeroSSL 、 Buypass、Google Cloud 及自定义的 ACME 服务。

创建 Acme 账户时填写的邮箱可以用于接收证书相关通知。

![img.png](_txtdbpic/b44e13bbbc43917a71b1c3d8c040ea3c_MD5.png)







# DNS 账户

点击证书列表上方的【DNS 账户】按钮，弹出 DNS 账户管理页面。在该页面中可以创建、编辑或删除 DNS 账户。DNS 账户用于调用对应 DNS 服务商 API，自动添加 DNS 解析记录验证域名所有权。

目前支持的账户类型有：

- 阿里云
- 腾讯云
- 华为云
- GoDaddy
- Cloudflare
- Vercel
- CloudDNS
- NameSilo
- NameCheap
- Name.com
- FreeMyIP
- 雨云
- 西部数码
- ClouDNS
- Spaceship
- 火山引擎
- DNSPod（即将废弃）

![img.png](_txtdbpic/e26f56455d88da26a9e5385c930fb6be_MD5.png)

说明

关于不同类型 DNS 账户需要的认证信息如何获取，请查阅对应服务商的 API 文档获取支持。







# PHP

## 1 创建 PHP 运行环境[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/php/#1-php)

**点击创建运行环境按钮，选择 PHP 版本和扩展**

- 1Panel 支持维护 5.x、7.x 和 8.x 三个大版本，用户可以根据自己的需求选择合适的版本

![img.png](_txtdbpic/a891adebd6af6caaf6244de2d96e1df1_MD5.png)

### 1.1.创建 本地 PHP 运行环境[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/php/#11-php)

**点击创建运行环境按钮，选择本地**

- 需要先在服务器上安装 php-fpm。

![img.png](_txtdbpic/8b034915c1289a47d12d3e7964a76086_MD5.png)

**1Panel 离线版**

- 可以从其他 1Panel 服务器拷贝 /opt/1panel/runtime/php/[php_name] 目录和镜像，并上传到离线版 1Panel 服务器，并使用 docker compose up 命令启动，记住映射的端口
- 创建运行环境网站，选择刚刚创建的 PHP 运行环境，修改端口为刚才启动的端口

![img.png](_txtdbpic/5ea5ac671139d9ca87bba1fae55890b2_MD5.png)

## 2 管理 PHP 扩展[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/php/#2-php)

点击 PHP 运行环境列表中的【扩展】按钮，可以查看当前 PHP 运行环境已加载的扩展，同时支持安装、卸载扩展。

![img.png](_txtdbpic/380887feace8aea63f04f3a743ca32f5_MD5.png)

## 3 修改 PHP 配置[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/php/#3-php)

点击 PHP 运行环境列表中的【更多】操作中的【配置】选项，可以查看并修改当前 PHP 运行环境的配置。

![img.png](_txtdbpic/b0f470d3bfdae07504a3607b21bb69d1_MD5.png)

## 4 配置进程守护[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/php/#4)

点击 PHP 运行环境列表中的【更多】操作中的【进程守护】选项，可以查看并修改当前 PHP 运行环境的进程守护配置。

适用于 PHP 应用需要额外的常驻进程的场景。

![img.png](_txtdbpic/123c1a3259f3f621e8dd26273bcbec9d_MD5.png)

## 5 PHP 扩展列表[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/php/#5-php)

|   Extension    | PHP 5.5 | PHP 5.6 | PHP 7.0 | PHP 7.1 | PHP 7.2 | PHP 7.3 | PHP 7.4 | PHP 8.0 | PHP 8.1 | PHP 8.2 |
| :------------: | :-----: | :-----: | :-----: | :-----: | :-----: | :-----: | :-----: | :-----: | :-----: | :-----: |
|      amqp      |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|      apcu      |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|    apcu_bc     |         |         |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |         |         |         |
|      ast       |         |         |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|     bcmath     |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|   blackfire    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |         |
|      bz2       |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|    calendar    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|   cassandra    |         |         |         |         |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|     cmark      |         |         |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |         |         |         |
|      csv       |         |         |         |         |         |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|      dba       |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|    ddtrace     |         |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|    decimal     |         |         |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|       ds       |         |         |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|    enchant     |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|       ev       |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|     event      |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|    excimer     |         |         |         |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|      exif      |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|      ffi       |         |         |         |         |         |         |    ✓    |    ✓    |    ✓    |    ✓    |
|       gd       |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|    gearman     |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |         |         |
|     geoip      |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |         |         |         |
|      geos      |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |         |         |         |
|   geospatial   |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|    gettext     |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|    gmagick     |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|      gmp       |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|     gnupg      |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|      grpc      |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|      http      |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|    igbinary    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|    imagick     |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|      imap      |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|    inotify     |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|   interbase    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |         |         |         |         |
|      intl      |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|      ion       |         |         |         |         |         |         |         |         |    ✓    |    ✓    |
| ioncube_loader |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |         |    ✓    |         |
|     jsmin      |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |         |         |         |
|   json_post    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|      ldap      |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|   luasandbox   |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|      lz4       |         |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|      lzf       |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|   mailparse    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|   maxminddb    |         |         |         |         |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|     mcrypt     |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|    memcache    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|   memcached    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|    memprof     |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|     mongo      |    ✓    |    ✓    |         |         |         |         |         |         |         |         |
|    mongodb     |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|   mosquitto    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |         |         |         |
|    msgpack     |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|     mssql      |    ✓    |    ✓    |         |         |         |         |         |         |         |         |
|     mysql      |    ✓    |    ✓    |         |         |         |         |         |         |         |         |
|     mysqli     |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|     oauth      |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|      oci8      |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|      odbc      |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|    opcache     |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|   opencensus   |         |         |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|   openswoole   |         |         |         |         |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
| opentelemetry  |         |         |         |         |         |         |         |    ✓    |    ✓    |    ✓    |
|    parallel    |         |         |         |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|     parle      |         |         |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|     pcntl      |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|      pcov      |         |         |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|   pdo_dblib    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|  pdo_firebird  |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|   pdo_mysql    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|    pdo_oci     |         |         |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|    pdo_odbc    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|   pdo_pgsql    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|   pdo_sqlsrv   |         |         |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|     pgsql      |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|    php_trie    |         |         |         |         |         |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|     propro     |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |         |         |         |
|    protobuf    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|     pspell     |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|    pthreads    |    ✓    |    ✓    |    ✓    |         |         |         |         |         |         |         |
|     raphf      |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|    rdkafka     |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|     recode     |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |         |         |         |         |
|     redis      |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|     relay      |         |         |         |         |         |         |    ✓    |    ✓    |    ✓    |    ✓    |
|    seaslog     |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|     shmop      |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|    simdjson    |         |         |         |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|   smbclient    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|     snappy     |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|      snmp      |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
| snuffleupagus  |         |         |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|      soap      |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|    sockets     |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|     sodium     |         |    ✓    |    ✓    |    ✓    |         |         |         |         |         |         |
|      solr      |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
| sourceguardian |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|      spx       |         |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|     sqlsrv     |         |         |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|      ssh2      |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|     stomp      |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |         |         |    ✓    |
|     swoole     |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|   sybase_ct    |    ✓    |    ✓    |         |         |         |         |         |         |         |         |
|    sysvmsg     |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|    sysvsem     |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|    sysvshm     |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|     tensor     |         |         |         |         |    ✓    |    ✓    |    ✓    |    ✓    |         |         |
|      tidy      |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|   timezonedb   |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|      uopz      |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
| uploadprogress |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|      uuid      |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|      vips      |         |         |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|      wddx      |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |         |         |         |         |
|     xdebug     |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|     xdiff      |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|     xhprof     |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|   xlswriter    |         |         |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|    xmldiff     |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|     xmlrpc     |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|      xsl       |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|      yac       |         |         |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|      yaml      |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|      yar       |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |         |
| zephir_parser  |         |         |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|      zip       |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|      zmq       |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|   zookeeper    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |
|      zstd      |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |    ✓    |

*Number of supported extensions: 132*











# Node.js

## 1 创建 Node 运行环境[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/node/#1-node)

点击创建运行环境按钮，选择 Node 版本和源码目录。

目前支持 12.x、14.x 16.x 和 18.x 四个大版本，用户可以根据自己的需求选择合适的版本。

![runtime_node_create.png](_txtdbpic/701f0e31f1a761252f5e1209cd94daf7_MD5.png)

## 2 操作 Node 运行环境[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/node/#2-node)

在列表页面，可以查看 Node 运行环境安装的模块，对 Node 运行环境进行停止、启动、重启、编辑、删除、模块管理和查看日志等操作。

![runtime_node_list.png](_txtdbpic/3c4bdc5d12b927ce3ca29b00769d0af4_MD5.png)

## 3 日志查看[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/node/#3)

点击【查看】日志按钮，可以查看 Node 运行环境的运行日志。

![runtime_node_log.png](_txtdbpic/acf6d6dcd471ed1f7ce0717f0f63ea6f_MD5.png)

## 4 模块管理[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/node/#4)

点击模块按钮，可以对 Node 运行环境的模块进行管理。

![runtime_node_module.png](_txtdbpic/7281ce9b51f773356f364402e22aa3b9_MD5.png)







# Java

## 1 创建 Java 运行环境[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/java/#1-java)

点击创建运行环境按钮，选择 Java 版本和运行目录等信息。

- 目前支持 Java 1.8、11、17、18、21、22 大版本，用户可以根据自己的需求选择合适的版本

![runtime_java_create.png](_txtdbpic/56d4d17b7a55f2663da24434a7b5b072_MD5.png)

## 2 操作 Java 运行环境[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/java/#2-java)

- 在列表页面，可以对 Java 运行环境进行停止、启动、重启、编辑、删除和查看日志等操作

![runtime_java_list.png](_txtdbpic/1a338428488186a9efabcc06622ba7b7_MD5.png)

## 3 日志查看[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/java/#3)

点击【查看】日志按钮，可以查看 Java 运行环境的运行日志。

![runtime_java_log.png](_txtdbpic/9c3c01ae2a2beac214aa898cfd9d892d_MD5.png)







# Golang

## 1 创建 Golang 运行环境[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/golang/#1-golang)

点击创建运行环境按钮，选择 Golang 版本和运行目录等信息。 - 目前支持 Golang 1.21、1.22、1.23、1.24 版本，用户可以根据自己的需求选择合适的版本

![runtime_golang_create.png](_txtdbpic/322f8c25e5e08fa5d59e0f8e5a83cae4_MD5.png)

## 2 操作 Golang 运行环境[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/golang/#2-golang)

- 在列表页面，可以对 Golang 运行环境进行停止、启动、重启、编辑、删除和查看日志等操作

![runtime_golang_list.png](_txtdbpic/9e45ba7a48d4101eff92fddb934af112_MD5.png)







# Python

## 1 创建 Python 运行环境[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/python/#1-python)

点击创建运行环境按钮，选择 Python 版本和运行目录等信息。

- 目前支持 Python 3.10、3.11、3.12、3.13 版本，用户可以根据自己的需求选择合适的版本

![runtime_python_create.png](_txtdbpic/cfa54528e4d7a69960c0ba7eb15d9bc1_MD5.png)

## 2 操作 Python 运行环境[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/python/#2-python)

- 在列表页面，可以对 Python 运行环境进行停止、启动、重启、编辑、删除和查看日志等操作

![runtime_python_list.png](_txtdbpic/0dfb6d2943680143dcaddd5296361666_MD5.png)





# .NET

## 1 创建 .NET 运行环境[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/dotnet/#1-net)

点击创建运行环境按钮，选择 .NET 版本和运行目录等信息。

- 目前支持 .NET 9.0、8.0、6.0 版本，用户可以根据自己的需求选择合适的版本
- 目前使用的是 mcr.microsoft.com/dotnet/aspnet 镜像，需要先把代码编译成 .dll 文件，然后放到运行目录中

![runtime_net_create.png](_txtdbpic/082276c7b218f0b8b9f90ab7566e85dd_MD5.png)

## 2 操作 .NET 运行环境[⚓︎](https://1panel.cn/docs/v2/user_manual/websites/dotnet/#2-net)

- 在列表页面，可以对 .NET 运行环境进行停止、启动、重启、编辑、删除和查看日志等操作

![runtime_net_list.png](_txtdbpic/e1a63f0b5a2e1c9daae5bbabdaaafe80_MD5.png)







# 模型

## Ollama[⚓︎](https://1panel.cn/docs/v2/user_manual/ai/model/#ollama)

### 1 管理 Ollama 应用[⚓︎](https://1panel.cn/docs/v2/user_manual/ai/model/#1-ollama)

要使用模型管理功能，需要先在应用商店中安装 Ollama 应用。Ollama 安装完成后可以在该页面查看 Ollama 应用状态，并进行启动、停止及重启等操作。

![img.png](_txtdbpic/b894a3084f69c9ab9ed265c2a2cd9cfc_MD5.png)

### 2 添加模型[⚓︎](https://1panel.cn/docs/v2/user_manual/ai/model/#2)

点击添加模型，输入模型名称点击添加按钮即可从 [Ollama 官方仓库](https://ollama.com/search)拉取对应模型。

![img.png](_txtdbpic/173183c3f84db070916df5c0d83b231d_MD5.png)

### 3 运行模型[⚓︎](https://1panel.cn/docs/v2/user_manual/ai/model/#3)

点击某个模型所在行的【运行】操作，即可在当前页面打开在线终端与该模型进行对话。

![img.png](_txtdbpic/96dddac367f627635d4862eac7b65ae4_MD5.png)

### 4 AI 代理增强[⚓︎](https://1panel.cn/docs/v2/user_manual/ai/model/#4-ai)

通过该功能可以为 Ollama 应用配置反向代理，从而支持域名、HTTPS、IP 白名单等配置，增强使用大模型时的安全性。

![img.png](_txtdbpic/e5529f1bf82e5288da2f35b26f52e901_MD5.png)

### 5 查看连接信息[⚓︎](https://1panel.cn/docs/v2/user_manual/ai/model/#5)

点击列表上方的【连接信息】按钮，即可查看 Ollama 应用的连接信息。

![img.png](_txtdbpic/47733a9aa168f738313c96f03f6679d5_MD5.png)

> 应用商店部署的 Ollama 采用容器化方式运行，不同的场景需要根据页面提示选择对应的连接信息。

### 6 从服务器同步[⚓︎](https://1panel.cn/docs/v2/user_manual/ai/model/#6)

当使用了其他工具或应用程序添加了模型，模型列表信息与实际不一致时，可以点击列表上方的【从服务器同步】按钮，主动从 Ollama 查询当前模型列表。

### 7 WEB 管理工具[⚓︎](https://1panel.cn/docs/v2/user_manual/ai/model/#7-web)

如果需要使用 WEB 图形化界面管理并使用 Ollama 时，可以列表上方的【OpenWebUI】按钮，跳转到对应工具页面。

目前支持的管理工具有：

- [OpenWebUI](https://github.com/open-webui/open-webui)

## TensorRT LLM[⚓︎](https://1panel.cn/docs/v2/user_manual/ai/model/#tensorrt-llm)

TensorRT LLM 是 NVIDIA 推出的全面开源库，用于在 NVIDIA GPU 上加速和优化最新大语言模型（LLM）的推理性能。

### 0 前置条件[⚓︎](https://1panel.cn/docs/v2/user_manual/ai/model/#0)

在使用 TensorRT LLM 创建模型之前，需要先安装 NVIDIA 显卡驱动并安装配置 NVIDIA Container Toolkit。参考文档【[Installing the NVIDIA Container Toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html)】。

### 1 创建模型[⚓︎](https://1panel.cn/docs/v2/user_manual/ai/model/#1)

在 TensorRT LLM 模型管理页面，点击【创建】按钮，输入模型名称等参数后，点击【确认】按钮即可创建模型。

参数说明

- **名称**：模型名称。
- **容器名称**：TensorRT LLM 模型管理功能，会使用 TensorRT LLM 镜像启动一个容器来运行模型，容器名称需要唯一，默认使用模型名称。
- **镜像**：TensorRT LLM 镜像，默认使用 NVIDIA 官方镜像。
- **版本**：TensorRT LLM 镜像的镜像标签，对应不同的 TensorRT LLM 版本，可以查看 [NVIDIA TensorRT LLM 官方仓库](https://catalog.ngc.nvidia.com/orgs/nvidia/teams/tensorrt-llm/containers/release/tags) 获取可用版本。
- **模型目录**：选择服务器上的本地模型目录挂载到容器中，需要将模型文件夹提前放置在该目录中。
- **启动命令**：启动容器时执行运行模型的命令，默认使用 NVIDIA 官方启动命令，可以自定义启动命令。需要注意启动命令中的模型路径，1Panel 会将上一个参数的本地模型目录映射到容器的 /models 目录。如果选择的模型目录为最终的模型路径，例如 /home/DeepSeek-V3，那么启动命令中 `trtllm-server` 后直接跟 `/models` 即可；如果选择的模型目录为模型文件夹的父目录，例如最终模型路径为 /home/DeepSeek-V3，选择的模型目录参数为 /home，则启动命令中 `trtllm-server` 后需要跟 `/models/DeepSeek-V3` 路径。
- **端口**：配置 TensorRT LLM 容器的端口映射，可以将容器启动命令中的 8000 端口映射到服务器的 8000 端口，从而可以通过服务器 IP:8000 访问 TensorRT LLM 服务（需要勾选端口外部访问）。
- **环境变量**：为 TensorRT LLM 容器配置环境变量。
- **挂载**：为 TensorRT LLM 容器挂载额外的目录，可以挂载服务器上的本地目录到容器中，从而可以在容器中访问服务器上的本地目录。

![img.png](_txtdbpic/a9e9668bca494448689a5831c76db5c2_MD5.png)

### 2 查看模型日志[⚓︎](https://1panel.cn/docs/v2/user_manual/ai/model/#2_1)

在 TensorRT LLM 模型管理页面，点击模型所在行的【查看日志】按钮，即可查看模型启动及运行日志。

### 3 其他模型操作[⚓︎](https://1panel.cn/docs/v2/user_manual/ai/model/#3_1)

在 TensorRT LLM 模型管理页面，可以对模型进行停止、启动、重启、删除、编辑等操作。







# MCP

## 1 MCP Server 管理[⚓︎](https://1panel.cn/docs/v2/user_manual/ai/mcp/#1-mcp-server)

MCP（Model Context Protocol，模型上下文协议） 是由人工智能企业 Anthropic 推出的开放标准，旨在为大语言模型和 AI 助手提供统一、标准化的接口，让AI可以轻松操作外部工具，完成更加复杂的任务，从而发挥真正的“工具调用”能力。

然而在实际操作过程中，搭建 MCP Server 需要手动配置大量依赖，部署门槛较高，许多用户难以上手。为了解决这个问题，1Panel v1.10.29 LTS 版本推出了原生的 MCP Server 管理功能，该功能通过容器化方式实现一键部署 MCP Server，能够极大简化搭建流程。

![img.png](_txtdbpic/b272db28676f533e4a91ad14d29325c6_MD5.png)

## 2 创建 MCP Server[⚓︎](https://1panel.cn/docs/v2/user_manual/ai/mcp/#2-mcp-server)

当前已支持两种方式运行的 MCP Server 的 stdio 模式发布为 SSE 模式，供 MCP 客户端调用：

- 支持通过 npx 命令启动 MCP Server
- 支持以二进制方式运行 MCP Server（需将二进制文件挂载至容器中）

### 2.1 npx 命令启动[⚓︎](https://1panel.cn/docs/v2/user_manual/ai/mcp/#21-npx)

![img.png](_txtdbpic/213af5cc78221a4c4ed47cf3e40c2026_MD5.png)

### 2.2 二进制方式运行[⚓︎](https://1panel.cn/docs/v2/user_manual/ai/mcp/#22)

![img.png](_txtdbpic/1a89bf7b1004e60a570e09d89590958e_MD5.png)

## 3 获取配置信息[⚓︎](https://1panel.cn/docs/v2/user_manual/ai/mcp/#3)

MCP Server部署成功后，1Panel会为每个MCP Server实例自动生成客户端配置信息，包括端口、地址、SSE路径等。点击“配置”按钮，即可快速获取该MCP Server的客户端配置信息。 用户只需要复制客户端配置信息并粘贴至MCP客户端，即可开始使用拥有MCP加成的AI助手。这种方式无需手动查找或配置环境变量，实现了从部署到使用的无缝衔接。

![img.png](_txtdbpic/759f6159b83b5f83719fda30b300101e_MD5.png)

## 4 统一域名与SSE路径[⚓︎](https://1panel.cn/docs/v2/user_manual/ai/mcp/#4-sse)

1Panel 支持将多个 MCP Server 实例统一绑定至同一个网站域名，每个实例仅需设置不同的SSE路径进行区分。这意味着用户无需为每个 MCP Server 单独开放端口，所有服务都可以通过同一个端口对外提供服务。

这种方式不仅简化了公网访问的配置逻辑，也让运维操作更加集中统一。尤其是在大规模部署和企业内部网络的场景下，统一绑定网站域名能够避免暴露过多端口，减少安全风险，进一步提升部署的灵活性、安全性和可维护性。

![img.png](_txtdbpic/1f7b78610ad2fc20a2c0a528a2221b25_MD5.png)

## 5 白名单访问限制[⚓︎](https://1panel.cn/docs/v2/user_manual/ai/mcp/#5)

1Panel 支持为每个 MCP Server 网站配置IP访问白名单，以此有效保障 MCP Server 的数据安全。用户可以根据实际需求将 IP 地址或 IP 段添加至白名单，从而保证只有白名单中的 IP 能够访问 MCP Server 网站。与此同时，系统将自动拒绝所有不在白名单中的 IP 的访问请求。

通过为 MCP Server 网站配置 IP 访问白名单，可以有效隔离外部非授权访问，在网络入口层面建立起第一道安全防线。同时配合 1Panel 的防火墙策略和容器隔离机制，可以显著提升整体系统的安全性与稳定性。

## 6 HTTPS 数据加密[⚓︎](https://1panel.cn/docs/v2/user_manual/ai/mcp/#6-https)

1Panel 还支持为 MCP Server 网站启用HTTPS协议，用户只需要上传证书即可开启加密访问，全面保障上下文交互数据的安全性。







# GPU 监控

## 1 安装驱动[⚓︎](https://1panel.cn/docs/v2/user_manual/ai/gpu/#1)

针对 NVIDIA 显卡，用户可以在 https://www.nvidia.com/en-us/drivers/ 网站查找对应显卡型号支持的驱动版本，并进行下载安装。

例如下载到的文件为 `NVIDIA-Linux-x86_64-570.86.15.run`，将文件上传到 1Panel 服务器后，可以在命令行执行以下命令进行安装：

```
chmod +x NVIDIA-Linux-x86_64-570.86.15.run
./NVIDIA-Linux-x86_64-570.86.15.run
```

> 执行命令后根据弹出的提示框信息进行安装即可。 `nvidia-smi` 命令会随 NVIDIA 驱动一同安装，1Panel 将使用 `nvidia-smi` 命令获取显卡相关信息。

## 2 查看显卡信息[⚓︎](https://1panel.cn/docs/v2/user_manual/ai/gpu/#2)

在 GPU 监控页面，可以查看到驱动版本，显卡型号以及显卡的使用率、温度、功耗等基础指标，还可以查看到目前正在使用显卡的进程信息。

![img.png](_txtdbpic/bceeaa3eebbeb514845d3fcf44b130ea_MD5.png)

## 3 使用 GPU[⚓︎](https://1panel.cn/docs/v2/user_manual/ai/gpu/#3-gpu)

显卡驱动安装完成后，还需要根据 [NVIDIA 官网指引](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html)安装容器支持工具，才可以在应用商店应用或其他容器中使用 GPU 能力。

> 在应用商店安装应用时，勾选高级设置中的 `GPU 加速` 即可让该应用获得 GPU 支持。

![img.png](_txtdbpic/a9ac7d3c36a0b1d7a6cfd208d7fd9ce5_MD5.png)







# MySQL

## 1 管理数据库实例[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/mysql/#1)

### 1.1 应用商店安装数据库[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/mysql/#11)

通过应用商店安装的 MySQL、MariaDB 数据库应用，会自动出现在数据库实例列表中。

### 1.2 远程服务器[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/mysql/#12)

除应用商店安装的本地数据库以外，还可以添加已存在的数据库服务地址。点击列表上方的【远程服务器】按钮，即可进入远程服务器管理页面。

![img.png](_txtdbpic/ea700cedccd2f69403bc597ace410489_MD5.png)

![img.png](_txtdbpic/b5ee8f81c2d6626eae60dd77ab4956d1_MD5.png)

### 1.3 切换数据库实例[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/mysql/#13)

点击数据库列表上方的下拉菜单，即可在不同的数据库实例间进行切换，管理不同数据库实例下的数据库及设置等。

![img.png](_txtdbpic/c0fd9b1bfd8fc1118b8b331fa96f09f9_MD5.png)

## 2 创建数据库[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/mysql/#2)

创建一个新的数据库，首先输入数据库名称，选择编码格式，输入密码，设置访问权限，即可成功创建一个数据库。

![img.png](_txtdbpic/b9cbfa81bed3267c12f6a1c895c26186_MD5.png)

- 数据库名：新建数据库的名称，选择编码格式，默认为 UTF-8 格式
- 用户名：访问该数据库的用户名
- 密码：默认为随机密码，需要可以自行修改
- 访问权限：默认权限本地服务器权限，选项有:本地服务器，所有人，指定 IP

## 3 查看连接信息[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/mysql/#3)

点击列表上方的【连接信息】按钮，即可查看数据库的地址、端口及 root 密码等连接信息，同时可以在这里修改数据库 root 密码。

![img.png](_txtdbpic/230b37a9525d186a0747fd2059cff961_MD5.png)

注意

应用商店部署的数据库采用容器化方式运行，不同的场景需要根据页面提示选择对应的连接信息。

## 4 从服务器同步[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/mysql/#4)

当使用了其他数据库工具或应用程序操作了数据库，数据库列表信息与实际不一致时，可以点击列表上方的【从服务器同步】按钮，主动从数据库查询当前数据库列表。

## 5 WEB 管理工具[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/mysql/#5-web)

如果需要使用 WEB 图形化界面管理 MySQL 数据库，可以列表上方的【管理】按钮，跳转到对应工具页面。

目前支持的管理工具有：

- [phpMyAdmin](https://www.wpdaxue.com/series/phpmyadmin)
- Adminer

## 6 备份[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/mysql/#6)

点击备份列表按钮，选择备份，即可备份当前数据库文件。

![img.png](_txtdbpic/a6f54b6070d029ccaa366372c385505d_MD5.png)

- 默认数据库路径为 /opt/1panel/backup/database/mysql
- 备份使用 mysqldump 方式

## 7 恢复[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/mysql/#7)

点击导入备份按钮，可以选择本地上传，或选择已备份的文件还原。

![img.png](_txtdbpic/dcf21fc63a7da4d65416e1300ac83d71_MD5.png)

- 如从上传文件恢复，则需要保证上传文件压缩包内存在 test.sql 文件，否则无法正确导入
- 导入的 sql 文件格式必须符合标准，若你使用 phpmyadmin 导出的 sql 文件，可能会缺少版本 编码等信息，导致无法通过 mysqldump 正确导入
- 若无法正常导入，可以尝试使用 phpmyadmin 导入

## 8 权限设置[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/mysql/#8)

点击操作列的【权限】按钮，可以修改指定数据库的访问权限，目前支持配置为所有人可访问或指定 IP 可访问。

![img.png](_txtdbpic/4c61c6a0d4827142c260d247a09de219_MD5.png)

- 所有人：任何人都可以远程连接至数据库
- IP 地址：仅限指定的 IP 访问，多个 IP 使用英文逗号分隔
- 若需要开启外网访问，仍需要在防火墙中放行 MySQL 端口（默认3306）

## 9 修改密码[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/mysql/#9)

- 修改当前的数据库账号的密码
- **注意事项：** 当前修改的密码为非 root 密码

## 10 数据库配置[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/mysql/#10)

点击状态栏设置按钮，即可进入数据库具体设置界面，具体包括配置修改、当前状态、性能调整、端口、日志、慢日志。 其中配置界面可对数据库配置进行手动调整。

![img.png](_txtdbpic/f50fa8a691d6c9e4b524376eb37184fa_MD5.png)

- 系统 MySQL 使用 Docker 安装，配置文件默认挂载在 /opt/1panel/apps/mysql/[数据库名称]/conf/my.cnf
- **注意事项：** 错误的数据库配置将导致 MySQL 服务不可用，请谨慎修改
- 如数据库配置不正确导致服务无法正常启动，可尝试恢复默认配置后保存

## 11 当前状态[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/mysql/#11_1)

当数据库查询缓慢时，可在数据库设置界面，点击当前状态按钮，查看当前数据库包括缓存命中数、索引命中数等各个常用指标的状态，通过这些状态对数据库进行性能优化。

![img.png](_txtdbpic/87da6728bdb13c16dd7d6b53b84906d4_MD5.png)

## 12 性能调整[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/mysql/#12_1)

系统支持表单方式直接调整数据库性能相关参数名，如索引缓冲区、连接数等，并且预设常用的优化方案，用户可根据系统环境，直接选择优化方案。

![img.png](_txtdbpic/85d150b952a3d9e71e1f41f14896d029_MD5.png)

## 13 端口[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/mysql/#13_1)

除了在用户安装 MySQL 应用时可自由选择端口外，设置界面也可以直接进行端口的修改操作。

## 14 日志[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/mysql/#14)

- 系统 MySQL 使用 Docker 安装，本处产生日志为对应 MySQL 容器产生的日志。支持时间段筛选、追踪及下载操作
- 设置界面还支持查看 MySQL 产生的慢日志

![img.png](_txtdbpic/baa9adfbadad50b241360f7f114b3ef9_MD5.png)







# PostgreSQL

## 1 管理数据库实例[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/postgresql/#1)

### 1.1 应用商店安装数据库[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/postgresql/#11)

通过应用商店安装的 PostgreSQL 数据库应用，会自动出现在数据库实例列表中。

### 1.2 远程服务器[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/postgresql/#12)

除应用商店安装的本地数据库以外，还可以添加已存在的数据库服务地址。点击列表上方的【远程服务器】按钮，即可进入远程服务器管理页面。

![img.png](_txtdbpic/f87cdf81d2fa07c24201852abc5cdf6a_MD5.png)

![img.png](_txtdbpic/5353e59559c9a15dd72a7bcffeff19ef_MD5.png)

### 1.3 切换数据库实例[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/postgresql/#13)

点击数据库列表上方的下拉菜单，即可在不同的数据库实例间进行切换，管理不同数据库实例下的数据库及设置等。

![img.png](_txtdbpic/1727343675ef8d61f87e8bd2f3cd0da9_MD5.png)

## 2 创建数据库[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/postgresql/#2)

创建一个新的数据库，输入数据库名称、用户名、密码，设置访问权限，即可成功创建一个数据库。

![img.png](_txtdbpic/f6d432b36a46c872bf5dcc63473bb52d_MD5.png)

- 数据库名：新建数据库的名称
- 用户名：访问该数据库的用户名
- 密码：默认为随机密码，需要可以自行修改
- 访问权限：默认权限本地服务器权限，选项有:本地服务器，所有人，指定 IP

## 3 查看连接信息[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/postgresql/#3)

点击列表上方的【连接信息】按钮，即可查看数据库的地址、端口及管理员用户名和密码等连接信息，同时可以在这里修改管理员用户密码。

![img.png](_txtdbpic/aecbdf9b7365aaa13387bc05a9a4eff6_MD5.png)

注意

应用商店部署的数据库采用容器化方式运行，不同的场景需要根据页面提示选择对应的连接信息。

## 4 从服务器同步[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/postgresql/#4)

当使用了其他数据库工具或应用程序操作了数据库，数据库列表信息与实际不一致时，可以点击列表上方的【从服务器同步】按钮，主动从数据库查询当前数据库列表。

## 5 WEB 管理工具[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/postgresql/#5-web)

如果需要使用 WEB 图形化界面管理 PostgreSQL 数据库，可以列表上方的【PGAdmin4】按钮，跳转到对应工具页面。

## 6 备份[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/postgresql/#6)

点击备份列表按钮，选择备份，即可备份当前数据库文件。

![img.png](_txtdbpic/550a6e066f059f6a55b263dd77a05dc0_MD5.png)

- 默认数据库路径为 /opt/1panel/backup/database/postgresql
- 备份使用 pg_dump 方式

## 7 恢复[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/postgresql/#7)

点击导入备份按钮，可以选择本地上传，或选择已备份的文件还原。

![img.png](_txtdbpic/d03d7b32be395c39eaf9788cf5fdbf21_MD5.png)

- 如从上传文件恢复，则需要保证上传文件压缩包内存在 test.sql 文件，否则无法正确导入。

## 8 权限设置[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/postgresql/#8)

点击操作列的【权限】按钮，可以修改当前数据库绑定的用户是否为超级用户。

## 9 修改密码[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/postgresql/#9)

- 修改当前的数据库绑定用户的密码
- **注意事项：** 当前修改的密码为非默认管理员密码

## 10 数据库配置[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/postgresql/#10)

点击状态栏设置按钮，即可进入数据库具体设置界面，具体包括配置修改、端口、日志查看。 其中配置界面可对数据库配置进行手动调整。

![img.png](_txtdbpic/14272a895a2879081bec7af79070d58b_MD5.png)

- 系统 PostgreSQL 使用 Docker 安装，配置文件默认挂载在 /opt/1panel/apps/postgresql/[数据库名称]/data/postgresql.cnf
- **注意事项：** 错误的数据库配置将导致 PostgreSQL 服务不可用，请谨慎修改

## 11 端口[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/postgresql/#11_1)

除了在用户安装 PostgreSQL 应用时可自由选择端口外，设置界面也可以直接进行端口的修改操作。

## 12 日志[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/postgresql/#12_1)

- 系统 PostgreSQL 使用 Docker 安装，本处产生日志为对应 PostgreSQL 容器产生的日志。支持时间段筛选、追踪及下载操作

![img.png](_txtdbpic/01fbc138a916ec021754afccd4d4e019_MD5.png)







# Redis

## 1 修改密码[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/redis/#1)

默认为随机密码，root 为最高权限账号密码，请谨慎操作。

## 2 Redis Commander[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/redis/#2-redis-commander)

WEB 图形化界面管理 redis 数据库的管理工具，工具使用方法详解见[工具教程](http://joeferner.github.io/redis-commander/)

## 3 数据库配置[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/redis/#3)

点击状态栏设置按钮，即可进入 Redis 具体设置界面，具体包括配置修改、当前状态、性能调整、端口、持久化。 其中配置界面可对 Redis 配置进行手动调整。

![img.png](_txtdbpic/5537731c03b6a146640984478c87ebef_MD5.png)

- 系统 Redis 使用 Docker 安装，配置文件默认挂载在 /opt/1panel/apps/redis/[数据库名称]/conf/redis.conf

**注意事项：** 错误的数据库配置将导致 Redis 服务不可用，请谨慎修改。如数据库配置不正确导致服务无法正常启动，可尝试恢复默认配置后保存。

## 4 当前状态[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/redis/#4)

当 Redis 查询缓慢时，可在设置界面，点击当前状态按钮，查看当前数据库包括内存分配、查询命中率等各个常用指标的状态，通过这些状态对 Redis 进行性能优化。

![img.png](_txtdbpic/36deaaa382782382599bd72f82b2aed4_MD5.png)

## 5 性能调整[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/redis/#5)

系统支持表单方式直接调整 Redis 相关参数，具体包括：超时时间、最大连接数、最大内存数。

![img.png](_txtdbpic/85de7d3cae793de57d2e43999de8dfd0_MD5.png)

## 6 端口[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/redis/#6)

除了在用户安装 Redis 应用时可自由选择端口外，设置界面也可以直接进行端口的修改操作。

## 7 持久化[⚓︎](https://1panel.cn/docs/v2/user_manual/databases/redis/#7)

Redis 持久化分为两种：AOF 及 RDB，其中：

- RBD
  - 实现： 父进程在保存 RDB 文件时，先 fork 出来一个子进程，然后子进程处理接下来的保存工作，父进程无需执行任何磁盘 I/O 操作
  - 优点： 将 Redis 在某个时间点上的数据集保存在一个文件中，适用于灾难恢复，可以最大化 Redis 性能，速度更快，并且在恢复大数据集时速度更快
  - 缺点： 有丢失数据的风险，需要设置备份频率，一旦发生故障停机时，可能会丢失数据，而且当数据集比较大时，fork 子进程将会非常耗时造成服务停止
- AOF
  - 实现： 定时或者在每次写入命令时追加操作到日志文件中，日志文件只进行追加操作，当 AOF 文件变的过大时，自动对 AOF 进行重写，重写仅保留恢复当前数据集所需的最小命令集合
  - 优点： 有序保存了对数据库执行的所有写入操作，数据不容易丢失，即使发生故障停机，也只会丢失上一次写入日志文件操作之后的数据，更可靠且更容易对文件进行分析
  - 缺点： 一般相同的数据集来说，AOF 体积要更大，而且速度可能会慢于 RDB

![img.png](_txtdbpic/4ee1a80be7dafe14691be9834e19af76_MD5.png)

- appendonly: 是否开启 AOF 备份
- appendfsync: 同步频率
  - always: 每次写入时
  - everysec: 每秒
  - no: 不同步

![img.png](_txtdbpic/ed123507880b178b406825ad50ce1e07_MD5.png)

- 设置持久化策略，当 Redis 满足其中任意一个条件时，将触发 RDB 持久化。









# 概览

在容器概览页面可以查看到当前服务器上容器服务的整体状态，包括容器、编排、镜像、网络、存储卷等数量信息，及容器服务基础配置信息等。

![img.png](_txtdbpic/6e45c709c18198b565809de125a11c30_MD5.png)







# 容器

## 1 添加容器[⚓︎](https://1panel.cn/docs/v2/user_manual/containers/container/#1)

- 从菜单中选择【容器】，然后单击【创建容器】
- 根据需要配置容器设置
- 镜像需要从镜像镜像菜单手动拉取

![img.png](_txtdbpic/68757e36e4b324ba573d50fdcbea6e17_MD5.png)

## 2 检查容器[⚓︎](https://1panel.cn/docs/v2/user_manual/containers/container/#2)

点击目标容器名称，有关容器的所有信息都将显示在右侧抽屉中。

![img.png](_txtdbpic/504c7ed197209f8cf164fbfb400e5169_MD5.png)

## 3 查看容器日志[⚓︎](https://1panel.cn/docs/v2/user_manual/containers/container/#3)

- 支持查看最近一天，最近 4 小时，最近 1 小时，最近 10 分钟的容器日志
- **追踪：** 实时刷新容器日志
- **下载：** 下载容器日志

![img.png](_txtdbpic/e8cd5ca3c2f9fc13da7676e389789a71_MD5.png)

## 4 访问容器的控制台[⚓︎](https://1panel.cn/docs/v2/user_manual/containers/container/#4)

- 选择要授予访问权限的命令和用户，然后单击【连接】

**注意：** 对于 Alpine Linux 容器，选择 /bin/ash 命令。如果需要定义除提供的命令之外的命令，请将 **自定义** 选项切换为打开。

![img.png](_txtdbpic/dec5aa9c43f86d556f28da3f51c07636_MD5.png)

## 5 查看容器统计信息[⚓︎](https://1panel.cn/docs/v2/user_manual/containers/container/#5)

支持查看的信息包括：

- 内存使用率
- CPU 使用率
- 磁盘 IO 使用情况
- 网络使用情况

**可以更改刷新间隔**。

![img.png](_txtdbpic/c2d96572e6ad66a948d226daf8a6ba86_MD5.png)







# 编排

## 1 创建编排[⚓︎](https://1panel.cn/docs/v2/user_manual/containers/compose/#1)

提供三种方法可以从 1Panel 部署新 Compose

- 编辑： 使用 Web 编辑器定义服务
- 路径选择： 选择 1Panel 服务中已存在的 docker-compose.yml
- 编排模版： 选择已存在的编排模版

[了解更多容器编排相关的知识](https://docs.docker.com/compose)

![img.png](_txtdbpic/093c22d79c6c639fcce22e1c0bd6e149_MD5.png)

## 2 编辑编排[⚓︎](https://1panel.cn/docs/v2/user_manual/containers/compose/#2)

Compose 按照来源可以区分为三种：

- Apps: 来源于应用商店应用部署
- 1Panel: 来源于系统编排创建
- Local: 服务器直接创建

**编辑仅适用于 1Panel 部署的 Compose**

## 3 编排详情[⚓︎](https://1panel.cn/docs/v2/user_manual/containers/compose/#3)

点击编排列表名称，进入编排详情界面，详情界面实现该 Compose 对应的容器列表，仅当该 Compose 为 1Panel 创建时，支持对 Compose 进行启停操作。

![img.png](_txtdbpic/9bf4a0b36ed3b6b0cd7de3eb88b6fdad_MD5.png)







# 镜像

## 1 拉取镜像[⚓︎](https://1panel.cn/docs/v2/user_manual/containers/image/#1)

- 支持从已添加的镜像仓库中拉取，等价于 docker pull 操作
- 拉取镜像将耗费一段时间，如果关闭抽屉后还想查看拉取日志，则可以去【主机 - 文件】中，下载或查看 [安装目录]/1panel/tmp/docker_logs/image_pull_[时间戳].log

## 2 导入镜像[⚓︎](https://1panel.cn/docs/v2/user_manual/containers/image/#2)

- 选择 1Panel 服务器上已导出的镜像文件，等价于 docker load 操作

## 3 构建镜像[⚓︎](https://1panel.cn/docs/v2/user_manual/containers/image/#3)

- 直接构建镜像，等价于 docker build 操作
- 构建镜像将耗费一段时间，如果关闭抽屉后还想查看构建日志，则可以去【主机 - 文件】中，下载或查看 [安装目录]/1panel/tmp/docker_logs/image_build_[时间戳].log

![img.png](_txtdbpic/d2854364a0b23aecff5e0de88320138b_MD5.png)

- 编辑： 使用 Web 编辑器编辑 Dockerfile
- 路径选择： 选择 1Panel 服务中已存在的 Dockerfile

## 4 Tag 镜像[⚓︎](https://1panel.cn/docs/v2/user_manual/containers/image/#4-tag)

- Tag 镜像，等价于 docker tag 操作

## 5 推送镜像[⚓︎](https://1panel.cn/docs/v2/user_manual/containers/image/#5)

- 将镜像推送到镜像仓库，推送过程中，后台将自动修改对应的镜像 Tag，等价于 docker tag + docker push 操作

## 6 导出镜像[⚓︎](https://1panel.cn/docs/v2/user_manual/containers/image/#6)

- 将镜像导出为 .tar 文件，等价于 docker save，当需要进行复制或者移动镜像时，可直接在系统执行导入导出操作





# 网络

1Panel 允许在环境中添加、删除网络，其中 none、host、bridge、1panel-network 四个网络为系统自带网络，无法删除。

[了解更多容器网络相关的知识](https://docs.docker.com/network)

![img.png](_txtdbpic/decc2add0233d0ab4b9b0e36b87c3347_MD5.png)

**模式：Docker中的网络驱动（network driver）是可插拔的，1Panel 提供几种网络驱动以提供核心的网络功能，包括：**

- bridge: docker 默认的 network driver。如果不显示指定 driver 类型，docker 默认会使用 bridge模式的 network。通常，当应用程序运行在独立的容器中，并且要相互通信，可以使用 bridge 模式。Bridge 模式下容器与 docker host 的网络是相互隔离的
- ipvlan: IPvlan 驱动程序让用户完全控制 IPv4 和 IPv6 寻址。VLAN 驱动程序建立在此基础上，为操作员提供对二层 VLAN 标记的完全控制，甚至对底层网络集成感兴趣的用户提供 IPvlan L3 路由
- macvlan: macvlan network 能够给容器分配一个 MAC地址，使的此容器就像一个此网络上的物理设备。Docker Daemon可以通过MAC地址给容器路由消息。对于一些遗留的应用需要直接连接到物理网络而不是通过 docker host 的网络栈转发时， macvlan 驱动是最好的选择
- overlay: Overlay network能够连通不同的 docker daemon，能够使 swarm service之间能够相互通信。Overlay network 也能够使 swarm service 与独立的容器连通, 能够使位于不同 Docker daemon上的独立的容器连通。Overlay 模式省去了容器之间操作系统层级的路由工作





# 存储卷

Volume 是一个数据存储区域，可以挂载到容器中以提供持久存储。

[了解更多容器存储相关的知识](https://docs.docker.com/storage/volumes)

![img.png](_txtdbpic/8afaac063fa2407076f9c67c91182e1d_MD5.png)







# 仓库

- 仓库存在认证信息时，后端会自动执行 docker login 操作
- 添加 http 协议仓库后，会自动在配置文件中添加该仓库的授信信息，需要重启 Docker 服务

![img.png](_txtdbpic/5be4c61409b97dd05afcb4ac17138269_MD5.png)







# 编排模版

供创建编排时使用。

![img.png](_txtdbpic/d8bcc7d5448be8e913f1f089ec69c863_MD5.png)







# 配置

## 1 配置[⚓︎](https://1panel.cn/docs/v2/user_manual/containers/setting/#1)

- 支持查看 Docker 运行状态，并执行重启服务等操作
- 配置文件默认为：/etc/docker/daemon.json

![img.png](_txtdbpic/ca30101ad88658945334ebd221fe497a_MD5.png)

- 镜像加速：应用安装失败，镜像拉取超时，此时可以配置镜像加速器进行优化

  - 配置加速地址：

    ```
    https://docker.1panel.live
    ```

    > 配置了上述加速地址后，如果拉取应用镜像仍然失败，[可以在论坛中进一步讨论](https://bbs.fit2cloud.com/t/topic/5886)

- 私有仓库：搭建的私有镜像仓库，如 harber、nexus、docker-registry 等

- iptables：该设置将关闭 Docker 对 iptables 规则的自动配置，这可能会导致容器无法与外部网络通信

- live-restore：停止 Docker 服务是，是否停止所有容器

- cgroup-driver：默认情况下使用的 Cgroup Driver 为 cgroupfs

## 2 使用 IPv6[⚓︎](https://1panel.cn/docs/v2/user_manual/containers/setting/#2-ipv6)

- 确保自己的设备被分配了一个 IPv6。通过 ip addr show 查看当前设备的 IPv6。其输出的物理网卡存在包含 inet6 和 scope global 的行时，表示该网卡支持 IPv6

  ```
  eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
      link/ether 00:16:xx:xx:xx:xx brd ff:ff:ff:ff:ff:ff
      inet 172.31.168.107/20 brd 172.31.175.255 scope global dynamic eth0
          valid_lft 314955046sec preferred_lft 314955046sec
      inet6 2xxx:xxxx:xxxxx:xxxx:xxxx:xxxx:xxxx:xxxx/64 scope global dynamic 
          valid_lft 113120sec preferred_lft 69920sec
      inet6 fe80::xxxx:xxxx:xxxx:xxxx/64 scope link 
          valid_lft forever preferred_lft forever
  ```

  

- 面板设置中开启 IPv6，其中 fixed-cidr-v6 是上一步获取到的 IPv6 网段的子网（配置默认网络，前缀长度最大为 /80）![img.png](_txtdbpic/a63d191ffd37ccc53f1aa50104487d34_MD5.png)

- 通过【网络】-【详情】检查是否生效。若生效，则 EnableIPv6 值为 true，IPAM.Config[1].Subnet 是上一步配置的 fixed-cidr-v6![img.png](_txtdbpic/8eb8de9443ed88827e76cbeb5218fdd7_MD5.png)

- 创建 IPv6 网络![img.png](_txtdbpic/54eaf0811b76488a3db794d66bfaef9f_MD5.png)

- 使用创建的 IPv6 网络创建容器





# 文件

## 1 文件操作[⚓︎](https://1panel.cn/docs/v2/user_manual/hosts/file/#1)

文件管理实现了很多实用的文件操作，除了基本的剪切、复制、粘贴、删除操作，还支持上传和下载文件、解压和解压、加密和解密、批量操作。

## 2 修改权限[⚓︎](https://1panel.cn/docs/v2/user_manual/hosts/file/#2)

点击文件列表“权限”列中的值（类似 0755、0644），可对文件的权限进行修改。

Linux 中文件权限可按照以下三个不用角色分别进行设置：

- 文件所有者
- 所属用户组
- 其它用户

在修改权限的窗口中，可直接勾选不同角色所具备的权限，下方的权限代码会随之自动变化。

如果你要修改的是目录的权限，勾选“同时修改子目录权限”后，目录中的所有文件和目录的权限也都会发生变化。

## 3 上传文件[⚓︎](https://1panel.cn/docs/v2/user_manual/hosts/file/#3)

点击工具栏中的“上传”按钮，可将本地电脑的文件上传到服务器上。

## 4 在线下载文件[⚓︎](https://1panel.cn/docs/v2/user_manual/hosts/file/#4)

如果想从其它服务器上下载文件到当前服务器上，可点击工具栏上的【在线下载】按钮进行操作。

## 5 下载文件[⚓︎](https://1panel.cn/docs/v2/user_manual/hosts/file/#5)

如果需要将服务器上的文件下载到本地，点击文件右侧下拉菜单中的【下载】即可。

## 6 压缩和解压[⚓︎](https://1panel.cn/docs/v2/user_manual/hosts/file/#6)

文件管理支持多种格式的压缩和解压，默认压缩格式为 .tar.gz，为 Linux 下最为常见的打包压缩格式。







# 监控

## 1 查看监控[⚓︎](https://1panel.cn/docs/v2/user_manual/hosts/monitor/#1)

点击【主机 - 监控】菜单，进入监控报表，直观的了解服务器的运行状态，包含【平均负载】、【CPU性能监控】、【内存使用监控】、【磁盘IO监控】、【网络IO监控】。

通过时间监控指标上方的时间选择组件，可以调整监控数据的时间范围。

![img.png](_txtdbpic/46bcd44f78118e9043c060f1549e54cd_MD5.png)

## 2 修改设置[⚓︎](https://1panel.cn/docs/v2/user_manual/hosts/monitor/#2)

在监控设置页面，可以开启/关闭监控功能，修改监控数据的保存时长，修改监控数据的采集间隔，或者手动清空监控记录。







# 防火墙

**1Panel 集成了两种广泛使用的 Linux 防火墙软件：Firewalld 和 UFW。**

- RedHat/CentOS 使用的是 Firewall 防火墙
- Debian/Ubuntu使用的是 UFW 防火墙

## 1 安装[⚓︎](https://1panel.cn/docs/v2/user_manual/hosts/firewall/#1)

[RedHat / CentOS](https://1panel.cn/docs/v2/user_manual/hosts/firewall/#__tabbed_1_1)[Ubuntu / Debian](https://1panel.cn/docs/v2/user_manual/hosts/firewall/#__tabbed_1_2)

**1、更新软件包**

```
sudo yum update
```

**2、安装 firewalld**

```
sudo yum install firewalld
```

**3、启动 firewalld**

```
sudo systemctl start firewalld
```

**4、如果你在远程位置连接你的服务器，在启用 firewalld 防火墙之前，你必须显式允许进来的 SSH 连接。否则，你将永远都无法连接到机器上。**

```
sudo firewall-cmd --zone=public --add-port=22/tcp --permanent
```

> 如果 SSH 运行在非标准端口，你需要将上述命令中的 22 端口替换为对应的 SSH 端口。

**5、放开 1Panel 系统端口。**

```
sudo firewall-cmd --zone=public --add-port=8090/tcp --permanent
```

> 上述命令中的 8090 端口需要替换为安装 1Panel 系统时自定义的端口。

**6、重新加载防火墙规则，使更改生效**

```
sudo firewall-cmd --reload
```

**7、设置开机启动 firewalld**

```
sudo systemctl enable firewalld
```

## 2 防火墙状态[⚓︎](https://1panel.cn/docs/v2/user_manual/hosts/firewall/#2)

**点击防火墙开关按钮，即可开启或关闭防火墙。**

![img.png](_txtdbpic/f2c804e4cc6876f0ea62050219b65677_MD5.png)

**点击禁 ping 按钮，即可开启或关闭 PING 命令。**

- 禁用 PING 命令的主要功能是：为了防止用户频繁 PING 服务器而导致服务器性能下降

![img.png](_txtdbpic/3e3cef3038f8685f626303659b2466ab_MD5.png)

## 3 端口规则[⚓︎](https://1panel.cn/docs/v2/user_manual/hosts/firewall/#3)

**点击创建端口规则按钮，即可设置端口规则。**

- 协议：默认为 TCP 协议，有 TCP、UDP、TCP/UDP 协议，根据你的实际情况选择
- 端口：输入你要设置规则的端口，自定义，端口范围是：0-65535
- 来源：默认为所有 IP，选择有：所有 IP、指定 IP
- 策略：默认为允许，有允许、拒绝

**端口放行成功后，可以查看防火墙列表查看当前端口的运行情况。**

![img.png](_txtdbpic/5ba0da1b263a9ee5002e63c4db032348_MD5.png)

![img.png](_txtdbpic/e8e8f8e1aa2e67f067f86c30f6899741_MD5.png)

## 4 端口转发[⚓︎](https://1panel.cn/docs/v2/user_manual/hosts/firewall/#4)

**点击创建端口转发按钮，即可设置端口转发规则。**

- 协议：默认为 TCP 协议，有 TCP、UDP、TCP/UDP 协议，根据你的实际情况选择
- 源端口：发送至源端口的报文，将被转发至 `目标 IP:目标端口`，端口范围是：0-65535
- 目标 IP：如果是本机端口转发，目标IP为：127.0.0.1；如果目标IP不填写，则默认为本机端口转发
- 目标端口：接收转发报文的目标端口

![img.png](_txtdbpic/09ab3f14dde78df41b1628f7157cbc4d_MD5.png)

## 5 IP 规则[⚓︎](https://1panel.cn/docs/v2/user_manual/hosts/firewall/#5-ip)

**点击创建 IP 规则按钮，即可设置IP规则**

- 指定 IP
- 策略：默认为放行，有放行、屏蔽

![img.png](_txtdbpic/44e9fc7029ba482caffcd1dc465d68df_MD5.png)

![img.png](_txtdbpic/a7b0f8968c1cef109d977977c7d795cb_MD5.png)







# 进程管理

## 1 查看进程[⚓︎](https://1panel.cn/docs/v2/user_manual/hosts/process/#1)

点击【主机 - 进程管理】菜单，进入进程管理页面。

- 在列表中可以查看系统中的所有进程信息
- 列表上方筛选组件可以根据进程 ID、进程名称、用户等信息对进程进行筛选
- 列表中可以根据 PID、父进程 ID、CPU 使用率、内存使用率进行排序，根据进程状态进行筛选
- 点击操作列的 `详情`，可以查看进程的更多信息，包括基本信息、内存信息、打开的文件、环境变量及网络连接信息等
- 点击操作列的 `结束`，可以结束掉指定进程

![img.png](_txtdbpic/28e0d055f99917c625777efd9c03cda0_MD5.png)

## 2 查看网络连接信息[⚓︎](https://1panel.cn/docs/v2/user_manual/hosts/process/#2)

点击当前页面上方的 `网络` 选项，可以进入网络连接列表。

- 在列表中可以查看系统中的所有网络连接及端口使用信息
- 列表上方筛选组件可以更具进程 ID、进程名称、端口号进行筛选
- 列表中可以根据 PID 进行排序，根据连接状态进行筛选

![img.png](_txtdbpic/7fe17d451153aebd5e0e94761bb14915_MD5.png)







# SSH 管理

## 1 配置 SSH 服务[⚓︎](https://1panel.cn/docs/v2/user_manual/hosts/ssh/#1-ssh)

在 SSH 管理配置页面，可以开启/关闭/重启 SSH 服务，设置 SSH 服务开机自启动，同时支持可视化调整监听端口、监听地址等常用配置，或者通过配置文件方式修改其他配置。

![img.png](_txtdbpic/134794da110bd3ace21e09bd7a9df358_MD5.png)

## 2 管理 SSH 会话[⚓︎](https://1panel.cn/docs/v2/user_manual/hosts/ssh/#2-ssh)

点击当前页面上方的 `会话` 选项，可以进入 SSH 会话列表。

- 在列表中可以查看系统中的所有活跃的 SSH 会话信息
- 点击操作列的 `断开`，可以断开指定的 SSH 会话

![img.png](_txtdbpic/89a055792a25088f070494dbc7e63d24_MD5.png)

## 3 查看 SSH 登录日志[⚓︎](https://1panel.cn/docs/v2/user_manual/hosts/ssh/#3-ssh)

点击当前页面上方的 `登录日志` 选项，可以进入 SSH 登录日志列表。

![img.png](_txtdbpic/015505d003f9451cdc7e14d6cea156dd_MD5.png)







# 计划任务

主要用于管理需要定时执行的任务，如定期执行某 shell 脚本、定期备份、定期访问 URL 等，同时支持手动执行。

基础概念：

- 任务类型：支持 Shell 脚本、备份应用、备份网站、备份数据库、备份目录 / 文件、备份日志、访问 URL、切割网站日志、缓存清理、系统快照、同步服务器时间；
- 分组：将不同的计划任务设置为不同的分组，便于计划任务的快速筛选；
- 执行周期：自定义执行周期仅支持【 分 时 日 月 周 】格式，如 0 0 * * * ，可参考 https://crontab.guru/ 修改执行周期。选择或输入完执行周期后，可以点击行末预览查看最近 5 次执行时间；
- 保留份数：为防止备份或者日志的无限制增加，可设置保留份数保留最新成功的 n 份；
- 备份账号：需要将备份文件上传的位置，在 [面板设置 - 备份账号] 中维护，支持多选，可同时备份到多个备份账号；
- 默认下载地址：备份账号中需要设置一个固定的备份账号提供下载和获取文件大小操作，当该备份账号上传失败时，任务将失败，而非默认下载地址的其他备份账号上传失败时，会被忽略并继续；
- 压缩密码：应用备份或者网站备份使用 tar 进行压缩，支持设置压缩密码，压缩加密使用 openssl，默认为不设置密码；
- 排除规则：备份过程中，可设置特定的文件排除规则，忽略不希望加入备份压缩的目录；
- 是否告警（✨专业版）： 定时任务执行失败时可以触发告警通知，当前支持短信及邮箱告警；
- 忽略错误：当任务中需要备份多个内容时，如备份所有数据库或应用，执行过程中出现错误是否需要忽略并且继续备份其他内容；
- 超时时间：任务的执行超时时间；
- 失败重试次数：失败后重试次数设置；

## 1 任务类型[⚓︎](https://1panel.cn/docs/v2/user_manual/cronjobs/#1)

### 1.1 Shell 脚本[⚓︎](https://1panel.cn/docs/v2/user_manual/cronjobs/#11-shell)

配置说明

- 在容器中执行：勾选后可以选择某个容器，在容器中执行指定的脚本，支持选择容器用户及命令执行器；
- 解释器：选择不同的解释器执行脚本内容，系统预设 bash python sh，支持自定义；
- 脚本内容：具体需要执行的脚本内容，支持编辑、选择脚本库以及选择服务器脚本执行；

![img.png](_txtdbpic/23f0d6d3f0a84666e927f25fd151476c_MD5.png)

### 2 备份应用 | 备份网站 ｜ 备份数据库[⚓︎](https://1panel.cn/docs/v2/user_manual/cronjobs/#2)

配置说明

备份应用、备份网站备份数据库大体相同，直接选择对应的备份内容，支持备份所有。

![img.png](_txtdbpic/2f87d338abfd2e3f6884444dec1bd977_MD5.png)

### 3 备份目录[⚓︎](https://1panel.cn/docs/v2/user_manual/cronjobs/#3)

配置说明

备份文件或目录，支持直接选择需要备份的多个文件，或者指定单个目录。

![img.png](_txtdbpic/d73b093e6508442609030c26b5a29a4a_MD5.png)

### 4 备份日志[⚓︎](https://1panel.cn/docs/v2/user_manual/cronjobs/#4)

备份以下日志内容：

- 1Panel 系统日志；
- 服务器的 SSH 登录日志；
- 所有网站日志；

### 5 访问 URL[⚓︎](https://1panel.cn/docs/v2/user_manual/cronjobs/#5-url)

URL 地址：需要定时访问的 URL 地址；

### 6 切割网站日志[⚓︎](https://1panel.cn/docs/v2/user_manual/cronjobs/#6)

计划任务执行时会将指定网站的日志进行切割，将之前产生的日志保存在备份目录下。

### 7 缓存清理[⚓︎](https://1panel.cn/docs/v2/user_manual/cronjobs/#7)

定时执行面板 `工具箱` 菜单中的 `缓存清理` 任务。

### 8 系统快照[⚓︎](https://1panel.cn/docs/v2/user_manual/cronjobs/#8)

定时执行面板 `面本设置`-`快照` 菜单中的 `创建快照` 任务。

### 9 同步服务器时间[⚓︎](https://1panel.cn/docs/v2/user_manual/cronjobs/#9)

定时从 `工具箱`-`快速设置` 页面配置的 NTP 服务器进行时间同步。

## 执行报告[⚓︎](https://1panel.cn/docs/v2/user_manual/cronjobs/#_1)

### 下载与查看[⚓︎](https://1panel.cn/docs/v2/user_manual/cronjobs/#_2)

备份类型的计划任务，可在计划任务列表直接查看备份文件份数，并支持下载操作。

![img.png](_txtdbpic/74e363f71a18c4fab9ccac90cec9a9dd_MD5.png)

显示该任务产生的所有报告详情，支持时间、状态筛选。

![img.png](_txtdbpic/03bcad02f4a562f40db17feff20a9ee4_MD5.png)

## 导入导出[⚓︎](https://1panel.cn/docs/v2/user_manual/cronjobs/#_3)

计划任务支持通过 json 文件一键导入或导出操作，导入计划任务时，如果存在相关内容关联异常的情况将修改计划任务状态为待编辑，如果导入计划任务名称已存在将被忽略。









# 终端

## 1 终端管理[⚓︎](https://1panel.cn/docs/v2/user_manual/terminal/#1)

点击【主机 - 终端】菜单，进入终端页面，终端默认连接本地服务器，如未填写本地服务器登录信息，则连接失败。

- 支持直接选择已有主机连接（【终端 - 主机】菜单中维护）和连接新主机
- 支持重新连接
- 支持打开多个本地服务器
- 支持全屏操作
- 支持快速快速命令（需要在【终端 - 快速命令】菜单中维护），用户可预定于常用快速命令
- 支持当前所有连接批量输入

![img.png](_txtdbpic/d35b190d6f39cd3b2ba0b0be9096fd3d_MD5.png)

## 2 主机管理[⚓︎](https://1panel.cn/docs/v2/user_manual/terminal/#2)

维护主机信息，支持主机分组。

![img.png](_txtdbpic/0d2769d0ed96305731529d5b7d50924a_MD5.png)







# 快速设置

在 `工具箱`-`快速设置` 页面，可以对常用的系统设置进行修改，包括：

- DNS
- Hosts
- Swap
- 主机名
- 操作系统用户密码
- NTP 服务器
- 系统时区
- 服务器时间

![img.png](_txtdbpic/b6ac24162f3b3fe2b689ddd5e78efb85_MD5.png)







# 缓存清理

在 `缓存清理` 页面，可以扫描并清理 1Panel 运行期间积累的垃圾文件，包括：

- 系统垃圾
  - 系统快照恢复前备份文件
  - 系统升级备份文件
  - 系统快照临时文件
  - 恢复前备份文件
  - 系统缓存文件
  - 系统废弃目录
- 容器垃圾
  - 所有违背任何容器使用的镜像
  - 所有处于停止状态的容器
  - 存储卷
  - 构建缓存
- 临时上传文件
  - 临时长传文件
  - 应用
  - 网站
  - 数据库
  - 文件夹
- 临时下载文件
  - 应用
  - 网站
  - 数据库
  - 文件夹
- 系统日志文件
  - 系统日志文件
  - 容器操作日志文件
  - 计划任务执行日志文件

![img.png](_txtdbpic/65412d46cc60ce99a5a126f33843ae46_MD5.png)







# 进程守护

## 1 安装[⚓︎](https://1panel.cn/docs/v2/user_manual/toolbox/supervisor/#1)

[RedHat / CentOS](https://1panel.cn/docs/v2/user_manual/toolbox/supervisor/#__tabbed_1_1)[Ubuntu / Debian](https://1panel.cn/docs/v2/user_manual/toolbox/supervisor/#__tabbed_1_2)

**1、安装 epel 源**

```
yum install -y epel-release
```

**2、安装 supervisor**

```
yum install -y supervisor
```

**3、启动 supervisord 服务**

```
systemctl start supervisord
```

**4、开机自启动**

```
systemctl enable supervisord
```

**5、查看 supervisord 服务状态**

```
systemctl status supervisord
```

## 2 初始化[⚓︎](https://1panel.cn/docs/v2/user_manual/toolbox/supervisor/#2)

首次使用需要先初始化 supervisor，导入配置文件位置和服务名称。

![初始化](_txtdbpic/d77d5ef8de310b5d3340f8c7f6d3034f_MD5.png)

后期服务名称和配置文件有变动，可以在设置页面进行重新初始化。

![重新初始化](_txtdbpic/0158a3eeaeb10de5e8cac9ff7d5a873e_MD5.png)

## 3 创建[⚓︎](https://1panel.cn/docs/v2/user_manual/toolbox/supervisor/#3)

点击创建守护进程按钮，填写相应参数，点击确认。

![创建](_txtdbpic/e63b2d32c817ee4cba2a484330e1aa48_MD5.png)

## 4 守护进程管理[⚓︎](https://1panel.cn/docs/v2/user_manual/toolbox/supervisor/#4)

列表页面可以操作守护进程，包括启动、停止、重启、查看日志、编辑、删除、修改源文等。

![创建](_txtdbpic/dee5a884012b910f5119d196df204305_MD5.png)

## 5 Supervisor 管理[⚓︎](https://1panel.cn/docs/v2/user_manual/toolbox/supervisor/#5-supervisor)

Supervisor 状态栏可以重启 停止 Supervisor 服务，查看日志，修改配置文件等。

![创建](_txtdbpic/b5089198a20f37a71ee132df51a908c1_MD5.png)







# 病毒扫描

## 1 介绍[⚓︎](https://1panel.cn/docs/v2/user_manual/toolbox/clam/#1)

ClamAV 是一个开源（GPLv2许可）的反病毒工具包，专为邮件网关上的电子邮件扫描而设计。它提供了多种实用工具，包括灵活且可扩展的多线程守护进程、命令行扫描器以及用于自动更新数据库的高级工具。该工具包的核心是一个作为共享库形式提供的反病毒引擎。

## 2 环境要求[⚓︎](https://1panel.cn/docs/v2/user_manual/toolbox/clam/#2)

**ClamAV 的最低建议配置为：**

- CPU 要求：1 CPU，2.0 Ghz+
- 内存要求：3 GiB+
- 服务器架构：至少 5GiB 可用磁盘空间

## 3 安装[⚓︎](https://1panel.cn/docs/v2/user_manual/toolbox/clam/#3)

[RedHat / CentOS](https://1panel.cn/docs/v2/user_manual/toolbox/clam/#__tabbed_1_1)[Ubuntu / Debian](https://1panel.cn/docs/v2/user_manual/toolbox/clam/#__tabbed_1_2)

**1、安装 epel 源**

```
yum install -y epel-release
```

**2、安装 ClamAV**

```
yum install clamav clamd clamav-update -y
```

**3、修改 ClamAV 配置文件**

```
/etc/clamd.d/scan.conf 取消下面行注释
LogFile /var/log/clamd.scan
LogFileMaxSize 2M
PidFile /run/clamd.scan/clamd.pid
DatabaseDirectory /var/lib/clamav
LocalSocket /run/clamd.scan/clamd.sock
```

**4、修改病毒库刷新配置文件**

```
/etc/freshclam.conf 取消下面行注释
DatabaseDirectory /var/lib/clamav
UpdateLogFile  /var/log/freshclam.log
PidFile  /var/run/freshclam.pid
DatabaseMirror database.clamav.net
Checks 12
```

**5、启动 ClamAV 服务**

```
freshclam
systemctl start clamd@scan.service
systemctl start clamav-freshclam.service
```

**6、开机自启动**

```
systemctl enable clamd@scan.service
systemctl enable clamav-freshclam.service
```

**7、查看 ClamAV 服务状态**

```
systemctl status clamd@scan.service
systemctl status clamav-freshclam.service
```

## 4 扫描规则[⚓︎](https://1panel.cn/docs/v2/user_manual/toolbox/clam/#4)

配置说明

- 扫描目录：病毒扫描任务扫描的目标目录
- 感染文件策略：发现感染文件后，需要执行的操作方式，支持不操作、删除文件、移动文件到隔离目录、复制文件到隔离目录
- 定时扫描（✨专业版）：配置定时任务，定时执行扫描任务
- 是否告警（✨专业版）：扫描到感染文件后，发送短信告警

点击操作列的 `执行` 可以手动执行该条扫描规则，点击 `报告` 即可查看该条扫描规则的执行记录和扫描结果。

![img.png](_txtdbpic/22416455ac1727628ca6ab3af86ad68b_MD5.png)

## 5 病毒类型说明[⚓︎](https://1panel.cn/docs/v2/user_manual/toolbox/clam/#5)

| 类型           | 说明                                                         |
| :------------- | :----------------------------------------------------------- |
| Adware         | 广告软件，通常在用户不知情的情况下显示广告。                 |
| Backdoor       | 后门，允许攻击者远程访问和控制受感染系统的程序或功能。       |
| Coinminer      | 加密货币挖矿程序，用于非法挖掘加密货币的恶意软件。           |
| Countermeasure | 反对抗措施，指示该签名用于识别防御性安全工具。               |
| Downloader     | 下载器，用于下载和执行其他恶意软件或组件的程序。             |
| Dropper        | 放置器，用于将其他恶意软件注入到受感染系统中的程序。         |
| Exploit        | 漏洞利用程序，利用系统或应用程序中的漏洞进行攻击的恶意软件。 |
| File           | 文件类型，用于描述独立文件的签名。                           |
| Filetype       | 文件类型，描述恶意文件的类型。                               |
| Infostealer    | 信息窃取程序，用于窃取用户敏感信息的恶意软件。               |
| Ircbot         | IRC 机器人，用于连接到 IRC（Internet Relay Chat）网络的恶意软件。 |
| Joke           | 恶作剧，不良影响系统但通常不造成实际损害的恶意软件。         |
| Keylogger      | 键盘记录器，用于记录用户输入的恶意软件。                     |
| Loader         | 装载器，用于加载和执行其他恶意软件的程序。                   |
| Macro          | 宏病毒，针对文档或电子表格中的宏命令进行攻击的恶意软件。     |
| Malware        | 恶意软件，一般术语，指任何有害的计算机程序。                 |
| Packed/Packer  | 打包/打包工具，用于压缩和加密恶意软件以逃避检测的程序。      |
| Phishing       | 钓鱼，用于欺骗用户输入个人信息的恶意软件。                   |
| Proxy          | 代理，用于通过受感染系统进行网络通信的恶意软件。             |
| Ransomware     | 勒索软件，加密用户文件并勒索解密费用的恶意软件。             |
| Revoked        | 已撤销的，指示签名或证书已被官方撤销的恶意软件。             |
| Rootkit        | 根套件，用于隐藏恶意软件活动和存在的程序。                   |
| Spyware        | 间谍软件，用于监视用户活动并发送给攻击者的恶意软件。         |

## 6 故障排除[⚓︎](https://1panel.cn/docs/v2/user_manual/toolbox/clam/#6)

- 如果 clamav 服务无法启动，请检查配置信息以及日志
- 检查病毒库数据是否正常，在配置文件中会指定 DatabaseDirectory ，即病毒库存放位置，检查是否存在，不存在的话，手动执行一下 freshclam 命令
- 如果手动执行 freshclam 也无法正常下载的话，可以从以下地址下载后传到该目录下
  - https://database.clamav.net/daily.cvd
  - https://database.clamav.net/bytecode.cvd
  - https://database.clamav.net/main.cvd





# FTP

## 1 安装[⚓︎](https://1panel.cn/docs/v2/user_manual/toolbox/ftp/#1)

[RedHat / CentOS](https://1panel.cn/docs/v2/user_manual/toolbox/ftp/#__tabbed_1_1)[Ubuntu / Debian](https://1panel.cn/docs/v2/user_manual/toolbox/ftp/#__tabbed_1_2)

**1、安装 epel 源**

```
yum install -y epel-release
```

**2、安装 Pure-FTPd**

```
yum -y install pure-ftpd
```

**3、修改默认配置**

```
# 默认配置位于 /etc/pure-ftpd/pure-ftpd.conf，在配置文件中找到下面几个参数进行修改：

# 指定路径，PureDB用户数据库文件
PureDB /etc/pure-ftpd/pureftpd.pdb
# 开启日志
VerboseLog yes
# 拒绝匿名登录
NoAnonymous yes
# 开启被动端口范围 (这里需要根据实际需求调整端口范围)
PassivePortRange 39000 40000
```

**4、启动 Pure-FTPd 服务**

```
systemctl start pure-ftpd.service
```

**5、查看 Pure-FTPd 服务状态。**

```
systemctl status pure-ftpd.service
```

## 2 故障排除[⚓︎](https://1panel.cn/docs/v2/user_manual/toolbox/ftp/#2)

- 如果之前已经安装过 Pure-FTPd，可以直接通过界面同步按钮同步到 1panel 上，但是同步过程中无法同步密码，需要在界面上手动编辑
- 如果无法正常连接，可以从以下方向检查
  - 防火墙是否开启，是否放行 Pure-FTPd 端口 ( 默认 21，可以通过 netstat -tunlp |grep pure-ftpd 或者 cat /etc/pure-ftpd/pure-ftpd.conf | grep Bind 查询)
  - 是否放行 Pure-FTPd 被动端口 ( 可以通过 cat /etc/pure-ftpd/pure-ftpd.conf | grep PassivePortRange 或者 cat /etc/pure-ftpd/conf/PassivePortRange 文件查询 )
  - 是否开启 selinux







# Fail2ban

## 1 安装[⚓︎](https://1panel.cn/docs/v2/user_manual/toolbox/fail2ban/#1)

[RedHat / CentOS](https://1panel.cn/docs/v2/user_manual/toolbox/fail2ban/#__tabbed_1_1)[Ubuntu / Debian](https://1panel.cn/docs/v2/user_manual/toolbox/fail2ban/#__tabbed_1_2)

**1、安装 epel 源**

```
yum install -y epel-release
```

**2、安装 Fail2ban**

```
yum install -y fail2ban
```

**3、启动 Fail2ban 服务**

```
systemctl start fail2ban
```

**4、开机自启动**

```
systemctl enable fail2ban
```

**5、查看 Fail2ban 服务状态**

```
systemctl status fail2ban
```

## 2 默认配置[⚓︎](https://1panel.cn/docs/v2/user_manual/toolbox/fail2ban/#2)

1Panel 会默认使用以下配置：

```
#DEFAULT-START
[DEFAULT]
bantime = 600
findtime = 300
maxretry = 5
banaction = firewallcmd-ipset
action = %(action_mwl)s
#DEFAULT-END

[sshd]
ignoreip = 127.0.0.1/8               # 白名单
enabled = true
filter = sshd
port = 22                            # 端口
maxretry = 2                         # 最大尝试次数
findtime = 300                       # 发现周期 单位s
bantime = 600                        # 封禁时间，单位s。-1为永久封禁
action = %(action_mwl)s
banaction = iptables-multiport       # 禁用方式
logpath = /var/log/secure            # SSH 登陆日志位置
```



## 3 故障排除[⚓︎](https://1panel.cn/docs/v2/user_manual/toolbox/fail2ban/#3)

- 如之前已经手动安装过 Fail2ban，需要将 [sshd] 部分的配置信息写入到 jail.local 中，重启 fail2ban 服务，否则可能出现获取黑名单报错的问题
- 如果选择的禁用方式为 -muliport，则在封禁时，只会禁用配置中的端口，如默认配置中的 22
- 如果需要修改禁用方式，需要先判读对应服务是否正常可用
  - RedHat/CentOS 使用的是 Firewall 防火墙
  - Debian/Ubuntu使用的是 UFW 防火墙
- 日志路径需要根据操作系统修改
  - RedHat/CentOS 日志为 /var/log/secure
  - Debian/Ubuntu 日志为 /var/log/auth.log
- Debian 从 12 开始弃用了 rsyslog，使用时需要先自行安装







# 概述

WAF 是 Web Application Firewall 的缩写，也被称为 Web 应用防火墙。 可以保护你的网站免受恶意攻击，如 SQL 注入、XSS 攻击等。

![img.png](_txtdbpic/a65261d51482a3b50c5967c980274a9d_MD5.png)







# 概览

概览页可以查看今日状态、拦截地图、请求趋势、拦截趋势等。

![img.png](_txtdbpic/a65261d51482a3b50c5967c980274a9d_MD5.png)







# 全局设置

全局设置可以查看并配置 WAF。
包括黑白名单、频率设置、默认规则、自定义规则、配置等功能。
注意：

- 全局设置的开关可以控制所有网站的规则，比如关闭访问频率之后所有网站的访问频率限制都会失效
- 全局设置中的小项，比如默认规则-参数规则的第一项，关闭了之后，只影响新建网站，不影响现存网站

![img.png](_txtdbpic/cdc8319e7b60c429cdac5e43e25fe3e7_MD5.png)

## 1 黑白名单[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/global/#1)

- 包括 IP 黑白名单、 URL 黑白名单、User-Agent 黑白名单、IP 组
- 黑名单：阻止携带黑名单特征的请求
- 白名单：对携带白名单特征的请求，不做 WAF 校验

### 1.1 IP 黑白名单[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/global/#11-ip)

可以根据 IP 地址阻止/放行请求。

### 1.2 URL 黑白名单[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/global/#12-url)

- 黑名单：可以阻止用户访问某些 URL
- 白名单：用户访问白名单中的 URL 不会触发 WAF 校验，适合某些请求中包含 SQL 注入和 XSS 特征的请求，比如 WordPress Halo 文章保存接口

### 1.3 User-Agent 黑白名单[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/global/#13-user-agent)

可以根据 User-Agent 阻止/放行请求。

### 1.4 IP 组[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/global/#14-ip)

可以把多个 IP 包含在一个组中，用于 IP 黑白名单。

## 2 频率限制[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/global/#2)

可以用来抵御 CC 攻击，包含访问频率限制、攻击频率限制、404 频率限制。

### 2.1 访问频率限制[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/global/#21)

- 如果单位时间内请求超过阈值，就拉黑 IP 一段时间
- 全局模式：单位时间请求任意 URL 次数之和超过阈值即触发
- URL 模式：单位时间请求单个 URL 次数超过阈值即触发

![img.png](_txtdbpic/e74c39cbda22a62221a5bdde9d34128c_MD5.png)

### 2.2 攻击频率限制[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/global/#22)

- 如果某个 IP 一直触发 WAF 规则，则拉黑此 IP
- 场景：某个 IP 一直攻击你的网站，触发了多次规则

![img.png](_txtdbpic/842a30876822653dd2e4431820a3e8f5_MD5.png)

### 2.3 404频率限制[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/global/#23-404)

- 如果某个 IP 的访问一直返回 404 ，则拉黑此 IP
- 场景：扫描器或者恶意爬虫一直爬你的网站

![img.png](_txtdbpic/15c243c1e24c8dc61e84faea3e7a976d_MD5.png)

## 3 默认规则[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/global/#3)

WAF 的默认规则，按照一定的规则来阻止恶意请求。

### 3.1 参数规则[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/global/#31)

过滤常见的恶意参数。

### 3.2 URL 规则[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/global/#32-url)

过滤常见的恶意 URL。

### 3.3 HTTP 规则[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/global/#33-http)

设置允许访问的方法类型，如果想限制某些类型访问，请关闭这个类型的按钮，例如：仅允许 GET 类型访问，那么需要关闭除了 GET 之外的其他类型按钮。

### 3.4 Cookie 规则[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/global/#34-cookie)

过滤携带恶意 Cookie 的请求。

### 3.5 Header 规则[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/global/#35-header)

过滤携带恶意 Header 的请求。

### 3.6 User-Agent 规则[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/global/#36-user-agent)

过滤携带恶意 User-Agent 的请求。

### 3.7 其他[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/global/#37)

SQL 注入防御 和 XSS 防御。

## 4 自定义规则[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/global/#4)

- 根据自己的需求制定 WAF 规则
- 包含自定义规则、文件上传限制、地区访问限制、CDN 配置

### 4.1 自定义规则（✨专业版）[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/global/#41)

- 根据自己的需求制定 WAF 规则
- 可以匹配 URL IP Header Host 的参数，并选择相应的动作
- 比如可以选择 URL 为 /login 的比如经过人机验证

![img.png](_txtdbpic/60db3a7dcd04d33de3e3214f8ffa36f2_MD5.png)

### 4.2 文件上传限制[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/global/#42)

可以根据文件后缀限制上传文件的类型。

![img.png](_txtdbpic/d5969a1cbcf4766fc4c76cfa1c3fa41a_MD5.png)

### 4.3 地区访问限制（✨专业版）[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/global/#43)

可以限制或者仅允许某些地区的访问。

![img.png](_txtdbpic/89903f081dcc88180f395922e4a2b2ff_MD5.png)

### 4.4 CDN[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/global/#44-cdn)

如果网站开启了 CDN 并且影响日志获取用户的 IP，可以开启此项：

- 从 HTTP Header 中获取：从指定的请求 Header 中获取，需要确认 CDN 把真实 IP 放在哪个 Header，比如 CloudFlare 默认是放在 cf-connecting-ip 中
- 从 Header 列表中获取： 从常用的 CDN 携带真实 IP 的 HTTP Header 中获取，取第一个能获取到的值
- 获取 X-Forwarded-For 的上一级代理地址：例如：X-Forwarded-For: client,proxy1,proxy2,proxy3 上一级代理会取最后一个 IP proxy3

![img.png](_txtdbpic/6659d7d1e7313c0b67cbcadee78bb634_MD5.png)

## 5 配置[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/global/#5)

包含拦截页面和恶意 IP 组。

### 5.1 拦截页面（✨专业版）[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/global/#51)

可以自定义拦截页面。

![img.png](_txtdbpic/ce4050aa92afd3f4c055d80f3e20fc6d_MD5.png)

### 5.2 恶意 IP 组[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/global/#52-ip)

拦截由 1Panel 提供的恶意 IP 组。









# 网站设置

网站设置，可以查看并配置某个网站的 WAF 规则。
包括频率设置 默认规则 自定义规则 等。

![img.png](_txtdbpic/8827ff8d78f211a8f52cc9e14fc199a8_MD5.png)

## 1 频率限制[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/site/#1)

可以用来抵御 CC 攻击，包含访问频率限制、攻击频率限制、404 频率限制。

### 1.1 访问频率限制[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/site/#11)

如果单位时间内请求超过阈值，就拉黑 IP 一段时间。

- 全局模式：单位时间请求任意 URL 次数之和超过阈值即触发
- URL 模式：单位时间请求单个 URL 次数超过阈值即触发

![img.png](_txtdbpic/e74c39cbda22a62221a5bdde9d34128c_MD5.png)

## 2 默认规则[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/site/#2)

WAF 的默认规则，按照一定的规则来阻止恶意请求。

### 2.1 参数规则[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/site/#21)

过滤常见的恶意参数。

### 2.2 URL 规则[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/site/#22-url)

过滤常见的恶意 URL。

### 2.3 HTTP 规则[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/site/#23-http)

设置允许访问的方法类型，如果想限制某些类型访问，请关闭这个类型的按钮，例如：仅允许 GET 类型访问，那么需要关闭除了 GET 之外的其他类型按钮。

### 2.4 Cookie 规则[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/site/#24-cookie)

过滤携带恶意 Cookie 的请求。

### 2.5 Header 规则[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/site/#25-header)

过滤携带恶意 Header 的请求。

### 2.6 User-Agent 规则[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/site/#26-user-agent)

过滤携带恶意 User-Agent 的请求。

### 2.7 其他[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/site/#27)

SQL 注入防御 和 XSS 防御。

## 3 自定义规则[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/site/#3)

根据自己的需求制定 WAF 规则。

- 包含自定义规则、文件上传限制、地区访问限制、CDN 配置

## 3.1 自定义规则（✨专业版）[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/site/#31)

根据自己的需求制定 WAF 规则。可以匹配 URL IP Header Host 的参数，并选择相应的动作。比如可以选择 URL 为 /login 的比如经过人机验证。

![img.png](_txtdbpic/60db3a7dcd04d33de3e3214f8ffa36f2_MD5.png)

## 3.2 文件上传限制[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/site/#32)

可以根据文件后缀限制上传文件的类型。

![img.png](_txtdbpic/d5969a1cbcf4766fc4c76cfa1c3fa41a_MD5.png)

## 3.3 地区访问限制（✨专业版）[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/site/#33)

可以限制或者仅允许某些地区的访问。

![img.png](_txtdbpic/89903f081dcc88180f395922e4a2b2ff_MD5.png)

## 3.4 CDN[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/waf/site/#34-cdn)

如果网站开启了 CDN 并且影响日志获取用户的 IP，可以开启此项：

- 从 HTTP Header 中获取：从指定的请求 Header 中获取，需要确认 CDN 把真实 IP 放在哪个 Header，比如 CloudFlare 默认是放在 cf-connecting-ip 中
- 从 Header 列表中获取： 从常用的 CDN 携带真实 IP 的 HTTP Header 中获取，取第一个能获取到的值
- 获取 X-Forwarded-For 的上一级代理地址：例如：X-Forwarded-For: client,proxy1,proxy2,proxy3 上一级代理会取最后一个 IP proxy3

![img.png](_txtdbpic/6659d7d1e7313c0b67cbcadee78bb634_MD5.png)









# 拦截记录

拦截记录 可以查看 WAF 拦截的请求。 可以拉黑 IP、给 URL 加白名单、查看详细信息等。

![img.png](_txtdbpic/8f14fc00b461db90b91878a97d955c4e_MD5.png)







# 封锁记录

封锁记录 可以查看 WAF 临时拉黑的 IP。 可以拉黑或者解封 IP。

![img.png](_txtdbpic/bda66111d4166b4846df85849dd857d5_MD5.png)







# 💎节点管理

1Panel 节点管理功能旨在为用户提供便捷、高效的多服务器管理体验。通过节点管理，用户可以轻松管理多个服务器节点，实现统一的资源监控、应用部署、配置管理和运维操作。

💎 **专业版功能**：节点管理为 1Panel 专业版专属功能，支持多节点切换、统一监控、批量更新、文件互传等高级特性。

## 1 功能概述[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/node/#1)

功能概述

- 节点管理功能支持多服务器节点的统一管理，包括节点添加、删除、状态监控、资源统计等
- 支持节点分组管理，便于按业务、环境或地域对节点进行分类管理
- 实时查看各节点的 CPU、内存、磁盘、网络等资源使用情况
- 支持多节点切换，可以在统一控制台切换到不同节点完成应用部署管理等操作
- 提供节点间的配置同步功能，确保集群配置的一致性

## 2 节点概览[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/node/#2)

在节点概览页面可以查看到当前集群中所有节点的整体状态，包括节点数量、在线状态、资源使用情况、应用分布等统计信息。

![img.png](_txtdbpic/136706b2716933f5438a10fde235f43d_MD5.png)

## 3 添加节点[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/node/#3)

点击【添加节点】按钮，输入节点信息，即可将新的服务器节点添加到集群中。

### 3.1 节点信息配置[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/node/#31)

- **主机地址**：输入节点的 IP 地址或域名，确保主节点服务器可以访问到该节点

- **用户名**：节点的 SSH 连接用户名，需要使用 root 或具有免密 sudo 权限的用户

- 认证方式

  ：支持密码认证和私钥认证两种方式

  - **密码认证**：输入节点的 SSH 连接密码
  - **私钥认证**：上传节点的私钥文件，支持 PEM 和 PPK 格式 如果有私钥密码，请输入密码

- **端口**：节点的 SSH 连接端口，默认为 22

- **安装目录**：1Panel 相关内容的安装目录，默认为 /opt

- **安装端口**：1Panel Agent 服务的监听端口，默认为 9999，请确保该端口未被占用且主节点服务器可以访问到该端口

- **节点类型**：选择该节点为社区版节点还是专业版节点，专业版节点包含专业版功能

- **许可证**：当节点为社区版节点时，选择某个专业版许可证将消耗该许可证的社区版节点额度 当节点为专业版节点时，需要选择某个未绑定的专业版许可证绑定到该节点 许可证可在[【许可证管理】](https://1panel.cn/user_manual/settings/#5)页面中导入和管理

- **节点分组**：选择节点所属的分组，便于分类管理

- **名称**：为节点设置一个便于识别的名称，建议使用有意义的命名规则

- **描述**：为节点添加描述信息，说明节点的用途和特点

- 数据同步配置

  ：选择特定的配置信息是否需要同步到该节点，包括

  - **系统代理设置**
  - **系统告警设置**
  - **自定义应用仓库**
  - **备份账号设置**

![img.png](_txtdbpic/7b184d442eb0fab7efd8e9be0a42c8a9_MD5.png)

### 3.2 可用性检查[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/node/#32)

添加节点前，需要先进性可用性检查，验证网络连通性和认证信息的正确性。只有通过可用性检查的节点才能成功添加。

![img.png](_txtdbpic/d8d98878f354b062d3fd8064115e255f_MD5.png)

### 3.3 添加节点[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/node/#33)

可用性检查通过后，点击【确定】按钮，完成节点添加。

![img.png](_txtdbpic/c427703c557b634cbf5f1bebfd010ad1_MD5.png)

## 4 节点管理[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/node/#4)

在节点列表页面，可以查看所有节点的详细信息，包括状态、资源使用情况、当前版本等，并对节点进行各种管理操作。

### 4.1 节点状态监控[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/node/#41)

- **状态**：实时显示节点的在线/离线状态
- **版本**：显示当前节点的版本信息及社区版/专业版标识
- **资源使用率**：显示 CPU、内存、磁盘、网络的使用情况
- **数据同步状态**：显示节点的数据同步状态

![img.png](_txtdbpic/7f5c16206a69b733e916b86327a54f40_MD5.png)

### 4.2 节点操作[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/node/#42)

支持对节点进行以下操作：

- **编辑**：修改节点配置信息
- **删除**：从集群中移除节点（可以选择是否删除节点数据）
- **更新**：更新节点版本
- **同步**：将主节点配置同步到当前节点
- **重启面板**：重启节点面板服务
- **重启服务器**：重启节点服务器

## 5 节点分组管理[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/node/#5)

节点分组功能允许用户按照业务需求、环境类型或地理位置对节点进行分类管理。

![img.png](_txtdbpic/68a3923c235094ea92c0d622592ace56_MD5.png)

## 6 节点切换[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/node/#6)

在面板管理页面左下角，显示当前节点信息，点击节点名称，可以切换到其他节点。后续进行的所有操作，例如应用部署、网站管理等，都会在当前节点上进行。

![img.png](_txtdbpic/9439cb727861d32b86a3c399f107583c_MD5.png)

## 7 故障处理[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/node/#7)

![img.png](_txtdbpic/2b25291bd26ce08cf7bcc66040a0bad9_MD5.png)

当节点状态异常时，可以点击节点列表状态列上的异常图标，查看异常原因。

![img.png](_txtdbpic/e3304aa2aa2be4cb92df65a44b8a84cf_MD5.png)









# 💎网站防篡改

1Panel 网站防篡改功能旨在保护网站免受未经授权的修改或篡改。

💎 **专业版功能**：网站防篡改为 1Panel 专业版专属功能。

## 1 功能概述[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/tamper/#1)

功能概述

- 支持通过设置排除、保护规则，适应各种网站目录结构；
- 支持排除、保护模版，针对不同的网站快速设置；
- 支持按照文件结构查看保护状态；
- 支持查看筛选拦截日志。

## 2 功能使用[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/tamper/#2)

```
以文件目录为例，列举两种规则设置：
     index
        index.html
        404.html
        test.ts
     log
        access.log
        err.log
```

规则 1

- 保护文件：.html
- 排除目录：log
- 设置：
  - index 目录下 *.html 的文件会被限制创建和删除操作，删除直接不允许操作，创建会生成一个拦截记录；
  - index 目录下 test.ts 可以自由删除和创建；
  - index 目录下可以自由创建 log 目录，因为该目录名被排除；
  - index 目录下不能创建 tmp 目录，因为其未被排除，创建会生成一个拦截记录；
  - log 目录以及目录下文件可以自由操作。

规则 2：

- 保护文件：.html ./log/access.log
- 排除目录：log
- 设置：
  - 和规则 1 相比，access.log 会被限制不允许删除修改，如果保护文件是具体文件目录，具有最高优先级
  - 其他和规则一相同

## 3 说明[⚓︎](https://1panel.cn/docs/v2/user_manual/xpack/tamper/#3)

其他说明

- 排除目录下所有文件可以自由操作，只是目录下具体路径的保护文件同样会被限制编辑和删除；
- 保护目录下可以自由创建非保护文件以及排除目录，否则会生成一条拦截记录；
- 限制保护目录下保护文件的编辑和删除等操作，限制非排除目录的创建和删除。





# 日志审计

## 1 面板日志[⚓︎](https://1panel.cn/docs/v2/user_manual/logs/#1)

### 1.1 操作日志[⚓︎](https://1panel.cn/docs/v2/user_manual/logs/#11)

用于记录用户在 1Panel 上进行的操作。

![面板日志-操作日志](_txtdbpic/944b48d3db769991330f5a0fdeecaa5e_MD5.png)

### 1.2 访问日志[⚓︎](https://1panel.cn/docs/v2/user_manual/logs/#12)

用于记录 1Panel 控制台的访问日志。

![面板日志-访问日志](_txtdbpic/b00e9e4339220d60d870d106ab8bf65e_MD5.png)

### 1.3 系统日志[⚓︎](https://1panel.cn/docs/v2/user_manual/logs/#13)

用于记录 1Panel 服务的运行日志，可用于开发人员等快速定位问题。

![面板日志-系统日志](_txtdbpic/da8f7d4cb69c41d4e1ba1966131449f6_MD5.png)

## 2 登录日志[⚓︎](https://1panel.cn/docs/v2/user_manual/logs/#2)

主要记录服务器的 ssh 登录记录，可用于查询是否有人恶意登录和操作。

提示

日志内容从操作系统 SSH 登录日志文件中读取而来，文件位置一般为 `/var/log/secure` 或者 `/var/log/auth.log`。

当需要清理登录日志时，可以手动删除上述文件中的历史内容。

![登录日志](_txtdbpic/b035ea177b75951f1c972877b675242f_MD5.png)

## 3 网站日志[⚓︎](https://1panel.cn/docs/v2/user_manual/logs/#3)

用于查看在 1Panel 上创建的各个网站的日志，分为运行日志和错误日志，可以用于排查网站的访问问题。

![img.png](_txtdbpic/632f809e9fceb0f9dd22d74776b498fa_MD5.png)

![img.png](_txtdbpic/f177ae597039a50f2e3cdb1d1e06bdc7_MD5.png)











# 面板设置

## 1 面板[⚓︎](https://1panel.cn/docs/v2/user_manual/settings/#1)

支持面板的一些基础设置，具体包括：

- 面板用户：1Panel 系统仅支持单主机单用户，此处是用于登录 1Panel 面板的验证信息，在初次登陆时由用户初始化
- 面板密码：用于登录 1Panel 面板的密码
- 主题颜色： 系统支持亮色（light）和 暗色（dark），可根据用户使用习惯手动切换，也可以选择跟随系统，根据浏览器及操作系统使用的主题模式自动切换
- 菜单标签页：开启后，将在页面最上方通过多标签页的方式，列出最近访问过的菜单
- 面板别名： 用户可自定义面板名称
- 系统语言： 系统当前支持中文和英文
- 超时时间： 此处为系统用户登陆后，多长时间未操作系统自动退出，最小超时时间为 300 秒
- 服务器地址：设置当前服务器的地址，配置后可以点击应用商店已安装应用的服务端口，快速打开指定应用服务页面
- 代理服务器（✨专业版）：配置代理服务器后，1Panel 中的部分网络请求将通过指定的代理服务器进行转发，适合用在内网环境服务器无法直接访问互联网的场景中
- 预览体验计划：开启后可以获取到 1Panel 的预览版本，以分享有关新功能和更新的反馈
- 高级功能菜单隐藏：控制是否在左侧菜单中显示高级功能菜单项

![img.png](_txtdbpic/32038177656f051de0e8cd1e548e5c7c_MD5.png)

## 2 安全[⚓︎](https://1panel.cn/docs/v2/user_manual/settings/#2)

配置说明

针对一些系统要求等级比较高的用户，我们增加了一些安全设置，具体包括：

- 面板端口：修改 1 监听地址：修改 1Panel 服务监听的 IP 地址，需谨慎操作，防止监听地址后当前客户端无法访问到面板
- 安全入口：开启安全入口后只能通过指定安全入口登录面板，同时支持配置是否开启相关提示
- 未认证设置：配置未使用安全入口访问面板时的返回内容
- 授权 IP：设置授权 IP 后，仅有设置中的 IP 可以访问 1Panel 服务，支持配置多个 IP 地址
- 域名绑定：设置域名绑定后，仅能通过设置中域名访问 1Panel 服务
- 面板 SSL：为面板设置 HTTPS 协议访问，提升面板访问安全性，开启后仅能通过 HTTPS 协议访问 1Panel 服务
- 密码过期时间： 系统支持设置密码过期天数，默认未设置，当密码超过过期时间时，系统将跳转到改密界面，需要修改账户密码，且新密码不能与老密码相同
- 密码复杂度校验： 开启后，账户密码必须长度大于 8 位，且包含数字、字母及特殊字符，如 Password@2023
- 两步校验： 开启 MFA 登录验证，登录时输入用户名密码后，需要手机或者浏览器扫描二维码完成登录，提升系统安全等级

![img.png](_txtdbpic/c769e82424b7ae81cbb248955c959dfd_MD5.png)

注意

以上设置修改后会影响访问 1Panel 服务的方式，可能导致不能正常打开、登录 1Panel 面板的情况。

此时可以 SSH 登录到服务器后，使用 `1pctl reset` 和 `1pctl update` 命令重置或更新特定配置。

```
root@hostname:/# 1pctl reset --help
重置系统信息

Usage:
1panel reset [command]

Available Commands:
domain      取消 1Panel 访问域名绑定
entrance    取消 1Panel 安全入口
https       取消 1Panel https 方式登录
ips         取消 1Panel 授权 IP 限制
mfa         取消 1Panel 两步验证

Flags:
-h, --help   help for reset

Use "1panel reset [command] --help" for more information about a command.
root@hostname:/# 1pctl update
修改面板信息

Usage:
1panel update [command]

Available Commands:
password    修改面板密码
port        修改面板端口
username    修改面板用户

Flags:
-h, --help   help for update

Use "1panel update [command] --help" for more information about a command.
```

## 3 备份账号[⚓︎](https://1panel.cn/docs/v2/user_manual/settings/#3)

### 3.1 已支持的备份账号[⚓︎](https://1panel.cn/docs/v2/user_manual/settings/#31)

**支持添加本地服务器磁盘和第三方账号：**

- 阿里云 OSS
- 腾讯云 COS
- 亚马逊 S3 云存储
- 微软 OneDrive
- 谷歌云盘
- 阿里云盘
- MINIO
- WebDAV
- SFTP
- 七牛云 Kodo
- 又拍云 对象存储

### 3.2 OneDrive 自定义配置[⚓︎](https://1panel.cn/docs/v2/user_manual/settings/#32-onedrive)

**在调用 Onedrive API 时需要使用到 4 个参数：**

- client_id: 客户端ID
- client_secret: 客户端密码
- redirect_uri: 重定向地址
- scope: API权限

（1）访问并登录 MicroSoft Azure：https://portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade。

（2）点击新注册，并填写注册信息，其中的重定向 URI 作为 重定向 Url 参数。

![img.png](_txtdbpic/95a2b33382c139ee46e040b61420f690_MD5.png)

（3）主页上的 应用程序(客户端) ID 作为客户端 ID。

![img.png](_txtdbpic/906df365a630d23c519122f4ea91fe90_MD5.png)

（4）在【证书和密码】页面新建客户端密码，填写相关信息，生成的值作为客户端密钥。

![img.png](_txtdbpic/19c5838996cf82cbc9f3470c4740dd56_MD5.png)

（5）在【API 权限】页面选择需要的权限，添加权限，Microsoft Graph，委托的权限，勾选 Files.ReadWrite All、offline_access、User.Read，这将作为 scope 传递。

![img.png](_txtdbpic/0d7d5941cc984a6fb55bf45bfa56a765_MD5.png)

### 3.3 OneDrive 账号绑定[⚓︎](https://1panel.cn/docs/v2/user_manual/settings/#33-onedrive)

（1）点击 OneDrive 授权码获取按钮。

![img.png](_txtdbpic/83bf833832c8159731da9c552097c306_MD5.png)

（2）输入 Onedrive 账号信息。

![img.png](_txtdbpic/94ef07d9008d5d37484bf5e1b41fdbf9_MD5.png)

（3）信任 1panel 服务。

![img.png](_txtdbpic/d7e8e2201c593dd7657155d030d41868_MD5.png)

（4）复制授权码到 1Panel 授权码输入框 (注意不要包含 &session_state=xxx 部分)。

![img.png](_txtdbpic/4b02770e668982ab63b8e916d70577bd_MD5.png)

### 3.4 阿里云盘账号绑定[⚓︎](https://1panel.cn/docs/v2/user_manual/settings/#34)

（1）登陆网页版阿里云盘 (https://www.alipan.com/)。

（2）右键检查或者 F12 打开浏览器调试模式，找到 token 信息，复制值。

![img.png](_txtdbpic/4066e1632d33e4c50f66d80f86d5a91b_MD5.png)

（3）将复制的值粘贴到 1 处，点击解析，自动解析出 3 和 4 输入框的值，修改备份目录后点击确认即可。

![img.png](_txtdbpic/eec925261e48d220387979da47b1e13d_MD5.png)

### 3.5 谷歌云盘账号绑定[⚓︎](https://1panel.cn/docs/v2/user_manual/settings/#35)

**在调用 Google API 时需要使用到 3 个参数：**

- client_id: 客户端ID
- client_secret: 客户端密码
- redirect_uri: 重定向地址

（1）访问并登录 Google Cloud：https://console.cloud.google.com/projectselector2/auth/clients?hl=zh-cn&supportedpurview=project。

（2）点击创建项目，并填写项目名称。

![img.png](_txtdbpic/99f79a1f691ef4d432a865cf7fc431eb_MD5.png)

（3）配置 Google Auth Platform，受众群体选择外部。

![img.png](_txtdbpic/40cbc61380f2c9ab2dc9f4fbfc5fbe7d_MD5.png)

（4）创建 OAuth 客户端，应用类型选择 Web应用，添加重定向地址 [https://localhost:8080](https://localhost:8080/)，创建。

![img.png](_txtdbpic/d06eff2b00c2f819b5eebb4b618b8e75_MD5.png)

（5）复制对应的客户端 ID 以及客户端密钥。

![img.png](_txtdbpic/c81c0095365aa6b11344fcf14d68551f_MD5.png)

（6）发布应用

![img.png](_txtdbpic/d05da3a953a3f98d3433924f05a0565c_MD5.png)

（7）启用 google drive API

![img.png](_txtdbpic/7c19c4da99663a72dbdcefbfddab00fd_MD5.png)

（8）点击授权码的获取按钮，登陆谷歌账号，跳转至 1Panel 应用，完成登陆。

![img.png](_txtdbpic/529b16f459ba3a58dcf7f98c3939471f_MD5.png)

（9）完成授权后继续跳转，在浏览器地址中复制授权码（注意！这里只需要复制 code 的值），粘贴复制的授权码到授权码输入框中，修改备份目录后点击确认即可

![img.png](_txtdbpic/f28a112d5c2d00db4018e18f8a624c43_MD5.png)

### 3.6 WebDAV 连接 AList[⚓︎](https://1panel.cn/docs/v2/user_manual/settings/#36-webdav-alist)

（1）从应用商店安装好 AList 后（记得打开端口外部访问），在容器日志中查看初始化密码，跳转到 AList 管理界面。

（2）存储 菜单中添加对应的存储，记住该路径。

![img.png](_txtdbpic/49b87857e505d291a05eab577917dc4a_MD5.png)

（3）1Panel 备份账号中，添加 WebDAV 类型的备份账号。地址参数填写 `${2步骤中的地址}/dav`，备份目录参数填写 `/${2步骤中的存储路径}/xxx`，如此处可以使用 `/tmp/sftp/1panel`，完成绑定。

![img.png](_txtdbpic/b1b70551c5fbfcdc52c72c3c22a7edc5_MD5.png)

### 3.7 部分对象存储服务商与亚马逊 S3 云存储的兼容性[⚓︎](https://1panel.cn/docs/v2/user_manual/settings/#37-s3)

| 服务商       | 文档                                                         | 兼容访问风格                      | 兼容性 |
| :----------- | :----------------------------------------------------------- | :-------------------------------- | :----- |
| 阿里云       | https://help.aliyun.com/document_detail/410748.html          | Virtual Hosted Style              | ✅      |
| 腾讯云       | https://cloud.tencent.com/document/product/436/41284         | Virtual Hosted Style / Path Style | ✅      |
| 七牛云       | https://developer.qiniu.com/kodo/4088/s3-access-domainname   | Virtual Hosted Style / Path Style | ✅      |
| 百度云       | https://cloud.baidu.com/doc/BOS/s/Fjwvyq9xo                  | Virtual Hosted Style / Path Style | ✅      |
| 京东云       | https://docs.jdcloud.com/cn/object-storage-service/api/regions-and-endpoints | Virtual Hosted Style              | ✅      |
| 金山云       | https://docs.ksyun.com/documents/6761                        | Virtual Hosted Style              | ✅      |
| 青云         | https://docsv3.qingcloud.com/storage/object-storage/s3/intro/ | Virtual Hosted Style / Path Style | ✅      |
| 网易数帆     | https://sf.163.com/help/documents/89796157866430464          | Virtual Hosted Style              | ✅      |
| Cloudflare   | Cloudflare S3 兼容性API https://developers.cloudflare.com/r2/data-access/s3-api/ | Virtual Hosted Style / Path Style | ✅      |
| Oracle Cloud | https://docs.oracle.com/en-us/iaas/Content/Object/Tasks/s3compatibleapi.htm | Virtual Hosted Style / Path Style | ✅      |
| 自建minio    | -                                                            | Path Style                        | ✅      |
| 又拍云       | [https://help.upyun.com/knowledge-base/aws-s3%E5%85%BC%E5%AE%B9/](https://help.upyun.com/knowledge-base/aws-s3兼容/) | Virtual Hosted Style / Path Style | ✅      |
| 华为云       | 文档未说明是否兼容，工单反馈不保证兼容性，实际测试可以使用   | Virtual Hosted Style              | ❓      |
| Ucloud       | 只支持 8MB 大小的分片，本插件暂不支持 https://docs.ucloud.cn/ufile/s3/s3_introduction | -                                 | ❌      |

## 4 快照[⚓︎](https://1panel.cn/docs/v2/user_manual/settings/#4)

快照用于全量备份 1Panel 所产生的数据，具体包括：

- Docker 配置文件，路径为 /etc/docker/daemon.json
- 应用商店应用，可在【应用商店 - 已安装】中查看
- 本地备份数据，可在【面板设置 - 备份账号】中查看
- 1Panel 产生的数据，将压缩整个 [安装目录]/1panel 目录，包括数据库文件
- 1panel 二进制文件，路径为 /usr/local/bin/1panel
- 1pctl 命令行工具，路径为 /usr/local/bin/1pctl
- 1panel.service 路径为 /etc/systemd/system/1panel.service

![img.png](_txtdbpic/63bd22bb4983ab1ba16c9fc4e42e30fe_MD5.png)

- 创建和同步快照只支持选择第三方账号
- 快照恢复过程中，将对恢复前数据进行备份，默认的备份路径为 [安装目录]/original_[快照名]
- 快照恢复失败后，可选择根据【面板日志 - 系统日志】排查失败原因后，重试恢复，或者直接回滚到恢复之前的版本
- 如果上述操作都不能使服务正常运行，则需要手动拿到恢复前的备份文件，手动替换当前系统数据，然后重启系统
- 如机器迁移等，需要将快照放到备份账号对应的指定目录下，如服务器磁盘：/opt/1panel/backup/system_snapshot/

## 5 许可证[⚓︎](https://1panel.cn/docs/v2/user_manual/settings/#5)

用于查看当前许可证状态，导入专业版许可证并成功激活后，可以使用专业版相关功能

[点击了解专业版更多信息](https://www.lxware.cn/1panel)

用户可以添加多个专业许可证，每个专业版许可证可以绑定一个节点将其激活为专业版节点，同时可以绑定多个社区版节点

![img.png](_txtdbpic/6093a86cd947cb78634a2b0cd3869254_MD5.png)

## 6 关于[⚓︎](https://1panel.cn/docs/v2/user_manual/settings/#6)

- 支持检查 1Panel 服务是否存在新版本，更新将替换 1panel 二进制文件、1pctl 命令行工具以及 1panel.service 文件
- 更新失败时，将回滚所有更新内容到更新前的状态，如更新后发现版本信息没有发生变化，则更新失败，可在【面板日志 - 系统日志】中查看失败原因，解决后重新完成更新操作

![img.png](_txtdbpic/6d842f10af9c7addd1e4ae89f94577a1_MD5.png)







# 使用 1Panel 可视化安装 OpenResty[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/openresty/#1panel-openresty)

**OpenResty** 是一个基于 Nginx 的高性能 Web 应用服务器，它将 Nginx 与 Lua 编程语言集成在一起，提供了强大的功能和灵活性。

## 1. 打开应用商店[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/openresty/#1)

进入 1Panel 控制台后，点击左侧菜单的 **「应用商店」**。

![image-20251016110510084](_txtdbpic/eeb13f4d4408b6065a4153b6566df73f_MD5.png)

## 2. 搜索 OpenResty 并安装[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/openresty/#2-openresty)

在右上角搜索框输入 **OpenResty**，点击应用卡片进入详情页，选择 **安装**。

![image-20251022205345484](_txtdbpic/b5947686e31e5b25249dadbef76968ca_MD5.png)

## 3. 配置安装参数[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/openresty/#3)

你可以根据需要选择：

- **名称**（输入框默认应用名称）
- **版本**（建议使用最新稳定版）
- **HTTP 端口**（默认 80，如果与现有服务冲突可调整）
- **HTTPS 端口**（默认 443，如果与现有服务冲突可调整）
- **网站目录**（默认网站目录会放置在 1Panel 安装目录下，如需修改请以绝对路径填写）

确认设置无误后，点击 **确定** 按钮开始安装。

![image-20251022205428034](_txtdbpic/73c5e848fb4b0b0628caa80bd5dc985d_MD5.png)

## 4. 查看运行状态[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/openresty/#4)

进入 **已安装** 页面，即可查看 OpenResty 的运行状态。你可以对应用执行以下操作：

- **重建**：重新创建应用
- **重启**：重启正在运行的应用
- **启动 / 停止**：启动或停止应用
- **卸载**：移除应用及其数据
- **查看参数**：查看应用启动配置
- **查看日志**：查看应用实时日志
- **进入容器终端**：在容器内执行命令
- **备份 / 恢复**：对应用数据进行备份和恢复

![image-20251022205720006](_txtdbpic/18be0ab84039308a8cce52f24eb19bbc_MD5.png)

## 5. 使用 OpenResty[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/openresty/#5-openresty)

进入 1Panel 左侧的 **网站** 菜单，即可创建新网站并使用 OpenResty 服务。

![image-20251022205757786](_txtdbpic/7b0c2b3d02a5b05b698ab39f72192e55_MD5.png)









# 使用 1Panel 可视化安装 MySQL[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/mysql/#1panel-mysql)

**MySQL** 是一个流行的开源关系型数据库管理系统（RDBMS），它提供了丰富的功能，适用于各种应用场景。

## 1. 打开应用商店[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/mysql/#1)

进入 1Panel 控制台后，点击左侧菜单的 **「应用商店」**。

![image-20251016110510084](_txtdbpic/eeb13f4d4408b6065a4153b6566df73f_MD5.png)

## 2. 搜索 MySQL 并安装[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/mysql/#2-mysql)

在右上角搜索框输入 **MySQL**，点击应用卡片进入详情页，选择 **安装**。

![image-20251016110903786](_txtdbpic/dc3485b635bdb3ecba8ad70a47f9db82_MD5.png)

## 3. 配置安装参数[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/mysql/#3)

你可以根据需要配置

- **名称**（输入框默认应用名称）
- **版本**（选择所需版本）
- **Root 密码**（默认随机生成）
- **端口**（默认 3306，如果与现有服务冲突可调整）
- **端口外部访问** （开启后，允许从外部网络连接到此数据库端口）

确认设置无误后，点击 **确认** 按钮开始安装。

![img](_txtdbpic/aea9a7dbc1b43df81e538115d419ab26_MD5.png)

等待安装完成即可

## 4. 创建 MySQL 数据库[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/mysql/#4-mysql)

安装完成后，点击左侧菜单的 **「数据库」**。

![image-20251016112506720](_txtdbpic/04f253ad546d5b0cca60eac95e68045e_MD5.png)

选择 **创建数据库** 根据需要修改相关信息

- **名称**（数据库名称）
- **用户名**（根据实际需求设置）
- **密码**（默认随机生成）
- **权限**（可选所有人或指定IP） 确认配置无误后，点击 **确认** 按钮开始创建。

![image-20251016113634840](_txtdbpic/4e28b7609003c13b1674a79924a05f3a_MD5.png)

## 5. 连接 MySQL 数据库[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/mysql/#5-mysql)

获取数据库配置信息

![image-20251016114303123](_txtdbpic/75d9b1be1a8204b2fa492c5850d44d04_MD5.png)

使用本地工具连接数据库

![image-20251016114547646](_txtdbpic/7853964cf6297ec0093953a341886828_MD5.png)







# 使用 1Panel 可视化安装 Redis[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/redis/#1panel-redis)

**Redis** 是一种开源的内存数据库，通常用作缓存系统或键值存储数据库。

## 1. 打开应用商店[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/redis/#1)

进入 1Panel 控制台后，点击左侧菜单的 **「应用商店」**。

![image-20251016110510084](_txtdbpic/eeb13f4d4408b6065a4153b6566df73f_MD5.png)

## 2. 搜索 Redis 并安装[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/redis/#2-redis)

在右上角搜索框输入 **Redis**，选择第一个，点击应用卡片进入详情页，选择 **安装**。

![image-20251016141645215](_txtdbpic/fa7ec5e1076cc9388b8ae4149f017871_MD5.png)

## 3. 配置安装参数[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/redis/#3)

你可以根据需要配置

- **名称**(输入框默认应用名称)
- **版本**(选择所需版本)
- **Root 密码**(默认随机生成)
- **端口**(默认 6379，如果与现有服务冲突可调整)
- **端口外部访问** (开启后，允许从外部网络连接到此数据库端口)

确认设置无误后，点击 **确认** 按钮开始安装。

![image-20251016141905753](_txtdbpic/064840e1106a2e269379d1afde52e9e8_MD5.png)

等待安装完成即可

## 4. 连接 Redis 数据库[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/redis/#4-redis)

点击左侧菜单的 **「数据库」** 选择Redis，即可输入命令

![image-20251016142801288](_txtdbpic/4700c18a4fcbcda3017583c14329c257_MD5.png)

使用工具进行连接。点击 **连接信息** 获取连接配置

![image-20251016143234658](_txtdbpic/fe07c9dac80ca469b3815a3a90d37cec_MD5.png)

本地输入连接信息进行连接

![image-20251016144637758](_txtdbpic/09aaa00e126fb785c5fe6dbf53f6c548_MD5.png)







# 使用 1Panel 可视化安装 AList[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/alist/#1panel-alist)

**AList** 是一个支持多种存储，支持网页浏览和 WebDAV 的文件列表程序，由 gin 和 Solidjs 驱动。

## 1. 打开应用商店[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/alist/#1)

进入 1Panel 控制台后，点击左侧菜单的 **「应用商店」**。

![image-20251016110510084](_txtdbpic/eeb13f4d4408b6065a4153b6566df73f_MD5.png)

## 2. 搜索 AList 并安装[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/alist/#2-alist)

在右上角搜索框输入 **AList**，点击应用卡片进入详情页，选择 **安装**。

![image-20251017093725067](_txtdbpic/c2455eb26434711a5479f43cab476c9a_MD5.png)

## 3. 配置安装参数[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/alist/#3)

你可以根据需要配置

- **名称** (输入框内可自定义应用名称，默认为 alist)
- **版本** (下拉选择所需的 AList 版本)
- **WebUI 端口** (Web 管理界面的访问端口，默认为 5244)
- **S3 端口** (S3 服务的访问端口，默认为 5246)
- **端口外部访问** (开启后，将允许从外部网络访问此应用端口)

确认设置无误后，点击 **确认** 按钮开始安装。

![image-20251017095132628](_txtdbpic/0c7467d73c429c7bd5fcb9de193477b9_MD5.png)

等待安装完成即可

## 4. 配置访问 AList 服务[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/alist/#4-alist)

安装完成后，确认 1Panel 配置默认访问地址，已配置过可忽略

![image-20251016172322315](_txtdbpic/6d62d3f0ed66130c9ceb43c5373908dd_MD5.png)

点击左侧菜单的 **容器** ，找到 AList 容器，点击终端

![image-20251017101043569](_txtdbpic/32007ae5a6843998740fd0b27c0324bd_MD5.png)

连接终端，生成密码，可选两种方式

- **生成随机密码**：./alist admin random
- **手动设置密码**：./alist admin set NEW_PASSWORD

![image-20251017101434307](_txtdbpic/696505d080d2df2f1b090b3cf521bc1a_MD5.png)

返回应用商店，点击 **跳转** 即可访问 AList 服务

![image-20251017101728523](_txtdbpic/8c6ef69853d08e9e90b2ac6f0074a1db_MD5.png)

输入生成的密码即可

![image-20251017101943414](_txtdbpic/a7c50305b2a108547fab2c32cdbc8e1c_MD5.png)









# 使用 1Panel 可视化安装 WordPress[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/wordpress/#1panel-wordpress)

**WordPress** 是一款广泛使用的开源内容管理系统（CMS），用于创建和管理网站和博客。

## 1. 打开应用商店[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/wordpress/#1)

进入 1Panel 控制台后，点击左侧菜单的 **「应用商店」**。

![image-20251016110510084](_txtdbpic/eeb13f4d4408b6065a4153b6566df73f_MD5.png)

## 2. 搜索 WordPress 并安装[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/wordpress/#2-wordpress)

在右上角搜索框输入 **WordPress**，点击应用卡片进入详情页，选择 **安装**。

![image-20251017154851362](_txtdbpic/a5a7b6a945cf512225ec966b3f3ea4a3_MD5.png)

## 3. 配置安装参数[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/wordpress/#3)

你可以根据需要配置，这里需要配置数据库服务

- **名称** (输入框内可自定义应用名称，默认为 wordpress)
- **版本** (下拉选择所需的 WordPress 版本)
- **数据库服务** (选择用于存储数据的 MySQL 服务)
- **数据库名** (为应用创建的数据库名称)
- **数据库用户** (用于连接数据库的用户名)
- **数据库密码** (数据库用户的密码)
- **端口** (应用的访问端口，默认为 8080)
- **端口外部访问** (开启后，将允许从外部网络访问此应用端口)

确认设置无误后，点击 **确认** 按钮开始安装。

![image-20251017155548615](_txtdbpic/6a0fd9c8e74affa59d5acd04740a8154_MD5.png)

等待安装完成即可

## 4. 访问 WordPress 服务[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/wordpress/#4-wordpress)

配置默认访问地址，已配置则忽略此步骤

![image-20251016172322315](_txtdbpic/6d62d3f0ed66130c9ceb43c5373908dd_MD5.png)

返回应用商店，点击 **跳转** 即可访问 WordPress 服务

![image-20251017155825666](_txtdbpic/4d5875a21fc56e9cd4c7bce95c630a39_MD5.png)

设置配置信息，完成初始化

![image-20251017155933483](_txtdbpic/b321915f8cca348878e50dfaf7778a3d_MD5.png)

输入用户名密码登录，即可使用

![image-20251017160433777](_txtdbpic/6e02a97cac8ba89acca0472c6814ddb3_MD5.png)







# 使用 1Panel 可视化安装 phpMyAdmin[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/phpmyadmin/#1panel-phpmyadmin)

**phpMyAdmin** 是一个开源的基于Web的MySQL数据库管理工具，它允许用户通过Web浏览器管理MySQL数据库。

## 1. 打开应用商店[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/phpmyadmin/#1)

进入 1Panel 控制台后，点击左侧菜单的 **「应用商店」**。

![image-20251016110510084](_txtdbpic/eeb13f4d4408b6065a4153b6566df73f_MD5.png)

## 2. 搜索 phpMyAdmin 并安装[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/phpmyadmin/#2-phpmyadmin)

在右上角搜索框输入 **phpMyAdmin**，点击应用卡片进入详情页，选择 **安装**。

![image-20251016175101288](_txtdbpic/c43a644c937ce17a0b86cff82ae17bdb_MD5.png)

## 3. 配置安装参数[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/phpmyadmin/#3)

你可以根据需要配置

- **名称** (输入框内可自定义应用名称，默认为 phpmyadmin)
- **版本** (下拉选择所需的 phpMyAdmin 版本)
- **端口** (应用的访问端口，默认为 8089)
- **端口外部访问** (开启后，将允许从外部网络访问此应用端口)

确认设置无误后，点击 **确认** 按钮开始安装。

![image-20251016175326474](_txtdbpic/fe394ad58e0f9bc81690711e4ccb89f3_MD5.png)

等待安装完成即可

## 4. 访问 phpMyAdmin 服务[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/phpmyadmin/#4-phpmyadmin)

安装完成后，确认 1Panel 配置默认访问地址

![image-20251016172322315](_txtdbpic/6d62d3f0ed66130c9ceb43c5373908dd_MD5.png)

返回应用商店，点击 **跳转** 即可访问 phpMyAdmin 服务

![image-20251016175944497](_txtdbpic/c7b81c7e4c6ce2c5ae8c4f16c2032376_MD5.png)

输入需要管理的数据库信息即可

![image-20251016180107079](_txtdbpic/799b78e89f4557a979a9a5d23fd40512_MD5.png)









# 使用 1Panel 可视化安装 Ollama[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/ollama/#1panel-ollama)

**Ollama** 是一个开源的大型语言模型服务，提供了类似 OpenAI 的 API 接口和聊天界面，可以非常方便地部署最新版本的 GPT 模型并通过接口使用。支持热加载模型文件，无需重新启动即可切换不同的模型。

## 1. 打开应用商店[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/ollama/#1)

进入 1Panel 控制台后，点击左侧菜单的 **「应用商店」**。

![image-20251016110510084](_txtdbpic/eeb13f4d4408b6065a4153b6566df73f_MD5.png)

## 2. 搜索 Ollama 并安装[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/ollama/#2-ollama)

在右上角搜索框输入 **Ollama**，点击应用卡片进入详情页，选择 **安装**。

![image-20251017163039229](_txtdbpic/2df0b489b6f169ac5267dbf6a627e190_MD5.png)

## 3. 配置安装参数[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/ollama/#3)

你可以根据需要配置

- **名称** (输入框内可自定义应用名称，默认为 ollama)
- **版本** (下拉选择所需的 Ollama 版本)
- **端口** (应用的访问端口，默认为 11434)
- **端口外部访问** (开启后，将允许从外部网络访问此应用端口)

确认设置无误后，点击 **确认** 按钮开始安装。

![image-20251017163107970](_txtdbpic/70eed2de6791267d8152ee72e7931531_MD5.png)

等待安装完成即可

## 4. 访问 Ollama 服务[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/ollama/#4-ollama)

配置默认访问地址，已配置则忽略此步骤

![image-20251016172322315](_txtdbpic/6d62d3f0ed66130c9ceb43c5373908dd_MD5.png)

返回应用商店，点击 **跳转** 即可访问 Ollama 服务

![image-20251017171351530](_txtdbpic/fe94e1f52dd9f4d608cab3d34bfbde16_MD5.png)

访问页面，可以看到 `Ollama is running` 表示搭建成功

![image-20251017171445095](_txtdbpic/6b7d5a58f5527575e247a728de8192e2_MD5.png)

点击 **终端** 连接ollama，使用命令控制

![image-20251017171937567](_txtdbpic/faa9ab1ee4087fd550c644c2bf5b4817_MD5.png)







# 使用 1Panel 可视化安装 frp[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/frp/#1panel-frp)

**frp（Fast Reverse Proxy）** 是一款开源的高性能反向代理工具，它允许您在不同网络之间建立安全的通信通道，用于实现端口映射、内网穿透和远程访问等多种网络连接需求。

## 1. 打开应用商店[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/frp/#1)

进入 1Panel 控制台后，点击左侧菜单的 **「应用商店」**。

![image-20251016110510084](_txtdbpic/eeb13f4d4408b6065a4153b6566df73f_MD5.png)

## 2. 搜索 frp 并安装[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/frp/#2-frp)

在右上角搜索框输入 **frp**，点击应用卡片进入详情页，选择 **安装**。

![image-20251022210133411](_txtdbpic/d3ac7ae9611b1a41fdfbaba92a84d17f_MD5.png)

## 3. 配置安装参数[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/frp/#3)

你可以根据需要配置

- **名称** (输入框内可自定义应用名称，默认为 frps)
- **版本** (下拉选择所需的 frp 版本)
- **服务端口** (frp 服务端用于与客户端通信的端口，默认为 7000)
- **Dashboard 端口** (WebUI 管理界面的访问端口，默认为 7500)
- **用户名** (Dashboard 登录用户名，默认为 admin)
- **密码** (Dashboard 登录密码)
- **密钥** (用于 frps 和 frpc 之间通信认证的令牌)

确认设置无误后，点击 **确认** 按钮开始安装。

![image-20251022210239559](_txtdbpic/89609d0056dbb7fc4813d8c8a7a8f657_MD5.png)

等待安装完成即可

## 4. 访问 frp 服务[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/frp/#4-frp)

配置默认访问地址，已配置则忽略此步骤

![image-20251016172322315](_txtdbpic/6d62d3f0ed66130c9ceb43c5373908dd_MD5.png)

返回应用商店，点击 **跳转** 即可访问 frp web 服务

![image-20251022210650881](_txtdbpic/c92673623e35ecd4815ee6c5f85a3df8_MD5.png)

输入账户密码即可

![image-20251022210723926](_txtdbpic/6da9d38dc8709c656bdc457e67e1e2a2_MD5.png)

如需修改配置，首先进入安装目录

![image-20251022210836670](_txtdbpic/e381265511db62688333093378a70db4_MD5.png)

修改frp配置文件即可

![image-20251022210951332](_txtdbpic/9900da3237c1eafe8ebfc2da477599d5_MD5.png)







# 使用 1Panel 可视化安装 ddns-go[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/ddns-go/#1panel-ddns-go)

**ddns-go** 是一个自动获得你的公网 IPv4 或 IPv6 地址，并解析到对应的域名服务。

## 1. 打开应用商店[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/ddns-go/#1)

进入 1Panel 控制台后，点击左侧菜单的 **「应用商店」**。

![image-20251016110510084](_txtdbpic/eeb13f4d4408b6065a4153b6566df73f_MD5.png)

## 2. 搜索 ddns-go 并安装[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/ddns-go/#2-ddns-go)

在右上角搜索框输入 **ddns-go**，点击应用卡片进入详情页，选择 **安装**。

![image-20251020154143141](_txtdbpic/e8b7f8d8e64471d9c0174a37aa63ec0d_MD5.png)

## 3. 配置安装参数[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/ddns-go/#3)

你可以根据需要配置

- **名称** (输入框内可自定义应用名称，默认为 ddns-go)
- **版本** (下拉选择所需的 ddns-go 版本)
- **网页端口** (WebUI 的访问端口，默认为 9876)

确认设置无误后，点击 **确认** 按钮开始安装。

![image-20251020155257247](_txtdbpic/9c7a5ad0c4b2a49e9081d99afb1e0cf5_MD5.png)

等待安装完成即可

## 4. 配置访问 ddns-go 服务[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/ddns-go/#4-ddns-go)

安装完成后，确认 1Panel 配置默认访问地址，已配置过可忽略

![image-20251016172322315](_txtdbpic/6d62d3f0ed66130c9ceb43c5373908dd_MD5.png)

返回应用商店，点击 **跳转** 即可访问 ddns-go 服务

![image-20251020154839215](_txtdbpic/97c4b42e4857d73f4ab2ebfc310ef262_MD5.png)

首次登录需配置管理员账号

![image-20251020154950622](_txtdbpic/c08de0a7a0dd31cc85cec6236593991a_MD5.png)







# 使用 1Panel 可视化安装 RustDesk[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/rustdesk/#1panel-rustdesk)

**RustDesk** 是一款开源的远程支持和远程桌面工具，它旨在为用户提供便捷的远程协助和远程访问功能。

## 1. 打开应用商店[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/rustdesk/#1)

进入 1Panel 控制台后，点击左侧菜单的 **「应用商店」**。

![image-20251016110510084](_txtdbpic/eeb13f4d4408b6065a4153b6566df73f_MD5.png)

## 2. 搜索 RustDesk 并安装[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/rustdesk/#2-rustdesk)

在右上角搜索框输入 **RustDesk**，点击应用卡片进入详情页，选择 **安装**。

![image-20251021135819982](_txtdbpic/376c3cc13bbb049d9d530ff69250de52_MD5.png)

## 3. 配置安装参数[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/rustdesk/#3)

你可以根据需要配置

- **名称** (输入框内可自定义应用名称，默认为 rustdesk)
- **版本** (下拉选择所需的 RustDesk 版本)
- **NAT 类型测试端口** (默认为 21115)
- **hbbs 端口(配合中继服务器使用)** (默认为 21116)
- **hbbr 端口(客户-客户端中继服务器端口)** (默认为 21117)
- **网页客户端端口 1** (默认为 21118)
- **网页客户端端口 2** (默认为 21119)
- **IP 地址或域名(必填)** (填写服务器的公网 IP 地址或域名)
- **端口外部访问** (开启后，将允许从外部网络访问此应用端口)

确认设置无误后，点击 **确认** 按钮开始安装。

![image-20251021140057677](_txtdbpic/b792ff97dcab53124bb0d49885f52cf8_MD5.png)

等待安装完成即可

## 4. 配置 RustDesk 并使用[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/rustdesk/#4-rustdesk)

点击参数获取配置信息

![image-20251021142500835](_txtdbpic/6b90477f364f63b5476b2cb041788a94_MD5.png)

进入安装目录

![image-20251021142617880](_txtdbpic/ce601abbcdcad9bf8644a9c5e6256c74_MD5.png)

根据找到对应的 pub 文件，获取key

![image-20251021142841367](_txtdbpic/dee0cccb374298ce7dbb05099a5ad71e_MD5.png)

下载客户端https://github.com/rustdesk/rustdesk/releases，下载后，打开客户端，进入设置选择中继服务器

![image-20251021141554097](_txtdbpic/158f9ba082d75c52f0545388a5642ea4_MD5.png)

填入对应的信息

![image-20251021142939475](_txtdbpic/6b40f42c09059c50588437af00985e91_MD5.png)

在另外一台主机的客户端，也填入相同的信息，输入连接信息远程连接即可

![image-20251021143340226](_txtdbpic/62269cdcbffcf8683781945574603b1e_MD5.png)







# 使用 1Panel 可视化安装 MinIO[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/minio/#1panel-minio)

**MinIO** 是根据 GNU Affero 通用公共许可证 v3.0 发布的高性能对象存储。它与 Amazon S3 云存储服务 API 兼容。使用 MinIO 为机器学习、分析和应用程序数据工作负载构建高性能基础架构。

## 1. 打开应用商店[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/minio/#1)

进入 1Panel 控制台后，点击左侧菜单的 **「应用商店」**。

![image-20251016110510084](_txtdbpic/eeb13f4d4408b6065a4153b6566df73f_MD5.png)

## 2. 搜索 MinIO 并安装[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/minio/#2-minio)

在右上角搜索框输入 **MinIO**，点击应用卡片进入详情页，选择 **安装**。

![image-20251016165333807](_txtdbpic/1924103691de18d195eb121bbb9379d4_MD5.png)

## 3. 配置安装参数[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/minio/#3)

你可以根据需要配置

- **名称**（输入框内可自定义应用名称，默认为 minio）
- **版本**（下拉选择所需的 MinIO 版本）
- **用户**（用于登录的用户名，默认随机生成）
- **密码**（设置用于登录的密码）
- **端口**（WebUI 的访问端口，默认为 9001）
- **API 端口**（S3 API 的访问端口，默认为 9000）
- **会话持续时间**（WebUI 登录会话的有效时长，默认为 12h）
- **启用 WebUI**（选择是否开启 MinIO 的网页管理界面）
- **WebUI 登录动画**（选择是否在登录页面启用动画效果）
- **端口外部访问**（开启后，将允许从外部网络访问此应用端口）

确认设置无误后，点击 **确认** 按钮开始安装。

![image-20251016170535427](_txtdbpic/ad454c2474d8d40bfda0298eebe06d4d_MD5.png)

等待安装完成即可

## 4. 访问 MinIO 服务[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/minio/#4-minio)

安装完成后，获取 MinIO 配置信息，点击 **已安装** 选择 **参数**

![image-20251016171810134](_txtdbpic/ad6d47ef15ad7b2a6a825aa9493dbe4c_MD5.png)

得到配置信息

![image-20251016172011132](_txtdbpic/1f8edb77b5f1337ef618c34a62e0e2fe_MD5.png)

配置默认访问地址

![image-20251016172322315](_txtdbpic/6d62d3f0ed66130c9ceb43c5373908dd_MD5.png)

返回应用商店，点击 **跳转** 即可访问 MinIO 服务

![image-20251016172526853](_txtdbpic/3ed58e6c1cc69c0ef6b15d253144bbdc_MD5.png)

输入上面得到的 **用户名和密码** ，进入 **MinIO Web 服务**

![image-20251016173115776](_txtdbpic/b1be418cdb8a13b278def9f981ab3c58_MD5.png)







# 使用 1Panel 可视化安装 Bitwarden[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/bitwarden/#1panel-bitwarden)

**Bitwarden** 是一款开源的密码管理器，提供强大的安全性和便捷的密码管理功能。本仓库使用的是 Bitwarden 客户端 API 的替代服务器实现，使用 Rust 编写，与官方 Bitwarden 客户端兼容，非常适合自托管部署，因为在这种情况下运行官方资源繁重的服务可能并不理想。部署服务端后，用户仍然可以使用 Bitwarden 的官方 APP 和浏览器拓展使用兼容的 API 服务。

## 1. 打开应用商店[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/bitwarden/#1)

进入 1Panel 控制台后，点击左侧菜单的 **「应用商店」**。

![image-20251016110510084](_txtdbpic/eeb13f4d4408b6065a4153b6566df73f_MD5.png)

## 2. 搜索 Bitwarden 并安装[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/bitwarden/#2-bitwarden)

在右上角搜索框输入 **Bitwarden**，点击应用卡片进入详情页，选择 **安装**。

![image-20251020154143141](_txtdbpic/afcb74d86c6b347fe281caebd996b59d_MD5.png)

## 3. 配置安装参数[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/bitwarden/#3)

你可以根据需要配置

- **名称** (输入框内可自定义应用名称，默认为 bitwarden)
- **版本** (下拉选择所需的 Bitwarden 版本)
- **端口** (应用的访问端口，默认为 40031)
- **端口外部访问** (开启后，将允许从外部网络访问此应用端口)

确认设置无误后，点击 **确认** 按钮开始安装。

![image-20251020154143141](_txtdbpic/f4f9303d5c9f3805d7823818ee7d998d_MD5.png)

等待安装完成即可

## 4. 配置 Bitwarden SSL 访问[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/bitwarden/#4-bitwarden-ssl)

注意 Bitwarden 需要配置 SSL证书访问，直接访问会一直转圈

![image-20251021103933402](_txtdbpic/92366ea0db2cfc13eafa02fddd577ec9_MD5.png)

点击左侧菜单的网站，选择创建网站

![image-20251021104405151](_txtdbpic/bb60c48dd7105e08ec97c59614d55f94_MD5.png)

点击反向代理

![image-20251021104522152](_txtdbpic/0d697bc875f9d3c87d1cba9e9b6493cd_MD5.png)

输入反向代理后的域名和端口，应用选择 Bitwarden，点击确认

![image-20251021111122113](_txtdbpic/78b7c3010293c0c14a012f93a78d522e_MD5.png)

网站创建成功后，点击配置

![image-20251021110218133](_txtdbpic/d9888ed4c53697bf56aab97df01cf091_MD5.png)

左侧选择 HTTPS ，启用 HTTPS

![image-20251021110452921](_txtdbpic/52c77a8a5f6325fe400b18fbf1c653a3_MD5.png)

导入你的证书，或者选择已有证书，配置好后点击保存即可

![image-20251021110637134](_txtdbpic/a9e963592ef1468f1c0275f16339236d_MD5.png)

## 5. 访问 Bitwarden 服务[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/bitwarden/#5-bitwarden)

访问反向代理的域名和端口地址即可

![image-20251021112440459](_txtdbpic/7c2173885566dc54c05d9945ca29344a_MD5.png)









# 使用 1Panel 可视化安装 MongoDB[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/mongodb/#1panel-mongodb)

**MongoDB** 是一款流行的NoSQL数据库管理系统，它提供了许多功能，使其成为处理大规模数据和灵活的数据模型的强大工具。

## 1. 打开应用商店[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/mongodb/#1)

进入 1Panel 控制台后，点击左侧菜单的 **「应用商店」**。

![image-20251016110510084](_txtdbpic/eeb13f4d4408b6065a4153b6566df73f_MD5.png)

## 2. 搜索 MongoDB 并安装[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/mongodb/#2-mongodb)

在右上角搜索框输入 **MongoDB**，点击应用卡片进入详情页，选择 **安装**。

![image-20251016155319717](_txtdbpic/dd4fcea23f690571c8356755ee511154_MD5.png)

## 3. 配置安装参数[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/mongodb/#3)

你可以根据需要配置

- **名称**（输入框默认应用名称）
- **版本**（选择所需版本）
- **用户名**（默认随机生成）
- **端口**（默认 27017，如果与现有服务冲突可调整）
- **端口外部访问** （开启后，允许从外部网络连接到此数据库端口）

确认设置无误后，点击 **确认** 按钮开始安装。

![image-20251016155828329](_txtdbpic/0f84da1cc60b96075d7dabd229550028_MD5.png)

等待安装完成即可

## 4. 连接 MongoDB 数据库[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/mongodb/#4-mongodb)

安装完成后，获取 MongoDB 配置信息，点击 **已安装** 选择 **参数**

![image-20251016162420157](_txtdbpic/000331a062ae1902ccbd487609fd1d93_MD5.png)

得到配置信息

![image-20251016162604193](_txtdbpic/b704f82d1f25242e1744ea8a6cd2fb07_MD5.png)

使用本地工具连接 MongoDB

![image-20251016162737239](_txtdbpic/feb638705e52649092713d8adcc598a0_MD5.png)







# 使用 1Panel 可视化安装 Nextcloud[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/nextcloud/#1panel-nextcloud)

**Nextcloud** 是一款开源的自托管云存储和协作平台，它提供了一系列功能，旨在帮助您管理和共享文件、日历、联系人、任务等，同时保护您的数据隐私。

## 1. 打开应用商店[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/nextcloud/#1)

进入 1Panel 控制台后，点击左侧菜单的 **「应用商店」**。

![image-20251016110510084](_txtdbpic/eeb13f4d4408b6065a4153b6566df73f_MD5.png)

## 2. 搜索 Nextcloud 并安装[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/nextcloud/#2-nextcloud)

在右上角搜索框输入 **Nextcloud**，点击应用卡片进入详情页，选择 **安装**。

![image-20251017113630514](_txtdbpic/a792d1bfadbac0e6e37f285f6697a140_MD5.png)

## 3. 配置安装参数[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/nextcloud/#3)

你可以根据需要配置

- **名称** (输入框内可自定义应用名称，默认为 nextcloud)
- **版本** (下拉选择所需的 Nextcloud 版本)
- **端口** (应用的访问端口，默认为 40069)
- **时区** (设置容器运行时区，默认为 Asia/Shanghai)
- **端口外部访问** (开启后，将允许从外部网络访问此应用端口)

确认设置无误后，点击 **确认** 按钮开始安装。

![image-20251017133618550](_txtdbpic/466e81d24895c85e603a6664aa0904bf_MD5.png)

等待安装完成即可

## 4. 访问 Nextcloud 服务[⚓︎](https://1panel.cn/docs/v2/user_manual/appstore/nextcloud/#4-nextcloud)

默认端口为 443，因此初次访问时，需要在浏览器地址栏使用 `https://IP:端口` 的格式

![image-20251017134623486](_txtdbpic/a0268579c52e43c019e583b83cc56a1b_MD5.png)

可以在 **容器** 页面点击 **编辑** 修改端口配置

![image-20251017134941753](_txtdbpic/422126acf3637cf34df9c1716a340254_MD5.png)

修改为 80 端口即可

![image-20251017135035543](_txtdbpic/2f6d859da6a6b1636db18f93f79c5980_MD5.png)







