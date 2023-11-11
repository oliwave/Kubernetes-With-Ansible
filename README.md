# Kubernetes-With-Ansible

Configure the system in an IaC way to automate the deployment of multiple servers.

- Written in YML format, easy to use and maintain

- Use SSH to communicate with remote server groups

- No need to install intermediate agents in remote server groups

Based on the above characteristics, we can quickly deploy the Kubernetes Cluster through Anisble.

## Features

### OS Distributions

- [X] Ubuntu 
  - [X] 20.04
<!-- - [ ] CentOS -->

### CNI (Container Network Interface)
- [x] Flannel
  - [x] VXLAN
  - [ ] host-gw
- [ ] Calico

### CRI (Container Runtime Interface)
- [X] Docker
- [X] containerd
- [X] cri-o

## ToolBox

### Initialize Cluster

- [X] Support single master control plane - `ansible-playbook -i hosts build-k8s-cluster.yaml -K`
- [X] Support high available control plane - `ansible-playbook -i hosts build-ha-k8s-cluster.yaml -K`

### Add worker/master node dynamically
- [X] worker - `ansible-playbook -i hosts add-worker-node.yaml -K`
- [ ] master

### Cleanup Cluster
- [X] Reset the cluster - `ansible-playbook -i hosts reset-cluster.yaml -K`

### Zero Downtime Upgrade

- [ ] kubeadm
- [ ] Replace CRI

## Prerequisite

- Edit `hosts` and `group_vars/all.yaml` as your desired 
