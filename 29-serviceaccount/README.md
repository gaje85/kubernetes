# Create a service account 

```
kubectl create namespace myspace
kubectl create serviceaccount my-service-account -n myspace

```

# deploy role and rolebinding 

```
kubectl apply -f pod-reader-role.yaml -n my-namespace
kubectl apply -f pod-reader-rolebinding.yaml -n my-namespace

```


# create Cluster role binding 

```

# Validate service account access via kubectl 

# validate service account call via api access





