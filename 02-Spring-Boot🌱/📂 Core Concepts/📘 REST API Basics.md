

> **Module:** Spring Boot Core Concepts
>
> **Prerequisite:** [[Spring REST Controller]]
>
> **Next:** [[📘 HTTP Status Codes]]

---

# 🌟 Quote

> "REST APIs allow different applications to communicate using HTTP."

---

# 🎯 Learning Objectives

After completing this note, you will understand:

- What is REST?
- What is an API?
- REST Principles
- HTTP Methods
- HTTP Status Codes
- Request & Response
- REST Architecture
- Best Practices
- Interview Questions

---

# 📖 What is an API?

API (Application Programming Interface) is a bridge that allows two applications to communicate with each other.

Example

```
Mobile App

↓

API

↓

Spring Boot

↓

Database
```

---

# 📖 What is REST?

REST stands for **Representational State Transfer**.

It is an architectural style for designing web services.

REST APIs use HTTP methods to perform operations.

---

# 🇮🇳 Malayalam Explanation

REST API എന്നത്

Applications തമ്മിൽ

Internet വഴി

Data കൈമാറാനുള്ള ഒരു Standard ആണ്.

Example

React

↓

Spring Boot API

↓

PostgreSQL

---

# 🏢 Real Company Example

Employee Mobile App

↓

REST API

↓

Employee Service

↓

Repository

↓

Database

↓

JSON Response

---

# 🏗 REST Architecture

```
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

Database

↓

JSON Response
```

---

# 📖 HTTP Methods

GET

Read Data

---

POST

Create Data

---

PUT

Update Existing Data

---

PATCH

Partial Update

---

DELETE

Delete Data

---

# 📖 HTTP Request

Example

```http
GET /employees
```

Contains

- URL
- Headers
- Query Parameters
- Body (optional)

---

# 📖 HTTP Response

Contains

- Status Code
- Headers
- JSON Body

Example

```json
{
  "id":1,
  "name":"Sarang"
}
```

---

# 📖 Request Body

```json
{
  "name":"Rahul",
  "department":"IT"
}
```

Spring Annotation

```java
@RequestBody
```

---

# 📖 Path Variable

```http
GET /employees/10
```

```java
@GetMapping("/{id}")
public Employee getEmployee(
        @PathVariable Long id){

}
```

---

# 📖 Query Parameter

```http
GET /employees?department=IT
```

```java
@RequestParam String department
```

---

# 📖 Common HTTP Status Codes

| Code | Meaning |
|------|---------|
| 200 | OK |
| 201 | Created |
| 204 | No Content |
| 400 | Bad Request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |
| 500 | Internal Server Error |

---

# 📖 REST Principles

✔ Client-Server

✔ Stateless

✔ Uniform Interface

✔ Cacheable

✔ Layered System

---

# 🏗 Complete Flow

```
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

Database

↓

JSON Response
```

---

# 📊 REST vs SOAP

| REST | SOAP |
|------|------|
| JSON/XML | XML |
| Lightweight | Heavy |
| Faster | Slower |
| Easy to Learn | Complex |

---

# 🎤 Interview Questions

## Q1

What is REST?

Answer

REST is an architectural style used to build web services.

---

## Q2

What is an API?

Answer

An API allows different applications to communicate.

---

## Q3

Which HTTP method creates data?

Answer

POST

---

## Q4

Difference between PUT and PATCH?

Answer

PUT updates the entire resource.

PATCH updates only selected fields.

---

## Q5

Why are REST APIs called Stateless?

Answer

Each request contains all the information needed to process it. The server does not store client session state between requests.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| REST | Representational State Transfer |
| API | Application Programming Interface |
| Endpoint | API URL |
| Request | Client Message |
| Response | Server Reply |
| JSON | Data Format |

---

# 💡 Pro Tips

> [!TIP]

Use nouns in URLs.

Example

```
/employees
```

instead of

```
/getEmployees
```

---

> [!IMPORTANT]

Always use appropriate HTTP methods and return meaningful HTTP status codes.

---

# 🧩 Assignment

- [ ] Create GET API.
- [ ] Create POST API.
- [ ] Create PUT API.
- [ ] Create DELETE API.
- [ ] Test using Postman.

---

# 📌 Summary

✔ REST APIs use HTTP.

✔ REST is Stateless.

✔ APIs exchange JSON.

✔ HTTP methods perform CRUD operations.

✔ Status codes indicate request results.

---

# 🔗 Related Notes

- [[Spring REST Controller]]
- [[📘 HTTP Status Codes]]
- [[📘 Spring Service]]