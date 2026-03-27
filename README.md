# Micro-Service Voting App on Kubernetes

A containerized **microservices-based voting application** deployed on **Kubernetes** using **Deployments** and **Services**.

---

## Overview

This project demonstrates how a microservices application can be deployed and managed in Kubernetes.

The application consists of:

- **Vote App** – Frontend for casting votes  
- **Redis** – Message broker for temporary vote storage  
- **Worker** – Backend service that processes votes  
- **PostgreSQL** – Database for storing processed results  
- **Result App** – Frontend for displaying vote results  

---

## Architecture

```text
User --> Vote App --> Redis --> Worker --> PostgreSQL --> Result App --> User
```

All resources are deployed inside the **vote** namespace for isolation and better management.

---

## Tech Stack

| Component | Technology |
|-----------|------------|
| Vote App | Python |
| Message Broker | Redis |
| Worker Service | .NET |
| Database | PostgreSQL |
| Result App | Node.js |
| Containerization | Docker |
| Orchestration | Kubernetes |

---

## Docker Images Used

| Component | Image |
|-----------|-------|
| Vote App | `dockersamples/examplevotingapp_vote` |
| Redis | `redis` |
| Worker | `dockersamples/examplevotingapp_worker` |
| PostgreSQL | `postgres` |
| Result App | `dockersamples/examplevotingapp_result` |

---

## Kubernetes Resources

This project uses the following Kubernetes objects:

- **Namespace**
- **Deployments**
- **Services**
- **Persistent Volume / EmptyDir** (based on configuration)
- **Configurable environment variables**

---

## Project Structure

```text
micro-service-voting-app/
├── namespace.yaml
├── vote-deployment.yaml
├── vote-service.yaml
├── redis-deployment.yaml
├── redis-service.yaml
├── worker-deployment.yaml
├── postgres-deployment.yaml
├── postgres-service.yaml
├── result-deployment.yaml
├── result-service.yaml
└── README.md
```

---

## Deployment Steps

### 1. Create Namespace

```bash
kubectl apply -f namespace.yaml
```

### 2. Deploy Redis

```bash
kubectl apply -f redis-deployment.yaml
kubectl apply -f redis-service.yaml
```

### 3. Deploy PostgreSQL

```bash
kubectl apply -f postgres-deployment.yaml
kubectl apply -f postgres-service.yaml
```

### 4. Deploy Vote App

```bash
kubectl apply -f vote-deployment.yaml
kubectl apply -f vote-service.yaml
```

### 5. Deploy Worker

```bash
kubectl apply -f worker-deployment.yaml
```

### 6. Deploy Result App

```bash
kubectl apply -f result-deployment.yaml
kubectl apply -f result-service.yaml
```

---

## Verify Resources

```bash
kubectl get all -n vote
```

---

## Access the Application

If **Vote App** and **Result App** are exposed using **NodePort**, access them with:

```bash
minikube service <service-name> -n vote
```

Or manually:

```bash
http://<NodeIP>:<NodePort>
```

---

## Learning Outcomes

Through this project, I learned:

- Basic Kubernetes architecture
- Working with Pods, Deployments, and Services
- Namespace-based resource isolation
- Communication between microservices
- Running multi-container applications in Kubernetes
- Real-world application deployment workflow

---

## Use Case

This project is useful for beginners who want to understand:

- How microservices communicate inside Kubernetes
- How frontend, backend, cache, and database services work together
- How Kubernetes manages deployment and service exposure

---

## Notes

- This project is mainly for **learning and practice**.
- The Docker images used are from **KodeKloud / DockerSamples** for Kubernetes hands-on learning.
- The deployment focuses on understanding Kubernetes concepts rather than building a custom production application.

---

## Author

**Prathap G**  
DevOps Learner | CSE Student
