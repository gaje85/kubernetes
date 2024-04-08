# Create a service account 

```
kubectl create namespace myspace
kubectl create serviceaccount my-service-account -n myspace

```

# deploy role and rolebinding and pod

```
kubectl apply -f pod-reader-role.yaml -n myspace
kubectl apply -f pod-reader-rolebinding.yaml -n myspace
kubectl apply -f my-pod.yaml -n myspace


```


# verify listing the pod 

```
kubectl exec -it my-pod -n myspace -- /bin/bash

# Now inside the my-pod container
kubectl get pods
kubectl describe pods

```





