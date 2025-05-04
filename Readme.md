# MongoDB + Mongo Express Deployment on Kubernetes

This project demonstrates how to deploy **MongoDB** and **Mongo Express** using Kubernetes. It uses Kubernetes `Deployment`, `Service`, `Secret`, and `ConfigMap` resources to manage both services effectively.

---

## 🧾 Prerequisites

- Kubernetes cluster (Minikube, Docker Desktop, GKE, etc.)
- `kubectl` installed and configured
- Basic knowledge of Kubernetes concepts

---

## 📁 Folder Structure

├── mongo-deployment.yaml
├── mongo-express-deployment.yaml
├── mongo-secret.yaml
├── mongo-configmap.yaml
└── README.md

---

## 🔐 1. Secret for MongoDB Credentials

Create a secret for MongoDB root username and password. This will store the credentials in a secure, encrypted form. Make sure to base64 encode the username and password.

---

## ⚙️ 2. ConfigMap for MongoDB Connection URL

Create a ConfigMap that holds the MongoDB connection URL. This will be used by Mongo Express to connect to MongoDB.

---

## 🐳 3. MongoDB Deployment & Service

Define a `Deployment` for MongoDB, specifying the MongoDB Docker image, and configure environment variables for the root username and password from the secret. Also, define a `Service` for MongoDB, specifying the port and type (`ClusterIP` by default).

---

## 🌐 4. Mongo Express Deployment & Service

Define a `Deployment` for Mongo Express, using the `mongo-express` Docker image and configuring environment variables for connecting to MongoDB using the credentials and URL stored in the ConfigMap and Secret. Also, define a `Service` for Mongo Express, setting the port and `NodePort` for external access.

---

## 🧪 Deployment Commands

### 1️⃣ Apply Secret

To create the MongoDB credentials secret in Kubernetes:

```bash
kubectl apply -f mongo-secret.yaml
```

### 2️⃣ Apply ConfigMap

kubectl apply -f mongo-configmap.yaml

### 3️⃣ Deploy MongoDB

kubectl apply -f mongo-deployment.yaml

### 4️⃣ Deploy Mongo Express

kubectl apply -f mongo-express-deployment.yaml

### 📋 Verify Deployments

kubectl get deployments
kubectl get pods
kubectl get services

### 🌐 Accessing Mongo Express

## If you're using Minikube, you can open Mongo Express in your browser by running:

minikube service mongo-express-service

## Alternatively, you can access Mongo Express manually via:

http://<NodeIP>:30001
Replace <NodeIP> with your node’s IP address if you're not using Minikube.

### 🧼 Clean Up Resources

To remove the resources you've created:
kubectl delete -f mongo-secret.yaml
kubectl delete -f mongo-configmap.yaml
kubectl delete -f mongo-deployment.yaml
kubectl delete -f mongo-express-deployment.yaml

### 📦 Docker Images Used

MongoDB: mongo

Mongo Express: mongo-express
