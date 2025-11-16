# Docker Cheat Sheet

## Getting Started

- **Docker** is a platform for developing, shipping, and running applications in
  containers
- **Dockerfile** - blueprint for building a Docker image
- **Docker Image** - template for running Docker containers
- **Docker Container** - a running instance of an image
- Check Docker version: `docker --version`
- Check Docker info: `docker info`
- Docker system info: `docker system df`

## Container Management

### Running Containers

- Run container: `docker run <image>`
- Run in detached mode: `docker run -d <image>`
- Run with name: `docker run --name <name> <image>`
- Run with port mapping: `docker run -p <host_port>:<container_port> <image>`
- Run with environment variable: `docker run -e <VAR>=<value> <image>`
- Run with volume: `docker run -v <host_path>:<container_path> <image>`
- Run with interactive terminal: `docker run -it <image>`
- Run and remove on exit: `docker run --rm <image>`
- Run with network: `docker run --network <network_name> <image>`
- Run with resource limits: `docker run --memory="512m" --cpus="1.0" <image>`

### Container Lifecycle

- Start container: `docker start <container_id_or_name>`
- Stop container: `docker stop <container_id_or_name>`
- Restart container: `docker restart <container_id_or_name>`
- Pause container: `docker pause <container_id_or_name>`
- Unpause container: `docker unpause <container_id_or_name>`
- Kill container: `docker kill <container_id_or_name>`
- Remove container: `docker rm <container_id_or_name>`
- Remove running container: `docker rm -f <container_id_or_name>`
- Remove all stopped containers: `docker container prune`

### Container Information

- List running containers: `docker ps`
- List all containers: `docker ps -a`
- Container logs: `docker logs <container_id_or_name>`
- Follow logs: `docker logs -f <container_id_or_name>`
- Container stats: `docker stats <container_id_or_name>`
- Container processes: `docker top <container_id_or_name>`
- Inspect container: `docker inspect <container_id_or_name>`
- Execute command in container: `docker exec <container_id_or_name> <command>`
- Interactive shell: `docker exec -it <container_id_or_name> /bin/bash`
- Container diff: `docker diff <container_id_or_name>`

## Image Management

### Building Images

- Build image: `docker build -t <tag> <path>`
- Build from current directory: `docker build -t <tag> .`
- Build with Dockerfile: `docker build -f <dockerfile> -t <tag> <path>`
- Build without cache: `docker build --no-cache -t <tag> <path>`
- Build with build args: `docker build --build-arg <ARG>=<value> -t <tag> <path>`

### Image Operations

- List images: `docker images`
- Remove image: `docker rmi <image_id_or_name>`
- Remove all unused images: `docker image prune`
- Remove all images: `docker image prune -a`
- Inspect image: `docker inspect <image_id_or_name>`
- Image history: `docker history <image_id_or_name>`
- Tag image: `docker tag <source> <target>`
- Save image: `docker save -o <file.tar> <image>`
- Load image: `docker load -i <file.tar>`

### Docker Hub

- Login: `docker login`
- Logout: `docker logout`
- Pull image: `docker pull <image>`
- Push image: `docker push <image>`
- Search images: `docker search <term>`

## Dockerfile Basics

- `FROM <image>` - base image
- `WORKDIR <path>` - set working directory
- `COPY <src> <dest>` - copy files from host to container
- `ADD <src> <dest>` - copy files (supports URLs and tar extraction)
- `RUN <command>` - execute command during build
- `CMD ["executable", "param"]` - default command to run
- `ENTRYPOINT ["executable", "param"]` - main command (not overridable)
- `EXPOSE <port>` - document port (doesn't publish it)
- `ENV <key>=<value>` - set environment variable
- `ARG <key>=<value>` - build-time variable
- `VOLUME ["/path"]` - create mount point
- `USER <user>` - set user for subsequent commands
- `LABEL <key>=<value>` - add metadata

## Volumes

- Create volume: `docker volume create <volume_name>`
- List volumes: `docker volume ls`
- Inspect volume: `docker volume inspect <volume_name>`
- Remove volume: `docker volume rm <volume_name>`
- Remove unused volumes: `docker volume prune`
- Mount volume: `docker run -v <volume_name>:<container_path> <image>`
- Bind mount: `docker run -v <host_path>:<container_path> <image>`
- Named volume: `docker run -v <name>:<container_path> <image>`

## Networks

- Create network: `docker network create <network_name>`
- List networks: `docker network ls`
- Inspect network: `docker network inspect <network_name>`
- Remove network: `docker network rm <network_name>`
- Remove unused networks: `docker network prune`
- Connect container to network: `docker network connect <network> <container>`
- Disconnect container: `docker network disconnect <network> <container>`

### Network Types

- Bridge (default): `docker network create --driver bridge <name>`
- Host: `docker network create --driver host <name>`
- None: `docker network create --driver none <name>`
- Overlay: `docker network create --driver overlay <name>`

## Docker Compose

### Overview

- **Docker Compose** - tool for running multi-container Docker applications
- Compose file: `docker-compose.yml` or `docker-compose.yaml`
- Start services: `docker-compose up`
- Start in detached mode: `docker-compose up -d`
- Start specific service: `docker-compose up <service_name>`
- Build and start: `docker-compose up --build`
- Stop services: `docker-compose down`
- Stop and remove volumes: `docker-compose down -v`
- Stop and remove images: `docker-compose down --rmi all`

### Compose Commands

- Build services: `docker-compose build`
- Build without cache: `docker-compose build --no-cache`
- Start services: `docker-compose start`
- Stop services: `docker-compose stop`
- Restart services: `docker-compose restart`
- View logs: `docker-compose logs`
- Follow logs: `docker-compose logs -f`
- View logs for service: `docker-compose logs <service_name>`
- Execute command: `docker-compose exec <service> <command>`
- Run one-off command: `docker-compose run <service> <command>`
- List services: `docker-compose ps`
- Scale services: `docker-compose up --scale <service>=<count>`

### Compose File Structure

```yaml
version: '3.8'
services:
  service_name:
    image: <image>
    build: <context>
    ports:
      - '<host_port>:<container_port>'
    environment:
      - <VAR>=<value>
    volumes:
      - <host_path>:<container_path>
    networks:
      - <network_name>
    depends_on:
      - <other_service>
volumes:
  volume_name:
networks:
  network_name:
```

### Common Compose Options

- `image` - image to use
- `build` - build context or Dockerfile path
- `ports` - port mappings
- `environment` - environment variables
- `env_file` - file with environment variables
- `volumes` - volume mounts
- `networks` - networks to connect to
- `depends_on` - service dependencies
- `restart` - restart policy (no, always, on-failure, unless-stopped)
- `command` - override default command
- `entrypoint` - override entrypoint
- `working_dir` - working directory
- `user` - user to run as

## Colima (macOS)

### Installation and Setup

- **Colima** - container runtime for macOS (alternative to Docker Desktop)
- Install Colima: `brew install colima`
- Start Colima: `colima start`
- Start with specific resources: `colima start --cpu 4 --memory 8`
- Stop Colima: `colima stop`
- Restart Colima: `colima restart`
- Delete Colima: `colima delete`
- Status: `colima status`
- List instances: `colima list`

### Colima Configuration

- Start with custom config: `colima start --edit`
- CPU allocation: `colima start --cpu <number>`
- Memory allocation: `colima start --memory <GB>`
- Disk size: `colima start --disk <GB>`
- VM type: `colima start --vm-type <vz|qemu>`
- Architecture: `colima start --arch <x86_64|aarch64>`
- Kubernetes: `colima start --kubernetes`
- Network mode: `colima start --network-address`

### Colima with Docker

- After starting Colima, Docker CLI works normally
- Set Docker context: `docker context use colima`
- List contexts: `docker context ls`
- Default context: `docker context use default`

### Colima with Docker Compose

- Docker Compose works with Colima automatically
- Use `docker-compose` or `docker compose` commands
- No additional configuration needed

## System Management

- System information: `docker system df`
- System prune: `docker system prune`
- Prune all: `docker system prune -a`
- Prune volumes: `docker system prune --volumes`
- Events: `docker events`
- Version: `docker version`
- Info: `docker info`

## Useful Tips

- Use `.dockerignore` to exclude files from build context
- Use multi-stage builds for smaller images
- Use specific tags instead of `latest`
- Use volumes for persistent data
- Use networks for container communication
- Use health checks: `HEALTHCHECK` in Dockerfile
- Use docker-compose for multi-container apps
- Use Colima on macOS for lightweight container runtime
- Clean up regularly: `docker system prune`
- Use `docker exec` to debug running containers
- Use `docker logs` to troubleshoot issues
- Use `docker inspect` to view container/image details
