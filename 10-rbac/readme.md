kubectl get csr

kubect get csr nilesh -o yaml

kubectl create clusterrole pod-reader --verb=get --resource=pods --resource-name=readablepod --dry-run=client -o yaml > 10-rbac/clusterrole.yaml

kubectl -n <ns> create rolebinding <bindingname> \
--serviceaccount <namesapce>:<sa-name> \
--clusterrole <clusterrole-name> \
-o yaml --dry-run=client

kubectl -n <ns> create clusterrolebinding <bindingname> \
--user <namesapce>:<sa-name> \
--clusterrole <clusterrole-name> \
-o yaml --dry-run=client

kubectl create sa nilesh-sa

kubectl get secrets | grep nilesh

## Activity

Create a service account with your name

attach clusterrole pod-reader to your service account

kubectl auth can-i get pods --as nilesh-sa:default
