
> **Module:** Spring Boot Backend Engineering
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 07 – Spring IoC, Dependency Injection (DI) & Spring Beans 2]]
>
> **Next:** [[📘 Day 09 – Spring REST Controller]]0

---

# 🌟 Daily Motivation

> "Every request starts at the Controller."

---

# 🎯 Learning Objectives

Today you will learn

✅ What is Spring Controller?

✅ Why do we use Controller?

✅ MVC Architecture

✅ @Controller Annotation

✅ @RequestMapping

✅ Constructor Injection

✅ Request Flow

---

# 📖 What is Spring Controller?

## Definition

A Spring Controller is a class responsible for handling incoming HTTP requests and returning responses.

It acts as the entry point of a Spring MVC application.

---

# 🇮🇳 Malayalam Explanation

User

↓

Browser / Mobile App / Postman

↓

Request

↓

Controller

Controller request സ്വീകരിച്ച്

Service Layer-ലേക്ക് അയക്കും.

Service processing കഴിഞ്ഞാൽ

Response

തിരികെ Client-ന് നൽകും.

---

# 🏗 Spring MVC Architecture

```
Client

↓

Controller

↓

Service

↓

Repository

↓

Database
```

---

# 🏢 Real Company Example

Employee Management System

Employee List

↓

GET /employees

↓

EmployeeController

↓

EmployeeService

↓

EmployeeRepository

↓

PostgreSQL

↓

JSON Response

---

# 💻 Creating Controller

```java
package com.sarang.ems.controller;

import org.springframework.stereotype.Controller;

@Controller
public class EmployeeController {

}
```

---

# 📖 @Controller

Marks a class as a Spring MVC Controller.

Spring automatically creates a Bean.

---

# 📖 @RequestMapping

Maps HTTP requests to Controller.

Example

```java
@Controller
@RequestMapping("/employees")
public class EmployeeController {

}
```

All URLs starting with

```
/employees
```

come to this controller.

---

# 💻 Constructor Injection

```java
@Controller
@RequestMapping("/employees")
public class EmployeeController {

    private final EmployeeService service;

    public EmployeeController(EmployeeService service){

        this.service = service;

    }

}
```

Spring injects

EmployeeService

automatically.

---

# 📖 Responsibilities

Controller should

✔ Receive Request

✔ Call Service

✔ Return Response

✔ Validate URL Parameters

✔ Handle Request Mapping

---

# ❌ Controller Should NOT

❌ Access Database

❌ Write SQL

❌ Business Logic

---

# 🏗 Request Flow

```
Client

↓

Controller

↓

Service

↓

Repository

↓

Hibernate

↓

PostgreSQL

↓

Repository

↓

Service

↓

Controller

↓

Client
```

---

# 📖 Controller vs Service

| Controller | Service |
|------------|----------|
| Handles HTTP Requests | Business Logic |
| Returns Response | Validation |
| Calls Service | Calls Repository |

---

# 🎤 Interview Questions

## Q1

What is Controller?

Answer

Controller receives HTTP requests and returns responses.

---

## Q2

Why do we use @Controller?

Answer

To register a class as a Spring MVC Controller.

---

## Q3

Can Controller access Repository directly?

Answer

No.

Controller should communicate only with Service.

---

## Q4

Where should Business Logic be written?

Answer

Service Layer.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| Controller | Request Handler |
| Request | Client Call |
| Response | Server Reply |
| Endpoint | API URL |
| Mapping | URL Configuration |

---

# 💡 Pro Tips

> [!TIP]

Keep Controllers small.

Move Business Logic to Service.

---

> [!IMPORTANT]

Always follow

Controller

↓

Service

↓

Repository

---

# 🗣 English Practice

Read aloud

Controller receives HTTP requests.

Controller calls Service.

Service contains business logic.

Repository accesses the database.

---

# 🧩 Assignment

- [ ] Create EmployeeController.
- [ ] Add @Controller.
- [ ] Add @RequestMapping("/employees").
- [ ] Inject EmployeeService.
- [ ] Explain Request Flow.

---

# 🚀 GitHub Task

Commit Message

```
docs: completed Day 08 Spring Controller
```

---

# ⭐ Today's Challenge

Without looking at notes,

Explain

1. What is Controller?

2. Why do we use @Controller?

3. What is @RequestMapping?

4. Can Controller access Database?

---

# 📌 Summary

✔ Controller receives requests.

✔ Controller calls Service.

✔ Service contains Business Logic.

✔ Repository accesses Database.

✔ Controller never communicates directly with Database.