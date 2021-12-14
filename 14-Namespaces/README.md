      kubectl get ns 
      kubectl create ns myspace
      kubectl get ns 
      kubectl delete ns myspace
      kubectl get ns 
      kubectl create ns myspace -o yaml --dry-run=client > namespace-defination.yaml
     
   cat namespace-defination.yaml 
  
   cp -rf ../05-Deployments/helloworld.yaml 
   cp -rf ../05-Deployments/helloworld.yaml .
   
   cat helloworld.yaml 
   cp -rf helloworld.yaml helloworld-with-myspace.yaml 
   
   rm -rf helloworld-with-myspace.yaml 
   
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
   
   kubectl get deploy --all-namespaces
   
   kubectl create -f helloworld.yaml -n myspace -o yaml --dry=run
   kubectl create -f helloworld.yaml -n myspace -o yaml --dry-run
   kubectl create -f helloworld.yaml -n myspace -o yaml --dry-run >  helloworld-with-ns.yaml
   
     kubectl create -f 14-Namespaces/
     kubectl get deploy --all-namespaces
     kubectl delete -f 14-Namespaces/
  