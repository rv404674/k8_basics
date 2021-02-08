
1. Basics
```bash
kubectl get deployment
kubectl delete deployment nginx-deployment
kubectl apply -f k8/nginx-deployment.yaml
```


2. Create a service
```bash
kubectl get pods
kubectl apply -f k8/nginx-service.yaml
```

3. Get Service

```bash
kubectl get service
NAME            TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)   AGE
kubernetes      ClusterIP   10.96.0.1       <none>        443/TCP   7d2h
nginx-service   ClusterIP   10.96.152.141   <none>        80/TCP    33s
# kubernetes is default service
```

*** check whether nginx-service is attached to right pod ***
```bash
kubectl describe service nginx-service
Name:              nginx-service
Namespace:         default
Labels:            <none>
Annotations:       <none>
Selector:          app=nginx
Type:              ClusterIP
IP Families:       <none>
IP:                10.96.152.141
IPs:               10.96.152.141
Port:              <unset>  80/TCP
TargetPort:        8080/TCP
Endpoints:         172.17.0.3:8080,172.17.0.4:8080
Session Affinity:  None
Events:            <none>
# note you have ips in the endpoints, these must be the ips of pds
```

```bash
# -o wide - List all pods in ps output format with more information (such as node name).
kubectl get pod -o wide
```


4. Status
NOTE:
i. Status is automatically managed by K8. (Appended at the end of K8 file).
ii. deployment will fetched from etcd.

```bash
kubectl get deployment nginx-deployment -o yaml

status:
  availableReplicas: 3
  conditions:
  - lastTransitionTime: "2021-02-02T14:35:08Z"
    lastUpdateTime: "2021-02-02T14:35:08Z"
    message: Deployment has minimum availability.
    reason: MinimumReplicasAvailable
    status: "True"
    type: Available
  - lastTransitionTime: "2021-02-02T14:30:03Z"
    lastUpdateTime: "2021-02-02T14:35:13Z"
    message: ReplicaSet "nginx-deployment-f4b7bbcbc" has successfully progressed.
    reason: NewReplicaSetAvailable
    status: "True"
    type: Progressing
  observedGeneration: 2
  readyReplicas: 3
  replicas: 3
  updatedReplicas: 3
```


```bash
kubectl describe deployments
```