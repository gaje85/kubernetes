# Taint & Tolerations

## Taint the nodes ( worker02 )  
```
kubectl taint nodes worker02 app=myapp:NoSchedule
kubectl describe nodes worker02 | grep -i taint
```


## Untaint the nodes
```
kubectl taint nodes worker02 myapp-
```

```

 kubectl apply -f 01-helloworld.yaml
 kubectl  get pods -o wide
 kubectl  get nodes
 kubectl taint node worker2 app=myapp:NoSchedule
 kubectl  describe node worker2 | grep -i taint
 kubectl  get pods -o wide
 kubectl scale --replicas=10 deploy helloworld-deployment
 kubectl  get pods -o wide
 kubectl scale --replicas=1 deploy helloworld-deployment
 kubectl  get pods -o wide
 kubectl scale --replicas=5 deploy helloworld-deployment
 kubectl  get pods -o wide
  
 kubectl delete -f 01-helloworld.yaml
 kubectl apply -f 02-helloworld-toleration.yaml
 kubectl  get pods -o wide
 kubectl scale --replicas=10 deploy toleration-deployment
 kubectl  delete -f 02-helloworld-toleration.yaml
 
 
 kubectl taint node worker2 app=example:NoSchedule
 kubectl taint node worker2 example=amit:NoSchedule
 kubectl describe nodes | grep -i taint
 
 kubectl describe nodes worker2 | grep -iA10 taint
 
 kubectl  apply -f 02-helloworld-toleration.yaml
 kubectl  get pods -o wide
 kubectl describe nodes worker2 | grep -iA5 taint
 
 kubectl  apply -f 03-helloworld-toleration-2.yaml
 kubectl  get pods -o wide
 kubectl  apply -f 04-helloworld-toleration-3.yaml
 kubectl  get pods -o wide
 kubectl taint node worker1 example2=example2-key:NoExecute
 kubectl  describe node master | grep -i taint
 
 kubectl  apply -f 05-helloworld-ds.yaml
 kubectl  describe node | grep -i taint
 kubectl taint node worker2 app-
 kubectl taint node worker1 example2-
 kubectl  describe node | grep -i taint
 kubectl taint node worker2 example-
 
 kubectl  delete -f 18-Taint-and-Toleration/

```

