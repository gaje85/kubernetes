~~~
	 kubectl create -f 10-Multi-Container-Pod/
     kubectl get svc,deploy,secrets,pod
     kubectl get pod
     kubectl describe pod wordpress-deployment-7d4896594c-kcqzf
     kubectl get pod
     kubectl describe pod wordpress-deployment-7d4896594c-kcqzf
     kubectl get svc
     kubectl get pod
     kubectl exec -it wordpress-deployment-7d4896594c-kcqzf -c mysql -- mysql -u root -p
~~~   
