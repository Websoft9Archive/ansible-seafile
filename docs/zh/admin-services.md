# 服务启停

使用由Websoft9提供的Seafile部署方案，可能需要用到的服务如下：

> start 启动一个被停止的容器；restart 重启容器；stop 停止正在运行的容器

## Seafile


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

## OnlyOffice DocumentServer

```shell
sudo systemctl start documentserver
sudo systemctl restart documentserver
sudo systemctl stop documentserver
sudo systemctl status documentserver
```

## Docker

```shell
sudo systemctl start docker
sudo systemctl restart docker
sudo systemctl stop docker
sudo systemctl status docker
```
