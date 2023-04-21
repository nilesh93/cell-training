1. Create deployment for image nj93/k8s-demo-container:latest which runs on 8080
2. Create a NodePort Service and access this through one of the node IPs
3. Inject an Environment Variable called ENV_NAME and set the value to your name
4. Create a secret called config-json with the following value and mount it to the path /app/config/config.secret.json

```
{
    "APP_VERSION": "2.0.0"
}
```
