# 🏋️‍♀️ Fullstack Fitness App - DevOps GitOps Multicloud
Ejemplos de código para una aplicación web de ejercicios físicos “fitness app”) que cubre Frontend, Backend, Docker, pipeline con Jenkins, despliegue en Kubernetes / OpenShift, servidor Nginx como reverse proxy / static server, y monitoreo con Prometheus + Grafana. Luego de ver esto, puedes ajustarlo al lenguaje/framework que prefieras.
## 📦 Estructura del Proyecto
fitness-app/
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   └── App.jsx
│   ├── public/
│   ├── package.json
│   └── Dockerfile
├── backend/
│   ├── src/
│   │   ├── controllers/
│   │   ├── routes/
│   │   ├── models/
│   │   └── app.js
│   ├── package.json
│   └── Dockerfile
├── nginx/
│   └── nginx.conf
├── k8s/
│   ├── frontend-deployment.yaml
│   ├── backend-deployment.yaml
│   ├── service-frontend.yaml
│   ├── service-backend.yaml
│   ├── ingress.yaml
│   └── configmap-nginx.yaml
├── jenkins/
│   └── Jenkinsfile
├── prometheus/
│   ├── prometheus.yml
│   └── serviceMonitor-backend.yaml  (si usas operator / kube-prometheus-stack)
├── grafana/
│   ├── dashboards/
│   └── datasources/
└── README.md

---

## 🖥️ Tecnologías Utilizadas

| Componente       | Tecnología         |
|------------------|--------------------|
| Frontend         | React + Nginx      |
| Backend          | Node.js (Express)  |
| CI/CD            | GitLab CI/CD       |
| GitOps           | ArgoCD + Helm      |
| Infraestructura  | Terraform          |
| Nube             | AWS / Azure / GCP  |
| Contenedores     | Docker             |
| Kubernetes       | EKS, AKS, GKE      |
| Observabilidad   | Prometheus + Grafana |
| Ingress          | NGINX Ingress Controller |

---

## 🚀 Flujo DevOps

1. **Push** al repositorio GitLab
2. **CI/CD** construye y publica imágenes en:
   - AWS ECR
   - Azure Container Registry (ACR)
   - Google Container Registry (GCR)
3. Actualiza archivos `values.yaml` del repositorio GitOps
4. ArgoCD sincroniza con el clúster Kubernetes (EKS/AKS/GKE)
5. Helm despliega el frontend y backend

---

## 🔁 GitLab CI/CD

El pipeline realiza:

- ✅ Instalación y tests de frontend y backend
- 🔧 Build de imágenes Docker
- ⬆️ Push a ECR / ACR / GCR
- 🔁 Actualización del repositorio GitOps
- 🎯 Desencadena despliegue automático en Kubernetes vía ArgoCD

---

## ☁️ Infraestructura como Código (Terraform)

Ubicación: `/infra/{aws,azure,gcp}`

Provisiona:

- Clústeres Kubernetes (EKS, AKS, GKE)
- Repositorios Docker
- Roles, redes, etc.

Variables definidas en `variables.tf`.

---

## 🎯 GitOps con ArgoCD

Manifiestos ubicados en:


