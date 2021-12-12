```    
	kubectl get secrets 
      cat /root/username.txt 
      cat /root/password.txt 
      kubectl create secret generic mysecrets --from-file=/root/username.txt --from-file=/root/password.txt
      kubectl get secrets 
      kubectl describe secrets mysecrets
      kubectl edit secrets mysecrets
      ls
      mkdir 09-Secrets 
     cd 09-Secrets/
     ls
     vim helloworld-secrets-volumes.yaml
     ls
     kubectl create -f helloworld-secrets-volumes.yaml 
     kubectl get deploy 
     kubectl get pods 
     kubectl describe pods helloworld-deployment-f6c47d6c5-fgt6v
     ls
     kubectl get pods
     kubectl exec -it helloworld-deployment-f6c47d6c5-fgt6v -- bash
     ls
     vi /etc/hosts
     kubectl exec -it helloworld-deployment-f6c47d6c5-fgt6v -- bash
     kubectl exec -it helloworld-deployment-f6c47d6c5-fgt6v -- /bin/bash
     kubectl get pods 
     kubectl get pods -o wide 
     kubectl exec -it helloworld-deployment-f6c47d6c5-h9thr -- /bin/sh
     cat /etc/hosts
     ping worker01
     ping worker02
     ls
     kubectl exec -it helloworld-deployment-f6c47d6c5-h9thr -- /bin/sh
     ls
     kubectl delete -f helloworld-secrets-volumes.yaml 
     vim helloworld-secrets.yaml
     echo -n "paypal" | base64
     echo -n "paypal@432!" | base64
     vim helloworld-secrets.yaml 
     ls
     vim helloworld-secrets-volumes.yaml 
     ls
     cd ..
     ls
     kubectl create -f 09-Secrets/
     kubectl get pods 
     kubectl exec -it helloworld-deployment-64968b454c-gcdvq -- /bin/sh
     ls
     cd 09-Secrets/
     ls
 ```   
