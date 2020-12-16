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

## Manage Seafile Password

We may **Modify** or **recover** Seafile administrator password

### Modify Seafile administrator password

Log in Seafile, go to Users->Your Profile,update your password
![Seafile Modify Seafile administrator password](https://libs.websoft9.com/Websoft9/DocsPicture/en/seafile/seafile-modifypw-websoft9.png)

### Recover Seafile administrator password

If you don't remember the Seafile administrator password, you can retrieve it in the following two ways.

#### Recover by Email

Seafile can retrieve the password by sending an email, but only if your Seafile site has already configured SMTP.
![Seafile Modify Seafile administrator password](https://libs.websoft9.com/Websoft9/DocsPicture/en/seafile/seafile-forgetpw-websoft9.png)

#### Recover by database

If the server does not support the function of sending email passwords, the database management panel phpmyadmin will modify it.

1. Log in to phpMyAdmin, find the *EmailUser* table of your Seafile database,Edit the user(e.g. your username is `me@example.com`)  
   ![Seafile database](https://libs.websoft9.com/Websoft9/DocsPicture/en/seafile/seafile-userspw-websoft9.png)
2. Replace the data with `PBKDF2SHA256$10000$7289a20ae4fc2329415b0645fa3d106019cc61952ae1bc2f9eeef7b30dc47d88$5418ac28f06bd84f2bb701a10dbea6b0bd30676c8042e1f73b9ce12aac302a8d`(MD5)
3. Click **run**
4. The new password is `123456` now

> Completed the modification of compose file, run the command `sudo cd /data && docker-compose up -d` for take effect.
