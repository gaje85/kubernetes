``` 
    kubectl get nodes 
    kubectl get nodes --show-labels
       
    kubectl create -f helloworld-nodeselector.yaml 
    kubectl get pods 
    kubectl describe pod helloworld-deployment-57986b947d-7p2nx
    kubectl get nodes
    kubectl label nodes worker hardware=virtual
    kubectl get nodes --show-labels
    kubectl get pods 
    kubectl get pods -o wide 
   
   
    
    kubectl create -f helloworld-nodeselector-multi.yaml 
    kubectl get pods 
    kubectl describe pod springboot-deployment-2-7fd7bbcd7-86jfs
    kubectl label nodes worker env=prod
    kubectl get pods 
    kubectl get pods -o wide 
     kubectl get nodes --show-labels
    
     kubectl label nodes worker env-
     kubectl label nodes worker hardware-
     kubectl get nodes --show-labels
     kubectl get pods -o wide 
     kubectl label nodes worker hardware=virtual
     kubectl get nodes --show-labels
    
     kubectl label nodes worker hardware-
     
     
     kubectl get pods

``` 
