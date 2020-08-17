---
typora-root-url: ..\..\img
---

# Pod
## Pod简介
Pod是一组紧密关联的容器集合， 它们共享 IPC、 Network 和 UTS namespace， 是Kubernetes 调度的基本单位。 Pod的设计理念是支持多个容器在一个 Pod中共享网络和文件系统， 可以通过进程间通信和文件共享这种简单高效的方式组合完成服务。

![01-pod](/01-pod.png)

## Pod 的特征
- 包含多个共享 IPC、 Network 和 UTC namespace 的容器， 可直接通过 localhost 通信
- 所有 Pod 内容器都可以访问共享的 Volume， 可以访问共享数据
- 无容错性： 直接创建的 Pod 一旦被调度后就跟 Node 绑定， 即使 Node 挂掉也不会被重新调度（ 而是被自动删除） ， 因此推荐使用 Deployment、 Daemonset 等控制器来容错
- 优雅终止： Pod 删除的时候先给其内的进程发送 SIGTERM， 等待一段时间（ grace period） 后才强制停止依然还在运行的进程
- 特权容器（ 通过 SecurityContext 配置） 具有改变系统配置的权限（ 在网络插件中大量应用） 



