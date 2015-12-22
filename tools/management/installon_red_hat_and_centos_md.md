# Install on Red Hat and Centos

aerospike 提供AMC RPM文件容易安装在Redhat，CentOS


# 要求

安装AMC的rpm文件需要以下几个条件
1. RedHat/CentOS 5+1. 
2. 至少双核处理器
3. 120 MB 可以的磁盘空间
4. 2G内存，推荐4G内存
5. 开放8081端口
 

### 预先安装 Pre-install
 全部的AMC版本安装，需要安装以下几个
* python (2.6+)
* gcc
* python-devel

如果系统缺少以上几个。你可以通过以下这个命令安装

```sudo yum install <package>```

这里的<package> 就是缺少的package.


企业版本[Enterprise Edition]

如何安装AMC的企业版使用更高级的功能，需要一些额外的的要求:

* 需要安装ansible 在机器上，具体操作参照
  http://www.ansibleworks.com/docs/intro_installation.html.

* 如果你希望不使用root用户运行AMC，你可以使用sudo 用户权限，添加sudo文件(/etc/sudoers)一行 使用visudo：
```<user> ALL=(ALL:ALL) NOPASSWD: ALL```

* 安装pip. 你可以找到安装说明： https://pip.pypa.io/en/latest/installing.html

* 你应该安装以下使用PIP的命令：
    
    ```sudo pip install markupsafe```
    
    ```sudo pip install paramiko```
    
    ```sudo pip install ecdsa```
    
    ```sudo pip install pycrypto```
    
    ```sudo pip install bcrypt```



### 下载rpm 文件


对于AMC的下载位置取决于版本


|版本| 描述 |
| -- | -- |
| [Community](http://www.aerospike.com/download/amc/3.6.4/)| 这是自由可用的版本，具有所有的基本功能。 |
| Enterprise| 企业版包含了更先进的管理功能，包括对集群配置进行动态修改的能力。客户与企业版订阅可下载此。|


### 安装 rpm 文件
一旦你的安装文件位于服务器上，你可以通过发布标准的rpm命令安装AMC：

sudo rpm -ivh aerospike-amc-<version>.rpm


### 下一步

看到AMC用户指南说明如何启动/停止服务器及其使用方法。
