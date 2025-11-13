

# 简介 [](https://docs.nextcloud.com/server/latest/admin_manual/index.html#introduction)

**欢迎来到 Nextcloud 服务器管理指南。**

本指南介绍了如何在 Nextcloud 中执行管理任务，Nextcloud 是一个功能强大且可扩展的开源平台，用于文件同步和内容协作。

Nextcloud 已超过 40 万次部署，可以在简单的双用户树莓派上运行，或扩展以支持全球分布式安装，服务于数千万用户。它可以在本地、私有云或混合环境中部署。在庞大且不断增长的社区支持下，Nextcloud 提供超过 60 种语言版本。

Nextcloud 最新版手册始终可在以下网址在线获取 [docs.nextcloud.com](https://docs.nextcloud.com/)。

## 目标受众 [](https://docs.nextcloud.com/server/latest/admin_manual/index.html#target-audience)

本指南适用于希望：

- 安装 Nextcloud 服务器
- 管理和维护其实例的用户
- 优化服务器性能

有关 Nextcloud 网页、桌面或移动客户端的文档，请参阅：

- [Nextcloud 用户手册](https://docs.nextcloud.com/server/latest/user_manual/en/)
- [Nextcloud 桌面客户端](https://docs.nextcloud.com/desktop/latest/)

有关开发主题的文档，请参阅：

- GitHub 中 [@nextcloud 组织](https://github.com/nextcloud/)内的各个存储库
- [Nextcloud 开发手册](https://docs.nextcloud.com/server/latest/developer_manual/)

## 核心组件 [](https://docs.nextcloud.com/server/latest/admin_manual/index.html#core-components)

Nextcloud 包括：

- Nextcloud 服务器（在 Linux 上运行的后端）
- 响应式、集成的网页客户端
- 跨平台桌面客户端（Windows、macOS 和 Linux），用于文件同步和本地访问
- 专用移动客户端（Android 和 iOS）
- 丰富的应用生态系统，扩展功能

## 版本 [](https://docs.nextcloud.com/server/latest/admin_manual/index.html#editions)

Nextcloud 服务器提供两种版本：

- **社区版：** 社区支持（点对点帮助），100%免费。
- **企业版：** 由核心开发者或授权合作伙伴支持，提供官方打包，包含广泛的企业特定文档和支持选项。

*两个版本都包含所有功能及源代码。*

企业版还可以包括部署指南、电话和电子邮件访问 Nextcloud 开发者、官方集成和插件支持、定制品牌以及扩展支持周期等额外优势。

本指南主要关注社区版，但信息同样适用于两个版本。

## 更多资源 [](https://docs.nextcloud.com/server/latest/admin_manual/index.html#further-resources)

- 视频教程、概览和会议演讲：[Nextcloud YouTube 频道 ](https://www.youtube.com/c/Nextcloud)。
- 最新新闻和更新： [Nextcloud 博客 ](https://nextcloud.com/news/)。
- 社区支持：[Nextcloud 帮助论坛 ](https://help.nextcloud.com/)。
- 商业支持：[Nextcloud GmbH](https://nextcloud.com/)。
- 文档：[Nextcloud 文档 ](https://docs.nextcloud.com/)。

## 入门 [](https://docs.nextcloud.com/server/latest/admin_manual/index.html#getting-started)

要开始使用，请参阅安装部分。

谁在开发 Nextcloud？

Nextcloud 平台的开发是一项合作努力，由核心维护者监督——他们主要受雇于 Nextcloud GmbH——以及成千上万的合作伙伴、供应商、协作者、项目成员和社区参与者。

Nextcloud 社区包括所有人——从个人用户和独立开发者到大型组织。

社区成员每天都在分享和讨论他们在平台上的经验。他们提出改进建议，合作进行设计，编写代码，创建文档，测试错误，处理错误报告和改进建议，支持他人，改进翻译，并帮助资助和组织这样一个规模的项目。最重要的是，他们每天都在日常生活中使用 Nextcloud。



# 维护和发布计划 [](https://docs.nextcloud.com/server/latest/admin_manual/release_schedule.html#maintenance-and-release-schedule)

## 概述 [](https://docs.nextcloud.com/server/latest/admin_manual/release_schedule.html#overview)

Nextcloud 每年发布多个主要版本，但通过“较轻”的维护更新，为每个主要版本提供一年的支持（并定期[回滚](https://en.wikipedia.org/wiki/Backporting)适用的安全漏洞和错误修复）。这允许高速的开发节奏，同时仍然为管理员在规划部署、升级和维护活动时提供灵活性。

详细的[即将到来的主要和维护发布计划 ](https://github.com/nextcloud/server/wiki/Maintenance-and-Release-Schedule)（以及生命周期结束的预测）会定期更新，以方便规划部署、测试和升级计划。

您是否想要最新的功能和优化，想要参与测试，或者只是想等到一切准备就绪，您都有选择，可以选择最初部署的 Nextcloud Server 版本以及进行主要升级的频率。

危险

我们始终建议尽快安装最新的 **维护** 版本，无论您使用的是哪个主要版本的 Nextcloud Server。我们还始终强烈建议尽快从 **生命周期结束** 版本升级。

提示

通过 Nextcloud 开发者通过 Nextcloud GmbH 提供的[企业支持订阅选项 ](https://nextcloud.com/enterprise/)，可获取扩展维护和额外支持。

## 发布类型 [](https://docs.nextcloud.com/server/latest/admin_manual/release_schedule.html#release-types)

Nextcloud 在默认发布渠道中有两种类型的发布：

1. 主要发布
2. 维护版本

**主要**版本的 Nextcloud Server（例如 `28.X.X`）引入了新功能和功能。

每个主要版本都通过定期的**维护**版本（例如 `X.X.4`）获得**一年**的支持，这些维护版本会修复关键错误和安全漏洞。

### 主要版本 [](https://docs.nextcloud.com/server/latest/admin_manual/release_schedule.html#major-releases)

主要版本通常引入新功能，并且经常也包含“底层”的变更。这些变更可能非常广泛。

一个特定的主要版本由版本字符串的第一部分表示。例如，Nextcloud Server `28.0.4` 是主要版本 `28`。而 `27.1.7` 是主要版本 `27`。

提示

最高编号的主版本提供了最新功能。而最低编号的主版本则提供了最长时间的市场应用。

注意

在更新器提供新主版本之前，您可能需要满足新的系统要求。即使提供了新版本，也可能需要其他更改，而更新器无法完全检查。我们尝试在每个新版的《管理员手册》中，在《发布说明》章节的“重大变更”部分中突出显示这些内容。

警告

应用程序通常根据它们所支持的 Nextcloud 服务器的主要版本来定义其兼容性。在选择要部署哪个主要版本或决定何时升级到新发布的主要版本之前，请考虑您最喜欢的关键应用程序与 Nextcloud 服务器未来主要版本的兼容性。此外，由于许多应用程序是由社区提供并由志愿者维护的，您可能希望主动测试该应用程序以针对 Nextcloud 的新主要版本（或者如果您有能力，则对其进行适配），以鼓励更快（或更高质量）的发布。

### 维护版本 [](https://docs.nextcloud.com/server/latest/admin_manual/release_schedule.html#maintenance-releases)

维护版本故意**不**引入新功能或破坏性变更。这是为了降低部署更新的风险和影响，以便能够快速且常规地解决关键错误或安全漏洞。

维护版本会发布（通常同时发布）所有尚未达到生命终结状态的稳定主要版本。

这些发布不应存在应用兼容性问题，也不应引入需要重新培训最终用户的变化。

特定维护版本由版本号的最后一部分标识。例如，`28.0.4` 是 Nextcloud Server 主版本 `28` 的第四次维护版本。它提供了自上次维护版本（在本例中为 `28.0.3`）以来解决的任何关键错误和安全漏洞的修复。

注意

所有关键错误修复，包括与安全相关的修复，都会[回滚](https://en.wikipedia.org/wiki/Backporting)到**所有**维护中的主要版本。

## 发布计划 [](https://docs.nextcloud.com/server/latest/admin_manual/release_schedule.html#release-schedule)

Nextcloud 服务器的全新 **主要** 版本大约每十六周发布一次。

全新 **维护** 版本大约每四周发布一次。

### 支持时长（“维护”)[](https://docs.nextcloud.com/server/latest/admin_manual/release_schedule.html#length-of-support-maintenance)

我们的发布计划意味着多个主要版本（例如 26.X.X、27.X.X、28.X.X）将同时获得支持。每当解决一个关键错误或漏洞时，如果它影响超过一个主要版本，它将被 **回退** 到所有适用的主要版本，并在下一个维护版本中发布（例如 `28.0.3` -> `28.0.4`）。任何尚未达到生命周期结束状态的主要版本都将接收这些维护更新。

这种重叠的日程和可预测的节奏允许快速开发，同时为管理员提供可见性、获取关键错误修复的途径，以及在如何积极升级到新主版本方面提供灵活性。

注意

由于每个主版本从发布之日起支持一年，为了保持更新，你至少需要做的是安装发布时发布的维护版本，并在你当前使用的版本达到生命周期结束状态时升级到下一个更高的主版本。由于维护版本仅通过最新错误和安全漏洞修复来修补服务器——并且**不**引入其他重大变化——升级到新的维护版本的风险远小于升级到新的主版本。

### 生命周期结束 [](https://docs.nextcloud.com/server/latest/admin_manual/release_schedule.html#end-of-life)

生命周期结束状态意味着支持/维护结束。在初始发布一周年纪念日，主版本不再发布维护版本。该主版本随后进入生命周期结束状态，将不再接收任何错误修复或安全漏洞修正。

注意

通过 Nextcloud 开发者通过 Nextcloud GmbH 提供的[企业订阅服务 ](https://nextcloud.com/enterprise/)，可以对主要版本提供支持。

所有主要版本的生命周期结束日期都会提前[公布 ](https://github.com/nextcloud/server/wiki/Maintenance-and-Release-Schedule)，以方便规划。

注意

只要一个主要版本仍然在[维护计划](https://github.com/nextcloud/server/wiki/Maintenance-and-Release-Schedule)中列为*当前维护* ，你就可以预期会收到所有相关的关键错误或安全漏洞修复（即使它们是为更新的主要版本提供的，如果它们与仍然受支持较早的主要版本相关）。

## 安装版本 [](https://docs.nextcloud.com/server/latest/admin_manual/release_schedule.html#installation-version)

由于每年都会发布多个主要版本，并且每个版本都会得到一年的支持，包括任何相关的错误和安全修复，因此您可以根据自己的判断选择最初部署哪个主要版本，以及何时升级到新的主要版本。

注意

如果您计划在企业环境中部署 Nextcloud，并且您的使用是关键任务，开发人员可以通过“[ 企业服务安排 ](https://nextcloud.com/enterprise/)”帮助您选择最适合您特定用例的主要版本，并帮助确保其得到最佳部署，同时解决您可能遇到的任何关键问题。

## 发布渠道 [](https://docs.nextcloud.com/server/latest/admin_manual/release_schedule.html#release-channels)

默认情况下，所有 Nextcloud 安装都使用`稳定`发布渠道。该渠道以最低风险为大多数用户提供最新的功能。

注意

Nextcloud 对新版本进行分阶段发布，以进一步降低大规模更新的风险。新版本，尤其是主要版本，通常最初只提供给一小部分系统。在一周（或更长时间）内没有报告大规模严重错误后，将向更多系统提供更新。有时主要版本会限制在<100%的系统上，直到第一个维护（错误修复）版本发布后才会全面开放。

警告

当使用 `稳定 `渠道时，你可能会被 *提供* 更新版本以升级，即使你现有的主版本尚未达到生命周期结束。是否升级取决于你选择何时进行，或者等待更好的时机部署新的主版本。另一方面，新的 **维护** 版本（在你当前运行的主版本内）应尽快部署，以保持与安全更新和其他关键错误修复同步。

危险

确保你运行的是活跃维护的 **主** 版本是至关重要的。一旦主版本达到生命周期结束状态，它将不再接收任何进一步维护版本来修正关键错误或漏洞。

你可以在我们定期更新的 [维护和发布计划 ](https://github.com/nextcloud/server/wiki/Maintenance-and-Release-Schedule) 中找到所有稳定渠道主版本和维护版本的详细计划，包括生命周期结束日期。

## 主要版本升级 [](https://docs.nextcloud.com/server/latest/admin_manual/release_schedule.html#major-version-upgrades)

在进行从一个主要版本升级到另一个主要版本之前，我们强烈建议您查看**发布说明**章节中的*重大变更*部分，以最大程度地减少在您的环境中引入意外破坏性变更的可能性。

警告

通常建议做好数据备份（并测试数据恢复方法！），但在执行更新（无论是主要版本还是仅维护版本）之前，这一点尤其重要。

## Beta 版本和候选版本 [](https://docs.nextcloud.com/server/latest/admin_manual/release_schedule.html#beta-releases-and-release-candidates)

在发布新的最终主要版本之前，通常至少会发布四个 Beta 版本，然后是两个候选版本，每个版本之间间隔一周。

在发布新的最终维护版本之前，大约会提前一周发布一个候选版本。

每个版本的预期发布日期可以在[详细日程](https://github.com/nextcloud/server/wiki/Maintenance-and-Release-Schedule)中找到。

提示

如果您希望更快地更新到新的大版本或测试版本，您可以根据自己的选择将实例调整为使用 `测试 `渠道。在大版本发布期间，无论 staging 参数如何，` 测试 `渠道也会更早地提供最新的大版本。

社区中的每个人都能从那些选择评估测试版本或候选版本的人的慷慨测试和反馈中获益良多，无论是在他们的测试环境中，还是对于大胆的人来说，在真实条件下。

如果您有机会评估预最终版本，开发者和整个社区都感谢您！

提示

我们建议将测试工作集中在验证您每天依赖的功能和特性（以确保它们按预期运行）。然后，如果您愿意，可以考虑评估任何引起您兴趣的新功能。请在[帮助论坛](https://help.nextcloud.com/)讨论出现的问题，并将疑似错误报告给 [GitHub 仓库 ](https://github.com/nextcloud/server/issues)。

## 降级 [](https://docs.nextcloud.com/server/latest/admin_manual/release_schedule.html#downgrading)

官方不支持在任意主要版本、维护版本或预发布版本之间进行降级。

## Bug 报告 [](https://docs.nextcloud.com/server/latest/admin_manual/release_schedule.html#bug-reporting)

在报告 bug 之前，请确保您正在运行一个仍然受支持的主要版本*并且*该版本的最新维护版本。

提示

Nextcloud GmbH（雇佣了众多核心开发者）提供 [Nextcloud 企业服务 ](https://nextcloud.com/enterprise/)，提供直接访问 Nextcloud 工程专家的服务，其中使用情况至关重要。除此之外，他们可以帮助您选择最适合您用例的主要版本（并确保其部署最优化）。







# Cookies[](https://docs.nextcloud.com/server/latest/admin_manual/gdpr/cookies.html#cookies)

Nextcloud 仅存储 Nextcloud 正常运行所需的 cookie。所有 cookie 都直接来自您的 Nextcloud 服务器，不会将任何第三方 cookie 发送到您的系统。关于 GDPR，[ 仅包含个人数据的数据才相关 ](https://gdpr-info.eu/recitals/no-26/)。

## Nextcloud 存储的 cookie[](https://docs.nextcloud.com/server/latest/admin_manual/gdpr/cookies.html#cookies-stored-by-nextcloud)

| Cookie        | 存储的数据                                                   | 有效期         |
| ------------- | ------------------------------------------------------------ | -------------- |
| 会话 cookie   | 会话 ID密钥令牌（用于在服务器上解密会话）                    | 24分钟         |
| 同站 Cookie   | 不存储与用户相关的数据，所有同站 Cookie 对所有 Nextcloud 实例中的所有用户都相同 | 永远           |
| 记住我 Cookie | 用户 ID原始会话 ID记住令牌                                   | 15天（可配置） |

同站 Cookie 用于确定请求如何到达 Nextcloud 服务器。我们使用它们来防止 CSRF 攻击。这些 Cookie 中不存储可识别的信息。其余的 Cookie 严格用于系统识别用户。







# 安装和服务器配置 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/index.html#installation-and-server-configuration)

- 系统要求
  - [服务器](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html#server)
  - [桌面客户端](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html#desktop-client)
  - [移动应用](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html#mobile-apps)
  - [网络浏览器](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html#web-browser)
- [部署建议](https://docs.nextcloud.com/server/latest/admin_manual/installation/deployment_recommendations.html)
- 准备 PHP
  - [PHP 安装](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#php-installation)
  - [必需的 PHP 模块](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#required-php-modules)
  - [必需的 PHP 数据库连接器](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#required-php-database-connectors)
  - [推荐的通用 PHP 模块](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#recommended-general-php-modules)
  - [推荐的 PHP 缓存模块](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#recommended-php-caching-modules)
  - [推荐的 PHP 命令行模块](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#recommended-php-cli-modules)
  - [用于媒体管理的 PHP 模块](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#php-modules-for-media-management)
  - [特定应用的 PHP 模块](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#php-modules-for-specific-applications)
  - [PHP ini 设置](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#php-ini-settings)
  - [关于 PHP ini 配置的说明](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#notes-on-php-ini-configuration)
  - [PHP 模块快速参考表](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#php-module-quick-reference-table)
  - [更多资源](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#further-resources)
- Linux 系统上的安装
  - [手动安装的先决条件](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#prerequisites-for-manual-installation)
  - [Apache Web 服务器配置](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#apache-web-server-configuration)
  - [美观的 URL](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#pretty-urls)
  - [启用 SSL](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#enabling-ssl)
  - [安装向导](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#installation-wizard)
  - [设置后台任务](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#setting-up-background-jobs)
  - [SELinux 配置技巧](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#selinux-configuration-tips)
  - [PHP-FPM 配置](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#php-fpm-configuration)
  - [其他 Web 服务器](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#other-web-servers)
  - [在 Windows（虚拟机）上安装](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#installing-on-windows-virtual-machine)
  - [通过 Snap 软件包安装](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#installing-via-snap-packages)
  - [在 VPS 或网络空间上通过 Web 安装程序安装](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#installation-via-web-installer-on-a-vps-or-web-space)
  - [在 TrueNAS 上安装](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#installation-on-truenas)
  - [通过安装脚本安装](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#installation-via-install-script)
- 安装向导
  - [快速入门](https://docs.nextcloud.com/server/latest/admin_manual/installation/installation_wizard.html#quick-start)
  - [数据目录位置](https://docs.nextcloud.com/server/latest/admin_manual/installation/installation_wizard.html#data-directory-location)
  - [数据库选择](https://docs.nextcloud.com/server/latest/admin_manual/installation/installation_wizard.html#database-choice)
  - [可信域名](https://docs.nextcloud.com/server/latest/admin_manual/installation/installation_wizard.html#trusted-domains)
- [命令行安装](https://docs.nextcloud.com/server/latest/admin_manual/installation/command_line_installation.html)
- SELinux 配置
  - [通过 Web 界面启用更新](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html#enable-updates-via-the-web-interface)
  - [禁止对整个 Web 目录的写访问](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html#disallow-write-access-to-the-whole-web-directory)
  - [允许访问远程数据库](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html#allow-access-to-a-remote-database)
  - [允许访问 LDAP 服务器](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html#allow-access-to-ldap-server)
  - [允许访问远程网络](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html#allow-access-to-remote-network)
  - [允许访问网络 memcache](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html#allow-access-to-network-memcache)
  - [允许访问 SMTP/sendmail](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html#allow-access-to-smtp-sendmail)
  - [允许访问 CIFS/SMB](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html#allow-access-to-cifs-smb)
  - [允许访问 FuseFS](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html#allow-access-to-fusefs)
  - [允许访问 Rainloop 的 GPG](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html#allow-access-to-gpg-for-rainloop)
  - [故障排除](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html#troubleshooting)
- NGINX 配置
  - [NGINX 的 Webroot 中的 Nextcloud](https://docs.nextcloud.com/server/latest/admin_manual/installation/nginx.html#nextcloud-in-the-webroot-of-nginx)
  - [NGINX Webroot 的子目录中的 Nextcloud](https://docs.nextcloud.com/server/latest/admin_manual/installation/nginx.html#nextcloud-in-a-subdir-of-the-nginx-webroot)
  - [小贴士和技巧](https://docs.nextcloud.com/server/latest/admin_manual/installation/nginx.html#tips-and-tricks)
- 加固和安全指南
  - [密码](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#passwords)
  - [操作系统](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#operating-system)
  - [部署](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#deployment)
  - [使用 HTTPS](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#use-https)
  - [将管理员操作限制在特定的 IP 地址范围内](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#restrict-admin-actions-to-a-specific-range-of-ip-addresses)
  - [为 Nextcloud 使用专用域名](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#use-a-dedicated-domain-for-nextcloud)
  - [确保你的 Nextcloud 实例安装在 DMZ 区域](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#ensure-that-your-nextcloud-instance-is-installed-in-a-dmz)
  - [通过 Web 服务器提供安全相关的头部信息](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#serve-security-related-headers-by-the-web-server)
  - [与远程服务器的连接](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#connections-to-remote-servers)
  - [设置 fail2ban](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#setup-fail2ban)
- 服务器调优
  - [使用 cron 执行后台任务](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#using-cron-to-perform-background-jobs)
  - [降低系统负载](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#reducing-system-load)
  - [日志级别](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#log-levels)
  - [调试模式](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#debug-mode)
  - [缓存](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#id1)
  - [压缩](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#compression)
  - [替换 SQLite](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#replacing-sqlite)
  - [调整你的数据库](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#tuning-your-database)
  - [使用基于 Redis 的交易文件锁定](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#using-redis-based-transactional-file-locking)
  - [TLS / 加密应用](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#tls-encryption-app)
  - [启用 HTTP/2 以实现更快的加载](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#enable-http-2-for-faster-loading)
  - [调整 PHP-FPM](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#tune-php-fpm)
  - [启用 PHP OPcache](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#enable-php-opcache)
  - [预览](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#previews)
- 在 Ubuntu 22.04 LTS 上的示例安装
  - [下一步](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_ubuntu.html#next-steps)
- 在 CentOS 8 上的示例安装
  - [Apache](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_centos.html#apache)
  - [PHP](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_centos.html#php)
  - [数据库](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_centos.html#database)
  - [Redis](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_centos.html#redis)
  - [安装 Nextcloud](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_centos.html#installing-nextcloud)
  - [SELinux](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_centos.html#selinux)
- 在 OpenBSD 上的示例安装
  - [HTTPD(8)](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_openbsd.html#httpd-8)
  - [PHP](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_openbsd.html#php)
  - [数据库](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_openbsd.html#database)
  - [Redis](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_openbsd.html#redis)
  - [定时任务](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_openbsd.html#cron-job)
  - [Chroot](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_openbsd.html#chroot)
  - [Nextcloud 最终步骤](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_openbsd.html#nextcloud-final-steps)
  - [注意](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_openbsd.html#note)
- [卸载](https://docs.nextcloud.com/server/latest/admin_manual/installation/uninstallation.html)





# 系统需求 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html#system-requirements)

## 服务器 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html#server)

为了获得最佳性能、稳定性和功能，我们已记录了一些运行 Nextcloud 服务器的建议。

注意

如果您计划为您的组织搭建系统，并且依赖专业的部署咨询（例如高效可靠的扩展）与支持，我们强烈建议您查看我们的[企业支持 ](https://nextcloud.com/enterprise/)。

| 平台             | 选项                                                         |
| ---------------- | ------------------------------------------------------------ |
| 操作系统（64位） | **Ubuntu 24.04 LTS** (推荐)Ubuntu 22.04 LTS**Red Hat Enterprise Linux 9** (推荐)Debian 12 (Bookworm)SUSE Linux Enterprise Server 15openSUSE Leap 15.6CentOS StreamAlpine Linux |
| 数据库           | MySQL 8.0 / **8.4**（推荐）MariaDB 10.6 / 10.11 / **11.4**（推荐） / 11.8Oracle Database 11g, 19c, 21c, 23ai ( *仅作为企业订阅的一部分* )PostgreSQL 13/14/15/16/17SQLite 3.24+ ( *仅推荐用于测试和最小实例* ) |
| Web 服务器       | **Apache 2.4 配合** `mod_php` **或** `php-fpm` (推荐)nginx with `php-fpm` |
| PHP 运行时       | 8.2 ( *已弃用* )8.3**8.4** ( *推荐* )                        |

参见 [Linux 系统上的安装](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html)了解安装 Nextcloud 所需的最低 PHP 模块和附加软件。

### CPU 架构和操作系统 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html#cpu-architecture-and-os)

Nextcloud 运行良好需要 64 位 CPU、操作系统和 PHP。

支持32位系统，但存在以下已知限制：

- 早于 Unix 纪元（1970-01-01）的日期不受支持
- 2038年之后的日期不受支持

### 内存 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html#memory)

运行 Nextcloud 服务器的内存需求差异很大，取决于用户数量、应用程序、文件数量以及服务器活动量。

Nextcloud 每个进程至少需要 **128MB** 内存，我们建议每个进程至少 **512MB** 内存。

在低内存环境中，某些功能或应用可能需要调整其默认设置才能正常运行（在某些情况下，可能需要完全禁用）。

警告

要使用内置的更新器，至少需要 256MB 内存。

### MySQL / MariaDB 的数据库要求 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html#database-requirements-for-mysql-mariadb)

如果你正在运行 Nextcloud 与 MySQL / MariaDB 数据库一起使用，则目前需要以下内容：

- InnoDB 存储引擎（不支持 MyISAM）
- “READ COMMITTED”事务隔离级别（参见：[ 数据库“READ COMMITTED”事务隔离级别 ](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/linux_database_configuration.html#db-transaction-label)）
- 禁用或 BINLOG_FORMAT = ROW 配置的二进制日志记录（参见：https://dev.mysql.com/doc/refman/5.7/en/binary-log-formats.html）
- 关于 **Emoji (UTF8 4 字节)支持** ，请参见[启用 MySQL 4 字节支持](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/mysql_4byte_support.html)

### 为什么我们弃用旧版 PHP[](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html#why-we-drop-old-php-versions)

每年，都会推出新的 PHP 版本，旧版 PHP 会被弃用。这也影响了我们文档中推荐的 PHP 版本。

我们尽可能长时间地支持旧的 PHP 版本。然而，安全、性能和错误修复的列表只会不断增加，其中一些修复可能被认为是关键的，因此在某个时刻弃用将不可避免。

因此建议保持您的 PHP 版本更新。

#### 升级 PHP 的优势 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html#advantages-of-upgrading-php)

- **安全性**

  PHP 弃用旧版本的安全修复。只要我们支持已弃用的 PHP 版本，Nextcloud 就无法实现新 PHP 版本带来的安全修复，因为我们允许使用的语法必须是支持版本中最低的那个，因此第三方上游软件包会因放弃这种支持而失效。

- **性能**

  该语言随着时间的推移不断改进，这使得在更短的时间内能够处理更多的请求。

#### 长期支持 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html#long-term-support)

如果您将 Nextcloud 用于组织关键用途，可以考虑将订阅升级为高级订阅，该订阅包含 5 年的长期支持。这意味着在此延长期间，您将继续收到针对高优先级和关键安全问题的维护版本、数据丢失修复以及版本回归的更新。

## 桌面客户端 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html#desktop-client)

我们强烈建议使用最新版本的操作系统，以获得最完整和最稳定的客户端体验。

- **Windows** 10+
- **macOS** Monterey (12.0)+ (仅限 64 位) * 请注意，为了使桌面客户端能够成功连接，您的服务器可能需要符合 Apple App Transport Security 的要求。这可能需要使用一个符合 Apple 制定的标准充分签名的数字证书。更多信息请参考 Apple 的开发者文档： https://developer.apple.com/documentation/security/preventing-insecure-network-connections
- **Linux** (64 位仅限) 应在任何更新于 Ubuntu 18.04 的发行版上运行，使用我们的官方 AppImage 包

## 移动应用 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html#mobile-apps)

我们强烈建议使用您移动操作系统的最新版本，以获得我们移动应用的完整和最稳定的体验。

### 文件应用 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html#files-app)

- **iOS** 17.0+
- **Android** 8.1+

### Talk App[](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html#talk-app)

- **iOS** 16.0+
- **Android** 8.0+
- **Nextcloud Server** 19.0+
- **Nextcloud Talk** 9.0+

## Web 浏览器 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html#web-browser)

为了获得最佳的 Nextcloud 网页界面体验，我们建议您使用此列表中最新且受支持的浏览器，或基于这些浏览器的浏览器：

- Microsoft **Edge**
- Mozilla **Firefox**
- Google **Chrome**/Chromium
- Apple **Safari**

注意

如果您想使用 Nextcloud Talk，您应该使用 Mozilla **Firefox** 52+或 Google **Chrome**/Chromium 49+以获得完整的视频通话和屏幕共享体验。Google Chrome/Chromium 需要额外的插件进行屏幕共享。







# 部署建议 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/deployment_recommendations.html#deployment-recommendations)

在我们的[客户门户](https://portal.nextcloud.com/categories/Scalability/Deployment-recommendations)中查找针对企业的最新部署建议。







# 准备 PHP[](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#preparing-php)

在安装 Nextcloud 服务器之前，请确保您的 PHP 环境已正确配置。这包括安装正确的 PHP 版本、启用所需的 PHP 模块以及调整重要的 php.ini 设置。本指南将解释哪些 PHP 模块是必要的，哪些是推荐用于最佳性能和兼容性的，以及如何配置您的 PHP 环境以供 Web 服务器和命令行使用。

注意

如果您计划使用即用型 Nextcloud 服务器安装方法（如 AIO、Snap、NCP 或社区 Docker），则可以安全地忽略本章。这些安装方法提供了已预先配置用于与 Nextcloud 服务器一起使用的 PHP 环境。有关在这些环境中自定义 PHP 的指导，请参考专门为或由这些安装方法提供的文档。

- [PHP 安装](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#php-installation)
- [必需的 PHP 模块](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#required-php-modules)
- [必需的 PHP 数据库连接器](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#required-php-database-connectors)
- [推荐通用 PHP 模块](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#recommended-general-php-modules)
- [推荐 PHP 缓存模块](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#recommended-php-caching-modules)
- [推荐 PHP 命令行模块](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#recommended-php-cli-modules)
- [媒体管理 PHP 模块](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#php-modules-for-media-management)
- [特定应用的 PHP 模块](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#php-modules-for-specific-applications)
- [PHP ini 设置](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#php-ini-settings)
- [关于 PHP ini 配置的说明](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#notes-on-php-ini-configuration)
- [PHP 模块快速参考表](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#php-module-quick-reference-table)
- [更多资源](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#further-resources)

## [PHP 安装 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#id1)[](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#php-installation)

参考您的操作系统发行版的文档来获取建立基础 PHP 安装的说明。您可能可以在多个 PHP 版本中选择。参考[系统要求](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html)来查看哪些 PHP 版本被此版本的 Nextcloud Server 所支持。在完成基础 PHP 安装后，请按照以下指南配置您的新的 PHP 安装以用于新的 Nextcloud Server 部署。

## [必需的 PHP 模块 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#id2)[](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#required-php-modules)

以下 PHP 模块**必须**被安装并启用，以便 Nextcloud Server 能够正常运行：

- ctype (随 PHP 一同提供)
- curl
- DOM
- fileinfo (随 PHP 一起提供)
- filter (仅在 Mageia 和 FreeBSD 上可用)
- GD
- libxml (需要 Linux 软件包 libxml2 版本 >= 2.7.0)
- mbstring
- OpenSSL (随 PHP 一起提供)
- posix
- session (PHP 自带)
- SimpleXML
- XMLReader
- XMLWriter
- zip
- zlib



> ctype

、fileinfo和OpenSSL模块通常在 PHP 中默认包含并启用。通常，其他一些必需的模块会由操作系统发行版的包管理器自动安装。



**如何检查模块是否启用：**

- 运行 `php -m | grep -i <module_name>` 。如果看到输出，则模块处于活动状态。

注意



> filter

模块仅在 Mageia 和 FreeBSD 上需要。



## [所需的 PHP 数据库连接器 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#id3)[](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#required-php-database-connectors)

安装您计划使用的数据库的 PHP 连接器模块（选择一个）：

- pdo_sqlite (>= 3，通常出于性能原因不建议使用)
- pdo_mysql (MySQL/MariaDB)
- pdo_pgsql (PostgreSQL)

## [推荐的一般 PHP 模块 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#id4)[](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#recommended-general-php-modules)

这些模块不是必需的，但强烈推荐以增强功能或安全性：

- intl: 修复非 ASCII 字符的排序并提高语言翻译性能。

- sodium: 提供 Argon2 密码散列（如果使用 PHP < 8.4 且 PHP 未使用 libargon2 构建时需要）。

  > 如果 Argon2 不可用，将使用 bcrypt，但如果密码先前使用 Argon2 哈希（例如在将现有 Nextcloud 服务器迁移到新服务器环境时），并且此模块缺失，账户将无法登录。

## [推荐 PHP 缓存模块 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#id5)[](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#recommended-php-caching-modules)

不需要内存缓存，因此这些模块不是必需的，但为了最佳性能和可靠性，强烈推荐安装。选择并安装您喜欢的内存缓存模块组合：

- APCu (>= 4.0.6)
- redis / phpredis (>= 2.2.6，用于事务文件锁定，必需)
- memcached (较旧的选择替代方案，不推荐用于新安装)

注意

内存缓存强烈推荐以获得最佳性能。在大多数情况下，对于新安装，APCu 和 redis 的组合是最佳选择。

有关配置详情，请参阅[内存缓存 ](https://docs.nextcloud.com/server/latest/admin_manual/configuration_server/caching_configuration.html)。

## [推荐的 PHP CLI 模块 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#id6)[](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#recommended-php-cli-modules)

**用于命令行处理** （可选）：

- pcntl：允许命令中断（例如，通过 `ctrl-c`）。

  > 确保 `pcntl_signal` 和 `pcntl_signal_dispatch` 在您的 php.ini 中没有被禁用。 `disable_functions` 选项。

**用于命令行更新器** （可选）：

- phar: 运行更新器需要：

  > `sudo -E -u www-data php /var/www/nextcloud/updater/updater.phar`

## [媒体管理 PHP 模块 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#id7)[](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#php-modules-for-media-management)

**图像元数据和方向** （可选）：

- exif: 图像元数据加载和旋转

**预览生成** (可选):

- imagick (用于图像预览)
- avconv 或 ffmpeg (用于视频预览)
- OpenOffice 或 LibreOffice（用于文档预览）

注意

如果预览 PDF 文件时出现“未授权”错误，您可能需要调整 imagick 策略文件。参见 https://cromwell-intl.com/open-source/pdf-not-authorized.html

参见 [预览配置 ](https://docs.nextcloud.com/server/latest/admin_manual/configuration_files/previews_configuration.html)获取更多预览生成的上下文信息。

## [针对特定应用的 PHP 模块 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#id8)[](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#php-modules-for-specific-applications)

某些可选的 Nextcloud 应用/功能需要额外的模块。按需安装：

- ldap: LDAP 集成
- smbclient: SMB/CIFS 集成（参见 [SMB/CIFS](https://docs.nextcloud.com/server/latest/admin_manual/configuration_files/external_storage/smb.html)）
- ftp: FTP 存储或外部用户认证
- imap: 外部用户认证

**推荐/可选：**

- gmp: SFTP 存储系统

## [PHP ini 设置 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#id9)[](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#php-ini-settings)

根据需要调整你的 php.ini 中的以下设置以适用于 Nextcloud：

- `disable_functions`：除非必要，否则避免禁用函数。
- `max_execution_time`：参见 [上传大文件 > 512MB](https://docs.nextcloud.com/server/latest/admin_manual/configuration_files/big_file_upload_configuration.html)
- `memory_limit`：应至少为 512MB。另见 [上传大文件 > 512MB](https://docs.nextcloud.com/server/latest/admin_manual/configuration_files/big_file_upload_configuration.html)
- `opcache.enable` 及相关设置：参见[内存缓存](https://docs.nextcloud.com/server/latest/admin_manual/configuration_server/caching_configuration.html)和[服务器调优](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html)
- `open_basedir`：参见[强化与安全指南](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html)
- `upload_tmp_dir`：参见[上传大文件 > 512MB](https://docs.nextcloud.com/server/latest/admin_manual/configuration_files/big_file_upload_configuration.html)

## [关于 PHP ini 配置的说明 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#id10)[](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#notes-on-php-ini-configuration)

- **多个 php.ini 文件：**

  > - 您可能需要在多个 php.ini 文件中配置设置（例如，用于 Web 服务器和 CLI）。
  >
  >   > - - Web server:
  >   >
  >   >     /etc/php/<version>/apache2/php.ini 或 /etc/php/<version>/fpm/php.ini
  >   >
  >   > - - CLI (used by Nextcloud CRON jobs):
  >   >
  >   >     /etc/php/<version>/cli/php.ini

- **查找每个 SAPI 使用的 php.ini 文件：**

  > - 对于 CLI，使用 `php --ini`，或者在网页中检查 `phpinfo()`。

- **搜索参数：**

  > - 运行 `grep -r <parameter_name> /etc/php` (例如 `grep -r date.timezone /etc/php` )

- **将 `<version>` 替换为您的实际 PHP 版本 (例如 8.1、8.2 等)。**

## [PHP 模块快速参考表 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#id11)[](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#php-module-quick-reference-table)

| 模块             | 必需 | 推荐 | 特定应用使用 | 描述                             |
| ---------------- | ---- | ---- | ------------ | -------------------------------- |
| ctype            | ✓    |      |              | 核心功能                         |
| curl             | ✓    |      |              | HTTP 请求                        |
| DOM              | ✓    |      |              | 文档对象模型（XML/HTML 处理）    |
| fileinfo         | ✓    |      |              | 文件类型检测                     |
| filter*          | ✓*   |      |              | 数据过滤和验证（Mageia/FreeBSD） |
| GD               | ✓    |      |              | 图像处理                         |
| libxml           | ✓    |      |              | XML 解析（libxml2 >= 2.7.0）     |
| mbstring         | ✓    |      |              | 多字节字符处理                   |
| OpenSSL          | ✓    |      |              | 安全通信                         |
| posix            | ✓    |      |              | POSIX 函数                       |
| session          | ✓    |      |              | 会话支持                         |
| SimpleXML        | ✓    |      |              | 简单 XML 解析                    |
| XMLReader        | ✓    |      |              | XML 读取                         |
| XMLWriter        | ✓    |      |              | XML 写入                         |
| zip              | ✓    |      |              | 压缩文件处理                     |
| zlib             | ✓    |      |              | 压缩和解压缩                     |
| intl             |      | ✓    |              | 改进翻译和排序                   |
| sodium           |      | ✓    |              | Argon2 密码哈希                  |
| ldap             |      |      | ✓            | LDAP 集成                        |
| smbclient        |      |      | ✓            | SMB/CIFS 集成                    |
| ftp              |      |      | ✓            | FTP 存储/认证                    |
| imap             |      |      | ✓            | 外部用户认证                     |
| gmp              |      |      | ✓ (可选)     | SFTP 存储                        |
| exif             |      |      | ✓ (可选)     | 图片应用中的图像旋转             |
| apcu             |      | ✓    |              | 性能缓存                         |
| memcached        |      | ✓    |              | 性能缓存                         |
| redis            |      | ✓    |              | 事务文件锁                       |
| imagick          |      |      | ✓ (可选)     | 图片预览                         |
| avconv/ffmpeg    |      |      | ✓ (可选)     | 视频预览                         |
| Open/LibreOffice |      |      | ✓ (可选)     | 文档预览                         |
| pcntl            |      |      | ✓ (可选)     | CLI 中的命令中断                 |
| phar             |      |      | ✓ (可选)     | 命令行更新器需要                 |

*过滤器模块仅在 Mageia 和 FreeBSD 上需要。

## [更多资源 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#id12)[](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html#further-resources)

- 关于每个模块的更多详细信息，请参阅 [官方 PHP 文档 ](https://php.net/manual/en/extensions.php).
- 有关在您的环境中安装 PHP 模块的具体信息，请参考您的操作系统发行版的文档。
- 在 PHP 中， *扩展*和*模块*这两个词可以互换使用。在我们的文档中，我们使用*模块*这个词。
- 在修改 `php.ini` 文件或安装模块后，始终重启您的 Web 服务器和 PHP-FPM。





# Linux 系统上的安装 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#installation-on-linux)

安装 Nextcloud 的方式有多种，具体取决于您的偏好、需求和目标。

如果您倾向于自动化安装，可以选择：

- 使用[官方 Nextcloud 安装方法 ](https://github.com/nextcloud/all-in-one#nextcloud-all-in-one)。Nextcloud AIO 提供便捷的部署和维护，大部分功能都包含在这个单一 Nextcloud 实例中。它包括 Office、即用型备份解决方案、Imaginary（用于预览 heic、heif、illustrator、pdf、svg、tiff 和 webp）等。
- 使用 [社区 Snap 包 ](https://snapcraft.io/nextcloud)。这包括一个完整的可生产堆栈，会为您维护 HTTPS 证书，并会根据需要自动更新以保持安全。
- 使用 [社区 Nextcloud VM 实例 ](https://github.com/nextcloud/vm/)（又名 Nextcloud 虚拟机或 NcVM）。这能帮助您更快更轻松地创建个人或企业 Nextcloud 服务器。它可以直接安装在干净的 Ubuntu 服务器上，也可以作为一个完全功能的虚拟机下载。
- 使用 [社区 NextcloudPi 脚本 ](https://nextcloudpi.com/)（基于 Debian）。它会为您设置一切，并包含用于自动安装应用（如 Collabora、OnlyOffice、Talk 等）的脚本。
- 使用 [社区 Nextcloud Docker 镜像 ](https://hub.docker.com/_/nextcloud/)。此镜像设计用于微服务环境。您可以选择两种镜像版本：Apache 版本包含完整的 Nextcloud 安装，包括 Apache 服务器。第二个选项是 FPM 安装，它运行一个 FastCGI 进程来提供您的 Nextcloud 安装（您需要提供您喜欢的 Web、数据库和其他所需补充服务）。

注意

请注意，社区选项并非由 Nextcloud GmbH 官方支持。

提示

如需基于 Helm Charts（也适用于 Podman）的企业级可扩展安装，请[联系 Nextcloud GmbH](https://nextcloud.com/enterprise/)。

如果您倾向于从源代码归档安装，可以使用经典的 LAMP 堆栈（Linux、Apache、MySQL/MariaDB、PHP）从零开始设置 Nextcloud。本文件提供了在 Ubuntu 18.04 LTS 服务器上使用 Apache 和 MariaDB，通过 [Nextcloud .tar 归档](https://nextcloud.com/install/)安装 Nextcloud 的完整指南。推荐使用此方法安装 Nextcloud。

本安装指南概述了所需的依赖项及其配置。如需特定发行版的设置指南，请查看 [Ubuntu 22.04 LTS 的示例安装](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_ubuntu.html)和 [CentOS 8 的示例安装 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_centos.html)。

注意

在 SELinux 启用的发行版（如 CentOS、Fedora 和 Red Hat Enterprise Linux）的管理员可能需要设置新的规则以启用安装 Nextcloud。请参阅 [SELinux 配置技巧](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#selinux-tips-label)以获取建议的配置。

## 手动安装的先决条件 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#prerequisites-for-manual-installation)

Nextcloud 的 .tar 存档包含所有必需的 PHP 模块。您的 Linux 发行版应该有所有必需模块的软件包。参见 [准备 PHP](https://docs.nextcloud.com/server/latest/admin_manual/installation/php_configuration.html) 获取必需和建议模块的列表。

您不需要为您的 Web 服务器（即 Apache 的 `mod_webdav`）安装 WebDAV 模块，因为 Nextcloud 自带 WebDAV 服务器 SabreDAV。如果启用了 `mod_webdav`，您必须将其禁用以供 Nextcloud 使用。（参见 [Apache Web 服务器配置 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#apache-configuration-label)获取示例配置。）



## Apache Web 服务器配置 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#apache-web-server-configuration)

配置 Apache 需要一个配置文件 文件。在 Debian、Ubuntu 及其衍生版本上，这个文件将是 `/etc/apache2/sites-available/nextcloud.conf` . 在 Fedora 上， CentOS、RHEL 及类似系统，配置文件将是 `/etc/httpd/conf.d/nextcloud.conf` .

您可以选择在现有 Web 服务器的目录中安装 Nextcloud，例如 https://www.example.com/nextcloud/，或者在虚拟主机中安装，如果您希望 Nextcloud 可以通过自己的子域名访问，例如 https://cloud.example.com/。

要使用基于目录的安装，请在您的 `nextcloud.conf` 替换 **Directory** 和 **Alias** 路径为适合您系统的路径：

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



要使用虚拟主机安装，请将以下内容放入您的 `nextcloud.conf` 替换 **ServerName**，以及 **DocumentRoot** 和 **Directory** 文件路径应使用适合您系统的值：

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



在 Debian、Ubuntu 及其衍生系统中，您应运行以下命令以启用配置：

```
a2ensite nextcloud.conf
```



### 额外的 Apache 配置 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#additional-apache-configurations)

- 为了让 Nextcloud 正常工作，我们需要模块 `mod_rewrite`。通过运行以下命令来启用它：

  ```
  a2enmod rewrite
  ```

  

  推荐的额外模块包括 `mod_headers`、`mod_env`、`mod_dir` 和 `mod_mime`：

  ```
  a2enmod headers
  a2enmod env
  a2enmod dir
  a2enmod mime
  ```

  

  如果你使用的是 `mod_fcgi` 而不是标准的 `mod_php`，还需要启用：

  ```
  a2enmod setenvif
  ```

  

  并对配置应用以下修改：

  ```
  ProxyFCGIBackendType FPM
  
  <FilesMatch remote.php>
    SetEnvIf Authorization "(.*)" HTTP_AUTHORIZATION=$1
  </FilesMatch>
  ```

  

- 您必须禁用服务器配置的任何 Nextcloud 认证，因为它内部使用基本认证为 DAV 服务。如果您已在一个父文件夹中启用了认证（例如通过 `AuthType Basic`） 指令), 您可以专门关闭身份验证 Nextcloud 条目。根据上述示例配置文件，添加 在 `<Directory>` 部分中的以下行：

  ```
  Satisfy Any
  ```

  

- 使用 SSL 时，请特别注意 ServerName。您应在服务器配置中指定一个，同时在证书的 CommonName 字段中指定。如果您希望您的 Nextcloud 可以通过互联网访问，则应将这两个字段都设置为要访问的 Nextcloud 服务器的域名。

- 现在重启 Apache：

  ```
  service apache2 restart
  ```

  

- 如果您在子目录中运行 Nextcloud 并希望使用 CalDAV 或 CardDAV 客户端确保您已配置正确的 [服务发现 ](https://docs.nextcloud.com/server/latest/admin_manual/issues/general_troubleshooting.html#service-discovery-label)URL。



## 美观的 URL[](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#pretty-urls)

美观的 URL 会从所有 Nextcloud URL 中移除 `index.php` 部分，例如在分享链接 `https://example.org/nextcloud/index.php/s/Sv1b7krAUqmF8QQ` 中，使 URL 更短，从而更美观。

`mod_env` 和 `mod_rewrite` 必须安装在你的 Web 服务器上，并且 `.htaccess` 必须可被 HTTP 用户写入。要启用 `mod_env` 和 `mod_rewrite`，运行 `sudo a2enmod env` 和 `sudo a2enmod rewrite`。然后你可以在 `config.php` 中设置两个变量：

```
'overwrite.cli.url' => 'https://example.org/nextcloud',
'htaccess.RewriteBase' => '/nextcloud',
```



如果你的设置可以在 `https://example.org/nextcloud` 访问，或者：

```
'overwrite.cli.url' => 'https://example.org/',
'htaccess.RewriteBase' => '/',
```



如果它没有安装在子文件夹中。最后运行这个 occ 命令来更新你的 .htaccess 文件：

```
sudo -E -u www-data php /var/www/nextcloud/occ maintenance:update:htaccess
```



每次更新后，这些更改将自动应用于 `.htaccess`-文件。

注意

如果自动添加的 `.htaccess` 配置 SetEnv front_controller_active true 在您的环境中不起作用：编辑 `config/config.php` 并添加 `'htaccess.IgnoreFrontController' => true` 。有关详细说明，请参阅 [配置参数 ](https://docs.nextcloud.com/server/latest/admin_manual/configuration_server/config_sample_php_parameters.html)。



## 启用 SSL[](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#enabling-ssl)

注意

您可以使用明文 HTTP 使用 Nextcloud，但我们强烈建议您使用 SSL/TLS 加密所有服务器流量，并保护用户的登录和数据传输过程中的安全。

在 Ubuntu 下安装的 Apache 已经预配置了一个简单的自签名证书。您需要做的只是启用 ssl 模块和默认站点。打开终端并运行：

```
a2enmod ssl
a2ensite default-ssl
service apache2 reload
```



注意

自签名证书有其缺点——尤其是在您打算公开访问 Nextcloud 服务器时。建议您考虑获取由认证机构签名的证书。您可以咨询您的域名注册商或托管服务提供商，以获取商业证书的优惠。或者使用免费的 [Let’s Encrypt](https://letsencrypt.org/) 证书。



## 安装向导 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#installation-wizard)

重启 Apache 后，您必须通过运行图形安装向导或使用命令行中的 `occ` 来完成安装 命令。要启用此功能，请更改您的 Nextcloud 目录的所有权为 你的 HTTP 用户：

```
chown -R www-data:www-data /var/www/nextcloud/
```



注意

在 SELinux 支持的发行版上的管理员可能需要编写新的 SELinux 规则来完成他们的 Nextcloud 安装；参见 [SELinux 配置技巧 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#selinux-tips-label)。

要使用 `occ` 请参阅 [从命令行安装 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/command_line_installation.html)。

要使用图形化安装向导，请参阅[安装向导 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/installation_wizard.html)。



## 设置后台任务 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#setting-up-background-jobs)

Nextcloud 要求定期运行某些任务。这些任务可能包括为确保最佳性能而进行的维护任务，或发送通知等时间敏感任务。

有关详细说明和好处，请参阅[后台任务 ](https://docs.nextcloud.com/server/latest/admin_manual/configuration_server/background_jobs_configuration.html)。



## SELinux 配置技巧 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#selinux-configuration-tips)

参见 [SELinux 配置 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html)，为 SELinux 启用的发行版（如 Fedora 和 CentOS）提供建议配置。



## PHP-FPM 配置 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#php-fpm-configuration)

### 概述 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#overview)

[PHP-FPM](https://www.php.net/manual/en/install.fpm.php) 是基于 FastCGI 的 PHP 实现，包含对繁忙网站和大型 Web 应用有用的功能。将其与 Nextcloud 一起使用是一个高级主题，需要熟悉 PHP-FPM 的工作方式。在大多数情况下，默认设置不适合 Nextcloud 使用。这里我们将重点介绍几个最重要的需要调整的领域。

### 进程管理器 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#process-manager)

许多 PHP-FPM 安装中的 `pm.max_children` 默认值低于适当值。值过低可能导致客户端连接问题、无法解释的错误以及性能问题。这是*网关超时*的常见原因。然而，相对于可用资源（如内存）而言，值过高也会导致问题。默认值通常是 `5`。这会极大地限制同时连接到您的 Nextcloud 实例的数量，并且除非您受到严重的资源限制，否则会浪费硬件资源。请查看[服务器调优](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html) 章节，以获取一些指导和建议，以及确定适当值的资源， 以及其他相关参数。

### 系统环境变量 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#system-environment-variables)

在使用 `php-fpm` 时，系统环境变量如 PATH、TMP 等并不会像使用 `php-cli` 时那样自动填充。因此，像 `getenv('PATH');` 这样的 PHP 调用可能会返回空结果。所以你可能需要手动在适当的 `php-fpm` ini 配置文件中配置环境变量。

以下是这些 ini 配置文件的示例根路径：

| Debian/Ubuntu/Mint  | CentOS/Red Hat/Fedora |
| ------------------- | --------------------- |
| `/etc/php/8.3/fpm/` | `/etc/php-fpm.d/`     |

在两个示例中，ini/config 文件被称为 `www.conf`，根据你的发行版版本或所做的自定义，它可能位于子目录中，例如 `pool.d`。

通常，你会发现在文件中已经存在一些或全部环境变量，但以如下方式被注释掉：

```
;env[HOSTNAME] = $HOSTNAME
;env[PATH] = /usr/local/bin:/usr/bin:/bin
;env[TMP] = /tmp
;env[TMPDIR] = /tmp
;env[TEMP] = /tmp
```



取消注释相应的现有条目。然后运行 `printenv PATH` 来确认你的路径，例如：

```
$ printenv PATH
/home/user/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:
/sbin:/bin:/
```



如果您的系统环境变量不在文件中，则必须添加它们。

或者，您可以通过修改：

```
/etc/php/8.3/fpm/pool.d/www.conf
```



并取消注释该行：

```
clear_env = no
```



当您使用共享主机或控制面板来管理您的 [Nextcloud VM](https://github.com/nextcloud/vm) 时 或服务器上，配置文件几乎 可以确定位于其他位置，出于安全和灵活性的原因，因此 请查阅您的文档以获取正确的位置。

请记住，可以创建不同的设置 `php-cli` 和 `php-fpm`，以及不同的域和网站。检查您设置的最佳方法是使用 [PHP 版本和信息 ](https://docs.nextcloud.com/server/latest/admin_manual/issues/general_troubleshooting.html#label-phpinfo)。

### 最大上传大小 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#maximum-upload-size)

如果您想增加最大上传大小，您还需要修改您的 `php-fpm` 配置，并增加 `upload_max_filesize` 和 `post_max_size` 值。您需要重启 `php-fpm` 和您的 HTTP 服务器，以便这些更改生效。

### .htaccess[](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#htaccess)

Nextcloud 自带自己的 `nextcloud/.htaccess` 文件。因为 `php-fpm` 无法读取 `.htaccess` 中的 PHP 设置，所以这些设置和权限必须在 `nextcloud/.user.ini` 文件中设置。



## 其他 Web 服务器 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#other-web-servers)

- [NGINX 配置](https://docs.nextcloud.com/server/latest/admin_manual/installation/nginx.html)



## 在 Windows 上安装（虚拟机）[](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#installing-on-windows-virtual-machine)

如果你使用的是 Windows，最容易让 Nextcloud 运行起来的方式是使用虚拟机（VM）。有两种选择：

- **企业/SME 设备**

Nextcloud GmbH 维护一个基于 [Univention Corporate Server (UCS)](https://www.univention.com/products/univention-app-center/app-catalog/nextcloud/) 的免费设备 具有简便的图形设置和基于网络的行政管理。它包括用户 通过 LDAP 进行管理，可以替换现有的 Active Directory 设置和 具有可选的 ONLYOFFICE 和 Collabora Online 集成，还有更多应用程序 易于快速安装。

它可以在硬件上安装，或使用 VirtualBox、VMWare (ESX) 和 KVM 镜像在虚拟机中运行。

在此处下载设备：

- [Univention Corporate Server (UCS)](https://www.univention.com/products/univention-app-center/app-catalog/nextcloud/)

- **家庭用户/SME 设备**

[Nextcloud 虚拟机](https://github.com/nextcloud/vm)由 [T&M Hansson IT](https://www.hanssonit.se/nextcloud-vm/) 维护，并提供多个不同版本。通过包含的脚本可以轻松安装 Collabora、OnlyOffice、全文搜索和其他应用，您可以选择在首次设置时运行这些脚本，或稍后下载并运行。您可以在 [GitHub](https://github.com/nextcloud/vm/blob/main/apps/) 上找到所有当前可用的自动化应用安装。

该虚拟机提供不同的大小和版本。

所有可用版本 [在此 ](https://shop.hanssonit.se/product-category/virtual-machine/nextcloud-vm/)。

完整的说明和下载请参阅：

- [Nextcloud VM (GitHub)](https://github.com/nextcloud/vm/)
- [Nextcloud VM (T&M Hansson IT)](https://www.hanssonit.se/nextcloud-vm/)

注意

只要您可以在您的虚拟机管理程序中挂载 OVA、VMDK 或 VHD/VHDX 虚拟机，您就可以在多种不同的操作系统上安装该虚拟机。如果您使用的是 KVM，则需要从 GitHub 上的脚本安装该虚拟机。您可以遵循 [README 中的说明 ](https://github.com/nextcloud/vm#build-your-own-vm-or-install-on-a-vps)。



## 通过 Snap 软件包安装 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#installing-via-snap-packages)

Nextcloud Snap 是一种由社区驱动的安装方法，旨在易于安装且维护简单。理想的 Nextcloud Snap 是一个“安装后无需管理”的 Nextcloud 实例，它适用于大多数架构，并能自行更新而无需管理员技能。将 Nextcloud 与 snapd 结合使用，使其非常适合物联网或可扩展环境。[Snapd](https://snapcraft.io/docs) 是一种安全且稳健的技术，Nextcloud Snap 团队已采用这一技术。

最重要的是，snap 包被设计为安全的、沙盒化的、容器化的应用程序，它们与底层系统和其它应用程序隔离。

然而，该 snap 是有特定见解的，并且需要满足[要求 ](https://github.com/nextcloud-snap/nextcloud-snap/wiki/Installation-requirements)。

- Nextcloud snap 使用推荐的 Apache。
- Nextcloud snap 使用推荐的 MySQL。
- Nextcloud snap 使用推荐的 PHP。

### 安装 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#installation)

**在 Ubuntu 上**

- https://snapcraft.io/nextcloud
- 安装 Nextcloud `sudo snap install nextcloud`

**其他所有发行版**[请注意](https://github.com/nextcloud-snap/nextcloud-snap/wiki/Why-Ubuntu-is-the-only-supported-distro/)

默认情况下将安装最新的稳定版 Nextcloud snap 包，并会自动更新到后续的稳定版本，但还有[其他版本可供选择](https://github.com/nextcloud/nextcloud-snap/wiki/Release-strategy) 并且你可以完全控制[自动更新 ](https://github.com/nextcloud-snap/nextcloud-snap/wiki/Managing-automatic-updates)。

安装完成后，Nextcloud 将自动启动。假设你和安装它的设备在同一网络中，你可以通过浏览器访问 `<hostname>.local` 或实例的 IP 地址来访问 Nextcloud 安装。如果你的主机名是 `localhost` 或 `localhost.localdomain`，就像在 Ubuntu Core 设备上那样， `nextcloud.local` 将被使用。

### 首次登录 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#st-login)

首次访问 Nextcloud 安装页面时，系统会提示您在初始化 Nextcloud 之前输入管理员用户名和密码。这可能需要一些时间，具体取决于资源和设备。提供这些信息后，您将登录并能够安装应用、创建用户以及上传文件。

### HTTPS 加密 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#https-encryption)

Nextcloud snap 包含一个用于自动化 HTTPS 加密和自动续期（使用 Let's Encrypt 或自签名证书）的服务。运行 `nextcloud.enable-https -h` 获取更多信息。[ 管理加密 ](https://github.com/nextcloud-snap/nextcloud-snap/wiki/Managing-HTTP-encryption-(HTTPS))。

### 配置 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#configuration)

虽然 Nextcloud 的默认配置大多可以满足需求，但可能需要通过手动编辑配置文件或使用管理控制台来微调 Nextcloud snap。 [配置 Nextcloud snap](https://github.com/nextcloud-snap/nextcloud-snap/wiki/Configure-Nextcloud-snap)。

### 外部媒体 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#external-media)

[snap 隔离](https://snapcraft.io/docs/snap-confinement)是一项安全功能，它决定了应用程序对系统资源（如文件、网络、外围设备和服务）的访问权限。因此，您的 Nextcloud snap 被安全地隔离在主机系统之外。除非您明确允许 Nextcloud snap 访问主机系统上的 `/media` 或 `/mnt` 目录，否则您将无法访问隔离之外的任何其他目录。

可移动媒体或外部存储必须以 root 权限挂载到 `/media` 或 `/mnt`，并与 Snap!连接。[ 管理外部媒体和存储](https://github.com/nextcloud-snap/nextcloud-snap/wiki/Managing-external-media,-shares-and-storage)

提供访问可移动媒体能力的界面在安装时不会自动连接，要使用外部存储（或在 `/media` 或 `/mnt` 中用于数据的其他设备），需要通过连接该界面授予 snap 访问可移动媒体的权限：

```
sudo snap connect nextcloud:removable-media
```

更多文档、一个广泛的 [Wiki](https://github.com/nextcloud-snap/nextcloud-snap/wiki) 和 [FAQ](https://github.com/nextcloud-snap/nextcloud-snap/wiki/FAQ's) 可以在[开发者 GitHub](https://github.com/nextcloud-snap/nextcloud-snap) 上找到。

注意

[snapd 技术 ](http://snapcraft.io/docs/core/) 是核心 为 snaps 提供动力的工具，它提供了一种新的打包、分发、更新和 在 Linux 系统上运行操作系统组件和应用程序。更多关于 snaps 的信息，请参见 [snapcraft.io](http://snapcraft.io/)

## 通过 VPS 或网页空间使用网页安装程序进行安装 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#installation-via-web-installer-on-a-vps-or-web-space)

当您无法访问命令行时，例如在网页托管或 VMPS 环境中， 一个简单的选择是使用我们的网页安装程序。此脚本可以在我们的 [服务器安装页面这里找到。](https://nextcloud.com/install/#instructions-server)

脚本检查依赖项，从官方服务器下载 Nextcloud，使用正确的权限和用户账户解压。最后，您将被重定向到 Nextcloud 安装程序。这里有一个快速指南：

1. 从安装页面获取文件
2. 将 setup-nextcloud.php 上传到您的网站空间
3. 将您的网页浏览器指向您网站空间上的 setup-nextcloud.php
4. 按照说明配置 Nextcloud
5. 登录到您新创建的 Nextcloud 实例！

注意

安装程序使用与 Nextcloud 内置更新器相同的 Nextcloud 版本。在重大版本发布后，可能需要长达一个月的时间才能通过网页安装程序和更新器获得。这是为了将新重大版本的部署分摊到一段时间内。

## 在 TrueNAS 上安装 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#installation-on-truenas)

请参阅 [TrueNAS 安装文档 ](https://www.truenas.com/docs/core/solutions/integrations/nextcloud/)。

## 通过安装脚本安装 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#installation-via-install-script)

安装最简单的方法之一是使用 Nextcloud VM 或 NextcloudPI 脚本。基本上只需要两个步骤：

1. 下载最新的[虚拟机安装脚本 ](https://github.com/nextcloud/vm/blob/main/nextcloud_install_production.sh/)。

2. 使用以下命令运行脚本：

   ```
   sudo bash nextcloud_install_production.sh
   ```

   

或者

1. 下载最新的 [PI 安装脚本 ](https://raw.githubusercontent.com/nextcloud/nextcloudpi/master/install.sh)。

2. 使用以下命令运行脚本：

   ```
   sudo bash install.sh
   ```

   

接下来将进入引导式设置，你只需要按照屏幕上的指示进行操作即可。







# 安装向导 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/installation_wizard.html#installation-wizard)

## 快速入门 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/installation_wizard.html#quick-start)

当 Nextcloud 的先决条件得到满足且所有 Nextcloud 文件都已安装后，完成安装的最后一步是运行安装向导。这只需要三个步骤：

1. 将您的 Web 浏览器指向 `http://localhost/nextcloud`
2. 输入您希望的管理员的用户名和密码。
3. 点击 **完成设置** 。

[![screenshot of the installation wizard](https://docs.nextcloud.com/server/latest/admin_manual/_images/install-wizard-a.png)](https://docs.nextcloud.com/server/latest/admin_manual/_images/install-wizard-a.png)

您已完成设置，可以开始使用新的 Nextcloud 服务器了。

当然，您还可以做更多事情来为 Nextcloud 服务器设置最佳性能和安全性。在接下来的部分中，我们将涵盖重要的安装和安装后步骤。

- [数据目录位置](https://docs.nextcloud.com/server/latest/admin_manual/installation/installation_wizard.html#data-directory-location-label)
- [数据库选择](https://docs.nextcloud.com/server/latest/admin_manual/installation/installation_wizard.html#database-choice-label)
- [可信域](https://docs.nextcloud.com/server/latest/admin_manual/installation/installation_wizard.html#trusted-domains-label)



## 数据目录位置 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/installation_wizard.html#data-directory-location)

点击**存储和数据库**以显示用于您的 Nextcloud 数据目录和数据库的附加安装配置选项。

[![installation wizard with all options exposed](https://docs.nextcloud.com/server/latest/admin_manual/_images/install-wizard-a1.png)](https://docs.nextcloud.com/server/latest/admin_manual/_images/install-wizard-a1.png)

如果你使用的是除 Apache 以外的 HTTP 服务器，或者出于其他原因（例如在存储服务器上）希望将 Nextcloud 数据存储在不同的位置，你应该将 Nextcloud 数据目录定位在 Web 根目录之外。最好在安装时配置数据目录的位置，因为安装后很难移动。你可以将其放在任何地方；在这个示例中，它位于 `/opt/nextcloud/`。这个目录必须已经存在，并且必须由你的 HTTP 用户拥有。



## 数据库选择 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/installation_wizard.html#database-choice)

SQLite 是 Nextcloud 服务器的默认数据库，它仅适用于测试和小型单用户设置，且不支持客户端同步。支持的数据库有 MySQL、MariaDB、Oracle 11g 和 PostgreSQL，我们推荐 [MySQL/MariaDB](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html)。在运行安装向导之前，您必须安装数据库和 PHP 连接器。如果您通过软件包安装 Nextcloud，所有必要的依赖项将会被满足（有关所需和可选 PHP 模块的详细列表，请参阅 [Linux 上的安装 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html)）。您需要使用数据库的 root 登录，或任何管理员登录，然后输入您希望为 Nextcloud 数据库命名的任何名称。请小心，您的管理员登录需要有创建和修改数据库的权限，并且需要有授予其他用户权限的权限。

在您输入数据库的根或管理员登录信息后，安装程序会创建一个具有仅限于 Nextcloud 数据库权限的特殊数据库用户。然后 Nextcloud 只需要这个特殊的 Nextcloud 数据库用户，并会删除根 dB 登录。此用户以您的 Nextcloud 管理员用户命名，带有 `oc_` 前缀，并分配一个随机密码。Nextcloud 数据库用户和密码会写入 `config.php`：

```
'dbuser' => 'oc_molly',
'dbpassword' => 'pX65Ty5DrHQkYPE5HRsDvyFHlZZHcm',
```



点击完成设置，开始使用您的新的 Nextcloud 服务器。

[![Nextcloud welcome screen after a successful installation](https://docs.nextcloud.com/server/latest/admin_manual/_images/install-wizard-a2.png)](https://docs.nextcloud.com/server/latest/admin_manual/_images/install-wizard-a2.png)

现在我们将查看一些重要的安装后步骤。



## 可信域名 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/installation_wizard.html#trusted-domains)

所有用于访问您的 Nextcloud 服务器的 URL 都必须在您的 `config.php` 文件中的 `trusted_domains` 设置下进行白名单设置。只有当用户将浏览器指向 `trusted_domains` 设置中列出的 URL 时，才允许他们登录 Nextcloud。这不是一个允许的客户端域名或 IP 地址的列表。您可以使用 IP 地址和域名。一个典型的配置如下：

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

回环地址 `127.0.0.1` 会自动白名单，只要你有权限访问物理服务器，就可以一直登录。如果设置了负载均衡器，只要它发送正确的 X-Forwarded-Host 头部信息就不会有问题。当用户尝试访问未白名单的 URL 时，会出现以下错误：

[![Error message when URL is not whitelisted](https://docs.nextcloud.com/server/latest/admin_manual/_images/install-wizard-a4.png)](https://docs.nextcloud.com/server/latest/admin_manual/_images/install-wizard-a4.png)







# 从命令行安装 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/command_line_installation.html#installing-from-command-line)

现在完全可以通过命令行安装 Nextcloud。这对于脚本操作、无头服务器以及偏好命令行的系统管理员来说很方便。通过命令行安装 Nextcloud 有三个阶段：

1. 下载 Nextcloud 代码并在适当的目录中解压 tarball。（参见 [Linux 上的安装 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html)。）
2. 将你的 `nextcloud` 目录的所有权更改为你的 HTTP 用户，例如 Debian/Ubuntu 的示例。你必须以你的 HTTP 用户身份运行 `occ`；参见 [以 HTTP 用户身份运行 occ](https://docs.nextcloud.com/server/latest/admin_manual/occ_command.html#http-user-label):

```
$ sudo chown -R www-data:www-data /var/www/nextcloud/
```



3. 使用 `occ` 命令完成你的安装。这取代了运行图形安装向导：

```
$ cd /var/www/nextcloud/
$ sudo -E -u www-data php occ  maintenance:install \
--database 'mysql' --database-name 'nextcloud' \
--database-user 'root' --database-pass 'password' \
--admin-user 'admin' --admin-pass 'password'
```



注意，你必须切换到根 Nextcloud 目录，如上例所示，以运行 `occ maintenance:install`，否则安装会因为 PHP 致命错误消息而失败。

支持的数据库有：

```
- sqlite (SQLite3 - Nextcloud Community edition only)
- mysql (MySQL/MariaDB)
- pgsql (PostgreSQL)
- oci (Oracle 11g currently only possible if you contact us at https://nextcloud.com/enterprise as part of a subscription)
```



更多信息，请参见[命令行安装 ](https://docs.nextcloud.com/server/latest/admin_manual/occ_command.html#command-line-installation-label)。







# SELinux 配置 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html#selinux-configuration)

当你在 Linux 发行版上启用了 SELinux 时，在新安装的 Nextcloud 后可能会遇到权限问题，并在 Nextcloud 日志中看到`权限 拒绝`错误。

提示

权限问题可能由 SELinux 引起，即使审计日志中没有显示拒绝信息。这是因为 SELinux 不会记录用于验证访问的所有系统调用。参见[静默拒绝的可能原因](https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/7/html/selinux_users_and_administrators_guide/sect-security-enhanced_linux-troubleshooting-fixing_problems#sect-Security-Enhanced_Linux-Fixing_Problems-Possible_Causes_of_Silent_Denials)来解决这个问题。

对于大多数使用默认发行版配置文件的 SELinux 系统，以下设置应该有效。以 root 身份运行这些命令，并记得根据你的安装情况调整这些示例中的文件路径：

```
semanage fcontext -a -t httpd_sys_rw_content_t '/var/www/html/nextcloud/data(/.*)?'
semanage fcontext -a -t httpd_sys_rw_content_t '/var/www/html/nextcloud/config(/.*)?'
semanage fcontext -a -t httpd_sys_rw_content_t '/var/www/html/nextcloud/apps(/.*)?'
semanage fcontext -a -t httpd_sys_rw_content_t '/var/www/html/nextcloud/.htaccess'
semanage fcontext -a -t httpd_sys_rw_content_t '/var/www/html/nextcloud/.user.ini'
semanage fcontext -a -t httpd_sys_rw_content_t '/var/www/html/nextcloud/3rdparty/aws/aws-sdk-php/src/data/logs(/.*)?'

restorecon -Rv '/var/www/html/nextcloud/'
```



如果你卸载了 Nextcloud，需要移除 Nextcloud 目录的标签。在卸载 Nextcloud 后，以 root 身份执行以下命令：

```
semanage fcontext -d '/var/www/html/nextcloud/data(/.*)?'
semanage fcontext -d '/var/www/html/nextcloud/config(/.*)?'
semanage fcontext -d '/var/www/html/nextcloud/apps(/.*)?'
semanage fcontext -d '/var/www/html/nextcloud/.htaccess'
semanage fcontext -d '/var/www/html/nextcloud/.user.ini'
semanage fcontext -d '/var/www/html/nextcloud/3rdparty/aws/aws-sdk-php/src/data/logs(/.*)?'

restorecon -Rv '/var/www/html/nextcloud/'
```



如果你自定义了 SELinux 策略，而以上示例不起作用，你必须给予 HTTP 服务器对这些目录的写权限：

```
/var/www/html/nextcloud/data
/var/www/html/nextcloud/config
/var/www/html/nextcloud/apps
```



## 通过网页界面启用更新 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html#enable-updates-via-the-web-interface)

要通过网页界面启用更新，您可能需要启用对目录的写入权限：

```
setsebool httpd_unified on
```



更新完成后，禁用写入权限：

```
setsebool -P  httpd_unified  off
```



## 禁止对整个网页目录的写入访问 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html#disallow-write-access-to-the-whole-web-directory)

出于安全原因，建议禁用 /var/www/（默认）中所有文件夹的写权限：

```
setsebool -P  httpd_unified  off
```



## 允许访问远程数据库 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html#allow-access-to-a-remote-database)

如果您的安装连接到远程数据库，则需要额外的设置：

```
setsebool -P httpd_can_network_connect_db on
```



## 允许访问 LDAP 服务器 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html#allow-access-to-ldap-server)

使用此设置以允许 LDAP 连接：

```
setsebool -P httpd_can_connect_ldap on
```



## 允许访问远程网络 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html#allow-access-to-remote-network)

Nextcloud 需要访问远程网络以实现服务器间共享、外部存储或应用商店等功能。要允许此访问，请使用以下设置：

```
setsebool -P httpd_can_network_connect on
```



## 允许访问网络 memcache[](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html#allow-access-to-network-memcache)

如果 `httpd_can_network_connect` 已经开启，则无需此设置：

```
setsebool -P httpd_can_network_memcache on
```



## 允许访问 SMTP/sendmail[](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html#allow-access-to-smtp-sendmail)

如果您希望允许 Nextcloud 通过 sendmail 发送电子邮件通知，您需要使用以下设置：

```
setsebool -P httpd_can_sendmail on
```



## 允许访问 CIFS/SMB[](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html#allow-access-to-cifs-smb)

如果你将 datadir 放置在 CIFS/SMB 共享上，请使用以下设置：

```
setsebool -P httpd_use_cifs on
```



## 允许访问 FuseFS[](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html#allow-access-to-fusefs)

如果你的数据文件夹位于 Fuse 文件系统（例如 EncFS 等）上，此设置也同样需要：

```
setsebool -P httpd_use_fusefs on
```



## 允许 Rainloop 访问 GPG[](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html#allow-access-to-gpg-for-rainloop)

如果你使用支持 GPG/PGP 的 rainloop 网页邮件客户端应用程序，你可能需要这个：

```
setsebool -P httpd_use_gpg on
```



## 故障排除 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html#troubleshooting)

对于 SELinux 及其配置文件的常规故障排除，尝试安装包 `setroubleshoot` 并运行：

```
sealert -a /var/log/audit/audit.log > /path/to/mylogfile.txt
```



以获取有助于你配置 SELinux 配置文件的报告。

另一个用于故障排除的工具是为您的 Nextcloud 目录启用单个规则集：

```
semanage fcontext -a -t httpd_sys_rw_content_t '/var/www/html/nextcloud(/.*)?'
restorecon -RF /var/www/html/nextcloud
```



使用更细粒度的规则集（如开头示例所示）可以提供更强的安全性，因此仅用于测试和故障排除。它具有与禁用 SELinux 类似的效果，因此不要在生产系统上使用它。







# NGINX 配置 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/nginx.html#nginx-configuration)

注意

本页面介绍了运行 Nextcloud 服务器的示例 NGINX 配置。这些配置示例最初由 [@josh4trunks](https://github.com/josh4trunks) 提供 并由社区独家维护。（感谢贡献者！）

- 您需要将以下代码插入**您的 Nginx 配置文件** 。根据您是在 NGINX 的 [Web 根目录中部署 Nextcloud](https://docs.nextcloud.com/server/latest/admin_manual/installation/nginx.html#nginx-webroot-example)（即 `https://cloud.example.com/`）还是在 NGINX Web 根目录的 [Nextcloud 子目录中部署 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/nginx.html#nginx-subdir-example)（即 `https://cloud.example.com/nextcloud` ），选择相应的示例。
- 调整 `upstream php-handler` 下方的服务器指令，以匹配你的 PHP 安装配置的 FPM 监听器（此处配置错误会导致 `502 Bad Gateway` - 详细信息请参阅 [PHP-Handler 配置 / 避免“502 Bad Gateway”](https://docs.nextcloud.com/server/latest/admin_manual/installation/nginx.html#nginx-php-handler-tips)）
- 调整在 *两个* `server` 部分中找到的现有 `server_name` 指令，以匹配你的实际主机名
- 调整 `root` 到你的 Nextcloud 安装的网络根目录
- 调整 `ssl_certificate` 和 `ssl_certificate_key` 指令，以匹配你的签名证书和私钥的真实路径。确保你的 SSL 证书对 nginx 服务器进程是可读的（参见 [nginx HTTPS SSL 模块文档 ](https://wiki.nginx.org/HttpSslModule)）
- 如果使用 Let’s Encrypt 作为 TLS 证书并使用 nginx 作为 Web 服务器，请将 ssl_stapling 和 ssl_stapling_verify 设置为 off 在主 nginx 配置文件中（参见[Let’s Encrypt 博客文章](https://letsencrypt.org/2024/12/05/ending-ocsp))。
- 如果复制示例，请小心处理换行符，因为长行可能会因页面显示而被截断，导致配置文件无效。
- 某些环境可能需要将 `cgi.fix_pathinfo` 设置为 `1`。 `php.ini`.



## Nextcloud 在 NGINX 的 webroot[](https://docs.nextcloud.com/server/latest/admin_manual/installation/nginx.html#nextcloud-in-the-webroot-of-nginx)

以下配置应在 Nextcloud 位于您的 nginx 安装的 webroot 时使用。在此示例中，它是 `/var/www/nextcloud`，并通过 `http(s)://cloud.example.com/` 访问。

```
# Version 2025-07-23

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

    # Proxy and client response timeouts
    # Uncomment an increase these if facing timeout errors during large file uploads
    #proxy_connect_timeout 60s;
    #proxy_send_timeout 60s;
    #proxy_read_timeout 60s;
    #send_timeout 60s;

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
        fastcgi_request_buffering on;                   # Required as PHP-FPM does not support chunked transfer encoding and requires a valid ContentLength header.

        # PHP-FPM 504 response timeouts
        # Uncomment and increase these if facing timeout errors during large file uploads
        #fastcgi_read_timeout 60s;
        #fastcgi_send_timeout 60s;
        #fastcgi_connect_timeout 60s;

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





## Nextcloud 位于 NGINX 网站根目录的子目录中 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/nginx.html#nextcloud-in-a-subdir-of-the-nginx-webroot)

当 Nextcloud 放置在一个子目录中时，应使用以下配置： 你的 nginx 安装的 webroot。 在这个示例中，Nextcloud 文件位于 `/var/www/nextcloud`，Nextcloud 实例通过 `http(s)://cloud.example.com/nextcloud/` 访问。该配置与上述“Nextcloud 在 Web 根目录中”的配置有以下不同：

- 所有对 `/nextcloud` 的请求都被封装在一个单独的 `location` 块内，即 `location ^~ /nextcloud`。
- 字符串 `/nextcloud` 会被添加到所有前缀路径前。
- 域的根目录映射到 `/var/www` 而不是 `/var/www/nextcloud`，以便 URI `/nextcloud` 映射到服务器目录 `/var/www/nextcloud`。
- 处理 `/nextcloud` 之外路径请求的块（即 `/robots.txt` 和 `/.well-known`）被从 `location ^~ /nextcloud` 块中提取出来。
- 处理 /.well-known 的模块不需要正则表达式例外，因为阻止用户访问 Nextcloud 安装根目录下隐藏文件夹的规则不再匹配该路径。

```
# Version 2025-07-23

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

        # Proxy and client response timeouts
        # Uncomment an increase these if facing timeout errors during large file uploads
        #proxy_connect_timeout 60s;
        #proxy_send_timeout 60s;
        #proxy_read_timeout 60s;
        #send_timeout 60s;

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
            fastcgi_request_buffering on;                   # Required as PHP-FPM does not support chunked transfer encoding and requires a valid ContentLength header.

            # PHP-FPM 504 response timeouts
            # Uncomment and increase these if facing timeout errors during large file uploads
            #fastcgi_read_timeout 60s;
            #fastcgi_send_timeout 60s;
            #fastcgi_connect_timeout 60s;

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



### PHP 处理器配置 / 避免“502 错误网关”[](https://docs.nextcloud.com/server/latest/admin_manual/installation/nginx.html#php-handler-configuration-avoiding-502-bad-gateway)

上述 `server` 行需要调整为反映您本地的 PHP FPM 配置。它必须与您为 NC 使用的 PHP FPM 池中配置的 `listen` 指令相匹配。

许多 Linux 发行版在名为 `www` 的默认 PHP-FPM 池的 `www.conf` 文件中定义了一个监听器，该文件位于类似 `/etc/php/8.1/pool.d` 的位置。

查找设置为类似以下内容的行：

```
listen = /var/run/php/php-fpm.sock` 或 `listen = 127.0.0.1:9000
```

如果 PHP FPM 将在 NGINX 的同一主机上运行（如果你不确定，这很可能是一个安全的假设），建议你使用 UNIX 套接字（即 `/var/run/php/php-fpm.sock`）而不是 TCP (`127.0.0.1:9000`) 以获得最佳性能（尽管只要你的 NGINX 和 PHP FPM 配置匹配，两者都可以使用）。

在决定如何连接 NGINX 与 PHP FPM（如有必要，更新本地 PHP FPM 配置并重启 FPM）后，将你的 NGINX 配置的 `upstream php-handler``server` 设置为你的偏好（注意：如果使用 UNIX 套接字，在 NGINX 配置中应添加 `unix:`，但在你的 PHP FPM `www.conf` 中不应添加）。

### 抑制日志消息 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/nginx.html#suppressing-log-messages)

如果你在日志文件中看到无意义的消息，例如 `client denied by server configuration: /var/www/data/htaccesstest.txt` ，请将此部分添加到你的 nginx 配置中以抑制它们：

```
location = /data/htaccesstest.txt {
  allow all;
  log_not_found off;
  access_log off;
}
```



### JavaScript (.js) 或 CSS (.css) 文件未正确提供 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/nginx.html#javascript-js-or-css-css-files-not-served-properly)

自定义 nginx 配置的一个常见问题是 JavaScript（.js）或 CSS（.css）文件无法正确提供，导致这些文件出现 404（文件未找到）错误，并且网页界面损坏。

这可能是由以下原因引起的：

```
location ~* \.(?:css|js)$ {
```



上述块未位于**下方** ：

```
location ~ \.php(?:$|\/) {
```



块。其他自定义配置，如通过 gzip 缓存 JavaScript (.js)或 CSS (.css)文件，也可能导致此类问题。

这个问题另一个可能的原因是 http 块中没有正确包含 mimetypes，如[这里](https://www.nginx.com/resources/wiki/start/topics/examples/full/)所示。

### 上传大于 10 MiB 的文件失败 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/nginx.html#upload-of-files-greater-than-10-mib-fails)

如果你配置 nginx（全局）来阻止所有对（隐藏）点文件的请求，由于 Nextcloud 要求将文件上传到以 `/.file` 结尾的 URL，因此可能无法通过网页上传大于 10 MiB 的文件。

你可能需要将：

```
location ~ /\. {
```



更改为以下内容以重新允许文件上传：

```
location ~ /\.(?!file).* {
```



参见 [nextcloud/server 上的 issue #8802](https://github.com/nextcloud/server/issues/8802) 获取更多信息。

除了上述参数外，其他参数与上传大文件相关（参见 [上传大文件 > 512MB](https://docs.nextcloud.com/server/latest/admin_manual/configuration_files/big_file_upload_configuration.html#uploading-big-files)）。

### 在 access.log、error.log 或 nextcloud.log 中没有任何线索的登录循环 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/nginx.html#login-loop-without-any-clue-in-access-log-error-log-nor-nextcloud-log)

如果在全新安装（Centos 7 配置 nginx）后首次登录时遇到问题，你应该首先检查以下文件：

```
tail /var/www/nextcloud/data/nextcloud.log
tail /var/log/nginx/access.log
tail /var/log/nginx/error.log
```



如果你在访问日志中看到一些正确的请求，但没有登录发生，你应该检查 php 会话和 wsdlcache 目录的访问权限。尝试检查权限并在需要时进行更改：

```
chown nginx:nginx /var/lib/php/session/
chown root:nginx /var/lib/php/wsdlcache/
chown root:nginx /var/lib/php/opcache/
```







# 加固和安全指南 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#hardening-and-security-guidance)

Nextcloud 旨在以安全的默认设置发布，无需管理员进行修改。然而，在某些情况下，当管理员对 Nextcloud 实例有完全控制权时，可以应用一些额外的安全加固。本页面假设您在 Linux 环境下使用 Apache2 运行 Nextcloud 服务器。

注意

如果缺少一些关键的安全相关选项，Nextcloud 将在管理界面中向您发出警告。然而，系统安全仍然由服务器管理员负责审查和维护。

## 密码 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#passwords)

### 访问令牌的存储 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#storage-of-access-tokens)

在成功认证后，Nextcloud 会颁发一个访问令牌，客户端将使用该令牌进行所有未来的 HTTP 请求。该访问令牌唯一标识一个用户，并且不应存储在任何除请求该令牌的客户端之外的系统上。用户密码也以加密形式存储在 Nextcloud 数据库中。密码的加密使用令牌和一个特定于实例的秘密。

访问令牌泄露可能导致安全后果。根据行为者访问的数据不同，风险也不同：

- 只有访问令牌访问权限的行为者可以冒充用户并登录。
- 访问令牌、Nextcloud 配置文件和 Nextcloud 数据库的行为者可以解密数据库中存储的用户密码。

### 密码长度限制 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#limit-on-password-length)

Nextcloud 使用 bcrypt 算法，因此出于安全性和性能考虑，例如当 CPU 需求呈指数级增长时可能会发生拒绝服务，它仅验证密码的前 72 个字符。这适用于你在 Nextcloud 中使用的所有密码：用户密码、链接共享密码以及外部共享密码。

## 操作系统 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#operating-system)



### 给予 PHP 对 `/dev/urandom`[](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#give-php-read-access-to-dev-urandom) 的读取权限

Nextcloud 使用符合 RFC 4086（“安全随机性要求”）的混合器来生成密码学安全的伪随机数。这意味着当生成随机数时，Nextcloud 会从不同来源请求多个随机数，并从中推导出最终的随机数。

随机数生成也会尝试从 `/dev/urandom` 请求随机数，因此强烈建议配置您的设置，以便 PHP 能够从中读取随机数据。

注意

当您的 `open_basedir` 在 `php.ini` 文件中配置时，请确保包含 `/dev/urandom`。

### 启用如 SELinux[](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#enable-hardening-modules-such-as-selinux) 之类的加固模块。

强烈建议尽可能启用 SELinux 等加固模块。有关 SELinux 的更多信息，请参阅 [SELinux 配置 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html)。

## 部署 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#deployment)

### 将数据目录放置在 Web 根目录之外 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#place-data-directory-outside-of-the-web-root)

强烈建议将您的数据目录放置在 Web 根目录之外（即位于 `/var/www` 之外）。在全新安装时这样做最简单。

### 禁用预览图像生成 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#disable-preview-image-generation)

Nextcloud 能够生成常见文件类型（如图像或文本文件）的预览图像。默认情况下，对于我们认为足够安全的某些文件类型，预览生成是启用的。但是，管理员应注意，这些预览是使用用 C 语言编写的 PHP 库生成的，这些库可能容易受到攻击。

对于高安全部署，我们建议通过在 `enable_previews` 中设置 `false` 来禁用预览生成，在 `config.php` 中。作为管理员，您还可以通过修改 `enabledPreviewProviders` 选项开关来管理启用的预览提供者。

### 禁用调试模式 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#disable-debug-mode)

验证你的 `config.php` 中 `debug` 是否为 `false`。默认值为 `false`。 在新安装（或未指定时）中不应启用。在生产环境中不应启用。 在非目标环境或非针对性故障排除情况下。启用时，事情 允许服务器范围的 WebDAV 集合列表。它是用于本地的。 仅在受控环境中开发和使用。



## 使用 HTTPS[](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#use-https)

在不使用加密的 HTTPS 连接使用 Nextcloud 会使您的服务器暴露于中间人（MITM）攻击的风险，并可能导致用户数据和密码被拦截。最佳实践是，强烈建议在生产服务器上始终使用 HTTPS，并且永远不允许未加密的 HTTP。

如何在您的 Web 服务器上设置 HTTPS 取决于您的配置；请查阅您的 HTTP 服务器的文档。以下示例适用于 Apache。

### 将所有未加密流量重定向到 HTTPS[](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#redirect-all-unencrypted-traffic-to-https)

要将所有 HTTP 流量重定向到 HTTPS，管理员建议使用 301 状态码发出永久重定向。在使用 Apache 时，这可以通过在 Apache VirtualHosts 配置中设置如下内容来实现：

```
<VirtualHost *:80>
   ServerName cloud.nextcloud.com
   Redirect permanent / https://cloud.nextcloud.com/
</VirtualHost>
```





### 启用 HTTP 严格传输安全 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#enable-http-strict-transport-security)

虽然将所有流量重定向到 HTTPS 是好的，但它可能无法完全防止中间人攻击。因此，管理员被鼓励设置 HTTP 严格传输安全头部，该头部指示浏览器不允许使用 HTTP 连接到 Nextcloud 实例，并试图防止网站访客绕过无效证书警告。

这可以通过在 Apache VirtualHost 文件中设置以下设置来实现：

```
<VirtualHost *:443>
  ServerName cloud.nextcloud.com
    <IfModule mod_headers.c>
      Header always set Strict-Transport-Security "max-age=15552000; includeSubDomains"
    </IfModule>
 </VirtualHost>
```



警告

我们建议将附加设置 `; preload` 添加到该头部。然后该域名将被添加到一个随所有主要浏览器附带的标准硬编码列表中，并强制这些域名使用 HTTPS。参见 [HSTS 预加载网站了解更多信息 ](https://hstspreload.org/)。由于该列表的策略，您需要一旦确定这是您想要的，就将其添加到上述示例中。 [从该列表中移除域名 ](https://hstspreload.org/#removal) 可能需要几个月的时间才能使其到达所有已安装的浏览器。

此示例配置将使所有子域名仅可通过 HTTPS 访问。如果您有无法通过 HTTPS 访问的子域名，请移除 `includeSubDomains`。

这需要 Apache 中的 `mod_headers` 扩展。

### 正确的 SSL 配置 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#proper-ssl-configuration)

Web 服务器的默认 SSL 配置通常不是最先进的，需要精细调整以获得最佳性能和安全性体验。可用的 SSL 密码和选项完全取决于您的环境，因此无法给出通用的建议。

我们推荐使用 [Mozilla SSL 配置生成器](https://mozilla.github.io/server-side-tls/ssl-config-generator/)来生成适合您环境的配置。您可以使用免费的 [Web TLS 分析器](https://tlsprofiler.danielfett.de/)服务来验证您的配置。如果您的服务器的 TLS 设置与 Mozilla 配置不符，该服务将提供详细的错误信息。另一个用于检查服务器 TLS 配置的有用工具是免费的 [Qualys SSL Labs 测试 ](https://www.ssllabs.com/ssltest/)，它提供有关 TLS 设置的常规信息。

%% 同时确保禁用 HTTP 压缩以减轻 BREACH 攻击。

## 限制管理员操作到特定的 IP 地址范围 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#restrict-admin-actions-to-a-specific-range-of-ip-addresses)

在 `config.php` 中配置 `allowed_admin_ranges`，以将管理员操作限制在可信的 IP 地址范围内。

这可以通过以下类型的设置来实现，通常使用私有 IP 地址范围：

```
'allowed_admin_ranges' => [
  '127.0.0.1/8',
  '192.168.0.0/16',
  'fd00::/8',
],
```



来自这些范围之外 IP 地址的所有请求将无法执行管理操作。

从不受信任的 IP 地址连接的管理员将能够使用 Nextcloud，但所有特定于管理员的操作将被隐藏。

## 为 Nextcloud 使用专用域名 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#use-a-dedicated-domain-for-nextcloud)

建议管理员将 Nextcloud 安装在专用域名（如 cloud.domain.tld）而非 domain.tld，以获得 Same-Origin-Policy 提供的所有好处。

## 确保您的 Nextcloud 实例安装在 DMZ[](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#ensure-that-your-nextcloud-instance-is-installed-in-a-dmz)

由于 Nextcloud 支持联邦文件共享等特性，我们不将服务器端请求伪造（SSRF）视为威胁模型的一部分。实际上，考虑到所有外部存储适配器，这可以被视为一个特性而非漏洞。

这意味着 Nextcloud 实例上的用户可以探测 Nextcloud 网络中其他主机是否可访问。如果您不希望这样，您需要确保 Nextcloud 正确安装在隔离网络中，并设置适当的防火墙规则。

## 由 Web 服务器提供与安全相关的头部 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#serve-security-related-headers-by-the-web-server)

Nextcloud 默认环境下已经提供了基本的安全头。这些包括：

- - `X-Content-Type-Options: nosniff`

    指示某些浏览器不要检测文件的 mimetype。例如，这用于防止浏览器将文本文件解释为 JavaScript。

- - `X-Robots-Tag: noindex, nofollow`

    指示搜索引擎不要索引这些页面，也不要跟随其中的任何链接。

- - `X-Frame-Options: SAMEORIGIN`

    防止将 Nextcloud 实例嵌入到其他域的 iframe 中，以防止点击劫持和其他类似攻击。

- - `Referrer-Policy: no-referrer`

    默认的 no-referrer 策略指示浏览器在向任何来源发送请求时不发送引用信息。

这些标头被硬编码到 Nextcloud 服务器中，无需服务器管理员干预。

为了最佳安全性，管理员应鼓励通过 Web 服务器提供这些基本 HTTP 头，并在响应中强制执行它们。为此，Apache 需要配置以使用 `.htaccess` 文件，并且需要启用以下 Apache 模块：

- mod_headers
- mod_env

管理员可以通过访问由 Web 服务器提供的一个静态资源来验证此安全更改是否处于活动状态，并确认上述提到的安全标头是否已发送。



## 连接到远程服务器 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#connections-to-remote-servers)

某些功能需要 Nextcloud 服务器能够通过 https/443 连接到远程系统。本段落还包含传输到 Nextcloud GmbH 的数据。根据您的服务器配置，可能的连接包括：

- - connectivity.nextcloud.com, www.eff.org, edri.org

    [可选（配置）](https://docs.nextcloud.com/server/latest/admin_manual/configuration_server/config_sample_php_parameters.html#has-internet-connection)用于检查网络连接

- - cloud.nextcloud.com

    用于企业许可证监控提交的数据：订阅密钥，用户数量

- - updates.nextcloud.com

    检查可用的 Nextcloud 服务器更新提交的数据：服务器版本、订阅密钥、安装时间、实例 ID、实例大小

- - apps.nextcloud.com, ltd[1-3].nextcloud.com, garm[1-5].nextcloud.com

    用于检查可用应用及其更新源是 apps.nextcloud.com，ltd 和 garm 服务器只是镜像 apps.json 文件提交的数据：订阅密钥

- - github.com, objects.githubusercontent.com, release-assets.githubusercontent.com

    下载 Nextcloud 标准应用用于下载 Nextcloud 服务器版本

- - push-notifications.nextcloud.com

    向移动客户端发送推送通知提交的数据：唯一设备标识符、公钥、推送令牌

- - pushfeed.nextcloud.com

    可选检查要在 Nextcloud 公告应用中显示的更新

- - lookup.nextcloud.com

    可选用于更新和查询联合共享地址簿提交的数据： *待处理*

- - surveyserver.nextcloud.com

    可选如果管理员同意共享匿名服务器数据提交的数据：统计数据。有关[详细字段列表 ](https://github.com/nextcloud/survey_client)，请参阅此处

- 任何通过联盟共享连接的远程 Nextcloud 服务器

- 从应用商店下载应用时，可能会访问其他域名，这取决于应用开发者选择在哪里托管发布版本。不过，对于所有官方的 Nextcloud 应用来说，情况并非如此，因为它们托管在 Github 上。

## 设置 fail2ban[](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#setup-fail2ban)

将您的服务器暴露在互联网上，不可避免地会导致暴露在互联网公开端口上的服务受到暴力破解登录尝试的攻击。

本指南将启用在操作系统级别阻止源 IP 地址的功能，因此 Web 服务器、PHP 和数据库都不需要处理这些不必要的数据流量。

### Nextcloud 前置条件 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#nextcloud-prerequisites)

Nextcloud 在 `nextcloud.log` 中以日志级别 `2` 记录失败的登录尝试，因此您需要在 `config.php` 中定义一个 `2` 或更低的 `loglevel`。

确保您的 `nextcloud.log` 可被您的 Web 服务器用户写入，可能通过在 `config.php` 中定义正确的 `logfilemode` 来实现。

执行一次不良登录尝试，并检查是否确实被记录到 `nextcloud.log` 中。

请注意，`audit.log`（如果已启用）目前仅记录成功的登录，不能使用。

### Fail2ban 介绍 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#fail2ban-introduction)

Fail2ban 是一个使用 iptables 自动从不断尝试认证但失败的 IP 地址上断开连接的服务，断开连接的时间为预定义的时间段。

要设置 Fail2ban，您首先需要在服务器上下载并安装它。多个发行版的下载链接可以在 [Fail2ban 下载页面 ](https://www.fail2ban.org/wiki/index.php/Downloads) 找到。它通常可以从大多数发行版的包管理器中获取（例如 `apt-get`）。

fail2ban 的标准配置路径是 `/etc/fail2ban`。

### 设置 Nextcloud 的过滤器及隔离区 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#setup-a-filter-and-a-jail-for-nextcloud)

一个过滤器定义正则规则，用于识别用户在 Nextcloud 的用户界面、WebDAV 上未能通过身份验证，或使用不受信任的域访问服务器的情况。

在 `/etc/fail2ban/filter.d` 中创建一个名为 `nextcloud.conf` 的文件，内容如下：

```
[Definition]
_groupsre = (?:(?:,?\s*"\w+":(?:"[^"]+"|\w+))*)
failregex = ^\{%(_groupsre)s,?\s*"remoteAddr":"<HOST>"%(_groupsre)s,?\s*"message":"Login failed:
            ^\{%(_groupsre)s,?\s*"remoteAddr":"<HOST>"%(_groupsre)s,?\s*"message":"Two-factor challenge failed:
            ^\{%(_groupsre)s,?\s*"remoteAddr":"<HOST>"%(_groupsre)s,?\s*"message":"Trusted domain error.
datepattern = ,?\s*"time"\s*:\s*"%%Y-%%m-%%d[T ]%%H:%%M:%%S(%%z)?"
```



监禁文件定义了如何处理 Nextcloud 过滤器发现的失败认证尝试。

在 `/etc/fail2ban/jail.d` 中创建一个名为 `nextcloud.local` 的文件，内容如下：

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



确保将 `logpath` 替换为您的安装的 `nextcloud.log` 位置。如果您使用的是除 `80` 和 `443` 以外的 Web 服务器端口，您也应该替换这些端口。`bantime` 和 `findtime` 以秒为单位定义。

重启 fail2ban 服务。您可以通过运行以下命令检查 Nextcloud 监狱的状态：

```
fail2ban-client status nextcloud
```



如果您需要解除某些 IP 地址的封禁（例如本例中的 `1.2.3.4`），可以通过执行以下命令来完成：

```
fail2ban-client unban 1.2.3.4
```



在某些情况下，您可能希望使用 fail2ban 的 `recidive` 功能，更永久地禁止某些反复生成恶意登录尝试（或其他攻击）的 IP 地址。







# 服务器调优 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#server-tuning)

## 使用 cron 执行后台任务 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#using-cron-to-perform-background-jobs)

参见[后台任务](https://docs.nextcloud.com/server/latest/admin_manual/configuration_server/background_jobs_configuration.html)了解描述和好处。

## 降低系统负载 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#reducing-system-load)

高系统负载会减慢 Nextcloud 的速度，还可能导致其他不希望出现的副作用。为了降低负载，您应该首先识别问题的来源。htop、iotop、[netdata](https://my-netdata.io/) 或 [glances](https://nicolargo.github.io/glances/) 等工具可以帮助您识别导致系统变慢的进程或驱动器。 首先，确保您已经安装并分配了足够的 RAM。最小化 swap 尽可能多地使用，因为过多的交换会严重降低性能。 如果你在虚拟机中运行数据库，请为数据库存储使用专用块设备 与其将其存储在虚拟机磁盘映像文件内部，以减少由 多层抽象层。



## 日志级别 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#log-levels)

检查你的 `loglevel` 在 `config.php` 文件中。新安装的默认日志级别设置为 `2` (WARN)。有时在故障排除后，这个参数可能会无意中保持在 DEBUG 级别 (`0`)。在一些较旧的安装中，这个参数也可能不是默认值。当你需要诊断问题时，使用 `0` (DEBUG)，然后重置你的日志级别到一个不那么详细的级别。DEBUG 会输出大量信息，可能会影响你的服务器性能。

## 调试模式 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#debug-mode)

验证你的 `debug` 在 `config.php` 文件中设置为 `false`。新安装的默认值是 `false`（或未指定时）。虽然与 DEBUG 日志级别类似，但此选项还会禁用各种优化（以方便调试），并在浏览器级别和服务器端生成额外的调试输出。除隔离故障排除期间外，不应在生产环境中启用它。

## 缓存 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#id1)

缓存通过将数据、代码和其他对象存储在内存中来提高性能。内存缓存默认情况下未启用，因为它需要可选扩展（如 APCu）和/或系统组件（例如 Redis）。虽然这些附加组件通常不难以安装和激活——至少在单服务器部署中——但在 Nextcloud 中启用它们之前，你必须先安装它们。参见 :doc:../configuration_server/caching_configuration 获取指导。

## 压缩 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#compression)

在您的 Web 服务器上为 JavaScript、CSS 和 SVG 文件启用压缩可以提高性能，因为传输给客户端的数据更少。

## 替换 SQLite[](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#replacing-sqlite)

SQLite 适用于某些使用场景，但使用 MariaDB、MySQL 或 PostgreSQL 与 Nextcloud 配合使用可能更有益。

如果你在安装时没有选择数据库，默认会使用 SQLite，因为它不需要任何外部组件。

然而，通常推荐为 Nextcloud 使用 MySQL/MariaDB 或 PostgreSQL，因为 [高度并发应用程序（如 Nextcloud）中 SQLite 的性能限制 ](https://www.sqlite.org/whentouse.html)。

如果您的安装已经运行在 SQLite，您可以使用提供的步骤将其转换为 MySQL 或 MariaDB [转换数据库类型 ](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/db_conversion.html)。

参见[数据库配置](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/linux_database_configuration.html)部分，了解如何为 MySQL 或 MariaDB 配置 Nextcloud。

## 调整数据库 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#tuning-your-database)

数据库并非即插即用。它们不仅需要基本的配置以兼容 Nextcloud，还需要在部署环境中进行调优。这种调优应根据您的硬件、存储、使用模式、底层操作系统、优先级和其他因素进行。

欲了解更多详情和帮助调整数据库：

- [MariaDB – 优化与调优](https://mariadb.com/docs/server/ha-and-performance/optimization-and-tuning/)
- [PostgreSQL – 资源消耗](https://www.postgresql.org/docs/17/runtime-config-resource.html)
- [PostgreSQL – 调优您的 PostgreSQL 服务器](https://wiki.postgresql.org/wiki/Tuning_Your_PostgreSQL_Server)

## 使用基于 Redis 的交易式文件锁定 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#using-redis-based-transactional-file-locking)

事务性文件锁定使用数据库作为默认后端。这将 增加您数据库的负载。参见 [事务性文件锁定](https://docs.nextcloud.com/server/latest/admin_manual/configuration_files/files_locking_transactional.html)部分，了解如何配置 Nextcloud 使用基于 Redis 的事务性文件锁定。

## TLS / 加密应用 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#tls-encryption-app)

TLS（HTTPS）和文件加密/解密可以卸载到处理器的 AES-NI 扩展。这既能加快这些操作，又能降低处理开销。这需要具有 [AES-NI 指令集](https://wikipedia.org/wiki/AES_instruction_set)的处理器。

以下是一些检查您的 CPU/环境是否支持 AES-NI 扩展的示例：

- 对于每个存在的 CPU 核心：`grep flags /proc/cpuinfo`，或者对所有核心进行汇总： `grep -m 1 '^flags' /proc/cpuinfo` . 如果结果包含 `aes`，则表示扩展已安装。
- 对于英特尔处理器，您可以在英特尔 ARK 数据库中搜索，以检查您的 CPU 是否支持 AES-NI。使用[英特尔处理器功能过滤器 ](https://ark.intel.com/MySearch.aspx?AESTech=true)，按“AES 新指令”进行筛选。
- 对于 openssl 版本 >= 1.0.1 的版本，AES-NI 无法通过引擎工作，并且不会在 `openssl engine` 命令中显示。它默认在支持的硬件上处于激活状态。您可以通过 `openssl version -a` 命令检查 OpenSSL 版本。
- 如果您的处理器支持 AES-NI，但通过 `grep` 或 `coreinfo` 命令无法显示，可能是 BIOS 中已禁用。请检查您的 BIOS 设置。
- 如果您的环境是虚拟化的，请检查虚拟化供应商是否提供支持。

## 启用 HTTP/2 以实现更快的加载 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#enable-http-2-for-faster-loading)

与使用多个请求的 HTTP 相比，HTTP/2 具有[巨大的速度提升 ](https://www.troyhunt.com/i-wanna-go-fast-https-massive-speed-advantage/)。大多数浏览器已经支持通过 TLS（HTTPS）的 HTTP/2。

## 调整 PHP-FPM[](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#tune-php-fpm)

PHP-FPM 的默认配置非常保守。你可能会注意到网页界面的加载时间过长，甚至同步问题。每个并发请求都由一个单独的 PHP-FPM 进程处理，因此即使是小型安装，你也应该允许更多进程并行运行以处理请求。

[这个链接 ](https://spot13.com/pmcalculator/) 可以帮助你计算系统的最佳值。

## 启用 PHP OPcache[](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#enable-php-opcache)

OPcache 通过缓存预编译的字节码来提高 PHP 应用的性能。

### 重新验证 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#revalidation)

PHP 中的 OPcache 重新验证功能处理存储在磁盘上的 PHP 应用程序代码的更改。代码更改发生在以下情况：

- Nextcloud 或 Nextcloud 应用升级
- 进行配置更改（例如，当修改 `config.php` 时）

Nextcloud 在需要时尽可能内部处理缓存重新验证。然而，这并非万无一失。在默认的 PHP 环境中，重新验证是启用的，并且缓存的脚本每 `2` 秒就会在磁盘上检查一次变化。在许多环境中，这些默认值是合理的，可能永远不需要更改。

然而，重新验证的频率可以调整，并且*可能*会提升性能。我们在此不提供关于重新验证适当值的建议（除了 PHP 默认值）。

危险

增加重新验证之间的时间（或完全禁用它）意味着脚本更改，包括 `config.php`，将需要更长时间才能生效（如果完全禁用重新验证，可能永远无法生效）。增加间隔还会增加服务器和应用程序升级的临时问题的风险，并防止维护模式的正确切换。

警告

如果你调整这些参数，在做出配置更改或执行升级后，你更有可能需要重启/重新加载你的 Web 服务器（`mod_php`）或 PHP-FPM。如果你忘记这样做，你可能会因为磁盘上的内容与内存中的内容不匹配而出现异常行为。这些看起来像是错误，但只要重启/重新加载 `mod_php` / fpm，它们就会消失。

要更改默认值从 `2` 并检查磁盘上的更改最多每 `60` 秒，将以下设置添加到你的 `php.ini` 文件中：

```
opcache.revalidate_freq = 60
```



或者，您可以完全禁用重新验证：

```
opcache.validate_timestamps = 0
```



任何服务器或应用升级，或对 `config.php` 的更改，随后将需要重启 PHP（或以其他方式手动清除缓存或使此特定脚本失效）。

警告

升级 Nextcloud 或 Nextcloud 应用后，请不要在重启 mod_php/fpm 之前报告任何错误或异常行为（以确认问题不是由本地重新验证配置引起的）。

### 尺寸 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#sizing)

如果任何 OPcache 的大小限制超过其分配大小的 90%，管理面板将显示相关警告并建议进行更改。

更多详情，请查看 [官方 PHP 文档 ](https://php.net/manual/en/opcache.configuration.php)。要监控 OPcache 的使用情况并清除单个或所有缓存条目，您可以使用 [opcache-gui](https://github.com/amnuts/opcache-gui)。

### 评论 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#comments)

Nextcloud 严格要求在 opcode 中保留代码注释，这是默认设置。如果您的 PHP 设置已更改，请确保在您的 `php.ini` 中设置以下内容：

```
opcache.save_comments = 1
```



### JIT[](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#jit)

PHP 自带一个 JIT 编译器，可以在 x86 平台上启用，以提升任何 CPU 密集型应用的性能。要在所有优化下启用跟踪 JIT，请向你的 `php.ini` 中添加：

```
opcache.jit = 1255
opcache.jit_buffer_size = 8M
```



注意

大多数 Nextcloud 实例使用的 JIT 缓冲区大小不到 2 MiB，因此 8 MiB 通常足够。然而，OPcache 的整体使用量会以更大的幅度增加。在某些情况下，PHP 参数 `opcache.memory_consumption` 可能需要提高。JIT 缓冲区的使用情况可以通过 [opcache-gui](https://github.com/amnuts/opcache-gui) 同样。

## 预览 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#previews)

可以使用外部微服务来加速预览生成： [Imaginary](https://github.com/h2non/imaginary)。

警告

Imaginary 目前与服务器端加密不兼容。参见 https://github.com/nextcloud/server/issues/34262

我们强烈推荐使用我们的自定义 Docker 镜像，它比官方镜像更新。您可以在 https://ghcr.io/nextcloud-releases/aio-imaginary 找到该镜像。运行时，通过向 docker run 命令（或 Compose 等效命令）添加 -p <port>:9000 来映射一个端口，例如：

```
docker run -d -p 9000:9000 --name nextcloud_imaginary --restart always ghcr.io/nextcloud-releases/aio-imaginary:latest
```



确保该服务只能从您的内部服务器访问。然后，通过编辑您的 `config.php` 文件来配置 Nextcloud 使用 Imaginary：

```
'enabledPreviewProviders' => [
    'OC\Preview\TXT',
    'OC\Preview\MarkDown',
    'OC\Preview\OpenDocument',
    'OC\Preview\Krita',
    'OC\Preview\Imaginary',
],
'preview_imaginary_url' => 'http://<url of imaginary>:<port>',
```



警告

确保使用 `-return-size` 命令行参数启动 Imaginary。否则，性能会有轻微影响。该标志需要 Imaginary 的较新版本（版本号高于 v1.2.4）。此外，请通过 `--cap-add=sys_nice` 或（对于 Compose） `cap_add: - SYS_NICE` 添加 `SYS_NICE` 能力，因为 Imaginary 生成 HEIC 预览需要该能力。

注意

对于大型实例，请遵循 [Imaginary 的扩展性建议 ](https://github.com/h2non/imaginary#scalability)。

### 设置 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#settings)

要为 Imaginary 设置预览格式（默认为 jpeg），请将以下内容添加到您的 `config.php`：

```
'preview_format' => 'webp',
```



要为 Imaginary 设置 API 密钥：

```
'preview_imaginary_key' => 'secret',
```



预览图片的默认 WebP 质量设置为“80”。使用以下方式更改：

```
occ config:app:set preview webp_quality --value="30"
```







# Ubuntu 22.04 LTS 上的示例安装 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_ubuntu.html#example-installation-on-ubuntu-22-04-lts)

您可以通过在终端中执行以下命令，使用 .deb 软件包来安装典型 Nextcloud 安装所需的和推荐的模块，使用 Apache 和 MariaDB：

```
sudo apt update && sudo apt upgrade
sudo apt install apache2 mariadb-server libapache2-mod-php php-gd php-mysql \
php-curl php-mbstring php-intl php-gmp php-xml php-imagick php-zip
```



- 这会安装 Nextcloud 核心系统的软件包。如果您计划运行额外的应用程序，请记住它们可能需要额外的软件包。有关详细信息，请参阅 [手动安装的先决条件 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#prerequisites-for-manual-installation)。

现在您需要使用 MySQL 命令行界面创建一个数据库用户和数据库本身。当您第一次登录时，Nextcloud 将创建数据库表。

要启动 MySQL 命令行模式，请使用以下命令：

```
sudo mysql
```



然后会出现一个 **MariaDB [root]>** 提示符。现在输入以下行，将 `username` 和 `password` 替换为适当的值，并按 Enter 键确认：

```
CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';
CREATE DATABASE IF NOT EXISTS nextcloud CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;
GRANT ALL PRIVILEGES ON nextcloud.* TO 'username'@'localhost';
FLUSH PRIVILEGES;
```



要退出提示符，请输入：

```
quit;
```



现在下载最新版本的 Nextcloud 归档文件：

- 前往 [Nextcloud 安装页面 ](https://nextcloud.com/install)。

- 前往**下载服务器 > 社区项目**并下载 tar.bz2 或.zip 归档文件。

- 这会下载一个名为 nextcloud-x.y.z.tar.bz2 或 nextcloud-x.y.z.zip 的文件（其中 x.y.z 是版本号）。

- 下载其对应的校验和文件，例如 nextcloud-x.y.z.tar.bz2.md5 或 nextcloud-x.y.z.tar.bz2.sha256。

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

  

- 现在您可以解压存档内容。运行适用于您存档类型的相应解压命令：

  ```
  tar -xjvf nextcloud-x.y.z.tar.bz2
  unzip nextcloud-x.y.z.zip
  ```

  

- 这将解压为一个单一的 `nextcloud` 目录。将 Nextcloud 目录复制到其最终目的地。当您运行 Apache HTTP 服务器时，您可以安全地将 Nextcloud 安装在 Apache 文档根目录下：

  ```
  sudo cp -r nextcloud /var/www
  ```

  

- 最后，将您的 Nextcloud 目录的所有权更改为您的 HTTP 用户：

  ```
  sudo chown -R www-data:www-data /var/www/nextcloud
  ```

  

在其他 HTTP 服务器上，建议将 Nextcloud 安装在文档根目录之外。

## 下一步 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_ubuntu.html#next-steps)

安装完先决条件并解压 nextcloud 目录后，您 应遵循 Apache 配置说明： [Apache Web 服务器配置 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#apache-configuration-label). 安装 Apache 后，你可以选择按照 [Linux 上的安装](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html)指南（来自[伪静态 URL](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#pretty-urls-label)）进行操作直到 [其他 Web 服务器](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#other-http-servers-label)







# 《在 CentOS 8 上的示例安装 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_centos.html#example-installation-on-centos-8)》

在这个安装教程中，我们将部署 CentOS 8、PHP 7.4、MariaDB、Redis 作为 memcache 以及运行在 Apache 上的 Nextcloud。

首先安装 CentOS 8 的精简版。这应该能提供一个足够成功的 Nextcloud 实例的运行平台。

首先安装一些在安装过程中会用到，同时在日常使用中也会很有用的依赖项：

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



在 `/etc/httpd/conf.d/nextcloud.conf` 中创建一个虚拟主机，并向其中添加以下内容：

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



有关详细信息，请参阅 [Apache Web 服务器配置 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html#apache-configuration-label)。

确保 Apache 网页服务已启用并启动：

```
systemctl enable httpd.service
systemctl start httpd.service
```



## PHP[](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_centos.html#php)

注意

CentOS 8 不自带 redis 和 imagick 的 PHP 扩展包。这些扩展包可以通过 pecl 安装。除了官方的 PHP 包，还有第三方仓库可用，位于 `https://rpms.remirepo.net`。使用 remirepo，你也可以安装最新的 PHP 版本，而不是标准提供的版本。

### 设置 remirepo 与 PHP 8.2[](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_centos.html#setting-up-remirepo-with-php-8-2)

更多详情请参见 `https://blog.remirepo.net/pages/Config-en`

安装 Remi 仓库配置包的命令：

```
dnf install https://rpms.remirepo.net/enterprise/remi-release-8.rpm
```



安装 yum-utils 软件的命令（用于 yum-config-manager 命令）：

```
dnf install yum-utils
```



你需要一个单一版本，这意味着替换来自发行版的基础软件包。软件包与基础仓库同名，即 php-*. 一些常见依赖项在 remi-safe 仓库中可用，该仓库默认已启用。

你需要为 8.2 启用模块流：

```
dnf module reset php
dnf module install php:remi-8.2
dnf update
```



### 安装 PHP 和所需模块 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_centos.html#installing-php-and-the-required-modules)

接下来，安装此安装所需的 PHP 模块。请记住，由于这是一个有限的 basic 安装，我们只安装必要的模块，而不是所有模块。如果您正在进行更完整的安装，请参考源安装文档中的 PHP 模块列表，[Linux 上安装 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/source_installation.html)：

```
dnf install -y php php-cli php-gd php-mbstring php-intl php-pecl-apcu\
     php-mysqlnd php-opcache php-json php-zip
```



### 安装可选模块 redis/imagick[](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_centos.html#installing-optional-modules-redis-imagick)

```
dnf install -y php-redis php-imagick
```



## 数据库 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_centos.html#database)

如前所述，我们将使用 MySQL/MariaDB 作为我们的数据库：

```
dnf install -y mariadb mariadb-server
```



确保数据库服务在启动时启用：

```
systemctl enable mariadb.service
systemctl start mariadb.service
```



提高 MariaDB 的安全性：

```
mysql_secure_installation
```



完成这些操作后，请确保您创建一个带有用户名和密码的数据库，以便 Nextcloud 可以访问它。有关数据库设置和配置的更多详细信息，请参阅 [数据库配置 ](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/linux_database_configuration.html)文档。

## Redis[](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_centos.html#redis)

```
dnf install -y redis
systemctl enable redis.service
systemctl start redis.service
```



## 安装 Nextcloud[](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_centos.html#installing-nextcloud)

快完成了，继续努力，你做得很好！

现在下载最新版本的 Nextcloud 压缩包：

- 前往 [Nextcloud 下载页面 ](https://nextcloud.com/install)。

- 前往 **下载 Nextcloud 服务器 > 下载 > 服务器所有者的存档文件** 并下载 tar.bz2 或 .zip 存档。

- 这将下载一个名为 nextcloud-x.y.z.tar.bz2 或 nextcloud-x.y.z.zip 的文件（其中 x.y.z 是版本号）。

- 下载其对应的校验和文件，例如 nextcloud-x.y.z.tar.bz2.md5 或 nextcloud-x.y.z.tar.bz2.sha256。

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

  

为了演示过程，我们下载了最新版本的 Nextcloud，以压缩文件的形式，并使用上述命令确认了下载，现在我们将解压它：

```
unzip nextcloud-*.zip
```



将内容复制到您的 Web 服务器的根目录。在我们的案例中，我们使用的是 apache，所以将是 `/var/www/html/`：

```
cp -R nextcloud/ /var/www/html/
```



在安装过程中，不会自动创建数据文件夹，因此我们将手动创建一个以帮助安装向导：

```
mkdir /var/www/html/nextcloud/data
```



确保 apache 对整个 nextcloud 文件夹有读写权限：

```
chown -R apache:apache /var/www/html/nextcloud
```



重启 apache：

```
systemctl restart httpd.service
```



为 apache 创建防火墙规则：

```
firewall-cmd --zone=public --add-service=http --permanent
firewall-cmd --reload
```



## SELinux[](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_centos.html#selinux)

同样，关于 SELinux 的详细说明可以在 [SELinux 配置](https://docs.nextcloud.com/server/latest/admin_manual/installation/selinux_configuration.html)中找到，如果你在 Enforcing 模式下使用 SELinux，请运行该页面建议的命令。以下命令仅适用于本教程：

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



如果你需要更多 SELinux 配置，请参考上述链接，然后返回本教程。

完成 SELinux 后，请前往 `http://your.server.com/nextcloud` 并按照 [安装向导 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/installation_wizard.html)中的步骤操作，它会详细解释如何通过您的网络浏览器以管理员用户身份完成安装的最后部分。

注意

如果你使用这个教程，并且在安装后浏览器中看到关于 `OPcache` 未启用或配置不正确的警告，你需要按照 `/etc/opt/rh/rh-php74/php.d/10-opcache.ini` 中的建议进行修改，以消除这些错误。这些警告将显示在管理页面下的基本设置中。

因为我们使用了 `Redis` 作为 memcache，在运行前面提到的在线安装向导时， `/var/www/html/nextcloud/config/config.php` 中将自动生成类似的配置文件。

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



请记住，本教程仅适用于在 CentOS 8 上安装 Nextcloud 的基本设置，使用 PHP 7.4。如果您打算使用 LDAP 或单点登录等更多功能，您还需要额外的 PHP 模块以及额外的配置。因此，请访问 Admin 手册的其余部分，[ 简介 ](https://docs.nextcloud.com/server/latest/admin_manual/index.html)，以获取如何完成这些操作的详细说明。







# OpenBSD 上的示例安装 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_openbsd.html#example-installation-on-openbsd)

警告

Nextcloud 没有官方的 OpenBSD 或其他 BSD 的支持

在这个安装教程中，我们将要在 OpenBSD 的极简系统上部署 Nextcloud，使用我们自己的 httpd(8)、PHP、PostgreSQL 和 redis（对于-stable 或-current 版本步骤相同）。

从已安装的 OpenBSD 系统开始，你只需要做：

```
# pkg_add nextcloud
```



额外的软件包：

```
# pkg_add postgresql-server redis pecl82-redis php-pdo_pgsql
```



这将处理您的依赖关系，并提供选择您想要哪个 PHP 版本的功能。

## HTTPD(8)[](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_openbsd.html#httpd-8)

在 `/etc/httpd.conf` 中创建一个虚拟主机，并向其中添加以下内容：

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



确保 httpd(8)已启用并启动：

```
# rcctl enable httpd
# rcctl start httpd
```



## PHP[](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_openbsd.html#php)

假设你使用的是 OpenBSD -current（或>= 6.8-stable），你可以使用 PHP 8.2，因此我将保持这个版本，但其他版本的概念是相同的。

自从你用 pkg_add 安装 Nextcloud 以来，PHP 软件包就已经可用，你只需要稍微调整一下 php.ini。

建议向其中添加 opcache：

```
[opcache]
opcache.enable=1
opcache.memory_consumption=512
opcache.interned_strings_buffer=8
opcache.max_accelerated_files=10000
opcache.revalidate_freq=1
opcache.save_comments=1
```



并且增加一些限制：

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

如前所述，我们将使用 PostgreSQL 作为数据库，并且我们已经安装了它，现在我们需要初始化：

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



您可以参考 `/usr/local/share/doc/pkg-readmes/postgresql-server` 的 README 来创建用户和权限。

## Redis[](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_openbsd.html#redis)

我们之前安装了 redis，需要启用它并启动它，同时还要将其添加到 Nextcloud 配置中：

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



## 计划任务 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_openbsd.html#cron-job)

我们需要添加 Nextcloud 的计划任务来执行一些任务，可以在计划任务中添加此条目：

```
*/5 * * * * /usr/bin/ftp -Vo - https://domain.tld/cron.php >/dev/null
```



## 根目录 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_openbsd.html#chroot)

由于在 OpenBSD 中 httpd(8)默认使用 chroot(8)工作，我们需要确保相关文件位于/var/www 的 jail 中：

```
# mkdir -p /var/www/etc/ssl
# install -m 444 -o root -g bin /etc/ssl/cert.pem /etc/ssl/openssl.cnf \
        /var/www/etc/ssl/
# cp /etc/resolv.conf /var/www/etc
```



## Nextcloud 最后步骤 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_openbsd.html#nextcloud-final-steps)

剩余的安装步骤在基于网络的安装向导中完成。

要激活此向导，请在安装的配置文件夹中创建一个名为 CAN_INSTALL 的文件：

> \# touch /var/www/nextcloud/config/CAN_INSTALL

使用浏览器导航到安装的 URL：

> [https://domain.tld](https://domain.tld/)

现在您只需按照步骤操作，输入您的数据库名称、usr 和密码即可。

请注意，您可以运行-current 来升级 Nextcloud：

```
# pkg_add -u -Dsnap
```



以及在-stable 上：

```
# pkg_add -u
```



然后你只需按照浏览器中的步骤操作即可。

## 注意 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/example_openbsd.html#note)

请始终阅读来自 OpenBSD 软件包的 READMES：

```
/usr/local/share/doc/pkg-readmes/
```



所有这些信息以及更多信息都在那里为您可用。







# 卸载 [](https://docs.nextcloud.com/server/latest/admin_manual/installation/uninstallation.html#uninstallation)

应用程序存储在服务器目录中，并与数据库协同工作以存储文件及其共享的元数据（EFSS 功能）。

由于 Nextcloud 在操作模式或操作平台方面提供了高度的灵活性，因此没有通用的卸载说明；例如抽象容器、虚拟机或“裸金属”，即直接在一台或多台服务器上安装。

因此，在卸载过程中，了解 Nextcloud 应用程序的安装位置以及相应数据的存储位置非常重要。

- 应用程序目录（安装前创建）
- 用户文件存储（在应用程序目录内配置或外部配置）
- 数据库中的元数据存储（使用 SQLite 时位于应用程序目录内，或位于同一服务器或另一服务器外部）
- 通过 Redis 服务器或类似服务进行缓存（如果使用）

在卸载过程中，必须决定是否备份文件存储，或者是否也应删除数据。此外，根据部署场景，必须完全取消分配相应的服务器，或者删除应用程序目录，以及数据库模式和 Redis 条目。如果使用专用容器或虚拟机，则必须取消分配这些容器或虚拟机，并且 Nextcloud 应用程序也必须取消分配。

要卸载，您可以从配置目录中的 `config` 读取值。检查：

- 源代码（手动安装，通常在 `/var/www` 或 `/opt/nextcloud`）：在所有服务器上删除该目录
- 数据库（相关配置键：`dbtype`、`dbhost`）：在所有数据库服务器上删除相应的数据库（你可能需要先备份）
- 缓存（相关配置键：`memcache.*`）：如果持久化，从所有缓存服务器上删除相应的数据库或键
- 数据（相关配置键：`datadirectory`）：在所有服务器上删除该目录（你可能需要事先创建备份）。Nextcloud 有选项将数据存储在不同的位置。同时检查外部存储和对象存储
- 日志（相关配置键：`logfile`、`logfile_audit`）：通常位于数据目录中，但也可能位于其他位置，如 `/var/log/`





# 数据库配置 [](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/index.html#database-configuration)

- 转换数据库类型
  - [运行转换](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/db_conversion.html#run-the-conversion)
  - [不可转换的表](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/db_conversion.html#inconvertible-tables)
- 数据库配置
  - [要求](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/linux_database_configuration.html#requirements)
  - [参数](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/linux_database_configuration.html#parameters)
  - [故障排除](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/linux_database_configuration.html#troubleshooting)
- [启用 MySQL 4 字节支持](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/mysql_4byte_support.html)
- [BigInt (64 位) 标识符](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/bigint_identifiers.html)
- [复制](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/replication.html)
- 数据库拆分
  - [初始拆分](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/splitting.html#initial-splitting)
  - [更新中的迁移](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/splitting.html#migrations-on-updates)





# 转换数据库类型 [](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/db_conversion.html#converting-database-type)

您可以使用 Nextcloud 命令行工具将 SQLite 数据库转换为性能更好的 MySQL、MariaDB 或 PostgreSQL 数据库。SQLite 适用于测试和简单的单用户 Nextcloud 服务器，但不适用于多用户生产服务器。

## 运行转换 [](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/db_conversion.html#run-the-conversion)

转换包括两个步骤：

1. 建立目标数据库（包括其凭证）
2. 触发转换工具，将现有数据库的内容迁移到目标数据库

### 建立目标数据库 [](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/db_conversion.html#establishing-the-target-database)

首先，按照您选择的目标数据库类型的手动数据库配置说明，创建目标（新）数据库（及其相关用户名和密码）：

- [配置 MySQL 或 MariaDB 数据库](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/linux_database_configuration.html#db-config-mysql-label)
- [PostgreSQL 数据库](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/linux_database_configuration.html#db-config-postgresql-label)

由于上述数据库说明使用新创建的数据库名称 `nextcloud`，为了保持一致性，我们在这里也将使用该名称，但您可以根据自己的喜好使用任何数据库名称。使用您在创建新数据库时指定的数据库名称、数据库用户名和数据库密码。

### 触发转换 [](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/db_conversion.html#triggering-the-conversion)

`occ db:convert-type` 命令处理所有转换任务。以下是可用的参数：

```
sudo -E -u www-data php occ db:convert-type [options] type username hostname database
```



`type` 应为目标数据库类型。这里提供的值与 `config.php``dbtype` 参数中的值相同。它应该是以下之一：`mysql` 用于 MariaDB/MySQL， `pgsql` 用于 PostgreSQL，或 `oci` 用于 Oracle。

选项：

- `--port="3306"` 数据库端口（可选）[默认为“3306”]
- `--password="mysql_user_password"` 新数据库的密码。如果省略，工具将提示您输入（可选）
- `--clear-schema` 清理模式（可选）
- `--all-apps` 默认情况下，会转换启用应用的表，使用该选项可以同时转换已停用应用的表（可选）
- `-n, --no-interaction` 不询问任何交互式问题

注意

转换工具会在您配置的应用文件夹中搜索应用，并使用应用中的模式（表）定义来创建新表。对于已移除应用但仍存在的任何表，将不会被转换（即使使用选项 `--all-apps`）。

让我们将现有的（可运行的）sqlite3 安装转换为基于 MariaDB/MySQL：

```
sudo -E -u www-data php occ db:convert-type --password="<password>" --port="3306" --all-apps mysql <username> <hostname> nextcloud
```



注意

在这个示例中指定端口是不必要的，因为 `3306` 已经是默认端口。我们这样做只是为了演示目的和完整性，以防读者在目标数据库服务器上使用非标准端口。

转换成功后，转换工具将自动在您的 Nextcloud 配置 `config.php` 中配置新数据库。

如果你要转换为 MySQL/MariaDB 数据库，还需要在你的 `config.php` 中将 `mysql.utf8mb4` 参数设置为 true：

```
sudo -E -u www-data php occ config:system:set mysql.utf8mb4 --type boolean --value="true"
```



如果你愿意，可以通过查找你的 `config.php` 中的 `db*` 参数来查看所做的更改（你也可以在转换之前使用此命令来比较配置前后）：

```
grep db config/config.php
```



## 不可转换的表 [](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/db_conversion.html#inconvertible-tables)

如果你更新了你的 Nextcloud 实例，可能会有一些不再使用的旧表的残留。更新程序会告诉你哪些是这些表。

```
The following tables will not be converted:
oc_permissions
...
```



你可以忽略这些表。以下是已知的老表列表：

- oc_calendar_calendars
- oc_calendar_objects
- oc_calendar_share_calendar
- oc_calendar_share_event
- oc_fscache
- oc_log
- oc_media_albums
- oc_media_artists
- oc_media_sessions
- oc_media_songs
- oc_media_users
- oc_permissions
- oc_privatedata - 这个表后来被应用 privatedata (https://apps.nextcloud.com/apps/privatedata) 再次添加，如果该应用未启用，可以安全地删除
- oc_queuedtasks
- oc_sharing







# 数据库配置 [](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/linux_database_configuration.html#database-configuration)

Nextcloud 需要一个用于存储管理数据的数据库。目前支持的数据库有：

- [MySQL](https://www.mysql.com/) / [MariaDB](https://mariadb.org/) 
- [PostgreSQL](https://www.postgresql.org/)
- [Oracle](http://www.oracle.com/)

推荐使用 MySQL 或 MariaDB 数据库引擎。

提示

并非所有支持的数据库版本都推荐使用。请查阅 Nextcloud 的[系统要求 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html)。 在确定特定版本之前。

## 需求 [](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/linux_database_configuration.html#requirements)

- 决定您是否希望使用 MySQL / MariaDB、PostgreSQL 或 Oracle 作为您的数据库
- 通过查看 Nextcloud [系统要求 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/system_requirements.html)选择推荐的数据库版本
- 在部署 Nextcloud 服务器之前，安装并设置所选的数据库服务器软件（以及首选版本）

注意

配置第三方数据库的步骤超出了本文档的范围。请参考您选择的特定数据库的文档以获取说明。



### 数据库“READ COMMITTED”事务隔离级别 [](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/linux_database_configuration.html#database-read-committed-transaction-isolation-level)

如上所述，Nextcloud 使用的是 `TRANSACTION_READ_COMMITTED` 事务隔离级别。某些数据库配置会强制使用其他事务隔离级别。为了避免在高负载场景下（例如，通过使用具有多个客户端/用户和许多并行操作的同步客户端）发生数据丢失，您需要相应地配置事务隔离级别。请参考 [MySQL 手册](https://dev.mysql.com/doc/refman/8.0/en/set-transaction.html) 获取详细信息。

## 参数 [](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/linux_database_configuration.html#parameters)

要设置 Nextcloud 以使用任何数据库，请使用 [安装向导 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/installation_wizard.html)中的说明。您通常不需要编辑 `config/config.php` 中的相应值。但是，在特殊情况下（例如，如果您想将 Nextcloud 实例连接到先前安装的 Nextcloud 创建的数据库），可能需要一些修改。



### 配置 MySQL 或 MariaDB 数据库 [](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/linux_database_configuration.html#configuring-a-mysql-or-mariadb-database)

如果你决定使用 MySQL 或 MariaDB 数据库，请确保以下事项：

- 在 MariaDB 服务器配置文件 `/etc/mysql/my.cnf` 中，将事务隔离级别设置为“READ-COMMITTED”，以确保在数据库服务器重启后仍然生效。

  验证 **transaction_isolation** 和 **binlog_format**：

```
[mysqld]
...
transaction_isolation = READ-COMMITTED
binlog_format = ROW
...
```



您的 `/etc/mysql/my.cnf` 可能如下所示：

```
[server]
skip_name_resolve = 1
innodb_buffer_pool_size = 128M
innodb_buffer_pool_instances = 1
innodb_flush_log_at_trx_commit = 2
innodb_log_buffer_size = 32M
innodb_max_dirty_pages_pct = 90
query_cache_type = 1
query_cache_limit = 2M
query_cache_min_res_unit = 2k
query_cache_size = 64M
tmp_table_size= 64M
max_heap_table_size= 64M
slow_query_log = 1
slow_query_log_file = /var/log/mysql/slow.log
long_query_time = 1

[client-server]
!includedir /etc/mysql/conf.d/
!includedir /etc/mysql/mariadb.conf.d/

[client]
default-character-set = utf8mb4

[mysqld]
character_set_server = utf8mb4
collation_server = utf8mb4_general_ci
transaction_isolation = READ-COMMITTED
binlog_format = ROW
innodb_large_prefix=on
innodb_file_format=barracuda
innodb_file_per_table=1
```



请参考 MySQL 手册中的 [页面 ](https://mariadb.com/kb/en/library/set-transaction/#read-committed)。

- 您已安装并启用了 PHP 中的 pdo_mysql 扩展
- **mysql.default_socket** 指向正确的套接字（如果数据库与 Nextcloud 运行在同一服务器上）。

注意

MariaDB 与 MySQL 向后兼容。所有说明都适用于两者。您无需将 mysql 替换为任何其他内容。

`/etc/php7/conf.d/mysql.ini` 中的 PHP 配置可能如下所示：

```
# configuration for PHP MySQL module
extension=pdo_mysql.so

[mysql]
mysql.allow_local_infile=On
mysql.allow_persistent=On
mysql.cache_size=2000
mysql.max_persistent=-1
mysql.max_links=-1
mysql.default_port=
mysql.default_socket=/var/lib/mysql/mysql.sock  # Debian squeeze: /var/run/mysqld/mysqld.sock
mysql.default_host=
mysql.default_user=
mysql.default_password=
mysql.connect_timeout=60
mysql.trace_mode=Off
```



现在您需要使用 MySQL 命令行界面创建数据库用户和数据库本身。当您首次登录时，Nextcloud 将创建数据库表。

要启动 MySQL 命令行模式，请使用：

```
mysql -uroot -p
```



使用 MariaDB 时，请使用：

```
mariadb -uroot -p
```



然后会出现一个 **mysql>** 或 **MariaDB [root]>** 提示符。现在输入以下行并按回车键确认：

```
CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';
CREATE DATABASE IF NOT EXISTS nextcloud CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;
GRANT ALL PRIVILEGES on nextcloud.* to 'username'@'localhost';
```



您可以通过输入以下内容退出提示符：

```
quit;
```



一个使用 MySQL 配置的 Nextcloud 实例将包含数据库运行的主机名、访问它的有效用户名和密码，以及数据库名。由 `config/config.php` 创建的 [安装向导 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/installation_wizard.html)因此将包含如下条目：

```
<?php

  "dbtype"        => "mysql",
  "dbname"        => "nextcloud",
  "dbuser"        => "username",
  "dbpassword"    => "password",
  "dbhost"        => "localhost",
  "dbtableprefix" => "oc_",
```



在使用 UTF8MB4 时，您还会发现：

```
"mysql.utf8mb4" => true,
```



### MySQL 数据库的 SSL 配置 [](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/linux_database_configuration.html#ssl-for-mysql-database)

如果您的数据库不位于与 Nextcloud 实例相同的服务器上，则启用 SSL 是必要的。如果您不是通过 localhost 连接并且需要允许远程连接，那么您应该启用 SSL。这仅涵盖 Nextcloud 服务器的 SSL 数据库配置。首先，您需要相应地配置您的数据库服务器。

```
'dbdriveroptions' => [
  \PDO::MYSQL_ATTR_SSL_KEY => '/../ssl-key.pem',
  \PDO::MYSQL_ATTR_SSL_CERT => '/../ssl-cert.pem',
  \PDO::MYSQL_ATTR_SSL_CA => '/../ca-cert.pem',
  \PDO::MYSQL_ATTR_SSL_VERIFY_SERVER_CERT => true,
],
```



根据您的环境调整 pem 文件的路径。



### PostgreSQL 数据库 [](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/linux_database_configuration.html#postgresql-database)

为了在 PostgreSQL 上安全运行 Nextcloud，我们假设只有 Nextcloud 使用这个数据库，因此只有一个用户访问数据库。对于其他服务和用户，我们建议创建一个单独的数据库或 PostgreSQL 实例。

如果你决定使用 PostgreSQL 数据库，请确保你已经安装并启用了 PHP 中的 PostgreSQL 扩展。PHP 配置文件 `/etc/php7/conf.d/pgsql.ini` 可能如下所示：

```
# configuration for PHP PostgreSQL module
extension=pdo_pgsql.so
extension=pgsql.so

[PostgreSQL]
pgsql.allow_persistent = On
pgsql.auto_reset_persistent = Off
pgsql.max_persistent = -1
pgsql.max_links = -1
pgsql.ignore_notice = 0
pgsql.log_notice = 0
```



PostgreSQL 的默认配置（至少在 Ubuntu 14.04 中）是使用对等认证方法。检查 `/etc/postgresql/9.3/main/pg_hba.conf` 以了解您的设置中使用了哪种认证方法。要启动 postgres 命令行模式，请使用：

```
sudo -u postgres psql -d template1
```



然后会出现一个 **template1=#** 提示。现在输入以下行并按回车键确认：

```
CREATE USER username CREATEDB;
CREATE DATABASE nextcloud OWNER username TEMPLATE template0 ENCODING 'UTF8';
GRANT CREATE ON SCHEMA public TO username;
```



您可以通过输入以下内容退出提示符：

```
\q
```



一个使用 PostgreSQL 配置的 Nextcloud 实例会包含数据库运行套接字路径作为主机名、PHP 进程使用的系统用户名、访问它的空密码以及数据库名。因此，由[安装向导](https://docs.nextcloud.com/server/latest/admin_manual/installation/installation_wizard.html)创建的 `config/config.php` 会包含如下条目：

```
<?php

  "dbtype"        => "pgsql",
  "dbname"        => "nextcloud",
  "dbuser"        => "username",
  "dbpassword"    => "",
  "dbhost"        => "/var/run/postgresql",
  "dbtableprefix" => "oc_",
```



注意

实际主机指向用于连接数据库的套接字。如果 postgreSQL 配置为使用对等认证，这里使用 localhost 将不起作用。此外，请注意没有指定密码，因为这种认证方法不使用密码。

如果你使用其他认证方法（非对等），你需要使用以下步骤来设置数据库：现在你需要使用 PostgreSQL 命令行界面创建数据库用户和数据库本身。数据库表将在你首次登录时由 Nextcloud 创建。

要启动 postgres 命令行模式，请使用：

```
psql -hlocalhost -Upostgres
```



然后会出现 **postgres=#** 提示符。现在输入以下行，并按回车键确认：

```
CREATE USER username WITH PASSWORD 'password' CREATEDB;
CREATE DATABASE nextcloud TEMPLATE template0 ENCODING 'UTF8';
ALTER DATABASE nextcloud OWNER TO username;
GRANT ALL PRIVILEGES ON DATABASE nextcloud TO username;
GRANT ALL PRIVILEGES ON SCHEMA public TO username;
```



您可以通过输入以下内容退出提示符：

```
\q
```



一个使用 PostgreSQL 配置的 Nextcloud 实例将包含数据库运行的主机名、访问它的有效用户名和密码以及数据库名。由 `config/config.php` 创建的 [安装向导 ](https://docs.nextcloud.com/server/latest/admin_manual/installation/installation_wizard.html)因此将包含如下条目：

```
<?php

  "dbtype"        => "pgsql",
  "dbname"        => "nextcloud",
  "dbuser"        => "username",
  "dbpassword"    => "password",
  "dbhost"        => "localhost",
  "dbtableprefix" => "oc_",
```





## 故障排除 [](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/linux_database_configuration.html#troubleshooting)

### 如何解决“一般错误：2006 MySQL 服务器已断开连接”[](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/linux_database_configuration.html#how-to-work-around-general-error-2006-mysql-server-has-gone-away)

数据库请求耗时过长，因此 MySQL 服务器超时。 也可能服务器正在丢弃一个过大的数据包。请 参考你的数据库手册，了解如何提高配置选项 `wait_timeout` 和/或 `max_allowed_packet`。

一些共享主机提供商不允许访问这些配置选项。对于这些系统，Nextcloud 在你的 `config/config.php` 中提供了一个 `dbdriveroptions` 配置选项，你可以将此类选项传递给数据库驱动程序。请参考[配置参数](https://docs.nextcloud.com/server/latest/admin_manual/configuration_server/config_sample_php_parameters.html)获取示例。

### 如何确定我的 MySQL/PostgreSQL 服务器是否可访问？[](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/linux_database_configuration.html#how-can-i-find-out-if-my-mysql-postgresql-server-is-reachable)

要检查服务器的网络可用性，请在服务器的主机名上使用 ping 命令（例如 db.server.com）：

```
ping db.server.com
```



```
PING db.server.com (ip-address) 56(84) bytes of data.
64 bytes from your-server.local.lan (192.168.1.10): icmp_req=1 ttl=64 time=3.64 ms
64 bytes from your-server.local.lan (192.168.1.10): icmp_req=2 ttl=64 time=0.055 ms
64 bytes from your-server.local.lan (192.168.1.10): icmp_req=3 ttl=64 time=0.062 ms
```



要更详细地检查数据库服务器软件的访问是否正常工作，请查看下一个问题。

### 如何确定创建的用户是否可以访问数据库？[](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/linux_database_configuration.html#how-can-i-find-out-if-a-created-user-can-access-a-database)

测试数据库是否可访问的最简单方法是从命令行界面开始：

**MySQL**:

假设数据库服务器安装在与你运行命令相同的系统上，请使用：

```
mysql -uUSERNAME -p
```



要访问不同机器上的 MySQL 安装，请使用相应的主机名添加-h 选项：

```
mysql -uUSERNAME -p -h HOSTNAME
```



```
mysql> SHOW VARIABLES LIKE "version";
+---------------+--------+
| Variable_name | Value  |
+---------------+--------+
| version       | 8.0.36 |
+---------------+--------+
1 row in set (0.00 sec)
mysql> quit
```



**PostgreSQL**:

假设数据库服务器安装在与你运行命令相同的系统上，请使用：

```
psql -Uusername -dnextcloud
```



要访问不同机器上的 PostgreSQL 安装，请添加相应的主机名和-h 选项：

```
psql -Uusername -dnextcloud -h HOSTNAME
```



```
postgres=# SELECT version();
PostgreSQL 16.2 on i686-pc-linux-gnu, compiled by GCC gcc (GCC) 4.1.3 20080704 (prerelease), 32-bit
(1 row)
postgres=# \q
```



### 有用的 SQL 命令 [](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/linux_database_configuration.html#useful-sql-commands)

**显示数据库用户** :

```
MySQL     : SELECT User,Host FROM mysql.user;
PostgreSQL: SELECT * FROM pg_user;
```



**显示可用数据库** :

```
MySQL     : SHOW DATABASES;
PostgreSQL: \l
```



**显示数据库中的 Nextcloud 表** :

```
MySQL     : USE nextcloud; SHOW TABLES;
PostgreSQL: \c nextcloud; \d
```



**退出数据库** :

```
MySQL     : quit
PostgreSQL: \q
```







# 启用 MySQL 4 字节支持 [](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/mysql_4byte_support.html#enabling-mysql-4-byte-support)

注意

在执行此数据库升级前，请务必备份您的数据库。

要在使用 MySQL 数据库的 Nextcloud 服务器上使用 Emoji（基于文本的表情符号），需要对安装进行一些调整。

警告

本手册仅涵盖 MySQL 8 或更新版本以及 MariaDB 10.2 或更新版本。 如果你使用 MariaDB 10.2，请检查 [这个旧版本](https://docs.nextcloud.com/server/20/admin_manual/configuration_database/mysql_4byte_support.html#mariadb-10-2-or-earlier) 文档中。如果你使用的是较旧版本的 MySQL 或 MariaDB，请注意它们不再受支持。 由当前 Nextcloud 版本决定。

1. 确保您的 MySQL 服务器上设置了以下 InnoDB 配置：

   ```
   [mysqld]
   innodb_file_per_table=1
   ```

   

2. 如果您在第一步中更改了配置，请重启 MySQL 服务器。

然后您可以验证更改是否生效：

```
SHOW VARIABLES LIKE 'innodb_file_per_table';
```



结果应如下所示：

```
mysql> SHOW VARIABLES LIKE 'innodb_file_per_table';
+-----------------------+-------+
| Variable_name         | Value |
+-----------------------+-------+
| innodb_file_per_table | ON    |
+-----------------------+-------+
1 row in set (0.00 sec)
```



1. 打开一个 shell，切换目录（如果需要，将 `/var/www/nextcloud` 修改为你的 nextcloud 安装位置），如果尚未启用维护模式，请将 nextcloud 实例置于维护模式：

   ```
   $ cd /var/www/nextcloud
   $ sudo -E -u www-data php occ maintenance:mode --on
   ```

   

2. 更改你的数据库字符集和排序规则：

```
ALTER DATABASE nextcloud CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;
```



1. 将 `mysql.utf8mb4` 配置设置为 true 在你的 config.php 中：

   ```
   $ sudo -E -u www-data php occ config:system:set mysql.utf8mb4 --type boolean --value="true"
   ```

   

2. 通过运行修复步骤将所有现有表转换为新的排序方式：

   ```
   $ sudo -E -u www-data php occ maintenance:repair
   ```

   

注意

这将同时将你的表的 ROW_FORMAT 更改为 DYNAMIC。

1. 禁用维护模式：

   ```
   $ sudo -E -u www-data php occ maintenance:mode --off
   ```

   

现在你应该能够在文件名、日历事件、评论等地方使用表情符号了。

注意

同时确保你的备份策略仍然有效。如果你使用 `mysqldump` ，请确保添加 `--default-character-set=utf8mb4` 选项。否则你的备份会损坏，恢复它们时将导致 `?` 而不是表情符号，使文件无法访问。







# BigInt (64 位) 标识符 [](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/bigint_identifiers.html#bigint-64bit-identifiers)

Nextcloud 使用大整数来存储数据库中的标识符和自动递增键。由于更改大型表中的列可能需要相当长的时间（取决于 Nextcloud 实例中的文件数量，可能长达数小时或数天），因此必须通过控制台命令手动触发文件缓存和活动表的迁移。

该命令可以安全执行。当没有需要处理的事项时，它会显示成功消息：

```
sudo -E -u www-data php occ db:convert-filecache-bigint
All tables already up to date!
```



或者，在执行重大操作之前会要求确认：

```
sudo -E -u www-data php occ db:convert-filecache-bigint
This can take up to hours, depending on the number of files in your instance!
Continue with the conversion (y/n)? [n]
```



要抑制确认消息，在参数列表中添加 `--no-interaction`：

```
sudo -E -u www-data php occ db:convert-filecache-bigint --no-interaction
```



注意

与正常更新类似，在运行命令之前应关闭您的 Apache 或 nginx 服务器或启用维护模式，以避免与同步客户端出现问题。







# 复制 [](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/replication.html#replication)

*添加于版本 29。*

Nextcloud 可以在数据库查询级别上原生地分割读写操作。副本仅用于读取。写入和因果读取将使用默认数据库连接。

```
'dbreplica' => [
    ['user' => 'nextcloud', 'password' => 'password1', 'host' => '10.0.3.1', 'dbname' => 'nextcloud'],
    ['user' => 'nextcloud', 'password' => 'password2', 'host' => '10.0.3.2', 'dbname' => 'nextcloud'],
],
```









# 拆分数据库 [](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/splitting.html#splitting-databases)

警告

这仍然是概念验证级别。请谨慎使用。

为了将来能够扩展，拆分某些表或允许拆分的应用可能是有意义的，因为它们可能更适合使用不同的复制方法等。

我们目前正在进行的一个尝试是拆分活动表。为了使用这个功能，应用/表需要符合以下标准：

- 不允许其他应用程序直接查询该表
- 在这个表和任何其他不在这个新独立连接上的表之间不执行任何 JOIN 操作
- 应用程序需要支持连接参数前缀

对于活动应用程序，前缀是 `activity_`。如果没有指定数据库配置，它会回退到这个值的正常数据库配置选项：

- `activity_dbuser` 回退到 `dbuser`
- `activity_dbpassword` 回退到 `dbpassword`
- `activity_dbname` 回退到 `dbname`
- `activity_dbhost` 回退到 `dbhost`
- `activity_dbport` 回退到 `dbport`
- `activity_dbdriveroptions` 回退到 `dbdriveroptions`

注意

对于拆分数据库，无法使用不同类型的数据库（SQLite、MySQL、PostgreSQL、Oracle）。此外，在 MySQL 和 MariaDB 的情况下，两个数据库上的 utf8mb4 选项需要保持一致。

## 初始拆分 [](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/splitting.html#initial-splitting)

对于初始拆分，需要将受影响的表复制到新数据库，对于活动应用来说，这些表包括：

- `oc_activity`
- `oc_activity_mq`

1. 启用维护模式

2. 确保应用可选的数据库更改：

   > 1. `occ db:convert-mysql-charset`
   > 2. `occ db:convert-filecache-bigint`
   > 3. `occ db:add-missing-columns`
   > 4. `occ db:add-missing-indices`
   > 5. `occ db:add-missing-primary-keys`

3. 指定所需的配置值

4. 将2个表复制到新数据库

5. 关闭维护模式

## 更新中的迁移 [](https://docs.nextcloud.com/server/latest/admin_manual/configuration_database/splitting.html#migrations-on-updates)

我们将尽量避免在这些表上进行迁移，但有时可能还是必要的。我们希望在那时能有一个专门的计划。目前一个可能的方法是：

1. 启用维护模式
2. 按常规更新
3. 执行应用程序作者提供的模式变更手动查询
4. 执行应用程序作者提供的数据变更手动查询
5. 关闭维护模式





