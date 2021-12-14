```
 836  cd 15-ResourceQuotas/
  837  ls
  838  vim resourcequota.yaml
  839  ls
  840  kubectl  apply -f resourcequota.yaml
  841  kubectl  get resourcequota
  842  kubectl  get resourcequota -n myspace
  843  kubectl  describe resourcequota -n myspace
  844  ls
  845  kubectl  describe resourcequota -n myspace
  846  kubectl api-resources
  847  kubectl  describe resourcequota -n myspace
  848  ls
  849  cat helloworld-with-no-quota.yaml
  850  kubectl  apply -f helloworld-with-no-quota.yaml
  851  kubectl get deploy
  852  kubectl get deploy -n myspace
  853  kubectl describe deploy  -n myspace
  854  kubectl get pods   -n myspace
  855  kubectl get rs    -n myspace
  856  kubectl describe rs helloworld-deployment-78cf6987f90/3   -n myspace
  857  kubectl describe rs helloworld-deployment-78cf6987f90   -n myspace
  858  kubectl describe rs helloworld-deployment-78cf6987f9   -n myspace
  859  ls
  860  kubectl  delete -f helloworld-with-no-quota.yaml
  861* kubectl  get pods -
  862  kubectl describe deploy  -n myspace
  863  ls
  864  cat helloworld-with-quota.yaml
  865  kubectl  apply -f helloworld-with-quota.yaml
  866  kubectl describe deploy  -n myspace
  867  kubectl get  deploy  -n myspace
  868  kubectl get  deploy,pods  -n myspace
  869  kubectl describe rs helloworld-deployment-6dc57c75b4  -n myspace
  870  kubectl  describe resourcequota -n myspace
  871  vim helloworld-with-quota.yaml
  872  ls
  873  kubectl config view
  874  kubectl config get-contexts
  875  kubectl config set-contexts --current --namespace=myspace
  876  kubectl config set-context --current --namespace=myspace
  877  kubectl config get-contexts
  878  kubectl  get pods -n myspace
  879  kubectl  get pods
  880  kubectl  get deploy,quota
  881  ls
  882  kubectl  get quota
  883  kubectl  get quota object-quota
  884  kubectl edit quota object-quota
  885  ls
  886  kubectl  get secrets
  887  kubectl describe quota object-quota
  888  kubectl create secret --help
  889  kubectl create secret generic
  890  kubectl create secret generic -h
  891  kubectl create secret generic test-secrets-1 --from-literal=user=test1
  892  kubectl create secret generic test-secrets-2 --from-literal=user=test2
  893  kubectl describe quota object-quota
  894  kubectl create secret generic test-secrets-3 --from-literal=user=test3
  895  kubectl  get secrets
  896  kubectl delete secrets  test-secrets-1 test-secrets-2
  897  kubectl  get secrets
  898  kubectl describe quota object-quota
  899  kubectl config get-contexts
  900  kubectl config set-context --current --name=default
  901  kubectl config set-context --current --namespace=default
  902  kubectl config get-contexts
  903  kubectl get pods
  904  kubectl get pods -n myspace
```
