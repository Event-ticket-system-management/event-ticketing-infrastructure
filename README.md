Event Ticketing - Infrastructure & DevOps

📌 Overview
This repository contains the Infrastructure as Code (Terraform), Kubernetes manifests, Helm Charts, Local Docker Compose environment configurations, and Monitoring Stack (Prometheus, Grafana, Loki) for the Event Ticketing System.

🛠️ Technologies
IaC: Terraform
Cloud Provider: AWS (EKS, RDS, MSK, ElastiCache, ECR)
Container Orchestration: Kubernetes (Local Kind/Minikube & EKS)
Observability: Prometheus, Grafana, Loki
CI/CD: GitHub Actions

🚀 Local Infrastructure Setup (Phase 2 - Level 1)
All microservices rely on shared infrastructure components (PostgreSQL databases, Redis cache, Apache Kafka) and application containers during local development. These are orchestrated using modular Docker Compose setups connected via a shared network (`event-ticketing-network`).

Prerequisites
* Docker Desktop installed and running
* Git

Step 1: Start Local Environment

Option A: Run Infrastructure & Applications Separately (Recommended)
# 1. Start core infrastructure (PostgreSQL, Redis, Kafka)
docker compose -f docker-compose.infra.yml up -d

# 2. Start application microservices
docker compose -f docker-compose-app.yml up -d

Option B: Start Everything Together
docker compose -f docker-compose.infra.yml -f docker-compose-app.yml up -d

Step 2: Stop Environment & Clean Resources
# Stop all services and remove volumes/networks
docker compose -f docker-compose.infra.yml -f docker-compose-app.yml down -v --remove-orphans

---

🌐 Shared Networking & Service Discovery

* Infrastructure stack creates and exposes the custom bridge network: `event-ticketing-network`.
* Microservices stack connects to this network marked as `external: true`.
* Internal DNS allows microservices to communicate with databases using service names (e.g., `jdbc:postgresql://postgres:5432/user_db`).
