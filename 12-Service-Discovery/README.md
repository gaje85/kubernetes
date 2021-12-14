```
   
   cat secrets.yaml
   cat database.yaml
   
   cat database-service.yml
   
   kubectl apply -f secrets.yaml
   kubectl apply -f database.yaml
   kubectl apply -f database-service.yml
   
   cat helloworld-app-deployment.yml
   kubectl  get svc
   
   kubectl get pods
   
   kubectl apply -f helloworld-app-deployment.yml
   kubectl apply -f helloworld-app-svc.yml
   cat helloworld-app-svc.yml
   kubectl get pods
   cat helloworld-app-deployment.yml
   cat helloworld-app-svc.yml
   kubectl get pods
   kubectl  get svc
   curl 172.31.0.101:32621
   kubectl  get pods
   kubectl exec -it database -- mysql -u root -p
   kubectl  get pods
   kubectl exec -it helloworld-deployment-7c557cd984-74jpl -- env

```
