# arl-distributed-
arl分布式部署---基于新版arl2.5.2版本

使用版本：https://github.com/ki9mu/ARL-plus-docker

克隆配置文件

在Master和不同的Worker上执行

git clone https://github.com/Cedric1314/arl-distributed-/

实际使用请修改master/docker-compose.yml 中配置的mongo 和rabbitmq密码。 并同步修改config-docker.yaml 中的mongo和 rabbitmq 密码 以及将master-vps 修改为 master 对应的公网IP, 并允许能通过公网访问到5003，27017、5672 端口

部署 master

为了部署简单，我们将后台Web系统, mongo, 以及rabbitmq 和 scheduler 都部署到master上，启动并观察是否生效

cd arl-distributed- /master

docker-compose up -d

docker-compose ps

部署 worker

修改 worker/config-docker.yaml 中的mongo和 rabbitmq 密码 以及将master-vps修改为master对应的公网IP, 并确保worker能访问到master 的 5003，27017、5672 端口

可以根据自己的需求修改worker /docker-compose.yml entrypoint 中的 -c 2 参数，默认是2个并发，并发数最好少于等于CPU核数。

在不同的worker上启动并观察是否生效

cd arl-distributed-

docker-compose up -d

docker-compose ps

![image](https://github.com/Cedric1314/arl-distributed-/blob/main/arl.png)

