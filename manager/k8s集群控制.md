# Kubernetes集群的管理角色：Master和Node
- Master

> Kubernetes 里的 Master 指的是集群控制节点，每个 Kubernetes 集群里需要有一个 Master节点来负责整个集群的管理和控制，  基本上 Kubernetes 的所有控制命令都发给它，它来负责具体的执行过程，执行的所有命令基本都是在 Master 节点上运行的 。 Master 节点通常会占据一个独立的服务器（ 高可用部署一般用 3 台服务器）， 其主要原因是它太重要了，是整个集群的 “ 首脑”，如果岩机或者不可用 ，那么对集群内容器应用的管理都将失效

- Node

> 除了 Master, Kubernetes 集群中的其他机器被称为 Node 节点，在较早的版本中也被称为Minion 。与 Master 一样 ， Node 节点可以是一台物理主机，也可以是一台虚拟机。 Node 节点才是 Kubernetes 集群中的工作负载节点，每个 Node 都会被 Master 分配一些工作负载（<font color="red">Docker</font>容器），当某个 Node 岩机时，其上的工作负载会被 Master 自动转移到其他节点上去。 
> 
> 获取集群中的节点
> kubectl get nodes  
> 查看某个节点的详细信息  
> kubectl describe node <node_name＞  

