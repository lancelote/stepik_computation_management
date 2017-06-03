# Notes

## Volumes Mounting

```
docker run -it --rm -v /volume:/volume ubuntu:16.10
```

## Data Volume Containers

To create a separate container with data volume:

```
docker create --name store -v /srv ubuntu:16.10
```

To start a new container and load data volume from `store`:

```
docker run -it --rm --volumes-from store ubuntu:16.10
```
