```
  
   kubectl  apply -f helloworld.yaml 
   kubectl  get deploy 
   kubectl  get svc 
   kubectl  delete svc springboot-deployment
   
   kubectl  get deploy 
   kubectl  get pods 
   kubectl  expose deploy springboot-deployment
   kubectl  get svc 
   curl <ipaddress of service>
   kubectl edit svc springboot-deployment
   kubectl  get svc 
   kubectl describe svc springboot-deployment
   kubectl  get pods -o wide --show-labels
   kubectl describe svc springboot-deployment
   kubectl  get pods --show-labels
   kubectl describe svc springboot-deployment
   
   kubectl  get svc 
   kubectl  delete svc springboot-deployment
   
   kubectl  apply -f helloworld-svc.yaml 
   kubectl  get svc 
   kubectl describe svc springboot-service
   
    
    kubectl  apply -f app-svc-deployment.yaml 
    kubectl  apply -f app-svc-deployment.yaml 
    kubectl  get deploy,svc,pods 
    kubectl  get pods 
    kubectl  get deploy,svc,pods 
    kubectl  describe svc springboot-svc
    kubectl  get pods -o wide 
    kubectl  describe svc springboot-svc
    kubectl exec -it springboot-deployment-54b95bd8d-xgsdm -- sh 
    kubectl exec -it python-webapp-deployment-54b95bd8d-xgsdm 
    kubectl exec -it python-webapp-deployment-54b95bd8d-xgsdm -- cat app.py 
    kubectl logs  python-webapp-deployment-54b95bd8d-xgsdm
    vim /etc/hosts
```
