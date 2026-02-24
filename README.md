## MEAN Stack DevOps Assignment

A fully containerized, production-ready MEAN stack application with automated CI/CD pipeline deployed on AWS EC2.

## What is This Project?
This project takes a full-stack MEAN (MongoDB, Express, Angular, Node.js) application and deploys it on a cloud server using modern DevOps practices — Docker containers, automated CI/CD, and Nginx as a reverse proxy.
Every time I push code to GitHub, the pipeline automatically builds new Docker images, pushes them to Docker Hub, and redeploys the application on the server — with zero manual steps.

## Project Architecture

- Frontend (Angular) → Nginx → Backend (Node.js + Express) → MongoDB  
- CI/CD → GitHub Actions → Docker Hub → EC2 Deployment

## Tech Stack

- **Frontend:** Angular 15
- **Backend:** Node.js + Express
- **Database:** MongoDB
- **Containerization:** Docker
- **Orchestration:** Docker Compose
- **CI/CD:** GitHub Actions
- **Reverse Proxy:** Nginx
- **Cloud VM:** Ubuntu (AWS EC2)

- ##  Docker Implementation

### Backend
- Custom Dockerfile
- Uses Node 18 Alpine image
- Exposes port 5000

### Frontend
- Multi-stage Docker build
- Angular production build
- Served using Nginx on port 80

### MongoDB
- Official MongoDB image
- Persistent volume enabled

---

##  Docker Compose Setup

All services are defined in `docker-compose.yml`:

- Backend container
- Frontend container
- MongoDB container
- Nginx reverse proxy
- Custom bridge network
- Persistent volumes

- To start the application manually: docker-compose up -d

## CI/CD Pipeline (GitHub Actions)

- The CI/CD workflow performs the following steps automatically on every push to main:

- Logs into Docker Hub

- Builds backend Docker image

- Builds frontend Docker image

- Pushes both images to Docker Hub

- SSH into Ubuntu VM

- Pull latest images

- Restart containers using Docker Compose

Workflow file:

.github/workflows/deploy.yml

## GitHub Secrets Used

- The following repository secrets are configured:

- DOCKER_USERNAME

- DOCKER_PASSWORD

- VM_HOST

- VM_USER

- VM_SSH_KEY



## Deployment Details

- Ubuntu VM hosted on AWS EC2

- Docker and Docker Compose installed

- Application accessible via:

- http://<EC2_PUBLIC_IP>

All traffic routed through Nginx on port 80.
