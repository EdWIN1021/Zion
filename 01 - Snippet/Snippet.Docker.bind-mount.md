## bind mount

```shell
docker container run -d --name nginx -p 80:80  -v /app/node_modules -v $(pwd):/usr/share/nginx/html nginx
```