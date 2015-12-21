# 配置

AMC 端口配置: AMC默认端口号运行在8081. 可以修改/etc/amc/config/gunicorn_config.py文件， 从 "0.0.0.0:8081" 到
"0.0.0.0:XXXX",  XXXX 是修改的端口号is the desired port number. After this change, AMC service needs to be restarted in order for the changes to take effect.

SSL Configuration: This feature is available for Enterprise AMC users only. To run AMC on HTTPS, please provision the ssl-certificate and ssl-key file paths within the /etc/amc/config/amc.cfg file. If you do not provide ssl certificate and key file, AMC will default to HTTP.
