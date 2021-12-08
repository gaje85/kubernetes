# Install Kubernetes Cluster using kubeadm

Set up a Kubernetes cluster on __Ubuntu 20.04 LTS__.

This documentation guides you in setting up a cluster with one master node and two worker node.

## Assumptions

1) One Master node with Ubuntu 20 OS and 4 GB RAM and 100 GB DISK Space.Machine named as master
2) Two Worker node with Ubuntu 20 OS and 2 GB RAM and 100 GB DISK Space.Machine named as worker1 and worker2

## On both master and worker

#### Login as `root` user
```
sudo su -
```
Perform all the commands as root user unless otherwise specified

#### Disable Firewall
```
ufw disable
```
#### Disable swap
```
swapoff -a; sed -i '/swap/d' /etc/fstab
```
#### Update sysctl settings for Kubernetes networking
```
cat >>/etc/sysctl.d/kubernetes.conf<<EOF
net.bridge.bridge-nf-call-ip6tables = 1
net.bridge.bridge-nf-call-iptables = 1
EOF
sysctl --system
```
#### Install docker engine
```
{
  apt install -y apt-transport-https ca-certificates curl gnupg-agent software-properties-common
  curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
  add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
  apt update
  apt install -y docker-ce=5:19.03.10~3-0~ubuntu-focal containerd.io
}
```
### Kubernetes Setup
#### Add Apt repository
```
{
  curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
  echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" > /etc/apt/sources.list.d/kubernetes.list
}
```
#### Install Kubernetes components
```
apt update && apt install -y kubeadm=1.18.5-00 kubelet=1.18.5-00 kubectl=1.18.5-00
```
If we just give kubeadm kubelet and kubectl without version then the latest will be installed (1.22 or 1.23 version) 

#### In case you are using LXC containers for Kubernetes nodes
Hack required to provision K8s v1.15+ in LXC containers
```
{
  mknod /dev/kmsg c 1 11
  echo '#!/bin/sh -e' >> /etc/rc.local
  echo 'mknod /dev/kmsg c 1 11' >> /etc/rc.local
  chmod +x /etc/rc.local
}
```

## On master
#### Initialize Kubernetes Cluster
Update the below command with the ip address of master.If we are using AWS or GCP cloud then we need to use the private ipaddress of the 
VM's used to create the master node 
```
kubeadm init --apiserver-advertise-address=<Master node ipaddress> --pod-network-cidr=192.168.0.0/16  --ignore-preflight-errors=all
```
#### Deploy Calico network
```
kubectl --kubeconfig=/etc/kubernetes/admin.conf create -f https://docs.projectcalico.org/v3.14/manifests/calico.yaml
```

#### Cluster join command
```
kubeadm token create --print-join-command
```

#### To be able to run kubectl commands as non-root user
If you want to be able to run kubectl commands as non-root user, then as a non-root user perform these
```
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
```

## On worker
#### Join the cluster
Use the output from kubeadm token create command in previous step from the master server and run here.

## Verifying the cluster (On master)
#### Get Nodes status
```
kubectl get nodes
```
#### Get component status
```
kubectl get cs
```
