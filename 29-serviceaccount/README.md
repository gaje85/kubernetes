# Create a service account 

```
kubectl create namespace devops-tools

kubectl create serviceaccount api-service-account -n devops-tools

or 

cat <<EOF | kubectl apply -f -
apiVersion: v1
kind: ServiceAccount
metadata:
  name: api-service-account
  namespace: devops-tools
EOF

```

# create cluster role 

```
cat <<EOF | kubectl apply -f -
---
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
  name: api-cluster-role
  namespace: devops-tools
rules:
  - apiGroups:
        - ""
        - apps
        - autoscaling
        - batch
        - extensions
        - policy
        - rbac.authorization.k8s.io
    resources:
      - pods
      - componentstatuses
      - configmaps
      - daemonsets
      - deployments
      - events
      - endpoints
      - horizontalpodautoscalers
      - ingress
      - jobs
      - limitranges
      - namespaces
      - nodes
      - pods
      - persistentvolumes
      - persistentvolumeclaims
      - resourcequotas
      - replicasets
      - replicationcontrollers
      - serviceaccounts
      - services
    verbs: ["get", "list", "watch", "create", "update", "patch", "delete"]
EOF
```

# create Cluster role binding 

```
cat <<EOF | kubectl apply -f -
---
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
  name: api-cluster-role-binding
subjects:
- namespace: devops-tools 
  kind: ServiceAccount
  name: api-service-account 
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: api-cluster-role 
EOF

```

# Validate service account access via kubectl 

```
kubectl auth can-i get pods --as=system:serviceaccount:devops-tools:api-service-account

kubectl auth can-i delete deployments --as=system:serviceaccount:devops-tools:api-service-account

```
# validate service account call via api access

First, get the secret name associated with the api-service-account

```
kubectl get serviceaccount api-service-account  -o=jsonpath='{.secrets[0].name}' -n devops-tools

```

Use the secret name to get the base64 decoded token. It will be used as a bearer token in the API call.

```
kubectl get secrets  <service-account-token-name>  -o=jsonpath='{.data.token}' -n devops-tools | base64 

```

Get the cluster endpoint to validate the API access. 

```
kubectl get endpoints | grep kubernetes
```

# do api call with curl 

```
curl -k  https://35.226.193.217/api/v1/namespaces -H "Authorization: Bearer eyJhbGcisdfsdfsdfiJ9.eyJpc3MiOisdfsdfVhY2NvdW50Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3sdf3BhY2UiOiJkZWZhdWx0Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9zZWNyZXQubmFtZSI6ImFwaS1zZXJ2aWNlsdfglkjoer876Y3BmNWYiLsdfsdfRlbTpzZXJ2aWNlYWNjb3VudDpkZWZhdWx0OmFwaS1zZXJ2aWNlLWFjY291bnQifQ.u5jgk2px_lEs3f5e5lh_UfS40fndtDKMTY5UvsdfrtsuhtgjrUj-ezrRXeLS8SLOae4DuOGGGbInSg_gIo6oO7bLHhCixWOBJNOA5gzrLVioof_kHDR8gH5crrsWoR-GSSsdfgsdfg6fA_LDOqdxzqMC0WlXt6tgHfrwIHerPPvkI6NWLyCqX9tn_akpcihd-bL6GwOKlph17l_ND710FnTkE7kBfdXtQWWxaPPe06UEmoKK9t-0gsOCBxJxViwhHkvwqetr987q9enkadfgd_2cY_CA"

```





