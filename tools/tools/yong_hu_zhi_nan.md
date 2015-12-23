# 用户指南

## Install
asadm默认在发布的安装包里，或者从github仓库获取安装

## Getting Help

1. Run asadm --help to learn about arguments that may be needed for your environment.
2. To start the interactive shell run asadm -h [HOST_IP].
3. From the Admin> prompt run help to see a complete list of supported commands.

## Command Organization(组成 结构）

命令被组织成一个层次结构,类似命令共享一个共同的源(parent)。每个命令可以支持一个或多个修改，可以限制命令到一个特定的组节点或过滤一个命令的输出。

所有的命令会输出基于asadm选择为节点的节点名称。节点名称是最短的独特的前缀完全限定域名(FQDN)或或IP如果域名无法解析。
All commands will sort output based on the node name that asadm chooses for the node. The node name is the shortest unique prefix of Fully Qualified Domain Name (FQDN) or IP if the FQDN cannot be resolved.

## Command Shortcuts[命令快捷键]


所有的命令都支持tab自动补全功能；在Admin>提示符,输入i 按<tab>键将出现完整的info命令，输入cl 按<tab>将会出现建议的列表。您还可以是短命令执行，例如，运行info，你可以输入i和net等同于 info network，将会输出namespace和网络信息
