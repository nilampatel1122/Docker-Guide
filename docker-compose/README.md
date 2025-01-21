## What is Docker compose?
  Docker compose is a tool used to define and manage multi-container Docker Application. It allows you to define and run services, networks, environment variables and volume which requires by application in a single docker-compose.yml file. docker-compose.yml file makes easier to build, deploy and run complex application with multiple interdependent containers. 

## Install Docker compose on ubuntu

### command: 
    sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

    sudo chmod +x /usr/local/bin/docker-compose
### verify docker compose installation

    docker-compose --version

## Docker Compose YAML file.

    Docker Compose configurations are mainly stored in a file named docker-compse.yml. 
    This file includes all the necessary details to set up and run your apllications.

### Key Elemnets of the docker-compose yaml file

    - Version: It defines the format of the Compose file, by ensuring the compatibility with
        specific Docker Compose features and syntax.

    - Services: In this section you can list each containerised service required for the
        application. Each service will have its configuration such as image to use, environment variables, resource limits.

    - Neworks: Here you can define custom networks, which enables container to communicate with
        each other. It also allows you to specify network drivers and custom settings for organizing container interactions. 

    - Volumes: Volumes allows for data persistence acrss container restarts and can be shared
        between containers if needed. It enables you to store data outside the containers lifecycle and make it use for to share storage or preserv in for applicaiton state.

    - Build: you can build your own custom image by specifying the directory containing
        dockerfile.

    - Environment: you can pass Environment variables such as configurations or sensitive
        information.

    - Depends_on: It controls the startup order of the services by ensuring that certain
        containers are runing before other start executing.

    - Ports: This maps a container's internal ports to those on the host machine. Which enables
      access to services from outside the container.

## docker-compose.yml
    please see example of docker-compose.yml



