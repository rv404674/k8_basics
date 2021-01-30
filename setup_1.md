# SETUP

You just need a hypervisor for minikube
`brew install minikube`.
It will install kubectl as well, because kubectl has a dependency on minkube.
https://minikube.sigs.k8s.io/docs/start/


# COMMANDS

1. minikube start --vm-driver=hyperkit
starts the cluste

2. kubectl get nodes
status of the nodes

3. minikube status
will tell the status

```bash
➜  ~ minikube status
minikube
type: Control Plane
host: Running
kubelet: Running
apiserver: Running
kubeconfig: Configured
timeToStop: Nonexistent
```

4. kubectl version

5. NOTE:
minikube will only be used to start the cluster and delete it.
if there is something wrong with your minikube cluster, then you can delete it and start it in debug mode.

```bash
minikube start --vm-driver=hyperkit --v=7 --alsologtostderr
```


