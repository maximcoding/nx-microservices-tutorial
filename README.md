## Nx Microservices Architecture

Run `nx list` to get a list of available plugins and whether they have generators. Then run `nx list <plugin-name>` to see what generators are available.
Learn more about [Nx generators on the docs](https://nx.dev/plugin-features/use-code-generators).

### Setup nx-workspace
```npx create-nx-workspace```

### Generate express / Nestjs microservices#
### In case
```npm i --save-dev @nx/express```
```nx generate @nrwl/express:application mx-users```
### Create DockerFile in new microservice

## Setup Your Environment
```brew update```
### NX - is build system with first class monorepo support and powerful integrations.
```npm install -g nx```
### kubectl - The Kubernetes command-line tool
```brew install kubectl```
### Docker - is an open source containerization platform.
```brew cask install docker```
```sudo apt install docker-compose```
### Minikube - is minikube is local Kubernetes
```brew cask install minikube```
### Virtualbox - is a general-purpose full virtualizer for x86 hardware, targeted at server, desktop and embedded use.
```brew cask install virtualbox```

-----
### Check Installation
1. ```kubectl version --client```
2. ```docker --version```
3. ```docker-compose --version```
4. ```docker-machine --version```
5. ```minikube version```


### Configure environment to use minikube’s Docker daemon
```eval $(minikube -p minikube docker-env)```

---
## Local Development

### Start the kubernetes cluster with minikube
```minikube start```
### Check if minikube node is ready
```kubectl get nodes```
### Build docker images of express microservices
```nx build mx-users && nx build my-app2```

### Configure environment to use minikube’s Docker daemon
```minikube docker-env ```
### Copy and run the "eval" command from the output
```eval $(minikube -p minikube docker-env)```

### Build the docker images
```docker build -f ./apps/mx-users/Dockerfile . -t mx-users```
```docker build -f ./apps/my-app2/Dockerfile . -t my-app2```

### ⚠️️ [internal] load metadata for docker.io/library/node:18
#### Solution:
- 1. open ~/.docker/config.json
- 2. remove "credsStore": "desktop"

----
### Check whether docker images has been created
```docker images --format "table {{.ID}}\t{{.Tag}}\t{{.Repository}}"```

-----
## Deployment Process to Kubernetes

### Create manifest config files in each microservice root dir: https://kubernetes.io/docs/concepts/configuration/overview/
   1. ```mx-users/deployment.json```
   2. ```mx-users/service.json```

### Apply the configuration in deployment.json and service.json to a pod
 ```kubectl apply -f apps/mx-users/deployment.json```

### Check if pods are running#
```kubectl get pods```

### Check if services are running#
```kubectl get services```

### Access services outside the node (minikube is able to create tunnel )#
```minikube service mx-users --url```
### Open up http://127.0.0.1:53401/api
### You should see the following JSON response:
```{"message":"Welcome to svc-cart!"}```
### 🚀 🚀 🚀 Open another terminal instance and run another service 🚀 🚀 🚀

### Monitor services with minikube dashboard#
### ```minikube dashboard```


### how to deploy microservices with ArgoCD https://argo-cd.readthedocs.io/en/stable/

---- 
### ⚠️ ⚠️ ⚠️ COMMON ISSUES   ⚠️ ⚠️ ⚠️️

