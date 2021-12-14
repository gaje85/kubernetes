# K8s Datastore - ETCD

## Check the status of ETCD
```
kubectl get pods -n kube-system | grep -i  etcd
```

## Let explore ETCD POD
```
kubectl exec -it etcd-kmaster -n kube-system   -- /bin/sh
```

## Check the ETCD Status
```  
# ETCDCTL_API=3 etcdctl --cacert="/etc/kubernetes/pki/etcd/ca.crt"  --cert="/etc/kubernetes/pki/etcd/server.crt" --key="/etc/kubernetes/pki/etcd/server.key" endpoint status  --write-out=table

+----------------+------------------+---------+---------+-----------+------------+-----------+------------+--------------------+--------+
|    ENDPOINT    |        ID        | VERSION | DB SIZE | IS LEADER | IS LEARNER | RAFT TERM | RAFT INDEX | RAFT APPLIED INDEX | ERRORS |
+----------------+------------------+---------+---------+-----------+------------+-----------+------------+--------------------+--------+
| 127.0.0.1:2379 | c22785f83a00f446 |   3.4.3 |  5.0 MB |      true |      false |         2 |      37052 |              37052 |        |
+----------------+------------------+---------+---------+-----------+------------+-----------+------------+--------------------+--------+
#
```

## Checking the ETCD Prefix
```
ETCDCTL_API=3 etcdctl --cacert="/etc/kubernetes/pki/etcd/ca.crt"  --cert="/etc/kubernetes/pki/etcd/server.crt" --key="/etc/kubernetes/pki/etcd/server.key" get / --prefix --keys-only

```
