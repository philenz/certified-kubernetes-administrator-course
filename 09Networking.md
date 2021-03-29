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
  - [16-Practice-Test-Networking-weave](docs/09-Networking/16-Practice-Test-Networking-weave.md)
  - [17-Service-Networking](17-Service-Networking.md)
    - Service types...
    1. `ClusterIP`: the default type, will create a Service resource with an IP address from the cluster’s pool, such a Service will be available from within the cluster only (or with kube-proxy)
    1. `NodePort`: will open a TCP port on each WorkerNode EС2, “behind it” automatically will create a ClusterIP Service and will route traffic from this TCP port on an ЕС2 to this ClusterIP – such a service will be accessible from the world (obviously, if an EC2 has a public IP), or within a VPC
    1. `LoadBalancer`: will create an external Load Balancer (AWS Classic LB), “behind it” automatically will create a NodePort, then ClusterIP and in this way will route traffic from the Load Balancer to a pod in a cluster
    1. `ExternalName`: something like a DNS-proxy – in response to such a Service will return a record taken via CNAME of the record specified in the externalName
    - IP range for pods and services must not overlap
  - [18-Practice-Test-Service-Networking](docs/09-Networking/18-Practice-Test-Service-Networking.md)
  - [19-DNS-in-kubernetes](docs/09-Networking/19-DNS-in-kubernetes.md)
      - Service DNS
          - _service.namespace.type.root_
          - web-service.apps.svc.cluster.local
      - Pod DNS (if enabled)
          - _pod-ip.namespace.type.root_
          - 10-244-2-5.apps.pod.cluster.local
  - [20-CoreDNS-in-Kubernetes](docs/09-Networking/20-CoreDNS-in-Kubernetes.md)
      - `/etc/coredns/Corefile`
      - `kubectl describe configmap coredns -n kube-system`
  - [21-Practice-Test-CoreDNS-in-Kubernetes](docs/09-Networking/21-Practice-Test-CoreDNS-in-Kubernetes.md)
  - [22-Ingress](docs/09-Networking/22-Ingress.md)
      - Deploy an Ingress controller (e.g.: nginx, haproxy, traefik)
      - Configure Ingress resources (config file)
      - Ingress Controller manifests...
          - Deployment
          - Service
          - ConfigMap
          - Auth
      - Ingress resource = manifest Kind = Ingress
  - [23-Ingress-Annotations-and-rewrite-target](docs/09-Networking/23-Ingress-Annotations-and-rewrite-target.md)
    - https://kubernetes.github.io/ingress-nginx/examples/rewrite/
    ```yaml
    apiVersion: extensions/v1beta1
    kind: Ingress
    metadata:
      annotations:
        nginx.ingress.kubernetes.io/rewrite-target: /$2
      name: rewrite
      namespace: default
    spec:
      rules:
      - host: rewrite.bar.com
        http:
          paths:
          - backend:
              serviceName: http-svc
              servicePort: 80
            path: /something(/|$)(.*)
    ```
  - [24-Practice-Test-CKA-Ingress-Net-1](docs/09-Networking/24-Practice-Test-CKA-Ingress-Net-1.md)
    ```bash
    k get ingress --all-namespaces
    k describe ingress --namespace app-space
    k edit ingress --namespace app-space
    ```
  - [25-Practice-Test-CKA-Ingress-Net-2](docs/09-Networking/25-Practice-Test-CKA-Ingress-Net-2.md)
    ```sh
    k create namespace ingress-space
    k create configmap nginx-configuration --namespace ingress-space
    k create serviceaccount ingress-serviceaccount --namespace ingress-space
    k get roles,rolebindings --namespace ingress-space
    k apply -f /var/answers/ingress-controller.yaml
    k apply -f /var/answers/ingress-service.yaml 
    k apply -f /var/answers/ingress-resource.yaml 
    ```
    ```yaml
    ---
    apiVersion: apps/v1
    kind: Deployment
    metadata:
      name: ingress-controller
      namespace: ingress-space
    spec:
      replicas: 1
      selector:
        matchLabels:
          name: nginx-ingress
      template:
        metadata:
          labels:
            name: nginx-ingress
        spec:
          serviceAccountName: ingress-serviceaccount
          containers:
            - name: nginx-ingress-controller
              image: quay.io/kubernetes-ingress-controller/nginx-ingress-controller:0.21.0
              args:
                - /nginx-ingress-controller
                - --configmap=$(POD_NAMESPACE)/nginx-configuration
                - --default-backend-service=app-space/default-http-backend
              env:
                - name: POD_NAME
                  valueFrom:
                    fieldRef:
                      fieldPath: metadata.name
                - name: POD_NAMESPACE
                  valueFrom:
                    fieldRef:
                      fieldPath: metadata.namespace
              ports:
                - name: http
                  containerPort: 80
                - name: https
                  containerPort: 443
    ```
    ```yaml
    ---
    apiVersion: v1
    kind: Service
    metadata:
      name: ingress
      namespace: ingress-space
    spec:
      type: NodePort
      ports:
      - port: 80
        targetPort: 80
        protocol: TCP
        nodePort: 30080
        name: http
      - port: 443
        targetPort: 443
        protocol: TCP
        name: https
      selector:
        name: nginx-ingress   
    ```
    ```yaml
    ---
    apiVersion: extensions/v1beta1
    kind: Ingress
    metadata:
      name: ingress-wear-watch
      namespace: app-space
      annotations:
        nginx.ingress.kubernetes.io/rewrite-target: /
        nginx.ingress.kubernetes.io/ssl-redirect: "false"
    spec:
      rules:
      - http:
          paths:
          - path: /wear
            backend:
              serviceName: wear-service
              servicePort: 8080
          - path: /watch
            backend:
              serviceName: video-service
              servicePort: 8080
    ```
  - [26-Dowload-Presentation-Deck](docs/09-Networking/26-Download-Presentation-Deck.md)
