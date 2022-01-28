# Install HA proxy
Install HA proxy in a separate machine (VM)
```
sudo su -

sudo apt-get update && sudo apt-get upgrade -y

sudo apt-get install haproxy -y

vi /etc/haproxy/haproxy.cfg


```
Add Below lines to the frontend configuration
```
frontend fe-apiserver
   bind 0.0.0.0:6443
   mode tcp
   option tcplog
   default_backend be-apiserver
```

Add the below lines to create a backend configuration for master1 and master2 nodes at port 6443. Note : 6443 is the default port of kube-apiserver

```
backend be-apiserver
   mode tcp
   option tcplog
   option tcp-check
   balance roundrobin
   default-server inter 10s downinter 5s rise 2 fall 2 slowstart 60s maxconn 250 maxqueue 256 weight 100

       server master1 10.138.0.15:6443 check
       server master2 10.138.0.16:6443 check

```


Here - master1 and master2 are the names of the master nodes and 10.138.0.15 and 10.138.0.16 are the corresponding internal IP addresses.

Restart and Verify haproxy

```
systemctl restart haproxy
systemctl status haproxy

```
Ensure haproxy is in running status.

Run nc command as below -

```
nc -v localhost 6443
Connection to localhost 6443 port [tcp/*] succeeded!
```
# Start Master1 on a separate VM 

Follow the same steps from 02 kubeadm setup for master and replace the kubeadm command with below command 

Give the private ip address of the load balancer in the below command

```
kubeadm init --control-plane-endpoint "loadbalancer:6443" --upload-certs --pod-network-cidr=192.168.0.0/16 
```
Your output should look like below -
```
To start using your cluster, you need to run the following as a regular user:

  mkdir -p $HOME/.kube
  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  sudo chown $(id -u):$(id -g) $HOME/.kube/config

You should now deploy a pod network to the cluster.
Run "kubectl apply -f [podnetwork].yaml" with one of the options listed at:
  https://kubernetes.io/docs/concepts/cluster-administration/addons/

You can now join any number of the control-plane node running the following command on each as root:

  kubeadm join loadbalancer:6443 --token cnslau.kd5fjt96jeuzymzb \
    --discovery-token-ca-cert-hash sha256:871ab3f050bc9790c977daee9e44cf52e15ee37ab9834567333b939458a5bfb5 \
    --control-plane --certificate-key 824d9a0e173a810416b4bca7038fb33b616108c17abcbc5eaef8651f11e3d146

Please note that the certificate-key gives access to cluster sensitive data, keep it secret!
As a safeguard, uploaded-certs will be deleted in two hours; If necessary, you can use 
"kubeadm init phase upload-certs --upload-certs" to reload certs afterward.

Then you can join any number of worker nodes by running the following on each as root:

kubeadm join loadbalancer:6443 --token cnslau.kd5fjt96jeuzymzb \
    --discovery-token-ca-cert-hash sha256:871ab3f050bc9790c977daee9e44cf52e15ee37ab9834567333b939458a5bfb5 
```
Save the above output

# Setup Master2 in a separate VM

Set up master node as per 02 kubeadm instructions. Do not run kubeadm init .

```

kubeadm join loadbalancer:6443 --token cnslau.kd5fjt96jeuzymzb \
    --discovery-token-ca-cert-hash sha256:871ab3f050bc9790c977daee9e44cf52e15ee37ab9834567333b939458a5bfb5 \
    --control-plane --certificate-key 824d9a0e173a810416b4bca7038fb33b616108c17abcbc5eaef8651f11e3d146

```

Your output should look like -

```
 This node has joined the cluster and a new control plane instance was created:

* Certificate signing request was sent to apiserver and approval was received.
* The Kubelet was informed of the new secure connection details.
* Control plane (master) label and taint were applied to the new node.
* The Kubernetes control plane instances scaled up.
* A new etcd member was added to the local/stacked etcd cluster.

```

Now 2 master nodes is configured . 

# Configure worker nodes 

# configuer kubeconfig on loadbalancer node 

```
mkdir -p $HOME/.kube
scp master1:/etc/kubernetes/admin.conf $HOME/.kube/config
chown $(id -u):$(id -g) $HOME/.kube/config
```

install kubectl library
```
snap install kubectl --classic
```
Verify the cluster

```
kubectl get nodes 

NAME      STATUS     ROLES    AGE     VERSION
master1   NotReady   master   21m     v1.16.2
master2   NotReady   master   15m     v1.16.2
worker1   NotReady   <none>   9m17s   v1.16.2
worker2   NotReady   <none>   9m25s   v1.16.2
```
# Install CNI and complete installation

```
kubectl apply -f https://docs.projectcalico.org/v3.8/manifests/calico.yaml
```
kubectl get nodes 

NAME      STATUS   ROLES    AGE   VERSION
master1   Ready    master   22m   v1.16.2
master2   Ready    master   17m   v1.16.2
worker1   Ready    <none>   10m   v1.16.2
worker2   Ready    <none>   10m   v1.16.2

