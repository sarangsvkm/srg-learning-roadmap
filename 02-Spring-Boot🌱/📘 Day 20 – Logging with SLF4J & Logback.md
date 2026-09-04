

> **Module:** Spring Boot Backend Engineering
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 19 – Lombok]]
>
> **Next:** [[📘 Day 21 – Spring Profiles]]

---

# 🌟 Daily Motivation

> "Good developers write code. Great developers write logs."

---

# 🎯 Learning Objectives

Today you will learn

✅ What is Logging?

✅ Why Logging is Important?

✅ SLF4J

✅ Logback

✅ @Slf4j

✅ Log Levels

✅ Logging Best Practices

---

# 📖 What is Logging?

## Definition

Logging is the process of recording application events while the application is running.

Logs help developers understand what the application is doing.

---

# 🇮🇳 Malayalam Explanation

Application run ചെയ്യുമ്പോൾ

എന്ത് സംഭവിക്കുന്നു എന്ന് record ചെയ്യുന്നതാണ്

Logging.

Production-ൽ error വന്നാൽ

Logs നോക്കിയാണ് പ്രശ്നം കണ്ടെത്തുന്നത്.

---

# 🏢 Real Company Example

User Login

↓

Login API Called

↓

Database Connected

↓

Login Success

↓

Logs Generated

Example

```
INFO  User login successful
```

---

# 📖 Why Logging?

Logging helps to

✔ Debug Errors

✔ Monitor Applications

✔ Track User Requests

✔ Find Performance Issues

✔ Troubleshoot Production Problems

---

# 📦 SLF4J

SLF4J

=

Simple Logging Facade for Java

It provides a standard logging API.

---

# 📦 Logback

Logback is the default logging framework used by Spring Boot.

Spring Boot

↓

SLF4J

↓

Logback

---

# 📖 @Slf4j

Lombok annotation

```java
@Slf4j
@RestController
public class EmployeeController {

}
```

Automatically creates

```java
log
```

object.

---

# 💻 Example

```java
@Slf4j
@RestController
@RequestMapping("/employees")
public class EmployeeController {

    @GetMapping
    public String getEmployees(){

        log.info("Fetching all employees");

        return "Employee List";

    }

}
```

---

# 📖 Log Levels

TRACE

Very detailed logs.

---

DEBUG

Developer debugging information.

---

INFO

Normal application events.

---

WARN

Potential problem.

---

ERROR

Application error.

---

# 💻 Example

```java
log.trace("Trace Log");

log.debug("Debug Log");

log.info("Application Started");

log.warn("Employee not found");

log.error("Database Connection Failed");
```

---

# 📖 Configure Logging

application.properties

```properties
logging.level.root=INFO

logging.level.com.sarang=DEBUG
```

---

# 📖 Log Pattern

```properties
logging.pattern.console=%d %-5level %logger - %msg%n
```

---

# ❌ Don't Use

```java
System.out.println("Employee Saved");
```

---

# ✅ Use

```java
log.info("Employee Saved Successfully");
```

---

# 🏗 Request Flow

Client

↓

Controller

↓

INFO Log

↓

Service

↓

Repository

↓

Database

↓

Response

---

# 🎤 Interview Questions

## Q1

What is Logging?

Answer

Logging records application events during execution.

---

## Q2

What is SLF4J?

Answer

SLF4J is a logging API for Java.

---

## Q3

What is Logback?

Answer

Logback is the default logging framework in Spring Boot.

---

## Q4

Which annotation creates a Logger automatically?

Answer

@Slf4j

---

## Q5

Name the log levels.

Answer

TRACE

DEBUG

INFO

WARN

ERROR

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| Logging | Recording Events |
| Logger | Log Writer |
| SLF4J | Logging API |
| Logback | Logging Framework |
| INFO | General Information |

---

# 💡 Pro Tips

> [!TIP]

Use `INFO` for important application events.

Use `DEBUG` only during development.

---

> [!IMPORTANT]

Never log passwords, OTPs, API keys, or other sensitive user information.

---

# 🗣 English Practice

Read aloud

Logging helps monitor applications.

SLF4J provides the logging API.

Logback is the default logging framework.

INFO logs application events.

ERROR logs application failures.

---

# 🧩 Assignment

- [ ] Add @Slf4j to EmployeeController.
- [ ] Replace System.out.println() with log.info().
- [ ] Configure logging.level.root in application.properties.
- [ ] Test log messages in IntelliJ console.

---

# 🚀 GitHub Task

Commit Message

```
feat: add SLF4J logging to Employee project
```

---

# ⭐ Today's Challenge

Without looking at notes

Explain

1. What is Logging?

2. What is SLF4J?

3. What is Logback?

4. Name all Log Levels.

5. Why should we avoid System.out.println() in production?

---

# 📌 Summary

✔ Logging records application events.

✔ SLF4J is the logging API.

✔ Logback is Spring Boot's default logging framework.

✔ @Slf4j creates a Logger automatically.

✔ Use INFO, DEBUG, WARN, and ERROR appropriately.

✔ Never log sensitive information.