# Parameters

The Seafile deployment package contains a sequence software (referred to as "components") required for Seafile to run. The important information such as the component name, installation directory path, configuration file path, port, version, etc. are listed below.

The deployment solution is based Docker, run the command`docker ps` to list all Containers running: 

```bash
CCONTAINER ID        IMAGE                          COMMAND                  CREATED             STATUS              PORTS                                         NAMES
cb57bbd9f1ef        onlyoffice/documentserver      "/bin/sh -c /app/ds/…"   2 hours ago         Up 2 hours          0.0.0.0:9002->80/tcp, 0.0.0.0:9003->443/tcp   documentserver
3878b29258e2        seafileltd/seafile-mc:latest   "/sbin/my_init -- /s…"   5 hours ago         Up About an hour    0.0.0.0:80->80/tcp                            seafile
4974ad7c20e8        memcached:1.5.6                "memcached -m 256"       5 hours ago         Up 2 hours          11211/tcp                                     seafile-memcached
c8d87bd732d7        mariadb:10.1                   "docker-entrypoint.s…"   5 hours ago         Up 2 hours          3306/tcp                                      seafile-mysql

```


## Path

The following mainly lists the parameters related to Docker: 

### Docker Compose

This environment uses Docker Compose as a container orchestration (scheduling) tool for managing multiple container configurations, launches, and service connections.

Docker Compose configuration file:  */data/docker-compose.yml*  
Docker Compose command directory: */usr/local/bin/docker-compose*  

### Seafile

Seafile install directory: */data/seafile*  
Seafile logs directory: */data/seafile/logs*  
Seafile ssl files directory: */data/seafile/ssl*  

Seafile installation directory includes: conf,seafile-data and other important folder

### MySQL

MySQL data storage: */data/mysql*

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

These Ports is need when use Seafile, refer to [Safe Group Setting on Cloud Console](https://support.websoft9.com/docs/faq/tech-instance.html)

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