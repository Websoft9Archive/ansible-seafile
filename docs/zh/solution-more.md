# 更多...

下面每一个方案，都经过实践证明行之有效，希望能够对你有帮助

## 域名绑定

绑定域名的前置条件是：完成域名解析，且 Seafile 可以通过域名访问

虽然如此，从服务器安全和后续维护考量，**域名绑定**步骤不可省却  

Seafile 域名绑定操作步骤：

1. 使用 SFTP 登录云服务器，修改 [Docker-compose 配置文件](/zh/stack-components.md#docker-compose)，将其中的 **SEAFILE_SERVER_HOSTNAME** 项的值为你的域名
   ```text
    - SEAFILE_SERVER_HOSTNAME=seafile.example.com  # Specifies your host name.
   ```
2. 保存配置文件，重启 Seafile 服务
   ```
   sudo cd /data && docker-compose up -d
   ```

## Docker-compose 配置文件

使用 SFTP 登录云服务器，修改 [Docker-compose 配置文件](/zh/stack-components.md#docker-compose)，可以完成常见的维护工作：

### 重置 Seafile 密码

如果忘记了 Seafile 管理员密码，修改如下字段

```text
- SEAFILE_ADMIN_PASSWORD=KkK303Ye4LmkC4h
```

### MariaDB/MySQL 连接配置

如果修改了 MariaDB/MySQL 的 root 密码，会导致 Seafile 无法启动，这个时候就需要重新修改如下的数据库连接字段
```text
- MYSQL_ROOT_PASSWORD=KkK303Ye4LmkC4h
- DB_ROOT_PASSWD=KkK303Ye4LmkC4h
```

> 修改 Docker-compose 配置文件后，运行命令 `sudo cd /data && docker-compose up -d` 后生效