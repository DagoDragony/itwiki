Docker

Workflow
1. Build
2. Share
3. Run

Parts
1. Docker Client(cli that wraps docker rest api(liker docker cmd) or some other software)
2. Docker Server(linux systemd service docker)
3. containerd(container runtime(overseen by CNCF, and fits OCI) that is used by docker)

Registries - image servers (like docker hub)

To create/modify docker container there are 2 ways
* use `Dockerfile`
* go to docker container, modify it and save

```
yay -S docker docker-compose
systemctl enable docker
systemctl start docker # start docker daemon(or so called docker engine or server) 
docker version # check status of docker
docker info
docker-compose version

docker-compose version

docker container rm -f $(docker container ls -aq) # clean docker containers
docker container rm --force $(docker container ls --all --quiet) # force remove containers event if they are running
docker image rm -f $(docker image ls -f reference='diamol/*' -q) # remove docker images

docker container run diamol/ch02-hello-diamol # hello world docker application
docker container run --interactive --tty diamol/base # connect to terminal session in container

docker container ls # get all running containers
docker container ls --all # get all running containers
docker container top c93f7c0db61a # show running processes in container
docker container logs c9 # first id member is enough no specifi if start is unique
docker container inspect c9

docker container run --detach --publish 8088:80 diamol/ch02-hello-diamol-web
docker container stats 96 # show live stats
docker exec -it 6ba /bin/bash # run shell in container
docker container cp index.html 86b:/usr/local/apache2/htdocs/index.html # copy local file into container

docker image pull diamol/ch03-web-ping
https://hub.docker.com/r/diamol/ch03-web-ping

docker container run -d --name web-ping diamol/ch03-web-ping
docker container logs web-ping

docker container run --env TARGET=http://www.google.com diamol/ch03-web-ping # no detach, logs are shown directly

docker image build --tag web-ping . # to build docker image
docker image ls 'w*' # list image cache

docker image history web-ping
docker image ls
docker system df # show how much actually docker images use disk

# mofify docker container and save modifications to image
docker container run -it --name ch03lab diamol/ch03-lab
echo Elton >> ch03.txt
exit
docker container commit ch03lab ch03-lab-soln
docker container run ch03-lab-soln cat ch03.txt

docker network create nat
docker container run --name iotd -d -p 800:80 --network nat image-of-the-day

docker -dit web-ping
docker atach web-ping

docker network inspect bridge | less
```

# RUN, CMD, ENTRYPOINT

* RUN - executes cmds in a new layer and creates a new image. I.e installing software packages
* CMD - set default command and/or parameters, which can be overwritten from cli when docker runs
* ENTRYPOINT - makes docker file executable

Forms
* shell (/bin/sh -c <cmd>
  ```
  RUN apt-get install python3
  CMD echo "Hello world"
  ENTRYPOINT echo "Hello world"
  ...
  $ Hello, John Dow
  ```
* exec (<instruction ["executable", "param1", "param2", ...] prefered for CMD and ENTRYPOINT
  ```
  RUN ["apt-get", "install", "python3"]
  CMD ["/bin/echo", "Hello world"]
  ENTRYPOINT ["/bin/echo", "Hello world"]
  ...
  $ Hello, $name
  ```
  
## CMD

Forms
1. `CMD ["executable","param1","param2"]` (exec form, preferred)
2. `CMD ["param1","param2"]` (sets additional default parameters for ENTRYPOINT in exec form)
3. `CMD command param1 param2` (shell form)

```
CMD echo "Hello world"
...
# cmd is ignored when docker container runs with command line parameters
docker run -it <image> /bin/bash # CMD is ignored and /bin/bash is ran instead
```

## ENTRYPOINT

Forms
1. Exec
   ```
   ENTRYPOINT ["/bin/echo", "Hello"]
   CMD ["world"]
   
   docker run -it <image>
   $ Hello world
   
   docker run -it <image> John
   $ Hello John
   ```
2. Shell - ignores any CMD or docker run command line args(not like Exec)

# Push docker images

```
docker login --username <dockerId> # loging to default docker registry
docker image tag image-gallery <dockerId>/image-gallery:v1
docker image ls --filter reference=image-gallery --filter reference='*/image-gallery'
docker image push <dockerId>/image-gallery:v1
echo "https://hub.docker.com/r/<dockerId>/image-gallery/tags"
```

# Persistent Storage

* Dockerfile VOLUME
  Volumes are created per container
  If you want to use volume from other container, you can do it by running with --volumes-from <containerName>
* Named volumes - create by docker volume create <volumeName>
* Bind mounts - mounts folder in host to docker container
  Can be used for optimizations like SSD or safety RAID etc.
  
Storage types
* Writeable layer - pefect for short-term storage. Unique to container, gone when container is removed
* Local bind mounts - for sharing data between host and container. Fits for source file changes on local pc
* Distributed bind mounts -for sharing data between network storage and containers. Has various limitations
* Volume mounts - for sharing data between the container and a storage object, that is managed by docker
* Image layers - these present the initial filesystem for the container.
  Stacked overriden by earlier layers, layers are read-only, can't be shared between containers


```
docker container run --name todo1 -d -p 8010:80 diamol/ch06-todo-list
docker container inspect --format '{{.Mounts}}' todo1
docker volume ls

docker volume create todo-list # named volume
docker container run -d -p 8011:80 -v todo-list:/data --name todo-v1 diamol/ch06-todo-list
docker container rm -f todo-v1
docker container run -d -p 8011:80 -v todo-list:/data --name todo-v2 diamol/ch06-todo-list:v2
# after recreation all data is still in same persistent named volume

source="$(pwd)/datbases" && target='/data'
mkdir ./databases
docker container run --mount type=bind,source=$source,target=$target -d -p 8012:80 diamol/ch06-todo-list
curl http://localhost:8012
ls ./databases
```

# Multiple Docker Containers Run

docker-compose.yml

```
docker-compose up --detach --scale iotd=3
docker-compsoe logs --tail=1 iotd
docker-compose stop
docker-compose start
docker container ls
```

# various

```
docker search -s 5 mysql # retuns images with 5 stars or more

```

