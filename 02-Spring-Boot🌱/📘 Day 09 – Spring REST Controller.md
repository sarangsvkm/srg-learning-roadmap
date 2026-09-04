

> **Module:** Spring Boot Backend Engineering
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 08 – Spring Controller]]
>
> **Next:** [[📘 Day 10 – REST API Basics & API Design]]

---

# 🌟 Daily Motivation

> "Every mobile app, website, and frontend communicates with the backend through REST APIs."

---

# 🎯 Learning Objectives

Today you will learn:

✅ What is REST?

✅ What is @RestController?

✅ @RequestMapping

✅ @GetMapping

✅ @PostMapping

✅ @PutMapping

✅ @DeleteMapping

✅ JSON Response

---

# 📖 What is REST?

## Definition

REST (Representational State Transfer) is an architectural style used for building web services.

REST APIs allow different applications to communicate over HTTP.

---

# 🇮🇳 Malayalam Explanation

REST API ഉപയോഗിച്ചാണ്

React

Angular

Flutter

Android

iOS

Postman

Backend-ുമായി communicate ചെയ്യുന്നത്.

---

# 🏢 Real Company Example

Mobile App

↓

GET /employees

↓

EmployeeController

↓

EmployeeService

↓

EmployeeRepository

↓

Database

↓

JSON Response

---

# 📖 What is @RestController?

## Definition

@RestController is a Spring annotation used to build REST APIs.

It combines

@Controller

+

@ResponseBody

Every method returns data (JSON/XML) instead of HTML.

---

# 💻 Example

```java
@RestController
@RequestMapping("/employees")
public class EmployeeController {

}
```

---

# 📖 @RequestMapping

Maps a base URL.

```java
@RequestMapping("/employees")
```

Base URL

```
/employees
```

---

# 📖 @GetMapping

Used to retrieve data.

Example

```java
@GetMapping
public String getEmployees(){

    return "Employee List";

}
```

Request

```
GET /employees
```

---

# 📖 @PostMapping

Used to create new data.

```java
@PostMapping
public String saveEmployee(){

    return "Employee Saved";

}
```

---

# 📖 @PutMapping

Used to update data.

```java
@PutMapping("/{id}")
public String updateEmployee(){

    return "Employee Updated";

}
```

---

# 📖 @DeleteMapping

Used to delete data.

```java
@DeleteMapping("/{id}")
public String deleteEmployee(){

    return "Employee Deleted";

}
```

---

# 🏗 Request Flow

Client

↓

@RestController

↓

Service

↓

Repository

↓

Hibernate

↓

PostgreSQL

↓

JSON Response

---

# 📖 JSON Response

```json
{
  "id":1,
  "name":"Sarang",
  "department":"IT"
}
```

---

# 📖 HTTP Methods

| Method | Purpose |
|---------|----------|
| GET | Read Data |
| POST | Create Data |
| PUT | Update Data |
| DELETE | Delete Data |

---

# 📖 @Controller vs @RestController

| @Controller | @RestController |
|-------------|-----------------|
| Returns HTML | Returns JSON |
| MVC | REST API |
| JSP/Thymeleaf | Backend API |

---

# 🎤 Interview Questions

## Q1

What is REST?

Answer

REST is an architectural style for building web services.

---

## Q2

What is @RestController?

Answer

@RestController is used to create REST APIs that return JSON responses.

---

## Q3

Difference between @Controller and @RestController?

Answer

@Controller returns Views.

@RestController returns JSON.

---

## Q4

Which annotation maps GET requests?

Answer

@GetMapping

---

## Q5

Which annotation maps POST requests?

Answer

@PostMapping

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| REST | Web Service Architecture |
| API | Application Programming Interface |
| JSON | Data Format |
| Endpoint | API URL |
| HTTP | Communication Protocol |

---

# 💡 Pro Tips

> [!TIP]

Always return Java Objects instead of Strings.

Spring Boot automatically converts Java Objects into JSON.

---

> [!IMPORTANT]

Use @RestController for Backend APIs.

Use @Controller only for HTML pages.

---

# 🗣 English Practice

Read aloud:

REST APIs exchange data using HTTP.

@RestController returns JSON.

GET retrieves data.

POST creates data.

PUT updates data.

DELETE removes data.

---

# 🧩 Assignment

- [ ] Create EmployeeController.
- [ ] Add @RestController.
- [ ] Add @RequestMapping("/employees").
- [ ] Create one GET API.
- [ ] Create one POST API.
- [ ] Create one PUT API.
- [ ] Create one DELETE API.

---

# 🚀 GitHub Task

Commit Message

```
docs: completed Day 09 Spring REST Controller
```

---

# ⭐ Today's Challenge

Without looking at notes:

1. What is REST?

2. What is @RestController?

3. Difference between @Controller and @RestController?

4. Name four HTTP methods.

5. What format does @RestController usually return?

---

# 📌 Summary

✔ REST is used to build web services.

✔ @RestController creates REST APIs.

✔ REST APIs usually return JSON.

✔ GET → Read

✔ POST → Create

✔ PUT → Update

✔ DELETE → Delete