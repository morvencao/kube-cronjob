# KUBE-CRONJOB

## Overview

A kubernetes cronjob implementation with [kubebuilder](https://github.com/kubernetes-sigs/kubebuilder).

## Prerequisites

- [go](https://golang.org/dl/) version v1.13+.
- [docker](https://docs.docker.com/install/) version 17.03+.
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/) version v1.11.3+.
- [kustomize](https://sigs.k8s.io/kustomize/docs/INSTALL.md) v3.1.0+
- Access to a Kubernetes v1.11.3+ cluster.

## Getting Started

### Cloning the repository

Checkout this kube-cronjob repository

```
$ mkdir -p $GOPATH/src/github.com/morvencao
$ cd $GOPATH/src/github.com/morvencao
$ git clone git@github.com:morvencao/kube-cronjob.git
$ cd kube-cronjob
```

### Pulling the dependencies

Run the following command

```
$ go mod tidy
```

### Test It Out locally

You’ll need a Kubernetes cluster to run against. You can use [KIND](https://sigs.k8s.io/kind) to get a local cluster for testing, or run against a remote cluster.

> Note: the controller will automatically use the current context in the kubeconfig file (i.e. whatever cluster `kubectl cluster-info` shows).

Install the CRDs into the cluster:

```
make install
```

Run your controller (this will run in the foreground, so switch to a new terminal if you want to leave it running):

```
make run
```

### Install Instances of Custom Resources

```
kubectl apply -f config/samples/
```

### Run It On the Cluster

Build and push your image to the location specified by `IMG`:

```
$ make docker-build docker-push IMG=<some-registry>/<project-name>:tag
```

Deploy the controller to the cluster with image specified by `IMG`:

```
make deploy IMG=<some-registry>/<project-name>:tag
```

> Note: If you encounter RBAC errors, you may need to grant yourself cluster-admin privileges or be logged in as admin.

### Uninstall CRDs

To delete your CRDs from the cluster:

```
make uninstall
```
