## Docker commands

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

use container interactively
```bash
docker run -it <containername>
```

download latest image
```bash
docker image pull <imagename>
```
restart container
```bash
docker start <containername>
```

restart container interactively
```bash
docker start -ai <containername>
```

create container with name und hostname
```bash
docker run -it --name <containername> -h <hostname> ubuntu
```

start a additional process in container, useful to inspect the container
```bash
docker exec -it <containername> /bin/bash
```

create container with port forwarding
```bash
docker run -p <hostport>:<containerport> <imagename>
```
create container, running in background
```bash
docker run -d <imagename>
```

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
