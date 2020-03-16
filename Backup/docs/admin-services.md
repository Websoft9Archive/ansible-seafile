# Start or Stop the Services

These commands you must know when you using the Seafile of Websoft9

> Use **start** to enable Container that been stopped,  **restart** to restart Container, **stop** to stop the running Container

## Seafile

```shell
#Seafile
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

## Docker Compose

```shell
#create dockers
sudo docker-compose up
#rebuild dockers
sudo docker-compose up -d
```

## Docker

```shell
sudo systemctl start docker
sudo systemctl restart docker
sudo systemctl stop docker
sudo systemctl status docker
```