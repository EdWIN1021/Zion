# rmi

Owner: Edwin

### Remove image

```docker
docker rmi image_name
```

## Remove all images

```docker
docker rmi -f $(docker images -q)
```