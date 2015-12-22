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