# Event Ticketing - Infrastructure & DevOps

## 📌 Overview
This repository contains the Infrastructure as Code (Terraform), Kubernetes manifests, Helm Charts, Local Docker Compose environment configurations, and Monitoring Stack (Prometheus, Grafana, Loki) for the Event Ticketing System.

## 🛠️ Technologies
- **IaC:** Terraform
- **Cloud Provider:** AWS (EKS, RDS, MSK, ElastiCache, ECR)
- **Container Orchestration:** Kubernetes (Local Kind/Minikube & EKS)
- **Observability:** Prometheus, Grafana, Loki
- **CI/CD:** GitHub Actions

---

## 🚀 Local Infrastructure Setup (Phase 2 - Level 1)

All microservices rely on shared infrastructure components (PostgreSQL databases, Redis cache, Apache Kafka) during local development. These are orchestrated using Docker Compose.

### Prerequisites
- [Docker Desktop](https://www.docker.com/products/docker-desktop/) installed and running
- Git

Verify Docker installation:
```bash
docker --version
docker compose version

