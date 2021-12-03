# Creating out First App

## Check the health of Cluster
```
kubectl get nodes 
```

## Deploy Hello OK App
```
kubectl run hello-k8s --image=gcr.io/google_containers/hpa-example --port=80
```

## Check the status of PODs 
```  
kubectl get pods 
kubectl describe pods hello-k8s
```
```
kubectl get pods

```


## Deploy Nginx App
```
kubectl apply -f hello-k8s.yaml
```

## Check the status of PODs 
```  
kubectl get pods 
kubectl describe pods hello-k8s
```

## Deploy python App
```
kubectl apply -f pythonflaskapp.yaml
```

## Check the status of PODs 
```  
kubectl get pods 
kubectl describe pods flask-demo-app
```

