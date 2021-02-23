# [Certified Kubernetes Administrator (CKA) Course](https://www.udemy.com/course/certified-kubernetes-administrator-with-practice-tests/)
* [Udemy](https://www.udemy.com/course/certified-kubernetes-administrator-with-practice-tests/)
* [KodeKloud Practice Tests](https://kodekloud.com/courses/enrolled/675080)

## General
* [Certified Kubernetes Administrator](https://www.cncf.io/certification/cka/)
* [Curriculum](https://github.com/cncf/curriculum)
* [Candidate Handbook](https://docs.linuxfoundation.org/tc-docs/certification/lf-candidate-handbook)
* [Exam Tips](https://docs.linuxfoundation.org/tc-docs/certification/tips-cka-and-ckad)

## Repositories
* [Kubernetes The Hard Way On VirtualBox](https://github.com/mmumshad/kubernetes-the-hard-way)
    * Forked to `~/src/kubernetes-the-hard-way`
* [Reference Notes for lectures and labs](https://github.com/kodekloudhub/certified-kubernetes-administrator-course)
    * Forked to this repository

## Study Guides
* [Best Practices for CKA Exam](https://medium.com/@emreodabas_20110/best-practices-for-cka-exam-9c1e51ea9b29)
* [Kubernetes Journey — CKA / CKAD Exam Tips](https://itnext.io/kubernetes-journey-cka-ckad-exam-tips-ff73e4672833)
* [David-VTUK/CKA-StudyGuide](https://github.com/David-VTUK/CKA-StudyGuide)
* [From ZERO Kubernetes knowledge to getting both CKA and CKAD](https://medium.com/@andreistefanciprian/from-zero-kubernetes-knowledge-to-getting-both-cka-and-ckad-certifications-c70ba503d6e0)
* [CKA Exam Study Resources](https://rudimartinsen.com/cka-resources/)

## Could be useful
* [A visual guide on troubleshooting Kubernetes deployments](https://learnk8s.io/troubleshooting-deployments)
* [CKA Simulator](https://killer.sh/cka)

# Sections
* NB: Presentations in PDF format also in `docs ` directories
```bash
source <(kubectl completion bash)
alias k=kubectl
complete -F __start_kubectl k
```
```bash
# az account set -s 'CloudOps_Learning'
# add creds to kubeconfig
# az aks get-credentials --resource-group cloudops-k8s --name cloudops-k8s-automation
kubectl config get-contexts
kubectl config current-context
kubectl config set-context cloudops-k8s-automation --namespace=upandrunning
kubectl config set-context cloudops-k8s-automation
```

- [01-Introduction](docs/01-Introduction)
  - [01-Course-Introduction](docs/01-Introduction/01-Course-Introduction.md)
  - [02-Certification](docs/01-Introduction/02-Certification.md)
  
- [02-Core-Concepts](02CoreConcepts.md)
  
- [03-Scheduling](03Scheduling.md)
  
- [04-Logging-and-Monitoring](04LoggingAndMonitoring.md)
  
- [05-Application-Lifecycle-Management](05ApplicationLifecycleManagement.md)
  
- [06-Cluster-Maintenance](06ClusterMaintenance.md)
  
- [07-Security](07Security.md)

- [08-Storage](08Storage.MD)

- [09-Networking](docs/09-Networking) 
  - [01-Networking-Introduction](docs/09-Networking/01-Networking-Introduction.md)
  - [02-Pre-requisite-Switching-Routing-Gateways](docs/09-Networking/02-Pre-requisite-Switching-Routing-Gateways.md)
  - [03-Pre-requisite-DNS](docs/09-Networking/03-Pre-requisite-DNS.md)
  - [04-Pre-requisite-CoreDNS](docs/09-Networking/04-Pre-requisite-CoreDNS.md)
    - https://github.com/kubernetes/dns/blob/master/docs/specification.md
    - https://coredns.io/plugins/kubernetes/
  - [05-Pre-requisite-Network-Namespace](docs/09-Networking/05-Pre-requisite-Network-Namespace.md)
    - `ip netns exec mynamespace ip link`
    - While testing the Network Namespaces, if you come across issues where you can't ping one namespace from the other, make sure you set the NETMASK while setting IP Address. ie: 192.168.1.10/24
    - `ip -n red addr add 192.168.1.10/24 dev veth-red`
    - Another thing to check is FirewallD/IP Table rules. Either add rules to IP Tables to allow traffic from one namespace to another. Or disable IP Tables all together (Only in a learning environment).
  - [06-Pre-requisite-Docker-Networking](docs/09-Networking/06-Pre-requisite-Docker-Networking.mdd)
  - [07-Pre-requisite-CNI](docs/09-Networking/07-Pre-requisite-CNI.md)
    - `Plugins` define how different pieces of the container network are defined
    - Sample plugins... `bridge`, `vlan`, `ipvlan`, `macvlan`, `windows`
  - [08-Cluster-Networking](docs/09-Networking/08-Cluster-Networking.md)
    - [Installing kubeadm](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/install-kubeadm/) lists Kubernetes required ports
    - [Deploy Weave network addon](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/high-availability/#steps-for-the-first-control-plane-node)
  - [09-Practice-Test-Explore-Env](docs/09-Networking/09-Practice-Test-Explore-Env.md)
  - [10-Pod-Networking](docs/09-Networking/10-Pod-Networking.md)
     - This is the bit not done oob by Kubernetes
     - Goal is to ensure all pods can talk to each other
     - Lots of implementations such as `WeaveWorks`
  - [11-CNI-in-Kubernetes](docs/09-Networking/11-CNI-in-Kubernetes.md)
    - Configure CNI in `kubelet` startup
  - [12-CNI-weave](docs/09-Networking/12-CNI-weave.md)
  - [13-Practice-Test-CNI-weave](docs/09-Networking/13-Practice-Test-CNI-weave.md)
  - [14-Practice-Test-Deploy-Network-Solution](docs/09-Networking/14-Practice-Test-Deploy-Network-Solution.md)
  - [15-ipam-weave](docs/09-Networking/15-ipam-weave.md)
  - *** HERE (204 practice test) [16-Practice-Test-Networking-weave](docs/09-Networking/16-Practice-Test-Networking-weave.md)
  - [17-Service-Networking](17-Service-Networking.md)
  - [18-Practice-Test-Service-Networking](docs/09-Networking/18-Practice-Test-Service-Networking.md)
  - [19-DNS-in-kubernetes](docs/09-Networking/19-DNS-in-kubernetes.md)
  - [20-CoreDNS-in-Kubernetes](docs/09-Networking/20-CoreDNS-in-Kubernetes.md)
  - [21-Practice-Test-CoreDNS-in-Kubernetes](docs/09-Networking/21-Practice-Test-CoreDNS-in-Kubernetes.md)
  - [22-Ingress](docs/09-Networking/22-Ingress.md)
  - [23-Ingress-Annotations-and-rewrite-target](docs/09-Networking/23-Ingress-Annotations-and-rewrite-target.md)
  - [24-Practice-Test-CKA-Ingress-Net-1](docs/09-Networking/24-Practice-Test-CKA-Ingress-Net-1.md)
  - [25-Practice-Test-CKA-Ingress-Net-2](docs/09-Networking/25-Practice-Test-CKA-Ingress-Net-2.md)
  - [26-Dowload-Presentation-Deck](docs/09-Networking/26-Dowload-Presentation-Deck.md)

- [10-Install](docs/10-Install)  
  - [01-Section-Introduction](docs/10-Install/01-Section-Introduction.md)
  - [02-Designing-a-Kubernetes-Cluster](docs/10-Install/02-Designing-a-Kubernetes-Cluster.md)
  - [03-Choosing-Kuberneter-Infrastructure](docs/10-Install/03-Choosing-Kuberneter-Infrastructure.md)
  - [04-Choosing-Network-Solution](docs/10-Install/04-Choosing-Network-Solution.md)
  - [05-Configure-High-Availability](docs/10-Install/05-Configure-High-Availability.md)
  - [06-ETCD-in-HA](docs/10-Install/06-ETCD-in-HA.md)
  - [07-Demo-Prequisitesd](docs/10-Install/07-Demo-Prequisites.md)
  - [08-Provisioning-VMS](docs/10-Install/08-Provisioning-VMS.md)
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

- [11-Troubleshooting](docs/11-Troubleshooting)  
  - [01-Troubelshooting-Section-Introduction](docs/11-Troubleshooting/01-Troubelshooting-Section-Introduction.md)
  - [02-Application-Failure](docs/11-Troubleshooting/02-Application-Failure.md)
  - [03-Solution-Application-Failure](docs/11-Troubleshooting/03-Solution-Application-Failure.md)
  - [04-Control-Plane-Failure](docs/11-Troubleshooting/04-Control-Plane-Failure.md)
  - [05-Practice-Test-Control-Plane-Failure](docs/11-Troubleshooting/05-Practice-Test-Control-Plane-Failure.md)
  - [06-Solution-Control-Plane-Failure](docs/11-Troubleshooting/06-Solution-Control-Plane-Failure.md)
  - [07-Worker-Node-Failure](docs/11-Troubleshooting/07-Worker-Node-Failure.md)
  - [08-Practice-Test-Worker-Node-Failure](docs/11-Troubleshooting/08-Practice-Test-Worker-Node-Failure.md)
  - [09-Solution-Worker-Node-Failure](docs/11-Troubleshooting/09-Solution-Worker-Node-Failure.md)

- [12-Other-Topics](docs/12-Other-Topics)  
  - [01-Labs-JSON-PATH](docs/12-Other-Topics/01-Labs-JSON-PATH.md)
  - [02-Pre-Requisites-JSON-PATH](docs/12-Other-Topics/02-Pre-Requisites-JSON-PATH.md)
  - [03-Advance-Kubectl-Commands](docs/12-Other-Topics/03-Advance-Kubectl-Commands.md)
  - [04-Practice-Test-Advance-Kubectl-Commands](docs/12-Other-Topics/04-Practice-Test-Advance-Kubectl-Commands.md)

- [13-Lightning-Labs](docs/13-Lightning-Labs)  
  - [01-Lightning-Labs-Introduction](docs/13-Lightning-Labs/01-Lightning-Labs-Introduction.md)
  - [02-Lightning-Lab-1](docs/13-Lightning-Labs/02-Lightning-Lab-1.md)
  
- [14-Mock-Exams](docs/14-Mock-Exams)  
  - [01-Introduction](docs/14-Mock-Exams/01-Introduction.md)
  - [02-Mock-Exam-1](docs/14-Mock-Exams/02-Mock-Exam-1.md)
  - [03-Mock-Exam-2](docs/14-Mock-Exams/03-Mock-Exam-2.md)
  - [04-CKA-MockExam-2-Solution](docs/14-Mock-Exams/04-CKA-MockExam-2-Solution.md)
  - [05-Mock-Exam-3](docs/14-Mock-Exams/05-Mock-Exam-3.md)
  - [06-CKA-MockExam-3-Solution](docs/14-Mock-Exams/06-CKA-MockExam-3-Solution.md)
