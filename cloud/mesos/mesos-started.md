##简介
Mesos 可以将整个数据中心的资源（包括 CPU、内存、存储、网络等）进行抽象和调度，使得多个应用同时运行在集群中分享资源，并无需关心资源的物理分布情况。

Mesos 拥有许多引人注目的特性，包括：
- 支持数万个节点的大规模场景（Apple、Twitter、eBay 等公司实践）；
- 支持多种应用框架，包括 Marathon、Singularity、Aurora 等；
- 支持 HA（基于 ZooKeeper 实现）；
- 支持 Docker、LXC 等容器机制进行任务隔离；
- 提供了多个流行语言的 API，包括 Python、Java、C++ 等；
- 自带了简洁易用的 WebUI，方便用户直接进行操作。

### Mesos分布式架构

这套架构包括三个组件：master、slave以及运行在其上的应用本身(framework)。
![](https://github.com/gmg0829/Img/blob/master/mesos/mesos-fram.png?raw=true)

- Masters 管理集群中在每台机器上运行的mesos slave守护进程。通过zookeeper和master之间协调哪个节点是主master。主master节点使用可插拔的分配模块和调度算法来分发资源给各种调度器，从而决定什么资源给某一特定的framework。

- slaves 在集群中负责执行framework任务的服务器称为slave节点。

- frameworks 它负责在集群上调度和执行任务。framework由调度器和执行器组成。
```
 调度器：它是典型的长运行态服务，负责与mesos master连接，接受和拒绝资源供给。
 执行器：执行器是在Mesos slave上启动的一个进程，负责运行framework的任务。
```

### 安装
主：192.168.124.128

从：192.168.124.129

#### 1、下载docker镜像
```
docker pull mesoscloud/zookeeper   #zookeeper
docker pull mesoscloud/mesos-master   #mesos-master
docker pull mesoscloud/mesos-slave   #mesos-slave 
docker pull mesoscloud/marathon   #marathon 
```
#### 2、启动docker镜像

以下命令在主机运行，将ip地址和相关参数修改为对应主机的ip地址和参数

2.1 运行zookeeper
```
docker run -d -e MYID=1 -e SERVERS=192.168.124.128 --name=zookeeper --net=host --restart=always mesoscloud/zookeeper
```
2.2 运行mesos-master
```
docker run -d -e MESOS_HOSTNAME=192.168.124.128 -e MESOS_IP=192.168.124.128 -e MESOS_QUORUM=1 -e MESOS_ZK=zk://192.168.124.128:2181/mesos \
--name mesos-master \
--net host \
--restart=always \
mesoscloud/mesos-master
```
2.3 运行marathon
```
docker run -d -e MARATHON_HOSTNAME=192.168.124.128 -e MARATHON_HTTPS_ADDRESS=192.168.124.128 -e MARATHON_HTTP_ADDRESS=192.168.124.128 \ 
-e MARATHON_MASTER=zk://192.168.124.128:2181/mesos \
-e MARATHON_ZK=zk://192.168.124.128:2181/marathon \
--name marathon \
--net host \
--restart=always \
mesoscloud/marathon
````

以下命令在从运行

2.4运行mesos-slave
```
 docker run -d -e MESOS_HOSTNAME=192.168.124.129 -e MESOS_IP=192.168.124.129 -e MESOS_MASTER=zk://192.168.124.128:2181/mesos \
-v /sys/fs/cgroup:/sys/fs/cgroup \
-v /var/run/docker.sock:/var/run/docker.sock \
--name mesos-slave \
--net host \
--privileged \
--restart=always \
mesoscloud/mesos-slave
```

#### 3、访问Mesos
- mesos地址：http://192.168.124.128:5050/
![](https://github.com/gmg0829/Img/blob/master/mesos/mesos-index.png?raw=true)
- marathon地址：http://192.168.124.128:8080/
![](https://github.com/gmg0829/Img/blob/master/mesos/marthon.png?raw=true)
- 查看 slave
![](https://github.com/gmg0829/Img/blob/master/mesos/mesos-agent.png?raw=true)

#### 4、通过Marathon发布应用

```
{
  "id":"nginxgmg",
  "cpus":0.2,
  "mem":20.0,
  "instances": 1,
  "constraints": [["hostname", "UNIQUE",""]],
  "container": {
  "type":"DOCKER",
  "docker": {
     "image": "daocloud.io/nginx",
     "network": "BRIDGE",
     "portMappings": [
        {"containerPort": 80, "hostPort": 0,"servicePort": 0, "protocol": "tcp" }
      ]
    }
  }
}
```
参考:https://blog.csdn.net/tianpy5/article/details/52828800