Ansible
=======

###快速入门


###概念
Control node
Managed node
Inventory
Modules
Tasks
Playbooks

###入门


###创建Inventory
hosts 可以是文件，也可以是目录，如果文件过长可以放在目录里分别管理
ansible -i hosts # 可以是目录也可以是文件
host_vars group_vars 可以在/etc/ansible/目录下或当前目录都可以

INI和YAML格式

all ungrouped

www[1:20].example.com

增加变量
```
INI
host1 http_port=80 maxRequestsPerChild=809
host2:2222

YAML
atlanta:
    host1:
        http_port: 80
        maxRequestsPerChild: 80
    host2:2222
```

定义别名
```
INI
    jumper ansible_port=5555 ansible_hosts=10.10.8.212
YAML
    hosts:
        jumper:
            ansible_port: 5555
            ansible_hosts: 10.10.1.212
```
组变量
```
[atlanta:vars]
ntp_server=ntp.atlanta.example.com
proxy=proxy.example.com

atlanta:
    hosts:
        host1:
        host2:
    vars:
        ntp_server: ntp.atlanta.example.com
        proxy: proxy.example.com
```
组和子组
```
all:
    children:
        china:
            children:
                dongbei:
                    children:
                        hosts:
                            liaoming.server.com.cn:
                            jilin.server.com.cn:
                            heilongjiang.server.com.cn::
                    vars:
                        server_port: 8080
                        update_time: 1030
                huabei:
                    children:
                        hosts:
                            shandong.server.com.cn:
```
host_vars group_vars


###定位主机和组

###临时命令简介

###连接方法和详细信息

### 使用命令行


###了解特权升级 become

###Ansible 金库

###使用模块

###使用插件

###Ansilbe和BSD

###使用收藏

