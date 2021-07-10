---
id: ek0wyOwdKnZslLXN92M1L
title: Vault
desc: ""
updated: 1625890422146
created: 1625883934363
---

# Vault Hashicorp

### Injecting Secrets into Kubernetes Pods via Vault Agent Containers

## Questions

![](/assets/images/2021-07-09-23-03-59.png)

1. https://www.youtube.com/watch?v=riI0B5bDkPs&t=215s

- How can I include to kubernettes Cluster?

  - [Demo: Vault + Kubernetes Sidecar Injection](https://www.youtube.com/watch?v=xUuJhgDbUJQ)
  - [Injecting Vault Secrets Into Kubernetes Pods via a Sidecar](#vault-agent-kubernetes)

- Do we need replicas?
- Which kind of authentication do we need?
- Can we used for current dev namespaces?

## Articles Notes

#### Vault Agent Kubernetes

Injecting Secrets into Kubernetes Pods via Vault Agent Containers

Author: backoff 1.562132589
URL: https://learn.hashicorp.com/tutorials/vault/kubernetes-sidecar

---

Authenticate and acquire a client token. _ Manage the lifecycle of the token. _ Retrieve secrets from Vault. \* Manage the leases of any dynamic secrets. Vault Agent takes responsibility for these tasks

    NOTE: The only consideration is to include annotations into the service but it can be patched without a problem.

---
