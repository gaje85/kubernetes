```
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh

ls
kubectl apply -f helm-rbac.yaml


helm version


helm repo add azure-marketplace https://marketplace.azurecr.io/helm/v1/repo

helm repo update


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
