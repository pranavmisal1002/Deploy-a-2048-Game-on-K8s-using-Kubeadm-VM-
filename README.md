# 🎮 Deploy a 2048-Game Application on Kubernetes using Kubeadm (Virtual Machines)

This project demonstrates how to set up a **Kubernetes cluster using Kubeadm** on virtual machines and deploy a **containerized game application** with **auto-scaling support**.

### The setup includes:

- Multi-node Kubernetes cluster (**Master + Worker**)  
- Application deployment using Kubernetes **YAML manifests**  
- Service exposure for **external access**  
- Horizontal Pod Autoscaler (**HPA**) for automatic scalability
   
## 🧰 Technologies Used

- Kubernetes (Kubeadm)  
- Docker / Container Runtime (containerd or Docker)  
- VirtualBox / VMware *(or AWS EC2 for cloud setup)*  
- Kubernetes YAML Manifests  
- Horizontal Pod Autoscaler (HPA)

## 📚 Prerequisites

- VirtualBox or VMware installed  
  *(AWS EC2 can also be used — VirtualBox used in this project)*  
- Two Ubuntu virtual machines:
  - **1 Master Node**
  - **1 Worker Node**
- Basic Linux and Kubernetes knowledge
## 🛠️ Complete Project Setup Guide
### ✅ Step 1: Install Virtualization Software

Install one of the following virtualization platforms:

- **VirtualBox** *(recommended)*  
- **VMware Workstation*  

👉 You may also use **AWS EC2 instances** instead of local virtual machines.

### ✅ Step 2: Create Two Virtual Machines

Create and launch the following virtual machines:

| Node Type   | Purpose                          |
|------------|----------------------------------|
| Master Node | Kubernetes Control Plane         |
| Worker Node | Runs application pods            |

Ensure the following:

- Both machines are on the **same network**
- **Internet access** is enabled on both VMs

### ✅ Step 3: Set Up Kubernetes Cluster Using Kubeadm

Install and configure the Kubernetes cluster (Master + Worker nodes) by following the complete kubeadm setup guide:

👉 **[Kubeadm Cluster Setup Documentation](https://github.com/pranavmisal1002/kubeadm-cluster-setup/blob/main/README.md#setting-up-kubernetes-on-virtualbox-virtual-machines)**

This guide covers:

- Container runtime setup  
- kubeadm, kubelet, kubectl installation  
- Cluster initialization  
- Worker node joining  
- Network plugin configuration

## 🚀 Deploy Game Application
### ✅ Step 4: Create Deployment File

Create a Kubernetes deployment manifest:

```text
game-deployment.yaml
```
This file defines:

- Game container image  
- Number of replicas  
- Pod configuration
Apply the deployment:
```bash
kubectl apply -f game-deployment.yaml
```
### ✅ Step 5: Create Service File

Create a Kubernetes service manifest:

```text
game-service.yaml
```
This service exposes the game application outside the Kubernetes cluster.
Apply the service:
```bash
kubectl apply -f game-service.yaml
```
Verify service creation:
```bash
kubectl get svc
```
### 📈 Step 6: Create Horizontal Pod Autoscaler (HPA)

Create the HPA manifest:

```text
hpa.yaml
```
Apply the autoscaling configuration:
```bash
kubectl apply -f hpa.yaml
```
Verify HPA status:
```bash
kubectl get hpa
```
## 🌍 Access the Application

Retrieve the service external IP:

```bash
kubectl get svc
```
Open the application in your browser:
```bash
http://<EXTERNAL_IP>:<PORT>
```
🎉 Your game application is now successfully running on Kubernetes!

![Kubernetes](https://img.shields.io/badge/Kubernetes-1.30-blue)
![DevOps](https://img.shields.io/badge/DevOps-Project-green)
