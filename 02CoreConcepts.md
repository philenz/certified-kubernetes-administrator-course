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
  ```bash
  kubectl run redis --image=redis --dry-run=client -o yaml > redis.yaml
  ```
  - [11-Practice-Test-Introduction](docs/02-Core-Concepts/11-Practice-Test-Introduction.md)
  - [12-Practice-Test-PODs](docs/02-Core-Concepts/12-Practice-Test-PODs.md)
  - [13-ReplicaSets](docs/02-Core-Concepts/13-ReplicaSets.md)
  ```yml
  apiVersion: apps/v1
  kind: ReplicaSet
  metadata:
    name: myreplicaset
    labels:
      app: myapp
      type: front-end
  spec:
    template:
      metadata:
        name: barney
        labels:
          app: rubble
          type: front-end
      spec:
        containers:
          - name: nginx-container
            image: nginx
    replicas: 3
    selector:
      matchLabels:
        type: front-end
  ```
  - [14-Practice-Tests-ReplicaSet](docs/02-Core-Concepts/14-Practice-Tests-ReplicaSet.md)
  - [15-Deployments](docs/02-Core-Concepts/15-Deployments.md)
  ```bash
  kubectl create deployment httpd-frontend --replicas=3 --image=httpd:2.4-alpine --dry-run=client -o yaml > deploy.yaml
  ```
  - [16-Practice-Tests-Deployments](docs/02-Core-Concepts/16-Practice-Tests-Deployments.md)
  - [17-Namespaces](docs/02-Core-Concepts/17-Namespaces.md)
      - On install: kube-system / Default / kube-public
      - DNS: `db.dev.svc.cluster.local`
      ```bash
      kubectl get-pods --all-namespaces
      kubectl config set-context $(kubectl config current-context) --namespace=dev
      ```
  - [18-Practice-Test-Namespaces](docs/02-Core-Concepts/18-Practice-Test-Namespaces.md)
  - [19-Services](docs/02-Core-Concepts/19-Services.md)
      - NodePort
      ```yml
      apiVersion: v1
      kind: Service
      metadata:
        name: front-end
      spec:
        type: NodePort
        ports:
          - targetPort: 80
            port: 80
            nodePort: 30008
        selector:
          app: myapp
          type: front-end
      ```
      - ClusterIp
      ```yml
      apiVersion: v1
      kind: Service
      metadata:
        name: back-end
      spec:
        type: ClusterIp
        ports:
          - targetPort: 80
            port: 80
        selector:
          app: myapp
          type: back-end
      ```
      - LoadBalancer
          - Config same as NodePort, just change type to LoadBalancer
  - [20-Services-ClusterIP](docs/02-Core-Concepts/20-Services-ClusterIP.md)
  - [21-Practice-Test-Services](docs/02-Core-Concepts/21-Practice-Test-Services.md)
  - [22-Imperative-Commands-with-kubectl](docs/02-Core-Concepts/22-Imperative-Commands-with-kubectl.md)
  ```bash
  # imperative...
  kubectl run --image=nginx nginx
  kubectl create deployment --image=nginx nginx
  kubectl expose deployment nginx --port=80
  kubectl edit deployment nginx
  kubectl scale deployment nginx --replicas=5
  kubectl set image deployment nginx nginx=nginx:1.18
  kubectl create -f nginx.yaml
  kubectl replace -f nginx.yaml
  kubectl delete -f nginx.yaml
  kubectl expose pod redis --port=6379 --name redis-service
  ```
  ```bash
  # declarative...
  kubectl apply -f nginx.yaml

  # bunch of manifests...
  kubectl apply -f /tmp/myapp

  ```
  - [23-Practice-Test-Imperative-Commands](docs/02-Core-Concepts/23-Practice-Test-Imperative-Commands.md)
  - [24-Attachments](docs/02-Core-Concepts/24-Attachments.md)
