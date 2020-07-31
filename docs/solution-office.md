# Online File preview and edit

Seafile opensource edition supports the **OnlyOffice Document Server** for file preview and edit. This deployment solution have installed the **OnlyOffice Document Server**, so you just need to configure it if you want to use it

## Preparation

1. Enable the **TCP:9002** port in your **[Inbound of Security Group Rule](https://support.websoft9.com/docs/faq/tech-instance.html)** of Cloud Console
2. Use the Chrome or Firefox to test it: visit the URL https://Internt IP of Server:9003, you can see the information **Document Server is running**
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/onlyoffice/onlyoffice-dkisrunning-websoft9.png)

## Configuration

1. Use the **SFTP** to connect Server, edit the [Seafile's configuration file](/stack-components.md#seafile)
2. Insert the template like below
   ```
   # Enable Only Office
   ENABLE_ONLYOFFICE = True
   VERIFY_ONLYOFFICE_CERTIFICATE = False
   ONLYOFFICE_APIJS_URL = 'https://example.seafile.com:9002/web-apps/apps/api/documents/api.js'
   ONLYOFFICE_FILE_EXTENSION = ('doc', 'docx', 'ppt', 'pptx', 'xls', 'xlsx', 'odt', 'fodt', 'odp', 'fodp', 'ods', 'fods')
   ONLYOFFICE_EDIT_FILE_EXTENSION = ('docx', 'pptx', 'xlsx')
   ```
   > Set **ONLYOFFICE_APIJS_URL**, e.g example.seafile.com to your domain or Internet IP

3. Restart the Docker of Seafile
   ```
   sudo docker restart seafile
   ```

4. Now, please opent the Seafile's console to test the previwe and edit