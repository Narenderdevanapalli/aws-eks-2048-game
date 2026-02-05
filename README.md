# AWS EKS 2048 Game Project

This project demonstrates deploying a **2048 game application** on **AWS EKS (Elastic Kubernetes Service)** using Kubernetes manifests. The project includes cluster setup using `eksctl`, application deployment, service, and ingress configuration.

---

## Project Structure



aws-eks-2048-game/
├── eks/
│ └── cluster.yaml # EKS cluster configuration
├── k8s/
│ └── 2048-app.yaml # Kubernetes manifests: namespace, deployment, service, ingress
├── screenshots/
│ ├── pods-running.png
│ ├── ingress-alb.png
│ └── game-ui.png
├── README.md # Project documentation
└── .gitignore # Optional git ignore


---

## Technologies Used

- **AWS EKS** – Managed Kubernetes cluster  
- **Kubernetes** – Deployment, Service, Ingress  
- **ALB Ingress Controller** – For external access to the app  
- **Docker** – Containerized 2048 game image  
- **Git & GitHub** – Version control and project showcase  

---

## Setup and Deployment Steps

### 1. Create EKS Cluster

```bash
eksctl create cluster -f eks/cluster.yaml


Creates an EKS cluster with default VPC, node group, and IAM roles

2. Deploy 2048 Game on Kubernetes
kubectl apply -f k8s/2048-app.yaml


Creates:

Namespace: game-2048

Deployment: 5 replicas of the 2048 game

Service: NodePort for internal communication

Ingress: ALB for external access

3. Verify Deployment
kubectl get pods -n game-2048
kubectl get svc -n game-2048
kubectl get ingress -n game-2048


Use screenshots in screenshots/ to verify pods running, service status, and ALB ingress

Accessing the Game

After deployment, use the ALB Ingress DNS from:

kubectl get ingress -n game-2048


Open it in a browser to play the 2048 game
