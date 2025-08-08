# 简介 [](https://docs.nextcloud.com/server/latest/admin_manual/#introduction "Link to this heading")

欢迎来到 Nextcloud 服务器管理指南。本指南描述了 Nextcloud 的管理任务，Nextcloud 是一个灵活的开源文件同步和共享解决方案。Nextcloud 包括运行在 Linux 上的 Nextcloud 服务器，适用于 Microsoft Windows、macOS 和 Linux 的客户端应用程序，以及适用于 Android 和 iOS 操作系统的移动客户端。

当前版本的 Nextcloud 手册始终在线可用： [docs.nextcloud.com](docs.nextcloud.com)。

Nextcloud 服务器是：

- 一个免费的、功能齐全的企业级社区支持服务器，具备所有企业功能。
  
- 或者提供完整的企业支持，包括电话和电子邮件联系 Nextcloud 开发人员。
  

## 视频和博客 [](https://docs.nextcloud.com/server/latest/admin_manual/#videos-and-blogs "Link to this heading")

参见[官方 Nextcloud 频道](https://www.youtube.com/c/Nextcloud) 在 YouTube 上观看教程、概览和会议视频。

访问[我们的博客](https://nextcloud.com/news/)获取最新资讯，并了解 Nextcloud 及其周边动态的最新情况。

## 目标受众 [](https://docs.nextcloud.com/server/latest/admin_manual/#target-audience "Link to this heading")

本指南适用于希望安装、管理和优化 Nextcloud 服务器的用户。如需了解 Nextcloud 网页用户界面以及桌面和移动客户端的相关信息，请参阅各自的手册：

- [Nextcloud 用户手册](https://docs.nextcloud.com/server/latest/user_manual/en/)
  
- [Nextcloud 桌面客户端](https://docs.nextcloud.com/desktop/latest/)
  



# 维护和发布计划 [](https://docs.nextcloud.com/server/latest/admin_manual/release_schedule.html#maintenance-and-release-schedule)

## 概述 [](https://docs.nextcloud.com/server/latest/admin_manual/release_schedule.html#overview)

Nextcloud 每年发布多个主要版本，但会通过“轻量级”维护更新为每个主要版本提供一年的完整支持（并定期回退适用的安全和错误修复）。这允许保持高频率的开发节奏，同时仍给管理员在规划部署、升级和维护活动时提供灵活性。

一个详细的未来主要版本和维护版本发布的时间表（以及生命周期结束预测）会定期更新，以方便规划部署、测试和升级。

无论您是希望使用最新功能和优化、希望参与测试，还是只想等到一切准备就绪再部署，您都有多种选择，可以决定首先部署哪个版本的 Nextcloud 服务器以及进行主要升级的频率。

危险

我们始终建议尽快安装最新的**维护**版本，无论您使用的是 Nextcloud 服务器的哪个主要版本。我们还强烈建议尽快从**生命周期结束**的版本进行升级。

提示

延长维护和支持可通过 Nextcloud 开发者通过 Nextcloud GmbH 提供的企业支持订阅选项获得。

## 发行类型 [](https://docs.nextcloud.com/server/latest/admin_manual/release_schedule.html#release-types)

Nextcloud 在默认发布渠道中有两种类型的发布：

1. 主要发布
2. 维护发布

**主要**版本的 Nextcloud 服务器（例如 `28.X.X`）会引入新的功能和功能。

每次主要版本发布后，都会通过定期的维护版本支持一年（例如，`X.X.4`），以修复关键错误和安全漏洞。

### 主要版本 [](https://docs.nextcloud.com/server/latest/admin_manual/release_schedule.html#major-releases)

主要版本通常会引入新功能，还经常包括一些“幕后”的更改。这些更改可能是相当广泛的。

具体的主要版本由版本字符串的第一部分表示。例如，Nextcloud Server `28.0.4` 是主要版本 `28`。而 `27.1.7` 是主要版本 `27`。

提示

版本号最高的主要版本提供了最新的功能。而版本号最低的主要版本则在实际应用中使用时间更长。

注意

在更新器提供新的主要版本之前，您可能需要满足新的系统要求。即使更新器提供了新的主要版本，也可能存在更新器无法完全检查的其他更改。我们会在《管理员手册》的每个新版本中，在《发布说明》章节的“关键变更”部分突出显示这些内容。

警告

应用程序通常根据其支持的 Nextcloud 服务器的主要版本来定义其兼容性。在选择部署哪个主要版本或决定升级到新可用的主要版本之前，请考虑您最常用和最重要的应用程序与 Nextcloud 服务器的潜在主要版本的兼容性。此外，由于许多应用程序是由社区提供的，并由志愿者维护，您可能希望提供测试应用程序与新的主要版本的 Nextcloud（或如果可能的话，对其进行调整），以鼓励更快（或更高质量）的发布。

### 维护版本 [](https://docs.nextcloud.com/server/latest/admin_manual/release_schedule.html#maintenance-releases)

维护版本特意不引入新的功能或破坏性更改。这旨在减少部署更新所伴随的风险和影响，以便能够快速且常规地解决关键错误或安全漏洞。

维护版本会在所有尚未达到生命周期结束状态的主要稳定版本中同时发布。

这些版本不应引起应用程序兼容性问题，也不应引入需要重新培训最终用户的更改。

特定的维护版本由版本号的最后一部分表示。例如，`28.0.4` 是 Nextcloud 服务器 28 版本的第四个维护版本。它包含了自上次维护版本（例如这里的 `28.0.3`）以来修复的所有关键错误和安全漏洞。

注意

所有关键的错误修复，包括安全相关的修复，都会回退到所有维护的主要版本中。

## 发布计划

Nextcloud Server 的新主要版本大约每 16 周发布一次。

新的**维护**版本大约每四周发布一次。

### 支持周期（“维护”）[](https://docs.nextcloud.com/server/latest/admin_manual/release_schedule.html#length-of-support-maintenance)

我们的发布计划意味着多个主要版本（例如 26.X.X、27.X.X、28.X.X）将同时受到支持。每当修复了一个关键错误或漏洞，如果影响了多个主要版本，它将被 **回退** 到所有适用的主要版本，并在下一个维护版本中发布（例如 `28.0.3` -> `28.0.4`）。任何尚未达到生命周期结束状态的主要版本都会收到这些维护更新。

这种重叠的计划和可预测的节奏既允许快速开发，又使管理员能够看到关键错误修复，同时在升级到新主要版本的频率上具有灵活性。

注意

由于每次主要版本发布后都会支持一年，因此要保持最新，您只需安装发布的维护版本，并在当前版本到达生命周期结束时升级到更高版本即可。由于维护版本只会为您的服务器打上最新的漏洞和安全问题修复补丁——而不引入其他重要更改——因此升级到新维护版本的风险远小于升级到新主要版本。

### 生命周期结束 [](https://docs.nextcloud.com/server/latest/admin_manual/release_schedule.html#end-of-life)

生命周期结束状态意味着不再提供支持/维护。主要版本在初始发布一周年纪念日后将不再发布维护版本。主要版本将进入生命周期结束状态，并且将不再接收任何进一步的错误修复或安全漏洞修正。

注意

Nextcloud 开发者通过 Nextcloud GmbH 提供的企业订阅服务可以延长主要版本的支持。

所有主要版本的生命周期结束日期会提前公布，以便于规划。

注意

只要主要版本仍然在维护计划中列为“当前维护”状态，您就可以期望收到所有相关的关键错误修复或安全漏洞修正（即使这些修正最初是为较新的主要版本提供的，只要它们对当前仍受支持的较早版本仍然相关）。

## 安装版本 [](https://docs.nextcloud.com/server/latest/admin_manual/release_schedule.html#installation-version)

由于一年中会发布多个主要版本，并且每个版本都会得到一年的支持，期间会修复任何相关的错误和安全问题，因此您可以自行决定最初部署哪个主要版本，以及何时升级到新的主要版本。

注意

如果你计划在企业环境中部署 Nextcloud，并且使用场景至关重要，开发者可以通过一种[企业服务协议帮助你选择最适合你特定使用场景的主要版本，并确保其在一对一的基础上得到最优部署，同时解决任何出现的关键问题。](https://nextcloud.com/enterprise/)

## 发布渠道 [](https://docs.nextcloud.com/server/latest/admin_manual/release_schedule.html#release-channels)

默认情况下，所有 Nextcloud 安装都会使用`稳定`发布渠道。该渠道会提供对大多数用户来说风险最小的最新功能。

注意

Nextcloud 会分阶段推出新版本以进一步降低大规模更新的风险。新版本，尤其是主要版本，通常最初只提供给一小部分系统。在一周（或更长时间）内没有报告广泛的关键错误后，更多的系统将被提供更新。有时主要版本可能直到第一个维护（修复）版本发布后才会提供给 <100% 的系统。

警告

当使用`稳定`通道时，即使您现有的主要版本尚未达到生命周期结束，您也可能被**提供**升级到更新的主要版本的机会。您可以自行决定是否立即升级，或者等待更好的时机部署主要新版本。另一方面，新的**维护**版本（在您已经运行的主要版本内）应尽快部署，以保持与安全和其他关键错误修复的同步。

警告

确保您正在运行一个活跃维护的主要版本至关重要。一旦主要版本达到生命周期结束状态，它将不再接收任何进一步的维护版本来修复关键错误或漏洞。

您可以在我们定期更新的[维护和发布计划](https://github.com/nextcloud/server/wiki/Maintenance-and-Release-Schedule)中找到所有稳定通道主要版本和维护版本的详细计划，包括生命周期结束日期。

## 主要版本升级 [](https://docs.nextcloud.com/server/latest/admin_manual/release_schedule.html#major-version-upgrades)

在从一个主要版本升级到另一个主要版本之前，我们强烈建议您查阅《发布说明》章节中的《重要变更》部分，以尽量减少引入意外中断变更的风险。

警告

进行更新之前（无论是主要更新还是维护更新），建议做好良好的数据备份（并测试好数据恢复方法）。

## Beta 版本和候选版本 [](https://docs.nextcloud.com/server/latest/admin_manual/release_schedule.html#beta-releases-and-release-candidates)

在发布一个新的主要最终版本之前，通常会先发布至少四个 Beta 版本，然后发布两个候选版本，每个版本之间间隔一周。

在发布一个新的维护最终版本之前，通常会在发布前大约一周发布一个候选版本。

每次发布的大致日期可以在[详细计划](https://github.com/nextcloud/server/wiki/Maintenance-and-Release-Schedule)中找到。

提示

为了更早地更新到新的主要版本或 beta 版本，您可以酌情将您的实例设置为使用 `beta` 通道。在大型发布前后，`beta` 通道也会提前提供最新的主要版本，而不考虑预发布参数。

社区中的每个人都从那些选择在测试环境中或在胆大的情况下使用 beta 版本或候选版本进行测试和反馈中受益匪浅。

如果您有机会评估预最终版本，开发人员和整个社区感谢您！

提示

我们建议将测试重点放在验证您每天依赖的功能和特性上（确保这些功能按预期工作）。然后，如果您愿意，可以考虑评估任何让您感兴趣的新功能。请在[帮助论坛](https://help.nextcloud.com/)讨论出现的问题，并将疑似 bug 报告给 [GitHub 仓库 ](https://github.com/nextcloud/server/issues)。

## 降级 [](https://docs.nextcloud.com/server/latest/admin_manual/release_schedule.html#downgrading)

从任何主要版本、维护版本或预发布版本降级是官方不支持的。

## 错误报告 [](https://docs.nextcloud.com/server/latest/admin_manual/release_schedule.html#bug-reporting)

在报告错误之前，请确保您正在运行一个仍受支持的主要版本及其最新的维护版本。

提示

Nextcloud GmbH - 雇佣了许多核心开发人员 - 提供 [Nextcloud 企业服务 ](https://nextcloud.com/enterprise/)，可直接访问 Nextcloud 工程师的专业知识，特别是在关键业务场景下。他们可以帮助您选择最适合您使用场景的主要版本（并确保其部署最优）。



# 系统要求 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html#system-requirements)

## 服务器 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html#server)

为了获得最佳性能、稳定性和功能，我们已经记录了一些关于运行 Nextcloud 服务器的建议。

注意

如果您计划为您的组织搭建系统，并依赖于专业的部署咨询（例如高效且可靠的扩展）和支持，我们强烈建议您查看我们的 [企业支持 ](https://nextcloud.com/enterprise/)。

| 平台             | 选项                                                         |
| ---------------- | ------------------------------------------------------------ |
| 操作系统（64位） | 推荐使用 **Ubuntu 24.04 LTS**Ubuntu 22.04 LTS推荐使用 **Red Hat Enterprise Linux 9**Red Hat Enterprise Linux 8Debian 12 (Bookworm)SUSE Linux Enterprise Server 15openSUSE Leap 15.5CentOS StreamAlpine Linux |
| 数据库           | MySQL 8.0 / **8.4** 或 MariaDB 10.6 / **10.11** / 11.4Oracle Database 11g, 18, 21, 23（仅作为企业订阅的一部分）PostgreSQL 13/14/15/16/17SQLite 3.24+（仅推荐用于测试和最小实例） |
| Web 服务器       | **Apache 2.4 以及** `mod_php` **或** `php-fpm`(推荐)nginx 配合 `php-fpm` |
| PHP 运行时       | 8.1 ( *已弃用* )8.28.3（推荐）8.4                            |

请参阅[在 Linux 上安装](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html)以了解安装 Nextcloud 所需的最小 PHP 模块和其他软件。

### CPU 架构和操作系统 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html#cpu-architecture-and-os)

Nextcloud 运行良好需要 64 位的 CPU、操作系统和 PHP。

32位系统受支持，但存在以下已知限制：

- 在 Unix 纪元之前（1970-01-01）的日期不被支持
- 在2038年之后的日期不被支持

### 内存 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html#memory)

运行 Nextcloud 服务器的内存需求因用户数量、应用、文件以及服务器活动量的不同而有很大差异。

Nextcloud 每个进程需要至少 **128MB** 的 RAM，我们建议每个进程至少有 **512MB** 的 RAM。

在内存有限的环境中，某些功能或应用可能需要调整其默认设置才能正常工作（在某些情况下，可能需要完全禁用这些功能）。

警告

要使用内置的更新器，至少需要 **256MB** 的内存。

### MySQL / MariaDB 的数据库要求 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html#database-requirements-for-mysql-mariadb)

如果你正在使用 MySQL / MariaDB 数据库与 Nextcloud 一起运行，目前需要以下条件：

- InnoDB 存储引擎（不支持 MyISAM）
- “READ COMMITTED”事务隔离级别（参见：[ 数据库“READ COMMITTED”事务隔离级别 ](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/linux_database_configuration.html#db-transaction-label)）
- 禁用或配置了 BINLOG_FORMAT = ROW 的二进制日志记录（详见：https://dev.mysql.com/doc/refman/5.7/en/binary-log-formats.html）
- 对于 **Emoji（UTF8 4 字节）支持** 请参阅 [启用 MySQL 4 字节支持](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/mysql_4byte_support.html)

### 为什么我们弃用旧的 PHP 版本 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html#why-we-drop-old-php-versions)

每年都会添加一个新的 PHP 版本，旧的 PHP 版本会被弃用。这也影响了我们文档中推荐的 PHP 版本。

我们尽可能长时间地支持旧的 PHP 版本。然而，安全、性能和错误修复的列表将会不断增加，其中一些修复可能被认为是关键性的，因此最终弃用这些旧版本是不可避免的。

因此，建议您将 PHP 版本保持最新。

#### 升级 PHP 的优势 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html#advantages-of-upgrading-php)

- **安全性**

  PHP 停止对旧版本的安全修复。只要我们支持已废弃的 PHP 版本，Nextcloud 就无法实现新 PHP 版本带来的安全修复，因为我们需要使用的语法必须是支持版本中最老的语法，因此第三方软件包会因为失去了对这些版本的支持而无法正常工作。

- **性能**

  语言随着时间不断改进，使得可以在显著更短的时间内处理更多的请求。

#### 长期支持 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html#long-term-support)

如果你正在为企业关键用途运行 Nextcloud，可以考虑将订阅升级为高级订阅，从而获得 5 年的长期支持。这意味着你在这段时间内将继续收到针对高危和关键安全问题、数据丢失修复以及版本内回归问题的维护更新。

## 桌面客户端 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html#desktop-client)

我们强烈建议使用您操作系统的最新版本，以获得我们的客户端提供的完整且最稳定的体验。

- **Windows** 10+
- **macOS** Monterey (12.0)+ (仅 64 位) 请注意，为了使桌面客户端能够成功连接，您的服务器可能需要符合 Apple App Transport Security 的要求。这可能需要使用一个适当签名的数字证书，符合 Apple 设定的标准。更多详细信息请参阅 Apple 开发者文档：[https://developer.apple.com/documentation/security/preventing_insecure_network_connections](https://developer.apple.com/documentation/security/preventing_insecure_network_connections)
- **Linux** (仅 64 位) 应能够运行任何比 Ubuntu 18.04 更新的发行版，使用我们官方的 AppImage 包

## 移动应用 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html#mobile-apps)

我们强烈建议使用您移动操作系统的最新版本，以获得我们移动应用的完整且最稳定的体验。

### 文件应用

- 15.0+
- Android 7.0+

### Talk 应用 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html#talk-app)

- 15.0+
- Android 8.0+
- Nextcloud Server 19.0+
- Nextcloud Talk 9.0+

## Web 浏览器 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html#web-browser)

为了获得 Nextcloud 网页界面的最佳体验，我们建议您使用以下列表中的最新且受支持的浏览器版本，或基于这些浏览器的其他浏览器版本：

- Microsoft **Edge**
- Mozilla **Firefox**
- Google **Chrome**/Chromium
- Apple **Safari**

注意

如果你想使用 Nextcloud Talk，你应该使用 Mozilla Firefox 52+ 或 Google Chrome/Chromium 49+，以获得完整的视频通话和屏幕共享体验。Google Chrome/Chromium 需要额外的插件才能进行屏幕共享。



# PHP 模块 & 配置 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#php-modules-configuration)

## PHP 模块 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#php-modules)

本节列出了所有必需和可选的 PHP 模块。有关模块的更多信息，请参阅 [PHP 手册 ](https://php.net/manual/en/extensions.php)。您可以使用 `php -m | grep -i <module_name>` 检查模块是否存在。如果得到结果，说明该模块已存在。

必需：

- PHP（请参阅[系统要求](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html)以获取支持版本列表）
- PHP 模块 ctype
- PHP 模块 curl
- PHP 模块 dom
- PHP 模块 fileinfo（随 PHP 一起提供）
- PHP 模块 filter（仅在 Mageia 和 FreeBSD 上提供）
- PHP 模块 GD
- PHP 模块 hash（仅在 FreeBSD 上提供）
- PHP 模块 JSON（包含在 PHP >= 8.0 中）
- PHP 模块 libxml（Linux 包 libxml2 必须 >= 2.7.0）
- PHP 模块 mbstring
- PHP 模块 openssl（包含在 PHP >= 8.0 中）
- PHP 模块 posix
- PHP 模块 session
- PHP 模块 SimpleXML
- PHP 模块 XMLReader
- PHP 模块 XMLWriter
- PHP 模块 zip
- PHP 模块 zlib

数据库连接器（请选择您数据库对应的版本）：

- PHP 模块 pdo_sqlite (>= 3，出于性能原因通常不推荐)
- PHP 模块 pdo_mysql (MySQL/MariaDB)
- PHP 模块 pdo_pgsql (PostgreSQL)

推荐安装的包：

- PHP 模块 intl（提高语言翻译性能并修复非 ASCII 字符排序问题）
- PHP 模块 sodium（用于密码哈希，当 PHP < 8.4且PHP未使用libargon2编译时，使用Argon2。如果使用bcrypt作为备用方案，但密码已使用Argon2进行哈希且缺少该模块，用户将无法登录。）

特定应用所需：

- PHP 模块 ldap（用于 LDAP 集成）
- PHP 模块 smbclient（SMB/CIFS 集成，请参见 [SMB/CIFS](https://docs.nextcloud.com/server/latest/admin_manual/configuration_files/external_storage/smb.html)）
- PHP 模块 ftp（用于 FTP 存储 / 外部用户身份验证）
- PHP 模块 imap（用于外部用户身份验证）

推荐用于特定应用（可选）：

- PHP 模块 gmp（用于 SFTP 存储）
- PHP 模块 exif（用于图片应用中的图片旋转）

为了提高服务器性能（可选），请选择以下缓存之一或多个：

- PHP 模块 apcu（>= 4.0.6）
- PHP 模块 memcached
- PHP 模块 redis（>= 2.2.6，用于事务文件锁定）

请参阅 [内存缓存 ](https://docs.nextcloud.com/server/latest/admin_manual/configuration_server/caching_configuration.html)以了解如何选择和配置缓存。

预览生成（可选）：

- PHP 模块 imagick
- avconv 或 ffmpeg
- OpenOffice 或 LibreOffice

注意

如果生成 PDF 文件的预览时出现“未授权”错误提示，您必须调整 imagick 策略文件。请参阅 https://cromwell-intl.com/open-source/pdf-not-authorized.html

对于命令行处理（可选）：

- PHP 模块 pcntl（允许通过按下 `ctrl-c` 中断命令）

注意

您还需要确保在 php.ini 中 `pcntl_signal` 和 `pcntl_signal_dispatch` 未被 `disable_functions` 选项禁用。

对于命令行更新器（可选）：

- PHP 模块 phar（通过运行 `sudo -E -u www-data php /var/www/nextcloud/updater/updater.phar` 升级 Nextcloud）

## ini 值 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#ini-values)

以下的 ini 设置如有需要可进行调整：

- `disable_functions`: 除非你知道确切的操作，否则不要禁用函数
- `max_execution_time`: 请参阅 [上传大文件（> 512MB）](https://docs.nextcloud.com/server/latest/admin_manual/configuration_files/big_file_upload_configuration.html)
- `memory_limit`: 至少应为 512MB。请参阅 [上传大文件（> 512MB）](https://docs.nextcloud.com/server/latest/admin_manual/configuration_files/big_file_upload_configuration.html)
- `opcache.enable` 及相关设置：请参阅 [内存缓存 ](https://docs.nextcloud.com/server/latest/admin_manual/configuration_server/caching_configuration.html)和 [服务器调优](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html)
- `open_basedir`: 请参阅 [强化和安全指南](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html)
- `upload_tmp_dir`: 请参阅 [上传大文件（> 512MB）](https://docs.nextcloud.com/server/latest/admin_manual/configuration_files/big_file_upload_configuration.html)



## php.ini 配置注意事项 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#php-ini-configuration-notes)

请注意，对 `php.ini` 的更改可能需要在多个 ini 文件中进行配置。例如，`date.timezone` 设置就可能需要在多个 ini 文件中进行配置。您可以使用以下命令搜索参数： `grep -r date.timezone /etc/php` 。

**php.ini - 由 Web 服务器使用：**

```
  /etc/php/8.3/apache2/php.ini
or
  /etc/php/8.3/fpm/php.ini
or ...
```



**php.ini - 用于 php-cli 并因此用于 Nextcloud CRON 任务：**

```
/etc/php/8.3/cli/php.ini
```



注意

路径名必须根据安装的 PHP（8.1、8.2、8.3 或 8.4）进行设置。



# 安装在 Linux 上 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#installation-on-linux)

根据您的偏好、需求和目标，有多种安装 Nextcloud 的方法。

如果您更喜欢自动化安装，您可以选择：

- 使用[官方 Nextcloud 安装方法 ](https://github.com/nextcloud/all-in-one#nextcloud-all-in-one)。Nextcloud AIO 提供了一键部署和维护，此单一 Nextcloud 实例包含了大部分功能。它包括 Office、开箱即用的备份解决方案、Imaginary（用于预览 heic、heif、illustrator、pdf、svg、tiff 和 webp）以及其他功能。
- 使用 [社区提供的 Snap 包 ](https://snapcraft.io/nextcloud)。这将包括一个完整的生产级堆栈，会为您管理 HTTPS 证书，并会自动更新以保持安全。
- 使用 [社区提供的 Nextcloud VM Appliance](https://github.com/nextcloud/vm/)（又称 Nextcloud 虚拟机或 NcVM）。这将帮助您更快更轻松地创建个人或企业的 Nextcloud 服务器。它可以直接安装在干净的 Ubuntu 服务器上，或者下载为一个完整的虚拟机。
- 使用 [社区提供的 NextcloudPi 脚本 ](https://nextcloudpi.com/)（基于 Debian）。这将为您设置一切，并包含用于自动安装应用程序（如 Collabora、OnlyOffice、Talk 等）的脚本。
- 使用 [社区提供的 Nextcloud Docker 镜像 ](https://hub.docker.com/_/nextcloud/)。此镜像设计用于微服务环境。您可以选择两种版本的镜像：Apache 版本包含完整的 Nextcloud 安装，包括 Apache web 服务器。第二种是 FPM 版本，运行一个 FastCGI 进程来提供您的 Nextcloud 安装（您需要提供您首选的 web、数据库和其他所需的补充服务）。

注意

请注意，社区选项不被 Nextcloud GmbH 正式支持。

提示

如需基于 Helm Charts（也适用于 Podman）的企业级且可扩展的安装，请[联系 Nextcloud GmbH](https://nextcloud.com/enterprise/)。

如果您更倾向于从源 tar 包安装，可以使用经典的 LAMP 堆栈（Linux、Apache、MySQL/MariaDB、PHP）从头开始设置 Nextcloud。本文档提供了在使用 [Nextcloud .tar 包 ](https://nextcloud.com/install/) 的 Ubuntu 18.04 LTS 服务器上安装 Nextcloud（使用 Apache 和 MariaDB）的完整指南。这种方法推荐用于安装 Nextcloud。

本安装指南提供了所需依赖及其配置的一般概述。对于特定发行版的安装指南，请参阅 [Ubuntu 22.04 LTS 的示例安装 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_ubuntu.html)和 [CentOS 8 的示例安装 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_centos.html)。

注意

SELinux 启用的发行版（如 CentOS、Fedora 和 Red Hat Enterprise Linux）的管理员可能需要设置新的规则以安装 Nextcloud。请参阅 [SELinux 配置提示](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#selinux-tips-label)以获取建议的配置。

## 手动安装的先决条件 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#prerequisites-for-manual-installation)

Nextcloud 的.tar 存档包含所有必需的 PHP 模块。您的 Linux 发行版应该有所有必需模块的软件包。请参阅 [PHP 模块与配置](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html)以获取所需和建议模块的列表。

您不需要 Web 服务器（例如 Apache）的 WebDAV 模块。 `mod_webdav`), 由于 Nextcloud 自带一个名为 SabreDAV 的 WebDAV 服务器，因此如果启用了 `mod_webdav`，您必须为 Nextcloud 禁用它。（请参阅 [Apache Web 服务器配置 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#apache-configuration-label)以获取一个示例配置。）



## Apache Web 服务器配置 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#apache-web-server-configuration)

配置 Apache 需要创建一个单一的配置 文件。在 Debian、Ubuntu 及其衍生发行版中，该文件将位于 `/etc/apache2/sites-available/nextcloud.conf` . 在 Fedora 中， CentOS、RHEL 及类似系统中，配置文件将位于 `/etc/httpd/conf.d/nextcloud.conf` .

你可以选择在现有的 Web 服务器目录中安装 Nextcloud，例如 https://www.example.com/nextcloud/，或者在虚拟主机中安装，以便 Nextcloud 可以从自己的子域名访问，例如 https://cloud.example.com/。

要使用基于目录的安装，请将以下内容放入您的 将 ``nextcloud.conf`` 中的 `**Directory**` 和 `**Alias**` 文件路径替换为您的系统相应的文件路径：

```
Alias /nextcloud "/var/www/nextcloud/"

<Directory /var/www/nextcloud/>
  Require all granted
  AllowOverride All
  Options FollowSymLinks MultiViews

  <IfModule mod_dav.c>
    Dav off
  </IfModule>
</Directory>
```



要使用虚拟主机安装，请在您的 `nextcloud.conf` 替换 **ServerName**，以及 将 **DocumentRoot** 和 **Directory** 文件路径设置为适用于您系统的适当值：

```
<VirtualHost *:80>
  DocumentRoot /var/www/nextcloud/
  ServerName  your.server.com

  <Directory /var/www/nextcloud/>
    Require all granted
    AllowOverride All
    Options FollowSymLinks MultiViews

    <IfModule mod_dav.c>
      Dav off
    </IfModule>
  </Directory>
</VirtualHost>
```



在 Debian、Ubuntu 及其衍生发行版中，您应该运行以下命令以启用配置：

```
a2ensite nextcloud.conf
```



### 额外的 Apache 配置 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#additional-apache-configurations)

- 为了使 Nextcloud 正常工作，我们需要启用模块 `mod_rewrite`。通过运行以下命令启用它：

  ```
  a2enmod rewrite
  ```

  

  推荐的附加模块有：`mod_headers`、`mod_env`、`mod_dir` 和 `mod_mime`：

  ```
  a2enmod headers
  a2enmod env
  a2enmod dir
  a2enmod mime
  ```

  

  如果你在运行 ``mod_fcgi`` 而不是标准的 ``mod_php``，也需要启用：

  ```
  a2enmod setenvif
  ```

  

  并对配置进行以下修改：

  ```
  ProxyFCGIBackendType FPM
  
  <FilesMatch remote.php>
    SetEnvIf Authorization "(.*)" HTTP_AUTHORIZATION=$1
  </FilesMatch>
  ```

  

- 您必须禁用任何服务器配置的认证，因为 Nextcloud 会为 DAV 服务内部使用 Basic 认证。如果您在父文件夹启用了认证（例如通过 ``AuthType Basic`` 在该指令中，您可以关闭特定于该目录的认证功能 Nextcloud 入口。按照上述示例配置文件，添加 在 ``<Directory>`` 部分添加以下行：

  ```
  Satisfy Any
  ```

  

- 使用 SSL 时，请特别注意 ServerName。您应该在服务器配置中指定一个，并且在证书的 CommonName 字段中也指定一个。如果您希望通过互联网访问 Nextcloud，请将这两个字段都设置为您想要访问的 Nextcloud 服务器的域名。

- 现在重启 Apache：

  ```
  service apache2 restart
  ```

  

- 如果您在子目录中运行 Nextcloud，并且希望使用 CalDAV 或 CardDAV 客户端，请确保已正确配置。 服务发现 [Service discovery](https://docs.nextcloud.com/server/latest/admin_manual/issues/general_troubleshooting.html#service-discovery-label) URLs。



## 美化 URL[](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#pretty-urls)

美化 URL 可以去掉所有 Nextcloud URL 中的 `index.php` 部分，例如在共享链接中，如 `https://example.org/nextcloud/index.php/s/Sv1b7krAUqmF8QQ` ，使 URL 更短且更美观。

`mod_env` 和 `mod_rewrite` 必须安装在你的 Web 服务器上，并且需要有 `.htaccess` 文件。 必须可被 HTTP 用户写入。要启用`mod_env`和`mod_rewrite`，请运行`sudo a2enmod env`和`sudo a2enmod rewrite`。然后您可以在`config.php`中设置两个变量：

```
'overwrite.cli.url' => 'https://example.org/nextcloud',
'htaccess.RewriteBase' => '/nextcloud',
```



如果您的设置可通过 `https://example.org/nextcloud` 访问：

```
'overwrite.cli.url' => 'https://example.org/',
'htaccess.RewriteBase' => '/',
```



或者，如果它未安装在子文件夹中。最后，请运行此 occ 命令以更新您的 .htaccess 文件：

```
sudo -E -u www-data php /var/www/nextcloud/occ maintenance:update:htaccess
```



每次更新后，这些更改会自动应用到 `.htaccess` 文件中。

注意

如果自动添加的 ``.htaccess`` 配置 `SetEnv front_controller_active true` 在您的环境中不起作用：编辑 ``config/config.php``，并添加 ` `'htaccess.IgnoreFrontController' => true` `。详细描述请参见 [配置参数 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#6)。



## 启用 SSL[](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#enabling-ssl)

注意

你可以使用 Nextcloud 通过明文 HTTP，但我们强烈建议你使用 SSL/TLS 来加密服务器上的所有流量，并保护用户在传输过程中的登录信息和数据。

在 Ubuntu 下安装的 Apache 已经配置了一个简单的自签名证书。你只需要启用 ssl 模块和默认站点即可。打开终端并运行：

```
a2enmod ssl
a2ensite default-ssl
service apache2 reload
```



注意

自签名证书有一些缺点，尤其是当你计划让你的 Nextcloud 服务器对外公开时。考虑获取由认证机构签名的证书。可以咨询你的域名注册商或托管服务提供商，了解商业证书的优惠。或者使用免费的 [Let’s Encrypt](https://letsencrypt.org/) 证书。



## 安装向导 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#installation-wizard)

重启 Apache 之后，您需要通过运行图形化安装向导或在命令行中使用 `occ` 命令来完成安装。要启用此功能，请将 Nextcloud 目录的所有权更改为 您的 HTTP 用户：

```
chown -R www-data:www-data /var/www/nextcloud/
```



注意

SELinux 启用分发版的管理员可能需要编写新的 SELinux 策略 完成 Nextcloud 安装的规则；请参阅 [SELinux 配置提示 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#selinux-tips-label).

要使用 ``occ``，请参阅 [从命令行安装 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/command_line_installation.html)。

要使用图形安装向导，请参见[安装向导 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/installation_wizard.html)。



## 后台任务的设置 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#setting-up-background-jobs)

Nextcloud 需要定期运行一些任务。这些任务可能包括维护任务以确保最佳性能，或者像发送通知这类时间敏感的任务。

请参见[后台任务](https://docs.nextcloud.com/server/latest/admin_manual/configuration_server/background_jobs_configuration.html)以获取详细描述和优势。



## SELinux 配置提示 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#selinux-configuration-tips)

请参阅 [SELinux 配置 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html)，了解在 Fedora 和 CentOS 等 SELinux 启用的发行版上的建议配置。



## PHP-FPM 配置 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#php-fpm-configuration)

### 概述 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#overview)

[PHP-FPM](https://www.php.net/manual/en/install.fpm.php) 是一个基于 FastCGI 的 PHP 实现，包含适用于繁忙网站和大型 Web 应用的功能。与 Nextcloud 一起使用时，这是一个高级话题，需要熟悉 PHP-FPM 的工作原理。在大多数情况下，PHP-FPM 的默认设置并不适合 Nextcloud。这里我们将突出显示几个需要调整的重要区域。

### 进程管理器 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#process-manager)

许多 PHP-FPM 安装中 `pm.max_children` 的默认值低于适当值。较低的值可能会导致客户端连接问题、无法解释的错误和性能问题。这是导致 *网关超时* 的常见原因。然而，如果相对于可用资源（如内存）设置的值过高，也会导致问题。默认值通常是 `5`。这极大地限制了同时连接到你的 Nextcloud 实例的数量，除非你资源极其紧张，否则会严重浪费硬件资源。请参阅 [服务器调优](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html) 用于获取一些指导和资源以确定合适的值， 以及其它相关参数。

### 系统环境变量 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#system-environment-variables)

当你使用 `php-fpm` 时，系统环境变量如 PATH、TMP 或其他变量不会像使用 `php-cli` 那样自动填充。因此，像 `getenv('PATH');` 这样的 PHP 调用可能会返回空结果。所以你可能需要手动在适当的 `php-fpm` ini/config 文件中配置环境变量。

以下是这些 ini/config 文件的一些示例根路径：

| Debian/Ubuntu/Mint  | CentOS/Red Hat/Fedora |
| ------------------- | --------------------- |
| `/etc/php/8.3/fpm/` | `/etc/php-fpm.d/`     |

在两个示例中，配置文件名为 ``www.conf``，根据发行版版本或您所做的自定义设置，该文件可能位于子目录中，例如 ``pool.d``。

通常，你会发现一些或全部的环境变量已经在文件中，但被注释掉了，如下所示：

```
;env[HOSTNAME] = $HOSTNAME
;env[PATH] = /usr/local/bin:/usr/bin:/bin
;env[TMP] = /tmp
;env[TMPDIR] = /tmp
;env[TEMP] = /tmp
```



取消注释相应的现有条目，然后运行 `printenv PATH` 确认路径，例如：

```
$ printenv PATH
/home/user/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:
/sbin:/bin:/
```



如果系统环境变量中有任何不在文件中的变量，那么你必须添加这些变量。

或者，你也可以通过修改以下内容来使用系统的环境变量：

```
/etc/php/8.3/fpm/pool.d/www.conf
```



并取消注释该行：

```
clear_env = no
```



当你使用共享主机或控制面板来管理你的 Nextcloud 虚拟机（VM）时 或服务器上，配置文件几乎 出于安全和灵活性的考虑，它可能会被安装在其他位置 请查阅文档以获取正确的路径。

请记住，可以为不同的环境创建不同的设置 使用 `php-cli` 和 `php-fpm`，并针对不同的域名和网站。检查设置的最佳方式是使用 [PHP 版本和信息 ](http://phpversionandinfo.com/)。

### 最大上传大小 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#maximum-upload-size)

如果你想增加最大上传文件大小，你还必须修改你的 `php-fpm` 配置，并增加 `upload_max_filesize` 和 `post_max_size` 的值。为了使这些更改生效，你需要重启 `php-fpm` 和你的 HTTP 服务器。

### .htaccess[](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#htaccess)

Nextcloud 自带了一个 `nextcloud/.htaccess` 文件。由于 `php-fpm` 无法读取 `.htaccess` 中的 PHP 设置，因此这些设置和权限必须在 `nextcloud/.user.ini` 文件中进行设置。



## 其他 Web 服务器 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#other-web-servers)

- [NGINX 配置](https://docs.nextcloud.com/server/latest/admin_manual/installation/nginx.html)



## 在 Windows（虚拟机）上安装

如果您使用的是 Windows，最简便的方法是使用虚拟机（VM）来启动和运行 Nextcloud。有两种选择：

- **企业/中小企业专用设备**

Nextcloud GmbH 提供了一个基于 [Univention Corporate Server (UCS)](https://www.univention.com/products/univention-app-center/app-catalog/nextcloud/) 的免费设备，具有简单的图形化安装设置和基于 Web 的管理功能。它包括用户 通过 LDAP 管理，可以替换现有的 Active Directory 配置和 可选集成 ONLYOFFICE 和 Collabora Online，以及更多应用程序 易于快速安装。

它可以在硬件上安装，也可以使用 VirtualBox、VMWare（ESX）和 KVM 镜像在虚拟机中运行。

在这里下载设备：

- [Univention Corporate Server (UCS)](https://www.univention.com/products/univention-app-center/app-catalog/nextcloud/)

- **家庭用户/中小企业设备**

Nextcloud 虚拟机由 [T&M Hansson IT](https://www.hanssonit.se/nextcloud-vm/) 提供了多个不同版本。您可以使用包含的脚本轻松安装 Collabora、OnlyOffice、全文搜索和其他应用程序，您可以在首次设置时选择运行这些脚本，或者稍后下载并在之后运行。您可以在 [GitHub](https://github.com/nextcloud/vm/blob/main/apps/) 上找到所有当前可用的自动化应用程序安装。

该虚拟机有不同的大小和版本。

您可以在[这里](https://shop.hanssonit.se/product-category/virtual-machine/nextcloud-vm/)找到所有可用的版本。

完整的安装说明和下载请参见：

- [Nextcloud VM（GitHub）](https://github.com/nextcloud/vm/)
- [Nextcloud VM (T&M Hansson IT)](https://www.hanssonit.se/nextcloud-vm/)

注意

你可以将虚拟机安装在多种不同的操作系统上，只要你的虚拟化环境可以挂载 OVA、VMDK 或 VHD/VHDX 格式的虚拟机。如果你使用的是 KVM，那么需要从 GitHub 上的脚本安装虚拟机。你可以按照 [README 中的说明 ](https://github.com/nextcloud/vm#build-your-own-vm-or-install-on-a-vps) 进行操作。



## 通过 Snap 包安装 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#installing-via-snap-packages)

Nextcloud 的 Snap 包是一种社区驱动的安装方法，旨在易于安装和维护。理想的 Nextcloud Snap 包是一个“安装后即可忽略”的 Nextcloud 实例，可以在大多数架构上运行，并且可以自动更新，无需管理员技能。将 Nextcloud 与 snapd 结合使用，使其非常适合物联网或可扩展环境。[snapd](https://snapcraft.io/docs) 是一种安全且可靠的技術，Nextcloud Snap 包团队已经采纳了它。

最重要的是，snap 是设计为安全的、沙盒化的、容器化的应用程序，与底层系统和其他应用程序隔离。

然而，此 snap 有偏见，并且需要满足某些要求。

- Nextcloud snap 使用推荐的 Apache。
- Nextcloud snap 使用推荐的 MySQL。
- Nextcloud snap 使用推荐的 PHP。

### 安装

**在 Ubuntu 上**

- https://snapcraft.io/nextcloud
- 安装 Nextcloud ``sudo snap install nextcloud``

**其他所有发行版请注意**

默认情况下，将安装最新稳定的 Nextcloud snap 版本，并会自动更新到后续的稳定版本，但也有其他版本可供选择。 并且您可以完全控制 [自动更新 ](https://github.com/nextcloud-snap/nextcloud-snap/wiki/Managing-automatic-updates)。

安装完成后，Nextcloud 将自动启动。假设您和安装设备在同一个网络中，您可以通过在浏览器中访问 `<hostname>.local` 或实例的 IP 地址来访问 Nextcloud 安装页面。如果您的主机名为 `localhost` 或 `localhost.localdomain`，例如在 Ubuntu Core 设备上， `nextcloud.local` 将被使用。

### 首次登录 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#st-login)

首次访问 Nextcloud 安装时，系统会提示您输入管理员用户名和密码，然后 Nextcloud 才会初始化。这可能需要一些时间，具体取决于资源和设备。提供这些信息后，您将登录并能够安装应用程序、创建用户和上传文件。

### HTTPS 加密 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#https-encryption)

Nextcloud snap 包含一个服务，用于自动进行 HTTPS 加密和使用 Let's Encrypt 或自签名证书的自动续期。运行 `nextcloud.enable-https -h` 以获取更多信息。[ 管理加密 ](https://github.com/nextcloud-snap/nextcloud-snap/wiki/Managing-HTTP-encryption-(HTTPS))。

### 配置 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#configuration)

虽然 Nextcloud 的默认配置大多已经足够，但可能需要通过手动编辑配置文件或使用管理控制台来进一步调整 Nextcloud snap。[ 配置 Nextcloud snap](https://github.com/nextcloud-snap/nextcloud-snap/wiki/Configure-Nextcloud-snap)。

### 外部媒体 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#external-media)

Snap 约束是一种安全功能，决定了应用程序对系统资源（如文件、网络、外设和服务）的访问权限。因此，你的 Nextcloud snap 会受到主机系统的安全约束。除非你特别允许 Nextcloud snap 访问主机系统的 `/media` 或 `/mnt` 目录，否则你将无法访问其他任何外部目录。

可移动介质或外部存储必须以 root 权限作为 root 用户挂载到 `/media` 或 `/mnt` 目录下，并连接到 Snap！[ 管理外部介质和存储](https://github.com/nextcloud-snap/nextcloud-snap/wiki/Managing-external-media,-shares-and-storage)

安装完成后，提供访问可移动介质界面不会自动连接，要使用外部存储（或使用 `/media` 或 `/mnt` 中的设备进行数据存储），您需要通过连接该界面来赋予 snap 访问可移动介质的权限：

```
sudo snap connect nextcloud:removable-media
```

进一步的文档、详尽的 [Wiki](https://github.com/nextcloud-snap/nextcloud-snap/wiki) 和 [FAQ](https://github.com/nextcloud-snap/nextcloud-snap/wiki/FAQ's) 可以在[开发者的 GitHub](https://github.com/nextcloud-snap/nextcloud-snap) 上找到。

注意

[snapd 技术](http://snapcraft.io/docs/core/)是核心 这驱动了 Snap 包的运行，并提供了一种新的打包、分发和更新方式 在 Linux 系统上运行操作系统组件和应用程序。更多关于 snaps 的信息，请参见 [snapcraft.io](http://snapcraft.io/)

## 通过 Web 安装程序安装（适用于 VPS 或网站空间）[](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#installation-via-web-installer-on-a-vps-or-web-space)

当您无法使用命令行，例如在网页托管或虚拟机平台（VMPS）上时， 一个简单的方法是使用我们的 Web 安装程序。该脚本可以在我们的网站上找到。 [服务器安装页面。](https://nextcloud.com/install/#instructions-server)

脚本会检查依赖项，从官方服务器下载 Nextcloud，使用正确的权限和用户账户解压。最后，您将被重定向到 Nextcloud 安装器。这里是一个快速指南：

1. 从安装页面获取文件
2. 将 setup-nextcloud.php 上传到你的 web 空间
3. 在你的 web 浏览器中访问 web 空间中的 setup-nextcloud.php
4. 按照指示配置 Nextcloud
5. 登录你新建的 Nextcloud 实例！

注意

安装程序使用的版本与 Nextcloud 内置更新器中可用的版本相同。在主要版本发布后，通过 Web 安装程序和更新器获取新版本可能需要长达一个月的时间。这是为了在时间上分散部署新主要版本。

## 在 TrueNAS 上安装 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#installation-on-truenas)

请参阅 [TrueNAS 安装文档 ](https://www.truenas.com/docs/core/solutions/integrations/nextcloud/)。

## 通过安装脚本安装 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#installation-via-install-script)

安装的一种最简便的方式是使用 Nextcloud 虚拟机或 NextcloudPI 脚本。基本上只需要两步：

1. 下载最新的 [虚拟机安装脚本 ](https://github.com/nextcloud/vm/blob/main/nextcloud_install_production.sh/)。

2. 运行该脚本：

   ```
   sudo bash nextcloud_install_production.sh
   ```

   

或者

1. 下载最新的 [PI 安装脚本 ](https://raw.githubusercontent.com/nextcloud/nextcloudpi/master/install.sh)。

2. 运行脚本：

   ```
   sudo bash install.sh
   ```

   

将引导您完成设置过程，您只需按照屏幕上的指示操作即可。





# 安装向导 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/installation_wizard.html#installation-wizard)

## 快速开始 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/installation_wizard.html#quick-start)

当 Nextcloud 的先决条件满足并且所有 Nextcloud 文件都已安装后，完成安装的最后一步是运行安装向导。这只需三个步骤：

1. 将 Web 浏览器指向 `http://localhost/nextcloud`
2. 输入您希望的管理员用户名和密码。
3. 点击 **完成设置** 。

[![screenshot of the installation wizard](https://cdn.jsdelivr.net/gh/otxtdb/txtdbpic@master/img/eb282898157696bd492cc79ee149ac04.png)](https://docs.nextcloud.com/server/latest/admin_manual/_images/install-wizard-a.png)

设置完成，您可以开始使用新的 Nextcloud 服务器了。

当然，您还可以采取更多措施来优化 Nextcloud 服务器的性能和安全性。在接下来的部分中，我们将介绍重要的安装和安装后的步骤。

- [数据目录位置](https://docs.nextcloud.com/server/latest/admin_manual/installation/installation_wizard.html#data-directory-location-label)
- [数据库选择](https://docs.nextcloud.com/server/latest/admin_manual/installation/installation_wizard.html#database-choice-label)
- [受信任域](https://docs.nextcloud.com/server/latest/admin_manual/installation/installation_wizard.html#trusted-domains-label)



## 数据目录位置 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/installation_wizard.html#data-directory-location)

点击 **存储和数据库** 以暴露更多 Nextcloud 数据目录和数据库的安装配置选项。

[![installation wizard with all options exposed](https://cdn.jsdelivr.net/gh/otxtdb/txtdbpic@master/img/b8c2c21a19d0986afb8e263d684d223e.png)](https://docs.nextcloud.com/server/latest/admin_manual/_images/install-wizard-a1.png)

如果你使用的是除 Apache 之外的 HTTP 服务器，应将 Nextcloud 的数据目录放在 Web 根目录之外，或者出于其他原因（例如存放在存储服务器上），你可能希望将 Nextcloud 的数据存储在不同的位置。最好在安装时配置数据目录的位置，因为安装后移动它会比较困难。你可以将它放在任何地方；在这个例子中，它位于 `/opt/nextcloud/`。该目录必须已经存在，并且必须由你的 HTTP 用户拥有。



## 数据库选择 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/installation_wizard.html#database-choice)

SQLite 是 Nextcloud 服务器的默认数据库，仅适用于测试和轻量级的单用户设置，且不支持客户端同步。支持的数据库包括 MySQL、MariaDB、Oracle 11g 和 PostgreSQL，我们推荐使用 [MySQL/MariaDB](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html)。在运行安装向导之前，您需要安装数据库和 PHP 连接器。如果您从包安装 Nextcloud，所有必要的依赖项将被满足（请参阅 [Linux 安装 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html)以获取所需和可选 PHP 模块的详细列表）。您需要使用 root 数据库登录，或任何管理员登录，然后输入您想要的 Nextcloud 数据库名称。请注意，管理员登录需要具有创建和修改数据库的权限，并且需要具有授予其他用户权限的权限。

在您输入数据库的根用户或管理员登录信息后，安装程序会创建一个特殊的数据库用户，该用户的权限仅限于 Nextcloud 数据库。然后，Nextcloud 只需使用这个特殊的 Nextcloud 数据库用户，就会删除根数据库登录信息。该用户的名字会以您的 Nextcloud 管理员用户名为基础，并带有`oc_`前缀，然后会生成一个随机密码。Nextcloud 数据库用户和密码会被写入`config.php`文件中：

```
'dbuser' => 'oc_molly',
'dbpassword' => 'pX65Ty5DrHQkYPE5HRsDvyFHlZZHcm',
```



点击完成设置，开始使用您的新 Nextcloud 服务器。

[![Nextcloud welcome screen after a successful installation](https://cdn.jsdelivr.net/gh/otxtdb/txtdbpic@master/img/8aa63b6b5816dad9abbcd8c7968601f1.png)](https://docs.nextcloud.com/server/latest/admin_manual/_images/install-wizard-a2.png)

现在我们将查看一些重要的安装后步骤。



## 受信任的域名 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/installation_wizard.html#trusted-domains)

访问您的 Nextcloud 服务器的所有 URL 都必须在您的白名单中列出 `config.php` 文件中的 `trusted_domains` 设置。只有当用户通过列出在 `trusted_domains` 设置中的 URL 访问 Nextcloud 时，才能登录 Nextcloud。这并不是客户端允许的域名或 IP 地址列表。您可以使用 IP 地址和域名。典型的配置如下：

```
'trusted_domains' =>
  array (
   0 => 'localhost',
   1 => 'server1.example.com',
   2 => '192.168.1.50',
   3 => '[fe80::1:50]',
),
```



注意：

回环地址 `127.0.0.1` 会自动被白名单允许，因此只要你能访问物理服务器，就可以始终登录。如果存在负载均衡器，只要它发送正确的 `X-Forwarded-Host` 头信息，就不会有问题。当用户尝试访问未被白名单允许的 URL 时，会出现以下错误：

[![Error message when URL is not whitelisted](https://cdn.jsdelivr.net/gh/otxtdb/txtdbpic@master/img/1cc0b6a73222186cc77c4a3a443a3c8a.png)](https://docs.nextcloud.com/server/latest/admin_manual/_images/install-wizard-a4.png)







# 从命令行安装

现在可以从命令行完全安装 Nextcloud。这对于脚本操作、无头服务器和偏好命令行的系统管理员来说非常方便。通过命令行安装 Nextcloud 分为三个阶段：

1. 下载 Nextcloud 代码，并将 tarball 解压到适当的目录中。（详见 [Linux 安装 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html)。）
2. 将你的 `nextcloud` 目录的所有权更改为 HTTP 用户，例如在 Debian/Ubuntu 系统上的示例。你必须以 HTTP 用户身份运行 `occ`；详见 [以 HTTP 用户身份运行 occ](https://docs.nextcloud.com/server/latest/admin_manual/occ_command.html#http-user-label)：

```
$ sudo chown -R www-data:www-data /var/www/nextcloud/
```



3. 使用 `occ` 命令完成安装。这将替代运行图形化安装向导。

```
$ cd /var/www/nextcloud/
$ sudo -E -u www-data php occ  maintenance:install \
--database='mysql' --database-name='nextcloud' \
--database-user='root' --database-pass='password' \
--admin-user='admin' --admin-pass='password'
Nextcloud is not installed - only a limited number of commands are available
Nextcloud was successfully installed
```



请注意，必须切换到根 Nextcloud 目录，如上例所示，才能运行 ``occ maintenance:install``，否则安装将会失败并显示 PHP 致命错误消息。

支持的数据库有：

```
- sqlite (SQLite3 - Nextcloud Community edition only)
- mysql (MySQL/MariaDB)
- pgsql (PostgreSQL)
- oci (Oracle 11g currently only possible if you contact us at https://nextcloud.com/enterprise as part of a subscription)
```



更多信息请参见 [命令行安装 ](https://docs.nextcloud.com/server/latest/admin_manual/occ_command.html#command-line-installation-label)。







# SELinux 配置 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html#selinux-configuration)

当您的 Linux 发行版启用了 SELinux，在完成新的 Nextcloud 安装后，可能会遇到权限问题，并在 Nextcloud 日志中看到 `permission denied` 错误。

提示

权限问题即使在审计日志中没有显示拒绝信息，也可能由 SELinux 引起。这是因为 SELinux 并未记录所有用于验证访问的系统调用。请参见[静默拒绝的可能原因](https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/7/html/selinux_users_and_administrators_guide/sect-security-enhanced_linux-troubleshooting-fixing_problems#sect-Security-Enhanced_Linux-Fixing_Problems-Possible_Causes_of_Silent_Denials)以解决问题。

以下设置应该适用于大多数使用默认发行版配置文件的 SELinux 系统。请以 root 身份运行这些命令，并记得根据您的安装调整这些示例中的文件路径：

```
semanage fcontext -a -t httpd_sys_rw_content_t '/var/www/html/nextcloud/data(/.*)?'
semanage fcontext -a -t httpd_sys_rw_content_t '/var/www/html/nextcloud/config(/.*)?'
semanage fcontext -a -t httpd_sys_rw_content_t '/var/www/html/nextcloud/apps(/.*)?'
semanage fcontext -a -t httpd_sys_rw_content_t '/var/www/html/nextcloud/.htaccess'
semanage fcontext -a -t httpd_sys_rw_content_t '/var/www/html/nextcloud/.user.ini'
semanage fcontext -a -t httpd_sys_rw_content_t '/var/www/html/nextcloud/3rdparty/aws/aws-sdk-php/src/data/logs(/.*)?'

restorecon -Rv '/var/www/html/nextcloud/'
```



如果你卸载了 Nextcloud，需要移除 Nextcloud 目录的标签。为此，在卸载 Nextcloud 后，以 root 用户执行以下命令：

```
semanage fcontext -d '/var/www/html/nextcloud/data(/.*)?'
semanage fcontext -d '/var/www/html/nextcloud/config(/.*)?'
semanage fcontext -d '/var/www/html/nextcloud/apps(/.*)?'
semanage fcontext -d '/var/www/html/nextcloud/.htaccess'
semanage fcontext -d '/var/www/html/nextcloud/.user.ini'
semanage fcontext -d '/var/www/html/nextcloud/3rdparty/aws/aws-sdk-php/src/data/logs(/.*)?'

restorecon -Rv '/var/www/html/nextcloud/'
```



如果你已经自定义了 SELinux 策略且这些示例不起作用，你必须给 HTTP 服务器写访问权限以访问这些目录：

```
/var/www/html/nextcloud/data
/var/www/html/nextcloud/config
/var/www/html/nextcloud/apps
```



## 通过 Web 界面启用更新 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html#enable-updates-via-the-web-interface)

为了通过 Web 界面启用更新，你可能需要允许写访问这些目录：

```
setsebool httpd_unified on
```



更新完成后，禁用写权限：

```
setsebool -P  httpd_unified  off
```



## 禁止整个 Web 目录的写访问 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html#disallow-write-access-to-the-whole-web-directory)

出于安全原因，建议禁用对 /var/www/（默认）下所有文件夹的写访问：

```
setsebool -P  httpd_unified  off
```



## 允许访问远程数据库 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html#allow-access-to-a-remote-database)

如果您的安装连接到远程数据库，还需要进行以下设置：

```
setsebool -P httpd_can_network_connect_db on
```



## 允许访问 LDAP 服务器 [¶](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html#allow-access-to-ldap-server)

使用此设置允许 LDAP 连接：

```
setsebool -P httpd_can_connect_ldap on
```



## 允许访问远程网络 [¶](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html#allow-access-to-remote-network)

Nextcloud 需要访问远程网络以实现服务器间共享、外部存储或应用商店等功能。要允许这种访问，请使用以下设置：

```
setsebool -P httpd_can_network_connect on
```



## 允许访问网络 memcache[](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html#allow-access-to-network-memcache)

如果已经启用了 `httpd_can_network_connect`，则无需设置此选项：

```
setsebool -P httpd_can_network_memcache on
```



## 允许通过 sendmail 发送 SMTP/邮件访问 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html#allow-access-to-smtp-sendmail)

如果你希望允许 Nextcloud 通过 sendmail 发送邮件通知，需要使用以下设置：

```
setsebool -P httpd_can_sendmail on
```



## 允许通过 CIFS/SMB 访问 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html#allow-access-to-cifs-smb)

如果你将 datadir 放置在 CIFS/SMB 共享上，请使用以下设置：

```
setsebool -P httpd_use_cifs on
```



## 允许访问 FuseFS[](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html#allow-access-to-fusefs)

如果您的数据文件夹位于 Fuse 文件系统（例如 EncFS 等）上，此设置也是必需的：

```
setsebool -P httpd_use_fusefs on
```



## 允许 Rainloop 访问 GPG

如果你使用支持 GPG/PGP 的 Rainloop 网页邮件客户端应用，你可能需要这个：

```
setsebool -P httpd_use_gpg on
```



## 故障排除 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html#troubleshooting)

对于 SELinux 及其配置文件的通用故障排除，可以尝试安装 `setroubleshoot` 包，并运行：

```
sealert -a /var/log/audit/audit.log > /path/to/mylogfile.txt
```



以获取帮助你配置 SELinux 配置文件的报告。

另一个故障排除工具是只为你的 Nextcloud 目录启用单一规则集：

```
semanage fcontext -a -t httpd_sys_rw_content_t '/var/www/html/nextcloud(/.*)?'
restorecon -RF /var/www/html/nextcloud
```



相比之下，更细粒度的规则集（如示例开头所示）具有更强的安全性，因此仅用于测试和故障排除。它的效果类似于禁用 SELinux，因此不要在生产系统中使用。





# NGINX 配置 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/nginx.html#nginx-configuration)

警告

请注意，除了 Apache 2.x 之外的其他 Web 服务器均不被官方支持。

注意

本页面提供了 NGINX 配置示例，用于运行 Nextcloud 服务器。这些配置示例最初由 @josh4trunks 提供 并由社区独家维护。（感谢各位贡献者！）

- 你需要将以下代码插入到 **你的 NGINX 配置文件** 中。根据你是在 NGINX 的根目录下部署 Nextcloud（即 `https://cloud.example.com/`）还是在 NGINX 根目录下的子目录中部署 Nextcloud（即 `https://cloud.example.com/nextcloud` ），选择合适的示例。
- 将 `upstream php-handler` 部分的 server 指令调整为匹配你的 PHP 安装中配置的 FPM 监听器（此处的错误配置会导致 `502 Bad Gateway` 错误，请参阅 [PHP-Handler 配置 / 避免“502 Bad Gateway”](https://docs.nextcloud.com/server/latest/admin_manual/installation/nginx.html#nginx-php-handler-tips) 以获取详细信息）
- 将两个 `server_name` 指令调整为你的真实主机名
- 将 `root` 调整为你的 Nextcloud 安装的 webroot 路径
- 将 `ssl_certificate` 和 `ssl_certificate_key` 指令调整为你已签名的证书和私钥的实际路径。确保你的 SSL 证书对 nginx 服务器进程是可读的（请参阅 [nginx HTTPS SSL 模块文档 ](https://wiki.nginx.org/HttpSslModule)）。
- 请注意，如果复制示例，请小心换行，因为长行可能会为了页面显示而被断开，从而导致配置文件无效。
- 某些环境可能需要将 `cgi.fix_pathinfo` 设置为 `1`。 `php.ini`



## NGINX 根目录下的 Nextcloud

当 Nextcloud 放置在 你的 NGINX 安装目录的 webroot。在这个示例中它是 `/var/www/nextcloud`，并通过 `http(s)://cloud.example.com/` 访问

```
# Version 2024-07-17

upstream php-handler {
    server 127.0.0.1:9000;
    #server unix:/run/php/php8.2-fpm.sock;
}

# Set the `immutable` cache control options only for assets with a cache busting `v` argument
map $arg_v $asset_immutable {
    "" "";
    default ", immutable";
}

server {
    listen 80;
    listen [::]:80;
    server_name cloud.example.com;

    # Prevent nginx HTTP Server Detection
    server_tokens off;

    # Enforce HTTPS
    return 301 https://$server_name$request_uri;
}

server {
    listen 443 ssl http2;
    listen [::]:443 ssl http2;
    # With NGinx >= 1.25.1 you should use this instead:
    # listen 443      ssl;
    # listen [::]:443 ssl;
    # http2 on;
    server_name cloud.example.com;

    # Path to the root of your installation
    root /var/www/nextcloud;

    # Use Mozilla's guidelines for SSL/TLS settings
    # https://mozilla.github.io/server-side-tls/ssl-config-generator/
    ssl_certificate     /etc/ssl/nginx/cloud.example.com.crt;
    ssl_certificate_key /etc/ssl/nginx/cloud.example.com.key;

    # Prevent nginx HTTP Server Detection
    server_tokens off;

    # HSTS settings
    # WARNING: Only add the preload option once you read about
    # the consequences in https://hstspreload.org/. This option
    # will add the domain to a hardcoded list that is shipped
    # in all major browsers and getting removed from this list
    # could take several months.
    #add_header Strict-Transport-Security "max-age=31536000; includeSubDomains; preload" always;

    # set max upload size and increase upload timeout:
    client_max_body_size 512M;
    client_body_timeout 300s;
    fastcgi_buffers 64 4K;

    # Enable gzip but do not remove ETag headers
    gzip on;
    gzip_vary on;
    gzip_comp_level 4;
    gzip_min_length 256;
    gzip_proxied expired no-cache no-store private no_last_modified no_etag auth;
    gzip_types application/atom+xml text/javascript application/javascript application/json application/ld+json application/manifest+json application/rss+xml application/vnd.geo+json application/vnd.ms-fontobject application/wasm application/x-font-ttf application/x-web-app-manifest+json application/xhtml+xml application/xml font/opentype image/bmp image/svg+xml image/x-icon text/cache-manifest text/css text/plain text/vcard text/vnd.rim.location.xloc text/vtt text/x-component text/x-cross-domain-policy;

    # Pagespeed is not supported by Nextcloud, so if your server is built
    # with the `ngx_pagespeed` module, uncomment this line to disable it.
    #pagespeed off;

    # The settings allows you to optimize the HTTP2 bandwidth.
    # See https://blog.cloudflare.com/delivering-http-2-upload-speed-improvements/
    # for tuning hints
    client_body_buffer_size 512k;

    # HTTP response headers borrowed from Nextcloud `.htaccess`
    add_header Referrer-Policy                   "no-referrer"       always;
    add_header X-Content-Type-Options            "nosniff"           always;
    add_header X-Frame-Options                   "SAMEORIGIN"        always;
    add_header X-Permitted-Cross-Domain-Policies "none"              always;
    add_header X-Robots-Tag                      "noindex, nofollow" always;

    # Remove X-Powered-By, which is an information leak
    fastcgi_hide_header X-Powered-By;

    # Set .mjs and .wasm MIME types
    # Either include it in the default mime.types list
    # and include that list explicitly or add the file extension
    # only for Nextcloud like below:
    include mime.types;
    types {
        text/javascript mjs;
	application/wasm wasm;
    }

    # Specify how to handle directories -- specifying `/index.php$request_uri`
    # here as the fallback means that Nginx always exhibits the desired behaviour
    # when a client requests a path that corresponds to a directory that exists
    # on the server. In particular, if that directory contains an index.php file,
    # that file is correctly served; if it doesn't, then the request is passed to
    # the front-end controller. This consistent behaviour means that we don't need
    # to specify custom rules for certain paths (e.g. images and other assets,
    # `/updater`, `/ocs-provider`), and thus
    # `try_files $uri $uri/ /index.php$request_uri`
    # always provides the desired behaviour.
    index index.php index.html /index.php$request_uri;

    # Rule borrowed from `.htaccess` to handle Microsoft DAV clients
    location = / {
        if ( $http_user_agent ~ ^DavClnt ) {
            return 302 /remote.php/webdav/$is_args$args;
        }
    }

    location = /robots.txt {
        allow all;
        log_not_found off;
        access_log off;
    }

    # Make a regex exception for `/.well-known` so that clients can still
    # access it despite the existence of the regex rule
    # `location ~ /(\.|autotest|...)` which would otherwise handle requests
    # for `/.well-known`.
    location ^~ /.well-known {
        # The rules in this block are an adaptation of the rules
        # in `.htaccess` that concern `/.well-known`.

        location = /.well-known/carddav { return 301 /remote.php/dav/; }
        location = /.well-known/caldav  { return 301 /remote.php/dav/; }

        location /.well-known/acme-challenge    { try_files $uri $uri/ =404; }
        location /.well-known/pki-validation    { try_files $uri $uri/ =404; }

        # Let Nextcloud's API for `/.well-known` URIs handle all other
        # requests by passing them to the front-end controller.
        return 301 /index.php$request_uri;
    }

    # Rules borrowed from `.htaccess` to hide certain paths from clients
    location ~ ^/(?:build|tests|config|lib|3rdparty|templates|data)(?:$|/)  { return 404; }
    location ~ ^/(?:\.|autotest|occ|issue|indie|db_|console)                { return 404; }

    # Ensure this block, which passes PHP files to the PHP process, is above the blocks
    # which handle static assets (as seen below). If this block is not declared first,
    # then Nginx will encounter an infinite rewriting loop when it prepends `/index.php`
    # to the URI, resulting in a HTTP 500 error response.
    location ~ \.php(?:$|/) {
        # Required for legacy support
        rewrite ^/(?!index|remote|public|cron|core\/ajax\/update|status|ocs\/v[12]|updater\/.+|ocs-provider\/.+|.+\/richdocumentscode(_arm64)?\/proxy) /index.php$request_uri;

        fastcgi_split_path_info ^(.+?\.php)(/.*)$;
        set $path_info $fastcgi_path_info;

        try_files $fastcgi_script_name =404;

        include fastcgi_params;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        fastcgi_param PATH_INFO $path_info;
        fastcgi_param HTTPS on;

        fastcgi_param modHeadersAvailable true;         # Avoid sending the security headers twice
        fastcgi_param front_controller_active true;     # Enable pretty urls
        fastcgi_pass php-handler;

        fastcgi_intercept_errors on;
        fastcgi_request_buffering off;

        fastcgi_max_temp_file_size 0;
    }

    # Serve static files
    location ~ \.(?:css|js|mjs|svg|gif|ico|jpg|png|webp|wasm|tflite|map|ogg|flac)$ {
        try_files $uri /index.php$request_uri;
        # HTTP response headers borrowed from Nextcloud `.htaccess`
        add_header Cache-Control                     "public, max-age=15778463$asset_immutable";
        add_header Referrer-Policy                   "no-referrer"       always;
        add_header X-Content-Type-Options            "nosniff"           always;
        add_header X-Frame-Options                   "SAMEORIGIN"        always;
        add_header X-Permitted-Cross-Domain-Policies "none"              always;
        add_header X-Robots-Tag                      "noindex, nofollow" always;
        add_header X-XSS-Protection                  "1; mode=block"     always;
        access_log off;     # Optional: Don't log access to assets
    }

    location ~ \.(otf|woff2?)$ {
        try_files $uri /index.php$request_uri;
        expires 7d;         # Cache-Control policy borrowed from `.htaccess`
        access_log off;     # Optional: Don't log access to assets
    }

    # Rule borrowed from `.htaccess`
    location /remote {
        return 301 /remote.php$request_uri;
    }

    location / {
        try_files $uri $uri/ /index.php$request_uri;
    }
}
```





## Nextcloud 子目录下的 NGINX 配置 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/nginx.html#nextcloud-in-a-subdir-of-the-nginx-webroot)

以下配置适用于 Nextcloud 放置在子目录中的情况： 你的 NGINX 安装的根目录。 在本例中，Nextcloud 文件位于 `/var/www/nextcloud`，并且 Nextcloud 实例通过 `http(s)://cloud.example.com/nextcloud/` 访问。与上方的“Nextcloud 在 web 根目录中”的配置相比，配置方式有所不同：

- 所有针对 `/nextcloud` 的请求都被封装在单一的 `location` 块中，即 `location ^~ /nextcloud`。
- 字符串 `/nextcloud` 被添加到所有前缀路径的前面。
- 该域名的根目录映射到 `/var/www`，而不是 `/var/www/nextcloud`，因此 URI`/nextcloud` 映射到服务器目录 `/var/www/nextcloud`。
- 处理 `/nextcloud` 之外路径的块（即 `/robots.txt` 和 `/.well-known`）被从 `location ^~ /nextcloud` 块中移出。
- 处理 /.well-known 的块不需要正则表达式例外，因为防止用户访问 Nextcloud 安装根目录下隐藏文件夹的规则不再匹配该路径。

```
upstream php-handler {
    server 127.0.0.1:9000;
    #server unix:/run/php/php8.2-fpm.sock;
}

# Set the `immutable` cache control options only for assets with a cache busting `v` argument
map $arg_v $asset_immutable {
    "" "";
    default ", immutable";
}

server {
    listen 80;
    listen [::]:80;
    server_name cloud.example.com;

    # Prevent nginx HTTP Server Detection
    server_tokens off;

    # Enforce HTTPS just for `/nextcloud`
    location /nextcloud {
        return 301 https://$server_name$request_uri;
    }
}

server {
    listen 443      ssl http2;
    listen [::]:443 ssl http2;
    # With NGinx >= 1.25.1 you should use this instead:
    # listen 443      ssl;
    # listen [::]:443 ssl;
    # http2 on;
    server_name cloud.example.com;

    # Path to the root of the domain
    root /var/www;

    # Use Mozilla's guidelines for SSL/TLS settings
    # https://mozilla.github.io/server-side-tls/ssl-config-generator/
    ssl_certificate     /etc/ssl/nginx/cloud.example.com.crt;
    ssl_certificate_key /etc/ssl/nginx/cloud.example.com.key;

    # Prevent nginx HTTP Server Detection
    server_tokens off;

    # Set .mjs and .wasm MIME types
    # Either include it in the default mime.types list
    # and include that list explicitly or add the file extension
    # only for Nextcloud like below:
    include mime.types;
    types {
        text/javascript mjs;
	application/wasm wasm;
    }

    location = /robots.txt {
        allow all;
        log_not_found off;
        access_log off;
    }

    location ^~ /.well-known {
        # The rules in this block are an adaptation of the rules
        # in the Nextcloud `.htaccess` that concern `/.well-known`.

        location = /.well-known/carddav { return 301 /nextcloud/remote.php/dav/; }
        location = /.well-known/caldav  { return 301 /nextcloud/remote.php/dav/; }

        location /.well-known/acme-challenge    { try_files $uri $uri/ =404; }
        location /.well-known/pki-validation    { try_files $uri $uri/ =404; }

        # Let Nextcloud's API for `/.well-known` URIs handle all other
        # requests by passing them to the front-end controller.
        return 301 /nextcloud/index.php$request_uri;
    }

    location ^~ /nextcloud {
        # set max upload size and increase upload timeout:
        client_max_body_size 512M;
        client_body_timeout 300s;
        fastcgi_buffers 64 4K;

        # Enable gzip but do not remove ETag headers
        gzip on;
        gzip_vary on;
        gzip_comp_level 4;
        gzip_min_length 256;
        gzip_proxied expired no-cache no-store private no_last_modified no_etag auth;
        gzip_types application/atom+xml text/javascript application/javascript application/json application/ld+json application/manifest+json application/rss+xml application/vnd.geo+json application/vnd.ms-fontobject application/wasm application/x-font-ttf application/x-web-app-manifest+json application/xhtml+xml application/xml font/opentype image/bmp image/svg+xml image/x-icon text/cache-manifest text/css text/plain text/vcard text/vnd.rim.location.xloc text/vtt text/x-component text/x-cross-domain-policy;

        # Pagespeed is not supported by Nextcloud, so if your server is built
        # with the `ngx_pagespeed` module, uncomment this line to disable it.
        #pagespeed off;

        # The settings allows you to optimize the HTTP2 bandwidth.
        # See https://blog.cloudflare.com/delivering-http-2-upload-speed-improvements/
        # for tuning hints
        client_body_buffer_size 512k;

        # HSTS settings
        # WARNING: Only add the preload option once you read about
        # the consequences in https://hstspreload.org/. This option
        # will add the domain to a hardcoded list that is shipped
        # in all major browsers and getting removed from this list
        # could take several months.
        #add_header Strict-Transport-Security "max-age=31536000; includeSubDomains; preload" always;

        # HTTP response headers borrowed from Nextcloud `.htaccess`
        add_header Referrer-Policy                   "no-referrer"       always;
        add_header X-Content-Type-Options            "nosniff"           always;
        add_header X-Frame-Options                   "SAMEORIGIN"        always;
        add_header X-Permitted-Cross-Domain-Policies "none"              always;
        add_header X-Robots-Tag                      "noindex, nofollow" always;

        # Remove X-Powered-By, which is an information leak
        fastcgi_hide_header X-Powered-By;

        # Specify how to handle directories -- specifying `/nextcloud/index.php$request_uri`
        # here as the fallback means that Nginx always exhibits the desired behaviour
        # when a client requests a path that corresponds to a directory that exists
        # on the server. In particular, if that directory contains an index.php file,
        # that file is correctly served; if it doesn't, then the request is passed to
        # the front-end controller. This consistent behaviour means that we don't need
        # to specify custom rules for certain paths (e.g. images and other assets,
        # `/updater`, `/ocs-provider`), and thus
        # `try_files $uri $uri/ /nextcloud/index.php$request_uri`
        # always provides the desired behaviour.
        index index.php index.html /nextcloud/index.php$request_uri;

        # Rule borrowed from `.htaccess` to handle Microsoft DAV clients
        location = /nextcloud {
            if ( $http_user_agent ~ ^DavClnt ) {
                return 302 /nextcloud/remote.php/webdav/$is_args$args;
            }
        }

        # Rules borrowed from `.htaccess` to hide certain paths from clients
        location ~ ^/nextcloud/(?:build|tests|config|lib|3rdparty|templates|data)(?:$|/)    { return 404; }
        location ~ ^/nextcloud/(?:\.|autotest|occ|issue|indie|db_|console)                  { return 404; }

        # Ensure this block, which passes PHP files to the PHP process, is above the blocks
        # which handle static assets (as seen below). If this block is not declared first,
        # then Nginx will encounter an infinite rewriting loop when it prepends
        # `/nextcloud/index.php` to the URI, resulting in a HTTP 500 error response.
        location ~ \.php(?:$|/) {
            # Required for legacy support
            rewrite ^/nextcloud/(?!index|remote|public|cron|core\/ajax\/update|status|ocs\/v[12]|updater\/.+|ocs-provider\/.+|.+\/richdocumentscode(_arm64)?\/proxy) /nextcloud/index.php$request_uri;

            fastcgi_split_path_info ^(.+?\.php)(/.*)$;
            set $path_info $fastcgi_path_info;

            try_files $fastcgi_script_name =404;

            include fastcgi_params;
            fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
            fastcgi_param PATH_INFO $path_info;
            fastcgi_param HTTPS on;

            fastcgi_param modHeadersAvailable true;         # Avoid sending the security headers twice
            fastcgi_param front_controller_active true;     # Enable pretty urls
            fastcgi_pass php-handler;

            fastcgi_intercept_errors on;
            fastcgi_request_buffering off;

            fastcgi_max_temp_file_size 0;
        }

        # Serve static files
        location ~ \.(?:css|js|mjs|svg|gif|ico|jpg|png|webp|wasm|tflite|map|ogg|flac)$ {
            try_files $uri /nextcloud/index.php$request_uri;
            # HTTP response headers borrowed from Nextcloud `.htaccess`
            add_header Cache-Control                     "public, max-age=15778463$asset_immutable";
            add_header Referrer-Policy                   "no-referrer"       always;
            add_header X-Content-Type-Options            "nosniff"           always;
            add_header X-Frame-Options                   "SAMEORIGIN"        always;
            add_header X-Permitted-Cross-Domain-Policies "none"              always;
            add_header X-Robots-Tag                      "noindex, nofollow" always;
            add_header X-XSS-Protection                  "1; mode=block"     always;
            access_log off;     # Optional: Don't log access to assets
        }

        location ~ \.(otf|woff2?)$ {
            try_files $uri /nextcloud/index.php$request_uri;
            expires 7d;         # Cache-Control policy borrowed from `.htaccess`
            access_log off;     # Optional: Don't log access to assets
        }

        # Rule borrowed from `.htaccess`
        location /nextcloud/remote {
            return 301 /nextcloud/remote.php$request_uri;
        }

        location /nextcloud {
            try_files $uri $uri/ /nextcloud/index.php$request_uri;
        }
    }
}
```



## 技巧和窍门 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/nginx.html#tips-and-tricks)



### PHP-Handler 配置 / 避免“502 Bad Gateway”[](https://docs.nextcloud.com/server/latest/admin_manual/installation/nginx.html#php-handler-configuration-avoiding-502-bad-gateway)

上述 `server` 行需要调整以反映您本地的 PHP FPM 配置。它必须与您将用于 Nextcloud 的 PHP FPM 池中 `listen` 指令配置相匹配。

许多 Linux 发行版在名为 `www.conf` 的文件中为默认的 PHP-FPM 池定义了一个监听器，该文件通常位于类似 `/etc/php/8.1/pool.d` 的位置。

查找设置为类似以下内容的行：

`listen = /var/run/php/php-fpm.sock` or ``` listen = 127.0.0.1:9000 ```

如果 PHP FPM 将在同一主机上运行 NGINX（如果你不确定的话，这是一个安全的假设），那么为了获得最佳性能，建议使用 UNIX 套接字（即 `/var/run/php/php-fpm.sock`）而不是 TCP（`127.0.0.1:9000`）。尽管如此，只要 NGINX 和 PHP FPM 的配置匹配，两者都可以正常工作。

在决定如何连接 NGINX 与 PHP FPM 后（如果需要，更新本地 PHP FPM 配置并重启 FPM），设置 NGINX 配置中的 ``upstream php-handler``server`` 以符合你的偏好（注意：如果使用 UNIX 套接字，请在 NGINX 配置中以 `unix:` 开头，但在 PHP FPM 的 `www.conf` 中不要加上 `unix:`）。

### 抑制日志消息 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/nginx.html#suppressing-log-messages)

如果你的日志文件中出现了无意义的消息，例如 `client denied by server configuration: /var/www/data/htaccesstest.txt` ，可以在 NGINX 配置中添加以下部分来抑制这些消息：

```
location = /data/htaccesstest.txt {
  allow all;
  log_not_found off;
  access_log off;
}
```



### JavaScript (.js) 或 CSS (.css) 文件未正确提供 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/nginx.html#javascript-js-or-css-css-files-not-served-properly)

自定义 NGINX 配置时常见的问题是，JavaScript（.js）或 CSS（.css）文件无法正确提供，导致这些文件出现 404（文件未找到）错误，从而使网页界面无法正常显示。

这可能是由以下原因引起的：

```
location ~* \.(?:css|js)$ {
```



block 显示在上述内容**下方** ：

```
location ~ \.php(?:$|\/) {
```



block。其他自定义配置，如通过 gzip 缓存 JavaScript (.js)或 CSS (.css)文件，也可能导致此类问题。

这个问题的另一个原因是未正确在 http 块中包含 mimetypes，如[此处](#0)所示。

### 上传大于 10 MiB 的文件会失败[](#0)

如果你全局配置了 nginx 禁止访问隐藏的点文件，由于 Nextcloud 的要求，上传大于 10 MiB 的文件可能会因为文件需要上传到以`/.file`结尾的 URL 而无法通过网页完成。

你可能需要更改：

```
location ~ /\. {
```



将以下内容添加以重新允许文件上传：

```
location ~ /\.(?!file).* {
```



有关更多信息，请参见 [issue #8802 on nextcloud/server](https://github.com/nextcloud/server/issues/8802)。

除了上述参数外，还有其他参数与上传大文件相关（请参见 [上传大文件（>512MB）](https://docs.nextcloud.com/server/latest/admin_manual/configuration_files/big_file_upload_configuration.html#uploading-big-files)）。

### 登录循环，access.log、error.log 和 nextcloud.log 中没有任何线索 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/nginx.html#login-loop-without-any-clue-in-access-log-error-log-nor-nextcloud-log)

如果在全新安装（Centos 7 与 nginx）后首次登录出现问题，你应该首先检查这些文件：

```
tail /var/www/nextcloud/data/nextcloud.log
tail /var/log/nginx/access.log
tail /var/log/nginx/error.log
```



如果只在访问日志中看到一些正确的请求，但没有登录发生，你应该检查 php 会话和 wsdlcache 目录的访问权限。尝试检查权限并根据需要进行更改：

```
chown nginx:nginx /var/lib/php/session/
chown root:nginx /var/lib/php/wsdlcache/
chown root:nginx /var/lib/php/opcache/
```







# 加固与安全指南 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#hardening-and-security-guidance)

Nextcloud 旨在提供安全的默认设置，无需管理员进行修改。但在某些情况下，如果管理员完全控制 Nextcloud 实例，可以应用额外的安全加固措施。本页面假设您在 Linux 环境中使用 Apache2 运行 Nextcloud 服务器。

注意

Nextcloud 会在管理界面中警告您，如果缺少某些关键的安全相关选项。然而，系统安全的审查和维护仍然由服务器管理员负责。

## 密码 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#passwords)

### 访问令牌的存储 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#storage-of-access-tokens)

成功认证后，Nextcloud 会发放一个访问令牌，客户端将使用该令牌进行所有后续的 HTTP 请求。该访问令牌唯一标识用户，不应存储在请求该令牌的客户端以外的任何系统中。用户密码也会以加密形式存储在 Nextcloud 数据库中。为了加密密码，令牌会使用一个实例特定的密钥。

访问令牌的泄露可能会带来负面的安全后果。根据行为者的数据访问权限，风险程度不同：

- 仅拥有访问令牌的行为者可以冒充用户并以该用户身份登录。
- 拥有访问令牌、Nextcloud 配置文件和 Nextcloud 数据库访问权限的攻击者可以解密数据库中存储的用户密码。

### 密码长度限制 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#limit-on-password-length)

Nextcloud 使用 bcrypt 算法，出于安全性和性能考虑，例如随着 CPU 负荷的增加，CPU 需求呈指数级增长，它仅验证密码的前 72 个字符。这适用于 Nextcloud 中使用的所有密码：用户密码、链接共享密码和外部共享密码。

## 操作系统 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#operating-system)



### 给 PHP 授予读取访问权限 `/dev/urandom`[](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#give-php-read-access-to-dev-urandom)

Nextcloud 使用符合 [RFC 4086（“安全所需的随机性要求”）](https://tools.ietf.org/html/rfc4086#section-5.2) 的混洗器来生成密码安全的伪随机数。这意味着在生成随机数时，Nextcloud 将从不同的来源请求多个随机数，并从中推导出最终的随机数。

随机数生成还会尝试从系统请求随机数 `/dev/urandom`，因此强烈建议配置您的环境，使 PHP 能够从中读取随机数据。

注意

当在你的 ``php.ini`` 文件中配置了 ``open_basedir`` 时，请确保包含 ``/dev/urandom``。

### 启用加固模块，如 SELinux[](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#enable-hardening-modules-such-as-selinux)

强烈建议在可能的情况下启用加固模块，如 SELinux。请参阅 [SELinux 配置 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html)以了解更多信息。

## 部署 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#deployment)

### 将数据目录放置在 Web 根目录之外 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#place-data-directory-outside-of-the-web-root)

强烈建议将数据目录放置在 Web 根目录之外（即，放置在 `/var/www` 之外）。在新安装时，这最为简便。

### 禁用预览图片生成 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#disable-preview-image-generation)

Nextcloud 能够生成常见文件类型的预览图片，如图片或文本文件。默认情况下，对于我们认为足够安全可以部署的某些文件类型，预览生成功能是启用的。然而，管理员应意识到，这些预览是使用用 C 语言编写的 PHP 库生成的，可能会受到攻击向量的影响。

对于高安全部署，我们建议通过在 `config.php` 中将 `enable_previews` 开关设置为 `false` 来禁用预览生成。作为管理员，您还可以通过修改 `enabledPreviewProviders` 选项开关来管理启用哪些预览提供者。

### 禁用调试模式 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#disable-debug-mode)

确保你的 `config.php` 中 ``debug`` 的值为 ``false``。默认值为 ``false``。 在新安装中（或未指定时）不应启用。在生产环境中不应启用。 在非目标调试环境中或外部。启用时，事物 允许在整个服务器范围内列出 WebDAV 集合。这仅适用于本地环境。 仅在受控环境中进行开发和使用。



## 使用 HTTPS

不使用加密的 HTTPS 连接会使得你的服务器面临中间人（MITM）攻击的风险，并可能导致用户数据和密码被截获。在生产服务器上始终使用 HTTPS，并且绝不允许使用未加密的 HTTP，这是最佳实践，强烈推荐这样做。

如何在 Web 服务器上设置 HTTPS 取决于您的配置，请参阅您所使用的 HTTP 服务器的文档。以下示例适用于 Apache。

### 将所有未加密的流量重定向到 HTTPS[](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#redirect-all-unencrypted-traffic-to-https)

为了将所有 HTTP 流量重定向到 HTTPS，管理员建议使用 301 状态码进行永久重定向。使用 Apache 时，这可以通过在 Apache 虚拟主机配置中设置如下内容来实现：

```
<VirtualHost *:80>
   ServerName cloud.nextcloud.com
   Redirect permanent / https://cloud.nextcloud.com/
</VirtualHost>
```





### 启用 HTTP 严格传输安全 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#enable-http-strict-transport-security)

虽然将所有流量重定向到 HTTPS 是很好的做法，但可能无法完全防止中间人攻击。因此，管理员被建议设置 HTTP 严格传输安全标头，该标头指示浏览器不允许使用 HTTP 连接到 Nextcloud 实例，并试图防止访客绕过无效证书警告。

这可以通过在 Apache 虚拟主机文件中设置以下配置来实现：

```
<VirtualHost *:443>
  ServerName cloud.nextcloud.com
    <IfModule mod_headers.c>
      Header always set Strict-Transport-Security "max-age=15552000; includeSubDomains"
    </IfModule>
 </VirtualHost>
```



警告

我们建议在该头部中添加额外设置 ``preload``。这样，该域将被添加到所有主要浏览器自带的硬编码列表中，并强制这些域使用 HTTPS。有关更多信息，请参阅 [HSTS 预加载网站 ](https://hstspreload.org/)。由于该列表的政策，您需要在确定这是您想要的之后，自己将其添加到上述示例中。从该列表中移除该域可能需要几个月的时间，直到所有安装的浏览器都更新了该列表。

此示例配置将使所有子域名仅可通过 HTTPS 访问。如果您有无法通过 HTTPS 访问的子域名，请移除 ``includeSubDomains``。

这需要在 Apache 中启用 ``mod_headers`` 扩展。

### 正确的 SSL 配置 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#proper-ssl-configuration)

默认的 Web 服务器 SSL 配置通常并不是最先进的，需要进行精细调整以获得最佳性能和安全性体验。可用的 SSL 密码套件和选项完全取决于您的环境，因此给出通用建议并不现实。

我们建议使用 [Mozilla SSL 配置生成器](https://mozilla.github.io/server-side-tls/ssl-config-generator/)来生成适合您环境的配置。您可以使用免费的 [Web TLS 分析器](https://tlsprofiler.danielfett.de/)服务来验证您的配置。该服务会提供详细的错误信息，如果您的服务器的 TLS 设置与 Mozilla 配置不符。另一个检查服务器 TLS 配置的有用工具是免费的 [Qualys SSL Labs 测试 ](https://www.ssllabs.com/ssltest/)，它会提供关于 TLS 设置的一般信息。

同样，请确保禁用 HTTP 压缩以缓解 BREACH 攻击。

## 限制管理员操作的 IP 地址范围 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#restrict-admin-actions-to-a-specific-range-of-ip-addresses)

在`config.php`中配置`allowed_admin_ranges`，以将管理员操作限制在受信任的 IP 范围。

这可以通过类似以下的设置实现，通常使用私有 IP 范围：

```
'allowed_admin_ranges' => [
  '127.0.0.1/8',
  '192.168.0.0/16',
  'fd00::/8',
],
```



所有来自这些范围之外 IP 地址的请求将无法执行管理员操作。

连接来自不受信任 IP 地址的管理员将能够使用 Nextcloud，但所有与管理员特定相关的行为都将被隐藏。

## 使用专用域名安装 Nextcloud[](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#use-a-dedicated-domain-for-nextcloud)

管理员应将 Nextcloud 安装在专用域名，如 cloud.domain.tld 而不是 domain.tld，以充分利用同源策略所提供的所有优势。

## 确保您的 Nextcloud 实例安装在 DMZ 中 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#ensure-that-your-nextcloud-instance-is-installed-in-a-dmz)

由于 Nextcloud 支持如联邦文件共享等功能，我们不将服务器端请求伪造（SSRF）视为威胁模型的一部分。实际上，考虑到我们所有的外部存储适配器，这可以被视为一个功能而不是漏洞。

这意味着您的 Nextcloud 实例中的用户可以探测其他主机是否可以从 Nextcloud 网络访问。如果您不希望这种情况发生，您需要确保您的 Nextcloud 正确安装在隔离网络中，并且有适当的防火墙规则。

## 通过 Web 服务器提供安全相关的头部信息 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#serve-security-related-headers-by-the-web-server)

默认环境中，Nextcloud 已经提供了基本的安全头部信息，包括：

- - `X-Content-Type-Options: nosniff`

    指示某些浏览器不要嗅探文件的 mimetype。例如，这可以防止浏览器将文本文件解释为 JavaScript。

- - `X-Robots-Tag: noindex, nofollow`

    指示搜索引擎不要索引这些页面，也不跟随页面中的任何链接。

- - `X-Frame-Options: SAMEORIGIN`

    防止将 Nextcloud 实例嵌入到其他域的 iframe 中，以防止点击劫持等类似攻击。

- - `Referrer-Policy: no-referrer`

    默认的 no-referrer 策略指示浏览器在向任何源发送请求时不要发送 referrer 信息。

这些头部信息已硬编码到 Nextcloud 服务器中，无需服务器管理员进行任何干预。

为了达到最佳安全效果，管理员应通过 Web 服务器提供这些基本的 HTTP 头，以在响应中强制执行它们。为此，Apache 需要配置使用 `.htaccess` 文件，并启用以下 Apache 模块：

- mod_headers
- mod_env

管理员可以通过访问 Web 服务器提供的静态资源来验证此安全更改是否生效，并检查上述安全头是否已发送。

## 远程服务器连接 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#connections-to-remote-servers)

某些功能需要 Nextcloud 服务器能够通过 https/443 连接到远程系统。本段还包含了 Nextcloud GmbH 接收的数据。根据您的服务器配置，这些是可能的连接：

- - nextcloud.com, startpage.com, eff.org, edri.org

    [可选（配置）](https://docs.nextcloud.com/server/latest/admin_manual/configuration_server/config_sample_php_parameters.html#has-internet-connection)用于检查互联网连接

- - cloud.nextcloud.com

    用于企业许可监控提交的数据：订阅密钥，用户数量

- - updates.nextcloud.com

    检查可用的 Nextcloud 服务器更新提交的数据：服务器版本、订阅密钥、安装时间、实例 ID、实例大小

- - apps.nextcloud.com

    检查可用的应用及其更新提交的数据：订阅密钥

- - github.com, objects.githubusercontent.com

    下载 Nextcloud 标准应用下载 Nextcloud 服务器版本

- - push-notifications.nextcloud.com

    向移动客户端发送推送通知提交的数据：唯一设备标识符、公钥、推送令牌

- - pushfeed.nextcloud.com

    可选检查 Nextcloud 公告应用中是否有可用更新

- - lookup.nextcloud.com

    可选用于更新和查找联邦共享地址簿提交的数据： *待定*

- - surveyserver.nextcloud.com

    可选如果管理员同意共享匿名服务器数据提交的数据：统计数据。详细字段列表请参见此处 [详细字段列表](https://github.com/nextcloud/survey_client)

- 任何通过联邦共享连接的远程 Nextcloud 服务器

## 设置 fail2ban [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#setup-fail2ban)

将服务器暴露在互联网上不可避免地会使运行在互联网暴露端口上的服务面临暴力破解登录尝试。

本指南将在操作系统层面阻止发起的 IP 地址，这样 web 服务器、PHP 和数据库都不需要处理这种不必要的流量。

### Nextcloud 前提条件 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#nextcloud-prerequisites)

Nextcloud 在 `nextcloud.log` 中以日志级别 `2` 记录失败的登录尝试，因此你需要在 `config.php` 中定义一个日志级别为 `2` 或更低。

确保你的 `nextcloud.log` 文件对你的 web 服务器用户是可写的，可能需要在 `config.php` 中正确定义 `logfilemode`。

进行一次错误登录尝试，并检查是否会被记录到 `nextcloud.log` 中。

请注意，如果启用了 `audit.log`，它目前只记录成功的登录，无法使用。

### Fail2ban 简介 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#fail2ban-introduction)

Fail2ban 是一个服务，它使用 iptables 自动在一定时间内拒绝来自连续认证失败的 IP 地址的连接。

要设置 fail2ban，首先需要在服务器上下载并安装它。可以在 [fail2ban 下载页面 ](https://www.fail2ban.org/wiki/index.php/Downloads) 找到多个发行版的下载。它通常可以从大多数发行版的包管理器中获得（例如 `apt-get`）。

Fail2ban 的标准配置路径是 `/etc/fail2ban`。

### 设置过滤器和沙箱用于 Nextcloud

过滤器定义正则表达式规则，用于识别用户在 Nextcloud 用户界面、WebDAV 或使用不受信任的域名访问服务器时的认证失败情况。

在 `/etc/fail2ban/filter.d` 目录下创建一个名为 `nextcloud.conf` 的文件，内容如下：

```
[Definition]
_groupsre = (?:(?:,?\s*"\w+":(?:"[^"]+"|\w+))*)
failregex = ^\{%(_groupsre)s,?\s*"remoteAddr":"<HOST>"%(_groupsre)s,?\s*"message":"Login failed:
            ^\{%(_groupsre)s,?\s*"remoteAddr":"<HOST>"%(_groupsre)s,?\s*"message":"Two-factor challenge failed:
            ^\{%(_groupsre)s,?\s*"remoteAddr":"<HOST>"%(_groupsre)s,?\s*"message":"Trusted domain error.
datepattern = ,?\s*"time"\s*:\s*"%%Y-%%m-%%d[T ]%%H:%%M:%%S(%%z)?"
```



监禁文件定义了如何处理 Nextcloud 过滤器发现的认证失败尝试。

在 `/etc/fail2ban/jail.d` 目录下创建一个名为 `nextcloud.local` 的文件，内容如下：

```
[nextcloud]
backend = auto
enabled = true
port = 80,443
protocol = tcp
filter = nextcloud
maxretry = 3
bantime = 86400
findtime = 43200
logpath = /path/to/data/directory/nextcloud.log
```



确保将 ``logpath`` 替换为您的安装路径中的 ``nextcloud.log``。 如果您的 Web 服务器使用的是除 ``80`` 和 ``443`` 之外的端口，也应该进行替换。``bantime`` 和 ``findtime`` 的单位是秒。

重启 fail2ban 服务。你可以通过运行以下命令检查 Nextcloud 监狱的状态：

```
fail2ban-client status nextcloud
```



如果你需要解封某些 IP 地址（例如这里的 `1.2.3.4`），可以通过以下命令来实现：

```
fail2ban-client unban 1.2.3.4
```



在某些情况下，你可能希望永久封禁那些反复产生不良登录尝试（或其他攻击）的 IP 地址，这时可以使用 fail2ban 的 `recidive` 功能。







# 服务器调优 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#server-tuning)

## 使用 cron 执行后台任务 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#using-cron-to-perform-background-jobs)

请参阅 [后台任务 ](https://docs.nextcloud.com/server/latest/admin_manual/configuration_server/background_jobs_configuration.html)以了解描述和优势。

## 降低系统负载 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#reducing-system-load)

高系统负载会减慢 Nextcloud 的运行速度，并可能导致其他不良后果。要减轻负载，您首先需要找出问题的根源。使用如 htop、iotop、[netdata](https://my-netdata.io/) 或 [glances](https://nicolargo.github.io/glances/) 等工具可以帮助您识别拖慢系统运行的进程或磁盘。首先 您应该确保已安装/分配足够的内存。交换空间的使用量应该 以一切手段防止这种情况发生。如果你在虚拟机中运行数据库，应避免这样做。 将其存放在虚拟机镜像文件中。最好将其放在一个专用的块设备上。 减少多层抽象导致的延迟。



## 日志级别 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#log-levels)

验证 `loglevel` 在你的 `config.php` 中。新安装的默认日志级别设置为 `2`（WARN）。有时在故障排除事件后，该参数可能会无意中保持在 DEBUG 级别（`0`）。在一些较旧的安装中，该参数也可能不是默认值。当你需要诊断问题时使用 `0`（DEBUG），然后将日志级别重置为更少的输出级别。DEBUG 会输出大量信息，可能会影响服务器性能。

## 调试模式 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#debug-mode)

验证你的 `config.php` 中 `debug` 是否为 `false`。默认情况下，在新安装中（或未指定时）`debug` 为 `false`。虽然这个选项类似于 DEBUG 日志级别，但它还会禁用各种优化（以便更容易进行调试）并在浏览器和服务器端生成额外的调试输出。在生产环境中不应启用此选项，除非在孤立的故障排查情况下。

## 缓存 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#id1)

缓存通过将数据、代码和其他对象存储在内存中来提高性能。Nextcloud 服务器的内存缓存配置必须安装并配置。请参阅 [内存缓存 ](https://docs.nextcloud.com/server/latest/admin_manual/configuration_server/caching_configuration.html)。

## 压缩 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#compression)

启用 Web 服务器对 JavaScript、CSS 和 SVG 文件进行压缩可以提高性能，因为这样可以减少传输给客户端的字节数。

## 使用 MariaDB/MySQL 代替 SQLite[](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#using-mariadb-mysql-instead-of-sqlite)

由于 SQLite 在高并发应用（如 Nextcloud）中存在性能限制，因此推荐使用 MySQL 或 MariaDB。

请参阅“数据库配置”部分，了解如何为 MySQL 或 MariaDB 配置 Nextcloud。如果您的安装已经在使用 SQLite，则可以通过提供的步骤将数据库类型转换为 MySQL 或 MariaDB，详见“转换数据库类型”部分。

要获取更多详细信息和帮助调整您的数据库，请参阅 [MariaDB 的这篇文章 ](https://mariadb.com/kb/en/optimization-and-tuning/)。

## 使用基于 Redis 的事务性文件锁定 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#using-redis-based-transactional-file-locking)

文件锁定默认是启用的，使用的是数据库锁定后端。这 对您的数据库造成了显著的负载。请参阅相关章节。 [基于 Redis 的事务性文件锁定 ](https://docs.nextcloud.com/server/latest/admin_manual/configuration_files/files_locking_transactional.html)，了解如何配置 Nextcloud 使用基于 Redis 的事务性文件锁定。

## TLS / 加密应用 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#tls-encryption-app)

TLS（HTTPS）和文件加密/解密可以卸载到处理器的 AES-NI 扩展中。这不仅可以加快这些操作的速度，还可以降低处理开销。这需要一个支持 [AES-NI 指令集](https://wikipedia.org/wiki/AES_instruction_set)的处理器。

以下是一些检查您的 CPU/环境是否支持 AES-NI 扩展的方法：

- 对于每个现有的 CPU 核心：`grep flags /proc/cpuinfo` 或者作为所有核心的汇总： `grep -m 1 '^flags' /proc/cpuinfo` 如果结果包含任何 `aes`，则该扩展已存在。
- 可以在 Intel 官网搜索以检查所用处理器是否支持该扩展 [Intel Processor Feature Filter](https://ark.intel.com/MySearch.aspx?AESTech=true) 您可以设置一个过滤器 将 `"AES New Instructions"` 以获得一个缩小的结果集。
- 对于 OpenSSL 版本 >= 1.0.1，AES-NI 不会通过引擎工作，也不会在 `openssl engine` 命令中显示。它在受支持的硬件上默认启用。你可以通过 `openssl version -a` 检查 OpenSSL 版本。
- 如果你的处理器支持 AES-NI 但未显示（例如通过 grep 或 coreinfo），可能是 BIOS 中禁用了它。
- 如果你的环境是虚拟化的，请检查虚拟化供应商是否支持。

## 启用 HTTP/2 以加快加载速度 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#enable-http-2-for-faster-loading)

HTTP/2 在多请求情况下相比 HTTP 有巨大的速度提升。大多数 [浏览器已经支持通过 TLS（HTTPS）使用 HTTP/2](https://www.troyhunt.com/i-wanna-go-fast-https-massive-speed-advantage/)。请参阅您的 Web 服务器手册以获取启用 HTTP/2 的指南。

## 调整 PHP-FPM [](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#tune-php-fpm)

如果你使用的是 PHP-FPM 的默认安装，可能会注意到网页界面加载时间过长，甚至出现同步问题。这是因为每个同时请求的元素都由一个独立的 PHP-FPM 进程处理。因此，即使在小型安装中，你也应该允许更多的进程并行运行以处理请求。

[此链接](https://spot13.com/pmcalculator/)可以帮助你计算适合你系统的最佳值。

## 启用 PHP OPcache [](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#enable-php-opcache)

OPcache 改善了 PHP 应用程序的性能，通过缓存预编译的字节码。

### 重新验证 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#revalidation)

PHP 中的 OPcache 重新验证处理存储在磁盘上的 PHP 应用程序代码的更改。每当发生以下情况时，代码会发生更改：

- Nextcloud 或 Nextcloud 应用被升级
- 进行了配置更改（例如修改了 `config.php`）

Nextcloud 尽可能在需要时在内部处理缓存重新验证。但这并非万无一失。在默认的 PHP 环境中，重新验证是启用的，并且缓存的脚本每 `2` 秒重新验证一次，以确保磁盘上的更改能够生效。在许多环境中，这些默认值是合理的（并且可能永远不需要更改）。

然而，重新验证的频率可以调整，并且可能会潜在地提高性能。我们在这里不推荐任何关于重新验证适当值的建议（除了 PHP 默认值）。

危险

延长重新验证的时间间隔（或完全禁用此功能）意味着手动修改脚本，包括 ``config.php``，将在更长时间后生效（或者如果完全禁用重新验证，则永远不会生效）。延长此时间间隔还会增加临时服务器和应用程序升级问题的可能性。这也会阻止正确切换维护模式。

警告

如果您调整了这些参数，那么在进行配置更改或执行升级后，您更有可能需要重启或重新加载您的 Web 服务器（mod_php）或 fpm。如果您忘记执行这些操作，可能会因为磁盘上的内容与内存中的内容不匹配而出现异常行为。这些情况可能会看起来像是 bug，但只要您重启或重新加载 mod_php/fpm，这些问题就会消失。

要将默认值从 ``2`` 改为每 ``60`` 秒最多检查一次磁盘上的更改，请使用以下设置：

```
opcache.revalidate_freq = 60
```



要完全禁用重新验证，请使用以下设置：

```
opcache.validate_timestamps = 0
```



任何服务器或应用程序的升级或对 ``config.php`` 的更改都可能需要重启 PHP（或以其他方式手动清除缓存或无效化该特定脚本）。

警告

为了避免误报，如果您环境未使用 PHP 的默认重新验证值，请在重启 mod_php/fpm（以确认它们不是由本地重新验证配置引起的）后再升级 Nextcloud 或 Nextcloud 应用程序后，不要报告 bug 或异常行为。

### 容量规划 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#sizing)

如果任何缓存大小限制超过90%，管理面板将显示相关警告并建议更改。

要获取更多详细信息，请参阅[官方 PHP 文档 ](https://php.net/manual/en/opcache.configuration.php)。要监控 OPcache 使用情况，清除个别或所有缓存条目时，可以使用 [opcache-gui](https://github.com/amnuts/opcache-gui)。

### 评论 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#comments)

Nextcloud 要求代码注释必须保留在 opcode 中，这是默认设置。但如果系统中的 PHP 设置被更改，你可能需要设置以下选项：

```
opcache.save_comments = 1
```



### JIT[](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#jit)

PHP 8.0 及以上版本自带 JIT 编译器，可以在 x86 平台上启用，以优化任何 CPU 密集型应用。要启用带有所有优化的跟踪 JIT，请使用以下设置：

```
opcache.jit = 1255
opcache.jit_buffer_size = 8M
```



注意

单个 Nextcloud 实例使用的 JIT 缓冲区大小不到 2MiB，因此 8MiB 已经绰绰有余。然而，整体 OPcache 使用量会显著增加，因此在某些情况下可能需要提高 `opcache.memory_consumption` 的值。Nextcloud 管理面板会显示相关警告。JIT 缓冲区使用量也可以通过进行监控。

## 预览 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#previews)

可以使用外部微服务来加快预览生成速度：[Imaginary](https://github.com/h2non/imaginary)。

警告

Imaginary 目前与服务器端加密不兼容。详见 [[https://github.com/nextcloud/server/issues/34262](https://github.com/nextcloud/server/issues/34262)](https://github.com/nextcloud/server/issues/34262)

我们强烈建议运行我们的自定义 Docker 镜像，该镜像比官方镜像更新。您可以在 [https://ghcr.io/nextcloud-releases/aio-imaginary](https://ghcr.io/nextcloud-releases/aio-imaginary) 找到该镜像。运行时，需要通过在 docker run 命令中添加 -p :9000 映射端口，例如 `docker run -d -p 9000:9000 --name nextcloud_imaginary --restart always ghcr.io/nextcloud-releases/aio-imaginary:latest` 。

要这样做，您需要部署该服务并确保其无法从服务器外部访问。然后，您可以编辑 `config.php` 配置 Nextcloud 使用 Imaginary：

```
'enabledPreviewProviders' => [
    'OC\Preview\MP3',
    'OC\Preview\TXT',
    'OC\Preview\MarkDown',
    'OC\Preview\OpenDocument',
    'OC\Preview\Krita',
    'OC\Preview\Imaginary',
],
'preview_imaginary_url' => 'http://<url of imaginary>:<port>',
```



警告

确保使用 `-return-size` 命令行参数启动 Imaginary。否则，将会有一些轻微的性能影响。该标志需要使用较新的 Imaginary 版本（新于 v1.2.4），并且默认会添加到 `aio-imaginary` 容器中。同时，请确保通过 `--cap-add=sys_nice` 或 `cap_add: - SYS_NICE` 添加 `SYS_NICE` 能力，因为 Imaginary 生成 HEIC 预览时需要该能力。

注意

对于大型实例，您应该遵循 Imaginary 的可扩展性建议 <https://github.com/h2non/imaginary#scalability>。

### 设置 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#settings)

如果您想设置 Imaginary 的预览格式，可以更改 jpeg 和 webp 之间的选项，默认为 jpeg：

```
'preview_format' => 'webp',
```



如果您想为 Imaginary 设置 API 密钥：

```
'preview_imaginary_key' => 'secret',
```



预览图片的默认 WebP 质量设置为“80”。使用以下命令进行更改：

```
occ config:app:set preview webp_quality --value="30"
```





# Example 安装（Ubuntu 22.04 LTS）

你可以使用 .deb 包来安装典型 Nextcloud 安装所需的模块，包括使用 Apache 和 MariaDB，只需在终端中输入以下命令：

```
sudo apt update && sudo apt upgrade
sudo apt install apache2 mariadb-server libapache2-mod-php php-gd php-mysql \
php-curl php-mbstring php-intl php-gmp php-xml php-imagick php-zip
```



- 这将安装 Nextcloud 核心系统的包。如果你计划运行额外的应用程序，请注意它们可能需要额外的包。详情请参见 [手动安装的先决条件 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#prerequisites-for-manual-installation)。 %%

现在你需要通过 MySQL 命令行界面创建一个数据库用户和数据库本身。当你首次登录时，Nextcloud 会创建数据库表。

要启动 MySQL 命令行模式，请使用以下命令：

```
sudo mysql
```



然后会出现一个 **MariaDB [root]>** 提示符。现在输入以下内容，将 `username` 和 `password` 替换为适当的值，并用 Enter 键确认：

```
CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';
CREATE DATABASE IF NOT EXISTS nextcloud CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;
GRANT ALL PRIVILEGES ON nextcloud.* TO 'username'@'localhost';
FLUSH PRIVILEGES;
```



你可以通过输入以下内容退出提示符：

```
quit;
```



现在下载最新版本的 Nextcloud 压缩包：

- 前往 [Nextcloud 安装页面 ](https://nextcloud.com/install)。

- 前往 **下载服务器 > 社区项目** ，下载 tar.bz2 或 .zip 压缩包。

- 这将下载一个名为 nextcloud-x.y.z.tar.bz2 或 nextcloud-x.y.z.zip 的文件（其中 x.y.z 是版本号）。

- 下载对应的校验和文件，例如 nextcloud-x.y.z.tar.bz2.md5 或 nextcloud-x.y.z.tar.bz2.sha256。

- 验证 MD5 或 SHA256 校验和：

  ```
  md5sum -c nextcloud-x.y.z.tar.bz2.md5 < nextcloud-x.y.z.tar.bz2
  sha256sum -c nextcloud-x.y.z.tar.bz2.sha256 < nextcloud-x.y.z.tar.bz2
  md5sum  -c nextcloud-x.y.z.zip.md5 < nextcloud-x.y.z.zip
  sha256sum  -c nextcloud-x.y.z.zip.sha256 < nextcloud-x.y.z.zip
  ```

  

- 你也可以验证 PGP 签名：

  ```
  wget https://download.nextcloud.com/server/releases/nextcloud-x.y.z.tar.bz2.asc
  wget https://nextcloud.com/nextcloud.asc
  gpg --import nextcloud.asc
  gpg --verify nextcloud-x.y.z.tar.bz2.asc nextcloud-x.y.z.tar.bz2
  ```

  

- 现在你可以提取归档文件内容。运行适合你归档类型的解压命令：

  ```
  tar -xjvf nextcloud-x.y.z.tar.bz2
  unzip nextcloud-x.y.z.zip
  ```

  

- 这会解压到一个单独的 `nextcloud` 目录。将 Nextcloud 目录复制到其最终位置。如果你正在运行 Apache HTTP 服务器，可以安全地将 Nextcloud 安装在 Apache 文档根目录中：

  ```
  sudo cp -r nextcloud /var/www
  ```

  

- 最后，将你的 Nextcloud 目录的所有权更改为 HTTP 用户：

  ```
  sudo chown -R www-data:www-data /var/www/nextcloud
  ```

  

对于其他 HTTP 服务器，建议将 Nextcloud 安装在文档根目录之外。

## 下一步 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_ubuntu.html#next-steps)

安装完先决条件并提取 nextcloud 目录后，您 应遵循 Apache 配置的说明 [Apache Web 服务器配置 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#apache-configuration-label)。安装完 Apache 后，您可以选择按照 [Linux 安装指南](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html)中的 [Pretty URLs 部分进行配置，直到 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#pretty-urls-label)[其他 Web 服务器](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#other-http-servers-label)







# 在 CentOS 8 上的示例安装 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_centos.html#example-installation-on-centos-8)

在本安装教程中，我们将部署 CentOS 8、PHP 7.4、MariaDB、Redis 作为内存缓存以及运行在 Apache 上的 Nextcloud。

首先安装一个最小化安装的 CentOS 8。这将提供一个足够强大的平台来运行成功的 Nextcloud 实例。

首先安装一些在安装过程中需要的依赖项，这些依赖项在日常使用中也非常有用：

```
dnf install -y epel-release yum-utils unzip curl wget \
bash-completion policycoreutils-python-utils mlocate bzip2
```



现在确保您的系统已更新：

```
dnf update -y
```



## Apache[](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_centos.html#apache)

```
dnf install -y httpd
```



创建一个虚拟主机，并将其内容添加如下：

```
<VirtualHost *:80>
  DocumentRoot /var/www/html/nextcloud/
  ServerName  your.server.com

  <Directory /var/www/html/nextcloud/>
    Require all granted
    AllowOverride All
    Options FollowSymLinks MultiViews

    <IfModule mod_dav.c>
      Dav off
    </IfModule>

  </Directory>
</VirtualHost>
```



请参阅 [Apache Web 服务器配置 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#apache-configuration-label)以获取更多详细信息。

确保已启用并启动了 Apache 网站服务：

```
systemctl enable httpd.service
systemctl start httpd.service
```



## PHP[](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_centos.html#php)

注意

CentOS 8 不包含 redis 和 imagick PHP 扩展的软件包。这些扩展可以使用 pecl 安装。除了官方的 PHP 软件包外，还可以在 `https://rpms.remirepo.net` 获取第三方仓库。使用 remirepo，还可以安装最新版本的 PHP 而不是默认版本。

### 设置 remirepo 以安装 PHP 8.2[](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_centos.html#setting-up-remirepo-with-php-8-2)

更多详细信息请参阅 `https://blog.remirepo.net/pages/Config-en`

安装 Remi 仓库配置包的命令：

```
dnf install https://rpms.remirepo.net/enterprise/remi-release-8.rpm
```



安装 yum-utils 包的命令（用于 yum-config-manager 命令）：

```
dnf install yum-utils
```



您希望使用单一版本，这意味着替换发行版的基本包。这些包的名称与基本仓库中的相同，即 php-*。一些常见的依赖项可以在默认启用的 remi-safe 仓库中找到。

您需要启用 8.2 的模块流：

```
dnf module reset php
dnf module install php:remi-8.2
dnf update
```



### 安装 PHP 及所需模块 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_centos.html#installing-php-and-the-required-modules)

接下来，安装此安装所需的 PHP 模块。请注意，因为这是一个有限的基本安装，我们只安装必要的模块，而不是全部模块。如果你要进行更完整的安装，请参阅源安装文档中的 PHP 模块列表，[Linux 安装 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html)。

```
dnf install -y php php-cli php-gd php-mbstring php-intl php-pecl-apcu\
     php-mysqlnd php-opcache php-json php-zip
```



### 安装可选模块 redis/imagick[](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_centos.html#installing-optional-modules-redis-imagick)

```
dnf install -y php-redis php-imagick
```



## 数据库 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_centos.html#database)

如前所述，我们将使用 MySQL/MariaDB 作为数据库：

```
dnf install -y mariadb mariadb-server
```



请确保数据库服务在启动时启用。:

```
systemctl enable mariadb.service
systemctl start mariadb.service
```



提高 MariaDB 安全性：

```
mysql_secure_installation
```



完成这些操作后，请确保创建一个数据库，并设置用户名和密码，以便 Nextcloud 可以访问该数据库。有关数据库设置和配置的详细信息，请参阅 [数据库配置 ](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/linux_database_configuration.html)文档。

## Redis[](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_centos.html#redis)

```
dnf install -y redis
systemctl enable redis.service
systemctl start redis.service
```



**安装 Nextcloud**

快到了，所以继续努力，你做得很好！

现在下载最新版本的 Nextcloud 压缩包：

- 前往 [Nextcloud 下载页面 ](https://nextcloud.com/install)。

- 访问 **下载 Nextcloud 服务器 > 下载 > 服务器所有者的存档文件** 并下载 tar.bz2 或 .zip 存档文件。

- 这会下载一个名为 nextcloud-x.y.z.tar.bz2 或 nextcloud-x.y.z.zip 的文件（其中 x.y.z 是版本号）。

- 下载对应的校验和文件，例如 nextcloud-x.y.z.tar.bz2.md5 或 nextcloud-x.y.z.tar.bz2.sha256。

- 验证 MD5 或 SHA256 校验和：

  ```
  md5sum -c nextcloud-x.y.z.tar.bz2.md5 < nextcloud-x.y.z.tar.bz2
  sha256sum -c nextcloud-x.y.z.tar.bz2.sha256 < nextcloud-x.y.z.tar.bz2
  md5sum  -c nextcloud-x.y.z.zip.md5 < nextcloud-x.y.z.zip
  sha256sum  -c nextcloud-x.y.z.zip.sha256 < nextcloud-x.y.z.zip
  ```

  

- 您也可以验证 PGP 签名：

  ```
  wget https://download.nextcloud.com/server/releases/nextcloud-x.y.z.tar.bz2.asc
  wget https://nextcloud.com/nextcloud.asc
  gpg --import nextcloud.asc
  gpg --verify nextcloud-x.y.z.tar.bz2.asc nextcloud-x.y.z.tar.bz2
  ```

  

为了演示，我们下载了最新版本的 Nextcloud，形式为 zip 文件，并使用上述命令确认了下载。现在我们将解压它：

```
unzip nextcloud-*.zip
```



将内容复制到 Web 服务器的根目录中。在我们的情况下，使用的是 Apache，因此路径为 /var/www/html/：

```
cp -R nextcloud/ /var/www/html/
```



在安装过程中不会创建数据文件夹，因此我们需要手动创建一个以帮助安装向导：

```
mkdir /var/www/html/nextcloud/data
```



确保 Apache 对整个 Nextcloud 文件夹具有读写权限：

```
chown -R apache:apache /var/www/html/nextcloud
```



重启 apache：

```
systemctl restart httpd.service
```



创建防火墙规则以访问 apache：

```
firewall-cmd --zone=public --add-service=http --permanent
firewall-cmd --reload
```



**SELinux**

同样，有关 SELinux 的详细配置说明可以在[SELinux 配置](#0)中找到，因此如果你使用的是 SELinux 强制模式，请运行该页面上建议的命令。以下命令仅适用于本教程：

```
semanage fcontext -a -t httpd_sys_rw_content_t '/var/www/html/nextcloud/data(/.*)?'
semanage fcontext -a -t httpd_sys_rw_content_t '/var/www/html/nextcloud/config(/.*)?'
semanage fcontext -a -t httpd_sys_rw_content_t '/var/www/html/nextcloud/apps(/.*)?'
semanage fcontext -a -t httpd_sys_rw_content_t '/var/www/html/nextcloud/.htaccess'
semanage fcontext -a -t httpd_sys_rw_content_t '/var/www/html/nextcloud/.user.ini'
semanage fcontext -a -t httpd_sys_rw_content_t '/var/www/html/nextcloud/3rdparty/aws/aws-sdk-php/src/data/logs(/.*)?'

restorecon -R '/var/www/html/nextcloud/'

setsebool -P httpd_can_network_connect on
```



如果你需要更多的 SELinux 配置，请参阅上述 URL，然后返回本教程。

完成 SELinux 配置后，请前往 `http://your.server.com/nextcloud` 并按照 [安装向导 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/installation_wizard.html)中的步骤操作，它会详细解释如何通过你的 Web 浏览器以管理员身份完成安装的最后一步。

注意

如果你使用本教程，并在安装后在 Web 浏览器中看到关于 `OPcache` 未启用或配置不正确的警告，你需要在 `/etc/opt/rh/rh-php74/php.d/10-opcache.ini` 中进行建议的更改，以使错误消失。这些警告将在管理员页面的基本设置部分显示。

因为我们使用 `Redis` 作为内存缓存，所以在 `/var/www/html/nextcloud/config/config.php` 中需要一个类似于以下示例的配置，该配置是在之前提到的在线安装向导运行时自动生成的。

示例配置：

```
'memcache.distributed' => '\OC\Memcache\Redis',
'memcache.locking' => '\OC\Memcache\Redis',
'memcache.local' => '\OC\Memcache\APCu',
'redis' => array(
  'host' => 'localhost',
  'port' => 6379,
),
```



请注意，本教程仅适用于在 CentOS 8 上安装 Nextcloud 的基本设置，使用的是 PHP 7.4。如果您打算使用更多功能，如 LDAP 或单点登录，您还需要额外的 PHP 模块以及额外的配置。因此，请参阅管理员手册的其余部分，[ 简介 ](https://docs.nextcloud.com/server/latest/admin_manual/index.html)，以获取详细说明。





# OpenBSD 上的示例安装 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_openbsd.html#example-installation-on-openbsd)

警告

Nextcloud 没有官方的 OpenBSD 或其他 BSD 的支持

在本安装教程中，我们将在一个最小化的 OpenBSD 系统上部署 Nextcloud，并使用我们自己的 httpd(8)、PHP、PostgreSQL 和 redis（对于 -stable 或 -current，步骤相同）。

从一个已安装的基本 OpenBSD 系统，你可以直接执行：

```
# pkg_add nextcloud
```



额外的软件包：

```
# pkg_add postgresql-server redis pecl82-redis php-pdo_pgsql
```



这将处理你的依赖关系，并允许你选择所需的 PHP 版本。

## HTTPD(8)[](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_openbsd.html#httpd-8)

在 ``/etc/httpd.conf`` 中创建一个虚拟主机，并添加以下内容：

```
  server "domain.tld" {
      listen on egress tls port 443
      hsts {
        max-age 15768000
        preload
        subdomains
      }

        tls {
                  certificate "/etc/ssl/domain.tld_fullchain.pem"
                  key "/etc/ssl/private/domain.tld_private.pem"
        }

        # Set max upload size to 513M (in bytes)
        connection max request body 537919488
        connection max requests 1000
        connection request timeout 3600
        connection timeout 3600

        root "/nextcloud"
        directory index "index.php"

        # Ensure that no '*.php*' files can be fetched from these directories
        location "/config/*" {
                block drop
        }

        location "/data/*" {
                block drop
        }

        # Note that this matches "*.php*" anywhere in the request path.
        location "/nextcloud/*.php*" {
                fastcgi socket "/run/php-fpm.sock"
        }

        location "/apps/*" {
                pass
        }

        location "/core/*" {
                pass
        }

        location "/.well-known/carddav" {
                block return 301 "https://$SERVER_NAME/remote.php/dav"
        }

        location "/.well-known/caldav" {
                block return 301 "https://$SERVER_NAME/remote.php/dav"
        }

        location "/.well-known/webfinger" {
                block return 301 "https://$SERVER_NAME/public.php?service=webfinger"
        }

        location match "/ocs-provider/*" {
                pass
        }
}
```



确保启用了并启动了 httpd(8)：

```
# rcctl enable httpd
# rcctl start httpd
```



## PHP[](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_openbsd.html#php)

假设你使用的是 OpenBSD -current（或 >= 6.8-stable），你可以使用 PHP 8.2，因此我将使用这个版本，但其他版本的概念是相同的。

由于你使用 pkg_add 安装了 Nextcloud，PHP 包已经可用，所以你只需要稍微调整一下 php.ini。

建议添加 opcache：

```
[opcache]
opcache.enable=1
opcache.memory_consumption=512
opcache.interned_strings_buffer=8
opcache.max_accelerated_files=10000
opcache.revalidate_freq=1
opcache.save_comments=1
```



并增加一些限制：

```
post_max_size = 513M
upload_max_filesize = 513M
```



我们可以使用以下命令启用 PHP 模块：

```
# cd /etc/php-8.2.sample
# for i in *; do ln -sf ../php-8.2.sample/$i ../php-8.2/; done
```



然后我们只需启用并启动 PHP：

```
# rcctl enable php82_fpm
# rcctl start php82_fpm
```



## 数据库 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_openbsd.html#database)

如前所述，我们将使用 PostgreSQL 作为数据库，并且已经安装了它，现在我们需要初始化：

```
$ su - _postgresql
$ mkdir /var/postgresql/data
$ initdb -D /var/postgresql/data -U postgres -A md5 -E UTF8 -W
...
Enter new superuser password: PASSWORD
Enter it again: PASSWORD
...
Success. You can now start the database server using:

pg_ctl -D /var/postgresql/data -l logfile start

$ pg_ctl -D /var/postgresql/data -l logfile start
server starting
$ exit
```



我们需要检查、启用并启动 postgres：

```
# rcctl check postgresql
# rcctl enable postgresql
# rcctl start postgresql
```



你可以按照 `/usr/local/share/doc/pkg-readmes/postgresql-server` 中的 README 创建用户和权限。

## Redis[](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_openbsd.html#redis)

我们之前安装了 redis，需要启用它并启动它，同时将其添加到 Nextcloud 配置中：

```
# rcctl enable redis
# rcctl start redis
# mg /var/www/nextcloud/config/config.php
...
  'memcache.local' => '\OC\Memcache\Redis',
  'redis' => array(
  'host' => 'localhost',
  'port' => 6379,
  'timeout' => 0.0,
),
...
```



## Cron 作业 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_openbsd.html#cron-job)

我们需要添加 Nextcloud 的定时任务，通过在 cron 作业中添加以下条目来完成一些任务：

```
*/5 * * * * /usr/bin/ftp -Vo - https://domain.tld/cron.php >/dev/null
```



## chroot

由于在 OpenBSD 中 httpd(8) 默认使用 chroot(8)，我们需要确保 /var/www 目录中有相关的文件：

```
# mkdir -p /var/www/etc/ssl
# install -m 444 -o root -g bin /etc/ssl/cert.pem /etc/ssl/openssl.cnf \
        /var/www/etc/ssl/
# cp /etc/resolv.conf /var/www/etc
```



## Nextcloud 最终步骤 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_openbsd.html#nextcloud-final-steps)

其余的安装步骤将在基于 Web 的安装向导中完成。

要激活此向导，请在安装目录的 config 文件夹中创建一个名为 CAN_INSTALL 的文件：

> \# touch /var/www/nextcloud/config/CAN_INSTALL

使用你的浏览器导航到安装的 URL：

> [https://domain.tld](https://domain.tld/)

现在你只需要按照步骤操作，并输入你的数据库名称、用户名和密码。

请记住，你可以通过运行 -current 来升级 Nextcloud：

```
# pkg_add -u -Dsnap
```



而通过 -stable 则是：

```
# pkg_add -u
```



然后你只需按照浏览器中的步骤操作。

## 注意 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_openbsd.html#note)

请始终阅读 OpenBSD 软件包中的所有 README 文件：

```
/usr/local/share/doc/pkg-readmes/
```



所有这些信息以及更多内容都可以在那里找到。





# 卸载 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/uninstallation.html#uninstallation)

应用程序存储在服务器目录中，并使用数据库来存储文件及其共享（EFSS 功能）的元数据。

没有通用的卸载指南，因为 Nextcloud 在运营模式或操作系统平台方面提供了高度的灵活性；例如，包括抽象容器、虚拟机或“裸机”，即直接安装在一台或多台服务器上。

因此，在卸载时需要了解 Nextcloud 应用安装在何处以及相应的数据存储在何处。

- 应用目录（安装前创建）
- 用户文件存储（在应用目录内配置或外部配置）
- 元数据存储在数据库中（使用 SQLite 时在应用目录内，或在相同服务器或另一服务器的外部）
- 通过 Redis 服务器或其他类似方式缓存（如果使用的话）

卸载时，需要决定是否备份文件存储，以及是否删除数据。此外，根据部署场景，需要完全解分配相应的服务器，或者删除应用目录、数据库模式和 Redis 条目。如果使用了专用容器或虚拟机，这些容器或虚拟机必须被解分配，同时 Nextcloud 应用也需要被解分配。

卸载时，可以从 `config` 目录中的配置中读取值。检查：

- 源代码（手动安装，通常在 `/var/www` 或 `/opt/nextcloud` 目录中）：在所有服务器上删除目录
- 数据库（相关配置键：`dbtype`, `dbhost`）：在所有数据库服务器上删除相应的数据库（您可能需要先进行备份）。
- 缓存（相关配置键：`memcache.*`）：如果缓存是持久化的，在所有缓存服务器上删除相应的数据库或键。
- 数据（相关配置键：`datadirectory`）：在所有服务器上删除相应的目录（您可能需要在此之前创建备份）。Nextcloud 可以将数据存储在不同的位置。请检查外部存储和对象存储。
- 日志（相关配置键：`logfile`, `logfile_audit`）：通常在数据目录中，但也可能在其他位置，例如 `/var/log/`。






# 管理页面中的警告 [](https://docs.nextcloud.com/server/latest/admin_manual/configuration_server/security_setup_warnings.html#warnings-on-admin-page "Link to this heading")

您的 Nextcloud 服务器内置了一个配置检查器，并会在管理页面顶部报告其发现的问题。以下是一些您可能会看到的警告以及相应的处理方法。

![../_images/security-setup-warning-1.png](https://docs.nextcloud.com/server/latest/admin_manual/_images/security-setup-warning-1.png)

您可以使用 [Nextcloud 安全扫描](https://scan.nextcloud.com/)  来检查您的系统是否是最新的并且安全。我们过去曾通过公共 IP 地址运行过这种扫描，以尝试联系那些 [极其过时的系统](https://nextcloud.com/blog/nextcloud-releases-security-scanner-to-help-protect-private-clouds/) ，未来可能会再次进行。请保护您的隐私并保持服务器的安全。 更新！没有安全措施，隐私就毫无意义。

## 缓存警告 [](https://docs.nextcloud.com/server/latest/admin_manual/configuration_server/security_setup_warnings.html#cache-warnings "Link to this heading")

“未配置内存缓存。为了提高性能，请配置一个 memcache（如果可用）。”Nextcloud 支持多种 PHP 缓存扩展：

- APCu（最小要求的 PHP 扩展版本 4.0.6）
    
- Memcached
    
- Redis（所需最小 PHP 扩展版本：2.2.6）
    

如果你没有安装并启用缓存，或者你的缓存没有安装所需的最小版本，将会看到此警告；较旧版本因性能问题已被禁用。

如果你看到“_{缓存}_ 版本低于 _{版本}_ 已安装。出于稳定性和性能考虑，我们建议更新到较新的 _{缓存}_ 版本”，则需要进行更新，或者如果你不使用它，则需要移除它。

您无需使用任何缓存，但缓存可以提高服务器性能。请参阅[内存缓存](https://docs.nextcloud.com/server/latest/admin_manual/configuration_server/caching_configuration.html) 。

## 事务文件锁定已禁用 [](https://docs.nextcloud.com/server/latest/admin_manual/configuration_server/security_setup_warnings.html#transactional-file-locking-is-disabled "Link to this heading")

“事务文件锁定已禁用，这可能会导致竞态条件问题。”

请参阅[事务文件锁定](https://docs.nextcloud.com/server/latest/admin_manual/configuration_files/files_locking_transactional.html)以了解如何正确配置事务文件锁定的环境。

## 您正在通过 HTTP 访问此站点 [](https://docs.nextcloud.com/server/latest/admin_manual/configuration_server/security_setup_warnings.html#you-are-accessing-this-site-via-http "Link to this heading")

“您正通过 HTTP 访问此站点。我们强烈建议您配置服务器以要求使用 HTTPS。请认真对待此警告；使用 HTTPS 是基本的安全措施。您必须配置 Web 服务器以支持它，然后在“ **安全** ”设置中进行一些配置。 请在 Nextcloud 管理页面的相关部分进行启用。以下页面 描述如何在 Apache 和 NginxWeb 服务器上启用 HTTPS。

[启用 SSL](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#enabling-ssl-label)（在 Apache 中）

[使用 HTTPS](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#use-https-label)

[NGINX 配置](https://docs.nextcloud.com/server/latest/admin_manual/installation/nginx.html)

## 使用 getenv("PATH")进行测试只会返回空响应 [](https://docs.nextcloud.com/server/latest/admin_manual/configuration_server/security_setup_warnings.html#the-test-with-getenv-path-only-returns-an-empty-response "Link to this heading")

某些环境没有向 Nextcloud 传递有效的 PATH 变量。 [PHP-FPM 配置](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#php-fpm-tips-label)提供了如何配置环境的信息。

## “Strict-Transport-Security” HTTP 头未配置 [](https://docs.nextcloud.com/server/latest/admin_manual/configuration_server/security_setup_warnings.html#the-strict-transport-security-http-header-is-not-configured "Link to this heading")

““Strict-Transport-Security” HTTP 头未配置为最少“15552000”秒。为了增强安全性，我们建议按照我们的安全提示中所述启用 HSTS。”

HSTS 头需要在你的 Web 服务器上进行配置，请参考 [启用 HTTP 严格传输安全](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#enable-hsts-label)文档

你可以通过浏览器开发者工具或使用 cURL 等工具查看该头是否出现在请求中： `curl --head https://cloud.domain.tld` 。

## /dev/urandom 对 PHP 是不可读的 [](https://docs.nextcloud.com/server/latest/admin_manual/configuration_server/security_setup_warnings.html#dev-urandom-is-not-readable-by-php "Link to this heading")

“/dev/urandom 无法被 PHP 读取，这从安全角度来说是严格禁止的。更多详细信息请参阅我们的文档。”

此消息需要认真对待，请参阅 [给 PHP 授予读取 /dev/urandom 的权限](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#dev-urandom-label) 文档。

## 您的 Web 服务器尚未正确设置以允许文件同步 [](https://docs.nextcloud.com/server/latest/admin_manual/configuration_server/security_setup_warnings.html#your-web-server-is-not-yet-set-up-properly-to-allow-file-synchronization "Link to this heading")

“由于 WebDAV 接口似乎存在问题，您的 Web 服务器尚未正确设置以允许文件同步。”

ownCloud 社区论坛上维护了一个较大的常见问题解答（FAQ） [，包含各种信息和调试提示。](https://forum.owncloud.org/viewtopic.php?f=17&t=7536)

## 过时的 NSS / OpenSSL 版本 [](https://docs.nextcloud.com/server/latest/admin_manual/configuration_server/security_setup_warnings.html#outdated-nss-openssl-version "Link to this heading")

“cURL 使用的是过时的 OpenSSL 版本（OpenSSL/$version）。请更新您的操作系统，否则通过应用商店安装和更新应用或进行去中心化云共享等功能将无法可靠地工作。”

cURL 使用的是过时的 NSS 版本（NSS/$version）。请更新您的操作系统，否则通过应用商店安装和更新应用或使用联邦云共享等功能将无法可靠地工作。

在较旧的 OpenSSL 和 NSS 版本中已知存在 bug，这会导致与使用 SNI 的远程主机结合使用时出现错误行为。SNI 是大多数 HTTPS 网站使用的技术。为了确保 Nextcloud 能正常工作，您需要将 OpenSSL 更新到至少 1.0.2b 或 1.0.1d。对于 NSS，补丁版本取决于您的发行版，并且正在运行一个测试，该测试实际上会重现该 bug。

## 您的 Web 服务器未正确设置以解析 /.well-known/caldav/ 或 /.well-known/carddav/

这两个 URL 都需要正确重定向到 Nextcloud 的 DAV 端点。请参阅 Service discovery 以获取更多信息。

## 一些文件未通过完整性检查 [](https://docs.nextcloud.com/server/latest/admin_manual/configuration_server/security_setup_warnings.html#some-files-have-not-passed-the-integrity-check "Link to this heading")

请参阅《 [修复无效代码完整性消息](https://docs.nextcloud.com/server/latest/admin_manual/issues/code_signing.html#code-signing-fix-warning-label) 》文档以调试此问题。

## 您的数据库未使用“READ COMMITTED”事务隔离级别 [](https://docs.nextcloud.com/server/latest/admin_manual/configuration_server/security_setup_warnings.html#your-database-does-not-run-with-read-committed-transaction-isolation-level "Link to this heading")

“您的数据库未使用“READ COMMITTED”事务隔离级别。当多个操作并行执行时，这可能会导致问题。”

请参阅[数据库“READ COMMITTED”事务隔离级别](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/linux_database_configuration.html#db-transaction-label)如何配置您的数据库以满足此要求。






