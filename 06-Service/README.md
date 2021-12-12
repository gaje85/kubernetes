```
  
   kubectl  apply -f helloworld.yaml 
   kubectl  get deploy 
   kubectl  get svc 
   
   kubectl  get pods 
   kubectl  expose deploy springboot-deployment
   kubectl  get svc 
   curl <ipaddress of service>
   kubectl edit svc springboot-deployment
   kubectl  get svc 
   kubectl describe svc springboot-deployment
   kubectl  get pods -o wide --show-labels
   kubectl  get pods --show-labels
   
   kubectl  get svc 
   kubectl  delete svc springboot-deployment
   
   kubectl  apply -f helloworld-svc.yaml 
   kubectl  get svc 
   kubectl describe svc springboot-service
   
    
    
    kubectl  apply -f app-svc-deployment.yaml 
    kubectl  get deploy,svc,pods 
    
    kubectl  describe svc springboot-svc
    kubectl  get pods -o wide 
    
    kubectl exec -it springbootdeployment-5447cd58fc-84cld  -- sh 
   
    kubectl logs  springbootdeployment-5447cd58fc-84cld 
    
```
