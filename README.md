# 一些开源组件常用命令用法
## rabbitmq

1、查看集群状态：

1.1 本地浏览器打开http://localhost:15672，输入vstation/vstation帐号密码登录，首页概览出现非绿色。

1.2 编译安装是在/usr/local/rabbitmq/etc/rabbitmq/rabbitmq.config.

rabbitmq.config配置文件允许配置RabbitMQ 核心程序， Erlang 服务和RabbitMQ 插件。
它是标准的Erlang 配置文件。RabbitMQ在找不到配置文件的情况下会按照默认的配置运行。

2、rabbitmq常用命令
```
cd /usr/local/services/rabbitmq_server3-1.0/sbin 
rabbitmqctl status #节点状态查询，如果命令执行卡住，节点异常，可关注各类资源使用率

rabbitmqctl cluster_status #集群状态查询，如果出现partition则集群异常，node少于环境部署节点数，
则缺少的node异常
rabbitmq-server –detached #启动集群
rabbitmqctl -detached& #启动单台
rabbitmqctl stop #停止MQ

#MQ详情查看
rabbitmqctl list_exchanges
rabbitmqctl list_bindings
rabbitmqctl list_queues

#MQ环境参数查看
rabbitmqctl environment

#用户权限操作
#查看所有用户的信息
rabbitmqctl list_permissions
#查看指定用户的信息
rabbitmqctl list_user_permissions guest
#添加rabbitmq控制台管理员用户
rabbitmqctl add_user admin admin #添加用户，前一个admin是用户名，后一个admin是密码
rabbitmqctl set_user_tags admin administrator #admin设置为管理员

#登录MQ任意节点通过MQ指令查看MQ总体运行状况
rabbitmqctl report

#查看MQ镜像队列复制情况
rabbitmqctl list_queues -p vstation name slave_pids synchronised_slave_pids

