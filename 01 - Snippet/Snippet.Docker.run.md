# run

Owner: Edwin

## options

| -a  | attached |  |
| --- | --- | --- |
| -d  | detached | run at backgrounf |
| -t  | tty | allows you to interact with the container's shell |
| -i | interactive | it keeps the input channel open |
| -it | -i & -t |  |
| —name |  | assign a custom name to a Docker container when creating it |
| —rm |  | automatically remove the container when it exits |
| -p |  |  |
| —network |  |  |

## Interactive with container

```docker
docker run -it container_id bash
```

## Run a new container

```docker
docker run --name container_name -p <host-port>:<container-port> -d <image-name>
```

## Network

```docker
docker run -d --name container_name -p <host-port>:<container-port> --network <network-name> <image-name>
```