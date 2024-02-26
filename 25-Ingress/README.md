# Ingress Controller required the following clusterroles bindings to be applied.

Deploy all the 4 yaml files 

```
kubectl create -f 01-nginx-ingress-controller.yaml 


kubectl create -f 02-helloworld-v1.yml
kubectl create -f 03-app-svc-deployment.yaml 
kubectl create -f 04-ingress-rules.yaml 

kubectl get all -n nginx-ingress
kubectl get all 
kubectl get ingress
kubectl describe ingress helloworld-rules 

```
Now get the clusterIP of the ngix controller service from the namespace nginx-ingress and run the curl commands  

```
curl nginxserviceip:nginxserviceport
curl nginxserviceip:nginxserviceport/ -H 'Host: helloworld-v1.example.com'
curl nginxserviceip:nginxserviceport/info -H 'Host: helloworld-v1.example.com'


```
