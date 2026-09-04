

> **Module:** Spring Boot Backend Engineering
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 11 – GET API (@GetMapping)]]]
>
> **Next:** [[📘 Day 13 – PUT API (@PutMapping)]]]

---

# 🌟 Daily Motivation

> "Today's API doesn't just return data—it creates new records."

---

# 🎯 Learning Objectives

Today you will learn

✅ What is POST API?

✅ @PostMapping

✅ @RequestBody

✅ @Valid

✅ ResponseEntity

✅ HTTP Status 201 Created

✅ Saving Data using Service

---

# 📖 What is POST API?

## Definition

POST API is used to create a new resource in the database.

It sends data from the client to the server.

---

# 🇮🇳 Malayalam Explanation

User Form Fill ചെയ്യും

↓

POST Request

↓

Spring Boot

↓

Database

↓

New Record Created

---

# 🏢 Real Company Example

Employee Registration

User clicks

Save Employee

↓

POST

```
POST /api/employees
```

↓

EmployeeController

↓

EmployeeService

↓

EmployeeRepository

↓

PostgreSQL

↓

Employee Saved

---

# 🏗 Request Flow

Client

↓

POST Request

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

201 Created

---

# 💻 Employee Entity

```java
@Entity
public class Employee {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;

    private String email;

    private String department;

}
```

---

# 💻 Controller

```java
@RestController
@RequestMapping("/api/employees")
public class EmployeeController {

    private final EmployeeService service;

    public EmployeeController(EmployeeService service) {
        this.service = service;
    }

    @PostMapping
    public ResponseEntity<Employee> saveEmployee(
            @RequestBody Employee employee){

        Employee savedEmployee =
                service.save(employee);

        return ResponseEntity.status(201)
                .body(savedEmployee);

    }

}
```

---

# 💻 Service

```java
@Service
public class EmployeeService {

    private final EmployeeRepository repository;

    public EmployeeService(EmployeeRepository repository) {
        this.repository = repository;
    }

    public Employee save(Employee employee){

        return repository.save(employee);

    }

}
```

---

# 💻 Repository

```java
@Repository
public interface EmployeeRepository
        extends JpaRepository<Employee, Long>{

}
```

---

# 📖 @RequestBody

Receives JSON data from the client.

Example Request

```json
{
  "name":"Sarang",
  "email":"sarang@gmail.com",
  "department":"IT"
}
```

Spring converts JSON → Java Object automatically.

---

# 📖 @Valid

Used to validate input.

Example

```java
public ResponseEntity<Employee> save(
        @Valid
        @RequestBody Employee employee)
```

---

# 📖 Validation Example

```java
@NotBlank
private String name;

@Email
private String email;

@NotBlank
private String department;
```

---

# 📖 ResponseEntity

```java
return ResponseEntity
        .status(HttpStatus.CREATED)
        .body(savedEmployee);
```

Returns

- Status Code
- Headers
- Response Body

---

# 🧪 Testing in Postman

Method

POST

URL

```
http://localhost:8080/api/employees
```

Headers

```
Content-Type: application/json
```

Body

```json
{
    "name":"Sarang",
    "email":"sarang@gmail.com",
    "department":"IT"
}
```

Expected Response

```json
{
    "id":1,
    "name":"Sarang",
    "email":"sarang@gmail.com",
    "department":"IT"
}
```

Status

```
201 Created
```

---

# 🎤 Interview Questions

## Q1

What is POST API?

Answer

POST API is used to create new resources.

---

## Q2

What is @RequestBody?

Answer

@RequestBody converts JSON into a Java Object.

---

## Q3

Why do we use @Valid?

Answer

To validate incoming request data.

---

## Q4

Which HTTP Status Code is returned after successful creation?

Answer

201 Created

---

## Q5

Which Repository method saves data?

Answer

save()

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| POST | Create Resource |
| RequestBody | Request Data |
| Validation | Input Checking |
| JSON | Data Format |
| ResponseEntity | HTTP Response |

---

# 💡 Pro Tips

> [!TIP]

Always validate user input before saving it.

---

> [!IMPORTANT]

Never trust client input directly.

Use validation annotations like @NotBlank and @Email.

---

# 🗣 English Practice

Read aloud

POST creates new data.

@RequestBody receives JSON.

Spring converts JSON into Java Objects.

Repository saves data into the database.

---

# 🧩 Assignment

- [ ] Create Employee Entity.
- [ ] Create POST API.
- [ ] Add @RequestBody.
- [ ] Test using Postman.
- [ ] Save data into PostgreSQL.

---

# 🚀 GitHub Task

Commit Message

```
feat: implement POST API for Employee
```

---

# ⭐ Today's Challenge

Without looking at notes

Explain

1. What is POST API?

2. What is @RequestBody?

3. Why do we use @Valid?

4. Why use ResponseEntity?

5. Which method saves data?

---

# 📌 Summary

✔ POST creates new resources.

✔ @PostMapping handles POST requests.

✔ @RequestBody converts JSON into Java Objects.

✔ @Valid validates user input.

✔ Repository.save() stores data in the database.

✔ Successful POST returns HTTP 201 Created.