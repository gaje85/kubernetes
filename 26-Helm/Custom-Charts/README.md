```
 1765  mkdir Custom-Charts
 1766  ls
 1767  cd Custom-Charts/
 1768  ls
 1769  helm create mychart
 1770  ls
 1771  cd mychart/
 1772  ls
 1773  ls -R .
 1774  ls
 1775  cat templates/service.yaml
 1776  ls
 1777  vim values.yaml
 1778  ls
 1779  helm list
 1780  helm delete mynginx
 1781  helm list
 1782  kubectl get pods,svc,deploy
 1783  kubectl delete  service/nginx-ingress-controller
 1784  kubectl get pods,svc,deploy
 1785  ls
 1786  cd ..
 1787  ls
 1788  helm install my-nginx mychart --dry-run
 1789  helm install my-nginx mychart
 1790  helm list
 1791  kubectl get pods,svc,deploy
 1792  ls
 1793  kubectl get pods,svc,deploy
 1794  ls
 1795  helm create my-python-webapp
 1796  ls
 1797  cd my-python-webapp/
 1798  ls
 1799  vim values.yaml
 1800  ls
 1801  cd ..
 1802  ls
 1803  history
 1804  helm install mypy-webapp my-python-webapp --dry-run
 1805  helm install mypy-webapp my-python-webapp
 1806  kubectl get pods,svc,deploy
 1807  ls
 1808  cd my-python-webapp/
 1809  ls
 1810  vim values.yaml
 1811  ls
 1812  cd ..
 1813  helm list
 1814  helm  delete mypy-webapp
 1815  ls
 1816  cd my-python-webapp/
 1817  ls
 1818  vi values.yaml
 1819  ls
 1820  vim templates/deployment.yaml
 1821  ls
 1822  cd ..
 1823  ls
 1824  helm install mypy-webapp my-python-webapp
 1825  kubectl get pods
 1826  kubectl get svc

```
