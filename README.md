# Kubernetes-With-Ansible

透過 [Infrastructure as Code](https://en.wikipedia.org/wiki/Infrastructure_as_code) 來管控與設定系統狀態，並且達成快速自動化部署多台伺服器的一套軟體工具。

- 以 YML 格式撰寫，容易上手與維護
- 使用 SSH 與遠端伺服器群溝通
- 不需安裝中間代理(ansible)在遠端伺服器群

基於以上特性，我們可以透過 Anisble 快速的部署 Kubernetes Cluster 。
在本範例中 Kubernetes Control Plane 為 Single Master Node。

## 安裝 Ansible

在工作電腦上安裝 Ansible

### Ubuntu
```
$ sudo apt update
$ sudo apt install software-properties-common
$ sudo apt-add-repository --yes --update ppa:ansible/ansible
$ sudo apt install ansible
```


### Other platform

[Installing Ansible on other platforms](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#)

## 在遠端伺服器上執行 Kubernetes 的安裝

1. 進入 `Kubernetes-With-Ansible` 專案
    > $ cd <your_workspace>/k8s_setup

2. **將 `hosts` 裡面的伺服器設定成自己的目標**

3. 執行 ansible 的 playbook

    > $ ansible-playbook -i hosts site.yaml -K
    
## 專案結構
- `site.yaml` 作為 ansible 主要的執行程式

- `roles` 劃分不同種類的工作內容
    - `roles/k8s-common` 針對**所有伺服器**都需要執行的設定(安裝 docker、kubeadm 等等)
    - `roles/master` 針對 **master 伺服器** 需要執行的設定(安裝 kubectl 以及設定 dns 等等)
    - `roles/worker` 針對 **worker 伺服器** 需要執行的設定 (加入 K8s cluster)
    
- `hosts` 為 ansible 要讀取的 [inventory](https://chusiang.github.io/ansible-docs-translate/intro_inventory.html)，用來註冊需要被遠端控制的伺服器群