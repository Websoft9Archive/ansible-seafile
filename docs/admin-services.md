# Start or Stop the Services

These commands you must know when you using the Seafile of Websoft9

> Use **start** to enable Container that been stopped,  **restart** to restart Container, **stop** to stop the running Container

#### Seafile

```shell
#Seafile-主程序
sudo docker start seafile
sudo docker restart seafile
sudo docker stop seafile

#Seafile-memcached
sudo docker start seafile-memcached
sudo docker restart seafile-memcached
sudo docker stop seafile-memcached

#Seafile-MySQL
sudo docker start seafile-mysql
sudo docker restart seafile-mysql
sudo docker stop seafile-mysql
```

### phpMyAdmin

```shell
sudo docker restart phpmyadmin
sudo docker stop phpmyadmin
sudo docker start phpmyadmin
sudo docker stats phpmyadmin
```

### OnlyOffice DocumentServer

```shell
sudo docker restart onlyoffice-documentserver
sudo docker stop onlyoffice-documentserver
sudo docker start onlyoffice-documentserver
sudo docker stats onlyoffice-documentserver
```

### Docker Compose

```shell
#create dockers
sudo docker-compose up
#rebuild dockers
sudo docker-compose up -d
```

### Docker

```shell
sudo systemctl start docker
sudo systemctl restart docker
sudo systemctl stop docker
sudo systemctl status docker
```