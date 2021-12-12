```    
	kubectl get secrets 
      cat /root/username.txt 
      cat /root/password.txt 
      kubectl create secret generic mysecrets --from-file=/root/username.txt --from-file=/root/password.txt
      kubectl get secrets 
      kubectl describe secrets mysecrets
      kubectl edit secrets mysecrets
      
     kubectl create -f helloworld-secrets-volumes.yaml 
     kubectl get deploy 
     kubectl get pods 
     kubectl describe pods springboot-deployment-f6c47d6c5-fgt6v
     
    
     kubectl delete -f helloworld-secrets-volumes.yaml 
    
     echo -n "paypal" | base64
     echo -n "paypal@432!" | base64
    
     kubectl create -f 09-Secrets/
     kubectl get pods 
     kubectl exec -it springboot-deployment-64968b454c-gcdvq -- /bin/sh
     
 
 ```   
