DevOps Internship Assessment — Next.js CI/CD with Docker, GitHub Actions & Minikube

 Objective

Containerize and deploy a Next.js application using Docker, GitHub Actions, and Kubernetes (Minikube).

Project Overview

This project demonstrates a complete DevOps workflow:

      1. Containerizing a Next.js application with Docker

      2. Automating image build & push to GitHub Container Registry (GHCR) via GitHub Actions

      3. Deploying and exposing the app on a Kubernetes (Minikube) cluster

Tech Stack

Next.js

Docker

GitHub Actions

GitHub Container Registry (GHCR)

Kubernetes (Minikube)

Setup Instructions

1. Clone the repository
git clone https://github.com/pratikshya-das/nextjs-devops-app.git
cd nextjs-devops-app

2. Run locally (optional)
npm install
npm run dev


Visit: http://localhost:3000

Docker Setup

Build Docker image
docker build -t nextjs-devops-app:local .

Run container
docker run -p 3000:3000 nextjs-devops-app:local


Access app at: http://localhost:3000

GitHub Actions CI/CD

Every push to the main branch triggers:

Docker image build

Automatic push to GHCR
→ ghcr.io/pratikshya-das/nextjs-devops-app:latest

Workflow file:
.github/workflows/docker.yml

Kubernetes Deployment (Minikube)

Start Minikube
minikube start --driver=docker

Apply Kubernetes manifests
kubectl create namespace demo
kubectl apply -f k8s/ -n demo

Verify pods and services
kubectl get pods -n demo
kubectl get svc -n demo

Access application
minikube -n demo service nextjs-service --url

 App URL will open automatically in browser.

Folder Structure

nextjs-devops-app/
├── .github/workflows/docker.yml
├── k8s/
│   ├── deployment.yaml
│   ├── service.yaml
├── Dockerfile
├── .dockerignore
├── package.json
└── README.md

Final Checklist

 Containerized app with Docker

 CI/CD pipeline on GitHub Actions

 Image pushed to GHCR

 Kubernetes deployment on Minikube

 Working application accessible via NodePort