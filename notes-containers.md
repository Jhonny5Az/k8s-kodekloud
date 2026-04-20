# Notes Containers
### images is a package, that create multiple containers

## container orchestration (k8s, docker swarm, mesos(apache))
manages and deploy thousand of containers in a cluster

> Node, machines physical or virtual, where k8s runs

> Cluster, set of nodes set together, sharing loads

> Master(node), Managing cluster, watches all nodes, responsible orchestation of containers on the worker nodes.

> By default install the following components, API SERVER, ETCD, Kubelet, Container runtime, Controller, Scheduler

- **API server**, frontend for k8s,
- **Etcd**, distributor reliable key-value store, store all data manage all data. implementes locks not conflicts between the masters.
- **Scheduler**, responsible for distributing work or containers across multiple nodes, looks for new container and assign them to nodes.
- **Controller**, brain behind the orchestation, responsible for when a node, container or end-points goes down, and make desicions to bring up new containers.
- **Container runtime**, is the underlying software that is used to run containers(docker in most cases).
- **Kubelet**, agent that run on each node in the cluster, make sure that the containers are running on the nodes as expected.(numbers as expected)
  
>>*kubectl*, kube control or kube command line, get cluster information, to get status of others nodes in the cluster, **kubectl run** is used to deploy an application on the cluster, **kubectl info** is used to view information about the cluster and the **kubectl get** is used to list all nodes part of the cluster

---
## Docker vs ContainerD
Container Runtime CRI, allow you if you follow the OCI(Open container iniative) **imagespec(how a image is created) and runtimespec(how the runtime are created)**, create a new container runtime integrated with k8s like docker,rkt </br>
Docker (CLI,API,BUILD,VOLUMES,AUTH,SECURITY, THE CONTAINER RUNTIME RUNC AND THE DAEMON THAT MANAGED RUNC CALLED CONTAINERD)not support CRI, tmp used dockershim</br>
>CONTAINERD can work with CRI, and can be used as a runtime on its own separate from docker, kubernetes removed dockershim v1.24, and the docker images continue working because they follow the OCI.</br>

>you can interact with containerd with its utility called **CTR**, which can do limited operations and API calls, because of that you can use the nerd control(nerdcli) which is a tool that its very similar to docker with all the upgrades of CONTAINERD(encrypted container images, lazy pulling, namespaces in kubernetes)</br>

```
    crt images 
    nerdctl 
```

>crictl, command line tool to interact with the CRI() from kubernetes community, from the perspective of kubernetes, work across different contianer runtimes, its used to inspect and debug container runtime, its not ideally to create container, if so kubelet is going to see that its create outside the list it maintain and is gonna be destroyed.</br>

```
    crictl images 
    crictl ps -a
    crictl pods
    crictl --runtime-endpoint (unix:///var/run/dockershim.sock or unix:///run/containerd/containerd.sock or unix:///run/crio/crio.sock or unix:///var/run/cri-dockerd.sock)
```

# Pods
Single object of the applications inside nodes, smaller object that you can create in kubernetes. 1-1 relationship with the container running your application but its not restricted you can have a helper container(processing user data, a file uploaded by the user,etc) alonside a container.