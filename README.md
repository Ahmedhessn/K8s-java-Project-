# Kubernetes Project

This project contains Kubernetes manifests for deploying a multi-service application.

## Services
1. **db01** - MySQL Database (with PVC for persistent data)
2. **mc01** - Memcached
3. **rmq01** - RabbitMQ (with management console)
4. **contapp** - Tomcat Application (with PVC for webapps)
5. **contweb** - Web server (Nginx or custom)

## How to Deploy
```sh
kubectl apply -f db01-deploy.yaml
kubectl apply -f mc01-deploy.yaml
kubectl apply -f rmq01-deploy.yaml
kubectl apply -f contapp-deploy.yaml
kubectl apply -f contweb-deploy.yaml
```
# K8s-java-Project-
