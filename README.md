# SimpleBankApp

# 💳 Banking Microservices Project

This is a backend microservices-based banking system built with Spring Boot and Docker. The system simulates a basic banking platform with functionalities like user management, account operations (credit, debit, transfer), transaction history, and inter-service communication via an API Gateway and service discovery with Eureka.

---


### ✅ Microservices:
1. **API Gateway**
   - Routes external client requests to microservices
   - Service discovery through Eureka
   - Will support JWT-based auth (future enhancement)

2. **User Service**
   - Create and manage user profiles
   - Spring Security configured (open endpoints currently)
   - Connected to PostgreSQL

3. **Account Service**
   - Create, credit, debit, rollback, and view account info
   - Transaction rollback logic included
   - Connected to PostgreSQL

4. **Transaction Service**
   - Records credit, debit, and transfer operations
   - Uses Feign client to communicate with Account Service
   - Logs transaction history

5. **Eureka Server**
   - Service registry and discovery
   - Enables load-balanced communication

---

## 🧪 Tech Stack

| Layer              | Technology                         |
|-------------------|-------------------------------------|
| Backend Framework | Spring Boot, Spring Web             |
| Service Registry  | Eureka (Netflix OSS)                |
| API Gateway       | Spring Cloud Gateway                |
| Database          | PostgreSQL                          |
| ORM               | Spring Data JPA, Hibernate          |
| Security          | Spring Security (JWT planned)       |
| Containerization  | Docker, Docker Compose              |
| Build Tool        | Maven                               |
| Communication     | REST, Feign Client                  |
| Dev Tools         | Lombok, Actuator                    |

---

## ⚙️ Getting Started
Checkout the Following Projects:

https://github.com/sidhantmourya/eureka-server

https://github.com/sidhantmourya/bank-gateway

https://github.com/sidhantmourya/user-service

https://github.com/sidhantmourya/transaction-service

https://github.com/sidhantmourya/account-service

### 🐳 Run with Docker Compose in the following order

```bash
docker network create banking-network
docker-compose -f eureka-server/deploy/docker-compose.yml up --build -d
docker-compose -f api-gateway/deploy/docker-compose.yml up --build -d
docker-compose -f user-service/deploy/docker-compose.yml up --build -d
docker-compose -f account-service/deploy/docker-compose.yml up --build -d
docker-compose -f transaction-service/deploy/docker-compose.yml up --build -d


