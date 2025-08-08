
为您的域名创建自定义电子邮件地址，并将收到的电子邮件路由到您首选的邮箱。

适用于所有计划

Cloudflare Email Routing 旨在简化创建和管理电子邮件地址的方式，无需时刻关注额外的邮件收件箱。使用 Email Routing，您可以在不需要共享主要电子邮件地址的情况下创建任意数量的自定义电子邮件地址，例如订阅新服务或新闻通讯时。电子邮件将被路由到您首选的电子邮件收件箱，而您永远不必暴露主要电子邮件地址。

Email Routing 设计为免费且私密。Cloudflare 不会存储或访问路由到您收件箱的电子邮件。

它适用于所有使用 Cloudflare 作为权威域名服务器的 Cloudflare 客户 [的客户](https://developers.cloudflare.com/dns/zone-setups/full-setup/) 。

---

## 功能

[](https://developers.cloudflare.com/email-routing/#features)

### Email Workers

利用 Cloudflare Workers 的强大功能来实现处理邮件所需的任何逻辑。您可以创建任意复杂度或简单度的规则。

[使用 Email Workers](https://developers.cloudflare.com/email-routing/email-workers/)

### 自定义地址

通过邮件路由，您可以为特定情况使用多个自定义邮件地址。

[使用自定义地址](https://developers.cloudflare.com/email-routing/get-started/enable-email-routing/)

### 分析

邮件路由包含指标，帮助您检查邮件流量历史。

[使用分析](https://developers.cloudflare.com/email-routing/get-started/email-routing-analytics/)

---

## 相关产品

[](https://developers.cloudflare.com/email-routing/#related-products)

**[电子邮件安全](https://developers.cloudflare.com/cloudflare-one/email-security/)**

Cloudflare 电子邮件安全是一款基于云的服务，能够阻止通过所有流量渠道（电子邮件、网络和网页）发起的钓鱼攻击，这是最大的网络安全威胁。

**[DNS](https://developers.cloudflare.com/dns/)**

Email Routing 仅适用于使用 Cloudflare 作为权威域名服务器的客户。



# 入门指南

要启用电子邮件路由，首先需要创建一个与目标地址或电子邮件工作者关联的自定义电子邮件地址。这形成了一个**电子邮件规则** 。您可以在 Cloudflare 管理面板中启用或禁用规则。有关更多详细信息，请参阅[启用电子邮件路由](https://developers.cloudflare.com/email-routing/get-started/enable-email-routing) 。

使用电子邮件路由创建的自定义地址仅作为转发地址。发送到自定义地址的电子邮件将由电子邮件路由转发到您的目标收件箱。Cloudflare 不处理出站电子邮件，也没有 SMTP 服务器。

首次访问电子邮件路由时，您将看到一个向导，引导您创建电子邮件规则的过程。您可以跳过向导，手动添加规则。

如果需要暂停电子邮件路由或迁移到另一个服务，请参阅[禁用电子邮件路由](https://developers.cloudflare.com/email-routing/setup/disable-email-routing/) 。

- [启用邮件路由](https://developers.cloudflare.com/email-routing/get-started/enable-email-routing/)
- [测试邮件路由](https://developers.cloudflare.com/email-routing/get-started/test-email-routing/)
- [分析](https://developers.cloudflare.com/email-routing/get-started/email-routing-analytics/)
- [审核日志](https://developers.cloudflare.com/email-routing/get-started/audit-logs/)




