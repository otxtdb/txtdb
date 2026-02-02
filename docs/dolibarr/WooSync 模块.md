# WOOSYNC 用户指南

# 1. 介绍

### 1.1. 功能

[Woosync](https://link.easya.solutions/woosync_dolistore) 是 Dolibarr/Easya 与 Wordpress/Woocommerce 之间的同步模块。它同步产品、库存、客户和联系人、订单，并允许创建发票及其付款。

|||
|---|---|
||![文本框: 模块兼容性与合规性 该模块与小计和多公司模块兼容。此外，它符合 2016 年财政法。](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image001-1769633437512-59.gif?lastModify=1769681364)|

### 1.2. 许可

我们所有的模块都在 [Dolistore](https://link.easya.solutions/dolistore_opendsi) 上以 [GPL v3 许可证分发](https://link.easya.solutions/gpl_v3)。

### 1.3. 资源

#### 本文档

我们的用户指南旨在为您提供全面的模块使用支持。部分指南篇幅较长，但阅读这些指南对于充分理解模块功能至关重要。

# 2. 开始之前

### 2.1. 警告

我们保证模块在 Dolibarr 原生环境中运行良好。但若对 Dolibarr 核心文件进行修改或使用其他附加模块，则无法保证其正常运行。

我们的模块与PostgreSQL数据库不兼容。

在NAS类平台（如QNAS、SYNOLOGY等）上使用我们的模块不受支持。由此引发的故障及其解决将由客户自行承担，或按Easya Solutions实际耗时计费。

|||
|---|---|
||![文本框: 注意！  Woosync是一个技术性强且复杂的模块。我们建议您在安装时寻求专业支持。  此外，我们建议您先在测试版的DOLIBARR和WORDPRESS实例上进行初始安装和配置，切勿直接在生产环境中操作。](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image002-1769633437512-57.gif?lastModify=1769681364)|

### 2.2. Easya/Dolibarr兼容性与技术要求

该模块支持18及以上版本。

您的环境还需具备以下配置要素：

• 至少 5.6.30 版的 Php

• MySQL 版本至少为 5.5.55

### 2.3. 功能兼容性

该模块存在以下功能限制（非详尽列表）：

|**Easya/Dolibarr功能**|![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image004-1769633437512-58.jpg?lastModify=1769681364) **→** **![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image006-1769633437512-60.jpg?lastModify=1769681364)**|![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image006-1769633437512-60.jpg?lastModify=1769681364) **→** **![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image007-1769633437585-61.jpg?lastModify=1769681364)**|
|---|---|---|
|通过 WPML 扩展实现多语言界面（[参见第 14 章，多语言商店](#_bookmark90)）|部分|部分|
|套件/虚拟产品（参见???）|否|部分|
|变体属性|否|否|
|[变](#_bookmark26)体（[参见“变体管理”](#_bookmark26)）|否|部分|
|限制与精度|部分|部分|

|Wordpress/Woocommerc扩展|![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image004-1769633437512-58.jpg?lastModify=1769681364) **→** **![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image006-1769633437512-60.jpg?lastModify=1769681364)**|![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image006-1769633437512-60.jpg?lastModify=1769681364) **→** **![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image007-1769633437585-61.jpg?lastModify=1769681364)**|
|---|---|---|
|礼品卡 参见[第6.2节“产品”](#_bookmark24)|部分|否|
|WPML [参见第14章，多语言商店](#_bookmark90)|是/否/部分|是/否/部分|
|[WooCommerce的库存位置](https://fr.wordpress.org/plugins/stock-locations-for-woocommerce/) 参见[第12.1节，“使用](#_bookmark83)[Woocommerce](#_bookmark83)[库存位置](#_bookmark83)[”](#_bookmark83)|是/否/部分|是/否/部分|
|[WooCommerce 多地点库存](https://codecanyon.net/item/woocommerce-multi-locations-inventory-management/28949586)[管理](https://codecanyon.net/item/woocommerce-multi-locations-inventory-management/28949586) 参见[第 12.2 节，“使用 WooCommerce](#_bookmark84) [多地点库存管理”](#_bookmark84)|是/否/部分|是/否/部分|
|[高级优惠券](https://wordpress.org/plugins/advanced-coupons-for-woocommerce-free/)|是/否/部分|是/否/部分|

### 2.4. 维护

购买该模块可享受一年_纠错维护服务_。此纠错_维护不包括_[_使用指导或_](mailto:info@open-dsi.fr)[_用户_](mailto:info@open-dsi.fr)支持，仅限于_修复_错误，前提是模块使用正确且与所用版本的Dolibarr兼容。

### 2.5. 更新

更新的可用性信息、访问条件和条款以及操作[流程详见第 18](#_bookmark94) [章“升级与更新”](#_bookmark94)。

# 3. 安装与激活

### 3.1. 操作步骤

如果您能够访问 Dolibarr 的文件夹和文件，请将模块的压缩包解压到其树形结构中的 custom 文件夹中。

压缩模块也可直接**从首页** > 配置 > 模块/应用程序页面中的“部署外部模块”选项卡进行安装。

**图** **3.1.** **从** **Dolibarr** 安装模块的屏幕

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image009.jpg?lastModify=1769681364)

注意

若您从GitHub下载该模块，请将ZIP压缩包重命名为_module_ecommerceng-**版本_号，并将其中内容重命名为ecommerceng，随后将其解压至Dolibarr的/custom文件夹中进行安装。

### 3.2. 激活

通过以下菜单显示模块列表来激活该模块

**首页** > 配置 > 已安装模块/应用程序。

**图** **3.2.** **已激活的** **Woosync** **模块**

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image012.jpg?lastModify=1769681364)

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image014.jpg?lastModify=1769681364)和![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image016.jpg?lastModify=1769681364) 按钮用于显示模块状态：点击![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image016-1769634110149-166.jpg?lastModify=1769681364) 即可激活模块。点击![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image014-1769634118989-168.jpg?lastModify=1769681364) 则可停用模块，此时按钮将显示模块处于激活状态。

# 4. 权限

### 用户权限

可根据以下列表，在用户和组的“权限”选项卡中限制其对模块功能的访问权限。

点击 ![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image016-1769634243019-170.jpg?lastModify=1769681364) 按钮授予权限，点击 ![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image014-1769634289968-174.jpg?lastModify=1769681364)按钮撤销权限。已授予的权限由![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image014-1769634271266-172.jpg?lastModify=1769681364)按钮表示。

**图** **4.1.** **模块用户权限**

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image018.jpg?lastModify=1769681364)

### 默认权限

模块的功能可通过模块安装后的“首页 > 配置 > 安全”页面中的“默认权限”选项卡，对现有用户和组或后续创建的用户和组进行限制。

**图** **4.2.** **模块的****默认权限**

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image020.jpg?lastModify=1769681364)

# 5. Easya/Dolibarr 与 Woocommerce 之间的连接

添加商店需要事先在 Dolibarr 中存在第三方类别和产品/服务类别，以便进行同步。根据解决方案的使用情况，可能还需要仓库、银行账户和供应商（例如 Stripe）。

在Wordpress/Woocommerce方面，必须激活具有读/写权限的API密钥。

为实施同步而添加商店的操作，需通过模块管理页面进行，该页面可通过**菜单首页** > 配置 > 已安装模块/应用程序访问。

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image022.jpg?lastModify=1769681364)点击已激活模块的 图标，或通过菜单**工具** > WOOSYNC > 站点配置进行操作。

**图**5.1.店铺登录页面

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image024.jpg?lastModify=1769681364)

• 网站名称：您在 Dolibarr 中（第一个）商店的名称。

• 网站地址：请输入您商店的访问网址。

注

点击链接“点击此处测试网址（应显示 XML 或 JSON 文件应显示）链接以测试 Easya/Dolibarr 与您的在线商店之间的通信是否正常。通信失败将显示 404 错误。通信成功将显示与您的在线商店相关的数据。

要成功连接，还需调整Wordpress中固定链接结构的设置，将其选项设为**除**"简单"以外的其他选项**。请进入商店管理界面，选择菜单**"设置" > "固定链接"。

• API版本：选择Wordpress/Woocommerce使用的API版本。

注意

使用 1 或 2 版本可能会限制未来的同步。

• 认证类型：可使用多种方法：

**OAuth1****（头部）**：

**OAuth1****（网址）**：

**基本**：

**URL**：

• WOOCOMMERCE API 客户密钥和 WOOCOMMERCE API 密钥：生成的密钥

在Woocommerce设置中。

• WOOCOMMERCE API 访问超时：从界面启动操作的执行时限，默认值（若未填写）为 30 秒。

• 调试：此模式可在发生卡顿或任何错误时显示更完整的错误信息。仅用于分析复杂错误原因时启用。

记录完这些初始信息后，将出现新的选项卡（第三方、产品、库存和订单/发票[——参见第 6](#_bookmark21) [章“对象同步](#_bookmark21)设置”），以及页面底部的“WebHooks 配置”（[参见第 8.1 节“](#_bookmark60)[“WebHooks配置”](#_bookmark60)）和WORDPRESS连接参数。

#### 连接其他商店

在同步配置页面，从“网站选择”下拉列表中选择“添加新网站”。您需要重新进行相同的设置，并根据您的另一个 Woocommerce 商店进行调整。

**图** **5.2.** **新增商店**页面

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image030.jpg?lastModify=1769681364)

请注意“删除”按钮。该按钮将删除与屏幕上显示的商店相关的所有连接信息。

# 6. 对象同步设置

|||
|---|---|
||![文本框: 为避免同步过程中出现卡顿...  如果您的对象记录包含额外的必填字段，建议为其设置默认值，以免在同步时阻塞其创建。](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image031.gif?lastModify=1769681364)|

### 6.1. 第三方

根据其他设置，客户同步将仅限于在“客户类别”字段中选择的类别。所有在 Dolibarr 中同步的商店客户都将添加到该类别。

**图** **6.1.** **第三方同步设置**

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image033.jpg?lastModify=1769681364)

通用第三方客户收集（未创建账户）功能可用于

汇总所有未创建账户的商店订单。在这种情况下，所有订单都将关联到该第三方，其送货地址和账单地址将添加到联系人中。

无需创建账户即可下单

激活模块后，系统将自动创建匿名客户。您可以保留、重命名、删除该客户，或选择其他第三方客户。

“支持的用户角色”字段可将Wordpress用户与Dolibarr的同步限制在此处输入的角色范围内。例如，您可仅同步**客户**类型的用户，这样就能避免在同步时将Wordpress管理员创建到Dolibarr中。

注意

最新版本的 Woocommerce 不再允许在此字段中选择多个角色。因此，请**从客户**、**管理员**、**作者**、**贡献者**、**编辑**、**订阅者**、**商店经理**等角色中进行选择。Wordpress 扩展可能会添加其他角色。

如果未输入任何角色，则所有联系人都会被同步。

其他第三方和联系人同步选项：

• DOLIBARR与电子商务平台的实时第三方同步：

当Dolibarr中的第三方数据发生任何变更时，Woocommerce数据将自动更新，

• DOLIBARR 与电子商务平台的实时联系人同步：

当Dolibarr中的联系人发生任何更改时，Woocommerce的数据都会自动更新。

• 按姓名和邮政编码搜索：

• 第三方更新：勾选此框可防止在Dolibarr中更新已存在的Woocommerce第三方数据。

|||
|---|---|
||![文本框: 为避免同步过程中出现任何阻塞... 在客户下单后创建客户时，"客户代码"字段将自动填充。但对于现有第三方供应商下单的情况，其"客户代码"字段将为空，这会在创建过程中导致阻塞。请在处理网络挂钩前手动修改第三方信息，将其转换为客户。](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image034-1769633437683-66.gif?lastModify=1769681364)|

### 6.2. 产品

数据同步设置显示在专用选项卡中。该页面包含两个表格：首先是常规选项，然后是数据同步方向。

与第三方设置类似，产品类别将限制产品数据同步的范围：只有该类别中的产品数据才会同步到 Dolibarr。从 Wordpress 到 Dolibarr 的所有产品同步操作都会将产品添加到该类别中。

然后请勾选“实时同步Dolibarr产品至电子商务平台”选项框，以指示是否需要将Dolibarr中的所有产品变更实时同步至Wordpress。

如果未勾选此框，Easya/Dolibarr中修改的数据将通过手动同步发送至Woocommerce。

产品的销售价格会持续进行双向同步：Dolibarr 修改后实时同步，以及通过手动同步或处理网络挂钩来同步 Wordpress 上的修改。销售价格同步字段决定了在 Wordpress 上促销时应更新的价格。

**图** **6.2.** **产品同步设置**

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image036.jpg?lastModify=1769681364)

"导入价格类型"决定了从Dolibarr导入更新Wordpress价格时需要填写的字段。详见?。

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image038.jpg?lastModify=1769681364)![文本框: 价格等级  如果您已启用产品的价格等级功能，请指定与您的商店同步的价格等级。](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image040.gif?lastModify=1769681364)

此页面用于在 Dolibarr 现有服务中声明在订单和发票行中使用的服务，这些服务在 Wordpress 中对应以下同步：

• 适用于Woocommerce订单的运费；

• 促销代码：Woocommerce的原生功能；

• 礼品卡（需使用 [PW](https://wordpress.org/plugins/pw-woocommerce-gift-cards/) [WooCommerce Gift Cards Pro](https://wordpress.org/plugins/pw-woocommerce-gift-cards/) 扩展程序）；

• 商店积分（需使用Advanced [Coupons](https://wordpress.org/plugins/advanced-coupons-for-woocommerce-free/)扩展程序）。

在“电子商务网站上的重量单位”和“电子商务网站上的尺寸单位”字段中，填写Wordpress上使用的商品管理单位。

**变体管理** 在Wordpress中使用变体时，请选择：

**一比一** 每个WordPress产品变体都将作为独立产品同步到Dolibarr。 注 为确保库存管理有效，建议选择此选项。

**全部** **=>** **单一** 仅父级产品会同步到 Dolibarr。变体产品会随其自身信息一起集成到订单行中。

WPML 扩展支持多语言商店的同步。更多信息请参阅第 [14](#_bookmark90) [章“多语言商店”](#_bookmark90)。

“支持状态”字段可限制在 Easya/dolibarr 中创建的产品，仅同步在此处选择状态的产品。 请输入您想要同步的产品的 woocommerce 状态，用逗号分隔（例如：**pending,publish**）。如果此字段留空，则所有产品无论其状态如何都将创建在 Dolibarr 中。

在页面后半部分，请为每个项目选择同步方向选项：

**无**

数据不会同步。在 Dolibarr 和/或 Wordpress 中输入的值将保持独立；

**双向**

当其中一个软件中的数据发生更改时，另一个软件中的数据也将随之更新（不推荐此选项）；

**从DOLIBARR到电子商务平台**

在Dolibarr中输入或修改的值将根据具体情况实时或通过[计划任务](#_bookmark65)发送至Wordpress；

**从电子商务平台到Dolibarr**

在Wordpress中输入或修改的值将通过Web钩子发送至Dolibarr，并由计划任务进行处理。

**图** **6.3.** 产品同步方向

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image045.jpg?lastModify=1769681364)

图示中的数值为建议的同步方向。

#### Easya/Dolibarr 与 Wordpress 字段对应关系

Easya/Dolibarr 的 RÉF 对应于 Woocommerce 的 UGS。

产品信息卡中添加了补充字段，用于存储来自 Woocommerce 的描述信息，同时不会干扰您商业文件 PDF 中显示的数据。

重量和尺寸填充两个解决方案中产品的原生字段。有关单位管理，请[参见图6.2](#_bookmark25)。

#### 图片管理

在双向同步图像或从 Easya/Dolibarr 同步图像到产品附件文件时，只有勾选了“通过链接共享文件”复选框的图像才会被同步。在从 Wordpress 同步图像到 Easya/Dolibarr 时，除了定义同步方向外，无需执行其他操作。

**图6.4.图片共享链接**

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image047.jpg?lastModify=1769681364)

根据设定的同步方向，将显示相应按钮：

**图** **6.5.** **图像同步按钮**

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image049.jpg?lastModify=1769681364)

#### 图像同步的服务器设置

**Apache服务器。** 服务器配置文件的目录标签中必须包含以下内容：

AllowOverride All

Options -Indexes +FollowSymLinks +Multiviews Order allow,deny

允许所有来源 要求所有授予

**Nginx服务器。** 在Dolibarr主机的配置文件中，服务器部分添加以下内容：

location ~ ^/[A-z]+/custom/ecommerceng/document/

{

重写 ^/([A-z]+)/custom/ecommerceng/document/([^/

]+)/[^/.]+.[A-z]+$ /$1/document.php?hashp=$2;

}

#### 6.2.1. 增值税类别同步

记录产品数据的同步方向后，点击页面顶部的“更新增值税类别词典”按钮，并在弹出窗口中确认操作。

此操作将从Woocommerce导入现有的各类增值税，并将其填入Dolibarr词典，您可通过**首页** > 配置 > 词典访问该词典。

**图6.6.增值税税率管理词典**

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image053.jpg?lastModify=1769681364)

《WOOCOMMERCE增值税分类列表》和《WOOCOMMERCE增值税税率列表》字典分别包含增值税分类和适用税率及国家信息，这些信息均依据Woocommerce中的设置进行配置。

分别包含增值税类别以及适用税率和国家/地区，这些信息均基于Woocommerce中的配置设置。

#### 6.2.2. Easya/Dolibarr补充字段与Woocommerce元数据

Dolibarr 的附加属性可与 Dolibarr 的元数据进行匹配。

附加字段词典

词典 WOOCOMMERCE 属性列表 包含两个软件之间创建的附加字段同步管理数据。

**图** **6.7. Woocommerce** 元数据

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image055.jpg?lastModify=1769681364)

在设置屏幕的字段中输入WooCommerce中对应元数据的名称。

**图** **6.8. Dolibarr** **的元数据和附加属性**

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image058.jpg?lastModify=1769681364)

勾选“激活”框以允许同步。

然后，在“订单同步”表中，定义对订单行中产品元数据的处理方式：首先激活它们，然后选择“包含”或“排除”，用逗号分隔。

### 6.3. 库存

在库存设置选项卡中，根据已查看的选项（[参见图 6.3](#_bookmark27)）指定库存的同步方向。

**图** **6.9.** 库存同步设置

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image060.jpg?lastModify=1769681364)

注

订单验证参数仅在Easya/Dolibarr设置中启用订单验证时进行库存减记时生效。此时，该参数将指定订单同步时库存调拨的仓库位置 （关于[发票确认时的库存减少，](#_bookmark46)请参阅“发票确认时的库存减少”）。

定义并保存库存同步方向后，请指定用于同步产品库存的仓库。

如果库存是从 Dolibarr 同步到 Woocommerce，请勾选“虚拟库存”选项，以便将产品的虚拟库存而非实际库存发送到您的商店。

**图6.10.仓库同步设置**

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image063.jpg?lastModify=1769681364)

如果库存从Dolibarr同步到Woocommerce，您可以选择多个仓库。产品数量将被累加后发送至Woocommerce。

Dolibarr与Woocommerce库存自动同步

在 Dolibarr 中修改库存后，库存数量的发送将通过一个计划任务完成，您需要激活该任务（参见[第 8.2 节](#_bookmark65)[“激活订单处理计划任务”](#_bookmark65)）。默认情况下，同步的产品数量为实际库存。如果您勾选“虚拟库存”复选框，则将发送虚拟库存数量而非实际库存。

请注意“仓库管理扩展”下拉列表。在此处选择用于管理多个仓库[的Wordpress扩展，可选项包括“Stock locations for](https://fr.wordpress.org/plugins/stock-locations-for-woocommerce/) [Woocommerce”和“Woocommerce Multi Locations Inventory](https://codecanyon.net/item/woocommerce-multi-locations-inventory-management/28949586) Management”。更多详情请[参阅第12](#_bookmark82)[章“高级库存管理](#_bookmark82)”。

### 6.4. 订单

订单/发票选项卡包含订单同步选项，分为三个表格。发票管理[将在第6.5节“发票”中](#_bookmark44)详细说明。

首先是常规设置。请指定：

• 是否需要通过勾选“创建订单”字段（模块激活时默认勾选）来创建Dolibarr中的订单。

此选项允许直接创建发票。

• 是否将订单在 Dolibarr 中的状态变更同步至 Woocommerce，通过勾选“将 Dolibarr 订单实时同步至电子商务平台”复选框

• 如果订单中增加的银行手续费需要作为订单行同步到Dolibarr，请勾选“将费用行视为服务行”参数。

如果未激活此参数，订单中将不会显示这些费用。此参数同样适用于[发票](#_bookmark44)。

此外，如果：

• 产品行元数据（即附加字段）必须包含在同步到 Dolibarr 的订单行中（[参见第 6.2.2](#_bookmark32) [节“Easya/Dolibarr 附加字段与 Woocommerce 元数据”](#_bookmark32)）；

• Woocommerce 订单备注应显示在订单的_公开备注中_，而非私密备注中。

**图** **6.11.** **订单同步设置**

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image066.jpg?lastModify=1769681364)

|||
|---|---|
||![文本框: 恢复日期  恢复日期是指从该日期起，Woocommerce上的订单将同步到Easya/Dolibarr。此操作将在初始同步时立即执行。  注意 若连接至现有商店，此字段保持空白时，WooCommerce上的所有订单都将同步至Easya/Dolibarr，并可能自动生成发票。](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image068-1769633437849-72.gif?lastModify=1769681364)|

在下方“订单状态同步”表格中，确认两个解决方案之间的状态对应关系。首先从 DOLIBARR 到 E-COMMERCE 的方向，然后从 E-COMMERCE 到 DOLIBARR 的方向。

参数“仅当级别高于

前一状态时才更改状态"意味着，当Dolibarr中的订单状态发生变更（例如从已处理变为进行中）时，发送至Woocommerce（参见["添加至](#_bookmark41)[Easya/Dolibarr订单](#_bookmark41)[的附加字段](#_bookmark41)["](#_bookmark41)）。

注意

您发送的订单成功接收通知可能会再次发送给客户，有时甚至会发送给客户已收到的旧订单。

**图** **6.12.** **订单及其发票的同步设置**

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image072.jpg?lastModify=1769681364)

在"E-COMMERCE 至 DOLIBARR"方向中，您可以通过勾选或不勾选网站订单状态来选择是否将这些订单同步至 Easya/Dolibarr。

#### 添加到 Easya/Dolibarr 订单的附加字段

该模块为订单添加了三个补充字段，用于显示订单是否已在线支付、通过URL访问您商店后台的订单页面以及状态对应字段。

**图** **6.13.** **订单附加字段**

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image076.jpg?lastModify=1769681364)

对于后者，如果Woocommerce扩展添加了状态，请根据以下规则补充其值列表。无对应状态将导致同步和/或处理网络挂钩时出现错误。

• n_：状态级别后跟下划线，

• 状态代码，后跟逗号，

• Easya/Dolibarr 界面显示的新状态**名称**。

示例 de statuts additionnels apportés sur Woocommerce par le 模块 模块 管理 模块 管理 管理 Colissimo ：2_lpc_ready_to_ship（Colissimo 准备发货）、2_lpc_partial_exp（Colissimo 部分发货）、2_lpc_anomaly（Colissimo 异常）或 3_lpc_transit（Colissimo 运输中）。

然后点击“更新支付方式”按钮。此操作将从Woocommerce导入您为客户提供的各种支付方式。

在弹出窗口中确认并完成操作后，请转到页面底部。对于网站提供的每种支付方式，请在 Easya/Dolibarr 中的数据中指定相应的支付方式和银行账户。

**图** **6.14.** **支付方式对应关系**

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image078.jpg?lastModify=1769681364)

### 6.5. 发票

|||
|---|---|
||![文本框: 注意！  如果Woocommerce中有历史记录，则所有订单的同步将创建自先前定义的同步日期起所有相关的发票。  发票创建功能可稍后激活。](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image079.gif?lastModify=1769681364)|

可以创建发票作为订单的补充或替代。为此，请激活“创建发票”参数（[图6.15](#_bookmark45)）。激活此参数后，将提供三个新选项。

若仅需创建发票（而非订单），请勾选/取消勾选相应参数（即创建订单和/或创建发票）。

注意

只有状态为“已确认”或更高的同步订单才能创建发票：状态为“草稿”的同步商店订单不会创建发票。

**图** **6.15.** **发票管理设置**

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image082.jpg?lastModify=1769681364)

• 发票类型：选择生成的发票是应付发票还是预付发票。

• 即使金额为零也创建发票：如果您希望所有订单都开具发票，即使金额为零（例如可免费下载的产品），

• 或者您希望通过电子邮件发送发票。

在发票确认时减少库存

如果您的库存减少设置为在发票确认时执行，请在库存选项卡中选择相应的仓库（发票确认字段）。

**图** **6.16.** **选择发票库存减少的仓库**

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image084.jpg?lastModify=1769681364)

激活这些选项需要填写以下参数：

支付方式与网站的对应关系：在发票上添加银行账户信息后，选择为该发票创建关联付款，最后在所选银行账户上选择创建关联付款。

在发票上显示银行账户信息，选择为所选银行账户创建关联付款，最后选择发送发票的电子邮件模板。

**图** **6.17.** **发票管理的附加参数**

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image087.jpg?lastModify=1769681364)

# 7. 初始化数据同步

完成操作设置、数据同步设置及其方向设置后，您需要初始化同步。这将建立 Easya/Dolibarr 与 Woocommerce 数据之间的连接。建立这些连接后，即可设置[自动同步](#_bookmark59)功能。

|||
|---|---|
||![文本框: 执行时间和待同步数据量  初始化可通过手动操作（详见下文）在数次点击内完成。根据待同步数据量，您可能超过服务器允许的执行时限。此时请选择使用初始化脚本（参见第7.2节 “脚本初始化”）。](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image088.gif?lastModify=1769681364)|

### 7.1. 手动初始化

**打开工具** > WOOSYNC > 同步页面。该页面显示您商店的手动同步按钮。

**图** **7.1.** **手动同步主页**

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image090.jpg?lastModify=1769681364)

该页面显示与连接商店数量相同的同步表。每个商店同步表都有两个按钮：

• 网站详细同步：将显示启动不同元素同步的按钮，并提供多种选项。推荐使用此方法。

• 为该网站同步所有内容：将依次执行所有同步操作。不建议用于大量数据：耗时且可能导致超时。

请点击“详细网站同步”按钮。

**图7.2.详细同步按钮**

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image092.jpg?lastModify=1769681364)

### 7.2. 通过脚本初始化

### 7.3. 首次同步分类

首先需要同步的是类别。这将把商店中的所有类别作为[之前](#_bookmark24)指定类别的子类别导入到Dolibarr中。

**图** **7.3.** **从** **Woocommerce** **同步到** **Easya/Dolibarr** **的类别**

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image094.jpg?lastModify=1769681364)

点击“同步产品类别”按钮，直到出现操作成功的确认信息。

**图** **7.4.** **类别同步成功**

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image096.jpg?lastModify=1769681364)

常规使用

在您网店的运营过程中，如果需要修改类别，请从同一界面重新进行同步：处理网页链接时类别不匹配会触发错误，可能导致部分同步操作受阻。

### 7.4. 首次产品同步

初始化产品同步包括以下步骤：

• 在Easya/Dolibarr平台上创建商店现有产品。

• 将这些产品添加到各自的类别中

• 添加已设置从Wordpress向Easya/Dolibarr[同步方向](#_bookmark24)的产品数据。

使用“同步新产品”按钮（[图 7.2](#_bookmark52)）启动首次产品同步。

在 Easya/Dolibarr 中创建新产品，而不是将现有产品添加到同步类别中，取决于 Woocommerce 产品的 UGS 与 Easya/Dolibarr 中已有的产品 RÉF. 之间的匹配情况。

创建规则如下：

• Woocommerce中的单一产品将在Easya/Dolibarr中创建为_单一产品_。

• 在Easya/Dolibarr中，WooCommerce的虚拟产品（可下载）会被创建为服务。

• Woocommerce的组合产品不会在Easya/Dolibarr中同步；仅其组成产品将被同步。在订单中，如同Wordpress购物车，将列出客户所选数量的组成产品清单。

|||
|---|---|
||![文本框: Easya/Dolibarr 参考号与 Woocommerce UGS  在 Easya/Dolibarr 中创建产品或服务需要参考号，而 Woocommerce 中 UGS 是可选的。在 Easya/Dolibarr 本机模块的配置中为您的产品添加编号掩码，以避免在未来的同步中出现产品创建错误。](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image098-1769633437962-74.gif?lastModify=1769681364)|

Woosync 在产品信息表中添加了许多附加字段，用于根据同步方向收集商店的产品数据。

**图7.5. Woosync同步的产品信息表**

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image100.jpg?lastModify=1769681364)

“站点库存管理”复选框

“不与网站同步库存”复选框

原生字段“标签/类别”将填充来自商店的值。

注

我们建议激活标签/类别模块的原生参数“自动与父标签/类别关联”。该参数

在同步后将您的产品关联到树形结构中的所有类别直至根类别。此功能将应用于后续录入或同步操作。

“从电商网站移除产品”按钮表示Easya/Dolibarr产品与Woocommerce产品之间存在关联。该按钮的存在也意味着：当Easya/Dolibarr中进行任何修改时，更新信息将被发送至

Woocommerce。在某些应用场景下，点击此按钮解除关联会很有用。详见?。

隐藏附加字段

如果您不需要模块提供的附加字段，请不要删除它们，而是从产品模块配置页面的附加属性配置页面将其隐藏，方法是将它们的可见性设置为 0。

此外，为提升使用体验，您可添加折叠式分隔符类型的附加字段。

|||
|---|---|
||![文本框: 特殊情况：需发送至Woocommerce进行初始化的Easya/Dolibarr产品](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image102-1769633437970-76.gif?lastModify=1769681364)|

# 8. 同步自动化

订单同步自动化需要在Woocommerce和Easya/Dolibarr中进行设置。

### 8.1. WebHooks配置

WebHooks 在每次新订单或订单修改（仅限状态）时，都会向您的 Dolibarr 创建一个调用。Dolibarr 将处理请求存储在队列中，该队列由计划任务定期处理。这些请求包含订单和产品的创建及修改信息。

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image104.jpg?lastModify=1769681364)在 Woosync 的配置中，进入“参数”选项卡，在“WebHooks 配置”表格中生成密钥，然后点击 图标保存配置。

**图** **8.1.** **为** **Webhook** **生成密钥**

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image106.jpg?lastModify=1769681364)

ALERTE VOLUMÉTRIE 字段的值决定了当待处理的 Webhook 数量超过该数量时是否发送电子邮件。在 Easya/Dolibarr 中执行已激活的计划任务时，将识别 Webhook 的阻塞情况。

注

大量待处理的网页挂钩可能是由需要修正的错误造成的。

在Woocommerce中，打开挂钩管理页面：

**WOOCOMMERCE** > 设置，高级选项卡，网络挂钩链接。

**图8.2.** 创建网页挂钩页面**

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image109.jpg?lastModify=1769681364)

在创建网络挂钩的屏幕上，请填写：

• 名称：上下文的名称。例如：_Dolibarr_ _创建订单_；

• 状态：只有“活动”状态的网页钩子才会发送到 Easya/Dolibarr；

• 主题：从列表中选择与上述输入情境相对应的名称：_订单创建_；

• 交付URL：在此粘贴在WEBHOOKS配置表的交付URL字段中提供的地址。参见[图8.1](#_bookmark61)；

• 密钥：在此处粘贴密钥字段的值。[参见图8.1](#_bookmark61)；

• API版本：保留Woocommerce预设值。

**图8.3.创建Webhook**

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image111.jpg?lastModify=1769681364)

重复相同操作，创建同步正常运行所需的网络挂钩：

• 创建命令；

• 订单更新；

• 产品创建；

• 产品更新。

**图** **8.4.** 网络挂钩列表

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image113.jpg?lastModify=1769681364)

### 8.2. 激活订单处理计划任务

最后一步是配置计划任务，特别是自动检索WooCommerce订单的任务。

若尚未启用，请激活计划任务模块

模块并进行设置。

**图** **8.5.** 已激活的计划任务模块

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image115.jpg?lastModify=1769681364)

请根据您的 Dolibarr 操作环境，按照配置页面中的说明实施该模块，或联系您的主机服务商。请访问计划任务管理页面：**首页** > 管理工具 > 计划任务。

激活计划任务“处理所有通过Webhooks提交的订单”。根据网站流量，将其执行间隔设置为每5至15分钟或每小时一次。

**图** **8.6.** **每** **15** 分钟执行一次的计划任务

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image117.jpg?lastModify=1769681364)

### 8.3. 其他可激活的计划任务

该模块还提供了其他可根据您的使用情况激活的计划任务。

**图** **8.7.** 计划任列表

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image119.jpg?lastModify=1769681364)

• 库存更新完成：在 Dolibarr 中完成库存移动后，可用数量将根据配置中选择的仓库和同步方向发送至您的商店，具体取决于配置中选择的仓库和同步方向。

• WEBHOOKS状态检查：此计划任务会提醒您Woocommerce端webhooks的停用情况。停用webhooks将阻止订单信息发送到Easya/Dolibarr。

• WEBHOOKS 体积检查：此计划任务计划任务会在大量Webhook处于"等待处理"状态时向您发出警报，这表明存在阻塞情况。

电子邮件警报

通过电子邮件 向 发送警报 阻塞 任何 处理最后两个计划任务，通过激活常量 ECOMMERCE_NOTIFY_EMAIL_ERRORS_CHECK_WEBHOOKS_STATUS 和 ECOMMERCE_NOTIFY_EMAIL_ERRORS_CHECK_WEBHOOKS_VOLUMETRY 与

作为各自的值，通知电子邮件地址列表需用逗号分隔，以及触发警报所需的网页挂钩数量。后者取决于您的订单量及其内容。

# 9. 订单同步的简单案例

需删除章节！

# 10. 处理网页挂钩

可通过菜单链接访问网络挂钩列表：**工具**

> WOOSYNC > 网络钩子（WEBHOOKS）访问。

主页小部件

每个用户可在仪表板上显示一个网络挂钩小部件。该小部件包含直接访问"待处理"或"错误"状态网络挂钩列表的入口。

该页面按状态显示网络挂钩列表。目标是确保没有处于错误状态的网络挂钩，并将处于待处理状态的网络挂钩暂时保留：即两个计划处理任务之间的时间间隔。

错误状态的网页挂钩在修正后，需要重新设置为待处理状态。为此，请勾选错误页面中的网页挂钩，并选择批量操作“重新处理”。这些网页挂钩将出现在“待处理”列表中，直至完成处理。

常见错误：

请确认计划任务未因常量XXX的存在而被阻止。如有此情况，请勾选右侧末行并点击页面底部的按钮将其删除

等待计划任务下次执行，并从**“****主页** > 管理工具 > 计划任务”页面强制执行。

注

每次同步都会从数据库中删除超过 7 天的已处理网络挂钩信息，并将信息保存在 Dolibarr 文档目录中的 woosync_webhooks_n_v2.log 文件中，其中 n 是实体编号（如果多公司模块已激活）。

过多的数据可能会降低浏览速度。此时可通过将常量ECOMMERCE_PROCESSING_WEBHOOK_LOGS_BEFORE_X_DAYS设置为所需天数来提高Web钩子的归档频率。

# 11. 高级产品管理

### 11.1. 将简单产品转换为可变产品

在同步过程中，将简单产品转换为变体产品涉及更新一个产品并创建其他产品（其变体）。

同步将根据模块配置中定义的参数和条件进行。

### 11.2. 可变产品转换为单一产品

此用例仅涉及WooCommerce中的修改，因为在Dolibarr中，变体本身已是独立产品，并与其父级产品相关联。

母产品的销售状态将随之更新。

### 11.3. 从 Dolibarr 中删除商店产品

无论是在停止销售还是从WooCommerce中删除产品的情况下，要停止产品的同步，请在Dolibarr的产品信息卡上点击“从电子商务网站删除产品”按钮。

此操作将解除Dolibarr与WooCommerce产品之间的关联，并将其从同步类别中移除。

**图** **11.1.** **删除** **Dolibarr/Woocommerce** **关联按钮**

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image124.jpg?lastModify=1769681364)

如果某产品在多个商店销售，弹出窗口将允许您选择要删除该产品的商店。

### 11.4. 通过导入批量更新价格

Woosync支持通过导出导入功能，从Dolibarr更新商店产品的价格。

通过导出功能导出数据，可通过Dolibarr工具访问产品价格导出功能（工具 > 导出助手 > 新建导出 > 产品价格导出（Woosync））。

**图** **11.2.** 产品更新导入文件

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image126.jpg?lastModify=1769681364)

在电子表格中更新价格，然后重新保存该文件，按照 Dolibarr 的标准导入步骤（**工具** > 导入助手 > 新建导入 > 产品价格导入（Woosync））将其原样导入。

**图11.3.检查导入文件的字段**

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image128.jpg?lastModify=1769681364)

注

根据所填价格基准（不含税或含税），仅填写

MINPRICEHT 和 PRIX UNITAIRE HT 或 MINPRICETTC 和 PRIX UNITAIRE TTC。

决定了电子表格中哪些列将被处理或忽略。

注意

导入功能**仅**允许 **JOUR PRODUITS**

它不允许创建产品。

# 12. 高级库存管理

### 12.1. 使用Stock locations for Woocommerce

**12.2.** **搭配WooCommerce多地点库存管理**

# 13. 其他功能

### 13.1. 隐藏参数

在本文档中，我们介绍了可通过常量激活的隐藏参数。以下是其他一些参数：

• ECOMMERCENG_SHIPPING_CONTACT_NAME 和 ECOMMERCENG_BILLING_CONTACT_NAME：这些常量在激活后，例如在**配送地址**和**账单地址**处，可让您在Dolibarr中修改配送地址和账单地址后，将修改内容同步到WooCommerce。

注意

WooCommerce 无法向 Dolibarr 推送更新。

• ECOMMERCENG_ENABLE_SEND_FILE_TO_ORDER：将Dolibarr订单的PDF文件发送至WordPress媒体库，并附带元数据（如商品信息及其ID、WordPress链接及直接URL）。

需要正确的 Oauth2 配置。

• ECOMMERCENG_WOOCOMMERCE_DEFAULT_LANG_OTHER_COUNTRY： 添加

在Dolibarr中同步第三方时，添加除您所在公司语言之外的默认语言。将常量设置为国家代码值：fr_FR、en_US等。

• ECOMMERCENG_WOOCOMMERCE_GET_EMAIL_ON_COMPANY：将同步到 Dolibarr 的第三方电子邮件设置为 wooCommerce 客户的电子邮件。

• ECOMMERCE_WOOCOMMERCE_DEFAULT_TVA：当WooCommerce商店配置为输入含税价格时，用于计算销售价格的增值税税率。请注意，在这种情况下，Woosync中配置的导入价格类型必须为含税价格。

### 13.2. 危险区域

|||
|---|---|
||![文本框: 请注意！  本节所述功能仅适用于 高级用户使用。  此类操作不可逆转，可能造成严重后果。  在执行任何此类操作之前，请务必备份您的数据库](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image132.gif?lastModify=1769681364)|

同步页面底部显示第三个危险区域表格，其中包含显示初始化/清除/调试工具的链接。

点击该链接可查看可用选项。

**图** **13.1.** **危险区域链接**

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image134.jpg?lastModify=1769681364)

注意

这些操作是最终性的，涉及所有同步元素和数据。无法撤销。

• **删除Dolibarr与商店之间的关联记录**：商店与Dolibarr之间的关联将被删除：无需您采取任何操作，两个系统将实现独立运行。类别、客户、产品和订单将保留在各自系统中，彼此之间不再存在关联。

• **从Dolibarr中删除所有来自商店同步的数据**：此操作将从Dolibarr中删除所有通过同步操作创建的元素。所有通过同步操作在Dolibarr中创建的产品、类别、订单和客户都将被永久删除。

如果上述操作涉及所有记录，则可以断开关联，并逐项删除数据。

在同步表的行中，危险区域选项的显示链接允许您选择要解除绑定和/或删除的元素。

**图13.2. 待删除元素的详细信息**

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image137.jpg?lastModify=1769681364)

• **删除链接：**与删除Dolibarr与商店之间的链接记录操作相同（商店与Dolibarr元素之间的链接将被删除），但仅限于行中的元素：类别或产品或订单...

• **删除** **链接** **和** **Dolibarr** **链接** **记录** ： 与 操作相同，即从DOLIBARR中删除所有来自商店同步的数据 （从DOLIBARR中删除所有通过同步操作创建的元素）但仅限于行元素：类别或产品或订单...

以下情况可能需要执行这些操作：

##### • 产品重新索引的必要性

##### • **在同步方向设置发生重大变更之前或之后**

其目的是随后重新启动同步，以正确重建链接和缺失元素，从而获得完整且一致的数据。

# 14. 多语言商店

目前 Woosync 支持 [WPML](https://wpml.org/) 扩展。该扩展可管理 WooCommerce 商店产品的翻译。

要启用该扩展的支持，请将常量

ECOMMERCENG_WOOCOMMERCE_WPML_SUPPORT 设置为 **1**。

> 杂项中将常量

翻译内容不会同步回Dolibarr，仍由WooCommerce进行管理。

# 15. 集成工具

脚本！

# 16. 常见问题

### 最佳实践

本章列出了使用该模块时可能遇到的困难。您将在其中找到关于其使用的解答。

若使用本模块时遇到以下未描述的其他错误：

1. 请先停用该模块，然后重新启用；
    
2. 在ChangeLog中查看是否有新版本发布，并确认其与您使用的Dolibarr版本兼容；
    
3. 重新安装/更新模块；
    
4. 最后检查是否存在与其他模块的不兼容情况。如有不兼容，请遵循我们的建议。
    

如果经过上述操作后错误仍然存在，请通过我们的[支持外联网](https://link.easya.solutions/support)联系我们。为提高处理效率，请注明：

• _模块_名称和版本；

• _Dolibarr_版本；

• _已激活_的附加模块列表；

• 以及处理您的请求所需的所有必要信息：背景、重现错误的步骤、屏幕截图等。

#### 获取令牌时出错：'unauthorized_client'：'此客户端ID未获授权类型'

您的 Oauth 令牌已失效。请进入模块配置界面生成新令牌。

#### 未找到与“银行转账”对应的付款方式订单同步过程中出现错误

两个解决方案的支付方式之间缺少对应关系。在模块设置中，请填写对应字段。

![img](file:///W:/Document/Github/otxtdb/txtdb/_images/clip_image135.gif?lastModify=1769681364)

#### 从网站 '404: Error: ID 无效。[woocommerce_rest_product_variation_invalid_id]' 检索远程产品 'id:boutique_wordpress' 时出错

Dolibarr无法为某产品建立两个解决方案之间的关联。这可能是由于从商店中删除了产品或删除了变体所致。请在Dolibarr中找到对应产品，并从其信息页中将该产品移出商店。

此错误可能在同步过程中或在 Dolibarr 中保存产品修改时出现。