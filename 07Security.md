 - [07-Security](docs/07-Security)
  - [01-Security-Section-Introduction](docs/07-Security/01-Security-Section-Introduction.md)
  - [02-Kubernetes-Security-Primitives](docs/07-Security/02-Kubernetes-Security-Primitives.md)
  - [03-Authentication](docs/07-Security/03-Authentication.md)
    - Authenticate to kube-apiserver using...
        1. Static password file
            - Specify `--basic-auth-file` when starting `kube-apiserver`
        1. Static token file
            - *Slightly* better `--token-auth-file` when starting `kube-apiserver`
        1. Certificates
        1. Identity Services
  - [04-TLS-Certificates](docs/07-Security/04-TLS-Certificates.md)
      - Asymmetric encryption = private key + public key
  ```bash
  openssl genrsa -out my-bank.key 1024
  openssl rsa -in my-bank.key -pubout > my-bank.pem
  ```
      - Public key typically names *.crt or *.pem
      - Private key named *.key or *-key.pem
  - [05-TLS-Basics](docs/07-Security/05-TLS-Basics.md)
  - [06-TLS-in-Kubernetes](docs/07-Security/06-TLS-in-Kubernetes.md)
      - Server certs required for...
          1. `kube-api` server
          1. `etcd` server
          1. `kubelet` server
      - Client certs required for...
          1. `admin user` client using `kubelet` and `REST API` to access kube-api server
          1. `kube-scheduler` client to access kube-api server
          1. `kube-controller-manager` client to access kube-api server
          1. `kube-proxy` client to access kube-api server
          1. `kube-api` server to access etcd server (or use kube-api server cert)
          1. `kube-api` server to access kubelet server (or use kube-api server cert)
  - [07-TLS-in-Kubernetes-Certificate-Creation](docs/07-Security/07-TLS-in-Kubernetes-Certificate-Creation.md)
  - [08-View-Certificate-Details](docs/07-Security/08-View-Certificate-Details.md)
    - [Kubernetes Cert Checker](https://github.com/mmumshad/kubernetes-the-hard-way/tree/master/tools)
```bash
openssl x509 -in /etc/kubernetes/pki/apiserver.crt -text -noout
```
  - [09-Certificate-Health-Check-Spreadsheet](docs/07-Security/09-Certificate-Health-Check-Spreadsheet.md)
  - [10-Practice-Test-View-Certificate-Details](docs/07-Security/10-Practice-Test-View-Certificate-Details.md)
  - [11-Certificate-API](docs/07-Security/11-Certificate-API.md)
  - [12-Practice-Test-Certificates-API](docs/07-Security/12-Practice-Test-Certificates-API.md)
  - [13-kubeconfig](docs/07-Security/13-kubeconfig.md)
  - [14-Practice-Test-KubeConfig](docs/07-Security/14-Practice-Test-KubeConfig.md)
  - [15-API-Groups](docs/07-Security/15-API-Groups.md)
  - [16-Authorization](docs/07-Security/16-Authorization.md)
      1. Node
      1. ABAC (attribute based)
      1. RBAC (role based)
      1. Web hook
      1. AlwaysAllow
      1. AlwaysDeny
      - Need to restart `kube-apiserver` if make changes, or change `authorization-mode`
  - [17-RBAC](docs/07-Security/17-RBAC.md)
  - [18-Practice-Test-RBAC](docs/07-Security/18-Practice-Test-RBAC.md)
  - [19-Cluster-Roles](docs/07-Security/19-Cluster-Roles.md)
      - kubectl api-resources
      - kubectl api-versions
  - [20-Practice-Test-Cluster-Roles](docs/07-Security/20-Practice-Test-Cluster-Roles.md)
  - [21-Image-Security](docs/07-Security/21-Image-Security.md)
      - `docker.io`
      - `gcr.io`
      ```bash
      kubectl create secret docker-registry regcred \
        --docker-server=myregistry.io \
        --docker-username=myuser \
        --docker-password=mypassword \
        --docker-email=myemail@blah.co
      ```
  - [22-Practice-Test-Image-Security](docs/07-Security/22-Practice-Test-Image-Security.md)
  - [23-Security-Context](docs/07-Security/23-Security-Context.md)
  - [24-Practice-Test-Security-Context](docs/07-Security/24-Practice-Test-Security-Context.md)
  - [25-Network-Policies](docs/07-Security/25-Network-Policies.md)
  - [26-Practice-Test-Network-Policies](docs/07-Security/26-Practice-Test-Network-Policies.md)
  - [27-kubectx-and-kubens-commands](docs/07-Security/27-kubectx-and-kubens-commands.md)
  - [28-Download-Presentation-Deck](docs/07-Security/28-Download-Presentation-Deck.md)

