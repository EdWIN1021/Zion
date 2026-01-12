# docker

- [docker-compose](docker-compose.md)
- [docker image](docker-image.md)
- [bind mount](bind-mount.md)
- [docker kill](docker-kill.md)
- [docker cp](docker-cp.md)
- [docker info](docker-info.md)
- [docker version](docker-version.md)


---

### postgres

```shell
docker run --name <container-name> -e POSTGRES_USER=root -e POSTGRES_PASSWORD=secret -p 5432:5432 -d postgres
```


### mysql

```shell
docker run --name <container-name> -e MYSQL_ROOT_PASSWORD=secret -d mysql:<tag>
```

### mongodb

```shell
docker run --name <container-name> -e MONGO_INITDB_ROOT_USERNAME=root -e MONGO_INITDB_ROOT_PASSWORD=secret -p 27017:27017 -d mongo
```

### nginx

```shell
 docker run --name <container-name> -p 80:80  -v $(pwd):/etc/nginx/nginx.conf -d nginx
```

### RabbitMQ

```shell
docker run -d --hostname my-rabbit --name some-rabbit -e RABBITMQ_DEFAULT_USER=user -e RABBITMQ_DEFAULT_PASS=password -p 15672:15672 -p 5672:5672 rabbitmq:3-management
```

### Jenkins
```shell
docker run -p 8080:8080 -p 50000:50000 -d -v jenkins_home:/var/jenkins_home jenkins/jenkins
```