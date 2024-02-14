# Install Kubernetes Cluster using kubeadm

Set up a Kubernetes cluster on __Ubuntu 20.04 LTS__.

This documentation guides you in setting up a cluster with one master node and two worker node.

## Assumptions

1) One Master node with Ubuntu 20.04 LTS OS and 4 GB RAM and 50 GB DISK Space.Machine named as master
2) Two Worker node with Ubuntu 20.04 LTS OS and 4 GB RAM and 50 GB DISK Space.Machine named as worker1 and worker2

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

### Enable Kernel Module 
```
modprobe overlay
modprobe br_netfilter
lsmod | egrep 'br_netfilter|overlay'
```
#### Install containerd
```
apt update
apt install -y curl gnupg2 software-properties-common apt-transport-https ca-certificates

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

apt update
apt install containerd.io=1.6.25-1
containerd config default > /etc/containerd/config.toml

Edit in the file /etc/containerd/config.toml  SystemdCgroup = true .This config will be false . Change it to true 
vi /etc/containerd/config.toml

systemctl restart containerd
systemctl enable containerd

```
### Kubernetes Setup
#### Add Apt repository
```
apt-get update
apt -y install curl vim git wget apt-transport-https gpg
mkdir -m 755 /etc/apt/keyrings
curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.28/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg
echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.28/deb/ /' | sudo tee /etc/apt/sources.list.d/kubernetes.list

```
#### Install Kubernetes components
```
apt update
apt -y install kubelet=1.28.4-1.1 kubeadm=1.28.4-1.1 kubectl=1.28.4-1.1
apt-mark hold kubelet kubeadm kubectl

kubectl version --client && kubeadm version
```
### Enable Kubelet
```
systemctl enable kubelet

```


## On master
#### Initialize Kubernetes Cluster
Update the below command with the private ip address of master.If we are using AWS or GCP cloud then we need to use the private ipaddress of the 
VM's used to create the master node 
```
kubeadm config images pull
kubeadm init --control-plane-endpoint <Master node private ipaddress>:6443 --pod-network-cidr=192.168.0.0/16  --ignore-preflight-errors=all
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
kubectl create -f https://raw.githubusercontent.com/projectcalico/calico/v3.26.4/manifests/tigera-operator.yaml
wget https://raw.githubusercontent.com/projectcalico/calico/v3.26.4/manifests/custom-resources.yaml

kubectl apply -f custom-resources.yaml

This process will take some time until all of the pods are running, you can watch the process by executing this command:

kubectl get pod --all-namespaces --watch


check the master node readyness once all the pods are there in the running state in the above command 
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

