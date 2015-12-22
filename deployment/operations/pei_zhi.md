# 配置Configure Aerospike Database

aerospike的配置文件位于/etc/aerospike/aerospike.conf. 配置文件分为5部分，其中两个部分是可选的。


aerospike.conf发现。配置文件分为五个情境两是可选的。一个contexts可以进一步分为sub-contexts。

下面是一个例子,一个空配置文件包括所有上下文和sub-contexts

```ruby
service {}               # Tuning parameters and process owner

network {                # Used to configure intracluster and application-node
                         # communications
    service {}           # Tools/Application communications protocol
    fabric {}            # Intracluster communications protocol
    info {}              # Administrator telnet console protocol
    heartbeat {}         # Cluster formation protocol
}

cluster {}               # (Optional) Configure rack-aware clustering

xdr {                    # (Aerospike Enterprise only) Configure Cross
                         # Datacenter Replication
    datacenter <name> {} # Remote datacenter node list
}

namespace <name> {       # Define namespace record policies and storage engine
    storage {}           # Configure persistence or lack of persistence
    set {}               # (Optional) Set specific record policies
}
```


##配置步骤

1. Configure Network service and heartbeat sub-contexts
2. Configure Namespaces
3. Configure Logging and Log Rotate
4. (Optional) Configure Rack-Aware
5. (Optional) Configure Cross Datacenter Replication