# install kube prometheus stack 
 
We will be installing kube prometheus stack in the kubernetes cluster 

The github page for the kube prometheus stack is https://github.com/prometheus-community/helm-charts/tree/main/charts/kube-prometheus-stack


#### Install helm 

```
curl https://baltocdn.com/helm/signing.asc | sudo apt-key add -
sudo apt-get install apt-transport-https --yes
echo "deb https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list
sudo apt-get update
sudo apt-get install helm

```

#### Add helm repo and update

```
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update

```

#### Install kube prometheus stack 

```
helm install prom prometheus-community/kube-prometheus-stack --set prometheusOperator.admissionWebhooks.enabled=false --set prometheusOperator.admissionWebhooks.patch.enabled=false --set prometheusOperator.tlsProxy.enabled=false

```
#### port forward prometheus and grafana

```
kubectl get all

kubectl port-forward --address 0.0.0.0 svc/prom-kube-prometheus-stack-prometheus 9090

kubectl port-forward --address 0.0.0.0 svc/prom-grafana 80

ss -lt

```
#### Get password for Grafana

```
kubectl get secret prom-grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo

```

#### Uninstall kube prometheus stack
```
helm uninstall prom(this is helm release name)

```
Also run the following commands 

```
kubectl delete crd alertmanagerconfigs.monitoring.coreos.com
kubectl delete crd alertmanagers.monitoring.coreos.com
kubectl delete crd podmonitors.monitoring.coreos.com
kubectl delete crd probes.monitoring.coreos.com
kubectl delete crd prometheuses.monitoring.coreos.com
kubectl delete crd prometheusrules.monitoring.coreos.com
kubectl delete crd servicemonitors.monitoring.coreos.com
kubectl delete crd thanosrulers.monitoring.coreos.com

```


