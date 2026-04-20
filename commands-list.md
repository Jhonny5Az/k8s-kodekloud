
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