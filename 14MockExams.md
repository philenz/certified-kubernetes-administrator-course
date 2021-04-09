# Course Links
- [14-Mock-Exams](docs/14-Mock-Exams)  
  - [01-Introduction](docs/14-Mock-Exams/01-Introduction.md)
  - [02-Mock-Exam-1](docs/14-Mock-Exams/02-Mock-Exam-1.md)
  - [03-Mock-Exam-2](docs/14-Mock-Exams/03-Mock-Exam-2.md)
  - [04-CKA-MockExam-2-Solution](docs/14-Mock-Exams/04-CKA-MockExam-2-Solution.md)
  - [05-Mock-Exam-3](docs/14-Mock-Exams/05-Mock-Exam-3.md)
  - [06-CKA-MockExam-3-Solution](docs/14-Mock-Exams/06-CKA-MockExam-3-Solution.md)
# Exam 1
* `1/12 Correct`: Deploy a pod named nginx-pod using the nginx:alpine image
* `2/12 Correct`: Deploy a messaging pod using the redis:alpine image with the labels set to tier=msg
* `3/12 Correct`: Create a namespace named apx-x9984574
* `4/12 Correct`: Get the list of nodes in JSON format and store it in a file at /opt/outputs/nodes-z3444kd9.json
* `5/12 Correct`: Create a service messaging-service to expose the messaging application within the cluster on port 6379
* Should use expose... no need to specify selector...
  ```bash
  kubectl expose pod messaging --name messaging-service --port 6379 --target-port 6379
  ```
* `6/12 Correct`: Create a deployment named hr-web-app using the image kodekloud/webapp-color with 2 replicas
* `7/12 Correct`: Create a static pod named static-busybox on the master node that uses the busybox image and the command sleep 1000
* `8/12 Correct`: Create a POD in the finance namespace named temp-bus with the image redis:alpine
* `9/12 Correct`: A new application orange is deployed. There is something wrong with it. Identify and fix the issue
* `10/12 Wrong`: Expose the hr-web-app as service hr-web-app-service application on port 30082 on the nodes on the cluster
  ```bash
  kubectl expose deployment hr-web-app --type=NodePort --port=8080 --name=hr-web-app-service --dry-run -o yaml > hr-web-app-service.yaml
  # ...to generate a service definition file.
  # Then edit the nodeport in it and create a service.
  ```
  * Did it totally differently... created a service... but got port and nodeport wrong way round
* `11/12 Correct`: Use JSON PATH query to retrieve the osImages of all the nodes and store it in a file /opt/outputs/nodes_os_x43kj56.txt
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
# Exam 3

