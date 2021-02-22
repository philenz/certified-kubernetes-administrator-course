- [08-Storage](docs/08-Storage)
  - [01-Storage-Section-Introduction](docs/08-Storage/01-Storage-Section-Introduction.md)
  - [02-Introduction-to-Docker-Storage](docs/08-Storage/02-Introduction-to-Docker-Storage.md)
  - [03-Storage-in-Docker](docs/08-Storage/03-Storage-in-Docker.md)
     - Storage Drivers
         - aufs, zfs, btrfs, device mapper, overlay
     - Volume Drivers
         - local (under /var/lib/docker), azure file storage, netapp, etc...
  - [04-Volume-Driver-Plugins-in-Docker](docs/08-Storage/04-Volume-Driver-Plugins-in-Docker.md)
  - [05-Container.Storage-Interface](docs/08-Storage/05-Container.Storage-Interface.md)
     - CRI is an interface into k8s for container runtimes (e.g.: Docker, rkt, cri-o)
     - CNI is an interface into k8s for network plugins (e.g.: weaveworks, flannel, cilium)
     - CSI  is an interface into k8s for storage plugins (e.g.: EBS, portworx, GlusterFS)
  - [06-Volumes](docs/08-Storage/06-Volumes.md)
  - [07-Persistent-Volumes](docs/08-Storage/07-Persistent-Volumes.md)
  - [08-Persistent-Volume-Claims](docs/08-Storage/08-Persistent-Volume-Claims.md)
  - [09-Using-PVC-in-PODs](docs/08-Storage/09-Using-PVC-in-PODs.md)
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: mypod
spec:
  containers:
    - name: myfrontend
      image: nginx
      volumeMounts:
      - mountPath: "/var/www/html"
        name: mypd
  volumes:
    - name: mypd
      persistentVolumeClaim:
        claimName: myclaim
```
  - [10-Practice-Test-Persistent-Volume-Claims](docs/08-Storage/10-Practice-Test-Persistent-Volume-Claims.md)
  - [11-Download-Presentation-Deck](docs/08-Storage/11-Download-Presentation-Deck.md)
     * Additional topics about `StatefulSets` are out of scope for the exam. 
  - [12-Storage-Class](docs/08-Storage/12-Storage-Class.md)
     * Automatically provisions disk specified by pvc.
  - [13-Practice-Test-Storage-Class](docs/08-Storage/13-Practice-Test-Storage-Class.md)
