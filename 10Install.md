# Installation steps
* Follow the pre-requisite instructions from [Install kubeadm](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/install-kubeadm/)
## 1. Create some VMs
```powershell
  vagrant up
  vagrant status
  # Current machine states:
  # kubemaster running (virtualbox)
  # kubenode01 running (virtualbox)
  # kubenode02 running (virtualbox)
```
## 2. `vagrant ssh` onto `kubemaster`, `kubenode01`, `kubenode02` and...
### a. Let iptables see bridged traffic
```bash
lsmod | grep br_netfilter
sudo modprobe br_netfilter

cat <<EOF | sudo tee /etc/modules-load.d/k8s.conf
br_netfilter
EOF

cat <<EOF | sudo tee /etc/sysctl.d/k8s.conf
net.bridge.bridge-nf-call-ip6tables = 1
net.bridge.bridge-nf-call-iptables = 1
EOF
sudo sysctl --system
```
### b. Install Docker container runtime
```bash
sudo apt-get remove docker docker-engine docker.io containerd runc
sudo apt-get update
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
sudo docker run hello-world
systemctl status docker
```
### c. Install kubeadm, kubelet and kubectl
```bash
sudo apt-get update
sudo apt-get install -y apt-transport-https ca-certificates curl

sudo curl -fsSLo /usr/share/keyrings/kubernetes-archive-keyring.gpg https://packages.cloud.google.com/apt/doc/apt-key.gpg
echo "deb [signed-by=/usr/share/keyrings/kubernetes-archive-keyring.gpg] https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list

sudo apt-get update
sudo apt-get install -y kubelet kubeadm kubectl
sudo apt-mark hold kubelet kubeadm kubectl
```
## 3. `vagrant ssh kubemaster` and...
### a. Create a cluster
```bash
sudo -i
kubeadm init --pod-network-cidr 10.244.0.0/16 --apiserver-advertise-address=192.168.56.2
# follow instructions from output of that command...
exit
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
# and take note of command to join a node to a cluster...
# kubeadm join 192.168.56.2:6443 --token r168fo.reoihkwydygpw98o \
#   --discovery-token-ca-cert-hash sha256:02bc65f22eb0902d933bb0aa50625b6e3fbcaebb4bca93a54a0951f55e3e0523
kubectl get nodes
```
### b. Install a Pod network plugin
```bash
# https://www.weave.works/docs/net/latest/kubernetes/kube-addon/
kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 | tr -d '\n')"
kubectl get pods --all-namespaces
```
## 4. `vagrant ssh kubenode1|2` and...
### Join the cluster
```bash
sudo -i
kubeadm join 192.168.56.2:6443 --token r168fo.reoihkwydygpw98o \
  --discovery-token-ca-cert-hash sha256:02bc65f22eb0902d933bb0aa50625b6e3fbcaebb4bca93a54a0951f55e3e0523
# NB: if token has expired...on the kubemaster run...
# kubeadm token create --print-join-command
```
## 5. `vagrant ssh kubemaster` and...
### Test the cluster
```bash
kubectl get nodes
kubectl run nginx --image-nginx
```

# Course Links
- [10-Install](docs/10-Install)  
  - [01-Section-Introduction](docs/10-Install/01-Section-Introduction.md)
  - [02-Designing-a-Kubernetes-Cluster](docs/10-Install/02-Designing-a-Kubernetes-Cluster.md)
  - [03-Choosing-Kubernetes-Infrastructure](docs/10-Install/03-Choosing-Kuberneter-Infrastructure.md)
    - `minikube`:
      - Deploys required VMs
      - Single node cluster
    - `kubeadm`:
      - Requires VMs to be ready
      - Single/multi node cluster
    - `kops`:
      - Deploy to AWS EC2
      - Single/multi node cluster
    - `OpenShift`:
      - RedHat fun
    - `Hosted solutions`:
      - AKS, GKE, EKS
  - [04-Choosing-Network-Solution](docs/10-Install/04-Choosing-Network-Solution.md)
  - [05-Configure-High-Availability](docs/10-Install/05-Configure-High-Availability.md)
    - `Controller Manager`: Active/Standby, first instance started up becomes the leader (active)
    - `Scheduler`: Active/Standby
    - `API Server`: Load balance
    - `etcd`: Can configure on its own servers
  - [06-ETCD-in-HA](docs/10-Install/06-ETCD-in-HA.md)
    - A `leader` node is elected and all `writes` go to this node and are distributed to other nodes
    - `RAFT` algorithm is used for leader election
    - A `write` is considered complete if it has been written to the majority of the nodes
    - Quorum = N/2 + 1, so need a minimum of 3 nodes
    - Always use an odd number of nodes >= 3
  - [07-Demo-Prequisites](docs/10-Install/07-Demo-Prequisites.md)
    - [YouTube](https://www.youtube.com/watch?v=uUupRagM7m0&list=PL2We04F3Y_41jYdadX55fdJplDvgNGENo)
    - [Kubernetes The Hard Way On VirtualBox](https://github.com/mmumshad/kubernetes-the-hard-way)
      - Cloned to `~/src/kubernetes-the-hard-way`
  - [08-Provisioning-VMS](docs/10-Install/08-Provisioning-VMS.md)
    - Install `Vagrant` and `VirtualBox`
  - [09-Install-Client-Tools](docs/10-Install/09-Install-Client-Tools.md)
  - [10-Secure-Cluster](docs/10-Install/10-Secure-Cluster.md)
  - [11-Create-KubeConfigfiles](docs/10-Install/11-Create-KubeConfigfiles.md)
  - [12-Data-Encryption](docs/10-Install/12-Data-Encryption.md)
  - [13-Kubernetes-Release-Binaries](docs/10-Install/13-Kubernetes-Release-Binaries.md)
  - [14-Install-Control-Plane-Components-Intro](docs/10-Install/14-Install-Control-Plane-Components-Intro.md)
  - [15-Install-ETCD-Cluster](docs/10-Install/15-Install-ETCD-Cluster.md)
  - [16-Install-Control-Plane-Components](docs/10-Install/16-Install-Control-Plane-Components.md)
  - [17-Install-Control-Plane-Load-Balancer](docs/10-Install/17-Install-Control-Plane-Load-Balancer.md)
  - [18-Install-Worker-node-componenets](docs/10-Install/18-Install-Worker-node-componenets.md)
  - [19-TLS-Bootstrap-worker-node](docs/10-Install/19-TLS-Bootstrap-worker-node.md)
  - [20-Demo-TLS-Bootstrap-worker-node](docs/10-Install/20-Demo-TLS-Bootstrap-worker-node.md)
  - [21-Configure-Kubectl-for-remote-access](docs/10-Install/22-Provision-Networking.md)
  - [23-Kubapi-to-kubelet-connectivity](docs/10-Install/23-Kubapi-to-kubelet-connectivity.md)
  - [24-Deploy-Core-DNS](docs/10-Install/24-Deploy-Core-DNS.md)
  - [25-End-to-End-tests](docs/10-Install/25-End-to-End-tests.md)
  - [26-End-To-End-Tests-Run-and-analyze](docs/10-Install/26-End-To-End-Tests-Run-and-analyze.md)
  - [27-Smoke-test](docs/10-Install/27-Smoke-test.md)
  - [28-End-to-End-test-part1](docs/10-Install/28-End-to-End-test-part1.md)
  - [29-Practise-Test-instal-using-kubeadm](docs/10-Install/29-Practise-Test-instal-using-kubeadm.md)
  - [30-Solution-Install-a-K8s-cluster-kubeadm](docs/10-Install/30-Solution-Install-a-K8s-cluster-kubeadm.md)
  - [31-Download-Presentation-Deck](docs/10-Install/21-Download-Presentation-Deck.md)
