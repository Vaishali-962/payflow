# PayFlow

A payment gateway backend built with Java Spring Boot microservices.
This is a personal project to learn how real fintech systems work —
things like idempotency, transaction states, fraud detection, and 
event-driven architecture using Kafka.

## Why I built this

Most tutorials show you one Spring Boot app with a single database.
Real systems don't work like that. This project is my attempt to 
build something closer to what actually runs in production.

## What it does

- Users can register, login, and get a JWT token
- Authenticated users can initiate payments
- Payments go through fraud checks before processing
- Every payment creates a transaction record with status tracking
- Notifications are sent async via Kafka (email/SMS simulation)
- Full audit log of every event in the system
- Angular frontend for checkout, payment initiation,and transaction history dashboard

## Services

| Service | Port | What it does |
|---------|------|--------------|
| eureka-server | 8761 | Service registry |
| api-gateway | 8080 | Single entry point, JWT validation |
| auth-service | 8081 | Register, login, JWT |
| payment-service | 8082 | Initiate and process payments |
| transaction-service | 8083 | Ledger, payment history |
| fraud-detection-service | 8084 | Risk scoring |
| notification-service | 8085 | Email/SMS events |
| angular-frontend | 4200 | Checkout, dashboard, transaction history |

## Tech Stack

- Java 17, Spring Boot 3.2
- Spring Cloud (Eureka, Gateway)
- Spring Security + JWT
- Kafka (async events)
- Redis (idempotency, caching)
- PostgreSQL (transactional data)
- MongoDB (audit logs)
- Flyway (DB migrations)
- MapStruct, Lombok
- Docker, Jenkins, AWS EC2
- - Angular 17, TypeScript
- Angular Material (UI components)
- RxJS (async handling)
- HttpClient + JWT interceptor

## How to run locally

> Make sure PostgreSQL, Redis, and Kafka are running before starting services.

```bash
# Start Eureka first
cd eureka-server && mvn spring-boot:run

# Then Gateway
cd api-gateway && mvn spring-boot:run

# Then any service
cd auth-service && mvn spring-boot:run
```

## Project status

Currently in active development. Building sprint by sprint.

- [ ] Monorepo setup
- [ ] Eureka Server
- [ ] API Gateway
- [ ] Auth Service
- [ ] Payment Processor
- [ ] Transaction Service
- [ ] Fraud Detection
- [ ] Notification Service
- [ ] Angular Frontend
  - [ ] Login / Register page
  - [ ] Checkout / Payment page
  - [ ] Transaction history dashboard
  - [ ] Payment status tracking
- [ ] Docker + CI/CD
