# Install Kubernetes Cluster using kubeadm

Set up a Kubernetes cluster on __Ubuntu 23.10 LTS__.

This documentation guides you in setting up a cluster with one master node and two worker node.

## Assumptions

1) One Master node with Ubuntu 23.10 OS and 4 GB RAM and 50 GB DISK Space.Machine named as master
2) Two Worker node with Ubuntu 23.10 OS and 4 GB RAM and 50 GB DISK Space.Machine named as worker1 and worker2

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
apt update
apt install docker.io
```
### Kubernetes Setup
#### Add Apt repository
```
apt-get update
apt-get install -y apt-transport-https ca-certificates curl gpg
curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.29/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg
echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.29/deb/ /' | sudo tee /etc/apt/sources.list.d/kubernetes.list
apt-get update


```
#### Install Kubernetes components
```
apt-get install -y kubelet kubeadm kubectl
apt-mark hold kubelet kubeadm kubectl

```


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
#### To be able to run kubectl commands as non-root user
If you want to be able to run kubectl commands as non-root user, then as a non-root user perform these
```
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
```
#### Deploy Calico network
```
kubectl create -f https://raw.githubusercontent.com/projectcalico/calico/v3.27.0/manifests/tigera-operator.yaml
kubectl create -f https://raw.githubusercontent.com/projectcalico/calico/v3.27.0/manifests/custom-resources.yaml

kubectl taint nodes --all node-role.kubernetes.io/control-plane-
kubectl taint nodes --all node-role.kubernetes.io/master-
run watch command after 1 min and make sure all the pods are there in running state 
watch kubectl get pods -n calico-system
check the master node readyness
kubectl get nodes -o wide
```

#### Cluster join command
```
kubeadm token create --print-join-command
```



## On worker
#### Join the cluster
Use the output from kubeadm token create command in previous step from the master server and run here.

## Verifying the cluster (On master)
#### Get Nodes status
```
kubectl get nodes -o wide
```

