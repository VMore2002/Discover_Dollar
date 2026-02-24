# Discover Dollar – MEAN Stack Deployment (DevOps Assignment)

## Project Overview

This project demonstrates containerization and deployment of a full-stack MEAN application using Docker and Docker Compose on an Ubuntu cloud instance (AWS EC2).

The application includes:

- Angular frontend
- Node.js + Express backend
- MongoDB database

The objective was to containerize the application, deploy it in the cloud, configure Nginx as a reverse proxy, and automate image builds using GitHub Actions CI/CD.

---

## Tech Stack

### Application
- Angular 15
- Node.js
- Express.js
- MongoDB

### DevOps & Deployment
- Docker
- Docker Compose
- Nginx (Reverse Proxy)
- AWS EC2 (Ubuntu)
- GitHub Actions (CI/CD)
- Docker Hub

---

## Project Structure


Discover_Dollar/
│
├── frontend/
│ ├── Dockerfile
│ ├── nginx.conf
│ └── Angular source code
│
├── backend/
│ ├── Dockerfile
│ └── Express API code
│
├── docker-compose.yml
└── .github/workflows/ci-cd.yml


---

## Architecture


User Browser
↓
Nginx (Frontend Container - Port 80)
↓
Node.js + Express Backend (Port 8080)
↓
MongoDB Container


---

## Docker Deployment

### Build and start services

```bash
docker-compose up --build -d
Verify running containers
docker ps

Expected containers:

frontend

backend

mongo

Application Access

After deployment:


Example:

http://98.84.49.204
Nginx Reverse Proxy

Nginx serves the Angular build and forwards API requests to backend.

Routing configuration:

/api  → backend:8080

This allows the complete application to run on port 80.

MongoDB Setup

MongoDB runs as a container using the official image.

Connection string used by backend:

mongodb://mongo:27017/mean
CI/CD Pipeline (GitHub Actions)

Workflow file:

.github/workflows/ci-cd.yml
Pipeline flow

Trigger on push

Build frontend Docker image

Build backend Docker image

Push images to Docker Hub

Docker Hub Images

vipulmore/frontend

vipulmore/backend

Cloud Environment

Cloud Provider: AWS EC2

OS: Ubuntu 24.04

Instance Type: t3.small

Open Ports:

80 (HTTP)

22 (SSH)
