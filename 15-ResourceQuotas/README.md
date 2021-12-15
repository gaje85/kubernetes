```
  kubectl  apply -f resourcequota.yaml
  kubectl  get resourcequota
  kubectl  get resourcequota -n myspace
  kubectl  describe resourcequota -n myspace
 
  kubectl  describe resourcequota -n myspace
  kubectl api-resources
  kubectl  describe resourcequota -n myspace
 
  kubectl  apply -f helloworld-with-no-quota.yaml
  kubectl get deploy
  kubectl get deploy -n myspace
  kubectl describe deploy  -n myspace
  kubectl get pods   -n myspace
  kubectl get rs    -n myspace
  kubectl describe rs helloworld-deployment-78cf6987f90/3   -n myspace
  kubectl describe rs helloworld-deployment-78cf6987f90   -n myspace
  kubectl describe rs helloworld-deployment-78cf6987f9   -n myspace
 
  kubectl  delete -f helloworld-with-no-quota.yaml
  kubectl  get pods -
  kubectl describe deploy  -n myspace
 
  kubectl  apply -f helloworld-with-quota.yaml
  kubectl describe deploy  -n myspace
  kubectl get  deploy  -n myspace
  kubectl get  deploy,pods  -n myspace
  kubectl describe rs helloworld-deployment-6dc57c75b4  -n myspace
  kubectl  describe resourcequota -n myspace
 
  kubectl config view
    kubectl config get-contexts
    kubectl config set-contexts --current --namespace=myspace
    kubectl config set-context --current --namespace=myspace
    kubectl config get-contexts
    kubectl  get pods -n myspace
    kubectl  get pods
    kubectl  get deploy,quota
  
     kubectl  get quota
    kubectl  get quota object-quota
    kubectl edit quota object-quota
   
   kubectl  get secrets
    kubectl describe quota object-quota
    kubectl create secret --help
    kubectl create secret generic
    kubectl create secret generic -h
    kubectl create secret generic test-secrets-1 --from-literal=user=test1
    kubectl create secret generic test-secrets-2 --from-literal=user=test2
    kubectl describe quota object-quota
    kubectl create secret generic test-secrets-3 --from-literal=user=test3
    kubectl  get secrets
    kubectl delete secrets  test-secrets-1 test-secrets-2
    kubectl  get secrets
    kubectl describe quota object-quota
    kubectl config get-contexts
    kubectl config set-context --current --name=default
    kubectl config set-context --current --namespace=default
    kubectl config get-contexts
    kubectl get pods
    kubectl get pods -n myspace
```
