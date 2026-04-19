# ☸️ SynergyChat – Kubernetes Deployment Demo

A Kubernetes-based deployment of a multi-service web application, demonstrating **scalable microservices architecture**, **Gateway API routing**, and **resource management**.

---

## 📌 About

This project showcases how to deploy and manage a distributed system on Kubernetes, including a frontend, backend API, and worker service, with autoscaling, persistent storage, and modern ingress routing.

---

## 🏗️ Architecture

```plaintext
Client
  |
  v
Gateway (HTTP)
  |
  |------------------------|
  |                        |
Web Frontend          Backend API
                          |
                          v
                    Persistent Storage
                          |
                          v
                     Crawler Service
```

---

## ✨ Components

* **Web (`synergychat-web`)**

  * 3 replicas + HPA (1–4)
  * ConfigMap-based config
  * Exposed via HTTPRoute

* **API (`synergychat-api`)**

  * Core backend service
  * PersistentVolumeClaim for data
  * Environment-driven config

* **Crawler (`synergychat-crawler`)**

  * Parallel worker service (3 replicas)
  * Uses `emptyDir` for caching

* **Testing Pods**

  * CPU & RAM stress testing deployments

---

## ⚙️ Key Features

* ☸️ Kubernetes-native deployments (Deployments, Services)
* 🌐 Gateway API (`Gateway`, `HTTPRoute`) for routing
* 📈 Horizontal Pod Autoscaling (HPA)
* 💾 Persistent storage using PVC
* 🔧 ConfigMaps for environment configuration
* 🧩 Modular microservices architecture

---

## 🚀 Deployment

Apply all manifests:

```bash
kubectl apply -f .
```

Ensure:

* Gateway API CRDs are installed
* Ingress/Gateway controller is running

---

## 📂 Structure

```
.
├── web-*.yaml        # Frontend deployment, HPA, routing
├── api-*.yaml        # Backend + PVC + routing
├── crawler-*.yaml    # Worker service
├── test*.yaml        # Resource testing pods
├── app-gateway.yaml  # Gateway definition
```

---

## 🧾 Summary

This project demonstrates real-world Kubernetes practices including **service isolation, autoscaling, persistent storage, and modern ingress routing**, making it a solid foundation for scalable cloud-native systems.

