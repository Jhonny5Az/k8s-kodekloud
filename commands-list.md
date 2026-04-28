
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
## See all resources 
```
kubectl get all
```
## Delete all
```
kubectl delete -f .
```

## Get Node configuration
```
kubectl get node -o wide
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

## Deployments
```
kubectl get deployments
kubectl get deployment my-first-deployment -o yaml
kubectl describe deployment myapp-deployment
kubectl apply -f deployment-definition.yml
kubectl set image deployment/myapp-deployment \ nginx=nginx:1.9.1
kubectl set image deploy frontend simple-webapp=kodekloud/webapp-color:v2
kubectl create -f .\deployment\deployment.yaml --record
> Scale  deployment
kubectl scale deployment vote --replicas=5
```

## Rollout
```
kubectl rollout undo deployment myapp-deployment
kubectl rollout status deployment/myapp-deployment
kubectl rollout history deployment/myapp-deployment
```

## Service
> NodePort
```
kubectl create -f service-definition.yml
kubectl get service || kubectl get svc
```


## Namespace
```
Create Namespace: kubectl create namespace my-namespace
Create Pod: kubectl run my-pod --image=nginx --namespace=my-namespace 
```

## Cronjobs
```
kubectl create cronjob my-job --image=busybox --schedule="*/5 * * * *" -- date
kubectl get cronjob
kubectl logs <pod-name>
trigger without waiting: kubectl create job --from=cronjob/hello-cronjob manual-run-01
```

## Jobs
```
Generate and save to file:
kubectl create job my-job --image=perl:5.34 --dry-run=client -o yaml > job-template.yaml
Create from a CronJob template:
kubectl create job manual-run --from=cronjob/my-cronjob
kubectl logs -l job-name=sleep-job
kubectl get jobs
```

## Jobs
```
kubectl exec time-check -n devops -- cat /opt/dba/time/time-check.log
kubectl exec time-check -n devops -- ps aux
kubectl exec time-check -n devops -- df -h | grep dba
```