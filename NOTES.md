# Notes

## Volumes Mounting

```
docker run -it --rm -v /volume:/volume ubuntu:16.10
```

## Data Volume Containers

### Basic Creation

To create a separate container with data volume:

```
docker create --name store -v /srv ubuntu:16.10
```

### Inside a Separate Container

To start a new container and load data volume from `store`:

```
docker run -it --rm --volumes-from store ubuntu:16.10
```

### Orphan Containers

To get a list of orphan data volume containers:

```
docker volume ls -qf dangling=true
```

To remove orphan data volume containers:

```
docker volume rm $(docker volume ls -qf dangling=true)
```

## Ports Sharing

```
docker run -d --name port-export -p <port_on_host_machine>:<port_inside_container> image
```

## Connect to Existed Container

```
docker exec -it <container-name> bash
```

## Network

Get list of networks:

```
docker network ls
```

By default there're:

 - `bridge` - option by default, each container has it's own IP 
 - `host` - copy network settings from host to container 
 - `none` - no connection to other containers

### Create Custom Network

```
docker network create custom
```

Connect container to network:

```
 docker run -it --rm --name one --network custom ubuntu:16.10
```
