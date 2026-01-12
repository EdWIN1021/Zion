# rm

Owner: Edwin

## Remove Container

```docker
docker rm container_id
```

### Remove all containers

```docker
docker rm -f $(docker ps -aq)
```