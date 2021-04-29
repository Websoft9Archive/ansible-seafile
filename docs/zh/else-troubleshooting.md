# 故障处理

此处收集使用 Seafile 过程中最常见的故障，供您参考

> 大部分故障与云平台密切相关，如果你可以确认故障的原因是云平台造成的，请参考[云平台文档](https://support.websoft9.com/docs/faq/zh/tech-instance.html)

#### Seafile 无法上传文件？

设置 Seafile 的主机地址（**必选项，否则无法使用文件上传功能**）

   - SERVICE_URL：*http://服务器公网IP*
   - FILE_SERVER_ROOT：*http://服务器公网IP/seafhttp*

   ![Seafile后台界面](https://libs.websoft9.com/Websoft9/DocsPicture/zh/seafile/seafile-seturl-websoft9.png)
   
   
#### 完成文档服务器配置，Seafile 仍然无法编辑和预览文件？

![](https://libs-websoft9-com/Websoft9/DocsPicture/zh/seafile/seafile-canotaccess-websoft9.png)  

问题原因：SERVICE_URL 与实际不符  
解决方案：需登录控制台的系统设置，修改 SERVICE_URL 为实际值

#### 完成 ONLYOFFICE Docs 配置，Seafile 编辑和预览显示错误 “文档安全令牌未正确形成”？

问题原因：ONLYOFFICE docs 安全设置过高   
解决方案：需修改 ONLYOFFICE docs 编排文件中的环境变量 JWT_ENABLED，设置为 false  

```
  onlyoffice-document-server:
    container_name: onlyoffice-docs
    image: onlyoffice/documentserver:6.0.2
    stdin_open: true
    tty: true
    restart: always
    environment:
     - JWT_ENABLED=flase
```




#### 数据库服务无法启动

数据库服务无法启动最常见的问题包括：磁盘空间不足，内存不足，配置文件错误。  
建议先通过命令进行排查  

```shell
# 查看磁盘空间
df -lh

# 查看内存使用
free -lh
```

#### Seafile 无法打开？

查看启动日志，分析错误原因

```
docker logs seafile
```
