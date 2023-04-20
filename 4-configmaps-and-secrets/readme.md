kubectl create cm cellcard-config --from-literal name=cellcard -o yaml --dry-run=client > 4-configmaps-and-secrets/configmap.yaml
kubectl create cm html-file --from-file ./4-configmaps-and-secrets/index.html -o yaml --dry-run=client > 4-configmaps-and-secrets/html-confimap.yaml

https://github.com/bitnami-labs/sealed-secrets

https://www.vaultproject.io/
