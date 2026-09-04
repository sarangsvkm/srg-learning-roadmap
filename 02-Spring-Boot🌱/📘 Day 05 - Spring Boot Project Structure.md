

> **Module:** Spring Boot Backend Engineering
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 04 – Maven & pom.xml]]
>
> **Next:** [[📘 Day 06 - application.properties]]]

---

# 🌟 Daily Motivation

> "A clean project structure makes software easier to build, maintain, and scale."

---

# 🎯 Learning Objectives

Today you will learn:

✅ Spring Boot Project Structure

✅ Package Organization

✅ Purpose of each folder

✅ Best Practices

---

# 📖 Spring Boot Project Structure

```
employee-management-system

├── src
│
├── main
│   │
│   ├── java
│   │
│   └── resources
│
├── test
│
├── pom.xml
│
├── mvnw
│
└── README.md
```

---

# 🇮🇳 Malayalam Explanation

Spring Boot project-ൽ ഓരോ folder-ക്കും ഓരോ responsibility ഉണ്ട്.

ഓരോ code-വും ശരിയായ package-ൽ എഴുതണം.

ഇതാണ് company standard.

---

# 📂 src/main/java

Contains Java Source Code.

Inside this folder we create packages.

Example

```
com.sarang.ems

├── controller

├── service

├── repository

├── entity

├── dto

├── config

├── exception

├── security

└── EmployeeManagementApplication.java
```

---

# 📂 controller

Responsibility

Receives HTTP Requests

Example

```
GET /employees

POST /employees
```

Controller talks to Service.

---

# 📂 service

Contains Business Logic.

Example

Calculate Salary

Validate Employee

Generate Report

Service talks to Repository.

---

# 📂 repository

Communicates with Database.

Example

Save Employee

Delete Employee

Find Employee

Uses Spring Data JPA.

---

# 📂 entity

Contains Database Tables.

Example

Employee.java

Department.java

Attendance.java

---

# 📂 dto

Data Transfer Objects.

Used to send data between Client and Server.

---

# 📂 config

Application Configuration.

Examples

CORS

Swagger

Bean Configuration

---

# 📂 security

Contains

JWT

Spring Security

Authentication

Authorization

---

# 📂 exception

Handles Exceptions.

Example

EmployeeNotFoundException

GlobalExceptionHandler

---

# 📂 resources

Contains

application.properties

application.yml

Static Files

Templates

SQL Scripts

---

# 📂 test

Contains Unit Tests.

JUnit

Mockito

Integration Tests

---

# 🏢 Real Company Flow

Browser

↓

Controller

↓

Service

↓

Repository

↓

PostgreSQL

↓

Repository

↓

Service

↓

Controller

↓

Browser

---

# 💻 Package Structure

```
com.sarang.ems

├── controller

├── service

├── repository

├── entity

├── dto

├── config

├── security

├── exception

└── EmployeeManagementApplication
```

---

# 🎤 Interview Questions

## Q1

Why do we use Controller?

Answer

Controller handles incoming HTTP requests.

---

## Q2

What is Service Layer?

Answer

Service layer contains business logic.

---

## Q3

What is Repository?

Answer

Repository communicates with the database.

---

## Q4

What is Entity?

Answer

Entity represents a database table.

---

## Q5

What is DTO?

Answer

DTO transfers data between client and server.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| Controller | Handles HTTP Requests |
| Service | Business Logic |
| Repository | Database Layer |
| Entity | Database Table |
| DTO | Data Transfer Object |
| Config | Configuration |
| Exception | Error Handling |

---

# 💡 Pro Tips

> [!TIP]

Never write database code inside Controller.

Controller → Service → Repository

Always follow layered architecture.

---

> [!IMPORTANT]

Each package should have a single responsibility.

---

# 🗣 English Practice

Read aloud:

Controller handles requests.

Service contains business logic.

Repository communicates with the database.

Entity represents database tables.

---

# 🧩 Assignment

- [ ] Create all packages.
- [ ] Understand each package's responsibility.
- [ ] Draw the architecture diagram in your notebook.
- [ ] Explain the request flow in your own words.

---

# 🚀 GitHub Task

Commit Message

```
docs: completed Day 05 project structure
```

---

# ⭐ Today's Challenge

Without looking at notes,

Explain

1. Controller

2. Service

3. Repository

4. Entity

5. DTO

---

# 📌 Summary

✔ Controller receives requests.

✔ Service contains business logic.

✔ Repository accesses the database.

✔ Entity maps database tables.

✔ DTO transfers data.

✔ Config manages application settings.

✔ Exception handles application errors.

✔ Security manages authentication and authorization.
