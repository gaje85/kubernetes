# Kubernetes User Accounts - Demo

## Create a new normal user

```   
apt install openssl -y 
openssl genrsa -out test.pem 2048
cat test.pem 
openssl  req -new -key test.pem -out test-csr.pem -subj "/CN=test/O=training"
   
cat test-csr.pem 
openssl x509 -req -in test-csr.pem -CA /etc/kubernetes/pki/ca.crt -CAkey /etc/kubernetes/pki/ca.key -CAcreateserial -out test.crt -days 10000

openssl x509 -in test.crt -text -noout
```

## Set the credentials in kube config
```
kubectl config view
kubectl config set-credentials test --client-certificate=/root/test.crt --client-key=/root/test.pem 
kubectl config view

kubectl config get-contexts
kubectl config set-context test@kubernetes --cluster=kubernetes --user=test
```

## Check the Credentials
```
kubectl config view
kubectl config get-contexts
```

## Create a new context in kube config
```
kubectl config use-context test@kubernetes
kubectl config get-contexts
```

## New let's try to run couple of commands ( if you are getting Forebiden error don't worry its because of missing RBAC roles of the newly created user )  
```
kubectl get pods 
```


## Switch back to the old context for regular opperations.
```
kubectl config use-context kubernetes-admin@kubernetes
kubectl get pods 
~~~
