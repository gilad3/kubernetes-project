# 🚀 Kubernetes Project

## 🌟 Introduction
Welcome to the Kubernetes Project! This setup uses Kubernetes to deploy a MySQL database and an Apache HTTP server, complete with autoscaling and persistent storage.

## 🛠️ Components
1. **💾 MySQL**:
   - Created Persistent Volume Claim (PVC) for durable storage.
   - Used Kubernetes Secret for secure credentials.
   - Deployed with the `mysql:5.7` image.

2. **🌐 Apache**:
   - Deployed using the `httpd:latest` image.
   - Configured a Service to expose Apache to the outside world.

3. **📈 Scaling**:
   - Implemented a Horizontal Pod Autoscaler (HPA) to handle traffic spikes based on CPU utilization.

## 📋 Commands
- **Apply configurations**: 
  ```sh
  kubectl apply -f <filename>.yml
