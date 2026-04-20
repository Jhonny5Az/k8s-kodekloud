# Yaml k8s structure
> Default structure
```
apiVersion: v1 //version api (string)
kind: pod      // type of object try to create (string)
metadata: //Data above the object, like name, labels,etc(dict)
    name: myapp-pod
    labels:
        app: myapp
spec: //Depending of the object(dict)
    container:(list/array)
        - name: nginx-container
          image: nginx

```
# Yaml k8s replicaset
