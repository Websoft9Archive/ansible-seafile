# SMTP

Sending mail is a common feature for RabbitMQ. After a large number of user practice feedback, only one way is recommended, that is, using the **third-party STMP service** to send the email.

> Do not try to install **Sendmail** or other Mail server software on your Cloud Server for sending mail, because it is very difficulty in maintenance.

Follow is the sample using **SendGrid's SMTP Service** to configure sending mail:

1. Log in SendGrid console, prepare your SMTP settings like the follow sample
   ```
   SMTP host: smtp.sendgrid.net
   SMTP port: 25 or 587 for unencrypted/TLS email, 465 for SSL-encrypted email
   SMTP Authentication: must be checked
   SMTP Encryption: must SSL
   SMTP username: websoft9smtp
   SMTP password: #fdfwwBJ8f    
2. Use the SFTP to connect Server of Seafile, edit the Seafile configuration file [seahub_settings.py](/stack-components.md#seafile)
2. Insert your SMPT items (refer to Seafile official docs [sending_email](https://download.seafile.com/published/seafile-manual/config/sending_email.md))
   ```
   EMAIL_USE_SSL = True
   EMAIL_HOST = 'smtp.sendgrid.net'
   EMAIL_HOST_USER = 'websoft9smtp'
   EMAIL_HOST_PASSWORD = '#fdfwwBJ8f'
   EMAIL_PORT = '465'
   DEFAULT_FROM_EMAIL = EMAIL_HOST_USER
   SERVER_EMAIL = EMAIL_HOST_USER
   ```
3. Restart the Seafile service
   ```
   sudo docker restart seafile
   ```

> More SMTP Service(Gmail, Hotmail, QQ mail, Yahoo mail, SendGrid and so on)  settings or Issues with SMTP, please refer to Websoft9's *[SMTP Guide](https://support.websoft9.com/docs/faq/tech-smtp.html)*