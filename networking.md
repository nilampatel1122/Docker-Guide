# Docker Networking

Networking allows containers to communicate with each other and the host system. Containers run isolated from the host system and need a way to communicate with each other and the host system.

By dfault, Docker provides two default network drivers. 
1. Bridge 
2. Overlay

```
docker network ls
```
Use the command above to see the output in your system.

```
NETWORK ID          NAME                DRIVER
xxxxxxxxxxxx        none                null
xxxxxxxxxxxx        host                host
xxxxxxxxxxxx        bridge              bridge
```

## Bridge Networking

The bridge is the default network mode in the docker. It creates the private network between the host and the containers. It allows the containers to communicate with each other and with the host system.



![image](https://user-images.githubusercontent.com/43399466/217745543-f40e5614-ac34-4b78-85a9-91b24512388d.png)


You can isolate your containers from the deault network by creating your own network. Use the command below to create your own bridge network.


```
docker network create -d bridge my_own_bridge
```

Now, If you list the docker network then you will be able to see a new created netwok

```
docker network ls

NETWORK ID          NAME                DRIVER
xxxxxxxxxxxx        bridge              bridge
xxxxxxxxxxxx        my_own_bridge       bridge
xxxxxxxxxxxx        none                null
xxxxxxxxxxxx        host                host
```

This newly created network can be attached to containers when your run these containers

```
docker run -d --net=my_own_bridge --name db 

``

This way you can run multiple contianers in a single host system. where one container is attached to the default network and the other is attached to your private network.

These containers are completly isolated with their private networks and can not talk to each other.

![image](https://user-images.githubusercontent.com/43399466/217748680-8beefd0a-8181-4752-a098-a905ebed5d2a.png)


you can connect the container from default bridge network to your private network at anytime to enable communication.


```
docker network connect my_bridge web
```


![image](https://user-images.githubusercontent.com/43399466/217748726-7bb347d0-3736-4f89-bdff-31d240b15150.png)

## Host Networking

Host network allows containers to share the host system's network stack, by providing direct access to the host system's network.

you can use the --network="host" command to attach a host network to a Docker container with docker run command. By using this option, the container can access the host's network stack, and able to share the host's network namespace. That means the container is using the same IP address and network configuration as the host.

Command to run a Docker container with the host network:

```
docker run --network="host" <image_name> <command>
```
Be careful, when you use the host network, the container is less isolated from the host system, and has access to all of the host's network resources. This can be a security risk, so use the host network with caution.

Additionally, first check, if is there any comatibility issues. as all Docker image and command combinations are not compatible with the host network, so it is very important to check the image documentation or run the image with the --network="bridge" option (the default network mode) to see if there are any compatibility issues.

### Overlay Networking

Overlay Networking enables communication between containers across multiple Docker host machines, It allows containers to be able to connect to a single network even though they are running on different hosts.

### Macvlan Networking

Macvlan Networking allows a container to appear on the network as a physical host rather than as a container.