# install kube prometheus stack 
 
We will be installing kube prometheus stack in the kubernetes cluster 

The github page for the kube prometheus stack is https://github.com/prometheus-community/helm-charts/tree/main/charts/kube-prometheus-stack


#### Install helm 

```
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh

```

#### Add helm repo and update

```
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update

```

#### Install kube prometheus stack 

```
helm install prom prometheus-community/kube-prometheus-stack 
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


