## 架构说明

本项目基于Seafile官方提供的compose文件进行Docker安装，额外增加了以下功能：

* phpMyAdmin
* Onlyoffice Document Server

以上两个组件，开机可以正常运行  

通过修改 /opt/seafile-data/seafile/conf/seahub_settings.py，/opt/seafile-data/seafile/conf/ccnet.conf 配置文件，修正用户的URL，成功实现文档预览编辑
