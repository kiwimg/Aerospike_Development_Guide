# 常规配置

aerospike配置的网络节需要以下小节：
* service
* fabric
* info
* heartbeat
通常情况下，只有服务和心跳分小节需要修改。在服务节确保访问地址配置，应用程序将与网络接口。从服务器版本3.3.26这个访问地址应该是一个物理网络接口地址。在虚拟访问地址使用virtual关键字的情况，例如访问虚拟地址192.168.1.100。
Typically, only the service and heartbeat sub-stanzas need modification. In the service stanza ensure that access-address is configured to the network interface that the Application will communicate to. From server version 3.3.26 this access-address should be one of the physical network interface address. In case of vitual access-address use virtual keyword in the end, e.g. access-address 192.168.1.100 virtual

```javascript
...
network {
  service {
    address any                  # IP of the NIC on which the service is
                               # listening.
    port 3000                    # port on which the service is listening.
    access-address 192.168.1.100 # IP address exported to clients that access
                               # the service.
  }

  fabric {
    address any
    port 3001   # Intra-cluster communication port (migrates, replication, etc).
  }

  info {
    address any
    port 3003   # Plain text telnet management port.
  }

  heartbeat {
    mode multicast                  # Send heartbeats using Multicast
    address 239.1.99.2              # multicast address
    port 9918                       # multicast port
    interface-address 192.168.1.100 # IP of the NIC to use to send out heartbeat
                                    # and bind fabric ports
    interval 150                    # Number of milliseconds between heartbeats
    timeout 10                      # Number of heartbeat intervals to wait
                                    # before timing out a node
  }

#  heartbeat {
#    mode mesh                   # Send heartbeats using Mesh (Unicast) protocol
#    address 192.168.1.100       # IP of the NIC on which this node is listening
#                                # to heartbeat
#    port 3002                   # port on which this node is listening to
#                                # heartbeat
#    mesh-seed-address-port 192.168.1.101 3002 # IP address for seed node in the cluster
#    mesh-seed-address-port 192.168.1.102 3002 # IP address for seed node in the cluster
#    interval 150                # Number of milliseconds between heartbeats
#    timeout 20                  # Number of heartbeat intervals to wait before
#                                # timing out a node
#  }
}
...```

什么是访问地址？ What is access-address?

访问地址参数确定为客户访问发布的地址。建议当一个aerospike节点有多个IP地址发布的访问地址指向的配置所需的IP。

The access-address parameter determines the address which is published for client access. It is recommended when an Aerospike node has multiple IP addresses to publish an access-address pointing to desired IP in the config.