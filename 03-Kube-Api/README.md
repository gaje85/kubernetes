```  
  cat /etc/kubernetes/manifests/kube-apiserver.yaml
    kubectl get pods -n kube-system
    kubectl cluster-info
    kubectl api-versions
    kubectl api-resources
    kubectl proxy --address='10.142.0.47' --port=8001 --accept-hosts='.' --accept-paths='.' &
    ip address is the internal ip of master node 
    curl -k 10.142.0.47:8001
    curl -k 10.142.0.47:8001/
    curl -k 10.142.0.47:8001/api
    kubectl config view
    kubectl get pods
    cd /root/.kube/
    ls
    cat config
    
``` 
