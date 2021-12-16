# Setting up NFS Server for K8s PV Demo. 

## Install Nfs Server 
```
apt-get install nfs-kernel-server -y 
mkdir /exports
chown nobody:nogroup /exports
```

## NFS Export Path & Share Config
```
root@master: grep -i exports /etc/exports
vi /etc/exports and write the below content in to it 
/exports  *(rw,sync,no_subtree_check)

```

## Restart the NFS Server Service
```
systemctl restart nfs-kernel-server
systemctl status  nfs-kernel-server
```

## Vertify the NFS Share
```
showmount -e localhost 
```


# On Client / Worker Nodes 

## Install NFS Client Utils 
```
apt-get install nfs-common -y
mount -t nfs 10.142.0.10:/exports /mnt/

The above ipaddress of the Master node private IP address since we installed NFS in master node

cd /mnt/
hostname >> hostname.txt
```


```

  
  
   kubectl get pv 
   kubectl apply -f 01-pv-nfs.yaml
   kubectl get pv 
  
   kubectl get pvc 
   kubectl apply -f 02-pvc-nfs.yaml
   kubectl get pvc 
   kubectl get pv
 
   kubectl apply -f 03-nfs-busybox-rc.yaml 
   kubectl get pods 
   kubectl describe pod nfs-busybox-2-fwzwr
  
   kubectl get pods -o wide 
   tail -f  /exports/index.html 
 
   kubectl apply -f 04-web-rc-pvc.yaml
   kubectl apply -f 05-nfs-web-svc.yaml 
   kubectl get svc 
   
   kubectl get svc 
   
   kubectl delete -f 18-Volumes-NFS/
```

