# [Certified Kubernetes Administrator (CKA) Course](https://www.udemy.com/course/certified-kubernetes-administrator-with-practice-tests/)
* [Udemy](https://www.udemy.com/course/certified-kubernetes-administrator-with-practice-tests/)
* [KodeKloud Practice Tests](https://kodekloud.com/courses/enrolled/675080)

## General
* [Certified Kubernetes Administrator](https://www.cncf.io/certification/cka/)
* [Curriculum](https://github.com/cncf/curriculum)
* [Candidate Handbook](https://docs.linuxfoundation.org/tc-docs/certification/lf-candidate-handbook)
* [Exam Tips](https://docs.linuxfoundation.org/tc-docs/certification/tips-cka-and-ckad)

## Repositories
* [Kubernetes the Hard Way on VirtualBox](https://github.com/mmumshad/kubernetes-the-hard-way)
    * Cloned to `~/src/kubernetes-the-hard-way`
* [Reference Notes for lectures and labs](https://github.com/kodekloudhub/certified-kubernetes-administrator-course)
    * Forked to this repository
* [Kubernetes the Hard Way on Azure](https://github.com/carlosonunez/kubernetes-the-hard-way-on-azure)

## Study Guides
* [Kubernetes Certified Administration](https://github.com/walidshaari/Kubernetes-Certified-Administrator)
* [Kubernetes Journey - CKA Exam Tips](https://itnext.io/kubernetes-journey-cka-ckad-exam-tips-ff73e4672833)... and [video](https://www.youtube.com/watch?app=desktop&v=RoSacSrr2oQ)
* [Best Practices for CKA Exam](https://medium.com/@emreodabas_20110/best-practices-for-cka-exam-9c1e51ea9b29)
* [Kubernetes Journey — CKA / CKAD Exam Tips](https://itnext.io/kubernetes-journey-cka-ckad-exam-tips-ff73e4672833)
* [David-VTUK/CKA-StudyGuide](https://github.com/David-VTUK/CKA-StudyGuide)
* [From ZERO Kubernetes knowledge to getting both CKA and CKAD](https://medium.com/@andreistefanciprian/from-zero-kubernetes-knowledge-to-getting-both-cka-and-ckad-certifications-c70ba503d6e0)
* [CKA Exam Study Resources](https://rudimartinsen.com/cka-resources/)

## Could be useful
* [A visual guide on troubleshooting Kubernetes deployments](https://learnk8s.io/troubleshooting-deployments)
* [CKA Simulator](https://killer.sh/cka)
* [KubeAcademy](https://kube.academy/courses)
* [Sonobuoy](https://github.com/vmware-tanzu/sonobuoy)
* [Kubernetes Dashboard](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/)
* [Native Kubernetes Continuous Delivery](https://kurtmadel.com/posts/native-kubernetes-continuous-delivery/native-k8s-cd/)

## Setup
```bash
source <(kubectl completion bash)
alias k=kubectl
complete -F __start_kubectl k
```
```bash
# az aks install-cli
# az account set -s 'CloudOps_Learning'
# add creds to kubeconfig
# az aks get-credentials --resource-group cloudops-k8s --name cloudops-k8s-automation
kubectl config get-contexts
kubectl config current-context
kubectl config set-context cloudops-k8s-automation --namespace=upandrunning
kubectl config set-context cloudops-k8s-automation
kubectl api-resources
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
## Sections
* NB: Presentations in PDF format also in `docs ` directories

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
- [10-Install](10Install.md)  
- [11-Troubleshooting](11Troubleshooting.md)  
- [12-Other-Topics](12OtherTopics.md)  
- [13-Lightning-Labs](13LightningLabs.md)  
- [14-Mock-Exams](14MockExams.md)  
