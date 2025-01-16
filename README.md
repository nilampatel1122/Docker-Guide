# Docker-Guide
# This Repository provides complete guide for engineers to learn Docker from scratch.
# Learn docker with Examples.

## If you find this repository useful please give it a star

### What is Docker?

Docker is a powerful containerization platform that simplifies the process of packaging and deploying applications. With Docker, you can build container images, run these images to create containers, and push the container images to registries like DockerHub, Quay.io, and others for easy sharing and deployment.

### Docker Architecture?

![alt text](<Screenshot 2025-01-16 140224.png>)

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

