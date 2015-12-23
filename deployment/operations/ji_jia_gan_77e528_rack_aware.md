# 机架感知(Rack aware)

配置机架感知，需要做以下几点：

* Configure the rack-aware protocol(协议).
* Configure each server node with its group.配置每个服务器节点组。

下面详细描述这些配置更改

### Configuring the Rack-Awareness Protocol

更新service 节点 paxos-protocol  v4参数如下所示:

```
service {
    ...
    paxos-protocol v4
    ...
}

```

### Configuring the Group (Rack)


在非机架感知的情况下，每个节点由一个节点的值被确定-一个64位的无符号整数，其中包括：16位端口标识加48位hardware MAC address。在集群中的每个节点的值必须是唯一的。

当使用机架感知时，一个节点的值包括：16-bit port ID + 16-bit group ID + 32-bit node ID:：

* 可以自动生成32位节点ID从节点的IP地址或者你可以显式地指定它。当你想要更多的控制节点ID值进行验证或集群调试可以显式地指定节点ID可能使用


* 组ID必须显式地指定。
