# MySQL

Seafile 预装包中内置 MySQL 容器以及可视化管理工具 phpMyAdmin。  

本部署方案支持如下两种 MySQL 管理方式：

## 可视化管理

1. 本地浏览器 Chrome 或 Firefox 访问：*http://服务器公网IP:9090*，进入phpMyAdmin
  ![登录phpMyadmin](https://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/phpmyadmin-logincn-websoft9.png)
2. 输入数据库用户名和密码([不知道密码？](/zh/stack-accounts.md))
3. 开始管理数据库
  ![phpMyadmin](https://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/phpmyadmin-adddb-websoft9.png)

## 命令管理

可以登录容器后使用命令对 MySQL 进行操作。

1. 使用 SSH 登录服务器后，运行`docker ps`命令获取 seafile-mysql 容器ID
  ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/awx/awx-getcontainerid-websoft9.png)

2. 进入 seafile-mysql 容器操作界面

   ```
   docker exec -it 5256509b7a09 /bin/bash
   ```
3. 使用 mysql 命令登录数据库
   ```
   mysql -uroot -pYouPassword
   ```

4. 接下来可以使用命令操作 MySQL 

> 阅读Websoft9提供的 [《MySQL教程》](https://support.websoft9.com/docs/mysql/zh/) ，掌握更多的MySQL实用技能：修改密码、导入/导出数据、创建用户、开启或关闭远程访问、日志配置等