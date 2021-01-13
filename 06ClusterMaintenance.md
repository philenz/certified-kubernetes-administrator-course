- [06-Cluster-Maintenance](docs/06-Cluster-Maintenance)
  - [01-Cluster-Maintenance-Section-Introduction](docs/06-Cluster-Maintenance/01-Cluster-Maintenance-Section-Introduction.md)
  - [02-OS-Upgrades](docs/06-Cluster-Maintenance/02-OS-Upgrades.md)
  - [03-Practice-Test-OS-Upgrades](docs/06-Cluster-Maintenance/03-Practice-Test-OS-Upgrades.md)
  - [04-Kubernetes-Software-Versions](docs/06-Cluster-Maintenance/04-Kubernetes-Software-Versions.md)
  - [05-Cluster-Upgrade-Introduction](docs/06-Cluster-Maintenance/05-Cluster-Upgrade-Introduction.md)
  - [06-Practice-Test-Cluster-Upgrade-Process](docs/06-Cluster-Maintenance/06-Practice-Test-Cluster-Upgrade-Process.md)
      - Run the commands `apt update`,
      - `apt install kubeadm=1.19.0-00`,
      - and then `kubeadm upgrade apply v1.19.0`,
      - and then `apt install kubelet=1.19.0-00`
      - to upgrade the kubelet on the master node
      - [Similar on nodes except use `kubeadm upgrade node`]
  - [07-Backup-and-Restore-Methods](docs/06-Cluster-Maintenance/07-Backup-and-Restore-Methods.md)
      1. Use declarative approach and save configs in a source repo
      1. `kubectl get all --all-namespaces -o yaml > all-deploy-services.yaml`
      1. 3rd party product such as `Velero` by `HeptIO`
      1. Backup `etcd` data... `ETCDCTL_API=3 etcdctl snapshot save snapshot.db`
         - Note when using etcdctl need to specify --cacert, --cert, and --key
  - [08-Working-With-ETCDCTL](docs/06-Cluster-Maintenance/08-Working-With-ETCDCTL.md)
  - [09-Practice-Test-Backup-and-Restore-Methods](docs/06-Cluster-Maintenance/09-Practice-Test-Backup-and-Restore-Methods.md)
      - Get version of etcd using `kubectl describe pod etcd-controlplane -n kube-system`
      - https://github.com/mmumshad/kubernetes-the-hard-way/blob/master/practice-questions-answers/cluster-maintenance/backup-etcd/etcd-backup-and-restore.md
      ```bash
      ETCDCTL_API=3 etcdctl --endpoints=https://[127.0.0.1]:2379 --cacert=/etc/kubernetes/pki/etcd/ca.crt --cert=/etc/kubernetes/pki/etcd/server.crt --key=/etc/kubernetes/pki/etcd/server.key snapshot save /opt/snapshot-pre-boot.db
      ```
      - https://kubernetes.io/docs/tasks/administer-cluster/configure-upgrade-etcd/#backing-up-an-etcd-cluster
      - https://github.com/etcd-io/etcd/blob/master/Documentation/op-guide/recovery.md
  - [10-Download-Presentation-Deck](docs/06-Cluster-Maintenance/10-Download-Presentation-Deck.md)
