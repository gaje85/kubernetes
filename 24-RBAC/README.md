# Kubernetes RBAC 

## Create a Pod Reader Role
```
kubectl create role pod-reader --verb=get,list,watch --resource=pods --dry-run -o yaml 
kubectl create -f pod-reader-role.yaml
```

## Create a POD Reader RoleBinding 
```
kubectl create rolebinding --help
kubectl create rolebinding read-pod-binding --role=pod-reader --user=test --dry-run -o yaml 
kubectl create -f read-pod-binding.yaml
```

## Check the Roles & Context with role Permissions:
```
kubectl get role
kubectl get rolebinding 

kubectl config get-contexts
kubectl config use-context test@kubernetes
kubectl config get-contexts

kubectl get pods 
kubectl get pods -n myspace
```


# Create a ClutserRole Binding with Cluster Admin role for normal user: test


## View Cluster & Binding via kubernetes-admin context
```
kubectl config get-contexts
kubectl config use-context kubernetes-admin@kubernetes
kubectl config get-contexts
kubectl get pods -n kube-system

kubectl get clusterrole
kubectl describe clusterrole cluster-admin
kubectl get clusterrolebinding
kubectl describe clusterrolebinding cluster-admin
```

## Create a Clusterole binding with existing cluster admin role
```
kubectl create clusterrolebinding admin-user-test --clusterrole=cluster-admin --user=test  --dry-run=client -o yaml 
cat test-cluster-rolebinding.yaml 

kubectl create -f test-cluster-rolebinding.yaml
kubectl get clusterrolebinding
kubectl describe clusterrolebinding admin-user-test
```

## Change the context & validate the role permissions
```
kubectl config get-contexts
kubectl config use-context test@kubernetes
kubectl get pods 
kubectl get pods --all-namespaces
   
kubectl create -f ../05-Deployments/helloworld-v2.yaml 
kubectl get pods 
kubectl delete -f ../05-Deployments/helloworld-v2.yaml 

kubectl config use-context kubernetes-admin@kubernetes

```
