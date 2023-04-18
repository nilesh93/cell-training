https://docs.rke2.io/install/quickstart
rke config --list-version --all

## Install container runtime in the VMs

sudo apt-get update -y
sudo apt-get install -y apt-transport-https ca-certificates curl software-properties-common
curl https://releases.rancher.com/install-docker/20.10.sh | sh
modprobe br_netfilter
sysctl net.bridge.bridge-nf-call-iptables=1
sudo systemctl enable docker

## confrim by running

systemctl status docker
