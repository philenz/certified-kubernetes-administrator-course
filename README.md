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
* [KubeAcademy](https://kube.academy/courses)

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
```bash
# connect to microk8s cluster...
philenz@NZL170:~$ ssh ztlnx
Welcome to Ubuntu 20.10 (GNU/Linux 5.8.0-44-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

0 updates can be installed immediately.
0 of these updates are security updates.

Last login: Tue Mar  9 18:13:16 2021 from 172.22.117.101
philenz@phil-Inspiron:~$ microk8s.status
```
```powershell
# use minikube...
PS C:\Users\Phil.Evans> minikube status
host: Running
kubelet: Running
apiserver: Running
kubeconfig: Configured
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
- [08-Storage](08Storage.md)
- [09-Networking](09Networking.md) 

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
