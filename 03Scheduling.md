- [03-Scheduling](docs/03-Scheduling)

  - [01-Scheduling-Section-Introduction](docs/03-Scheduling/01-Scheduling-Section-Introduction.md)
  - [02-Manual-Scheduling](docs/03-Scheduling/02-Manual-Scheduling.md)
  - [03-Practice-Test-Manual-Scheduling](docs/03-Scheduling/03-Practice-Test-Manual-Scheduling.md)
  - [04-Labels-and-Selectors](docs/03-Scheduling/04-Labels-and-Selectors.md)
  - [05-Practice-Test-Scheduling](docs/03-Scheduling/05-Practice-Test-Scheduling.md)
  - [06-Taints-and-Tolerations](docs/03-Scheduling/06-Taints-and-Tolerations.md)
  ```bash
  # taint
  kubectl taint nodes node1 app=blue:NoSchedule
  # untaint
  kubectl taint nodes node1 app=blue:NoSchedule-
  ```
  - [07-Practice-Test-Taints-and-Tolerations](docs/03-Scheduling/07-Practice-Test-Taints-and-Tolerations.md)
  - [08-Node-Selectors](docs/03-Scheduling/08-Node-Selectors.md)
  ```yaml
  nodeSelector:
    size: Large
  ```
  ```bash
  kubectl label nodes node-1 size=Large
  ```
  - [09-Node-Affinity](docs/03-Scheduling/09-Node-Affinity.md)
  - [10-Practice-Test-Node-Affinity](docs/03-Scheduling/10-Practice-Test-Node-Affinity.md)
  - [11.Taints-and-Tolerations-vs-Node-Affinity](docs/03-Scheduling/11.Taints-and-Tolerations-vs-Node-Affinity.md)
  - [12-Resource-Limits](docs/03-Scheduling/12-Resource-Limits.md)
  ```yaml
  resources:
     requests:
      memory: "1Gi"
      cpu: "1"
     limits:
      memory: "2Gi"
      cpu: "2"
  ```
      - Create `LimitRange` objects to set limits per namespace
  - [13-Practice-Test-Resource-Limits](docs/03-Scheduling/13-Practice-Test-Resource-Limits.md)
  - [14-DaemonSets](docs/03-Scheduling/14-DaemonSets.md)
  - [15-Practice-Test-DaemonSets](docs/03-Scheduling/15-Practice-Test-DaemonSets.md)
  - [16-Static-Pods](docs/03-Scheduling/16-Static-Pods.md)
      - `/etc/kubernetes/manifests`
  - [17-Practice-Test-StaticPods](docs/03-Scheduling/17-Practice-Test-StaticPods.md)
  - [18-Multiple-Schedulers](docs/03-Scheduling/18-Multiple-Schedulers.md)
  - [19-Practice-Test-Multiple-Schedulers](docs/03-Scheduling/19-Practice-Test-Multiple-Schedulers.md)
  - [20-Configuring-Kubernetes-Schedulers](docs/03-Scheduling/20-Configuring-Kubernetes-Schedulers.md)
  - [21-Download-Presentation-Deck](docs/03-Scheduling/21-Download-Presentation-Deck.md)

