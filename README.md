# Kubernetes-With-Ansible

透過 [Infrastructure as Code](https://en.wikipedia.org/wiki/Infrastructure_as_code) 來管控與設定系統狀態，並且達成快速自動化部署多台伺服器的一套軟體工具。

- 以 YML 格式撰寫，容易上手與維護
- 使用 SSH 與遠端伺服器群溝通
- 不需安裝中間代理(ansible)在遠端伺服器群

基於以上特性，我們可以透過 Anisble 快速的部署 Kubernetes Cluster 。

## Features

### OS Distributions

- [X] Ubuntu 
  - [X] 20.04
- [ ] CentOS

### CNI (Container Network Interface)
- [X] Flannel
  - [X] VXLAN
  - [ ] host-gw
- [ ] Calico 

### CRI (Container Runtime Interface)
- [X] Docker
- [ ] containerd
- [ ] cri-o

## ToolBox

### Initialize Cluster

- [X] Support single master control plane - `ansible-playbook -i hosts build-k8s-cluster.yaml -K`
- [X] Support high available control plane - `ansible-playbook -i hosts build-ha-k8s-cluster.yaml -K`

### Cleanup Cluster
- [X] Reset the cluster - `ansible-playbook -i hosts reset-cluster.yaml -K`

### Zero Downtime Upgrade

- [ ] kubeadm
- [ ] Replace CRI

## Prerequisite

- Edit `hosts` and `group_vars/all.yaml` as your desired 
