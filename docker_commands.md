## Docker commands

### Basics

test simple image
```bash
docker run hello-world
```

list all containers (active and inactive)
```bash
docker ps -a
```

list all images
```bash
docker images
```

delete container
```bash
docker rm <containername>
```

delete image
```bash
docker image rm <imagename>
```

download latest image
```bash
docker image pull <imagename>
```

stop container
```bash
docker stop <containername>
```

restart container
```bash
docker start <containername>
```

create container with name und hostname
```bash
docker run -it --name <containername> -h <hostname> ubuntu
```

create container with port forwarding
```bash
docker run -p <hostport>:<containerport> <imagename>
```

create container, running in background
```bash
docker run -d <imagename>
```

create container with named volume, mounted on /var/lib/mysql
```bash
docker run -d -v <volumename>:/var/lib/mysql <imagename>
```

create container with volume in local directory, mounted on /var/lib/mysql

**ATTENTION:** path to local directoy must start with a '/' under linux,
otherwise it is interpreted as an named volume
```bash
docker run -d -v /some/path/:/var/lib/mysql <imagename>
```

### Inspection

inspect details of an image
```bash
docker image inspect
```

inspect details of a container
```bash
docker inspect <container name>
```

inspect details of the volume, doesnt work with bind mounts
```bash
docker volume inspect <64 long hex Code>
```

show details for memory of all container, images and volumes
```bash
docker system df -v
```

list memory space of containers
the shown memory space is virtual, meaning it includes the image space, 
with is possibly shared by several containers
```bash
docker ps -a -s 
```

### Interaction

use container interactively
```bash
docker run -it <containername>
```

restart container interactively
```bash
docker start -ai <containername>
```

start a additional process in container, useful to inspect the container
```bash
docker exec -it <containername> /bin/bash
```
start a mariadb client in the container
```bash
docker exec -it <containername> mariadb -u root -p
```

### Logs

view logs of a specific container
```bash
docker logs <container name>
```

view logs of docker-compose
```bash
docker-compose logs
```
view logs of docker-compose for a specific container
```bash
docker-compose logs <container name>
```

### Networking

test internet connection for docker network
```bash
docker run --rm alpine ping -c 4 google.com
```

get docker network interface and monitor connection
for example: docker0 is network interface of docker
```bash
ifconfig 
sudo tcpdump -i docker0 
```

### Clean-up

show all volumes with containers that are already deleted
```bash
docker volume ls -q -f dangling=true
```

delete all volumes with containers that are already deleted
```bash
docker volume prune
```

delete all inactive containers and images not used by other images

**ATTENTION:** Use with caution
```bash
docker system prune 
```

delete all inactive containers and images not used by other images
in addition all volumes and images that are not used by containers

**ATTENTION:** Use with caution
```bash
docker system prune -a --volumes
```
