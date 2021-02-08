# TERMS

1. strategy:
    rollingUpdate:
      maxSurge: 25%
      maxUnavailable: 25%
    type: RollingUpdate

***Rolling update*** - Rolling updates allow Deployments' update to take place with zero downtime by incrementally updating Pods instances with new ones

***maxSurge*** - 25% (at max there will only 125% desired pods are up)
currentPods - 100, scale to 150
K8 will ensure, that there is atmost 150*1.25 pods.

***maxUnavailable*** - Deployment ensures that only a certain number of Pods are down while they are being updated. By default, it ensures that at least 75% of the desired number of Pods are up (25% max unavailable).

