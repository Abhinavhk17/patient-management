# 🏥 Patient Service – Microservices Configuration Guide

Welcome to the **Patient Service**! This document provides all the necessary environment variables and configuration details needed to run the **Patient**, **Notification**, and **Kafka** services seamlessly in your local or containerized environment.

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

🔔 Notification Service
<details> <summary><strong>🔧 Environment Variables</strong></summary>
env
Copy
Edit
SPRING_KAFKA_BOOTSTRAP_SERVERS=kafka:9092

SPRING_DATASOURCE_URL=jdbc:postgresql://auth-service-db:5432/db
SPRING_DATASOURCE_USERNAME=admin_user
SPRING_DATASOURCE_PASSWORD=password
SPRING_JPA_HIBERNATE_DDL_AUTO=update
SPRING_SQL_INIT_MODE=always
</details>
