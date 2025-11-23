**Dolibarr ERP & CRM** 是一款模块化软件（我们只激活需要的功能），适用于不同规模的企业（中小企业、大型公司、自由职业者或协会）的商业管理软件。

它是一个开源项目，通过模块的添加（你只启用需要的特性），在 WAMP、MAMP 或 LAMP 服务器（Apache、Mysql、PHP，适用于所有操作系统）上构建。Dolibarr 旨在提供一套 ERP 和 CRM 解决方案，主要目标是简化操作：

- 易于安装
- 易于使用
- 易于开发

Dolibarr 可以作为云端或本地解决方案进行安装，为没有技术知识的用户提供 **自动安装程序** ，只需一个软件包即可 **安装 Dolibarr 及其所有先决条件（Apache、Mysql、PHP）**。这些软件包包括：

- [DoliWamp](https://wiki.dolibarr.org/index.php/DoliWamp "DoliWamp"), Windows 用户的自动执行安装程序。
- [DoliDeb](https://wiki.dolibarr.org/index.php/Dolibarr_for_Ubuntu_or_Debian "Dolibarr for Ubuntu or Debian"), Linux Debian/Ubuntu 用户的自动安装程序。
- [DoliRpm](https://wiki.dolibarr.org/index.php/Dolibarr_for_Redhat_or_Fedora_\(rpm_package\) "Dolibarr for Redhat or Fedora (rpm package)"), Linux RedHat/Fedora/OpenSuse/Mandriva/Mageia 用户的自动安装程序。

其他所有操作系统和大多数云解决方案也由"通用"版本支持。

以下为 Dolibarr 功能概览，详见"主要模块/功能"部分

## 目录

- [1主要模块/功能](https://wiki.dolibarr.org/index.php/What_Dolibarr_Does#Main_modules_.2F_features)
- [2杂项](https://wiki.dolibarr.org/index.php/What_Dolibarr_Does#Miscellaneous)
- [3前提条件](https://wiki.dolibarr.org/index.php/What_Dolibarr_Does#Prerequisites)
- [4Dolibarr 发布](https://wiki.dolibarr.org/index.php/What_Dolibarr_Does#Dolibarr_Releases)

##  [![Art.png](https://wiki.dolibarr.org/images/6/66/Art.png)](https://wiki.dolibarr.org/index.php/File:Art.png)主要模块/功能

- 客户、潜在客户或供应商目录（CRM）
- 产品和服务目录
- 银行账户管理
- 商业行为管理
- 订单管理
- 商业提案管理
- 合同管理
- 发票管理
- 项目管理（机会管理、活动组织、工时表等）
- 付款管理，在线支付收款（通过 Paypal、Stripe、等）
- 直接借记和信用转账管理
- 库存、盘点和发货管理
- 制造订单管理（MRP）
- 跟踪社会和财政税务支付
- 双账会计，总账和辅助会计
- 带 ical,vcal 导出的日程安排，用于第三方工具集成
- EDM/DMS（电子文档管理/文档管理系统）
- 适用于商店、酒吧或餐馆的 POS 系统
- 基础成员管理
- 费用报告
- 员工休假申请
- 批量邮件发送
- 实现调查问卷
- 捐赠
- 大量即用型报告
- 所有管理对象（发票、报价单、订单、发货单、库存等）的 PDF 生成
- 导入和导出工具（CSV 或 Excel）
- LDAP 连接

注意：Dolibarr 的功能可以通过从 [DoliStore.com](https://www.dolistore.com/)（皮肤、Google 同步、Prestashop、AWStats、Gravatar、...）提供的众多外部模块进行扩展。

##  [![Art.png](https://wiki.dolibarr.org/images/6/66/Art.png)](https://wiki.dolibarr.org/index.php/File:Art.png)其他

- 多用户，每个功能都有多个权限级别
- 多货币
- 多语言
- 非常用户友好，易于使用
- 高度可定制：仅启用您需要的模块；字段可由用户个性化设置；选择您的皮肤；多个菜单管理器（可用于内部用户作为具有特定菜单的后台，或用于外部用户作为具有另一个菜单的前台）。
- 开放的 Web 服务 API（REST API）
- 易于理解、维护和编码，可与您自己的系统信息接口（使用无重型框架的 PHP）。开发人员友好的架构，具有触发器和钩子。

  

- 支持特定国家的财务管理要求：
    - 特定国家的税收系统（西班牙税收 RE 和 IRPF、法国针对 DOM-TOME 的“Non Perçu Récupérable”增值税、巴斯克地区的 TicketBAI、加拿大的双重税收（联邦/省）、突尼斯税票、印度 GST 等），法国财政法 - 反欺诈增值税 [[1]](https://wiki.dolibarr.org/index.php?title=Loi_finances_2016_sur_les_logiciels_de_caisse_et_Certification_NF525_ou_LNE)
    - 生成沙特阿拉伯的 ZATCA/ZAKAT 条形码电子发票、EPC QR 码等。
    - 符合欧洲指令（2006/112/CE ... 2010/45/UE）[[2]](http://europa.eu/legislation_summaries/taxation/l31057_en.htm)
    - 支持电子发票（FacturX, Peppol）
    - 支持本地支付信息，如比利时的"结构化通信"、芬兰的"RF 支付参考"...

  
以下页面描述了 Dolibarr 尚未提供（目前）的功能： [What Dolibarr can't do](https://wiki.dolibarr.org/index.php/What_Dolibarr_can%27t_do "What Dolibarr can't do")

##  [![Art.png](https://wiki.dolibarr.org/images/6/66/Art.png)](https://wiki.dolibarr.org/index.php/File:Art.png)前提条件

- 支持 PHP **7.1.0+**、MySQL **5.1+** 或 MariaDB **5.1+** 或 PostgreSQL **9.1.0+**
- 兼容所有操作系统（Windows 7+、Ubuntu 14.04+ 等）和所有浏览器（IE 11+、Edge 12+、Firefox 20+、Opera 12.1+、Chrome 29+、Safari 9+、所有支持 flex CSS 的浏览器）
- Windows、Debian/Ubuntu、Fedora/Redhat/OpenSuse 的安装程序，或用于在任何 Web 服务器上手动安装的软件包
- 也兼容所有满足 PHP、MySQL/MariaDB 或 PostgreSQL 先决条件的云解决方案（例如在以下云供应商上：[https://saas.dolibarr.org](https://saas.dolibarr.org/)）

##  [![Art.png](https://wiki.dolibarr.org/images/6/66/Art.png)](https://wiki.dolibarr.org/index.php/File:Art.png)Dolibarr 版本发布

- Dolibarr 主要版本列表已在页面 [RoadMap](https://wiki.dolibarr.org/index.php/Category:RoadMap "Category:RoadMap") 上定义
- 对于完整列表，包括小版本发布，请查看此表格： [发布](https://wiki.dolibarr.org/index.php/Releases "Releases")
