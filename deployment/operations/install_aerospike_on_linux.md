# Install Aerospike on Linux


## Install on Red Hat


```ruby
wget -O aerospike.tgz 'http://aerospike.com/download/server/latest/artifact/el6'
tar -xvf aerospike.tgz
cd aerospike-server-community-*-el6
sudo ./asinstall # will install the .rpm packages
sudo service aerospike start && \
sudo tail -f /var/log/aerospike/aerospike.log | grep cake
# wait for it. "service ready: soon there will be cake!"
```

## Overview

使用本教程在红帽企业Linux，CentOS、Fedora，Amazon，Oracle Linux安装Aerospike，和其他Linux发行版使用的RPM包。
以上是一个简明的版本，下面按照一步一步的说明。


>```注意，安装的软件包需要root权限（sudo）。如果没有root访问，安装发布的[二进制包aerospike.tgz](http://www.aerospike.com/docs/operations/install/linux/other/)```

## Download Aerospike

如果您已经下载到服务器,您可以跳过此步骤。

>1. 下载aerospike  Community Edition

>```wget -O aerospike.tgz 'http://aerospike.com/download/server/latest/artifact/el6'```

Or if your distribution does not include a copy of wget, you can use curl:

>```curl -L 'http://www.aerospike.com/download/server/latest/artifact/el6' > aerospike.tgz```

有关发布的详细访问该[下载页](http://www.aerospike.com/download)。


>```这个el6包进行验证过的包括Red Hat-based distributions、CentOS,Fedora,Oracle Linux,Amazon Linux和Red Hat Enterprise Linux 7。```

## Install Aerospike
如果已经在服务器安装过，可以跳过此步骤，启动aerospike

>2. 解压安装包
>```tar -xvf aerospike.tgz```

解压后的目录名称类似这样子:
>```aerospike-server-community-<version>-el6/```

这里的<version>是安装包的版本号.

目录的内容应包括：

* license.txt — licenses for Aerospike and other software included in the package.
* aerospike-tools-<version>.el6.x86_64.rpm — Aerospike command-line tools and utilities.
* aerospike-server-community-<version>.el6.x86_64.rpm — the Aerospike server package.

>3.Install Aerospike Server & Tools

>```默认情况下，许多发布的SELinux的启用，会第一时间安装。在安装过程中禁用。```

安装server 和工具包执行以下命令:

>```cd aerospike-server-community-<version>-el6```

>```sudo ./asinstall```

一旦安装完毕，服务器应该可以使用默认配置文件。看[目录结构](http://www.aerospike.com/docs/operations/manage/aerospike/directory_structure.html)的更多细节。


在安装期间如果有错误,请参考故障[排除指南](http://www.aerospike.com/docs/operations/troubleshoot/install/)。

















