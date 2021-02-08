# BASIC KUBECTL COMMANDS

## Get status of diff components 
Create and Edit a pod.

1. kubectl create

```kubectl create deployment NAME --image=image```
```➜  ~ kubectl create deployment nginx-depl --image=nginx```

NOTE: The above one is the most basic config.
Replicasets is managed by default.

```bash
➜  ~ kubectl get replicasets
NAME                    DESIRED   CURRENT   READY   AGE
nginx-depl-5c8bf76b5b   1         1         1       11m
➜  ~
```

NOTE: to edit deployment file
```bash
kubectl edit deployment nginx-depl
```

change image to nginx:1.16

```➜  ~ kubectl get pods
NAME                          READY   STATUS              RESTARTS   AGE
nginx-depl-5c8bf76b5b-bqnlq   1/1     Running             0          16m
nginx-depl-7fc44fc5d4-q848g   0/1     ContainerCreating   0          9s
```

2. 
```bash
kubectl logs nginx-depl-5c8bf76b5b
```

NOTE: If you want to see the logs of the application running on that container.

```bash
kubectl create deployment mongo-depl --image=mongo
```

## DEBUGGING

1. 
NOTE: if you want to see the details of a pod, how it started (more debugging info)
```➜  ~ kubectl describe pod mongo-depl-5fd6b7d4b4kubectl ```

2. 
NOTE: to see streaming logs - log to console
```bash
kubectl logs mongo-depl-5fd6b7d4b4-zdh6q -f
```

3. attach a terminal to a pod
```bash
kubectl exec -it mongo-depl-5fd6b7d4b4-zdh6q -- bin/bash
```

### DEPLOYMENT

1. NOTE: kubectl delete deployment - will delete the pods and repliaset as well and deployment as well.

```bash
kubectl delete deployment mongo-depl
```


### Use config file

in practice, you work with the config file for the deployment.
it is impractical to write all the options in command line
you write a config file and tell k8 to use it for deployment

```bash
kubectl apply -f k8/nginx-deployment.yaml
```

NOTE: if i want three replicas now. Just change config. and apply again
also k8 knows when to create or update a deployment



## SUMMARY

1. CRUD Commands

create, edit and delete deployment
NOTE: delete deployment will also delete the associated replicasets and pods

 ```bash
    kubectl create deployment nginx-depl --name=nginx
    kubectl edit deployment nginx-depl
    kubectl delete deployment nginx-depl
    kubectl describe 
 ```

 2. Status of diff K8 components
 ```bash
    kubectl get nodes/ pods/ replicasets / services / deployments
```

 3. Debugging Pods
log to console
get interactive terminal
get info about the pod (more debugging info)

```bash
kubectl logs pod_name
kubectl exec -it pod_name -- bin/bash
kubectl describe pod pod_name
```

4. Use config file for CRUD
apply a config file
update a config file - Just update the params and again do the apply

NOTE:
if you want o delete the deployment/service directly delete the file. Deployment will be gone , pods replicaset everything will be gone.

```bash
kubectl apply -f k8/nginx-deployment.yaml
kubectl delete -f file_name
```


