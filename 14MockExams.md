# Course Links
- [14-Mock-Exams](docs/14-Mock-Exams)  
  - [01-Introduction](docs/14-Mock-Exams/01-Introduction.md)
  - [02-Mock-Exam-1](docs/14-Mock-Exams/02-Mock-Exam-1.md)
  - [03-Mock-Exam-2](docs/14-Mock-Exams/03-Mock-Exam-2.md)
  - [04-CKA-MockExam-2-Solution](docs/14-Mock-Exams/04-CKA-MockExam-2-Solution.md)
  - [05-Mock-Exam-3](docs/14-Mock-Exams/05-Mock-Exam-3.md)
  - [06-CKA-MockExam-3-Solution](docs/14-Mock-Exams/06-CKA-MockExam-3-Solution.md)
# Exam 1
* `5/12 Correct`: Create a service messaging-service to expose the messaging application within the cluster on port 6379
* Should use expose... no need to specify selector...
  ```bash
  kubectl expose pod messaging --name messaging-service --port 6379 --target-port 6379
  ```
* `10/12 Wrong`: Expose the hr-web-app as service hr-web-app-service application on port 30082 on the nodes on the cluster
  ```bash
  kubectl expose deployment hr-web-app --type=NodePort --port=8080 --name=hr-web-app-service --dry-run -o yaml > hr-web-app-service.yaml
  # ...to generate a service definition file.
  # Then edit the nodeport in it and create a service.
  ```
* `12/12 Wrong`: Create a Persistent Volume with the given specification
  * Got the specification of host path wrong
  * Really useful!!!!...
  ```bash
  kubectl explain pv --recursive | less
  ```
  * manifest needs...
  ```yaml
  hostPath:
    path: /blah
  ```
# Exam 2
* `6/8 Wrong`: Create a new user called john. Grant him access to the cluster. John should have permission to create, list, get, update and delete pods in the development namespace . The private key exists in the location: /root/CKA/john.key and csr at /root/CKA/john.csr
- CSR: john-developer Status:Approved
- Role Name: developer, namespace: development, Resource: Pods
- Access: User 'john' has appropriate permissions
```bash
# https://kubernetes.io/docs/tasks/tls/managing-tls-in-a-cluster/
# create csr...
cat <<EOF | kubectl apply -f -
apiVersion: certificates.k8s.io/v1
kind: CertificateSigningRequest
metadata:
  name: john-developer
spec:
  request: $(cat john.csr | base64 | tr -d '\n')
  signerName: kubernetes.io/kubelet-serving
  usages:
  - digital signature
  - key encipherment
  - server auth
EOF
kubectl get csr
kubectl certificate approve john-developer
# create role...
kubectl create role developer --resource=pods --verb=create,list,get,update,delete --namespace development
# create rolebinding...
kubectl create rolebinding bob --role=developer --user=john --namespace=development
# verify...
kubectl auth can-i update pods --namespace=development --as=john
```
* `7/8 Wrong`: Create an nginx pod called nginx-resolver using image nginx, expose it internally with a service called nginx-resolver-service. Test that you are able to look up the service and pod names from within the cluster. Use the image: busybox:1.28 for dns lookup. Record results in /root/CKA/nginx.svc and /root/CKA/nginx.pod
- Pod: nginx-resolver created
- Service DNS Resolution recorded correctly
- Pod DNS resolution recorded correctly
```bash
k run nginx-resolver --image=nginx
k expose pod nginx-resolver --name=nginx-resolver-service --port=80 --target-port=80 --type=ClusterIP
kubectl run test-nslookup --image=busybox:1.28 --rm -it -- nslookup nginx-resolver-service > /root/CKA/nginx.svc
kubectl run test-nslookup --image=busybox:1.28 --rm -it -- nslookup 10-32-0-5.default.pod > /root/CKA/nginx.pod
```
# Exam 3

