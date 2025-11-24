Dolibarr ERP & CRM 开源网络套件的 Docker 镜像。

Dolibarr 是一个现代软件包，用于管理您组织的活动（联系人、报价、发票、订单、库存、日程、人力资源、费用报告、会计、电子内容管理系统、制造业等）。

> [更多信息 ⁠](https://github.com/dolibarr/dolibarr)

#### Docker 上可用的版本/标签

参见 https://hub.docker.com/r/dolibarr/dolibarr/tags

*非常旧的 Dolibarr 版本可能不会在 Docker Hub 上更新，但您始终可以从 Dolibarr 官方网站获取标准 zip 包*

#### 支持的架构

Linux x86-64 (`amd64`) 和 ARMv8 64 位 (`arm64v8`)。

#### 如何运行这个镜像？

这个镜像基于官方的 [PHP 仓库](https://hub.docker.com/_/php/)和官方的 [Dolibarr 仓库 ⁠](https://github.com/Dolibarr/dolibarr)。它使用保存在 [Dolibarr Docker 构建仓库 ⁠](https://github.com/Dolibarr/dolibarr-docker) 中的工具构建。

这个镜像不包含数据库，因此您需要将其与数据库容器连接。让我们看看如何使用 [Docker Compose⁠](https://docs.docker.com/compose/) 将其与 [MariaDB](https://hub.docker.com/_/mariadb/)（如果您更喜欢，也可以使用 [MySQL](https://hub.docker.com/_/mysql/)）集成：

如果您希望在重启或升级后保留数据库和 Dolibarr 数据文件，您必须在主机上首先创建用于存储持久化文件的目录 `/home/dolibarr_mariadb`、`/home/dolibarr_documents` 和 `/home/dolibarr_custom`，分别用于数据库、Dolibarr 文档文件和已安装的外部 Dolibarr 模块。

```
mkdir /home/dolibarr_mariadb /home/dolibarr_documents /home/dolibarr_custom;
```

然后，创建一个 `docker-compose.yml` 文件，如下所示：

```yaml
# Edit this file then run 
# docker-compose up -d
# docker-compose logs

services:
    mariadb:
        image: mariadb:latest
        environment:
            MYSQL_ROOT_PASSWORD: ${MYSQL_ROOT_PASSWORD:-root}
            MYSQL_DATABASE: ${MYSQL_DATABASE:-dolidb}
            MYSQL_USER: ${MYSQL_USER:-dolidbuser}
            MYSQL_PASSWORD: ${MYSQL_PASSWORD:-dolidbpass}

        volumes:
            - /home/dolibarr_mariadb:/var/lib/mysql

    web:
        # Choose the version of image to install
        # dolibarr/dolibarr:latest (the latest stable version)
        # dolibarr/dolibarr:develop
        # dolibarr/dolibarr:x.y.z
        image: dolibarr/dolibarr:latest
        environment:
            DOLI_INIT_DEMO: ${DOLI_INIT_DEMO:-0}
            DOLI_DB_HOST: ${DOLI_DB_HOST:-mariadb}
            DOLI_DB_NAME: ${DOLI_DB_NAME:-dolidb}
            DOLI_DB_USER: ${DOLI_DB_USER:-dolidbuser}
            DOLI_DB_PASSWORD: ${DOLI_DB_PASSWORD:-dolidbpass}
            DOLI_URL_ROOT: "${DOLI_URL_ROOT:-http://0.0.0.0}"
            DOLI_ADMIN_LOGIN: "${DOLI_ADMIN_LOGIN:-admin}"
            DOLI_ADMIN_PASSWORD: "${DOLI_ADMIN_PASSWORD:-admin}"
            DOLI_CRON: ${DOLI_CRON:-0}
            DOLI_CRON_KEY: ${DOLI_CRON_KEY:-mycronsecurekey}
            DOLI_COMPANY_NAME: ${DOLI_COMPANY_NAME:-MyBigCompany}
            WWW_USER_ID: ${WWW_USER_ID:-1000}
            WWW_GROUP_ID: ${WWW_GROUP_ID:-1000}

        ports:
            - "80:80"
        links:
            - mariadb
        volumes:
            - /home/dolibarr_documents:/var/www/documents
            - /home/dolibarr_custom:/var/www/html/custom
```

然后构建并运行所有服务（-d 是用于在后台运行）。

```
sudo docker-compose up -d
```

如果"docker-compose"命令不可用，你可以将其替换为"docker compose"命令。

你可以验证 Web 和 MariaDB 容器是否已启动，并使用以下命令查看日志：

```
sudo docker-compose ps
sudo docker-compose logs
```

一旦日志显示启动完成（你应该会看到消息"你可以连接到你的 Dolibarr Web 应用程序..."），请访问 [http://0.0.0.0⁠](http://0.0.0.0/) 来访问新的 Dolibarr 安装，首次管理员登录用户名是 admin/admin（如果你之前没有在docker-compose.yml文件中更改默认值）。

注意：如果主机端口 80 已被使用，可以将"80:80"替换为"xx:80"，其中 xx 是主机上的一个空闲端口编号。您将能够通过 URL [http://0.0.0.0:xx⁠](http://0.0.0.0:xx/) 访问 Dolibarr

其他示例：

您可以在 `examples` 目录中找到其他关于docker-compose.yml文件的增强使用示例，例如：

- [使用 cron 运行 Dolibarr（用于计划任务模块）⁠](https://github.com/Dolibarr/dolibarr-docker/tree/main/examples/with-cron/)
- [使用 letsencrypt 证书运行 Dolibarr⁠](https://github.com/Dolibarr/dolibarr-docker/tree/main/examples/with-certbot/)
- [使用 mysql 服务器运行 Dolibarr⁠](https://github.com/Dolibarr/dolibarr-docker/tree/main/examples/with-mysql/)
- [使用 Traefik 反向代理运行 Dolibarr⁠](https://github.com/Dolibarr/dolibarr-docker/tree/main/examples/with-rp-traefik/)
- [使用 secrets 运行 Dolibarr⁠](https://github.com/Dolibarr/dolibarr-docker/tree/main/examples/with-secrets/)

#### 升级 Dolibarr 版本并迁移数据库

警告：只有在持久化目录中存储的数据（请参阅你的docker-compose.yml中的“volumes”部分）在容器升级后不会丢失。

使用以下方法之一删除位于容器卷 `/var/www/documents` 内的 `install.lock` 文件：

```
sudo docker exec nameofwebcontainer bash -c "rm -f /var/www/documents/install.lock"
```

或

```
sudo docker exec -it nameofwebcontainer bash
rm -f /var/www/documents/install.lock; exit
```

或如果文档目录已设置为持久化目录，可以从主机进行操作：

```
rm -f /home/dolibarr_documents/install.lock
```

然后下载容器更新版本并重启它们。

```
sudo docker-compose pull
sudo docker-compose up -d
sudo docker-compose logs
```

确保在docker-compose.yml中设置 env `DOLI_INSTALL_AUTO` 为 `1`，以便它将数据库迁移到新版本，或者你可以选择通过调用/install 页面通过 Web 界面以标准方式升级 Dolibarr。

#### 环境变量概览

您可以使用以下变量来更好地自定义您的 docker-compose 文件。

| 变量                            | 默认值                                  | 描述                                                         |
| :------------------------------ | :-------------------------------------- | :----------------------------------------------------------- |
| **DOLI_INSTALL_AUTO**           | *1*                                     | 1: 安装将在 docker 首次启动时完成                            |
| **DOLI_INIT_DEMO**              | *0*                                     | 1: 安装时也会在 docker 首次启动时加载演示数据                |
| **DOLI_PROD**                   | *1*                                     | 1: Dolibarr 将以生产模式运行                                 |
| **DOLI_INSTANCE_UNIQUE_ID**     |                                         | 用作某些加密的盐/密钥的 Secret ID。默认情况下，在创建 docker 容器时随机设置。 |
| **DOLI_DB_TYPE**                | *mysqli*                                | 数据库服务器的类型（**mysqli**，pgsql）                      |
| **DOLI_DB_HOST**                | *mariadb*                               | MariaDB/MySQL 服务器的主机名                                 |
| **DOLI_DB_HOST_PORT**           | *3306*                                  | MariaDB/MySQL 服务器的端口号                                 |
| **DOLI_DB_NAME**                | *dolidb*                                | 数据库名称                                                   |
| **DOLI_DB_USER**                | *dolidbuser*                            | 数据库用户                                                   |
| **DOLI_DB_PASSWORD**            | *dolidbpass*                            | 数据库用户的密码                                             |
| **DOLI_DB_SSL**                 | *false*                                 | 启用加密数据库连接（需要 MySQL 和 Dolibarr >v19）            |
| **DOLI_URL_ROOT**               | *[http://localhost⁠](http://localhost/)* | Dolibarr 安装的 URL 根目录                                   |
| **DOLI_ADMIN_LOGIN**            | *管理员*                                | 首次启动时创建的管理员登录名                                 |
| **DOLI_ADMIN_PASSWORD**         | *admin*                                 | 管理员首次启动时创建的初始密码                               |
| **DOLI_ENABLE_MODULES**         |                                         | 以逗号分隔的要在安装时激活的模块列表。modUser 将始终被激活。（例如：`Societe,Facture,Stock`）。如果未设置 DOLI_COMPANY_NAME 和 DOLI_COMPANY_COUNTRYCODE，模块可能无法正确激活 |
| **DOLI_COMPANY_NAME**           |                                         | 在容器初始化时设置 Dolibarr 的公司名称                       |
| **DOLI_COMPANY_COUNTRYCODE**    |                                         | 在容器初始化时设置公司和 Dolibarr 国家。需要类似"FR"、"GB"、"US"等两字母代码 |
| **DOLI_AUTH**                   | *dolibarr*                              | 哪种方法用于连接用户，切换到 `ldap` 或 `ldap, dolibarr` 以使用 LDAP |
| **DOLI_LDAP_HOST**              | *127.0.0.1*                             | LDAP 服务器的地址                                            |
| **DOLI_LDAP_PORT**              | *389*                                   | LDAP 服务器的端口                                            |
| **DOLI_LDAP_VERSION**           | *3*                                     | 要使用的 LDAP 版本                                           |
| **DOLI_LDAP_SERVER_TYPE**       | *openldap*                              | LDAP 服务器的类型（openLDAP、Active Directory、eGroupWare）  |
| **DOLI_LDAP_LOGIN_ATTRIBUTE**   | *uid*                                   | 用于绑定用户的属性                                           |
| **DOLI_LDAP_DN**                | *ou=users,dc=my-domain,dc=com*          | 查找用户的基准                                               |
| **DOLI_LDAP_FILTER**            |                                         | 授权用户连接的过滤器                                         |
| **DOLI_LDAP_BIND_DN**           |                                         | 具有读取权限的用户的全名                                     |
| **DOLI_LDAP_BIND_PASS**         |                                         | 绑定用户的密码                                               |
| **DOLI_LDAP_DEBUG**             | *false*                                 | 激活调试模式                                                 |
| **DOLI_CRON**                   | *0*                                     | 1: 启用 cron 服务                                            |
| **DOLI_CRON_KEY**               |                                         | 启动 cron 作业的安全密钥                                     |
| **DOLI_CRON_USER**              |                                         | 用于启动 cron 作业的 Dolibarr 用户（如果未定义，将使用 firstadmin） |
| **WWW_USER_ID**                 |                                         | www-data 用户的 ID。如果留空，ID 不会改变。在开发过程中，将主机用户的相同 ID 设置进来非常实用。 |
| **WWW_GROUP_ID**                |                                         | www-data 组的 ID。如果留空，ID 不会改变。                    |
| **PHP_INI_DATE_TIMEZONE**       | *UTC*                                   | PHP 的默认时区                                               |
| **PHP_INI_MEMORY_LIMIT**        | *256M*                                  | PHP 内存限制                                                 |
| **PHP_INI_UPLOAD_MAX_FILESIZE** | *2M*                                    | PHP 上传文件的最大允许大小                                   |
| **PHP_INI_POST_MAX_SIZE**       | *8M*                                    | PHP PHP 接受的 POST 数据最大大小。                           |
| **PHP_INI_ALLOW_URL_FOPEN**     | *0*                                     | 允许 URL 感知的 fopen 包装器                                 |

某些环境变量与 docker secrets 行为兼容，只需在变量名后添加 `_FILE` 后缀，并将值文件指向读取位置。与 docker secrets 兼容的环境变量：

- `DOLI_INSTANCE_UNIQUE_ID` => `DOLI_INSTANCE_UNIQUE_ID_FILE`
- `DOLI_DB_USER` => `DOLI_DB_USER_FILE`
- `DOLI_DB_PASSWORD` => `DOLI_DB_PASSWORD_FILE`
- `DOLI_ADMIN_LOGIN` => `DOLI_ADMIN_LOGIN_FILE`
- `DOLI_ADMIN_PASSWORD` => `DOLI_ADMIN_PASSWORD_FILE`
- `DOLI_CRON_KEY` => `DOLI_CRON_KEY_FILE`
- `DOLI_CRON_USER` => `DOLI_CRON_USER_FILE`

#### 高级设置

##### 添加部署后和启动前的脚本

通过挂载卷，可以在部署结束时或启动 Apache 之前执行 `*.sh`、`*.sql` 和/或 `*.php` 自定义文件。要在部署期间执行脚本，请挂载卷到 `/var/www/scripts/docker-init.d` ；要在 Apache 启动前执行脚本，请挂载卷到 `/var/www/scripts/before-starting.d` 。

```bash
\docker-init.d
|- custom_script.sql
|- custom_script.php
|- custom_script.sh
```

使用 compose 文件挂载卷：

```yaml
services:
    mariadb:
        image: mariadb:latest
        environment:
            MYSQL_ROOT_PASSWORD: ${MYSQL_ROOT_PASSWORD:-root}
            MYSQL_DATABASE: ${MYSQL_DATABASE:-dolidb}
            MYSQL_USER: ${MYSQL_USER:-dolidbuser}
            MYSQL_PASSWORD: ${MYSQL_PASSWORD:-dolidbpass}

    web:
        # Choose the version of image to install
        # dolibarr/dolibarr:latest (the latest stable version)
        # dolibarr/dolibarr:develop
        # dolibarr/dolibarr:x.y.z
        image: dolibarr/dolibarr
        environment:
            DOLI_INIT_DEMO: ${DOLI_INIT_DEMO:-0}
            DOLI_DB_HOST: ${DOLI_DB_HOST:-mariadb}
            DOLI_DB_NAME: ${DOLI_DB_NAME:-dolidb}
            DOLI_DB_USER: ${DOLI_DB_USER:-dolidbuser}
            DOLI_DB_PASSWORD: ${DOLI_DB_PASSWORD:-dolidbpass}
            DOLI_URL_ROOT: "${DOLI_URL_ROOT:-http://0.0.0.0}"
            DOLI_ADMIN_LOGIN: "${DOLI_ADMIN_LOGIN:-admin}"
            DOLI_ADMIN_PASSWORD: "${DOLI_ADMIN_PASSWORD:-admin}"
            DOLI_CRON: ${DOLI_CRON:-0}
            DOLI_CRON_KEY: ${DOLI_CRON_KEY:-mycronsecurekey}
            WWW_USER_ID: ${WWW_USER_ID:-1000}
            WWW_GROUP_ID: ${WWW_GROUP_ID:-1000}
        volumes :
          - volume-scripts:/var/www/scripts/docker-init.d
          - before-starting-scripts:/var/www/scripts/before-starting.d
        ports:
            - "80:80"
        links:
            - mariadb
```

##### 调整 apache 配置以适应你的需求

###### 服务器名称

如果你在容器内运行 apache2ctl configtest，你可能会得到类似以下的消息：

> AH00558: apache2: 无法可靠地确定服务器的完全限定域名，使用 x.y.z.w 设置全局的 'ServerName' 指令以抑制此消息

简单修复，创建一个单独的文本文件

内容："ServerName dolibarr.example.com"

挂载点："/etc/apache2/conf-enabled/servername.conf"

只读：是，以:ro 方式挂载它

###### 你的 dolibarr 在代理后面运行吗？

如果你希望 Dolibarr 或来自 dolibarr 容器的日志显示原始 IP 地址而不是仅显示代理的 IP 地址，你应该创建两个文本文件：

*remoteip.load* 这个文件将加载 apache 模块 remoteip [https://httpd.apache.org/docs/current/mod/mod_remoteip.html⁠](https://httpd.apache.org/docs/current/mod/mod_remoteip.html)

内容："LoadModule remoteip_module /usr/lib/apache2/modules/mod_remoteip.so"

挂载点："/etc/apache2/mods-enabled/remoteip.load"

只读：是，使用:ro 以只读方式挂载它

*remoteip.conf* 此文件将包含 remoteip 的配置，并且应该以只读方式在容器内部挂载。内容将取决于您的代理以及它使用的哪种类型的头部。您或许还可以启用代理协议，更多内容请查看 [https://httpd.apache.org/docs/current/mod/mod_remoteip.html⁠](https://httpd.apache.org/docs/current/mod/mod_remoteip.html)

示例内容："RemoteIPHeader X-Forwarded-For"

挂载点: "/etc/apache2/mods-enabled/remoteip.conf"

##### 支持 PostgreSQL

将 `DOLI_DB_TYPE` 设置为 `pgsql` 可以使 Dolibarr 使用 PostgreSQL 数据库运行。当设置为使用 `pgsql` 时，Dolibarr 必须在首次执行时手动安装：

- 访问 `http://0.0.0.0/install`；
- 按照安装设置进行操作；
- 在容器卷 `install.lock` 中添加（例如 `docker-compose exec services-data_dolibarr_1 /bin/bash -c "touch /var/www/html/documents/install.lock"` ）。

以这种方式设置时，升级版本必须使用网页界面：

- 删除 `install.lock` 文件（例如 `docker-compose exec services-data_dolibarr_1 /bin/bash -c "rm -f /var/www/html/documents/install.lock"` ）。
- 浏览到 `http://0.0.0.0/install`；
- 升级数据库；
- 在容器卷 `install.lock` 中添加 `/var/www/html/documents`（例如 `docker-compose exec services-data_dolibarr_1 /bin/bash -c "touch /var/www/html/documents/install.lock"` ）。

#### 故障排除

如果在 docker-compose 过程中出现错误"urllib3.exceptions.URLSchemeUnknown: 不支持的 URL 方案 http+docker"，尝试升级或降级 pip 包：pip install requests==2.31.0