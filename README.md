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