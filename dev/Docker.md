Docker

```
yay -S docker docker-compose
systemctl enable docker
systemctl start docker # start docker daemon(or so called docker engine or server)

docker version # check status of docker
docker info
docker-compose version

docker-compose version

docker container rm -f $(docker container ls -aq) # clean docker containers
docker image rm -f $(docker image ls -f reference='diamol/*' -q) # remove docker images

docker container run diamol/ch02-hello-diamol # hello world docker application
docker container run --interactive --tty diamol/base # connect to terminal session in container

docker container ls # get all running containers
docker container top c93f7c0db61a # show running processes in container
docker container logs c93f7c0db61a
docker container inspect c93f7c0db61a

```

