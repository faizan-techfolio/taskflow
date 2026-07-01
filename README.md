# TaskFlow — DevOps playground

A small but real task-management app (Node/Express API + PostgreSQL + static
frontend) that you'll containerize, pipeline, orchestrate, provision, and
monitor over the course of the 30-day plan. Every folder maps to a week:

- `backend/`, `frontend/` — the app itself (Week 1)
- `docker-compose.yml`, `backend/Dockerfile`, `frontend/Dockerfile` — Week 1-2
- `.github/workflows/` — CI/CD pipelines (Week 2)
- `k8s/` — Kubernetes manifests (Week 3)
- `terraform/` — AWS infrastructure as code (Week 4)
- `monitoring/` — Prometheus + Grafana stack (Week 4)

## Quick start (local, Week 1-2)

```bash
docker compose up --build
# API:      http://localhost:3000/tasks
# Frontend: http://localhost:8080
```

## Run tests

```bash
cd backend
npm install
npm test
```

## Local Kubernetes (Week 3)

Requires Minikube and kubectl.

```bash
minikube start
eval $(minikube docker-env)
docker build -t taskflow-backend:local ./backend
kubectl apply -f k8s/
kubectl get pods -w
```

## AWS provisioning (Week 4)

Requires Terraform and an AWS account.

```bash
cd terraform
cp terraform.tfvars.example terraform.tfvars   # fill in your values
terraform init
terraform plan
terraform apply
```

## Monitoring (Week 4)

```bash
cd monitoring
docker compose up
# Prometheus: http://localhost:9090
# Grafana:    http://localhost:3001 (admin/admin)
```

See the full 30-day plan for the day-by-day breakdown of what to build, break,
and fix in this repo.
