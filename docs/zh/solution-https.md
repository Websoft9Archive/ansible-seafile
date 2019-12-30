# SSL/HTTPS

网站完成域名绑定且可以通过HTTP访问之后，方可设置HTTPS。

Seafile预装包已内置 SSL 模块方案，需要根据自己的域名进行设置方可使用


## 基本设置

1. 使用 SFTP 连接服务器，编辑 [docker-compose 配置文件](/zh/stack-components.md#docker-compose)
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/seafile/seafile-editconfig-websoft9.png)

2. 最少修改配置文件三个核心参数，然后保存
   ```
     seafile:
    image: seafileltd/seafile-mc:latest
    container_name: seafile
    ports:
      - "80:80"
      - "443:443"  # If https is enabled, cancel the comment.
    volumes:
      - /data/seafile:/shared   # Requested, specifies the path to Seafile data persistent store.
    environment:
      - DB_HOST=db
      - DB_ROOT_PASSWD=123456  # Requested, the value shuold be root's password of MySQL service.
     #      - TIME_ZONE=Asia/Shanghai # Optional, default is UTC. Should be uncomment and set to your local time zone.
      - SEAFILE_ADMIN_EMAIL=admin@admin.com # Specifies Seafile admin user, default is 'me@example.com'.
      - SEAFILE_ADMIN_PASSWORD=admin123   # Specifies Seafile admin password, default is 'asecret'.
      - SEAFILE_SERVER_LETSENCRYPT=true   # Whether use letsencrypt to generate cert.
      - SEAFILE_SERVER_HOSTNAME=seafile.websoft9.cn # Specifies your host name.

   ```
   - 去掉#注释，启用 "443:443" 端口
   - SEAFILE_SERVER_LETSENCRYPT 设置为 true
   - SEAFILE_SERVER_HOSTNAME 修改为你自己的域名
3. 运行 compose 重建命令
   ```
   sudo cd /data && docker-compose up -d
   ```
4. HTTPS 设置成功

以上方案是对 Seafile 官方文档：[向Let's encrypt申请SSL证书](https://manual-cn-origin.seafile.com/deploy/deploy_with_docker#xiang-lets-encrypt-shen-qing-ssl-zheng-shu)的实践解读，验证可用

## 常见问题

#### 设置HTTPS之后，Seafile 容器无法启动？

先运行 `sudo docker logs seafile` 查看日志文件，然后根据日志逐步排查错误

#### 没有域名是否可以设置 Seafile HTTPS？

不可以，即如果 SEAFILE_SERVER_HOSTNAME 处设置为IP地址，会导致 Seafile 无法启动