# SSL/HTTPS

Seafile deployment package has installed the SSL module of Nginx and open Certificate Authority **[Let's Encrypt](https://letsencrypt.org/)** for you configure the HTTPS quickly and conveniently.

## Quick start

1. Use the SFTP to connect Server, edit [docker-compose](/stack-components.md#docker-compose) configuration file
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/seafile/seafile-editconfig-websoft9.png)

2. You should modify three items at least, then save it
   ```
   - Remove # to enable "443:443"
   - SEAFILE_SERVER_LETSENCRYPT set to **true**
   - SEAFILE_SERVER_HOSTNAME set to you domain
   ```

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

#### Can I upload my SSL certificate?

Yes, upload it to **/opt/seafile-data/ssl**, make sure the certificate's name is same with your domain:
- seafile.example.com.key
- seafile.example.com.crt