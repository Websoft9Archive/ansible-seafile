# 服务启停

使用由Websoft9提供的Seafile部署方案，可能需要用到的服务如下：

> start 启动一个被停止的容器；restart 重启容器；stop 停止正在运行的容器

### Seafile

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
#创建容器
sudo docker-compose up
#创建容器并重建有变化的容器
sudo docker-compose up -d
```

### Docker

```shell
sudo systemctl start docker
sudo systemctl restart docker
sudo systemctl stop docker
sudo systemctl status docker
```