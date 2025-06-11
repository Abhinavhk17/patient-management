# 🏥 Patient Management Platform  
🚀 Streamlining hospital workflows • 🔐 Secure access to critical data • ⚡ Powered by real-time updates

---

## ✨ Overview  
Welcome to the **Patient Management Platform** — a modern, microservices-based solution designed to simplify hospital operations and enhance healthcare data accessibility.

Built for scalability and security, this platform integrates advanced technologies to deliver seamless performance across healthcare modules.

---

## 🔑 Core Features

- 🔐 **OAuth2 + JWT Authentication**  
  Secure user access and role-based authorization

- 🌐 **RESTful APIs for Patient Data**  
  Designed for handling high-volume medical records efficiently

- 📡 **Real-Time Communication via Kafka**  
  Keeps all services in sync with live patient data streams

- 🐳 **Dockerized Microservices**  
  Easy to scale, deploy, and manage independently

- ☁️ **Cloud-Native Infrastructure (AWS Localstack)**  
  Emulates real AWS services for local testing and CI/CD readiness

---

## 📦 Environment Configuration

### 🌡️ Patient Service

<details>
<summary><strong>🔧 Environment Variables</strong></summary>

```env
JAVA_TOOL_OPTIONS=-agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=*:5005
SPRING_DATASOURCE_URL=jdbc:postgresql://patient-service-db:5432/db
SPRING_DATASOURCE_USERNAME=admin_user
SPRING_DATASOURCE_PASSWORD=password
SPRING_JPA_HIBERNATE_DDL_AUTO=update
SPRING_KAFKA_BOOTSTRAP_SERVERS=kafka:9092
SPRING_SQL_INIT_MODE=always
```
</details>

### 🧾 Billing Service Integration

<details>
<summary><strong>🔧 Environment Variables</strong></summary>

```env
BILLING_SERVICE_ADDRESS=billing-service
BILLING_SERVICE_GRPC_PORT=9005
```
</details>

### 📨 Kafka Container (Local Dev Setup)

<details>
<summary><strong>🔧 Environment Variables</strong></summary>

```env
KAFKA_CFG_ADVERTISED_LISTENERS=PLAINTEXT://kafka:9092,EXTERNAL://localhost:9094
KAFKA_CFG_CONTROLLER_LISTENER_NAMES=CONTROLLER
KAFKA_CFG_CONTROLLER_QUORUM_VOTERS=0@kafka:9093
KAFKA_CFG_LISTENER_SECURITY_PROTOCOL_MAP=CONTROLLER:PLAINTEXT,EXTERNAL:PLAINTEXT,PLAINTEXT:PLAINTEXT
KAFKA_CFG_LISTENERS=PLAINTEXT://:9092,CONTROLLER://:9093,EXTERNAL://:9094
KAFKA_CFG_NODE_ID=0
KAFKA_CFG_PROCESS_ROLES=controller,broker

```
</details>

### 🏭 Kafka Producer Setup (Patient Service)

<details>
<summary><strong>🔧 application.properties Configuration</strong></summary>

```properties
spring.kafka.consumer.key-deserializer=org.apache.kafka.common.serialization.StringDeserializer
spring.kafka.consumer.value-deserializer=org.apache.kafka.common.serialization.ByteArrayDeserializer
```
</details>

### 🔔 Notification Service

<details>
<summary><strong>🔧 Environment Variables</strong></summary>

```env
SPRING_KAFKA_BOOTSTRAP_SERVERS=kafka:9092

SPRING_DATASOURCE_URL=jdbc:postgresql://auth-service-db:5432/db
SPRING_DATASOURCE_USERNAME=admin_user
SPRING_DATASOURCE_PASSWORD=password
SPRING_JPA_HIBERNATE_DDL_AUTO=update
SPRING_SQL_INIT_MODE=always
```
</details>
