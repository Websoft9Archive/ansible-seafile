# Parameters

The Seafile deployment package contains a sequence software (referred to as "components") required for Seafile to run. The important information such as the component name, installation directory path, configuration file path, port, version, etc. are listed below.

The deployment solution is based Docker, run the command`docker ps` to list all Containers running: 

```bash
CONTAINER ID        IMAGE                              COMMAND                  CREATED             STATUS              PORTS                                         NAMES
8d3ddd4e7927        seafileltd/seafile-mc:latest       "/sbin/my_init -- /s…"   24 minutes ago      Up 22 minutes       0.0.0.0:80->80/tcp, 0.0.0.0:443->443/tcp      seafile
3d2b1f711684        phpmyadmin/phpmyadmin:latest       "/docker-entrypoint.…"   24 minutes ago      Up 24 minutes       0.0.0.0:9090->80/tcp                          phpmyadmin
26fdc3c2d63b        memcached:1.5.6                    "memcached -m 256"       24 minutes ago      Up 24 minutes       11211/tcp                                     seafile-memcached
b1d7b3350ce0        mariadb:10.1                       "docker-entrypoint.s…"   24 minutes ago      Up 24 minutes       3306/tcp                                      seafile-mysql
a4498231bb29        onlyoffice/documentserver:latest   "/bin/sh -c /app/ds/…"   40 hours ago        Up About an hour    0.0.0.0:9002->80/tcp, 0.0.0.0:9003->443/tcp   onlyoffice-documentserver
```


## Path

The following mainly lists the parameters related to Docker: 

### Docker Compose

This environment uses Docker Compose as a container orchestration (scheduling) tool for managing multiple container configurations, launches, and service connections.

Docker Compose configuration file:  */data/docker-compose.yml*  
Docker Compose command directory: */usr/local/bin/docker-compose*  

### Seafile

Seafile configuration file: */data/wwwroot/seafile-data/seafile/conf*  
Seafile install directory: */data/wwwroot/seafile-data*  
Seafile logs directory: */data/wwwroot/seafile-data/logs*  
Seafile ssl files directory: */data/wwwroot/seafile/ssl*  

Seafile configuration file directory includes: seahub_settings.py, seafile.conf...

### MariaDB/MySQL

MySQL data storage: */data/seafile-mysql*

### phpMyAdmin

The web based GUI tool for MySQL/MariaDB, visit URL: *http://Internet IP:9090*  

### OnlyOffice Document Server

OnlyOffice Document Server certs storage: */data/certs/onlyoffice_DocumentServer*  
OnlyOffice Document Server logs storage: */data/logs/onlyoffice_DocumentServer*  
OnlyOffice Document Server data storage: */data/wwwroot/onlyoffice_DocumentServer/data*  
OnlyOffice Document Server lib storage: */data/wwwroot/onlyoffice_DocumentServer/lib*  
OnlyOffice Document Server database storage: *data/onlyoffice_DocumentServer_postgresql*  

### Docker

Docker root directory: */var/lib/docker*  
Docker image directory: */var/lib/docker/image*   
Docker storage: */var/lib/docker/volumes*  
Docker daemon.json: It is not created by default, please go to the * /etc/docker* to create it yourself as needed

## Ports

You can control(open or shut down) ports by **[Security Group Setting](https://support.websoft9.com/docs/faq/zh/tech-instance.html)** of your Cloud Server whether the port can be accessed from Internet.

You can run the cmd `netstat -tunlp` to list all used ports, and we list the following most useful ports:

| Name | Number | Use |  Necessity |
| --- | --- | --- | --- |
| PostgreSQL | 5432 | Remote connect PostgreSQL | Optional |
| HTTP | 80 | HTTP requests for Seafile | Required |
| HTTPS | 443 | HTTPS requests Seafile | Optional |
| HTTP | 9002 | HTTP requests OnlyOffice Document Server | Optional |
| HTTPS | 9003 | HTTPS requests OnlyOffice Document Server | Optional |

## Version

You can see the version from product page of Marketplace. However, after being deployed to your server, the components will be automatically updated, resulting in a certain change in the version number. Therefore, the exact version number should be viewed by running the command on the server:

```shell
# Check all components version
sudo cat /data/logs/install_version.txt

# Linux Version
lsb_release -a

# Python Version
python --version

# Docker Version
docker -v

# Docker image lists(includes version)
sudo docker images

# Docker Compose Version
docker-compose --version
```