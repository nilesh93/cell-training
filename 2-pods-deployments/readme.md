## Namespaces

```
kubectl get ns
kubectl create ns nilesh
kubectl apply -f 2-pods-deployments/deployment.yaml -n nilesh
```

## Pods

```
kubectl get nodes
kubectl get pods
kubectl explain pod.spec.containers
kubectl explain pod.spec.containers.ports

kubectl apply -f 2-pods-deployments/pod.yaml
kubectl get pods
kubectl get pods -o wide

kubectl top pods
kubectl describe pod <pod-name>
kubectl delete pod <pod-name>

kubectl port-forward po/nginx 3000:80
kubectl logs -f nginx

kubectl exec -it nginx -- /bin/sh

```

## Deployments

```
kubectl explain pod.spec.containers.ports
kubectl explain deploy.spec.template.spec.containers.ports

deploy.spec.template.spec == pod.spec

kubectl create deploy nginx-deploy --image nginx --port 80 -o yaml --dry-run=client > 2-pods-deployments/deployment.yaml

kubectl apply -f 2-pods-deployments/deployment.yaml

```

## Activity

1. Create a Namespace under your name
2. Create a deplyment nginx yaml using kubectl create command
3. Update the yaml to 3 replicas
4. apply the yaml to the cluster
5. Port forward one pod to your machine on port 3000
