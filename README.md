# MongoDB & Mongo Express Deployment on Kubernetes (AWS)

This project demonstrates how to deploy **MongoDB** and **Mongo Express** on **Kubernetes**, using AWS **EBS** for persistent storage.  
It showcases secure credential management using **Secrets**, configuration via **ConfigMaps**, and external access through a **LoadBalancer Service**.

---

##  Project Architecture

Client → LoadBalancer (mongo-express-svc) → Mongo Express Pods → MongoDB Service (ClusterIP) → MongoDB Pod (Persistent Data)

### Key Points:
- **MongoDB** stores data persistently on AWS **EBS** using a PVC.
- **Mongo Express** is deployed as a frontend to manage MongoDB.
- **Secrets** store the database credentials securely.
- **ConfigMap** stores the internal MongoDB connection URL.

---

##  Files Overview

| File | Description |
|------|--------------|
| `mongo-app.yml` | Contains MongoDB Deployment, Service, PVC, and Secret. |
| `mongo-express-app.yml` | Contains Mongo Express Deployment, ConfigMap, and LoadBalancer Service. |

---

##  Technologies Used

- **Kubernetes** (Deployments, Services, Secrets, PVCs, PVs)
- **AWS EBS CSI Driver**
- **MongoDB** (official image)
- **Mongo Express**
- **ConfigMap** for environment setup
- **YAML configuration**

---

##  Prerequisites

Before deploying, make sure you have:
- A running **Kubernetes cluster** (EKS / Minikube / Kind)
- `kubectl` installed and configured
- AWS EBS CSI driver installed
- Proper IAM permissions for provisioning volumes

---

##  Deployment Steps

1. **Apply all YAML files:**
   ```bash
   kubectl apply -f mongo-app.yml
   kubectl apply -f mongo-express-app.yml

2. **Verify that pods are running:**
      ```bash 
      kubectl get pods
3. **Access Mongo Express dashboard:**
      ```bash
      kubectl get svc mongo-express-svc
  Open your browser at:
     http://NODE-IP:32000
