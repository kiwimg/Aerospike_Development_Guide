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