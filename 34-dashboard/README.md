```

kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.4.0/aio/deploy/recommended.yaml

kubectl  apply -f serviceaccount.yaml

kubectl get svc -n kubernetes-dashboard

````

Setup a port-forward for the clusterIP service of the kubernetes-dashboard 


```
kubectl port-forward --address 0.0.0.0 service/kubernetes-dashboard 8443:443 -n kubernetes-dashboard &
Access Dashboard : https://<masternode public ip >:8443

```

Generate token to login to dashbpard .

```
kubectl -n kubernetes-dashboard create token dashboard-admin

```
copy paste the token from the previous command in the dashboard webapp 

