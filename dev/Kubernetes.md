Kubernetes

For learning and experimenting locally minicube can be used
Limitation is that it runs only on 1 node

https://labs.play-with-k8s.com/ - k8s sandbox/playground

# Create Kubernetes node from zero

```
kubeadm init    # master
kubeadm join .. # for slaves
```


# CSP
Clout Service Providers

Almost all CSP offers hosted or managed kubernetes
* AWS (Amazon Web Services) offers EKS (Elastic Container Service for Kubernetes)
* GCP (Google Cloud Platform)
	* GKE (Google Kubernetes Engine)
	* GCE (Google Compute Engine)
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

gcloud components list
kubectl cluster-info [dump]

~/.kube/config
kubectl config view |grep token
kubectl proxy --port=8001

kubectl get nodes
kubectl get events
kubectl get services
kubectl get pods
kubectl get pods --namespace=kube-system

gcloud compute ssh --zone "us-central1-b" "kubernetes-master"
docker container ls --format 'table {{.Image}}\t{{.Status}}' 

kubernetes/cluster/kube-up.sh # tear down the cluster
```

# Minicube

```
minicube start

kubectl run hello-minikube --image=k8s.gcr.io/echoserver:1.4 --port=8080
kubectl expose deployment hello-minikube --type=NodePort

minikube dashboard
```

# Patterns

* Sidecar - app container is unaware of the sidecar container and just goes it's business
* Ambassador pattern - represent remote service as if it was local
* Adapter pattern - about standardizing output from the main application container
* Multinode

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

