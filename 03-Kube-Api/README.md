```  
  cat /etc/kubernetes/manifests/kube-apiserver.yaml
    kubectl get pods -n kube-system
    kubectl cluster-info
    kubectl api-versions
    kubectl api-resources
    kubectl proxy --address='172.31.0.10' --port=8001 --accept-hosts='.' --accept-paths='.' &
    curl  172.31.0.10:8001
    curl  172.31.0.10:8001/
    curl  172.31.0.10:8001/api
    kubectl config view
    kubectl get pods
    cd /root/.kube/
    ls
    cat config
    
``` 
