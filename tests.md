# 🧪 Testing and Verification

# Verify MySQL Deployment

kubectl get pods -l app=mysql

# Output:

NAME READY STATUS RESTARTS AGE
mysql-deployment-5c97bff567-btgcq 1/1 Running 0 84m

kubectl describe pod mysql-deployment-5c97bff567-btgcq

# Output:

Name: mysql-deployment-5c97bff567-btgcq
Namespace: default
Labels: app=mysql
...
Events:
Type Reason Age From Message

---

Normal Scheduled 84m default-scheduler Successfully assigned default/mysql-deployment-5c97bff567-btgcq to minikube
Normal Pulled 84m kubelet, minikube Container image "mysql:5.7" already present on machine
Normal Created 84m kubelet, minikube Created container mysql
Normal Started 84m kubelet, minikube Started container mysql

kubectl logs mysql-deployment-5c97bff567-btgcq

# Output:

2023-02-05T12:45:23.456789Z 0 [Note] mysqld: ready for connections.
Version: '5.7.34' socket: '/var/run/mysqld/mysqld.sock' port: 3306 MySQL Community Server (GPL)

# Verify Apache Deployment

kubectl get pods -l app=apache

# Output:

NAME READY STATUS RESTARTS AGE
apache-deployment-5fd955856f-64cd5 1/1 Running 0 169m

kubectl describe pod apache-deployment-5fd955856f-64cd5

# Output:

Name: apache-deployment-5fd955856f-64cd5
Namespace: default
Labels: app=apache
...
Events:
Type Reason Age From Message

---

Normal Scheduled 169m default-scheduler Successfully assigned default/apache-deployment-5fd955856f-64cd5 to minikube
Normal Pulled 169m kubelet, minikube Container image "httpd:latest" already present on machine
Normal Created 169m kubelet, minikube Created container apache
Normal Started 169m kubelet, minikube Started container apache

kubectl logs apache-deployment-5fd955856f-64cd5

# Output:

[Mon Feb 05 12:45:23.456789 2023] [mpm_event:notice] [pid 1:tid 140670055229760] AH00489: Apache/2.4.46 (Unix) configured -- resuming normal operations
[Mon Feb 05 12:45:23.456789 2023] [core:notice] [pid 1:tid 140670055229760] AH00094: Command line: 'httpd -D FOREGROUND'

# Verify Horizontal Pod Autoscaler (HPA)

kubectl get hpa

# Output:

NAME REFERENCE TARGETS MINPODS MAXPODS REPLICAS AGE
apache-hpa Deployment/apache-deployment cpu: <unknown>/50% 1 3 1 171m
