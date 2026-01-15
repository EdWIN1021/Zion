# 反向代理找不到静态文件

# 反向代理找不到静态文件

```docker
location /react {
    proxy_pass http://192.168.3.88:3000;
}

location ~ .*\.(js|css|svg)?$ {
    proxy_pass http://192.168.3.88:3000;
}
```