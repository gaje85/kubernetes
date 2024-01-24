```
   cat springboot-rc.yaml
   
   kubectl apply -f springboot-rc.yaml
   
   kubectl get rc
   
   kubectl describe rc springbootrc-controller

```
Now try deleting some pods by getting the pod names . To get pod names pls run kubectl get pods.
Once the pods got deleted , replication controller will recreate the pods and maintain the replica count.
```
   
   kubectl delete pod <give 2 pod names > --force
   
   kubectl describe rc springbootrc-controller
   
   kubectl get rc
```
We can also increase and decrease the replica count from the CLI.
```
   
   kubectl scale --replicas=1 rc springbootrc-controller
   
   kubectl get rc 
   
   kubectl scale --replicas=5 rc springbootrc-controller
   
   
   kubectl delete -f springboot-rc.yaml --force
   kubectl delete --all --force

```
Open a separate window to watch the pods getting terminated and recreated .

```
 watch -n .5 kubectl get pods -o wide
```
