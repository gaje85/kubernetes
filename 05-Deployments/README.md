 ```
     kubectl apply -f helloworld.yaml 
     kubectl  get deploy,rs,pod
     kubectl get pods 
     kubectl  get svc 
     kubectl  get deploy 
     cat README.md 
     kubectl set image deployment springboot-deployment springboot=gaje85/hellodockerzulu
     kubectl  get deploy 
     kubectl  get deploy,rs,pod
     kubectl set image deployment springboot-deployment springboot=gaje85/greeting
     kubectl set image deployment springboot-deployment springboot=gaje85/ckaboothelloapi
     cat helloworld.yaml 
     cat README.md 
     kubectl rollout history deploy springboot-deployment
     kubectl rollout history deploy springboot-deployment --revision=1
     kubectl rollout history deploy springboot-deployment --revision=2
     kubectl rollout history deploy springboot-deployment
     kubectl rollout undo deploy springboot-deployment
     kubectl rollout history deploy springboot-deployment
     kubectl rollout undo deploy springboot-deployment
     kubectl rollout history deploy springboot-deployment
     kubectl rollout undo deploy springboot-deployment --to-revision=2
     kubectl rollout history deploy springboot-deployment
     kubectl rollout undo deploy springboot-deployment --to-revision=1
     kubectl rollout history deploy springboot-deployment
     kubectl set image deployment springboot-deployment springboot=gaje85/helloworld --record 
     kubectl rollout history deploy springboot-deployment
     kubectl set image deployment springboot-deployment springboot=gaje85/greeting --record 
     kubectl set image deployment springboot-deployment springboot=gaje85/hellodockerzulu --record 
     kubectl set image deployment springboot-deployment springboot=gaje85/springbootdockerdemo --record 
     kubectl rollout history deploy springboot-deployment
     kubectl edit deploy springboot-deployment
       kubectl get deploy springboot-deployment -o yaml > one.yaml    
```

```
    kubectl run hello-k8s --image=nginx --port=80 --dry-run=client
    kubectl run hello-k8s --image=nginx --port=80 --dry-run=client -o yaml
    kubectl run hello-k8s --image=nginx --port=80 --dry-run=client -o yaml  > two.yaml
    
    kubectl apply -f two.yaml
```

```
     
     kubectl get deployment 
     kubectl get deploy springboot-deployment
     kubectl describe deploy springboot-deployment
     kubectl get deploy 
     kubectl scale --replicas=7 deploy springboot-deployment
     kubectl  edit deploy springboot-deployment
     kubectl  get deploy 
     kubectl set image deployment springboot-deployment springboot=gaje85/hellodockerzulu --record 
     kubectl delete -f helloworld.yaml 
     
     kubectl  apply -f helloworld-v2.yaml 
     kubectl set image deployment springboot-2-deployment k8s-demo=gaje85/hellodocker --record 
     cat helloworld-v2.yaml 
     kubectl  get deploy 
     kubectl  describe deploy springboot-2-deployment 
     kubectl  delete -f helloworld-v2.yaml 
     
     kubectl apply -f helloworld-v3.yaml 
     kubectl set image deployment springboot-3-deployment k8s-demo=gaje85/ckaboothelloapi --record 
     kubectl delete -f helloworld-v3.yaml 
```
