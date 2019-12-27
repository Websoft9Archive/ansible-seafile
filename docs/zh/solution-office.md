# Office 文档预览与编辑

Seafile 开源版支持集成 OnlyOffice 作为 Office 格式的文档预览与编辑，本部署解决默认已经安装 OnlyOffice Document Server

## 前置条件

1. 开启服务器安全组的 9003 端口
2. 使用本地电脑浏览器，打开 URL：https://服务器公网IP:9003，会看到 OnlyOffice Document Server 正在运行的提示 
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/onlyoffice/onlyoffice-dkisrunning-websoft9.png)

## 配置

3. 使用 SSH 连接服务器，编辑 Seafile 配置文件
2. 插入下面的模板
   ```
   # Enable Only Office
   ENABLE_ONLYOFFICE = True
   VERIFY_ONLYOFFICE_CERTIFICATE = False
   ONLYOFFICE_APIJS_URL = 'https://119.8.39.175:9003/web-apps/apps/api/documents/api.js'
   ONLYOFFICE_FILE_EXTENSION = ('doc', 'docx', 'ppt', 'pptx', 'xls', 'xlsx', 'odt', 'fodt', 'odp', 'fodp', 'ods', 'fods')
   ONLYOFFICE_EDIT_FILE_EXTENSION = ('docx', 'pptx', 'xlsx')
   ```
   ONLYOFFICE_APIJS_URL 为

3. 重启 Seafile 容器服务
   ```
   sudo docker restart seafile
   ```

4. 打开 Seafile 控制台，试一试预览或编辑文档