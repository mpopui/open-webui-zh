# 将 UI 和模型分别托管

有时，将 Ollama 与 UI 分开托管，但保留跨用户共享的 RAG 和 RBAC 支持功能是有益的：

# 打开 WebUI 配置

## UI 配置

对于 UI 配置，可以按如下方式设置 Apache VirtualHost：

```
# 假设您有一个网站在“server.com”托管此 UI
<VirtualHost 192.168.1.100:80>
    ServerName server.com
    DocumentRoot /home/server/public_html

    ProxyPass / http://server.com:3000/ nocanon
    ProxyPassReverse / http://server.com:3000/

</VirtualHost>
```

在请求 SSL 之前先启用站点：

`a2ensite server.com.conf` # 这将启用该站点。a2ensite 是 "Apache 2 Enable Site" 的缩写

```
# 对于 SSL
<VirtualHost 192.168.1.100:443>
    ServerName server.com
    DocumentRoot /home/server/public_html

    ProxyPass / http://server.com:3000/ nocanon
    ProxyPassReverse / http://server.com:3000/

    SSLEngine on
    SSLCertificateFile /etc/ssl/virtualmin/170514456861234/ssl.cert
    SSLCertificateKeyFile /etc/ssl/virtualmin/170514456861234/ssl.key
    SSLProtocol all -SSLv2 -SSLv3 -TLSv1 -TLSv1.1

    SSLProxyEngine on
    SSLCACertificateFile /etc/ssl/virtualmin/170514456865864/ssl.ca
</VirtualHost>
```

我在这里使用 virtualmin 进行 SSL 集群，但您也可以直接使用 certbot 或您首选的 SSL 方法。要使用 SSL：

### 前提条件

运行以下命令：

`snap install certbot --classic`  
`snap apt install python3-certbot-apache`（这将安装 Apache 插件）。

导航到 Apache sites-available 目录：

`cd /etc/apache2/sites-available/`

如果尚未创建 server.com.conf，则包含上述 `<virtualhost>` 配置（应根据您的情况调整）。使用没有 SSL 的：

创建后，运行 `certbot --apache -d server.com`，这将为您请求并添加/创建 SSL 密钥，并创建 server.com.le-ssl.conf

# 配置 Ollama 服务器

在最新版本的 Ollama 安装中，请确保您根据官方 Ollama 参考设置了 API 服务器：

[Ollama FAQ](https://github.com/jmorganca/ollama/blob/main/docs/faq.md)

### TL;DR

该指南似乎与当前更新的 Linux 服务文件不匹配。因此，我们将在这里处理：

除非您从源代码编译 Ollama，否则使用标准安装 `curl https://ollama.com/install.sh | sh` 会在 /etc/systemd/system 中创建一个名为 `ollama.service` 的文件。您可以使用 nano 编辑该文件：

```
sudo nano /etc/systemd/system/ollama.service
```

添加以下行：

```
Environment="OLLAMA_HOST=0.0.0.0:11434" # 该行是必需的。您也可以指定
```

例如：

```
[Unit]
Description=Ollama Service
After=network-online.target

[Service]
ExecStart=/usr/local/bin/ollama serve
Environment="OLLAMA_HOST=0.0.0.0:11434" # 该行是必需的。您也可以指定 192.168.254.109:DIFFERENT_PORT，格式
Environment="OLLAMA_ORIGINS=http://192.168.254.106:11434,https://models.server.city" # 该行是可选的
User=ollama
Group=ollama
Restart=always
RestartSec=3
Environment="PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/s>

[Install]
WantedBy=default.target
```

按 CTRL+S 保存文件，然后按 CTRL+X

当您的计算机重新启动时，Ollama 服务器将开始监听您指定的 IP:PORT，在这种情况下是 0.0.0.0:11434 或 192.168.254.106:11434（无论您的本地 IP 地址是什么）。确保您的路由器正确配置为通过将 11434 转发到您的本地 IP 服务器来提供页面。

# Ollama 模型配置

## 对于Ollama模型配置，使用以下Apache VirtualHost设置：

导航到apache的sites-available目录：

`cd /etc/apache2/sites-available/`

`nano models.server.city.conf` #根据你的ollama服务器域名进行匹配

添加以下virtualhost示例（根据需要进行修改）：

```
# 假设你在“models.server.city”上托管此UI的网站
<IfModule mod_ssl.c>
    <VirtualHost 192.168.254.109:443>
        DocumentRoot "/var/www/html/"
        ServerName models.server.city
        <Directory "/var/www/html/">
            Options None
            Require all granted
        </Directory>

        ProxyRequests Off
        ProxyPreserveHost On
        ProxyAddHeaders On
        SSLProxyEngine on

        ProxyPass / http://server.city:1000/ nocanon # 或端口11434
        ProxyPassReverse / http://server.city:1000/ # 或端口11434

        SSLCertificateFile /etc/letsencrypt/live/models.server.city/fullchain.pem
        SSLCertificateKeyFile /etc/letsencrypt/live/models.server.city/privkey.pem
        Include /etc/letsencrypt/options-ssl-apache.conf
    </VirtualHost>
</IfModule>
```

你可能需要先启用此站点（如果尚未启用）才能请求SSL：

`a2ensite models.server.city.conf`

#### 对于Ollama服务器的SSL部分

运行以下命令：

导航到apache的sites-available目录：

`cd /etc/apache2/sites-available/`
`certbot --apache -d server.com`

```
<VirtualHost 192.168.254.109:80>
    DocumentRoot "/var/www/html/"
    ServerName models.server.city
    <Directory "/var/www/html/">
        Options None
        Require all granted
    </Directory>

    ProxyRequests Off
    ProxyPreserveHost On
    ProxyAddHeaders On
    SSLProxyEngine on

    ProxyPass / http://server.city:1000/ nocanon # 或端口11434
    ProxyPassReverse / http://server.city:1000/ # 或端口11434

    RewriteEngine on
    RewriteCond %{SERVER_NAME} =models.server.city
    RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]
</VirtualHost>
```

不要忘记使用`systemctl reload apache2`重启/重新加载Apache。

在 https://server.com 打开你的网站！

**恭喜**，你的_**类似Open-AI的Chat-GPT风格UI**_现在已经具备RAG、RBAC和多模态功能！如果你还未下载Ollama模型，请马上下载！

如果遇到任何配置错误或问题，请提交问题或参与讨论。这里有很多友好的开发者为你提供帮助。

让我们把这个UI做得对每个人更友好！

感谢选择open-webui作为AI的UI选项！

本文档由菲律宾的**Bob Reyes**制作，你的**Open-WebUI**粉丝。
