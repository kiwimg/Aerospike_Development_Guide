# 常规配置

aerospike配置的网络节需要以下小节：
* service
* fabric
* info
* heartbeat



什么是访问地址？ What is access-address?

访问地址参数确定为客户访问发布的地址。建议当一个aerospike节点有多个IP地址发布的访问地址指向的配置所需的IP。

The access-address parameter determines the address which is published for client access. It is recommended when an Aerospike node has multiple IP addresses to publish an access-address pointing to desired IP in the config.