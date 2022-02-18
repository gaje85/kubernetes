# Network policies in kubernetes


```
kubectl create ns policy-demo

kubectl create deployment --namespace=policy-demo nginx --image=nginx

kubectl expose --namespace=policy-demo deployment nginx --port=80

kubectl run --namespace=policy-demo access --rm -ti --image busybox /bin/sh

inside the container run 

wget -q nginx -O -

We should get response 

exit the pod 

Now deny ingress to the namespace policy-demo

kubectl create -f - <<EOF
kind: NetworkPolicy
apiVersion: networking.k8s.io/v1
metadata:
  name: default-deny
  namespace: policy-demo
spec:
  podSelector:
    matchLabels: {}
EOF

Test Isolation 

kubectl run --namespace=policy-demo access --rm -ti --image busybox /bin/sh

wget -q --timeout=5 nginx -O -


```
### Allow access through network policy 

```
kubectl create -f - <<EOF
kind: NetworkPolicy
apiVersion: networking.k8s.io/v1
metadata:
  name: access-nginx
  namespace: policy-demo
spec:
  podSelector:
    matchLabels:
      app: nginx
  ingress:
    - from:
      - podSelector:
          matchLabels:
            run: access
EOF

kubectl run --namespace=policy-demo access --rm -ti --image busybox /bin/sh

wget -q --timeout=5 nginx -O -


Try with different label

kubectl run --namespace=policy-demo cant-access --rm -ti --image busybox /bin/sh


wget -q --timeout=5 nginx -O -


Do clean up

kubectl delete ns policy-demo





```







