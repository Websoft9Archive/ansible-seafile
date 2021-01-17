# Update & Upgrade

Updates and upgrades are one of the maintenance tasks for sytem. Programs that are not upgraded for a long time, like buildings that are not maintained for a long time, will accelerate aging and gradually lose functionality until they are unavailable.

You should know the differences between the terms **Update** and **Upgrade**([Extended reading](https://support.websoft9.com/docs/faq/tech-upgrade.html#update-vs-upgrade))
- Operating system patching is **Update**, Ubuntu16.04 to Ubuntu18.04 is **Upgrade**
- MySQL5.6.25 to MySQL5.6.30 is **Update**, MySQL5.6 to MySQL5.7 is **Upgrade**

For Seafile maintenance, focus on the following two Update & Upgrade jobs

- Sytem update(Operating System and Running Environment) 
- Seafile upgrade 

## System Update

Run an update command to complete the system update:

``` shell
#For Ubuntu
apt update && apt upgrade -y

#For Centos&Redhat
yum update -y
```
> This deployment package is pre-configured with a scheduled task for automatic updates. If you want to remove the automatic update, please delete the corresponding Cron

## Seafile Upgrade

Modify the version information in the file: */data/docker-compose.yml*, run the command below

1. Use **SSH** to connect Seafile Server and pull the latest image of Seafile
   ```
   docker image pull seafileltd/seafile-mc:latest
   ```

2. Create new Seafile container by *docker-compose.yml*
    cd /data/wwwroot/seafile 
    docker-compose down -v
    docker-compose up -d
    ```

More details please refer to official docs [Seafile upgrade](https://manual.seafile.com/docker/deploy%20seafile%20with%20docker/#upgrading-seafile-server)