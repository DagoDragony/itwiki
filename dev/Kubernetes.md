Kubernetes

# CSP
Clout Service Providers

Almost all CSP offers hosted or managed kubernetes
* AWS (Amazon Web Services) offers EKS (Elastic Container Service for Kubernetes)
* GCP (Google Cloud Platform) offers GKE (Google Kubernetes Engine)
* MS Azure offers AKS (Azure Container service)




Needed packages to install
```
docker
kubectl
conntrack
```

```
docker --version
systemctl status docker
docker run hello-world
docker image ls # list all images locally
docker image rm imgName
docker container ls --all # list all docker containers
docker network ls
docker container stop containerName 
docker container kill containerName
docker container logs --tail 100 containerName
```

