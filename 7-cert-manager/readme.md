https://cert-manager.io/docs/installation/helm/

```
helm repo add jetstack https://charts.jetstack.io

helm repo update

helm install \
  cert-manager jetstack/cert-manager \
  --namespace cert-manager \
  --create-namespace \
  --version v1.11.0 \
  --set installCRDs=true


  kubectl get certificate
  kubectl describe certificate <name>

  kubectl get certificaterequests
  kubectl describe certificaterequests <name>
```
