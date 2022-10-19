~~~

# Add kubernetes-dashboard repository
helm repo add kubernetes-dashboard https://kubernetes.github.io/dashboard/
# Deploy a Helm Release named "kubernetes-dashboard" using the kubernetes-dashboard chart
helm install kubernetes-dashboard kubernetes-dashboard/kubernetes-dashboard

export POD_NAME=$(kubectl get pods -n default -l "app.kubernetes.io/name=kubernetes-dashboard,app.kubernetes.io/instance=kubernetes-dashboard" -o jsonpath="{.items[0].metadata.name}")


kubectl -n default port-forward --address=0.0.0.0 $POD_NAME 8443:8443


kubectl -n kube-system get secret

kubectl -n kube-system describe secret deployment-controller-token-<actualname>

Access Dashboard : https://<masternode public ip >:8443

copy paste the token from the previous command 
~~~
