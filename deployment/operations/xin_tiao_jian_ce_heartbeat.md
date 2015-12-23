# 网络心跳配置

aerospike的心跳协议负责维护集群的完整性。有两种方式心跳模式

* Multicast (UDP)
* Mesh (TCP)


## 多播 Multicast Heartbeat
配置步骤

在 heartbeat 段落里面配置：

* Set mode to multicast.

* Set address to a valid multicast address (239.0.0.0-239.255.255.255).

*(Optional) Set interface-address to the IP of the interface intended for intracluster communication. This setting also controls the interface fabric will use. Needed when isolating intra-cluster traffic to a particular network interface. 
  

* Set interval and timeout

* interval (recommended: 150) controls how often to send a heartbeat packet.

* timeout (recommended: 10) controls the number of intervals after which a node is

* considered to be missing by rest of nodes in the cluster if they haven't received the heartbeat from missing node.

* With the default settings, a node will be aware of another node leaving the cluster within 1.5 seconds.

## 单播 Mesh (Unicast) Heartbeat