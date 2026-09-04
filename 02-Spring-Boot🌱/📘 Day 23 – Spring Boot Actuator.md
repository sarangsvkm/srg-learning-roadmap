

> **Module:** Spring Boot Backend Engineering
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 22 – @ConfigurationProperties]]
>
> **Next:** [[📘 Day 24 – Spring Boot DevTools]]

---

# 🌟 Daily Motivation

> "A production application is not just built—it is monitored."

---

# 🎯 Learning Objectives

Today you will learn

✅ What is Spring Boot Actuator?

✅ Why use Actuator?

✅ Health Endpoint

✅ Info Endpoint

✅ Metrics Endpoint

✅ Custom Information

✅ Production Monitoring

---

# 📖 What is Spring Boot Actuator?

## Definition

Spring Boot Actuator is a module that provides production-ready features such as monitoring, health checks, metrics, and application information.

---

# 🇮🇳 Malayalam Explanation

Application run ചെയ്തതിന് ശേഷം

Application healthy ആണോ?

Memory എത്ര ഉപയോഗിക്കുന്നു?

CPU Usage?

Application Running ആണോ?

ഇവയെല്ലാം അറിയാൻ

Spring Boot Actuator ഉപയോഗിക്കുന്നു.

---

# 🏢 Real Company Example

Production Server

↓

Spring Boot Application

↓

Actuator

↓

Health

↓

Metrics

↓

Monitoring Dashboard

↓

DevOps Team

---

# 📦 Maven Dependency

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
```

---

# 📖 Default Endpoint

```
http://localhost:8080/actuator
```

---

# 📖 Health Endpoint

```
GET

/actuator/health
```

Response

```json
{
  "status":"UP"
}
```

Meaning

Application is running successfully.

---

# 📖 Info Endpoint

application.properties

```properties
info.app.name=Employee Management System

info.app.version=1.0.0

info.app.developer=Sarang
```

Access

```
GET

/actuator/info
```

Response

```json
{
    "app":{
        "name":"Employee Management System",
        "version":"1.0.0",
        "developer":"Sarang"
    }
}
```

---

# 📖 Metrics Endpoint

```
GET

/actuator/metrics
```

Shows

- JVM Memory
- CPU Usage
- HTTP Requests
- Database Connections

---

# 📖 Expose Endpoints

application.properties

```properties
management.endpoints.web.exposure.include=*
```

Expose all endpoints.

---

# 📖 Secure Endpoints

Production

Do NOT expose every endpoint publicly.

Instead

```properties
management.endpoints.web.exposure.include=health,info
```

---

# 🏗 Request Flow

Client

↓

Actuator Endpoint

↓

Spring Boot

↓

Monitoring Information

↓

JSON Response

---

# 📊 Common Actuator Endpoints

| Endpoint | Purpose |
|----------|---------|
| /actuator | List Endpoints |
| /health | Application Health |
| /info | Application Information |
| /metrics | Performance Metrics |
| /env | Environment Properties |
| /beans | Spring Beans |

---

# 🎤 Interview Questions

## Q1

What is Spring Boot Actuator?

Answer

It provides production-ready monitoring and management features.

---

## Q2

Which endpoint checks application health?

Answer

```
/actuator/health
```

---

## Q3

Which endpoint displays application information?

Answer

```
/actuator/info
```

---

## Q4

Why should Actuator endpoints be secured?

Answer

To prevent unauthorized users from accessing sensitive application information.

---

## Q5

How do you expose all Actuator endpoints?

Answer

```properties
management.endpoints.web.exposure.include=*
```

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| Actuator | Monitoring Module |
| Health | Application Status |
| Metrics | Performance Statistics |
| Endpoint | API URL |
| Monitoring | System Observation |

---

# 💡 Pro Tips

> [!TIP]

Use `/actuator/health` for Kubernetes and Docker health checks.

---

> [!IMPORTANT]

Never expose all Actuator endpoints in production unless they are protected by authentication.

---

# 🗣 English Practice

Read aloud

Spring Boot Actuator monitors applications.

Health endpoint shows application status.

Metrics endpoint shows application performance.

Production systems use Actuator for monitoring.

---

# 🧩 Assignment

- [ ] Add Spring Boot Actuator dependency.
- [ ] Expose actuator endpoints.
- [ ] Configure application info.
- [ ] Test `/actuator/health`.
- [ ] Test `/actuator/info`.
- [ ] Test `/actuator/metrics`.

---

# 🚀 GitHub Task

Commit Message

```
feat: integrate Spring Boot Actuator for monitoring
```

---

# ⭐ Today's Challenge

Without looking at notes

Explain

1. What is Spring Boot Actuator?

2. Why do we use Actuator?

3. What does `/actuator/health` do?

4. What does `/actuator/info` do?

5. Why shouldn't all endpoints be exposed in production?

---

# 📌 Summary

✔ Spring Boot Actuator provides production-ready monitoring.

✔ `/actuator/health` checks application health.

✔ `/actuator/info` shows application information.

✔ `/actuator/metrics` displays performance metrics.

✔ Secure Actuator endpoints in production.