# kubernetes

### Install

```shell
swapoff -a

sudo apt-get install openssh-server apt-transport-https curl -y

sudo apt-get install docker.io -y

sudo systemctl start docker
sudo systemctl enable docker

sudo apt-get update
sudo apt-get install -y apt-transport-https ca-certificates curl

# download the oogle cloud public signing key
sudo curl -fsSLo /usr/share/keyrings/kubernetes-archive-keyring.gpg https://packages.cloud.google.com/apt/doc/apt-key.gpg

# Add the Kubernetes ap repository
echo "deb [signed-by=/usr/share/keyrings/kubernetes-archive-keyring.gpg] https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list

sudo apt-get update
sudo apt-get install -y kubectl

sudo apt-get install kubeadm=1.18.6-00 kubelet=1.18.6-00 kubectl=1.18.6-00

sudo kubeadm init --pod-network-cidr=10.244.0.0/16 --apiserver-advertise-address=10.0.2.5

mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config

kubectl apply -f 'https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml'
```
