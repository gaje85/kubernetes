```
   kubectl  apply -f helloworld.yaml
   kubectl  get pods
   kubectl  describe pod helloworld-deployment-b64578fb-fk294
   kubectl  get nodes
   kubectl  label node worker1 env=prod
   kubectl  get pods -o wide
   kubectl  label node worker2 env=dev
   kubectl get nodes --show-labels
   kubectl  get pods -o wide
   kubectl scale --replicas=5 deploy helloworld-deployment
   kubectl  get pods -o wide
   kubectl scale --replicas=1 deploy helloworld-deployment
   kubectl  get pods -o wide
 
   sdiff helloworld.yaml helloworld-dev-prod.yaml
   kubectl  delete -f helloworld.yaml
  
   kubectl  get deploy
   kubectl  apply -f helloworld-dev-prod.yaml
   kubectl  get pods -o wide
 
   kubectl  delete -f helloworld-dev-prod.yaml
   kubectl get nodes --show-labels
   kubectl  apply -f helloworld-multi-affinity.yaml
   kubectl get pods
   kubectl get pods -o wide
   kubectl delete  -f helloworld-multi-affinity.yaml
   kubectl get nodes --show-labels
   kubectl label node worker1 env-
   kubectl label node worker1 env=dev
   kubectl get nodes --show-labels
   kubectl  apply -f helloworld-multi-affinity.yaml
   kubectl  get pods -o wide
   kubectl delete  -f helloworld-multi-affinity.yaml
  
   kubectl label node worker1 team=engineering-project1
   kubectl  apply -f helloworld-multi-affinity.yaml
   kubectl  get pods -o wide
   kubectl scale --replicas=10 deploy helloworld-deployment
   kubectl  get pods -o wide
   kubectl scale --replicas=20 deploy helloworld-deployment
   kubectl  get pods -o wide
   kubectl scale --replicas=2 deploy helloworld-deployment
   kubectl  get pods -o wide
```
