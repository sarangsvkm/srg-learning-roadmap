

> **Module:** Spring Boot Backend Engineering
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 10 – REST API Basics & API Design]]
>
> **Next:** [[📘 Day 12 – POST API (@PostMapping)]]

---

# 🌟 Daily Motivation

> "Today you write your first real API. Every backend developer starts here."

---

# 🎯 Learning Objectives

Today you will learn

✅ What is GET API?

✅ @GetMapping

✅ @PathVariable

✅ @RequestParam

✅ ResponseEntity

✅ Returning JSON

✅ Testing using Postman

---

# 📖 What is GET API?

## Definition

A GET API is used to retrieve data from the server.

GET never creates or modifies data.

---

# 🇮🇳 Malayalam Explanation

Database-ൽ ഉള്ള Data

Read ചെയ്യാൻ

GET API ഉപയോഗിക്കുന്നു.

GET

↓

Read Only

---

# 🏢 Real Company Example

Employee List

↓

GET

```
/api/employees
```

↓

Returns all Employees

---

Employee Details

↓

GET

```
/api/employees/10
```

↓

Returns Employee with ID 10

---

# 🏗 Request Flow

Client

↓

GET Request

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

# 💻 Example 1

```java
@RestController
@RequestMapping("/api/employees")
public class EmployeeController {

    @GetMapping

    public String getEmployees(){

        return "Employee List";

    }

}
```

---

# 📖 URL

```
GET

http://localhost:8080/api/employees
```

Response

```
Employee List
```

---

# 💻 Example 2

```java
@GetMapping("/{id}")

public String getEmployeeById(
        @PathVariable Long id){

    return "Employee ID : " + id;

}
```

Request

```
GET

/api/employees/5
```

Response

```
Employee ID : 5
```

---

# 📖 @PathVariable

Used to receive values from URL.

Example

```
/employees/10
```

10

↓

@PathVariable

---

# 💻 Example 3

```java
@GetMapping

public String searchEmployee(
        @RequestParam String name){

    return name;

}
```

Request

```
GET

/api/employees?name=Sarang
```

Response

```
Sarang
```

---

# 📖 @RequestParam

Receives query parameters.

Example

```
?name=Sarang
```

---

# 💻 Returning JSON

```java
@GetMapping

public Employee employee(){

    return new Employee(
            1L,
            "Sarang",
            "IT"
    );

}
```

Spring Boot automatically converts the Java object into JSON.

---

# 💻 ResponseEntity

```java
@GetMapping("/{id}")

public ResponseEntity<String> getEmployee(
        @PathVariable Long id){

    return ResponseEntity.ok(
            "Employee : " + id
    );

}
```

---

# 🧪 Testing in Postman

Method

GET

URL

```
http://localhost:8080/api/employees
```

Click

Send

Verify the response.

---

# 🎤 Interview Questions

## Q1

What is GET API?

Answer

GET API retrieves data from the server.

---

## Q2

Does GET modify data?

Answer

No.

GET only reads data.

---

## Q3

What is @PathVariable?

Answer

@PathVariable receives values from the URL.

---

## Q4

What is @RequestParam?

Answer

@RequestParam receives query parameters.

---

## Q5

Why do we use ResponseEntity?

Answer

To return HTTP status code, headers and response body.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| GET | Read Data |
| Path Variable | Value inside URL |
| Query Parameter | URL Parameter |
| ResponseEntity | HTTP Response Wrapper |
| JSON | JavaScript Object Notation |

---

# 💡 Pro Tips

> [!TIP]

Use GET only for reading data.

Never use GET to create or update records.

---

> [!IMPORTANT]

Use plural nouns in endpoints.

Good

```
/api/employees
```

Bad

```
/getEmployee
```

---

# 🗣 English Practice

Read aloud

GET retrieves data.

@PathVariable reads values from URL.

@RequestParam reads query parameters.

ResponseEntity returns HTTP responses.

---

# 🧩 Assignment

- [ ] Create EmployeeController.
- [ ] Create GET /api/employees.
- [ ] Create GET /api/employees/{id}.
- [ ] Create GET using RequestParam.
- [ ] Test APIs using Postman.

---

# 🚀 GitHub Task

Commit Message

```
feat: implement GET APIs for Employee
```

---

# ⭐ Today's Challenge

Without looking at notes

Explain

1. What is GET API?

2. What is @GetMapping?

3. Difference between @PathVariable and @RequestParam?

4. Why do we use ResponseEntity?

---

# 📌 Summary

✔ GET retrieves data.

✔ @GetMapping handles GET requests.

✔ @PathVariable reads values from URL.

✔ @RequestParam reads query parameters.

✔ ResponseEntity returns flexible HTTP responses.

✔ Spring Boot converts Java Objects into JSON automatically.