Kubernetes 结构
用图来表示体系结构，是阐述 Kubernetes 最快的方式，下面是一张称为 Kubernetes Architecture graphic 。

Kubernetes_Architecture_graphic

上图是简单的 kubernetes 结构，左侧虚线方框中，是 master 节点，运行着各种各样的组件，master 节点负责控制整个集群，当然在很大的集群中也可以有多个 master 节点；而右侧是三个工作节点，负责运行我们的容器应用。这种结构一般称为 master-slave 结构，因为某些原因，在 Kubernetes 中后来改称为 master-minions。工作节点挂了没关系，master 节点会将故障节点上的业务自动在另一个节点上部署。

工作节点比较简单，在工作节点中，我们看到有 kubelet 和 kube-proxy 两个组件，这两个组件在上一章中接触过了，kubelet 和 kube-proxy 都是跟 主节点的 kube-apiserver 进行通信的。kube-proxy 全称是 Kubenetes Service Proxy，负责组件之间的负载均衡网络流量。

在上图中， 主节点由多个组件构成，结构比较复杂， 主节点中记录了整个集群的工作数据，负责控制整个集群的运行。工作节点挂了没关系，但是 主节点挂了，整个集群就挂了。因此， 有条件的情况下，也应该 设置多个 主节点。

一个 主节点中包含以下访问：

**一个 API 服务(kube-apiserver)
一个调度器(kube-scheduler)
各种各样的控制器(上图有两个控制器)
一个存储系统(这个组件称为etcd)，存储集群的状态、容器的设置、网络配置等数据。**

这张图片中还有很多东西，这里暂时不作讲解，我们在后面的章节再去学习那些 Kubernetes 中的术语和关键字。
