https://docs.rke2.io/install/quickstart

## Install RKE

curl -s https://api.github.com/repos/rancher/rke/releases/latest | grep download_url | grep amd64 | cut -d '"' -f 4 | wget -qi -
chmod +x rke_linux-amd64
sudo mv rke_linux-amd64 /usr/local/bin/rke
rke --version

## Install Kubectl

curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin/kubectl
kubectl version --client

## Install Helm

curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh

## Install container runtime in the VMs

sudo apt-get update -y
sudo apt-get install -y apt-transport-https ca-certificates curl software-properties-common
curl https://releases.rancher.com/install-docker/20.10.sh | sh
modprobe br_netfilter
sysctl net.bridge.bridge-nf-call-iptables=1
sudo systemctl enable docker

systemctl status docker

## Create Cluster

rke config --list-version --all

rke up --config 1-create-cluster/cluster.yaml

## Check certs

cd /etc/kubernetes/ssl/

rke cert rotate --config 1-create-cluster/cluster.yaml
