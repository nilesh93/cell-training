https://docs.rke2.io/install/quickstart

# Setting up an RKE Cluster

## Step 1: Connect to VM and setup Master Node Pre requisites

SSH into VM1, let's consider that the master node and run the following commands

### Clone Git Repo

```
git clone https://github.com/nilesh93/cell-training.git
```

### COPY PEM file for ssh and check if SSH works from VM1 to VM2

```
chmod 600 cellcard.pem
```

```
ssh -i cellcard.pem ubunutu@<ip-address>
```

### Install RKE

```
curl -s https://api.github.com/repos/rancher/rke/releases/latest | grep download_url | grep amd64 | cut -d '"' -f 4 | wget -qi -
chmod +x rke_linux-amd64
sudo mv rke_linux-amd64 /usr/local/bin/rke
rke --version
```

### Install Kubectl

```
curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin/kubectl
kubectl version --client
```

### Install Helm

```
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh
```

### Install container runtime in the VMs

```
sudo apt-get update -y
sudo apt-get install -y apt-transport-https ca-certificates curl software-properties-common
curl https://releases.rancher.com/install-docker/20.10.sh | sh
modprobe br_netfilter
sysctl net.bridge.bridge-nf-call-iptables=1
sudo systemctl enable docker
sudo usermod -aG docker $USER

```

## Step 2: Connect to VM and setup Worker Node Pre requisites

SSH into VM2, let's consider that the worker node and run the following commands

### Install container runtime in the VMs

```
sudo apt-get update -y
sudo apt-get install -y apt-transport-https ca-certificates curl software-properties-common
curl https://releases.rancher.com/install-docker/20.10.sh | sh
modprobe br_netfilter
sysctl net.bridge.bridge-nf-call-iptables=1
sudo systemctl enable docker
sudo usermod -aG docker $USER

```

## Step 3: Create Cluster

Get the k8s versions available

```
rke config --list-version --all
```

clone repo if you havent already.

```
git clone https://github.com/nilesh93/cell-training.git
```

Update cluster.yaml with your VM IP details

```
vi cell-training/1-create-cluster/cluster.yaml
```

```
rke up --config cell-training/1-create-cluster/cluster.yaml
```

```
export KUBECONFIG= $(pwd)/kube_config_cluster.yaml
```

## Check certs

cd /etc/kubernetes/ssl/

rke cert rotate --config 1-create-cluster/cluster.yaml
