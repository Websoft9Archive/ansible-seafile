# SMTP

大量用户实践反馈，使用**第三方 SMTP 服务发送邮件**是一种最稳定可靠的方式。  

请勿尝试在服务器上安装sendmail等发邮件方案，因为邮件系统的路由配置受制与域名、防火墙、路由等多种因素制约，导致不稳定、不易维护、诊断故障困难。

下面以**网易邮箱**为例，提供设置 Seafile 发邮件的步骤：

1. 在网易邮箱管理控制台获取 SMTP 相关参数

2. 使用 SFTP 连接服务器，编辑 Seafile 配置文件 [seahub_settings.py](/zh/stack-components.md#seafile)，插入邮箱配置段
   ```
   EMAIL_USE_SSL = True
   EMAIL_HOST = 'smtp.163.com'
   EMAIL_HOST_USER = 'websoft9@163.com'
   EMAIL_HOST_PASSWORD = 'Auth_Code'  //此密码不是邮箱密码，是需要通过163邮箱后台设置去获取的授权码
   EMAIL_PORT = '465'
   DEFAULT_FROM_EMAIL = EMAIL_HOST_USER
   SERVER_EMAIL = EMAIL_HOST_USER
   ```
   参考官方文档：[发送邮件提醒](https://manual-cn-origin.seafile.com/config/sending_email)

3. 重启 Seafile 容器服务
   ```
   sudo docker restart seafile
   ```

> 更多邮箱设置（QQ邮箱，阿里云邮箱，Gmail，Hotmail等）以及无法发送邮件等故障之诊断，请参考由Websoft9提供的 [SMTP 专题指南](https://support.websoft9.com/docs/faq/zh/tech-smtp.html)

## FAQ

#### 如何将邮件通知签名 "Seafile 团队" 修改成自己的签名？

Seafile 采用[邮件模板](https://manual-cn-origin.seafile.com/config/customize_email_notifications)进行邮件内容规范化，【Seafile 团队】在邮件模板文件中对应的是【site_name】字段，即网站名称。因此，只需登录到 Seafile 修改网站名称即可。  
![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/seafile/seafile-sitename-email-websoft9.png)
