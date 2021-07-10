---
id: a104c545-bf72-4e5e-a3b1-ec7db40358bf
title: Kubernetes
desc: ""
updated: 1622002408193
created: 1621703001520
stub: false
---

# Kubernetes

## Working dev environments

https://kubernetes.io/blog/2018/05/01/developing-on-kubernetes/

## Gotchas

port forward from internal ip insede network, for example: Access to an RDS that k8s network has access only.

https://hub.docker.com/r/marcnuri/port-forward

```bash
kubectl run --env REMOTE_HOST=rds-host-ip --env REMOTE_PORT=5432 --env LOCAL_PORT=25432 --port 5432 --image marcnuri/port-forward test-port-forward

kubectl port-forward test-port-forward 5432:25432
```
