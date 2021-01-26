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

```
kubectl create deployment mongo-depl --image=mongo

NOTE: if you want to see the details of a pod, how it started
```➜  ~ kubectl describe pod mongo-depl-5fd6b7d4b4-zdh6q```

```bash
kubectl logs mongo-depl-5fd6b7d4b4-zdh6q -f
```