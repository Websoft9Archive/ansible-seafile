# SSL/HTTPS

Seafile deployment package has installed the SSL module of Nginx and open Certificate Authority **[Let's Encrypt](https://letsencrypt.org/)** for you configure the HTTPS quickly and conveniently.

1. Use the SFTP to connect Server, edit [docker-compose configuration file](/stack-components.md#docker-compose)
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/seafile/seafile-editconfig-websoft9.png)

2. You should modify three items at least, then save it
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
   - Remove # to enable "443:443"
   - SEAFILE_SERVER_LETSENCRYPT set to **true**
   - SEAFILE_SERVER_HOSTNAME set to you domain

3. Run the compose command to rebuild them
   ```
   sudo cd /data && docker-compose up -d
   ```
4. HTTPS settings completed

The steps above is from  Seafile official docs: [Let's encrypt SSL certificate](https://download.seafile.com/published/seafile-manual/deploy/deploy_with_docker.md)

## FAQs

#### Seafile container is not running after the HTTPS setting?

Please run the command `sudo docker logs seafile` to check the error and repair it

#### Can I set the HTTPS if no Domain prepared for Seafile?

No, if you set **SEAFILE_SERVER_HOSTNAME** as IP, the Seafile container can't run again