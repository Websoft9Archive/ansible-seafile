# 参数

Seafile 预装包包含 Seafile 运行所需一序列支撑软件（简称为“组件”），下面列出主要组件名称、安装路径、配置文件地址、端口、版本等重要的信息。

本项目基于Docker安装，针对容器提供了持久化存储设置，保证数据不会随着容器的生命周期而丢失。通过运行`docker ps`，可以查看到 Seafile 运行时所有的 Container：

```bash
CCONTAINER ID        IMAGE                          COMMAND                  CREATED             STATUS              PORTS                                         NAMES
cb57bbd9f1ef        onlyoffice/documentserver      "/bin/sh -c /app/ds/…"   2 hours ago         Up 2 hours          0.0.0.0:9002->80/tcp, 0.0.0.0:9003->443/tcp   documentserver
3878b29258e2        seafileltd/seafile-mc:latest   "/sbin/my_init -- /s…"   5 hours ago         Up About an hour    0.0.0.0:80->80/tcp                            seafile
4974ad7c20e8        memcached:1.5.6                "memcached -m 256"       5 hours ago         Up 2 hours          11211/tcp                                     seafile-memcached
c8d87bd732d7        mariadb:10.1                   "docker-entrypoint.s…"   5 hours ago         Up 2 hours          3306/tcp                                      seafile-mysql

```

## 路径

下面主要列出Docker有关的参数：

### Seafile

### MySQL

PostgreSQL 数据持久存储：*/data/mysql*

### OnlyOffice Document Server

### Docker

Docker 根目录: */var/lib/docker*  
Docker 镜像目录: */var/lib/docker/image*   
Docker 存储卷：*/var/lib/docker/volumes*  
Docker daemon.json 文件：默认没有创建，请到 */etc/docker* 目录下根据需要自行创建

### Docker Compose

本环境使用 Docker Compose 作为容器编排（调度）工具，用于管理多个容器的启动和服务连接。

Docker Compose 配置目录 */data/docker-compose.yml*  
Docker Compose 命令位置：*/usr/local/bin/docker-compose*  

## 端口号

下面是您在使用本镜像过程中，需要用到的端口号，请通过 [云控制台安全组](https://support.websoft9.com/docs/faq/zh/tech-instance.html)进行设置

| 名称 | 端口号 | 用途 |  必要性 |
| --- | --- | --- | --- |
| HTTP | 80 | 通过 http 访问 Seafile | 必须 |
| HTTPS | 443 | 通过 https 访问 Seafile | 可选 |
| HTTP | 9002 | 通过 http 访问 OnlyOffice Document Server | 可选 |
| HTTPS | 9003 | 通过 https访问 OnlyOffice Document Server | 可选 |

## 版本号

组件版本号可以通过云市场商品页面查看。但部署到您的服务器之后，组件会自动进行更新导致版本号有一定的变化，故精准的版本号请通过在服务器上运行命令查看：

```shell
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