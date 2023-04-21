1. Create deployment for image nj93/k8s-demo-container:latest which runs on 8080
2. Create a NodePort Service and access this through one of the node IPs
3. Inject an Environment Variable called ENV_NAME and set the value to your name
4. Create a secret called config-json with the following value and mount it to the path /app/config/config.secret.json

```
{
    "API_KEY": "New Secret"
}
```

## Answer

```
kubectl create deploy microservice --image nj93/k8s-demo-container:latest  --port 8080 -o yaml --dry-run > 6-Activity/deployment.yaml

kubectl get pods

kubectl port-forward microservice-7784bdbd7d-kggsd  3000:8080

kubectl expose deploy microservice --port 80 --target-port 8080 --type=NodePort -o yaml --dry-run=client > 6-Activity/service.yaml

kubectl get svc

kubectl get nodes -o wide

kubectl create cm name-config --from-literal ENV_NAME=nilesh123 -o yaml --dry-run=client > 6-Activity/name-config.yaml

kubectl create secret generic api-key-secret --from-file ./6-Activity/config.secret.json -o yaml --dry-run=client > 6-Activity/api-key-secret.yaml

```

## Ingress

```
kubectl get ingressclass


```
