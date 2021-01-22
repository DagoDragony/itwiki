Kubernetes

```
kubectl get all # get all active parts
kubectl delete deployment.apps/myDeployment # delete by get all
kubectl describe pod

kubectl config view # view configurations of contexts
kubectl config use-context ppprocessingmstapi # change current context

kubectl edit deployment task0
kubectl edit configmaps
kubectl edit service task2

kubectl get pods | grep mstapi |  awk '{print $1}' | xargs -I % sh -c "kubectl logs --since=1h % mstapi" # get 1h errors
```

