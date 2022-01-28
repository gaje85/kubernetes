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



