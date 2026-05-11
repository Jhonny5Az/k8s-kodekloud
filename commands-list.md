
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
kubectl exec -it <pod-name> -- /bin/bash
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

## Describe configmaps
```
kubectl get pod
kubectl get configmap
kubectl describe configmap nginx-config
```
## Download the pod definition and modify the conf
```
kubectl get pod nginx-phpfpm -o yaml > /tmp/nginx.yaml
sed -i 's|/usr/share/nginx/html|/var/www/html|g' /tmp/nginx.yaml
kubectl replace -f /tmp/nginx.yaml --force
```
## Copy to container file
```
kubectl cp /home/thor/index.php nginx-phpfpm:/var/www/html -c nginx-container
```
## Get VPC and pod ip assigned
```
aws ec2 describe-vpcs --query 'Vpcs[*].{VpcId:VpcId,CidrBlock:CidrBlock}' --output table
kubectl get pod nginx -o jsonpath='{.status.podIP}'
```

curl -o aws-k8s-cni.yaml https://raw.githubusercontent.com/aws/amazon-vpc-cni-k8s/master/config/master/aws-k8s-cni.yaml


## Utility AWS eksdemo - eksctl
```
eksdemo get clusters
eksdemo get vpc
eksdemo get subnets
eksdemo get network-interface
kubectl logs -n kube-system aws-node-g9h8w -c aws-vpc-cni-init
```
## Get ec2 instance id of node
```
kubectl get nodes -o custom-columns=NAME:.metadata.name,INSTANCE_ID:.spec.providerID
```

## Debug a Node
```
# 1. Identify the node name
kubectl get nodes

# 2. Start a debug session on the target node
kubectl debug node/<NODE_NAME> -it --image=ubuntu
```

aws ssm start-session --target i-038904693471f4a3a
ip a | less
ip route show
ip -6 route shown