 ```
     kubectl apply -f helloworld.yaml 
     kubectl  get deploy,rs,pod
     kubectl get pods 
     kubectl  get svc 
     kubectl  get deploy 
     cat README.md 
     kubectl set image deployment springboot-deployment k8s-springboot=gaje85/hellodockerzulu
     kubectl  get deploy 
     kubectl  get deploy,rs,pod
     kubectl set image deployment springboot-deployment k8s-springboot=gaje85/greeting
     kubectl set image deployment springboot-deployment k8s-springboot=gaje85/greeting1
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
     kubectl set image deployment springboot-deployment k8s-springboot=gaje85/helloworld --record 
     kubectl rollout history deploy springboot-deployment
     kubectl set image deployment springboot-deployment k8s-springboot=gaje85/greeting --record 
     kubectl set image deployment springboot-deployment k8s-springboot=gaje85/hellodockerzulu --record 
     kubectl set image deployment springboot-deployment k8s-springboot=gaje85/springbootdockerdemo --record 
     kubectl rollout history deploy springboot-deployment
     kubectl edit deploy springboot-deployment
       kubectl get deploy springboot-deployment -o yaml > one.yaml    
```

```
    kubectl run hello-k8s --image=nginx --port=80 --dry-run
    kubectl run hello-k8s --image=nginx --port=80 --dry-run -o yaml
    kubectl run hello-k8s --image=nginx --port=80 --dry-run -o yaml  > abc.yaml
    ls
    kubectl apply -f abc.yaml
```

```
     ls
     kubectl get deployment 
     kubectl get deploy helloworld-deployment
     kubectl describe deploy helloworld-deployment
     kubectl get deploy 
     vim helloworld.yaml 
     kubectl apply -f helloworld.yaml 
     kubectl scale --replicas=7 deploy helloworld-deployment
     kubectl  edit deploy helloworld-deployment
     kubectl  get deploy 
     kubectl set image deployment helloworld-deployment k8s-demo=amitvashist7/k8s-tiny-web:2 --record 
     kubectl delete -f helloworld.yaml 
     ls
     vim helloworld-v2.yaml 
     kubectl  apply -f helloworld-v2.yaml 
     kubectl set image deployment helloworld-deployment k8s-demo=amitvashist7/k8s-tiny-web:2 --record 
     kubectl  get deploy 
     kubectl set image deployment helloworld-2-deployment k8s-demo=amitvashist7/k8s-tiny-web:2 --record 
     cat helloworld-v2.yaml 
     kubectl  get deploy 
     kubectl  describe deploy helloworld-2-deployment 
     kubectl  delete -f helloworld-v2.yaml 
     vim helloworld-v3.yaml 
     kubectl apply -f helloworld-v3.yaml 
     kubectl set image deployment helloworld-3-deployment k8s-demo=amitvashist7/k8s-tiny-web:2 --record 
     kubectl delete -f helloworld-v3.yaml 
```
