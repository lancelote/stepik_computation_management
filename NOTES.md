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
