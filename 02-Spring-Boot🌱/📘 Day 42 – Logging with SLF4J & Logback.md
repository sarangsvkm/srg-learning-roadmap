

> **Module:** Spring Boot Backend Engineering
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 41 – Global Exception Handling]]
>
> **Next:** [[📘 Day 43 – Spring Boot Caching]]

---

# 🌟 Daily Motivation

> "Good developers write code. Great developers write logs."

---

# 🎯 Learning Objectives

Today you will learn

- ✅ What is Logging?
- ✅ Why Logging?
- ✅ SLF4J
- ✅ Logback
- ✅ Logger Levels
- ✅ Log Configuration
- ✅ Best Practices
- ✅ Production Logging

---

# 📖 What is Logging?

Logging is the process of recording important events that occur while an application is running.

Logs help developers monitor, debug, and troubleshoot applications.

---

# 🇮🇳 Malayalam Explanation

Application Run ചെയ്യുമ്പോൾ

↓

Information Save ചെയ്യും

↓

Console

↓

Log File

↓

Developer Error കണ്ടെത്തും

↓

Problem Fix ചെയ്യും

---

# 🤔 Why Logging?

Without Logging

```
Application Error

↓

No Information

↓

Hard to Debug
```

Problems

- Difficult Debugging

- Unknown Errors

- No Production Monitoring

---

With Logging

```
Application

↓

Generate Logs

↓

Console

↓

Log File

↓

Developer
```

Advantages

✔ Easy Debugging

✔ Error Tracking

✔ Production Monitoring

✔ Performance Analysis

---

# 🏢 Real Company Example

Employee Login

↓

User Login

↓

Authentication Success

↓

INFO Log

↓

Dashboard

---

Database Failure

↓

ERROR Log

↓

Developer Investigation

---

# 📖 What is SLF4J?

SLF4J (Simple Logging Facade for Java) is a logging abstraction.

It provides a common API for different logging frameworks.

Spring Boot uses SLF4J by default.

---

# 📖 What is Logback?

Logback is the default logging framework used by Spring Boot.

It works together with SLF4J to write logs.

---

# 🏗 Logging Architecture

```
Application

↓

SLF4J

↓

Logback

↓

Console / File

↓

Developer
```

---

# 📖 Create Logger

```java
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

public class EmployeeService {

    private static final Logger logger =
            LoggerFactory.getLogger(EmployeeService.class);

}
```

---

# 📖 INFO Log

```java
logger.info("Employee created successfully.");
```

---

# 📖 DEBUG Log

```java
logger.debug("Employee ID : {}", employee.getId());
```

---

# 📖 WARN Log

```java
logger.warn("Employee salary is below minimum.");
```

---

# 📖 ERROR Log

```java
logger.error("Database connection failed.");
```

---

# 📖 Log Levels

| Level | Purpose |
|--------|---------|
| TRACE | Detailed Information |
| DEBUG | Debugging |
| INFO | General Information |
| WARN | Warning Messages |
| ERROR | Errors |

---

# 📖 application.yml

```yaml
logging:
  level:
    root: INFO
    com.company.project: DEBUG
```

---

# 📖 Logback Configuration

Create

```
logback-spring.xml
```

Example

```xml
<configuration>

    <include resource="org/springframework/boot/logging/logback/base.xml"/>

</configuration>
```

---

# 📖 Logging Best Practices

✔ Log important business events.

✔ Log exceptions.

✔ Log user login/logout.

✔ Log API requests.

✔ Avoid logging passwords.

✔ Avoid logging sensitive information.

---

# 🏗 Logging Flow

```
Client

↓

REST API

↓

Service

↓

Logger

↓

Console

↓

Log File
```

---

# 📊 Log Levels Example

| Event | Level |
|--------|-------|
| Application Started | INFO |
| User Login | INFO |
| SQL Debug | DEBUG |
| Invalid Input | WARN |
| Database Failure | ERROR |

---

# 🎤 Interview Questions

## Q1

What is SLF4J?

**Answer**

SLF4J is a logging abstraction that provides a common API for logging frameworks.

---

## Q2

What is Logback?

**Answer**

Logback is Spring Boot's default logging framework.

---

## Q3

Which log level is used for application information?

**Answer**

INFO

---

## Q4

Which log level is used for debugging?

**Answer**

DEBUG

---

## Q5

Should passwords be logged?

**Answer**

No.

Sensitive information should never be written to logs.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| Logger | Log Generator |
| SLF4J | Logging API |
| Logback | Logging Framework |
| DEBUG | Debug Information |
| ERROR | Application Failure |

---

# 💡 Pro Tips

> [!TIP]

Use placeholders instead of string concatenation.

Example

```java
logger.info("Employee ID : {}", id);
```

---

> [!IMPORTANT]

Never log

- Passwords
- JWT Tokens
- Credit Card Numbers
- OTPs
- API Secrets

---

# 🗣 English Practice

Read aloud

Logging helps developers identify application issues.

Spring Boot uses SLF4J with Logback.

Sensitive information should never be logged.

---

# 🧩 Assignment

- [ ] Create Logger.
- [ ] Add INFO log.
- [ ] Add DEBUG log.
- [ ] Add WARN log.
- [ ] Add ERROR log.
- [ ] Configure logging level.
- [ ] Create logback-spring.xml.

---

# 🚀 GitHub Task

```text
feat: implement application logging using SLF4J and Logback
```

---

# 📌 Summary

✔ Logging records application events.

✔ SLF4J is the logging API.

✔ Logback is the default Spring Boot logging framework.

✔ INFO, DEBUG, WARN, and ERROR are commonly used log levels.

✔ Never log sensitive information.

---

# 🔗 Related Notes

- [[📘 Day 41 – Global Exception Handling]]
- [[📘 Day 43 – Spring Boot Caching]]
- [[📘 Day 20 – Logging]]
- [[📘 HTTP Status Codes]]