# Kubernetes Data Lab - Big Data Ecosystem Project

We decided to run our Data Lab locally, through a Minikube Kubernetes Cluster.

## Basic Requirements

* 2 CPUs or more
* 2GB of free memory
* 20GB of free disk space
* Internet connection

If you don't have these basic requirements, we're afraid you can't run our project 😢

## Requirements

* Docker (or similarly compatible) container or a Virtual Machine environment
* Kubernetes
* Kubectl
* Minikube

In case you don't have these requirements, please follow the instructions on this [this article](https://minikube.sigs.k8s.io/docs/start/)


## Setting-up Minikube on macOS Intel environment

From a terminal with administrator access, install [Homebrew Package Manager](https://brew.sh/) by running:

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

If you don't have Docker nor Kubernetes installed, follow these steps:

```sh
brew install docker
```

```sh
brew install kubernetes
```

Now install Minikube:
```sh
brew install minikube
```

## Start the cluster

```sh
minikube start
```

## Deploying the Jupyter on the cluster

We implemented Service and Deployment configurations in order to run the Jupyter lab on our cluster. We also made our [Dockerfile](https://github.com/seb-jul/kubernetes-data-lab/tree/main/Notebook_dockerfile) for specific dependencies. Run on your terminal the following:

```sh
kubectl apply -f Config_Jupyter/jupyter-service.yaml
kubectl apply -f Config_Jupyter/jupyter-deployment.yaml
```

Finally, run on your terminal:

```sh
minikube service jupyter-service
```

You should have access of the Jupyter on the nodeport 30080

Inter the password: `'password'` to connect to the environment


## Deploying MongoDB

We implemented [here](https://github.com/seb-jul/kubernetes-data-lab/tree/main/mongodb) several configuration files to run MongoDB on our cluster.

Run on your terminal the following:

```sh
kubectl apply -f mongodb/mongo-service.yaml
kubectl apply -f mongodb/mongo-deployment.yaml
kubectl apply -f mongodb/mongo-config.yaml
kubectl apply -f mongodb/mongo-secret.yaml
```
You can test now by importing the library in a new notebook

```sh
import pymongo
```
