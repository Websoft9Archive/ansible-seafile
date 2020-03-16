# SMTP

Sending mail is a common feature for Seafile. After a large number of user practice feedback, only one way is recommended, that is, using the **third-party STMP service** to send the email.

> Do not try to install **Sendmail** or other Mail server software on your Cloud Server for sending mail, because it is very difficulty in maintenance.

1. Use the SFTP to connect Server of Seafile, edit the Seafile configuration file [seahub_settings.py](/stack-components.md#seafile)
2. Insert your SMPT items (refer to Seafile official docs [sending_email](https://download.seafile.com/published/seafile-manual/config/sending_email.md))
3. Restart the Seafile service
   ```
   sudo docker restart seafile
   ```

> More SMTP Service(Gmail, Hotmail, QQ mail, Yahoo mail, SendGrid and so on)  settings or Issues with SMTP, please refer to Websoft9's *[SMTP Guide](https://support.websoft9.com/docs/faq/tech-smtp.html)*