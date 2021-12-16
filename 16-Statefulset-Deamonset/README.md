
StatefullSet

~~~

    kubectl create -f helloworld-statefulset.yaml
    kubectl get pods
    kubectl get statefulset
    kubectl scale --replicas=10 statefulset helloworld-statefull
    kubectl delete pod helloworld-statefull-0 helloworld-statefull-3 helloworld-statefull-7
    kubectl scale --replicas=2 statefulset helloworld-statefull
    kubectl scale --replicas=10 statefulset helloworld-statefull
    kubectl describe statefulset
    kubectl set image k8s-demo=gaje85/greeting statefulset helloworld-statefull --record
    kubectl set image statefulset helloworld-statefull k8s-demo=gaje85/greeting
    kubectl rollout status statefulset helloworld-statefull
   
    kubectl describe pod helloworld-statefull-9
~~~

~~~
    
    
     kubectl create -f helloworld-deamonset.yaml
     kubectl get pods
     kubectl get daemonset
    


~~~
