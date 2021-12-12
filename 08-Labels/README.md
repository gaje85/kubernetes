``` 
    kubectl get nodes 
    kubectl get nodes --show-labels
       
    kubectl create -f helloworld-nodeselector.yaml 
    kubectl get pods 
    kubectl describe pod helloworld-deployment-57986b947d-7p2nx
    kubectl get nodes
    kubectl label nodes worker2 hardware=virtual
    kubectl get nodes --show-labels
    kubectl get pods 
    kubectl get pods -o wide 
    kubectl label nodes worker1 hardware=virtual
    kubectl get pods -o wide 
    kubectl get nodes --show-labels
    kubectl get pods -o wide 
    kubectl scale --replicas=6 deploy springboot-deployment
    kubectl get po
    
    kubectl scale --replicas=3 deploy springboot-deployment
    
    kubectl create -f helloworld-nodeselector-multi.yaml 
    kubectl get pods 
    kubectl describe pod springboot-deployment-2-7fd7bbcd7-86jfs
    kubectl label nodes worker1 env=prod
    kubectl get pods 
    kubectl get pods -o wide 
     kubectl get nodes --show-labels
     kubectl get pods -o wide 
     kubectl label nodes worker1 env-
     kubectl label nodes worker1 hardware-
     kubectl get nodes --show-labels
     kubectl get pods -o wide 
     kubectl label nodes worker1 hardware=virtual
     kubectl get nodes --show-labels
     kubectl label nodes worker2 hardware-
     kubectl get nodes --show-labels
     kubectl get pods -o wide 
     kubectl scale --replicas=5 deploy springboot-deployment
     kubectl get pods -o wide 
     ls
     kubectl label nodes worker1 hardware-
     kubectl label nodes worker1 env-
     kubectl label nodes worker2 env-
     kubectl get pods

``` 
