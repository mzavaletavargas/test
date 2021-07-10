---
id: 1769ba5b-d9f2-4564-8a8e-a4c4f32169c7
title: Devspace
desc: ""
updated: 1625873307295
created: 1622780489289
---

After installing teleprescense, dealing with imcoptibilities, old documentation, they are passing to a new version and old files and docs are outdated, I decided to give up and use devspace.

Documentation is fine, even if you end up finding some info for version 1 is almost the same for version 2.

There some issues with the documentation but after setting up everything for my team it was great!, we were able to solve the issue to learn a lot of things related to kubernetes and focus on developing our stuff.

## Development

Hands on! Just Run, is it the first time setting your environment? Go here for [1-time steps](#1-time-steps)

```bash
# located in this directory
devspace dev

```

> You may need to use `npm run migrate` for the first time or if you would like to apply migration files using prisma.

```bash
# In a new visual studio terminal to sync files between local and remote pod.
devspace sync
# select `backend-legacy...`

```

## 1-Time steps

Get your environment variables from [1Password](https://start.1password.com/open/i?a=GNL6QEUMMNGZ7GOKC3TMMZQ6FM&h=team-hapi.1password.com&i=5iu3bv2gd2ng2kzlxipz2y2nvm&v=ilpavzwvfrqcgrfafogq65nuee) and save it as `hapi.properties`

> Use your AWS username (RBAC_USERNAME) e.g: `gustavo`

```bash

npm install -g devspace

kubectl create namespace RBAC_USERNAME

devspace use namespace RBAC_USERNAME

# with your hapi.properties file in the base path, set config map values, this is a command defined on devspace.yml that allows you to store some commands
devspace run create-configmap

```

> `devspace run delete-configmap` is available to be used.

Change placeholder RBAC_USERNAME by your ingress configuration `./manifest/ingress.yml`

```yaml
---
spec:
  rules:
    - host: RBAC_USERNAME.hapi.trade
```

Run this command to apply these changes, that way will be exposed and will be shareable.

```bash
devspace run ingress
```

## Database

Conenct to your database using your favorite client and pointing to localhost, username, password and database can be found on `hapi.properties`.

Port `5432` is already exposed and you'll be able to use it.

## Logging

```bash
devspace logs -f
```

## Environment variables

All environment variables had been update when creating configmap on k8s, you can include your own on a `.env` file.

## Debugging with VS Code

Port `9229` is exposed and you will be able to debug your remote pod.
For debugging with docker we have to setup the following configuration on 'launch.json'

```sh
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "HAPI Docker: Attach to node",
            "type": "node",
            "request": "attach",
            "port": 9229,
            "address": "localhost",
            "localRoot": "${workspaceFolder}",
            "remoteRoot": "/usr/src/app",
            "protocol": "inspector",
            "sourceMapPathOverrides": {
                "/usr/src/app/*": "${workspaceRoot}/*",
            },
            "restart": true,
        },
    ]
}
```

## Config file sample

```yaml
version: v1beta10
images:
  app:
    image: image:debug-tag
    dockerfile: ./Dockerfile
    build:
      disabled: true
    # cmd: ['npm', 'run', 'start:debug']

deployments:
  - name: app
    kubectl:
      manifests:
        - ./manifests/microservice-template.yml

# `dev` only applies when you run `devspace dev`
dev:
  logs:
    showLast: 200
    sync: true

  ports:
    - imageName: app # Select the Pod that runs our `app` image
      forward:
        - port: 3000
        - port: 9229


  open:
    - url: http://localhost:3000

  # `dev.sync` configures a file sync between our Pods in k8s and your local project files
  sync:
    - imageName: app # Select the Pod that runs our `app` image
      initialSync: preferRemote
      disableDownload: true
      excludePaths:
        - .git/
      uploadExcludePaths:
        - Dockerfile
        - Dockerfile.dev
        - node_modules/
commands:
  - name: ingress
    command: 'kubectl apply -f manifests/ingress.yml'
  - name: create-configmap
    command: 'kubectl create configmap backend-config --from-env-file=hapi.properties'
  - name: delete-configmap
    command: 'kubectl delete configmap backend-config'

profiles:
  - name: production
      patches:
      - op: remove
        path: images.app.build.disabled

```

## FAQs

- Issue authenticating to download images from EKS

```bash
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 567599088800.dkr.ecr.us-east-1.amazonaws.com
```
