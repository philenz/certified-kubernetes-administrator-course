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
* https://github.com/David-VTUK/CKA-StudyGuide
* https://github.com/burkeazbill/cka-studyguide
* https://medium.com/@andreistefanciprian/from-zero-kubernetes-knowledge-to-getting-both-cka-and-ckad-certifications-c70ba503d6e0

# Sections

- [01-Introduction](docs/01-Introduction)
  - [01-Course-Introduction](docs/01-Introduction/01-Course-Introduction.md)
  - [02-Certification](docs/01-Introduction/02-Certification.md)
  
- [02-Core-Concepts](docs/02-Core-Concepts)

  - [01-Core-Concepts-Section-Introduction](docs/02-Core-Concepts/01-Core-Concepts-Section-Introduction.md)
  - [02-Cluster-Architecture](docs/02-Core-Concepts/02-Cluster-Architecture.md)
      - Master node / control plane
          - etcd cluster
          - kube-apiserver
          - kube controller manager (e.g.: node controller)
          - kube-scheduler
      - Worker nodes
          - kubelet
          - kube-proxy
          - container runtime engine (e.g.: docker, container-d)
  - [03-ETCD-For-Beginners](docs/02-Core-Concepts/03-ETCD-For-Beginners.md)
      - Runs on port 2379
  - [04-ETCD-in-Kubernetes](docs/02-Core-Concepts/04-ETCD-in-Kubernetes.md)
  - [05-Kube-API-Server](docs/02-Core-Concepts/05-Kube-API-Server.md)
  - [06-Kube-Controller-Manager](docs/02-Core-Concepts/06-Kube-Controller-Manager.md)
  - [07-Kube-Scheduler](docs/02-Core-Concepts/07-Kube-Scheduler.md)
  - [08-Kubelet](docs/02-Core-Concepts/08-Kubelet.md)
  - [09-Kube-Proxy](docs/02-Core-Concepts/09-Kube-Proxy.md)
  - [10-Pods](docs/02-Core-Concepts/10-Pods.md)
  ```yml
  apiVersion: v1
  kind: Pod
  metadata:
    name: fred
    labels:
      app: fender
  spec:
    containers:
      - name: nginx-container
        image: nginx
  ```
  - [11-Practice-Test-Introduction](docs/02-Core-Concepts/11-Practice-Test-Introduction.md)
  - [12-Practice-Test-PODs](docs/02-Core-Concepts/12-Practice-Test-PODs.md)
  - [13-ReplicaSets](docs/02-Core-Concepts/13-ReplicaSets.md)
  - [14-Practice-Tests-ReplicaSet](docs/02-Core-Concepts/14-Practice-Tests-ReplicaSet.md)
  - [15-Deployments](docs/02-Core-Concepts/15-Deployments.md)
  - [16-Practice-Tests-Deployments](docs/02-Core-Concepts/16-Practice-Tests-Deployments.md)
  - [17-Namespaces](docs/02-Core-Concepts/17-Namespaces.md)
  - [18-Practice-Test-Namespaces](docs/02-Core-Concepts/18-Practice-Test-Namespaces.md)
  - [19-Services](docs/02-Core-Concepts/19-Services.md)
  - [20-Services-ClusterIP](docs/02-Core-Concepts/20-Services-ClusterIP.md)
  - [21-Practice-Test-Services](docs/02-Core-Concepts/21-Practice-Test-Services.md)
  - [22-Imperative-Commands-with-kubectl](docs/02-Core-Concepts/22-Imperative-Commands-with-kubectl.md)
  - [23-Practice-Test-Imperative-Commands](docs/02-Core-Concepts/23-Practice-Test-Imperative-Commands.md)
  - [24-Attachments](docs/02-Core-Concepts/24-Attachments.md)
  
- [03-Scheduling](docs/03-Scheduling)

  - [01-Scheduling-Section-Introduction](docs/03-Scheduling/01-Scheduling-Section-Introduction.md)
  - [02-Manual-Scheduling](docs/03-Scheduling/02-Manual-Scheduling.md)
  - [03-Practice-Test-Manual-Scheduling](docs/03-Scheduling/03-Practice-Test-Manual-Scheduling.md)
  - [04-Labels-and-Selectors](docs/03-Scheduling/04-Labels-and-Selectors.md)
  - [05-Practice-Test-Scheduling](docs/03-Scheduling/05-Practice-Test-Scheduling.md)
  - [06-Taints-and-Tolerations](docs/03-Scheduling/06-Taints-and-Tolerations.md)
  - [07-Practice-Test-Taints-and-Tolerations](docs/03-Scheduling/07-Practice-Test-Taints-and-Tolerations.md)
  - [08-Node-Selectors](docs/03-Scheduling/08-Node-Selectors.md)
  - [09-Node-Affinity](docs/03-Scheduling/09-Node-Affinity.md)
  - [10-Practice-Test-Node-Affinity](docs/03-Scheduling/10-Practice-Test-Node-Affinity.md)
  - [11.Taints-and-Tolerations-vs-Node-Affinity](docs/03-Scheduling/11.Taints-and-Tolerations-vs-Node-Affinity.md)
  - [12-Resource-Limits](docs/03-Scheduling/12-Resource-Limits.md)
  - [13-Practice-Test-Resource-Limits](docs/03-Scheduling/13-Practice-Test-Resource-Limits.md)
  - [14-DaemonSets](docs/03-Scheduling/14-DaemonSets.md)
  - [15-Practice-Test-DaemonSets](docs/03-Scheduling/15-Practice-Test-DaemonSets.md)
  - [16-Static-Pods](docs/03-Scheduling/16-Static-Pods.md)
  - [17-Practice-Test-StaticPods](docs/03-Scheduling/17-Practice-Test-StaticPods.md)
  - [18-Multiple-Schedulers](docs/03-Scheduling/18-Multiple-Schedulers.md)
  - [19-Practice-Test-Multiple-Schedulers](docs/03-Scheduling/19-Practice-Test-Multiple-Schedulers.md)
  - [20-Configuring-Kubernetes-Schedulers](docs/03-Scheduling/20-Configuring-Kubernetes-Schedulers.md)
  - [21-Download-Presentation-Deck](docs/03-Scheduling/21-Download-Presentation-Deck.md)

- [04-Logging-and-Monitoring](docs/04-Logging-and-Monitoring)

  - [01-Logging-and-Monitoring-Section-Introduction](docs/04-Logging-and-Monitoring/01-Logging-and-Monitoring-Section-Introduction.md)
  - [02-Monitor-Cluster-Components](docs/04-Logging-and-Monitoring/02-Monitor-Cluster-Components.md)
  - [03-Practice-Test-Monitor-Cluster-Components](docs/04-Logging-and-Monitoring/03-Practice-Test-Monitor-Cluster-Components.md)
  - [04-Managing-Application-Logs](docs/04-Logging-and-Monitoring/04-Managing-Application-Logs.md)
  - [05-Download-Presentation-Deck](docs/04-Logging-and-Monitoring/05-Download-Presentation-Deck.md)
  - [06-Practice-Test-Managing-Application-Logs](docs/04-Logging-and-Monitoring/06-Practice-Test-Managing-Application-Logs.md)
  
- [05-Application-Lifecycle-Management](docs/05-Application-Lifecycle-Management)

  - [01-Application-Lifecycle-Management--Section-Introduction](docs/05-Application-Lifecycle-Management/01-Application-Lifecycle-Management--Section-Introduction.md)
  - [02-RollingUpdates-and-Rollback](docs/05-Application-Lifecycle-Management/02-RollingUpdates-and-Rollback.md)
  - [03-Practice-Test-RollingUpdates-Rollback](docs/05-Application-Lifecycle-Management/03-Practice-Test-RollingUpdates-Rollback.md)
  - [04-Commands-and-Arguments-in-Docker](docs/05-Application-Lifecycle-Management/04-Commands-and-Arguments-in-Docker.md)
  - [05-Commands-and-Arguments-in-Kubernetes](docs/05-Application-Lifecycle-Management/05-Commands-and-Arguments-in-Kubernetes.md)
  - [06-Practice-Test-Commands-and-Arguments](docs/05-Application-Lifecycle-Management/06-Practice-Test-Commands-and-Arguments.md)
  - [07.Configure-Environment-Variables-in-Applications](docs/05-Application-Lifecycle-Management/07.Configure-Environment-Variables-in-Applications.md)
  - [08-Configure-ConfigMaps-in-Applications](docs/05-Application-Lifecycle-Management/08-Configure-ConfigMaps-in-Applications.md)
  - [09-Practice-Test-Env-Variables](docs/05-Application-Lifecycle-Management/09-Practice-Test-Env-Variables.md)
  - [10.Secrets](docs/05-Application-Lifecycle-Management/10.Secrets.md)
  - [11.Practice-Test-Secrets](docs/05-Application-Lifecycle-Management/11.Practice-Test-Secrets.md)
  - [12.Multi-Containers-PODs](docs/05-Application-Lifecycle-Management/12.Multi-Containers-PODs.md)
  - [13-Practice-Test-Multi-Container-Pods](docs/05-Application-Lifecycle-Management/13-Practice-Test-Multi-Container-Pods.md)
  - [14-Multi-Container-Pods-Design-Patterns](docs/05-Application-Lifecycle-Management/14-Multi-Container-Pods-Design-Patterns.md)
  - [15.Init-Containers](docs/05-Application-Lifecycle-Management/15.Init-Containers.md)
  - [16-Practice-Test-Init-Containers](docs/05-Application-Lifecycle-Management/16-Practice-Test-Init-Containers.md)
  - [17.Self-Healing-Applications](docs/05-Application-Lifecycle-Management/17.Self-Healing-Applications.md)
  - [18.Download-Presentation-Deck](docs/05-Application-Lifecycle-Management/18.Download-Presentation-Deck.md)
  
- [06-Cluster-Maintenance](docs/06-Cluster-Maintenance)

  - [01-Cluster-Maintenance-Section-Introduction](docs/06-Cluster-Maintenance/01-Cluster-Maintenance-Section-Introduction.md)
  - [02-OS-Upgrades](docs/06-Cluster-Maintenance/02-OS-Upgrades.md)
  - [03-Practice-Test-OS-Upgrades](docs/06-Cluster-Maintenance/03-Practice-Test-OS-Upgrades.md)
  - [04-Kubernetes-Software-Versions](docs/06-Cluster-Maintenance/04-Kubernetes-Software-Versions.md)
  - [05-Cluster-Upgrade-Introduction](docs/06-Cluster-Maintenance/05-Cluster-Upgrade-Introduction.md)
  - [06-Practice-Test-Cluster-Upgrade-Process](docs/06-Cluster-Maintenance/06-Practice-Test-Cluster-Upgrade-Process.md)
  - [07-Backup-and-Restore-Methods](docs/06-Cluster-Maintenance/07-Backup-and-Restore-Methods.md)
  - [08-Working-With-ETCDCTL](docs/06-Cluster-Maintenance/08-Working-With-ETCDCTL.md)
  - [09-Practice-Test-Backup-and-Restore-Methods](docs/06-Cluster-Maintenance/09-Practice-Test-Backup-and-Restore-Methods.md)
  - [10-Download-Presentation-Deck](docs/06-Cluster-Maintenance/10-Download-Presentation-Deck.md)
  

- [07-Security](docs/07-Security)
  
  - [01-Security-Section-Introduction](docs/07-Security/01-Security-Section-Introduction.md)
  - [02-Kubernetes-Security-Primitives](docs/07-Security/02-Kubernetes-Security-Primitives.md)
  - [03-Authentication](docs/07-Security/03-Authentication.md)
  - [04-TLS-Certificates](docs/07-Security/04-TLS-Certificates.md)
  - [05-TLS-Basics](docs/07-Security/05-TLS-Basics.md)
  - [06-TLS-in-Kubernetes](docs/07-Security/06-TLS-in-Kubernetes.md)
  - [07-TLS-in-Kubernetes-Certificate-Creation](docs/07-Security/07-TLS-in-Kubernetes-Certificate-Creation.md)
  - [08-View-Certificate-Details](docs/07-Security/08-View-Certificate-Details.md)
  - [09-Certificate-Health-Check-Spreadsheet](docs/07-Security/09-Certificate-Health-Check-Spreadsheet.md)
  - [10-Practice-Test-View-Certificate-Details](docs/07-Security/10-Practice-Test-View-Certificate-Details.md)
  - [11-Certificate-API](docs/07-Security/11-Certificate-API.md)
  - [12-Practice-Test-Certificates-API](docs/07-Security/12-Practice-Test-Certificates-API.md)
  - [13-kubeconfig](docs/07-Security/13-kubeconfig.md)
  - [14-Practice-Test-KubeConfig](docs/07-Security/14-Practice-Test-KubeConfig.md)
  - [15-API-Groups](docs/07-Security/15-API-Groups.md)
  - [16-Authorization](docs/07-Security/16-Authorization.md)
  - [17-RBAC](docs/07-Security/17-RBAC.md)
  - [18-Practice-Test-RBAC](docs/07-Security/18-Practice-Test-RBAC.md)
  - [19-Cluster-Roles](docs/07-Security/19-Cluster-Roles.md)
  - [20-Practice-Test-Cluster-Roles](docs/07-Security/20-Practice-Test-Cluster-Roles.md)
  - [21-Image-Security](docs/07-Security/21-Image-Security.md)
  - [22-Practice-Test-Image-Security](docs/07-Security/22-Practice-Test-Image-Security.md)
  - [23-Security-Context](docs/07-Security/23-Security-Context.md)
  - [24-Practice-Test-Security-Context](docs/07-Security/24-Practice-Test-Security-Context.md)
  - [25-Network-Policies](docs/07-Security/25-Network-Policies.md)
  - [26-Practice-Test-Network-Policies](docs/07-Security/26-Practice-Test-Network-Policies.md)
  - [27-kubectx-and-kubens-commands](docs/07-Security/27-kubectx-and-kubens-commands.md)
  - [28-Download-Presentation-Deck](docs/07-Security/28-Download-Presentation-Deck.md)


- [08-Storage](docs/08-Storage)

  - [01-Storage-Section-Introduction](docs/08-Storage/01-Storage-Section-Introduction.md)
  - [02-Introduction-to-Docker-Storage](docs/08-Storage/02-Introduction-to-Docker-Storage.md)
  - [03-Storage-in-Docker](docs/08-Storage/03-Storage-in-Docker.md)
  - [04-Volume-Driver-Plugins-in-Docker](docs/08-Storage/04-Volume-Driver-Plugins-in-Docker.md)
  - [05-Container.Storage-Interface](docs/08-Storage/05-Container.Storage-Interface.md)
  - [06-Volumes](docs/08-Storage/06-Volumes.md)
  - [07-Persistent-Volumes](docs/08-Storage/07-Persistent-Volumes.md)
  - [08-Persistent-Volume-Claims](docs/08-Storage/08-Persistent-Volume-Claims.md)
  - [09-Using-PVC-in-PODs](docs/08-Storage/09-Using-PVC-in-PODs.md)
  - [10-Practice-Test-Persistent-Volume-Claims](docs/08-Storage/10-Practice-Test-Persistent-Volume-Claims.md)
  - [11-Download-Presentation-Deck](docs/08-Storage/11-Download-Presentation-Deck.md)
  - [12-Storage-Class](docs/08-Storage/12-Storage-Class.md)
  - [13-Practice-Test-Storage-Class](docs/08-Storage/13-Practice-Test-Storage-Class.md)


- [09-Networking](docs/09-Networking)
  
  - [01-Networking-Introduction](docs/09-Networking/01-Networking-Introduction.md)
  - [02-Pre-requisite-Switching-Routing-Gateways](docs/09-Networking/02-Pre-requisite-Switching-Routing-Gateways.md)
  - [03-Pre-requisite-DNS](docs/09-Networking/03-Pre-requisite-DNS.md)
  - [04-Pre-requisite-CoreDNS](docs/09-Networking/04-Pre-requisite-CoreDNS.md)
  - [05-Pre-requisite-Network-Namespace](docs/09-Networking/05-Pre-requisite-Network-Namespace.md)
  - [06-Pre-requisite-Docker-Networking](docs/09-Networking/06-Pre-requisite-Docker-Networking.mdd)
  - [07-Pre-requisite-CNI](docs/09-Networking/07-Pre-requisite-CNI.md)
  - [08-Cluster-Networking](docs/09-Networking/08-Cluster-Networking.md)
  - [09-Practice-Test-Explore-Env](docs/09-Networking/09-Practice-Test-Explore-Env.md)
  - [10-Pod-Networking](docs/09-Networking/10-Pod-Networking.md)
  - [11-CNI-in-Kubernetes](docs/09-Networking/11-CNI-in-Kubernetes.md)
  - [12-CNI-weave](docs/09-Networking/12-CNI-weave.md)
  - [13-Practice-Test-CNI-weave](docs/09-Networking/13-Practice-Test-CNI-weave.md)
  - [14-Practice-Test-Deploy-Network-Solution](docs/09-Networking/14-Practice-Test-Deploy-Network-Solution.md)
  - [15-ipam-weave](docs/09-Networking/15-ipam-weave.md)
  - [16-Practice-Test-Networking-weave](docs/09-Networking/16-Practice-Test-Networking-weave.md)
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
