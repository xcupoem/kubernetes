# Kubernetes对象
Kubernetes中的一种资源类型，是Kubernetes系统中的持久实体。Kubernetes使用这些实体来表示集群的状态。具体来说，他们可以描述：  
- 容器化应用正在运行(以及在哪些节点上)
- 这些应用可用的资源
- 关于这些应用如何运行的策略，如重新策略，升级和容错  

1. 对象（Object）规范和状态

   每个Kubernetes对象都包含两个嵌套对象字段，用于管理Object的配置：Object Spec和Object Status。Spec描述了对象所需的状态 - 希望Object具有的特性，Status描述了对象的实际状态，并由Kubernetes系统提供和更新。

2. 必填字段 
   对于要创建的Kubernetes对象的yaml文件，需要为以下字段设置值：  

 - apiVersion 创建对象的Kubernetes API 版本  
 - kind 要创建什么样的对象？  
 - metadata 具有唯一标示对象的数据，包括 name（字符串）、UID和Namespace（可选项）  
 - 还需要提供对象Spec字段，对象Spec的精确格式（对于每个Kubernetes 对象都是不同的），以及容器内嵌套的特定于该对象的字段。  
Kubernetes API reference可以查找所有可创建Kubernetes对象的Spec格式。
