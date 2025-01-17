# Docker-Guide
# This Repository provides complete guide for engineers to learn Docker from scratch.
# Learn docker with Examples.

## If you find this repository useful please give it a star

### What is Docker?

Docker is a powerful containerization platform that simplifies the process of packaging and deploying applications. With Docker, you can build container images, run these images to create containers, and push the container images to registries like DockerHub, Quay.io, and others for easy sharing and deployment.

### Docker Architecture?

![image](https://user-images.githubusercontent.com/43399466/217507877-212d3a60-143a-4a1d-ab79-4bb615cb4622.png)


The image above clearly illustrates that the Docker Daemon is the central component of Docker, acting as its "brain." If the Docker Daemon is stopped or becomes unresponsive for any reason, Docker effectively becomes non-functional.

### Docker LifeCycle.

Please refer above image to understand the Lifecycle of Docker.

Three main Phases to understand:

1. docker build: Builds the Docker images from the Dockerfile
2. docker run: runs(create) the container from the built images
3. docker push: push the container images to the private/public registries to share the docker images.


### Understanding the Docker terminology.

#### Docker daemon: 

The Docker daemon (dockerd) is responsible for handling Docker API requests and managing Docker resources, including images, containers, networks, and volumes. It can also interact with other daemons to coordinate and manage Docker services.

#### Docker client:

The Docker client (docker) is the main interface, users use this interface to interact with Docker. When you executes the docker commands such as docker build, docker run, the client forwards them to the Docker daemon(dockerd) and executes them. These commnads communicates with the Docker AOI and interact with multiple daemons at the same time.

#### Dcoker Desktop

Docker Desktop is an easy-to-install application for any environment, such as Mac, Windows or Linux. Once you install Desktop, it enables you to build and share containerized applications and microservices. Docker Desktop includes the Docker Daemon (dockerd), the client (docker), Docker compose, docker Content Trust, Kubernetes and Credential Helper.

#### Docker Registries.

Docker Hub is a public registry that anyone can use, Dockr registry stores the Docker images and Docker congifured to look for an images on the Docker Hub. User can use proivate/public registery.

when we xecute dockr pull or docker run commands, the required images are pulled from your configured registry. when docker push commands get executed the image is being pushed to configured registry.


#### Docker objects

whilst using Docker, we are creating and using images, containers, networks, volumes, plugins, and other objects.

### Dockerfile

Dockerfile is the file where you writes the number of steps to build your Docker image of your application. Dockerfile does not have any extension and the name of the file shoule be Dockerfile itself.

#### Images

An Image is a read-only template with instructions of creating container. Image is often build upon other image with additional customizations. For instance, you might start with the Ubuntu image and add the Apache web server, your applicaiton and the necessary configuration to make it work. you can also able to create your own images by writing a Dockerfile, Dockerfile has the steps to build the image. Each steps of instruction in the Dockerfile forms a layer, and when you rebuild the image( Docker does the cachin of the layers), only layers that have changes are recreated. This process helps keep Docker images small and efficient compared to other virtulizaion mthhods.

## Steps to Install Docker

Detailed instruciton to install Docker provided in below Link

https://docs.docker.com/get-docker/

## Start the Docker and Grant Access

After you have installed docker using the sudo access, Do not forget to Start the Docker daemon and grant acess to the user you want to use to interact with docker and run docker commands.

Always ensure the docker daemon is up and running.

Try to verify your Docker installation by running bellow command

```
docker run Hello-World

```

If you get permission denied output try running bellow command 

```
docker run -help

```

If you are going through above steps means Docker daemon is not running and user does not have access to run docker commands as you have install docker using sudo.


To overcome above problem follow below steps.

#### Stat docker daemon

```
sudo systemctl status docker

```

### Grant Access to your user to run docker commands

To grant access to your user to run the docker command, you should add the user to the Docker group. Docker group has been created by default when docker is installed.

```
sudo usermod -aG docker ubuntu

```

In the above command `ubuntu` is the name of the user, you can change the username appropriately.

**NOTE:** : For above changes to be reflected, you will need to logout and login back.

### Docker is Installed, up and running 🥳🥳

Use the same command to ensure docker is up and running

```
docker run hello-world

```

Output should look like this

```
....
....
Hello from Docker!
This message shows that your installation appears to be working correctly.
...
...
```

## Now we can write our own Dockerfile. 

Refer a Dockerfile in the folder provided and uild an image with command

docker build -t nilam232/my-first-image:latest .

## Verify Docker images is created!! Use below command

docker images 

## Run your First container with below command

docker run -it nilam232/my-first-image:latest 

### Push the Image to DockerHub and share it with the world

docker push nilam232/my-first-image:latest .


#### Thats all !! you are a Pro of Docker!!!

