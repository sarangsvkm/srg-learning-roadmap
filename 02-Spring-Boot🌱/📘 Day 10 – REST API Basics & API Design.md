
> **Module:** Spring Boot Backend Engineering
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 09 – Spring REST Controller]]
>
> **Next:** [[📘 Day 11 – GET API (@GetMapping)]]]

---

# 🌟 Daily Motivation

> "A good API is easy to understand, easy to use, and easy to maintain."

---

# 🎯 Learning Objectives

Today you will learn

✅ What is REST API?

✅ REST API Principles

✅ API Endpoint Design

✅ HTTP Methods

✅ HTTP Status Codes

✅ JSON Request & Response

✅ ResponseEntity

✅ API Best Practices

---

# 📖 What is REST API?

## Definition

REST API (Representational State Transfer API) is a web service that allows different applications to communicate using HTTP.

---

# 🇮🇳 Malayalam Explanation

Frontend

↓

React

Flutter

Angular

Android

↓

REST API

↓

Spring Boot

↓

Database

REST API ആണ് Frontend-നും Backend-നും ഇടയിൽ data exchange ചെയ്യുന്നത്.

---

# 🏢 Real Company Example

Employee Management System

Employee List Screen

↓

GET /api/employees

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

# 📖 REST API Principles

REST APIs should be

- Stateless
- Client-Server
- Cacheable
- Uniform Interface

---

# 📖 API Endpoint Design

Good API

```
GET /api/employees
```

Bad API

```
GET /getEmployeeList
```

Use nouns

Not verbs.

---

# 📖 HTTP Methods

GET

Retrieve Data

Example

```
GET /api/employees
```

---

POST

Create Data

```
POST /api/employees
```

---

PUT

Update Complete Resource

```
PUT /api/employees/1
```

---

PATCH

Update Partial Resource

```
PATCH /api/employees/1
```

---

DELETE

Delete Resource

```
DELETE /api/employees/1
```

---

# 📖 HTTP Status Codes

200 OK

Request Successful

---

201 Created

Resource Created

---

204 No Content

Delete Successful

---

400 Bad Request

Invalid Request

---

401 Unauthorized

Authentication Required

---

403 Forbidden

Access Denied

---

404 Not Found

Resource Not Found

---

500 Internal Server Error

Server Error

---

# 📖 JSON Request

```json
{
  "name":"Sarang",
  "email":"sarang@gmail.com",
  "department":"IT"
}
```

---

# 📖 JSON Response

```json
{
  "id":1,
  "name":"Sarang",
  "email":"sarang@gmail.com",
  "department":"IT"
}
```

---

# 💻 ResponseEntity

Example

```java
@GetMapping("/{id}")

public ResponseEntity<Employee> getEmployee(
        @PathVariable Long id){

    Employee employee = service.getEmployee(id);

    return ResponseEntity.ok(employee);

}
```

---

# 📖 Why ResponseEntity?

Allows us to return

- Status Code
- Headers
- Body

in one object.

---

# 📖 API Naming Best Practices

Good

```
/api/employees
```

```
/api/departments
```

```
/api/attendance
```

Bad

```
/getEmployees
```

```
/saveEmployee
```

---

# 🏗 Request Flow

Client

↓

HTTP Request

↓

REST Controller

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

# 🎤 Interview Questions

## Q1

What is REST API?

Answer

REST API is a web service that allows applications to communicate over HTTP.

---

## Q2

Which HTTP method creates data?

Answer

POST

---

## Q3

Which HTTP method retrieves data?

Answer

GET

---

## Q4

Why do we use ResponseEntity?

Answer

To return HTTP status code, headers and response body.

---

## Q5

Difference between PUT and PATCH?

Answer

PUT updates the complete resource.

PATCH updates only specific fields.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| REST | Representational State Transfer |
| API | Application Programming Interface |
| Endpoint | API URL |
| JSON | Data Format |
| HTTP | Communication Protocol |
| ResponseEntity | HTTP Response Wrapper |

---

# 💡 Pro Tips

> [!TIP]

Always use plural nouns for API endpoints.

Example

/api/employees

---

> [!IMPORTANT]

Never expose database table names directly.

Design clean and meaningful API URLs.

---

# 🗣 English Practice

Read aloud

REST APIs communicate over HTTP.

GET retrieves data.

POST creates data.

PUT updates data.

DELETE removes data.

ResponseEntity returns HTTP responses.

---

# 🧩 Assignment

- [ ] Learn all HTTP methods.
- [ ] Learn status codes.
- [ ] Design 10 API endpoints.
- [ ] Create JSON request examples.
- [ ] Create JSON response examples.

---

# 🚀 GitHub Task

Commit Message

```
docs: completed Day 10 REST API Basics
```

---

# ⭐ Today's Challenge

Without looking at notes

Explain

1. REST API

2. HTTP Methods

3. Status Codes

4. JSON

5. ResponseEntity

---

# 📌 Summary

✔ REST APIs connect Frontend and Backend.

✔ HTTP methods define operations.

✔ JSON is the standard data format.

✔ ResponseEntity provides flexible HTTP responses.

✔ Good API design improves maintainability.