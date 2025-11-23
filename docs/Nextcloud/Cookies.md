# Cookies[](https://docs.nextcloud.com/server/latest/admin_manual/gdpr/cookies.html#cookies)

Nextcloud 仅存储其正常运行所需的 cookie。所有 cookie 都直接来自您的 Nextcloud 服务器，不会向您的系统发送任何第三方 cookie。关于 GDPR，[ 仅包含个人数据的数据才相关 ](https://gdpr-info.eu/recitals/no-26/)。

## Nextcloud 存储的 Cookies[](https://docs.nextcloud.com/server/latest/admin_manual/gdpr/cookies.html#cookies-stored-by-nextcloud)

| Cookie        | 存储的数据                                                   | 有效期         |
| ------------- | ------------------------------------------------------------ | -------------- |
| 会话 cookie   | 会话 ID密钥令牌（用于在服务器上解密会话）                    | 24分钟         |
| 同站 Cookies  | 不存储与用户相关的数据，所有同站 Cookies 对所有 Nextcloud 实例中的用户都相同 | 永远           |
| 记住我 Cookie | 用户 ID原始会话 ID记住令牌                                   | 15天（可配置） |

同站点 Cookie 用于确定请求如何到达 Nextcloud 服务器。我们使用它们来防止 CSRF 攻击。这些 Cookie 中不存储任何可识别的信息。其余的 Cookie 严格用于系统识别用户。