Kubernetes

For learning and experimenting locally minicube can be used
Limitation is that it runs only on 1 node

* Init containers
* Deployment - highges level of pod manager
* ReplicaSet - responsible for keebing pod number
* pod

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

minikube dashboard

kubectl run hello-minikube --image=k8s.gcr.io/echoserver:1.4 --port=8080
kubectl expose deployment hello-minikube --type=NodePort


kubectl get componentstatuses # check status of etcd and others
kubectl get nodes -o json | less

kubectl create -f nodejs-pod.yaml
kubectl describe pods/node-js-pod
kubectl get pod node-js-pod --template={{.status.podIP}}
kubectl exec node-js-pod -- curl `kubectl get pod node-js-pod --template={{.status.podIP}}`
kubectl exec -it node-js-pod -- /bin/bash
kubectl exec node-js-pod -- ls / # dashes in case command has same args as kubectl

kubectl create -f nodejs-controller.yaml
kubectl create -f nodejs-rc-service.yaml

kubectl get pods
kubectl describe pod/node-js-p484w

minikube ssh # ssh to node with pods(minikube supports only 1 node)
	sudo docker ps --filter="name=node-js"
	sudo docker stop <node-express container id>
	sudo docker rm <container id>
	sudo docker ps --filter="name=node-js"

```

```
kubectl config set-context --current --namespace=my-namespace
kubectl apply -f busybox-pod.yaml
kubectl delete po busybox
kubectl get pod busybox -o wide
kubectl describe pod busybox # get pod info
kubectl get po busybox -o jsonpath={..image} # get running container image
kubectl edit pod busybox # edit online, imperative way(not recomended), upon save changes will be synchronized
kubectl delete -f busybox-pod.yaml # delete everything that we declared by given .yaml

kubectl scale --replicas=2 deployment/nginx # imperative(not recomended) way
kubectl delete po -o wide # delete pod, however if deployment defined pods, new is started right after

# relicasets manages number of pods
# if you want your pod not to be restarted after kill, you need to delete replicaset
kubectl get replicaset
kubectl delete rs nginx-7b8964db65
# however after kill we see that is was recreated, it's because deployment manages replicasets
kubectl get replicaset

kubectl get deploy # get deployment list
kubectl delete deploy nginx # deletes all that is with deployment
```


# Patterns

* Sidecar - app container is unaware of the sidecar container and just goes it's business
* Ambassador pattern - represent remote service as if it was local
* Adapter pattern - about standardizing output from the main application container
* Multinode

# Cluster nodes
master nodes components only run on a subset of the Kubernetes cluster, but the node  components run
everywhere

* Kubelet
* Kube-proxy
* Container runtime

# Init Containers

* Prepare env for containers(i.e. apply sysctl params, download files, etc)
* Do not start containers until other external services are available

```
# init cotainers won't be visible in get po, only here
kubectl describe pod nginx-7fd7896f47-8hwbg
```

# ConfigMap

```
kubectl apply -f nginx-config.yaml
kubectl get configmap # list config maps
kubectl get configmap configName -o yaml
```

# Network Policies

```
kubectl create -f nginx-policy.yaml
```



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

