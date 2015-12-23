# 网络Network Configuration

Aerospike数据库的网络配置节设置关键网络端口包括节点，应用，和工具。下表列出并描述了由Aerospike数据库和XDR使用的端口：

| Name | Default Port | Description |
| -- | -- | -- |
| Service | 3000 |  ```Application, Tools, and Remote XDR use the Service port for database operations and cluster state.```|
| Fabric | 3001 | Intra-cluster communication port. Replica writes, migrations, and other node-to-node communications use the Fabric port.|
| Mesh Heartbeat | 3002 | Heartbeat protocol ports are used to form and maintain the cluster. (Only one heartbeat port may be configured.) |
| Multicast Heartbeat| 9918 | Heartbeat protocol ports are used to form and maintain the cluster. (Only one heartbeat port may be configured.) |
| Info | 1:6 | 2:6 |
| 0:7 | 1:7 | 2:7 |


		
