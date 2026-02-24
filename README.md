# 🚀 MEAN Stack DevOps Deployment

This project demonstrates full DevOps implementation of a MEAN (MongoDB, Express, Angular, Node.js) application including:

- Containerization using Docker
- CI/CD automation using Jenkins
- Docker Hub image management
- Cloud deployment on AWS EC2 (Ubuntu)
- Webhook-triggered automated deployments
- Nginx reverse proxy serving application on Port 80

---

# 🛠 Tech Stack

- MongoDB
- Express.js
- Angular 15
- Node.js
- Docker
- Docker Compose
- Jenkins (Declarative Pipeline)
- GitHub Webhooks
- AWS EC2 (Ubuntu 22.04)
- Nginx

---
# 📦 Project Architecture
        ┌─────────────┐
        │   GitHub    │
        └──────┬──────┘
               │ Webhook Trigger
               ▼
        ┌─────────────┐
        │   Jenkins   │
        │  (EC2:8080) │
        └──────┬──────┘
               │
     Build & Push Docker Images
               │
               ▼
        ┌─────────────┐
        │ Docker Hub  │
        └──────┬──────┘
               │
               ▼
        ┌─────────────┐
        │  EC2 Server │
        │ Docker Compose
        └──────┬──────┘
               │
    ┌──────────┼──────────┐
    ▼          ▼          ▼
MongoDB Backend Frontend
(Internal) (Internal) (Port 80 via Nginx)


---

# 🐳 Docker Setup

## Backend
- Base Image: Node 18
- Production dependencies installed
- Exposed internally on port 8080
- Connected to MongoDB via Docker network

## Frontend
- Multi-stage Docker build
- Angular production build
- Served using Nginx
- Exposed on Port 80

## Database
- Official MongoDB Docker image
- Internal Docker network communication

---

# ☁️ Cloud Deployment

- Ubuntu EC2 instance
- Docker & Docker Compose installed
- Jenkins running on port 8080
- Application accessible on port 80
- Containers managed using Docker Compose

---

# 🔁 CI/CD Pipeline

Implemented using **Jenkins Declarative Pipeline**.

Webhook triggers pipeline automatically on GitHub push.

## Pipeline Stages

1. Checkout Code
2. Build Backend Docker Image
3. Build Frontend Docker Image
4. Login to Docker Hub
5. Push Images
6. Deploy using Docker Compose

Pipeline automatically:
- Builds updated images
- Pushes to Docker Hub
- Pulls latest images on EC2
- Restarts containers

---

# 📸 Screenshots

### Jenkins Successful Pipeline Execution
![Jenkins](screenshots/jenkins-success.png)

### Docker Hub Images
![DockerHub](screenshots/dockerhub-images.png)

### EC2 Running Containers
![EC2](screenshots/ec2-containers.png)

### Application UI Running on Port 80
![App](screenshots/app-ui.png)

### GitHub Webhook Trigger Success
![Webhook](screenshots/webhook-success.png)

All screenshots are available in the `/screenshots` directory.

---

# ▶️ How to Run Locally

```bash
docker
http://localhostcompose up -d
http://localhost






