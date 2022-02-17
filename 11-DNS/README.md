~~~   
   kubectl create -f busybox.yaml
    kubectl get pods 
    kubectl exec -it busybox -- /bin/sh 
    
	kubectl create -f custom-dns.yaml 
    kubectl get pods 
    kubectl exec -it custom-dns-example -- cat /etc/resolv.conf 
    kubectl exec -it busybox -- cat /etc/resolv.conf 
    
	
    kubectl create -f busybox-headless.yaml
    kubectl get pods 
    kubectl get svc
    kubectl exec -it busybox -- nslookup default-subdomain
    kubectl exec -it busybox -- nslookup wordpress-service
    kubectl exec -it busybox -- nslookup busybox-1.default-subdomain.default.svc.cluster.local
    kubectl exec -it busybox -- nslookup 192.168.5.6
   
~~~
