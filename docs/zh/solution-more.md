# 更多...

下面每一个方案，都经过实践证明行之有效，希望能够对你有帮助

## 域名绑定

绑定域名的前置条件是：Seafile已经可以通过解析后的域名访问。  

虽然如此，从服务器安全和后续维护考量，**域名绑定**步骤不可省却  

Seafile 域名绑定操作步骤：

1. 使用 SFTP 登录云服务器
2. 修改 [Docker-compose 配置文件](/zh/stack-components.md#docker-compose)，将其中的 **SEAFILE_SERVER_HOSTNAME** 项的值为你的域名
   ```text
   ...
    - SEAFILE_SERVER_HOSTNAME=seafile.websoft9.cn # Specifies your host name.
   ...
   ```
3. 保存配置文件，重启 Docker-compose服务
   ```
   sudo cd /data && docker-compose up -d
   ```
