# Ingress Cantroller required the following clusterroles bindings to be applied.
```
kubectl create clusterrolebinding add-on-cluster-admin   --clusterrole=cluster-admin   --serviceaccount=kube-system:default
kubectl create clusterrolebinding add-on-cluster-admin-1   --clusterrole=cluster-admin   --serviceaccount=default:default
```

