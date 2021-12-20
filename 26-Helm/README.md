```
wget https://get.helm.sh/helm-v3.4.2-linux-amd64.tar.gz

tar -zxvf helm-v3.4.2-linux-amd64.tar.gz

sudo mv linux-amd64/helm /usr/local/bin/helm

ls
kubectl apply -f helm-rbac.yaml


helm version


helm repo add azure-marketplace https://marketplace.azurecr.io/helm/v1/repo


helm search repo nginx


helm install mynginx azure-marketplace/nginx


kubectl get nginx


kubectl get pods

~~~



~~~

Create Custom chart

helm create testchart

helm install testpod testchart --dry-run

helm install testpod testchart





~~~
