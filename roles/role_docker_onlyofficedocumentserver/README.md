Ansible Role: docker_onlyoffice_documentserver
=========

本 Role 用于在CentOS或者Ubuntu服务器上安装和配置 OnlyOffice DocumentServer。

官方安装文档：https://helpcenter.onlyoffice.com/server/docker/document/docker-compose.aspx

Requirements
------------

运行本 Role，请确认符合如下的必要条件：

| **Items**      | **Details** |
| ------------------| ------------------|
| Operating system | CentOS7.x Ubuntu18.04 AmazonLinux|
| Python 版本 | Python2  |
| Python 组件 |    |
| Runtime |  |


## Related roles

本 Role 在语法上不依赖其他 role 的变量，但程序运行时需要确保已经运行：docker。下面以 OnlyOffice DoumentServer 为例：

```
  roles:
    - { role: role_common } 
    - { role: role_docker } 
    - { role: role_docker_onlyofficedocumentserver }
```


## Variables

暂无

## Example

```
- name: OnlyOfficeDocumentServer
  hosts: all
  become: yes
  become_method: sudo 
  vars_files:
    - vars/main.yml 

  roles:
    - { role: role_common } 
    - { role: role_docker } 
    - { role: role_docker_onlyofficedocumentserver }
```

## FAQ
