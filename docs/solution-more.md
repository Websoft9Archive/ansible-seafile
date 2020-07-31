# More

Each of the following solutions has been proven to be effective and We hope to be helpful to you.

## Domain binding

The precondition for binding a domain is that Seafile can accessed by domain name.

Nonetheless, from the perspective of server security and subsequent maintenance considerations, the **Domain Binding** step cannot be omitted.

Seafile domain name binding steps:

1. Use the SFTP to connect your Server
2. Modify [Docker-compose file](/stack-components.md#docker-compose)
   ```text
   ...
    - SEAFILE_SERVER_HOSTNAME=seafile.websoft9.cn # Specifies your host name.
   ...
   ```
   set the item **SEAFILE_SERVER_HOSTNAME** to your domain

3. Save it and then restart Docker-compose service
   ```
   sudo cd /data && docker-compose up -d
   ```


## Docker-compose 配置文件

You can reset [Docker-compose file](/stack-components.md#docker-compose) for more settings, includes:

### Reset Seafile administrator password

If you have forgotten the Seafile administrator password, modify the item below:

```text
- SEAFILE_ADMIN_PASSWORD=KkK303Ye4LmkC4h
```

### MariaDB/MySQL 连接配置

If you have modify the MariaDB/MySQL root password, Seafile will not running normally. You should modify the items below:

```text
- MYSQL_ROOT_PASSWORD=KkK303Ye4LmkC4h
- DB_ROOT_PASSWD=KkK303Ye4LmkC4h
```

> Completed the modification of compose file, run the command `sudo cd /data && docker-compose up -d` for take effect.