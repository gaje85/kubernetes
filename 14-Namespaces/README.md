~~~
      kubectl get ns 
      kubectl create ns myspace
      kubectl get ns 
      kubectl delete ns myspace
      kubectl get ns 
      kubectl create ns myspace -o yaml --dry-run=client > namespace-defination.yaml
     
   cat namespace-defination.yaml 
  
   kubectl create -f helloworld.yaml 
   kubectl get pods 
   kubectl get ns 
   kubectl create -f namespace-defination.yaml 
   kubectl create -f helloworld.yaml -n myspace
   kubectl get deployment 
   kubectl get deployment -n myspace
   kubectl describe deployment helloworld-deployment -n myspace
   kubectl describe deployment helloworld-deployment 
   kubectl delete deployment helloworld-deployment -n myspace
   kubectl delete deployment helloworld-deployment 
   
   
  

   kubectl create -f helloworld.yaml -n myspace -o yaml --dry-run=client
   kubectl create -f helloworld.yaml -n myspace -o yaml --dry-run=client >  helloworld-with-ns.yaml
   
     kubectl create -f helloworld-with-ns.yaml
     kubectl get deploy --all-namespaces
     kubectl delete -f 14-Namespaces/
~~~