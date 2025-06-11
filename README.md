# 🏥 Patient Service – Microservices Configuration Guide

Welcome to the **Patient Service**! This document provides all the necessary environment variables and configuration details needed to run the **Patient**, **Notification**, and **Kafka** services seamlessly in your local or containerized environment.

---

## 📦 Environment Configuration

### 🌡️ Patient Service

<details>
<summary><strong>🔧 Core Environment Variables</strong></summary>

```env
JAVA_TOOL_OPTIONS=-agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=*:5005
SPRING_DATASOURCE_URL=jdbc:postgresql://patient-service-db:5432/db
SPRING_DATASOURCE_USERNAME=admin_user
SPRING_DATASOURCE_PASSWORD=password
SPRING_JPA_HIBERNATE_DDL_AUTO=update
SPRING_KAFKA_BOOTSTRAP_SERVERS=kafka:9092
SPRING_SQL_INIT_MODE=always
