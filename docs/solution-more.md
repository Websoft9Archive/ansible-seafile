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