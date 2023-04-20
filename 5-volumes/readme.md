kubectl create deploy echo-time --image busybox:1.27
--dry-run=client -o yaml > 5-volumes/deployment.yaml
