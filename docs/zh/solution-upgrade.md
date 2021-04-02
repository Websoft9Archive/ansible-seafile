# 更新升级

网站技术日新月异，**更新升级**是维护工作之一，长时间不升级的程序，就如长时间不维护的建筑物一样，会加速老化、功能逐渐缺失直至无法使用。  

这里注意更新与升级这两词的差异（[延伸阅读](https://support.websoft9.com/docs/faq/zh/tech-upgrade.html#更新-vs-升级)），例如：
- 操作系统打个补丁常称之为**更新**，Ubuntu16.04 变更为 Ubuntu18.04，称之为**升级**
- MySQL5.6.25-->MySQL5.6.30 常称之为**更新**，MySQL5.6->MySQL5.7 称之为**升级**

Seafile 完整的更新升级包括：系统级更新（操作系统和运行环境）和 Seafile 程序升级两种类型

## 系统级更新

运行一条更新命令，即可完成系统级更新：

``` shell
#For Ubuntu
apt update && apt upgrade -y

#For Centos&Redhat
yum update -y
```
> 本部署包已预配置一个用于自动更新的计划任务。如果希望去掉自动更新，请删除对应的Cron


## Seafile 升级

Seafile 升级大致流程：先拉取最新版本的 Seafile 镜像，然后重新运行容器。

> Seafile 升级之前请完成服务器的快照备份，以防不测。

1. 使用 SSH 登录 Seafile 服务器后，停止容器

   ```
   cd /data/wwwroot/seafile 
   docker-compose down -v
   ```

2. 拉取最新版本镜像
   ```
   docker image pull seafileltd/seafile-mc:latest
   ```

3. 重新运行 docker-compose 编排文件，启用新的容器
    ```
    docker-compose up -d
    ```
    
4. 登录 Seafile 后台查看升级后的版本
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/seafile/seafile-aboutversion-websoft9.png)

更多参考官方升级文档：[升级 Seafile 服务](https://cloud.seafile.com/published/seafile-manual-cn/docker/%E7%94%A8Docker%E9%83%A8%E7%BD%B2Seafile.md#user-content-%E5%8D%87%E7%BA%A7%20Seafile%20%E6%9C%8D%E5%8A%A1)
