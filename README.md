أكيد 👍
إليك **README.md** بسيط وواضح يناسب الـ **Jenkins pipeline** والمشروع اللي بتشتغل عليه (Docker + Kubernetes + Jenkins):

---

# 🧩 DevOps Project — Dockerized Microservices CI/CD Pipeline

## 📘 Overview

This project demonstrates a complete **CI/CD pipeline** using **Jenkins**, **Docker**, and **Kubernetes**.
It builds, pushes, and deploys microservices automatically from source code to a Kubernetes cluster.

---

## 🚀 Pipeline Workflow

### 🏗️ 1. **Checkout**

* Jenkins clones the GitHub repository from:

  ```
  https://github.com/abdelrahmanonline4/dockerized-microservices.git
  ```

### 🐳 2. **Build Docker Images**

* Builds two Docker images:

  * **Application Image:** `3booda24/vprofileapp:latest`
  * **Database Image:** `3booda24/vprofiledb:latest`

### ☁️ 3. **Push to Docker Hub**

* Jenkins logs into Docker Hub using saved credentials (`credentialsId: dockerhub`)
* Pushes both images to Docker Hub repository

### ☸️ 4. **Deploy to Kubernetes**

* Jenkins applies the Kubernetes manifests to deploy the full application stack:

  ```
  kubectl apply -f app-secret.yml
  kubectl apply -f db-CIP.yml
  kubectl apply -f mc-CIP.yml
  kubectl apply -f mcdep.yml
  kubectl apply -f rmq-CIP-service.yml
  kubectl apply -f rmq-dep.yml
  kubectl apply -f vproapp-service.yml
  kubectl apply -f vproappdep.yml
  kubectl apply -f vprodbdep.yml
  ```

### ✅ 5. **Post Build**

* On success: Jenkins prints
  `✅ Build and deployment completed successfully.`
* On failure: Jenkins prints
  `❌ Pipeline failed. Check logs.`

---

## 🧰 Prerequisites

* Jenkins server with:

  * Docker plugin
  * Kubernetes CLI (`kubectl`)
* Docker Hub account
* Kubernetes cluster (local via Minikube or remote)
* Jenkins credentials named `dockerhub` containing:

  * **Username**
  * **Password or Token**

---

## 📂 Folder Structure

```
.
├── Docker-files/
│   ├── app/          # Dockerfile for application
│   └── db/           # Dockerfile for database
├── k8s/
│   ├── vproappdep.yml
│   ├── vprodbdep.yml
│   ├── vproapp-service.yml
│   ├── ...
├── Jenkinsfile
└── README.md
```

---

## 🧑‍💻 How to Run

1. Clone the repository

   ```bash
   git clone https://github.com/abdelrahmanonline4/dockerized-microservices.git
   ```
2. Set up Jenkins pipeline using the `Jenkinsfile`
3. Add Docker Hub credentials (`dockerhub`)
4. Run the pipeline
5. Verify deployment:

   ```bash
   kubectl get pods
   kubectl get svc
   ```

---

## 🏁 Result

After pipeline success:

* Docker images are pushed to Docker Hub
* Application is deployed on Kubernetes
* Accessible via the LoadBalancer service

---

هل تحب أضيف **صورة توضيحية (diagram)** للـ CI/CD flow (Jenkins → Docker → K8s) في الـ README؟
هتخلي شكل المشروع احترافي جدًا.
