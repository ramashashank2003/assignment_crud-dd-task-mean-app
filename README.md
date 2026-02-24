# MEAN Stack DevOps Deployment

This project demonstrates containerization, CI/CD automation, and cloud deployment of a full-stack MEAN application using Docker, Jenkins, and AWS EC2.

---

## 🚀 Tech Stack

- MongoDB
- Express.js
- Angular 15
- Node.js
- Docker
- Docker Compose
- Jenkins
- GitHub Webhooks
- AWS EC2 (Ubuntu)

---

## 📦 Project Architecture

GitHub → Webhook → Jenkins → Docker Build → Docker Hub → EC2 → Docker Compose → Running Containers

---

## 🐳 Docker Setup

### Backend
- Node 18 base image
- Production dependencies installed
- Exposed internally on port 8080

### Frontend
- Multi-stage build
- Angular production build
- Served via Nginx (port 80)

### Database
- Official MongoDB Docker image
- Internal Docker network communication

---

## ☁️ Cloud Deployment

- Ubuntu EC2 instance
- Docker & Docker Compose installed
- Jenkins running on port 8080
- Application accessible on port 80

---

## 🔁 CI/CD Pipeline

Implemented using Jenkins Declarative Pipeline.

### Pipeline Stages:
1. Checkout Code
2. Build Backend Docker Image
3. Build Frontend Docker Image
4. Login to Docker Hub
5. Push Images
6. Deploy using Docker Compose

Webhook triggers pipeline automatically on GitHub push.

---

## 📸 Screenshots

See `/screenshots` folder for:

- Jenkins successful pipeline execution
- Docker Hub image repository
- EC2 running containers
- Application UI running on port 80
- GitHub webhook delivery success

---

## ▶️ How to Run Locally

```bash
docker compose up -d
Navigate to `http://localhost:8081/`
# assignment_crud-dd-task-mean-app
