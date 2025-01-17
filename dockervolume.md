# Docker volumes

## What is Docker volume?

A Docker volume is a persistent storage mechanism used by Docker containers to store data. Unlike the container’s filesystem, which is temporary and erased when the container is removed or stopped, Docker Volume ensures that is persist even after the container is gone, when data insdie the container is temporary and disappears once the container is deleted.Volumes are useful for storing important data, like databases or logs, that need to survive container restarts. Volumes can be shared between containers so that the multiple containers can access the same data. Docker volume is the better choice for storing data in productoin environmnets because they offer better performance and ensure that the important information is preserved for future.


## What is the solution to this problem?

There are two different ways how Docker solves the problem.

    1. Volumes.
    2. Bind Directory on a host as a mount.

## Volumes:

Volumes solve this problem by offering a way to store data on the host file system, separate from the container’s file system. This ensures that the data remains intact, even if the container is deleted and recreated.

![image](https://user-images.githubusercontent.com/43399466/218018334-286d8949-d155-4d55-80bc-24827b02f9b1.png)

Volumes can be created with the help of docker volume command.  
Following command will create a new volume:

```
docker volume create <volume_name>
```


Now volume has been created with above command so that we can mount it to a container using the -v or --mount option with docker run command. 

For example:

```
docker run -it -v <volume_name>:/data <image_name> /bin/bash
```

Above command will mount the volume <volume_name> to the /data directory in the container.
Any data written to the /data directory inside the container will be persisted in the volume on the host file system.

### Bind Directory on a host as a Mount

Bind mounts also helps to resolve the same problem but in a complete different way.

Using this way, user is able to mount a directory from the host file system into a container. Bind mounts and volume has the same behavior, 
but need to specify using a host path instead of a volume name. 

For example, 

```
docker run -it -v <host_path>:<container_path> <image_name> /bin/bash
```

## Differences between Volumes and Bind Directory on a host as a Mount

### Volume:

- Managed using Docker API
- Can be created, mounted and deleted independently of the host file system.
- More flexible and can be backedup, moved between containers.
- Ideal for complex use cases where you need greater control over the data.

## Bind Directory on a Host as a Mount:

- Mounts specific directory from host file system to containers.
- simple and strightforward.
- suitable for simple usecases where sharing data between host and container needed.
- Less flexible than Volumes, have limited options for backup and management.
