# Kubernets-Dashboard-UI
set up Kubernets-Dashboard-UI and port-forward to external, get access token in my HP Z600 workstation running Unbuntu server20.04 LTS.
## Use kubenets bootstrap tool start up a cluster
```
kind create cluster
```

## Deploy Dashboard with yaml file
```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.3.1/aio/deploy/recommended.yaml
```

## Port-forward Dashboard 
Z600 private IP is 10.0.0.26 in my private subnet.
kubernetes-dashboard service port in kubernetes is 443(https)
```
kubectl port-forward svc/kubernetes-dashboard -n kubernetes-dashboard 8000:443 --address 10.0.0.26
```
## Access to Dashboard in browser
```
https://10.0.0.26:8000/
```
## Get the access Token
```
kubectl -n kube-system describe $(kubectl -n kube-system get secret -n kube-system -o name | grep namespace) | grep token
```
