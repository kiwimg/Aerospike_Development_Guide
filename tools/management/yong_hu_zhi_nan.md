# 用户指南

AMC的用户指南已经分成2个不同的部分来反映2个不同的版本。AMC企业版包括所有AMC的社区版的特点。

AMC Community Edition

AMC Enterprise Edition

Common tasks
There are many common tasks that you may need to do. The following commands work for either edition of the AMC.

Starting the AMC server
To start the AMC:

sudo /etc/init.d/amc start
To stop the AMC server:

sudo /etc/init.d/amc stop
To restart the AMC server:

sudo /etc/init.d/amc restart
To see whether or not the AMC server is up:

sudo /etc/init.d/amc status

Should you have any problem with the AMC, you can check the error logs in /var/log/amc/error.log.

