# Scalable Online Store Microservices

A microservices-based online shopping application built with Spring Boot 3. It includes Product, Order, Inventory, and Notification services, with an API Gateway for request routing and Apache Kafka for asynchronous communication.

Based on [Programming Techie's Spring Boot 3 Microservices course](https://youtu.be/yn_stY3HCr8).

## Services Overview

- Product Service
- Order Service
- Inventory Service
- Notification Service
- API Gateway using Spring Cloud Gateway MVC
- Shop Frontend using Angular 18

## Tech Stack

- Spring Boot 3 / Java 21
- Angular 18
- MongoDB / MySQL
- Kafka
- Keycloak
- Testcontainers with WireMock
- Grafana Stack (Prometheus, Grafana, Loki, Tempo)
- Docker / Kubernetes (Kind)

## Prerequisites

- Java 21
- Maven 3.9+
- Docker
- Node.js 20+ (frontend)
- Kind + kubectl (Kubernetes)

## How to run the frontend

```shell
cd frontend
npm install
npm run start
```

## How to build the backend services

```shell
mvn clean package -DskipTests
```

To build Docker images locally (no registry push by default):

```shell
mvn spring-boot:build-image -DskipTests
```

## How to run with Docker Compose

```shell
docker compose up -d
```

## How to run on Kubernetes (Kind)

```shell
./k8s/kind/create-kind-cluster.sh
kubectl apply -f k8s/manifests/infrastructure/
kubectl apply -f k8s/manifests/applications/
```

### Port forwards

```shell
kubectl port-forward svc/gateway-service 9000:9000
kubectl port-forward svc/keycloak 8080:8080
kubectl port-forward svc/grafana 3000:3000
```
