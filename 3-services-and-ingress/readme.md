```
kubectl delete all --all
kubectl create deploy nginx --image nginx --port 80 -o yaml --dry-run=client > 3-services-and-ingress/deployment.yaml
kubectl expose deploy nginx --port 80 --target-port 8
0 --type ClusterIP --dry-run=client -o yaml > 3-services-and-ingress/service.yaml

kubectl get pods --show-labels

kubectl get svc
kubectl run -it busybox  --image busybox:1.27 --rm -- /bin/sh




```

## DNS

Accessible within any Namespace

```
<svc-name>.<namespace>.svc
```

if service and the caller of the service is in the samenamespace

```
<svc-name>
```
