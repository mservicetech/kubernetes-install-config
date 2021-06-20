# Kubernetes-install-config

## Introduction

Kubernetes is an open source platform for managing container technologies such as Docker.

Docker lets you create containers for a pre-configured image and application. Kubernetes provides the next step, allowing you to balance loads between containers and run multiple containers across multiple systems

![diagram](docs/k8s.PNG)



## Content

Kubernetes requires an existing Docker installation. Install docker on each node

- [Install & Enable docker](docker-install.md)

Install Kubernetes

- [Install Kubernetes](k8s-install.md)


Deploy Kubernetes and set the Kubernetes Cluster

- [Deploy Kubernetes & Kubernates cluster config](k8s-deploy.md)



## Use the Kubernetes Cluster



To start using your cluster, you need to run the following as a regular user:

```

  mkdir -p $HOME/.kube
  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  sudo chown $(id -u):$(id -g) $HOME/.kube/config

```

Use the follow command to verify

```
kubectl get nodes
kubectl get ns
kubectl get po --all-namespaces

```

## Firewall 

enable the firewall and allow ssh and https connection only to the nodes. Also allow the connection between nodes.

On the k8s1

```
sudo ufw enable
sudo ufw allow ssh
sudo ufw allow 443
sudo ufw allow from {k8s2IP}
sudo ufw allow from {k8s3IP}
sudo ufw status
```

On the k8s2

```
sudo ufw enable
sudo ufw allow ssh
sudo ufw allow 443
sudo ufw allow from {k8s1IP}
sudo ufw allow from {k8s3IP}
sudo ufw status

```


On the k8s3

```
sudo ufw enable
sudo ufw allow ssh
sudo ufw allow 443
sudo ufw allow from {k8s1IP}
sudo ufw allow from {k8s2IP}
sudo ufw status

```
