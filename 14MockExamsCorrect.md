# Exam 1
* `1/12 Correct`: Deploy a pod named nginx-pod using the nginx:alpine image
* `2/12 Correct`: Deploy a messaging pod using the redis:alpine image with the labels set to tier=msg
* `3/12 Correct`: Create a namespace named apx-x9984574
* `4/12 Correct`: Get the list of nodes in JSON format and store it in a file at /opt/outputs/nodes-z3444kd9.json
* `5/12 Correct`: Create a service messaging-service to expose the messaging application within the cluster on port 6379
* `6/12 Correct`: Create a deployment named hr-web-app using the image kodekloud/webapp-color with 2 replicas
* `7/12 Correct`: Create a static pod named static-busybox on the master node that uses the busybox image and the * * `8/12 Correct`: Create a POD in the finance namespace named temp-bus with the image redis:alpine
* `9/12 Correct`: A new application orange is deployed. There is something wrong with it. Identify and fix the issue
* `11/12 Correct`: Use JSON PATH query to retrieve the osImages of all the nodes and store it in a file /opt/outputs/nodes_os_x43kj56.txt
# Exam 2
* `1/8 Correct`: Take a backup of the etcd cluster and save it to /opt/etcd-backup.db
* `2/8 Correct`: Create a Pod called redis-storage with image: redis:alpine with a Volume of type emptyDir that lasts for the life of the Pod. Specs on the right.
* `3/8 Correct`: Create a new pod called super-user-pod with image busybox:1.28. Allow the pod to be able to set system_time
* `4/8 Correct`: A pod definition file is created at /root/CKA/use-pv.yaml. Make use of this manifest file and mount the persistent volume called pv-1. Ensure the pod is running and the PV is bound.
* `5/8 Correct`: Create a new deployment called nginx-deploy, with image nginx:1.16 and 1 replica. Record the version. Next upgrade the deployment to version 1.17 using rolling update. Make sure that the version upgrade is recorded in the resource annotation.
* `8/8 Correct`: Create a static pod on node01 called nginx-critical with image nginx. Create this pod on node01 and make sure that it is recreated/restarted automatically in case of a failure.