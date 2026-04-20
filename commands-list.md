
## Basic Commands
```
kubectl get nodes
kubectl get nodes -o wide
```

```
kubectl run nginx -image=nginx
kubectl describe pod nginx
```

## Create a manifest file
```
kubectl run redis --image=redis123 --dry-run=client -o yaml > redis-definition.yaml
```
## Deploy a pod
```
kubectl create deployment nginx --image=nginx
```

## Delete pod
```
kubectl delete pod nginx
```

## Create pod
```
kubectl apply -f sample.yaml
```

## Replica Set
> Commands
```
kubectl create -f replicaset-definition.yml
kubectl get replicaset
kubectl edit replicaset myapp-replicaset 
kubectl scale replicaset myapp-replicaset --replicas=2
```
```
kubectl delete replicaset myapp-replicaset 
kubectl apply -f replicaset-definition.yml
kubectl scale --replicas=6 -f replicaset-definition.yml
kubectl scale --replicas=6 replicaset
```

# Deployments


## See all resources 
```
kubectl get all
```