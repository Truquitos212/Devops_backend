# ⚙️ Innovatech: Backend Ventas y Despachos en Kubernetes (EKS)

Backend del sistema de **Ventas y Despachos** de Innovatech Chile: dos microservicios Spring Boot con MySQL, desplegados en **AWS EKS** con un pipeline de CI/CD en GitHub Actions.

Proyecto en equipo de la asignatura **Ingeniería DevOps (ISY1101)**, DuocUC. Frontend: [innovatech-devops-frontend](https://github.com/Truquitos212/innovatech-devops-frontend).

## Stack

- Java 17 + Spring Boot (microservicios `ventas` y `despachos`)
- MySQL
- Docker + Amazon ECR
- Kubernetes en Amazon EKS (Deployments, Services, Secrets, HPA)
- GitHub Actions

## Pipeline CI/CD

Con cada push, `.github/workflows/deploy-backend.yml`:

1. Se autentica en AWS y en ECR
2. Construye y sube las imágenes de **Ventas** y **Despachos** con un tag por commit
3. Configura `kubectl` contra el clúster EKS
4. Aplica MySQL (Secret, Deployment, Service)
5. Despliega los microservicios
6. Aplica el **Horizontal Pod Autoscaler**
7. Muestra el estado final del clúster

## Estructura

```
back-Ventas_SpringBoot/     microservicio de ventas
back-Despachos_SpringBoot/  microservicio de despachos
k8s/                        manifiestos de Kubernetes (deployments, services, secret, hpa)
docker-compose.yml          ejecución local
```

## Ejecución local

```bash
docker compose up
```

- Ventas: `http://localhost:8001`
- Despachos: `http://localhost:8002`
