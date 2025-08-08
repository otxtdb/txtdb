# 欢迎来到 Stalwart

欢迎来到 **Stalwart**，一个为现代互联网设计的开源邮件和协作服务器。Stalwart 支持多种协议，包括 **JMAP**、**IMAP4**、**POP3**、**SMTP**、**CalDAV**、**CardDAV** 和 **WebDAV**，使其成为一个全面的解决方案，用于管理电子邮件、日历、联系人、文件存储等。Stalwart 用 **Rust** 编写，旨在使其安全、快速、稳健且可扩展，能够从小型个人邮件服务器到大型分布式企业部署，无所不能。

本 **入门指南** 旨在帮助新用户安装、配置和优化 Stalwart，以满足其特定需求。它将引导您完成成功部署所需的基本步骤和考虑因素。

我们从[系统要求](https://stalw.art/docs/install/requirements)概览开始，了解内存和 CPU 使用量随服务器负载变化的情况，并学习如何相应地配置系统。 [安装指南](https://stalw.art/docs/category/installation)提供了在您选择的平台上安装 Stalwart 的步骤，包括配置细节。

接下来，我们将探讨如何[选择合适的数据库](https://stalw.art/docs/install/store) ，解释 Stalwart 的模块化存储架构，并学习如何将不同的存储后端与它们管理的数据匹配。您还将了解如何选择一个内部或外部的目录，用于处理用户身份验证和账户管理。

一旦服务器配置完成，正确的 [DNS 设置](https://stalw.art/docs/install/dns)对于确保安全可靠的邮件传递和客户端连接至关重要。本节将解释所有所需的 DNS 记录，包括 SPF、DKIM、DMARC、MTA-STS 等。

为了确保您的部署保持安全，我们在[服务器安全](https://stalw.art/docs/install/security)部分涵盖了多项最佳实践。这包括禁用未使用的端口、配置 HTTP 访问控制以及实施明确的管理角色，以降低风险并保持操作的完整性。

最后，对于大型或高流量环境， [性能调优](https://stalw.art/docs/install/performance)部分提供了关于缓存和并发设置的指导，帮助您在苛刻的条件下从服务器中获得最佳性能。

无论您是运行单节点配置还是计划分布式部署，本指南都将帮助您高效且安全地启动和运行 Stalwart。让我们开始吧。

# 系统要求

Stalwart 是一款高性能的邮件和协作服务器，设计上能够从小型个人部署高效扩展到大型企业环境。其资源需求，尤其是内存和 CPU 的需求，高度依赖于使用模式，包括并发连接的数量和客户端活动的强度。本文件提供了估算和管理内存和 CPU 需求的指导，以确保在不同部署场景中实现最佳性能。

## 内存使用情况[​](https://stalw.art/docs/install/requirements#memory-usage "Direct link to Memory Usage")

Stalwart 在内存使用方面设计得非常高效和轻量。在空闲状态下，它保持大约 **100MB** 的低内存占用，使其适合轻量级环境和资源受限的系统。然而，实际内存消耗会根据并发连接的总数和服务器的整体活动量而有所不同。

对于仅服务 5 到 10 名用户的较小部署，具有 1GB 内存的系统通常足以舒适地运行 Stalwart。相比之下，处理数千个并发连接的高流量服务器——尤其是在企业环境中运行的服务器——需要更多的内存以保持性能和响应性。

管理员可以通过几个可配置参数来管理和限制 Stalwart 的内存使用。一个主要的控制机制是服务器接受的并发连接数限制。默认情况下，Stalwart 在其所有服务（包括 IMAP、JMAP、WebDAV、SMTP 和 POP3）之间共享最多 8192 个并发连接。降低这个数字可以在资源受限的环境中帮助降低内存需求。

另一个影响内存使用的关键因素是缓存。Stalwart 使用了多个缓存来优化性能，每个缓存都可以进行精细调整或限制大小。调整这些缓存的大小提供了另一种控制服务器内存消耗的方法，取决于所需的性能与资源使用之间的平衡。

## CPU 需求[​](https://stalw.art/docs/install/requirements#cpu-requirements "Direct link to CPU Requirements")

Stalwart 的 CPU 使用量会根据用户数量、邮件流量以及在支持协议上同时进行的操作强度进行调整。对于低流量设置——通常涉及大约五名用户——通常只需要一个 CPU 核心就可以处理常规操作而不会影响性能。

要估算更大或更动态环境的 CPU 需求，可以采用以下方法：首先评估高峰时段预期的并发连接数，然后评估用户最常执行的操作类型（例如，通过 IMAP 进行复杂的搜索、通过 JMAP 进行同步，或通过 SMTP 进行大量的邮件投递）。这些活动消耗 CPU 资源的方式各不相同，而整体的工作负载应指导核心数的分配。一般来说，随着并发性和活动的增加，为了保持低延迟和高吞吐量，需要更多的 CPU 核心。

部署后监控实际服务器性能也是有帮助的，这可以允许根据实际需求精细调整和扩展资源，而不是基于估计的使用量。



# Linux / MacOS

要在 Linux 或 MacOS 上安装 Stalwart，请在终端中执行以下命令：

```bash
$ curl --proto '=https' --tlsv1.2 -sSf https://get.stalw.art/install.sh -o install.sh
```



然后以 root 用户执行安装脚本。默认安装目录为 /opt/stalwart。如果你想在其他目录安装 Stalwart，可以在安装脚本中指定安装目录作为参数：

```bash
$ sudo sh install.sh /path/to/install
```



如果你计划使用 FoundationDB 作为后端，可以在安装脚本中添加 --fdb 参数以下载带有 FoundationDB 支持的版本。

### 登录 Web 界面[](https://stalw.art/docs/install/platform/linux/#log-in-to-the-web-interface)

安装完成后，安装脚本会打印出管理员账户和密码：

```bash
$ sudo sh install.sh
✅ Configuration file written to /opt/stalwart/etc/config.toml
🔑 Your administrator account is 'admin' with password 'w95Yuiu36E'.
🎉 Installation complete! Continue the setup at http://yourserver.org:8080/login
```



有了这些信息，您可以在 `http://yourserver.org:8080/login` 登录到 Web 界面。

### 选择数据存储位置[](https://stalw.art/docs/install/platform/linux/#choose-where-to-store-your-data)

登录后，请转到 `Settings` > `Storage` 部分，并配置您的[数据 ](https://stalw.art/docs/storage/data)、[blob](https://stalw.art/docs/storage/blob)、[ 全文](https://stalw.art/docs/storage/fts)和[内存](https://stalw.art/docs/storage/in-memory)存储。阅读[选择数据库](https://stalw.art/docs/install/store)部分以获取更多可用选项的详细信息。

如果您需要外部身份验证目录，例如 [LDAP](https://stalw.art/docs/auth/backend/ldap) 或 [SQL](https://stalw.art/docs/auth/backend/sql)，请转到 `Settings` > `Authentication` 部分，并配置您的[身份验证后端 ](https://stalw.art/docs/install/directory)。

选填

Stalwart 预配置了 `RocksDB` 作为所有存储的默认后端。如果您对默认配置满意，可以跳过此步骤。

### 配置主机名和域名[](https://stalw.art/docs/install/platform/linux/#configure-your-hostname-and-domain)

接下来，请确保 `Settings` > `Server` > `Network` 中的服务器主机名是正确的。然后，在 `Management` > `Directory` > `Domains` 中添加您的主要域名。创建域名后，界面会显示您需要添加到域名 DNS 设置中的 DNS 记录。

例如：

```txt
MX  example.org.                      10 mail.example.org.
TXT 202404e._domainkey.example.org.   v=DKIM1; k=ed25519; h=sha256; p=MCowBQYDK2VwAyEAOT2JN9F8SLTVFNEODDu22SD9RJDC282mugCAeXkzjH0=
TXT 202404r._domainkey.example.org.   v=DKIM1; k=rsa; h=sha256; p=MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAykeYJjv5N0AlnJ8gKF+/8qjbStiMFWvPg+p3JPh96GPXEN6l9W/Ee6Lag6i3vLyTVH5dnRVRBhfWhc+Dc0nKreZe4f5i4L5M4RI31+RpEgu4bCmncUIk2WzJgGBW5XbiOwXjge6OKWtJQN9d8Lc1AuryL5xeged9iS6xd/+EJz4WxAf18U+j38xmAm8fJUTBnQVeb/AZup+voSKAS59jyumsb0jQtXfX5xnwTFXdiX2OF8LRrmmNs/ObHozgHftxAv+YCiSU4bqSlKNPQIrN5kk1YnZDnLlc1Gr66AWlmdUVE7PWtZPTy4f8+uHO93EW3WUxLmynZm+Syn9FTJC2uwIDAQAB
TXT mail.example.org.                 v=spf1 a -all ra=postmaster
TXT example.org.                      v=spf1 mx -all ra=postmaster
TXT _dmarc.example.org.               v=DMARC1; p=reject; rua=mailto:postmaster@example.org; ruf=mailto:postmaster@example.org
```



提示

部分自动生成的记录可能是可选的，具体取决于您的设置，请参阅[设置 DNS](https://stalw.art/docs/install/dns) 部分以获取更多信息。

### 启用 TLS[](https://stalw.art/docs/install/platform/linux/#enable-tls)

Stalwart 要求使用有效的 TLS 证书来确保服务器与客户端之间的连接安全。您可以通过以下方式之一启用 TLS：

- 如果您已经为服务器拥有 TLS 证书，可以在 `Settings` > `Server` > `TLS` > `Certificates` 部分上传它。
- 如果没有证书，您可以使用 [ACME](https://stalw.art/docs/server/tls/acme/overview) 从 Let's Encrypt 启用自动 TLS 证书。要启用 ACME，请前往 `Settings` > `Server` > `TLS` > `ACME Providers` 部分，并将 Let's Encrypt 添加为您的 ACME 提供商，确保您的服务器主机名被列为其中一个主体名称。Stalwart 支持 `tls-alpn-01`、`dns-01` 和 `http-01` 挑战。如果您不确定使用哪种挑战，请阅读 [ACME 挑战类型 ](https://stalw.art/docs/server/tls/acme/challenges)文档。
- 如果您在 Traefik、Caddy、HAProxy 或 NGINX 等反向代理后面运行 Stalwart，应跳过此步骤，并在反向代理中配置 TLS。

### 重启服务[](https://stalw.art/docs/install/platform/linux/#restart-service)

完成设置说明后，请重启 Stalwart：

```bash
$ sudo systemctl restart stalwart
```



或者，如果你使用的是 MacOS：

```bash
$ sudo launchctl kickstart -k stalwart.mail
```



### 下一步[](https://stalw.art/docs/install/platform/linux/#next-steps)

如果你选择了使用内部目录，现在可以在“管理” > “目录” > “账户”部分添加用户。如果你选择了外部目录，你需要在目录服务器中创建用户。

如果一切顺利，你的用户现在应该能够连接到服务器并发送和接收邮件。如果你无法连接到服务器，请检查 web-admin 的日志文件或目录安装路径下的<INSTALL_DIR>/logs，查看是否有任何错误。

如果遇到任何问题，请参阅[故障排除](https://stalw.art/docs/management/troubleshoot)部分获取帮助。如果您有疑问，请查看[常见问题](https://stalw.art/docs/faq)部分，或在[社区论坛](https://github.com/stalwartlabs/stalwart/discussions)发帖讨论。

提示

在使服务器对外公开之前，请务必阅读[确保服务器安全](https://stalw.art/docs/install/security)部分。

### 安装演示[](https://stalw.art/docs/install/platform/linux/#setup-demonstration)

![[_images/1b01ccb8ea8b9f616463abe3c8ddc684_MD5.gif]]



# Windows

要在 Windows 上安装 Stalwart，请下载 [最新版本 ](https://github.com/stalwartlabs/stalwart/releases/latest/)的 `stalwart` 包。然后，通过运行 `stalwart.exe` 可执行文件初始化安装目录：

```powershell
C:\Downloads> stalwart.exe --init "C:\Program Files\Stalwart"
```



然后，将 `stalwart.exe` 可执行文件移动到安装目录：

```powershell
C:\Downloads> mkdir "C:\Program Files\Stalwart\bin"
C:\Downloads> move stalwart.exe "C:\Program Files\Stalwart\bin"
```



### 启动服务[](https://stalw.art/docs/install/platform/windows#start-service)

要将 Stalwart 作为服务运行，请遵循这些步骤：

- 下载 [NSSM](http://nssm.cc/download) 服务管理器。

- 在终端中运行：

  ```text
  nssm install Stalwart_Mail
  ```

  

- 一旦出现 NSSM 图形界面，使用以下参数配置服务：

  ```text
  Path: C:\Program Files\Stalwart\bin\stalwart.exe
  Startup directory: C:\Program Files\Stalwart
  Arguments: --config="C:\Program Files\Stalwart\etc\config.toml"
  ```

  

- 点击安装服务按钮。

### 登录 Web 界面[](https://stalw.art/docs/install/platform/windows#log-in-to-the-web-interface)

安装完成后，安装脚本会打印出管理员账户和密码：

```bash
$ sudo sh install.sh
✅ Configuration file written to /opt/stalwart/etc/config.toml
🔑 Your administrator account is 'admin' with password 'w95Yuiu36E'.
🎉 Installation complete! Continue the setup at http://yourserver.org:8080/login
```



有了这些信息，您可以在 `http://yourserver.org:8080/login` 登录到 Web 界面。

### 选择数据存储位置[](https://stalw.art/docs/install/platform/windows#choose-where-to-store-your-data)

登录后，前往 `设置 `> `存储 `部分，并配置你的 [数据 ](https://stalw.art/docs/storage/data)、[ 对象 ](https://stalw.art/docs/storage/blob)、[ 全文 ](https://stalw.art/docs/storage/fts)和 [内存 ](https://stalw.art/docs/storage/in-memory)存储。阅读 [选择数据库 ](https://stalw.art/docs/install/store)部分以获取更多可用选项的详细信息。

如果你想使用外部认证目录，如 [LDAP](https://stalw.art/docs/auth/backend/ldap) 或 [SQL](https://stalw.art/docs/auth/backend/sql)，则可以前往 `设置 `> `认证 `部分，并配置你的 [认证后端 ](https://stalw.art/docs/install/directory)。

可选

Stalwart 预配置了 ``RocksDB`` 作为所有存储的默认后端。如果你对默认配置满意，可以跳过这一步。

### 配置主机名和域名[](https://stalw.art/docs/install/platform/windows#configure-your-hostname-and-domain)

接下来，请确保在 ``Settings`` > ``Server`` > ``Network`` 中的服务器主机名是正确的。然后，在 ``Management`` > ``Directory`` > ``Domains`` 中添加你的主域名。创建域名后，界面会显示你需要添加到域名 DNS 设置中的 DNS 记录。

例如：

```txt
MX  example.org.                      10 mail.example.org.
TXT 202404e._domainkey.example.org.   v=DKIM1; k=ed25519; h=sha256; p=MCowBQYDK2VwAyEAOT2JN9F8SLTVFNEODDu22SD9RJDC282mugCAeXkzjH0=
TXT 202404r._domainkey.example.org.   v=DKIM1; k=rsa; h=sha256; p=MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAykeYJjv5N0AlnJ8gKF+/8qjbStiMFWvPg+p3JPh96GPXEN6l9W/Ee6Lag6i3vLyTVH5dnRVRBhfWhc+Dc0nKreZe4f5i4L5M4RI31+RpEgu4bCmncUIk2WzJgGBW5XbiOwXjge6OKWtJQN9d8Lc1AuryL5xeged9iS6xd/+EJz4WxAf18U+j38xmAm8fJUTBnQVeb/AZup+voSKAS59jyumsb0jQtXfX5xnwTFXdiX2OF8LRrmmNs/ObHozgHftxAv+YCiSU4bqSlKNPQIrN5kk1YnZDnLlc1Gr66AWlmdUVE7PWtZPTy4f8+uHO93EW3WUxLmynZm+Syn9FTJC2uwIDAQAB
TXT mail.example.org.                 v=spf1 a -all ra=postmaster
TXT example.org.                      v=spf1 mx -all ra=postmaster
TXT _dmarc.example.org.               v=DMARC1; p=reject; rua=mailto:postmaster@example.org; ruf=mailto:postmaster@example.org
```



提示

部分自动生成的记录可能是可选的，具体取决于您的设置，请参阅[设置 DNS](https://stalw.art/docs/install/dns) 部分以获取更多信息。

### 启用 TLS[](https://stalw.art/docs/install/platform/windows#enable-tls)

Stalwart 要求使用有效的 TLS 证书来确保服务器与客户端之间的连接安全。您可以通过以下方式之一启用 TLS：

- 如果你已经为服务器拥有 TLS 证书，可以在 ``Settings`` > ``Server`` > ``TLS`` > ``Certificates`` 部分上传它。
- 如果没有证书，可以使用 Let's Encrypt 的自动 TLS 证书功能 [ACME](https://stalw.art/docs/server/tls/acme/overview) 来启用。要启用 ACME，请转到 `设置 `> `服务器 `> `TLS` > `ACME 提供商 `部分，并将 Let's Encrypt 添加为您的 ACME 提供商，确保您的服务器主机名被列为其中一个主体名称。Stalwart 支持 `tls-alpn-01`、`dns-01` 和 `http-01` 挑战，如果您不确定使用哪个挑战，请阅读 [ACME 挑战类型 ](https://stalw.art/docs/server/tls/acme/challenges)文档。
- 如果您在 Traefik、Caddy、HAProxy 或 NGINX 等反向代理后面运行 Stalwart，应跳过此步骤，并在反向代理中配置 TLS。

### 重启服务[](https://stalw.art/docs/install/platform/windows#restart-service)

完成设置说明后，请重新启动 Stalwart。

### 下一步[](https://stalw.art/docs/install/platform/windows#next-steps)

如果您选择了内部目录，现在可以在 `管理 `> `目录 `> `账户 `部分添加用户。如果您选择了外部目录，则需要在目录服务器中创建用户。

如果一切顺利，您的用户现在应该能够连接到服务器并发送和接收邮件。如果无法连接到服务器，请检查 web-admin 的日志文件或 `<INSTALL_DIR>/logs` 目录中的错误信息。

如果遇到任何问题，请参阅[故障排除](https://stalw.art/docs/management/troubleshoot)部分获取帮助。如果您有疑问，请查看[常见问题](https://stalw.art/docs/faq)部分，或在[社区论坛](https://github.com/stalwartlabs/stalwart/discussions)发帖讨论。



# Docker

Stalwart 以包含 JMAP、IMAP、SMTP 和 WebDAV 服务器的 Docker 镜像形式提供。要开始使用，请拉取 ``stalwart:latest`` 镜像，例如：

```bash
$ docker pull stalwartlabs/stalwart:latest
```



然后，在您的主机上创建一个目录，用于存储配置文件和邮件服务器的数据，例如：

```bash
$ mkdir /var/lib/stalwart
```



完成设置说明后，启动 Stalwart 容器：

```bash
$ docker run -d -ti -p 443:443 -p 8080:8080 \
             -p 25:25 -p 587:587 -p 465:465 \
             -p 143:143 -p 993:993 -p 4190:4190 \
             -p 110:110 -p 995:995 \
             -v <STALWART_DIR>:/opt/stalwart \
             --name stalwart stalwartlabs/stalwart:latest
```



请确保将 ``<STALWART_DIR>`` 替换为上面创建的目录路径。请注意，并非必须暴露所有这些端口，请参阅 [《保护您的服务器》](https://stalw.art/docs/install/security) 文档以获取更多信息。

### 登录 Web 界面[](https://stalw.art/docs/install/platform/docker#log-in-to-the-web-interface)

执行 ``docker logs stalwart`` 以获取管理员账户和密码：

```bash
$ docker logs stalwart
✅ Configuration file written to /opt/stalwart/etc/config.toml
🔑 Your administrator account is 'admin' with password 'w95Yuiu36E'.
```



有了这些信息，您可以在 `http://yourserver.org:8080/login` 登录到 Web 界面。

### 选择数据存储位置[](https://stalw.art/docs/install/platform/docker#choose-where-to-store-your-data)

登录后，前往 `设置 `> `存储 `部分，并配置你的 [数据 ](https://stalw.art/docs/storage/data)、[ 对象 ](https://stalw.art/docs/storage/blob)、[ 全文 ](https://stalw.art/docs/storage/fts)和 [内存 ](https://stalw.art/docs/storage/in-memory)存储。阅读 [选择数据库 ](https://stalw.art/docs/install/store)部分以获取更多可用选项的详细信息。

如果你想使用外部认证目录，如 [LDAP](https://stalw.art/docs/auth/backend/ldap) 或 [SQL](https://stalw.art/docs/auth/backend/sql)，则可以前往 `设置 `> `认证 `部分，并配置你的 [认证后端 ](https://stalw.art/docs/install/directory)。

可选

Stalwart 预配置了 ``RocksDB`` 作为所有存储的默认后端。如果你对默认配置满意，可以跳过这一步。

### 配置主机名和域名[](https://stalw.art/docs/install/platform/docker#configure-your-hostname-and-domain)

接下来，请确保在 ``Settings`` > ``Server`` > ``Network`` 中的服务器主机名是正确的。然后，在 ``Management`` > ``Directory`` > ``Domains`` 中添加你的主域名。创建域名后，界面会显示你需要添加到域名 DNS 设置中的 DNS 记录。

例如：

```txt
MX  example.org.                      10 mail.example.org.
TXT 202404e._domainkey.example.org.   v=DKIM1; k=ed25519; h=sha256; p=MCowBQYDK2VwAyEAOT2JN9F8SLTVFNEODDu22SD9RJDC282mugCAeXkzjH0=
TXT 202404r._domainkey.example.org.   v=DKIM1; k=rsa; h=sha256; p=MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAykeYJjv5N0AlnJ8gKF+/8qjbStiMFWvPg+p3JPh96GPXEN6l9W/Ee6Lag6i3vLyTVH5dnRVRBhfWhc+Dc0nKreZe4f5i4L5M4RI31+RpEgu4bCmncUIk2WzJgGBW5XbiOwXjge6OKWtJQN9d8Lc1AuryL5xeged9iS6xd/+EJz4WxAf18U+j38xmAm8fJUTBnQVeb/AZup+voSKAS59jyumsb0jQtXfX5xnwTFXdiX2OF8LRrmmNs/ObHozgHftxAv+YCiSU4bqSlKNPQIrN5kk1YnZDnLlc1Gr66AWlmdUVE7PWtZPTy4f8+uHO93EW3WUxLmynZm+Syn9FTJC2uwIDAQAB
TXT mail.example.org.                 v=spf1 a -all ra=postmaster
TXT example.org.                      v=spf1 mx -all ra=postmaster
TXT _dmarc.example.org.               v=DMARC1; p=reject; rua=mailto:postmaster@example.org; ruf=mailto:postmaster@example.org
```



提示

部分自动生成的记录可能是可选的，具体取决于您的设置，请参阅[设置 DNS](https://stalw.art/docs/install/dns) 部分以获取更多信息。

### 启用 TLS[](https://stalw.art/docs/install/platform/docker#enable-tls)

Stalwart 要求使用有效的 TLS 证书来确保服务器与客户端之间的连接安全。您可以通过以下方式之一启用 TLS：

- 如果你已经为服务器拥有 TLS 证书，可以在 ``Settings`` > ``Server`` > ``TLS`` > ``Certificates`` 部分上传它。
- 如果没有证书，可以使用 Let's Encrypt 的自动 TLS 证书功能 [ACME](https://stalw.art/docs/server/tls/acme/overview) 来启用。要启用 ACME，请转到 `设置 `> `服务器 `> `TLS` > `ACME 提供商 `部分，并将 Let's Encrypt 添加为您的 ACME 提供商，确保您的服务器主机名被列为其中一个主体名称。Stalwart 支持 `tls-alpn-01`、`dns-01` 和 `http-01` 挑战，如果您不确定使用哪个挑战，请阅读 [ACME 挑战类型 ](https://stalw.art/docs/server/tls/acme/challenges)文档。
- 如果您在 Traefik、Caddy、HAProxy 或 NGINX 等反向代理后面运行 Stalwart，应跳过此步骤，并在反向代理中配置 TLS。

### 重启容器[](https://stalw.art/docs/install/platform/docker#restart-the-container)

完成设置说明后，请重启容器：

```bash
$ docker restart stalwart
```



### 下一步[](https://stalw.art/docs/install/platform/docker#next-steps)

如果您选择了内部目录，现在可以在 `管理 `> `目录 `> `账户 `部分添加用户。如果您选择了外部目录，则需要在目录服务器中创建用户。

如果一切顺利，您的用户现在应该能够连接到服务器并发送和接收邮件。如果无法连接到服务器，请检查 web-admin 的日志文件或 `<INSTALL_DIR>/logs` 目录中的错误信息。

如果遇到任何问题，请参阅[故障排除](https://stalw.art/docs/management/troubleshoot)部分获取帮助。如果您有疑问，请查看[常见问题](https://stalw.art/docs/faq)部分，或在[社区论坛](https://github.com/stalwartlabs/stalwart/discussions)发帖讨论。

提示

在使您的服务器对外公开之前，请务必阅读[确保服务器安全](https://stalw.art/docs/install/security)部分。

### 安装演示[](https://stalw.art/docs/install/platform/docker#setup-demonstration)

![[_images/1b01ccb8ea8b9f616463abe3c8ddc684_MD5.gif]]



# 选择数据库

Stalwart 使用模块化的存储架构，将不同类型的数据分别存储在四个独立的存储库中。这种设计提供了灵活性，并允许每个存储组件独立优化，以适应部署的规模和需求。

- The [Data Store](https://stalw.art/docs/storage/data) 负责存储结构化元数据，如邮件头、文件夹层次结构、日历、联系人、用户设置以及其他非二进制信息。简而言之，它保存了所有除了大型二进制对象之外的所有内容。
- The [Blob Store](https://stalw.art/docs/storage/blob) 用于存储大型二进制文件，如实际的邮件内容、sieve 脚本和附件。
- 为了支持高效的搜索操作，Stalwart 还利用了一个[全文搜索存储 ](https://stalw.art/docs/storage/fts)，它维护索引以加快对消息内容的文本查询速度。
- 最后，[ 内存存储](https://stalw.art/docs/storage/in-memory)处理由安全、集群和反垃圾邮件组件使用的临时键值数据，包括速率限制、分布式锁、贝叶斯模型、发件人信誉评分以及消息交互跟踪。

在简单的单节点设置中，完全有可能将这些角色合并到一个存储后端中。例如，像 **RocksDB** 或 **PostgreSQL** 这样的数据库可以配置为数据存储、对象存储、全文搜索存储，甚至内存存储。在轻量级部署中，常见的是仅使用 RocksDB 来执行所有四个功能，从而简化管理和减少基础设施的复杂性。

然而，在较大的部署中，特别是在[分布式环境中 ](https://stalw.art/docs/cluster/overview)，建议为每个存储角色分配一个专门为此目的设计的后端。一个更可扩展和稳健的配置可能包括使用 **FoundationDB** 作为数据存储，**S3 兼容的服务**用于对象存储，**Redis** 用于处理易失性内存数据，以及一个专门的搜索引擎，如 **Elasticsearch** 或 **Meilisearch** 用于全文索引。

选择合适的数据库组合将取决于部署的性能要求、容错期望以及运营限制。Stalwart 的灵活架构确保它可以从小型单服务器配置扩展到复杂的多节点集群，并为每个存储层提供专门的基础设施。

下表总结了每种存储类型支持的后端：

|                 | 数据存储 | 对象存储 | 全文存储 | 内存存储 |
| --------------- | -------- | -------- | -------- | -------- |
| RocksDB         | ✅        | ✅        | ✅        | ✅        |
| FoundationDB    | ✅        | ✅        | ✅        | ✅        |
| PostgreSQL      | ✅        | ✅        | ✅        | ✅        |
| MySQL / MariaDB | ✅        | ✅        | ✅        | ✅        |
| SQLite          | ✅        | ✅        | ✅        | ✅        |
| S3/MinIO        |          | ✅        |          |          |
| Azure Blob 存储 |          | ✅        |          |          |
| 文件系统        |          | ✅        |          |          |
| ElasticSearch   |          |          | ✅        |          |
| Meiliearch      |          |          | ✅        |          |
| Redis / Valkey  |          |          |          | ✅        |

注意

请注意，稍后更改数据库后端将需要迁移您的数据。



# 选择目录

在 Stalwart 中， *目录*指的是负责管理用户身份和访问凭据的认证后端。目录对于验证登录尝试、检索账户相关信息以及在某些情况下管理用户配置至关重要。Stalwart 支持内部和外部目录配置，为管理员提供了在处理认证方面更大的灵活性。

当使用内部目录时，所有用户账户数据（包括用户名、密码和配额）都存储在 Stalwart 自身的数据存储中。在这种设置中，Stalwart 完全管理用户相关的数据，管理员可以直接在系统中执行所有账户管理任务，包括创建新账户、更新凭证、配置邮件配额以及管理账户级别的设置。内部目录适用于独立部署或小型规模的部署，其中集中控制和简单性非常重要。

或者，Stalwart 可以配置为使用外部目录，将认证和用户信息委托给第三方系统。支持的外部目录包括 **LDAP**、**OpenID Connect** 和 **基于 SQL 的认证后端** 。在这种配置下，Stalwart 依赖外部系统进行用户认证和账户数据。然而，它没有在外部目录中修改用户详细信息（如重置密码或创建账户）的能力。所有用户管理都必须直接在外部系统中通过其相应的工具或 API 进行。

选择内部目录还是外部目录取决于您的运营模式。内部目录提供了简洁性和完全集成，适用于 Stalwart 作为独立平台部署的情况。另一方面，对于已经维护集中身份基础设施并需要与现有系统集成的组织，建议使用外部目录。

Stalwart 的目录系统灵活且设计用于满足广泛的应用场景，从独立部署到具有联邦身份验证的企业环境。可用的身份验证后端包括：

- [内部 ](https://stalw.art/docs/auth/backend/internal)：由 Stalwart 自动创建和管理的内部目录。它使用与数据存储相同的数据库后端。
- *LDAP*：包括 OpenLDAP 和 Active Directory 的 LDAP 服务器。
- [SQL](https://stalw.art/docs/auth/backend/sql): SQL 数据库，包括 PostgreSQL、MySQL 和 SQLite。
- [OpenID Connect](https://stalw.art/docs/auth/backend/oidc): OpenID Connect 服务器，包括 Authentik、Keycloak 等。

REMEMBER THAT...

- 当使用内部目录时，Stalwart 会在其自身系统中管理所有用户相关数据。在这种配置下，所有账户管理任务，如创建新用户账户、更新密码和设置配额，都会直接在 Stalwart 中完成。
- 当使用外部 LDAP 或 SQL 目录时，所有用户账户管理都必须在该外部系统中进行。Stalwart 将依赖该外部目录进行身份验证和获取用户信息，但无法直接从[基于 Web 的管理员界面](https://stalw.art/docs/management/webadmin/overview)修改用户详情。



# 设置 DNS

部署邮件服务器时，正确配置 DNS 记录对于确保邮件投递、客户端兼容性和安全性至关重要。DNS 记录引导邮件流量，验证出站邮件，实施传输安全，并使邮件客户端能够自动发现并连接到服务器。

Stalwart 通过自动为每个配置的域名生成所需的 DNS 记录简化了这一过程。这些记录可以轻松复制并添加到您的域名 DNS 提供商中。以下是每种记录类型及其在邮件基础设施中作用的详细解释。

## 邮件交换（MX）记录[](https://stalw.art/docs/install/dns#mail-exchange-mx-records)

MX 记录指定了负责接收您域名邮件消息的邮件服务器。这些记录对于将流入的邮件流量导向您的服务器至关重要。

```text
MX  example.org.    10 mail.example.org.
```



在本例中，`example.org` 的邮件被导向 `mail.example.org`，优先级为 10。较低的数字表示在列出多个服务器时具有更高的优先级。

## DKIM 记录[](https://stalw.art/docs/install/dns#dkim-records)

[DomainKeys Identified Mail (DKIM)](https://stalw.art/docs/mta/authentication/dkim/overview) 为出站邮件添加数字签名，以证明邮件来自您的域名且在传输过程中未被篡改。DKIM 使用 TXT 记录来发布用于验证这些签名的公钥。

```text
TXT 202404e._domainkey.example.org. v=DKIM1; k=ed25519; h=sha256; p=N/BkJD6xbEiMb39v7JW6AwdPHO5gKB3fcCnod4zQ31U=
TXT 202404r._domainkey.example.org. v=DKIM1; k=rsa; h=sha256; p=MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAqlddLN3BjInvBqI1KpdouG7feBsEt5t233jWQJW7FaY7sR/MfWNxuzTObLoZ3l76DFq3xPjVhmy/YYiOAnMOtq9hUFqgBVTSwUNHYPz1YUEcrI5+Ban7P7LV8kggvTAaWhAI3iSXJIFaUq78K8YYr/zrGyBlg5HCPpd+DMRAB8j1ID8bcWFaVebwAOrartXOO/f8Bn9jrRrLhjP3c8UlmkJLXkSncXPp69R9VpevrKJtpBjaFxKtx7DXGie821MHuWJ7pWMdU1Uf3z8UBKF9bnrCZ5v0SdiaFkPXR1Iiq/gR6bMwdlWvST9V6ePnqZqX+Iv4FA28byOot73/CIINFwIDAQAB
```



每条 DKIM 记录对应一个加密密钥，并通过选择器引用，例如 `202404e` 或 `202404r`。

## SPF 记录[](https://stalw.art/docs/install/dns#spf-records)

Sender Policy Framework (SPF) 帮助邮件服务器验证声称来自您域名的邮件是否确实由授权服务器发送。SPF 记录以 TXT 记录的形式发布。

```text
TXT mail.example.org.   v=spf1 a ra=postmaster -all
TXT example.org.    v=spf1 mx ra=postmaster -all
```



这些策略表明邮件可以从由域名的 MX 或 A 记录定义的服务器发送，并指示接收服务器拒绝来自未经授权来源的邮件。

## DMARC 记录[](https://stalw.art/docs/install/dns#dmarc-record)

Domain-based Message Authentication, Reporting & Conformance (DMARC) 建立在 SPF 和 DKIM 的基础上，指定了当邮件认证失败时应采取的措施以及报告的发送地址。

```text
TXT _dmarc.example.org. v=DMARC1; p=reject; rua=mailto:postmaster@example.org; ruf=mailto:postmaster@example.org
```



这个示例会指示接收服务器拒绝未认证的消息，并将聚合（`rua`）和取证（`ruf`）报告发送给邮件管理员。

## MTA-STS 记录[](https://stalw.art/docs/install/dns#mta-sts-records)

[邮件传输代理严格传输安全（MTA-STS）](https://stalw.art/docs/mta/transport-security/mta-sts) 确保发送到您域名的邮件是加密的，并通过安全通道发送。

```text
CNAME   mta-sts.example.org.    mail.example.org.
TXT _mta-sts.example.org.   v=STSv1; id=16561011793845132961
```



CNAME 记录指向您的 MTA-STS 策略托管位置，而 TXT 记录标识版本和策略 ID 以跟踪更改。

## TLS Reporting (TLS-RPT) 记录[](https://stalw.art/docs/install/dns#tls-reporting-tls-rpt-record)

[SMTP TLS Reporting](https://stalw.art/docs/mta/reports/tls) 允许邮件服务器在尝试向您的域名发送邮件时，发送关于 TLS 协商失败的报告。

```text
TXT _smtp._tls.example.org. v=TLSRPTv1; rua=mailto:postmaster@example.org
```



这条记录告诉发送服务器如何报告 TLS 问题，帮助你监控和改进安全传输。

## 客户端服务的 SRV 记录[](https://stalw.art/docs/install/dns#srv-records-for-client-services)

SRV 记录指导 Thunderbird、Outlook 或移动应用等邮件客户端找到各种服务的正确服务器和端口。

```text
SRV _imap._tcp.example.org. 0 1 110 mail.example.org.
SRV _imaps._tcp.example.org.    0 1 993 mail.example.org.
SRV _submissions._tcp.example.org.  0 1 465 mail.example.org.
SRV _submission._tcp.example.org.   0 1 587 mail.example.org.
```



这些条目指定了邮件客户端应使用的协议和端口，以连接到如 IMAP 和 SMTP 等服务。

## 自动配置记录[](https://stalw.art/docs/install/dns#autoconfiguration-records)

为了使邮件客户端能够自动配置，这些 CNAME 记录应指向您的邮件服务器：

```text
CNAME   autoconfig.example.org. mail.example.org.
CNAME   autodiscover.example.org.   mail.example.org.
```



这样用户就可以更容易地设置邮件客户端，而无需手动输入服务器详细信息。

## TLSA 记录（DANE）[](https://stalw.art/docs/install/dns#tlsa-records-dane)

是基于 DNS 的命名实体认证（DANE）的一部分，提供了您的邮件服务器 TLS 证书与其 DNS 记录之间的加密链接。这些记录是可选的，但为了提高 TLS 安全性，建议使用。

```text
TLSA    _25._tcp.mail.example.org.  3 0 1 064dbc632f1ba7d0a2a3faeadeedfebd6f90f850dfb852c97ee9df9b6e5c5e7c
...
```



您可以根据证书管理策略发布一个或多个 TLSA 记录。如果不太频繁地轮换密钥，一个使用类型为 `3`（DANE-EE）的记录通常就足够了。对于频繁轮换密钥的情况，发布多个 TLSA 记录可以提供冗余，并在密钥过渡期间避免服务中断。

正确的 DNS 配置对于邮件服务器的安全可靠运行至关重要。Stalwart 使生成这些记录变得容易，但管理员需要确保在 DNS 提供商处正确发布它们。每次更改后，务必验证传播情况，并使用测试工具检查您的设置。



# 保护您的服务器

Stalwart 设计时就注重安全性。从部署的那一刻起，它就会应用安全的、[ 安全导向的默认设置 ](https://stalw.art/docs/configuration/overview#safe-defaults)，遵循现代邮件服务器操作的最佳实践。开箱即用，它内置了防御机制来[抵御常见的威胁 ](https://stalw.art/docs/server/auto-ban)。例如，Stalwart 可以自动检测并阻止尝试暴力破解密码的 IP 地址、猜测账户名称、扫描漏洞或发起 SYN 洪泛攻击。这些保护措施会持续运行，以降低滥用和被攻击的风险。

尽管 Stalwart 提供了强大的安全基础，但服务器管理员仍然在维护安全环境方面扮演着关键角色。本节提供了额外的建议和最佳实践，以进一步加固服务器、最小化攻击面，并确保在各种部署场景（从小型个人设置到大型互联网基础设施）中的安全运行。

## 禁用未使用的端口[](https://stalw.art/docs/install/security#disable-unused-ports)

为了简化初始设置，Stalwart 默认为所有支持的服务启用了网络监听，包括 IMAP、HTTP、SMTP、POP3 和 ManageSieve。虽然这确保了服务器在大多数环境中可以立即使用，但强烈建议管理员 **禁用任何不活跃使用的服务及其关联端口**。这样做可以提高安全性，减少服务器的攻击面，并最小化资源使用。

未使用的端口是攻击者潜在的入口点。即使底层服务是安全的，每个开放的端口仍然可能受到暴力破解尝试、协议特定的攻击或资源耗尽攻击。因此，作为最佳实践，只启用实际需要的端口和服务。

管理员可以通过以下两种方式之一禁用未使用的端口：

- **从 Stalwart 配置中移除相应的监听器**——这确保服务不再绑定到该端口。
- **在网络或主机防火墙级别阻止入站流量**，即使监听器在内部活动，也能防止外部访问。

Stalwart 使用多种端口来支持邮件投递、访问和管理任务。了解每个端口的作用将帮助您决定哪些端口需要保持开放，哪些可以安全关闭。

关键端口包括：

- **端口 25（SMTP）**: 用于从其他邮件服务器接收邮件。此端口必须保持开放，以便您的域名能够可靠地接收外部邮件流量。
- **端口 465（SMTPS）**: 用于使用隐式 TLS 加密的邮件提交。推荐用于用户客户端安全发送出站邮件。最好保持此端口开放，并优先使用它而不是端口 587。
- **端口 993（IMAPS）**: 通过隐式 TLS 的 IMAP。对于通过 IMAP 客户端进行安全邮件访问是必需的。保持此端口开放，以允许加密邮件检索。
- **端口 443（HTTPS）**: 用于多个基于 Web 的安全服务，包括 [网络管理 ](https://stalw.art/docs/management/webadmin/overview)、[JMAP](https://stalw.art/docs/http/jmap/overview)、[REST API](https://stalw.art/docs/api/management/overview)、[OAuth](https://stalw.art/docs/auth/oauth/overview)、TLS 证书颁发（[ACME 挑战 ](https://stalw.art/docs/server/tls/acme/challenges#tls-alpn-01)）、[ 自动配置 ](https://stalw.art/docs/server/autoconfig)和 [MTA-STS](https://stalw.art/docs/mta/transport-security/mta-sts#policy-publishing)。在几乎所有部署中，此端口都必须保持开放。

非必需端口包括：

- **端口 587（SMTP 提交）**: 使用 STARTTLS 处理邮件提交。如果所有客户端都配置为使用带有隐式 TLS 的端口 465，则可以出于简化和安全考虑禁用端口 587。
- **端口 143（IMAP4）**: 未加密的标准 IMAP 端口。通常应禁用此端口，转而使用加密的 IMAPS 端口（993）。
- **端口 4190（ManageSieve）：** 用于远程管理 Sieve 脚本。只有在您的用户积极使用 Sieve 进行邮件过滤规则时，才保留此端口的访问权限。
- **端口 110（POP3）** 和 **端口 995（POP3S）**：这些端口用于通过 POP3 获取邮件。除非有遗留需求或特定用例，否则 POP3 在 IMAP 的支持下已经过时，通常可以禁用。
- **端口 8080（HTTP）**：主要用于初始设置。设置完成后，强烈建议禁用此端口，以防止未认证且未加密的访问。

通过仔细审查并禁用任何未使用的网络端口，可以显著加强服务器的安全性。无论您是运行小型私有邮件服务器还是生产系统，这一步骤对于减少潜在攻击的暴露至关重要。您可以使用 Stalwart 的配置系统或服务器的防火墙来一致地实施这些更改。

## 实施 HTTP 访问控制[](https://stalw.art/docs/install/security#enforce-http-access-control)

Stalwart 的 HTTP 监听器在启用服务器的许多现代功能中扮演着核心角色。它被用于提供对包括 JMAP、WebDAV、管理 API、ACME 证书颁发、自动配置/自动发现协议、.well-known 资源、指标端点以及基于 OAuth 的身份验证等一系列服务的访问。

虽然这种广泛的功能非常强大，但也意味着 HTTP 监听器默认会暴露多个端点。在您只想允许访问这些功能的一部分——例如启用 JMAP 但禁用 WebDAV 或公共指标访问——的情况下，您需要定义 [HTTP 访问控制规则 ](https://stalw.art/docs/http/access-control)。

HTTP 访问控制规则是逻辑表达式，用于评估每个传入的 HTTP 请求。这些规则根据请求路径、方法、源 IP、认证状态或其他条件来确定是否应授予对特定 URL 的访问权限。这提供了对哪些 HTTP 端点可以访问以及在什么情况下可以访问的细粒度控制。

为了加强安全性并减少不必要的暴露，强烈建议您审查 [Stalwart 使用的 HTTP 路径列表 ](https://stalw.art/docs/http/overview)，并明确禁用任何在部署中不需要的端点。对于面向互联网的服务器来说，这一点尤为重要，因为未使用的或配置错误的服务可能会成为攻击目标。

您可以通过在配置中创建适当的 [HTTP 访问控制规则 ](https://stalw.art/docs/http/access-control)来实施访问限制。这些规则允许您根据具体需求制定访问策略，确保仅提供必要的基于 HTTP 的服务。

花时间配置 HTTP 访问控制不仅能够提升服务器的安全性，还能通过消除不必要的或未使用的端点来提高服务器的性能和可预测性。

## 了解管理员角色[](https://stalw.art/docs/install/security#understand-administrator-roles)

当 Stalwart 首次启动时，它会自动创建一个 [备用管理员账户 ](https://stalw.art/docs/auth/authorization/administrator#fallback-administrator)。该账户旨在帮助进行服务器的 **初始配置** ，并在外部目录服务不可用或配置错误时作为 **紧急访问机制** 。备用管理员账户拥有 **全部且不受限制的访问权限** ，使其成为一个强大但敏感的账户。

在设置过程中，此账户是必不可少的，但在服务器完全配置好后，强烈建议禁用备用管理员账户。保持该账户活跃会无谓地增加未经授权访问或权限提升的风险。只有在绝对必要的情况下，例如在关键恢复场景中，才应重新启用该账户。

对于日常操作，最佳实践是定义多个具有特定限制权限的管理员账户。例如，一个管理员可能仅负责管理用户账户，另一个负责修改服务器配置，还有一个负责监督 SMTP 队列。虽然这样划分职责可能会显得不便，但它能显著降低泄露凭证或意外配置错误的影响，因为访问权限仅限于必要的功能。

除了职责分离之外，还必须严格执行一项关键安全规则： **管理员账户绝不能用于访问 IMAP、JMAP 或 WebDAV 服务** 。这些服务旨在供普通用户使用，应与管理功能隔离，以防止通过客户端软件误用或暴露高级别凭证。

通过明确定义管理员角色并限制不必要的权限，您可以同时提升邮件服务器环境的**安全性和可维护性**。





# 性能调优

Stalwart 旨在提高效率，并且即使在默认设置下也能处理大量的工作负载。对于**小型或个人部署** ，通常不需要进行广泛的性能调优——默认配置已经足够提供可靠的服务性能。然而，对于**大规模或高流量环境** ，精细调整特定参数可以帮助充分发挥服务器的潜力，并确保在高负载下达到最佳响应性。

缓存在提高性能方面起着关键作用，它通过减少延迟、降低数据库负载以及确保频繁操作的更快响应时间来发挥作用。在 Stalwart 中，缓存深度集成到服务器的内部架构中，并在各个组件中用于临时将频繁访问的数据存储在内存中。

Stalwart 为不同类型的元数据维护了**专用缓存** ，包括电子邮件、日历、联系人和文件。在这之中， **电子邮件元数据缓存**是最关键的性能部分。IMAP 客户端会不断访问它来进行操作，如列出文件夹、检查新邮件、更新标记和同步消息。拥有足够大的电子邮件缓存可以显著提升性能，通过减少发送到底层数据存储的读取操作次数来实现。

为了进一步优化，Stalwart 使用了**增量缓存**策略，该策略确保在更新发生时仅重新获取发生变化的数据部分，从而避免昂贵的全量数据重新加载，并允许客户端在大型邮件文件夹中高效地保持同步。

为了充分利用缓存，建议您的服务器有足够的可用内存来缓存所有同时连接用户的元数据。虽然确切的内存需求取决于邮件文件夹大小和用户活动模式，但为经常访问的邮件文件夹分配充足的缓存可以带来最明显的性能提升，特别是在高流量环境中。

除了存储相关的缓存外，Stalwart 还实现了**认证缓存** ，用于临时存储访问令牌、角色权限和用户会话数据，以减少认证开销。同样地，还有 **DNS 缓存** ，用于存储 DNS 查询结果，帮助避免重复查找并提高邮件投递性能。虽然这些非存储缓存不像邮件缓存那样对性能影响巨大，但它们仍然有助于提高服务器的整体响应能力和效率。

在高并发环境中，适当调整缓存大小是有效扩展 Stalwart 的关键部分。始终监控内存使用情况，并根据观察到的负载调整缓存限制，以在性能和资源可用性之间取得平衡。



# 概述

Stalwart 使用 [TOML](https://toml.io/en/) 格式进行配置。TOML 是 Tom's Obvious, Minimal Language 的缩写，是一种由于其清晰的语义而易于阅读的配置文件格式。它设计用于无歧义解析，使得人类和机器都能轻松理解其结构。TOML 文件将配置组织成键值对、表、数组和嵌套结构，使其适用于广泛的应用场景。这种格式确保了 Stalwart 的配置既易于访问又易于维护，便于进行简单的设置和调整。

Stalwart 配置的一个强大之处在于可以使用静态值或动态值。静态值非常直接——它们是你直接在配置中指定的且不会改变的值。而动态值则使用表达式在运行时确定最终值。这意味着实际值可以根据用户输入、系统条件或其他变量等多种因素进行变化。这对于创建能够适应不同场景或条件的灵活配置非常有用，而无需手动更新。

在 Stalwart 配置文件中，设置可能期望以字符串、整数、大小、布尔值、IP 地址、持续时间、速率、查找路径或包含这些类型的数组形式的值。某些设置支持表达式，可以在运行时动态确定设置的值。

要为 Stalwart 指定配置，用户必须提供 TOML 配置文件的路径。这可以通过启动服务器时使用的 `--config` 参数来实现。

## 本地和数据库设置[](https://stalw.art/docs/configuration/overview#local-and-database-settings)

除了将配置存储在本地的 TOML 文件中，Stalwart 还支持将配置设置存储在任何支持的数据存储中。这在分布式环境中特别有用，允许集群中的所有服务器共享相同的配置设置。

为了适应数据库存储，层次化的 TOML 结构被展平为一系列键。这个过程涉及将每个配置选项转换为唯一的键值对，其中键反映了原始 TOML 文件的结构。例如，考虑以下 TOML 配置：

```toml
[server.listener."smtp"]
bind = ["127.0.0.1:25", "192.0.2.1:25"]
tls.implicit = false
```



在数据库中，此配置将表示为：

```text
server.listener.smtp.bind.0 = "127.0.0.1:25"
server.listener.smtp.bind.1 = "192.0.2.1:25"
server.listener.smtp.tls.implicit = false
```



Stalwart 允许对哪些配置项存储在本地以及哪些存储在数据库中进行精细控制。这通过本地 TOML 配置文件中的 `config.local-keys` 设置进行管理。此设置接受一组通配符数组来匹配配置键。如果键匹配某个模式，则该键保留在本地 TOML 文件中；否则，该键将存储在数据库中。通过在通配符模式前加上 `!`，可以排除特定的键。

如果没有指定 `config.local-keys`，默认配置如下：

```toml
[config]
local-keys = [ "store.*", "directory.*", "tracer.*", "!server.blocked-ip.*", "!server.allowed-ip.*", "server.*",
               "authentication.fallback-admin.*", "cluster.*",   "config.local-keys.*", 
               "storage.data", "storage.blob", "storage.lookup", "storage.fts", "storage.directory", "certificate.*" ]
```



需要注意的是，某些键（特别是匹配 `store.*`、`storage.*` 和 `server.*` 模式）必须始终存储在本地。Stalwart 依赖这些本地配置来正确初始化和启动。从本地存储中排除这些键模式将阻止服务器启动。

## 安全的默认设置[](https://stalw.art/docs/configuration/overview#safe-defaults)

Stalwart 在设计时考虑到了灵活性和易用性，无需强制配置设置即可启动。如果没有特定的配置指令，Stalwart 会默认采用安全且合理的设置以确保服务器安全运行。例如，如果没有明确配置，SMTP 中继将被禁用，以防止服务器被误用为开放中继服务器发送垃圾邮件或未经授权的邮件传输。

Stalwart 的“安全默认设置”哲学意味着它预配置了优先考虑安全性和基本功能的设置。这种做法简化了初始设置过程，尤其是对于新接触邮件服务器管理的用户。服务器智能地默认配置为最小化潜在安全漏洞的同时确保可靠运行。

## 最小配置[](https://stalw.art/docs/configuration/overview#minimal-configuration)

尽管没有必需的设置，但为了使 Stalwart 作为邮件服务器运行，它至少需要配置一个有效的存储和监听器。这些是启动 Stalwart 所需的唯一必要设置。以下是一个使用 RocksDB 配置基本 Stalwart 实例的最小配置示例：

```toml
[server.listener."smtp"]
bind = ["[::]:25"]
protocol = "smtp"

[server.listener."submissions"]
bind = ["[::]:465"]
protocol = "smtp"
tls.implicit = true

[server.listener."imaptls"]
bind = ["[::]:993"]
protocol = "imap"
tls.implicit = true

[storage]
data = "rocksdb"
fts = "rocksdb"
blob = "rocksdb"
lookup = "rocksdb"
directory = "internal"

[store."rocksdb"]
type = "rocksdb"
path = "%{env:STALWART_PATH}%/data"
compression = "lz4"

[directory."internal"]
type = "internal"
store = "rocksdb"

[tracer."stdout"]
type = "stdout"
level = "info"
ansi = false
enable = true

[authentication.fallback-admin]
user = "admin"
secret = "%{env:ADMIN_SECRET}%"
```



# 宏

配置文件中的宏允许您根据各种来源动态赋值，包括环境变量、其他配置设置以及本地文本文件的内容。宏特别适用于减少冗余、简化配置管理，并直接将外部或环境特定的值集成到您的配置中。

## 宏的类型[](https://stalw.art/docs/configuration/macros#types-of-macros)

Stalwart 支持三种类型的宏：

1. **配置设置引用：** 若要在文件中引用其他配置设置，请使用语法 ``%{cfg:key_name}%``。这允许一个设置的值在另一个设置中被重用，从而确保一致性并简化更新。
2. **环境变量检索：** 若要将环境变量的值纳入配置中，请使用 ``%{env:ENVIRONMENT_VAR_NAME}%``。这对于包含敏感信息（如密钥或令牌）特别有用，这些信息不应硬编码在配置文件中。
3. 本地文本文件内容扩展：要将本地文本文件的内容直接包含到配置值中，可以使用 `%{file:/path/to/file.txt}%`。此方法适用于插入证书数据或其他独立于 Stalwart 配置文件管理的外部配置片段。

## 示例[](https://stalw.art/docs/configuration/macros#example)

以下示例展示了每种宏的用法：

```toml
# OAuth Key from an environment variable
[oauth]
key = "%{env:OAUTH_SECRET}%"

# SSL/TLS Certificate from a local file
[certificate."default"]
cert = "%{file:/etc/letsencrypt/live/mail.example.org/fullchain.pem}%"

# Dynamic hostname using another configuration setting
[server]
hostname = "mail.%{cfg:report.domain}%"

[report]
domain = "example.org"
```



## 限制[](https://stalw.art/docs/configuration/macros#limitations)

需要注意的是，宏仅支持在本地配置键中使用。存储在数据库中的配置设置不支持宏展开。这一设计选择是由于 Stalwart 访问和管理数据库中存储的设置的方式。由于宏是动态解析的，最好将其保留在本地配置范围内，以确保它们的值在服务器启动或重新加载时能够正确处理和应用。





# 字符串

字符串可以以几种不同的方式表示：

- 基本字符串：基本字符串由双引号 ``"`` 包围的一系列字符表示。例如，`"Hello, world!"`。
- 多行字符串：多行字符串由三引号 ``"""`` 包围的一系列字符表示。这种类型的字符串可以跨越多行，并在字符串内部保留换行符。例如，

```toml
multiline_string = """
This is a multiline
string in TOML format.
"""
```



- 字面量字符串：字面量字符串由单引号 ``'`` 包围的一系列字符表示。这种类型的字符串适用于表示包含在基本字符串或多行字符串中通常需要转义的字符的字符串，例如双引号。例如，`'Hello, "world"'`。

在 TOML 文件中，字符串可以作为键的值或数组的元素使用。无论字符串在 TOML 文件中以何种形式表示，都必须用引号或字符串字面量包围，以便被识别为字符串。





# 整数

整数可以表示为带小数点的正负整数，例如：

```toml
positive_integer = 42
negative_integer = -42
```



需要注意的是，在 TOML 中，整数不能包含前导零或在数字前加上正号。整数可以作为键的值或数组元素使用。



# 布尔

布尔值可以不带引号表示为 true 或 false，例如：

```toml
is_enabled = true
is_disabled = false
```



在 TOML 文件中，布尔值可以作为键的值使用，也可以作为数组中的元素使用。



# IP 地址

IP 地址以字符串形式表示，可以是 IPv4 或 IPv6 地址，例如：

```toml
ip_v4 = "192.0.2.1"
ip_v6 = "2001:db8::"
```



# 大小

大小以字节表示为正整数，不带小数点，例如：

```toml
size = 1024
```



# 持续时间

持续时间以一个包含数值和单位的字符串表示。可用的持续时间单位包括：

- `ms`: 毫秒
- `s`: 秒
- `m`: 分钟
- `h`: 小时
- `d`: 天

例如：

```toml
timeout = "30s"
```



在本例中，持续时间 `30s` 表示 30 秒。整数值和单位之间由单位符号分隔，并且整个字符串必须用引号或字符串字面量包围，以便在 TOML 文件中被视为字符串。



# 速率

利率表示为一个包含整数值和持续时间的字符串，整数值后跟斜杠 `/` 和持续时间。持续时间指定了整数值分布的时间间隔。例如：

```toml
rate1 = "20 / 5m"  # 20 every 5 minutes
rate2 = "1 / 1d"  # 1 per day
```



在第一个示例中，`20 / 5m` 表示每 5 分钟发生 20 次。在第二个示例中，`1 / 1d` 表示每天发生 1 次。整数值、`/` 符号和持续时间必须用引号或字符串字面量包围，以便在 TOML 文件中被视为字符串。





# 数组

数组是一系列可以是任何类型的值，包括字符串、整数、布尔值或其他任何类型。数组使用方括号 ``[]`` 表示，并用逗号 ``,`` 分隔。例如：

```toml
array_of_strings = [ "apple", "banana", "cherry" ]
array_of_integers = [ 1, 2, 3 ]
```





# Cron

Stalwart 会定期运行自动化任务，执行必要的维护以确保存储使用高效和数据库操作优化。这些任务的调度是通过简化后的类 cron 语法配置的：

```txt
<minute> <hour> <week-day>
```



其中：

- `<minute>`: 执行任务的分钟，范围为 0 到 59。
- `<hour>`: 执行任务的小时，范围为 0 到 23，或使用 `*` 表示每小时执行一次。
- `<week-day>`: 每周运行任务的日期，范围从 `1`（周一）到 `7`（周日），或使用 `*` 表示每天运行。

所有值必须使用服务器的本地时间进行指定。

例如：

- 要在本地时间凌晨 3 点每天运行任务，语法为 `0 3 *`。
- 要在本地时间凌晨 5 点 45 分每周二运行任务，语法为 `45 5 2`。



