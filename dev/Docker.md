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
```

