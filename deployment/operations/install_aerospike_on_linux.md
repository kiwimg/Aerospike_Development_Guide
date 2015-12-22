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