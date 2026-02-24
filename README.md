## MEAN Stack DevOps Assignment

A fully containerized, production-ready MEAN stack application with automated CI/CD pipeline deployed on AWS EC2.


## What is This Project?
This project takes a full-stack MEAN (MongoDB, Express, Angular, Node.js) application and deploys it on a cloud server using modern DevOps practices — Docker containers, automated CI/CD, and Nginx as a reverse proxy.
Every time I push code to GitHub, the pipeline automatically builds new Docker images, pushes them to Docker Hub, and redeploys the application on the server — with zero manual steps.

## Project Architecture

- Frontend (Angular) → Nginx → Backend (Node.js + Express) → MongoDB  
 CI/CD → GitHub Actions → Docker Hub → EC2 Deployment

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

##  Docker Compose Setup

All services are defined in `docker-compose.yml`:

- Backend container
- Frontend container
- MongoDB container
- Nginx reverse proxy
- Custom bridge network
- Persistent volumes

- To start the application manually: docker-compose up -d

##  Docker Containers Running on EC2
   
<img width="1920" height="1080" alt="Screenshot 2026-02-24 161152" src="https://github.com/user-attachments/assets/60461810-ad61-4aa0-bd7d-0e07cc902289" />



## CI/CD Pipeline (GitHub Actions)

- The CI/CD workflow performs the following steps automatically on every push to main:

  ##  GitHub Actions - Successful Pipeline
  
<img width="1920" height="1080" alt="Screenshot 2026-02-24 160223" src="https://github.com/user-attachments/assets/a723d91e-f999-40b1-8d95-8ca5e53b8cd1" />



- Logs into Docker Hub

- Builds backend Docker image

- Builds frontend Docker image
  
- Pushes both images to Docker Hub

  ##  Build and Push Docker Images (Logs)

  <img width="1920" height="1080" alt="Screenshot 2026-02-24 160646" src="https://github.com/user-attachments/assets/9bde03ca-dbfe-49fd-8858-e3b104a5006b" />

  

- SSH into Ubuntu VM

- Pull latest images

- Restart containers using Docker Compose

- Workflow file:

.github/workflows/deploy.yml

##  Deploy to Production VM


<img width="1920" height="1080" alt="Screenshot 2026-02-24 160709" src="https://github.com/user-attachments/assets/7d8547a9-8094-4cfc-a2f4-7fe692d89a5e" />



## GitHub Secrets Used

- The following repository secrets are configured:

- DOCKER_USERNAME

- DOCKER_PASSWORD

- VM_HOST

- VM_USER

- VM_SSH_KEY

##  GitHub Secrets Configuration

<img width="1920" height="1080" alt="Screenshot 2026-02-24 161301" src="https://github.com/user-attachments/assets/171089a3-c904-4394-8ddc-a272b8d823d1" />



## Deployment Details

##  AWS EC2 Instance Running

<img width="1920" height="1080" alt="Screenshot 2026-02-24 161433" src="https://github.com/user-attachments/assets/b280623a-8fc8-45b8-9316-9c663c82bf85" />



- Ubuntu VM hosted on AWS EC2

- Docker and Docker Compose installed

- Application accessible via:

- http://<EC2_PUBLIC_IP>

##  Live Application

<img width="1920" height="1080" alt="Screenshot 2026-02-24 161337" src="https://github.com/user-attachments/assets/3d064ccd-83d2-461c-8ef7-b4708d8e098f" />



<img width="1920" height="1080" alt="Screenshot 2026-02-24 161345" src="https://github.com/user-attachments/assets/138e3ee7-f96e-467d-881d-4e67455720da" />



All traffic routed through Nginx on port 80.
