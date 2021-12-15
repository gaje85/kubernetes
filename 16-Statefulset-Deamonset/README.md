~~~

    cp -rf ../05-Deployments/helloworld.yaml .
    ls
    vim helloworld.yaml
    ls
    kubectl create -f helloworld.yaml --dry-run
    vim helloworld.yaml
    kubectl create -f helloworld.yaml --dry-run
    ls
    kubectl create -f helloworld.yaml
    kubectl get pods
    kubectl get statefulset
    kubectl scale --replicas=10 statefulset helloworld-statefull
    kubectl delete pod helloworld-statefull-0 helloworld-statefull-3 helloworld-statefull-7
    kubectl scale --replicas=2 statefulset helloworld-statefull
    kubectl scale --replicas=10 statefulset helloworld-statefull
    kubectl describe statefulset
    kubectl set image k8s-demo=amitvashist7/k8s-tiny-web:2 statefulset helloworld-statefull --record
    kubectl set image statefulset helloworld-statefull k8s-demo=amitvashist7/k8s-tiny-web:2
    kubectl rollout status statefulset helloworld-statefull
    kubectl describe pod helloworld-statefull-0
    kubectl describe pod helloworld-statefull-9
~~~

~~~
     cp -rf ../05-Deployments/helloworld.yaml .
     ls
     vim helloworld.yaml
     ls
     kubectl create -f helloworld.yaml --dry-run
     vim helloworld.yaml
     kubectl create -f helloworld.yaml --dry-run
     ls
     kubectl create -f helloworld.yaml
     kubectl get pods
     kubectl get statefulset
     kubectl scale --replicas=10 statefulset helloworld-statefull
     kubectl delete pod helloworld-statefull-0 helloworld-statefull-3 helloworld-statefull-7
     kubectl scale --replicas=2 statefulset helloworld-statefull
     kubectl scale --replicas=10 statefulset helloworld-statefull
     kubectl describe statefulset
     kubectl set image k8s-demo=amitvashist7/k8s-tiny-web:2 statefulset helloworld-statefull --record
     kubectl set image statefulset helloworld-statefull k8s-demo=amitvashist7/k8s-tiny-web:2
     kubectl rollout status statefulset helloworld-statefull
     kubectl describe pod helloworld-statefull-0
     kubectl describe pod helloworld-statefull-9


~~~
