# 参数

Seafile 预装包包含 Seafile 运行所需一序列支撑软件（简称为“组件”），下面列出主要组件名称、安装路径、配置文件地址、端口、版本等重要的信息。

本项目基于Docker安装，针对容器提供了持久化存储设置，保证数据不会随着容器的生命周期而丢失。通过运行`docker ps`，可以查看到 Seafile 运行时所有的 Container：

```bash
CONTAINER ID        IMAGE                              COMMAND                  CREATED             STATUS              PORTS                                         NAMES
958e4cbc8dbe        seafileltd/seafile-mc:latest       "/sbin/my_init -- /s…"   14 hours ago        Up 9 minutes        0.0.0.0:80->80/tcp, 0.0.0.0:443->443/tcp      seafile
80c266262079        phpmyadmin/phpmyadmin:latest       "/docker-entrypoint.…"   14 hours ago        Up 9 minutes        0.0.0.0:9090->80/tcp                          phpmyadmin
cea7ee7b8f2a        memcached:1.5.6                    "memcached -m 256"       14 hours ago        Up 9 minutes        11211/tcp                                     seafile-memcached
43881d791ed6        seafileltd/elasticsearch:5.6.16    "/docker-entrypoint.…"   14 hours ago        Up 9 minutes        3306/tcp                                      seafile-elasticsearch
a4498231bb29        onlyoffice/documentserver:latest   "/bin/sh -c /app/ds/…"   39 hours ago        Up 9 minutes        0.0.0.0:9002->80/tcp, 0.0.0.0:9003->443/tcp   onlyoffice-documentserver
```

## 路径

下面主要列出Docker有关的参数：

### Seafile

本项目中的 Seafile 是由：seafile、seafile-memcached和seafile-elasticsearch(企业版专有)组成，它们均基于 Docker 安装，并完成了集成。 

#### Seafile

Seafile 存储目录： */data/wwwroot/seafile/seafile-data*  
Seafile docker-compose 文件路径： */data/wwwroot/seafile/docker-compose.yml*  
Seafile 日志目录： */data/wwwroot/seafile/seafile-data/logs*

seafile-memcached 存储目录： */data/wwwroot/seafile/seafile-data*  
seafile-memcached docker-compose 文件路径： */data/wwwroot/seafile/docker-compose.yml*  
seafile-memcached 日志目录： */data/wwwroot/seafile/seafile-data/logs*

seafile-elasticsearch 存储目录： */data/wwwroot/seafile/seafile-elasticsearch*  
seafile-elasticsearch docker-compose 文件路径： */data/wwwroot/seafile/docker-compose.yml*  
seafile-elasticsearch 日志目录： */data/wwwroot/seafile/seafile-data/logs*

> Seafile配置文件包括 seahub_settings.py, seafile.conf等

#### ONLYOFFICE Document Server

ONLYOFFICE Document Server存储目录： */data/apps/onlyofficedocumentserver*  
ONLYOFFICE docker-compose 文件路径： */data/apps/onlyofficedocumentserver/docker-compose.yml*  
ONLYOFFICE 日志目录： */data/apps/onlyofficedocumentserver/logs*

### MySQL

MySQL 安装路径: */usr/local/mysql*  
MySQL 数据文件 */data/mysql*  
MySQL 配置文件: */etc/my.cnf*  

MySQL 可视化管理参考 [MySQL 管理](/zh/admin-mysql.md) 章节。

###  phpMyAdmin

phpMyAdmin 是一款可视化 MySQL 管理工具，在本项目中它基于 Docker 安装。  

phpMyAdmin directory：*/data/apps/phpmyadmin*  
phpMyAdmin docker compose file：*/data/apps/phpmyadmin/docker-compose.yml* 


## 端口号

下面是您在使用本镜像过程中，需要用到的端口号，请通过 [云控制台安全组](https://support.websoft9.com/docs/faq/zh/tech-instance.html)进行设置

通过命令`netstat -tunlp` 看查看相关端口，下面列出可能要用到的端口：

| 名称 | 端口号 | 用途 |  必要性 |
| --- | --- | --- | --- |
| HTTP | 80 | 通过 http 访问 Seafile | 必须 |
| HTTPS | 443 | 通过 https 访问 Seafile | 可选 |
| HTTP | 9090 | 通过 http 访问 phpMyAdmin | 可选 |
| HTTP | 9002 | 通过 http 访问 OnlyOffice Document Server | 可选 |
| HTTPS | 9003 | 通过 https访问 OnlyOffice Document Server | 可选 |

## 版本号

组件版本号可以通过云市场商品页面查看。但部署到您的服务器之后，组件会自动进行更新导致版本号有一定的变化，故精准的版本号请通过在服务器上运行命令查看：

```shell
# Check all components version
sudo cat /data/logs/install_version.txt

# Linux Version
lsb_release -a

# Python Version
python --version

# Docker Version
docker -v

# Docker image lists(includes version)
sudo docker images

# Docker Compose Version
docker-compose --version
```