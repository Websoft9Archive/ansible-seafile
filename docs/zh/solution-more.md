# 更多...

下面每一个方案，都经过实践证明行之有效，希望能够对你有帮助

## 域名绑定

绑定域名的前置条件是：完成域名解析，且 Seafile 可以通过域名访问

虽然如此，从服务器安全和后续维护考量，**域名绑定**步骤不可省却  

Seafile 域名绑定操作步骤：

1. 使用 SFTP 登录云服务器，修改 [Docker-compose 配置文件](/zh/stack-components.md#docker-compose)，将其中的 **SEAFILE_SERVER_HOSTNAME** 项的值为你的域名
   ```text
    - SEAFILE_SERVER_HOSTNAME=seafile.example.com  # Specifies your host name.
   ```
2. 保存配置文件，重启 Seafile 服务
   ```
   sudo cd /data && docker-compose up -d
   ```

## Docker-compose 配置文件

使用 SFTP 登录云服务器，修改 [Docker-compose 配置文件](/zh/stack-components.md#docker-compose)，可以完成常见的维护工作：

## 管理员密码

实际工作中，我们可能会 **修改** 或 **找回** Seafile 管理员密码

### 修改Seafile管理员密码？

1. 以管理员账号登录后台
2. 依次打开：【设置】>【更新】，编辑需要修改密码的账号
3. 修改密码后提交，退出后新密码生效 
   ![Seafile 修改密码](https://libs.websoft9.com/Websoft9/DocsPicture/zh/seafile/seafile-modifypw-websoft9.png)

### 找回 Seafile 管理员密码？

若不记得 Seafile 管理员密码，可以通过如下两个方式找回

#### 方案一：通过邮件找回密码

Seafile可以通过发送邮件找回密码，但前提条件是您的 Seafile 已经配置好SMTP
![Seafile 找回密码](https://libs.websoft9.com/Websoft9/DocsPicture/zh/seafile/seafile-forgetpw-websoft9.png)

#### 方案二：修改数据库中的密码字段

如果不能发邮件，请登录数据库管理面板 phpMyAdmin 进行修改

1. 登录 phpMyAdmin，并找到你的网站数据库下的 *EmailUser* 表,编辑管理员用户（下图以用户名 `me.example.com`为例）
   ![Wordpress 修改密码](https://libs.websoft9.com/Websoft9/DocsPicture/zh/seafile/seafile-userspw-websoft9.png)
   
2. 截图的地方数据库密码(加密后的密文)，用`PBKDF2SHA256$10000$7289a20ae4fc2329415b0645fa3d106019cc61952ae1bc2f9eeef7b30dc47d88$5418ac28f06bd84f2bb701a10dbea6b0bd30676c8042e1f73b9ce12aac302a8d`替换之
3. 点击【执行】
4. 新的密码为`123456`

> 修改 Docker-compose 配置文件后，运行命令 `sudo cd /data && docker-compose up -d` 后生效
