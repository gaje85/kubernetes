```
   cat springboot-rc.yaml
   
   kubectl apply -f springboot-rc.yaml
   
   kubectl get rc
   
   kubectl describe rc springbootrc-controller
   
   kubectl delete pod <give 2 pod names >
   
   kubectl describe rc springbootrc-controller
   
   kubectl get rc
   
   kubectl scale replicas=1 rc springbootrc-controller
   
   kubectl scale --replicas=1 rc springbootrc-controller
   
   kubectl get rc 
   
   kubectl delete pod <give pod name>
   
   kubectl scale --replicas=5 rc springbootrc-controller
   
   kubectl apply -f springboot-rc.yaml
   
   kubectl delete -f springboot-rc.yaml

```


```
 watch -n .5 kubectl get pods -o wide
```
