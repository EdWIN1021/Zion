## docker volume

### cleanup unused volumes

```shell 
docker volume prune
```

### list volumes

```shell
docker volume ls
```

### display volume details

```shell
docker volume inspect <volume-id>
```

### named volume

```shell 
docker run -d --name mysql -e MYSQL_ROOT_PASSWORD=True -v mysql-db:/var/lib/mysql  mysql
```