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
```

