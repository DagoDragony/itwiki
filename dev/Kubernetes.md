Kubernetes

# CSP
Clout Service Providers

Almost all CSP offers hosted or managed kubernetes
* AWS (Amazon Web Services) offers EKS (Elastic Container Service for Kubernetes)
* GCP (Google Cloud Platform) offers GKE (Google Kubernetes Engine)
* MS Azure offers AKS (Azure Container service)

# GCP

```
curl https://sdk.cloud.google.com | bash # install gcp sdk
gcloud auth login                        # login - routes you to browser and lets connect through google acc
gcloud config list project               # list current project
gcloud config set project <PROJECT ID>
gcloud alpha projects list               # list all existing projects


mkdir ~/code/gsw-k8s-3
cd ~/code/gsw-k8s-3
curl -sS https://get.k8s.io | bash

gcloud components install beta
kubernetes/cluster/kube-up.sh


```



Needed packages to install
```
docker
kubectl
conntrack ```

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

