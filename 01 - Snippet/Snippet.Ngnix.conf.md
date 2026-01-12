# conf

# conf

```bash
user  nginx;

#启动进程, 设置成和cpu的内核数相等
worker_processes 1;

events {    
	worker_connections  1024;
}
http {    

# 请求类型 mime.types    
include       /etc/nginx/mime.types;    

# mime.types中没有的就用default_type解析    default_type  application/octet-stream;    log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '                      '$status $body_bytes_sent "$http_referer" '                      '"$http_user_agent" "$http_x_forwarded_for"';    access_log  /var/log/nginx/access.log  main;    # 数据0拷贝    sendfile        on;    # tcp_nopush     on;    keepalive_timeout  65;    # gzip  on;    # include /etc/nginx/conf.d/*.conf;    # 一个server代表一个虚拟主机    server {        listen       80;        listen  [::]:80;        # 域名或者主机名        server_name  localhost;        # access_log  /var/log/nginx/host.access.log  main;        location / {            root   /usr/share/nginx/html;            index  index.html index.htm;        }        # error_page  404              /404.html;        # redirect server error pages to the static page /50x.html        error_page   500 502 503 504  /50x.html;        location = /50x.html {            root   /usr/share/nginx/html;        }    }}error_log  /var/log/nginx/error.log notice;pid        /var/run/nginx.pid;
```