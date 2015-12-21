# 配置

AMC 端口配置: AMC默认端口号运行在8081. 可以修改/etc/amc/config/gunicorn_config.py文件， 从 "0.0.0.0:8081" 到
"0.0.0.0:XXXX",  XXXX 是修改的端口号. 修改后需要重新启动以便生效

SSL 配置: 这个功能仅是企业版用户使用. To run AMC on HTTPS, please provision the ssl-certificate and ssl-key file paths within the /etc/amc/config/amc.cfg file. If you do not provide ssl certificate and key file, AMC will default to HTTP.
