# Course Links
- [13-Lightning-Labs](docs/13-Lightning-Labs)  
  - [01-Lightning-Labs-Introduction](docs/13-Lightning-Labs/01-Lightning-Labs-Introduction.md)
  - [02-Lightning-Lab-1](docs/13-Lightning-Labs/02-Lightning-Lab-1.md)
# Lab Questions

## 1/7 Correct
* Upgrade the current version of kubernetes from 1.18 to 1.19.0 exactly using the kubeadm utility.
* Make sure that the upgrade is carried out one node at a time starting with the master node.
* To minimize downtime, the deployment gold-nginx should be rescheduled on an alternate node before upgrading each node.

```bash
# Pretty much just follow this...
# https://kubernetes.io/docs/tasks/administer-cluster/kubeadm/kubeadm-upgrade/
# or the 1.19 version...
# https://v1-19.docs.kubernetes.io/docs/tasks/administer-cluster/kubeadm/kubeadm-upgrade/
```
### on the master node as root...
```bash
kubectl drain controlplane --ignore-daemonsets

apt update
apt-cache madison kubeadm | head
apt-mark unhold kubeadm
apt-get update && apt-get install -y kubeadm=1.19.4-00
apt-mark hold kubeadm
kubeadm version

kubeadm upgrade plan
kubeadm upgrade apply v1.19.4

apt-mark unhold kubelet kubectl
apt-get update && apt-get install -y kubelet=1.19.4-00 kubectl=1.19.4-00
apt-mark hold kubelet kubectl

sudo systemctl daemon-reload
sudo systemctl restart kubelet

kubectl uncordon controlplane

kubectl drain node01 --ignore-daemonsets
```
### on the worker node as root...
```bash
apt update
apt-cache madison kubeadm | head
apt-mark unhold kubeadm
apt-get update && apt-get install -y kubeadm=1.19.3-00
apt-mark hold kubeadm
kubeadm version

kubeadm upgrade node

apt-mark unhold kubelet kubectl
apt-get update && apt-get install -y kubelet=1.19.3-00 kubectl=1.19.3-00
apt-mark hold kubelet kubectl

sudo systemctl daemon-reload
sudo systemctl restart kubelet
```
### on the master node as root...
```bash
kubectl uncordon node01
kubectl get nodes
```

## 2/7 Correct
* Print the names of all deployments in the admin2406 namespace in the following format:

DEPLOYMENT | CONTAINER_IMAGE | READY_REPLICAS | NAMESPACE
--- | --- | --- | ---
\<deployment name> | \<container image used> | \<ready replica count> | \<namespace>
 | 

* The data should be sorted by the increasing order of the deployment name.

```bash
# narrow down using jsonpath, e.g....
k get deployments -o jsonpath='{ .items[0].spec.template.spec.containers[0].image }'

k get deployments --sort-by=.metadata.name -o custom-columns="DEPLOYMENT:metadata.name,CONTAINER_IMAGE:.spec.template.spec.containers[].image,READ_REPLICAS:status.readyReplicas,NAMESPACE:metadata.namespace"
```

## 3/7 Correct
* A kubeconfig file called admin.kubeconfig has been created in /root/CKA. There is something wrong with the configuration. Troubleshoot and fix it.

```bash
cp ~/.kube/config ~/CKA/admin.kubeconfig
kubectl cluster-info --kubeconfig /root/CKA/admin.kubeconfig
```

## 4/7 Correct
* Create a new deployment called nginx-deploy, with image nginx:1.16 and 1 replica.
* Next upgrade the deployment to version 1.17 using rolling update.
* Make sure that the version upgrade is recorded in the resource annotation.

```bash
kubectl create deployment  nginx-deploy --image=nginx:1.16
kubectl set image deployment/nginx-deploy nginx=nginx:1.17 --record
```

## 5/7 Correct
* A new deployment called alpha-mysql has been deployed in the alpha namespace.
* However, the pods are not running. Troubleshoot and fix the issue.
* The deployment should make use of the persistent volume alpha-pv to be mounted at /var/lib/mysql and should use the environment variable MYSQL_ALLOW_EMPTY_PASSWORD=1 to make use of an empty root password.

```bash
# delete existing pvc
# create a new one matching name in deployment
# ensure characteristics of pvc (e.g.: size) are a match for the pv
```
```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  annotations:
  name: mysql-alpha-pvc
  namespace: alpha
spec:
  accessModes:
  - ReadWriteOnce
  resources:
    requests:
      storage: 1Gi
  storageClassName: slow
```

## 6/7 Correct
* Take the backup of ETCD at the location /opt/etcd-backup.db on the master node.

```bash
export ETCDCTL_API=3
etcdctl snapshot save --cacert=/etc/kubernetes/pki/etcd/ca.crt --cert=/etc/kubernetes/pki/etcd/server.crt --key=/etc/kubernetes/pki/etcd/server.key --endpoints=127.0.0.1:2379 /opt/etcd-backup.db
```

## 7/7 Correct
* Create a pod called `secret-1401` in the `admin1401` namespace using the `busybox` image.
* The container within the pod should...
  * be called `secret-admin`
  * sleep for `4800` seconds
* The container should mount a read-only secret volume called `secret-volume` at the path `/etc/secret-volume`.
* The secret being mounted has already been created for you and is called `dotfile-secret`.
```bash
# Configure a pod to use a ConfigMap...
# https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/
# Secrets...
# https://kubernetes.io/docs/concepts/configuration/secret/
# Distribute Credentials Securely Using Secrets...
# https://kubernetes.io/docs/tasks/inject-data-application/distribute-credentials-secure/
```
```yaml
apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: null
  labels:
    run: secret-1401
  name: secret-1401
  namespace: admin1401
spec:
  volumes:
  - name: secret-volume
    secret:
      secretName: dotfile-secret
  containers:
  - command:
    - sleep
    args:
    - "4800"
    image: busybox
    name: secret-admin
    volumeMounts:
    - name: secret-volume
      readOnly: true
      mountPath: "/etc/secret-volume"
```

