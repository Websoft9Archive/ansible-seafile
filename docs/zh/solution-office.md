# Office 文档预览与编辑

Seafile 开源版支持集成 OnlyOffice Document Server 作为 Office 格式的文档预览与编辑，而本部署解决默认已经安装 OnlyOffice Document Server，无需设置即可使用

## 前置条件

1. 在云控制台安全组中，检查 **TCP:9002** 端口是否开启
2. 使用本地电脑浏览器测试文档服务是否可用：打开网址：http://服务器公网IP:9002，会看到 OnlyOffice Document Server 正在运行的提示 
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/onlyoffice/onlyoffice-dkisrunning-websoft9.png)
   
   > 如果 OnlyOffice Document Server 设置好了 HTTPS 访问，请使用 9003 端口

## 配置

1. 使用 SFTP 连接服务器，编辑 Seafile 配置文件/opt/seafile-data/seafile/conf/seahub_settings.py
2. 插入下面的模板（或对已经存在的模板进行修改）
   ```
   # Enable Only Office
   ENABLE_ONLYOFFICE = True
   VERIFY_ONLYOFFICE_CERTIFICATE = False
   ONLYOFFICE_APIJS_URL = 'http://119.8.39.175:9002/web-apps/apps/api/documents/api.js'
   ONLYOFFICE_FILE_EXTENSION = ('doc', 'docx', 'ppt', 'pptx', 'xls', 'xlsx', 'odt', 'fodt', 'odp', 'fodp', 'ods', 'fods')
   ONLYOFFICE_EDIT_FILE_EXTENSION = ('docx', 'pptx', 'xlsx')
   ```
   > ONLYOFFICE_APIJS_URL 字段中的 IP 地址请更改为你的服务器公网IP地址。如果启用 https，URL地址改成 https 开头

3. 重启 Seafile 容器服务
   ```
   sudo docker restart seafile
   ```

4. 打开 Seafile 控制台，试一试预览或编辑文档
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/seafile/seafile-onlyofficepr-websoft9.png)
