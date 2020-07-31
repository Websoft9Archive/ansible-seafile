# SSL/HTTPS

网站完成域名绑定且可以通过HTTP访问之后，方可设置HTTPS。

Seafile预装包已内置 SSL 模块方案，需要根据自己的域名进行设置方可使用

## 前置条件

1. 在云控制台开启 **TCP:443** 端口
2. 完成域名解析，确保 Seafile 可以通过域名访问
3. 登录 Seafile 后台，修改主机地址
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/seafile/seafile-seturl-websoft9.png)

## 基本设置

Seafile 默认支持 [Let's Encrypt](https://letsencrypt.org/) 免费证书自动部署方案，只需如下几步设置：

1. 使用 SFTP 连接服务器，编辑 [docker-compose 配置文件](/zh/stack-components.md#docker-compose)
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/seafile/seafile-editconfig-websoft9.png)

2. 修改（检查）配置文件并保存，确保三个核心参数符合如下要求
   ```
   - "443:443" 启用
   - SEAFILE_SERVER_LETSENCRYPT 设置为 true
   - SEAFILE_SERVER_HOSTNAME 修改为你自己的域名
   ```
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

#### 是否支持自己上传证书？

支持，具体参考[官方文档](https://manual-cn-origin.seafile.com/deploy/deploy_with_docker#xiang-lets-encrypt-shen-qing-ssl-zheng-shu)