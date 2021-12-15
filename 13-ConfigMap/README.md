~~~   
    vim nginx-pod.yml
    vim nginx-service.yaml
    vim reverseproxy.conf
   
    kubectl get configmap
    kubectl create configmap nginx-config --from-file=reverseproxy.conf -o yaml --dry-run=client
    kubectl get configmap
    kubectl create configmap nginx-config --from-file=reverseproxy.conf -o yaml --dry-run=client > ConfigMap.yaml
    vim ConfigMap.yaml
 
   kubectl create -f 13-ConfigMap/
   kubectl get configmap
   kubectl describe configmap nginx-config
   kubectl get pods
   kubectl describe pods helloworld-nginx
   kubectl get svc
   kubectl exec -it  helloworld-nginx -c nginx -- bash
  
~~~