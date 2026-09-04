

> **Module:** Spring Boot Backend Engineering
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 12 – POST API (@PostMapping)]]
>
> **Next:** [[📘 Day 14 – DELETE API (@DeleteMapping)]]

---

# 🌟 Daily Motivation

> "Creating data is only the beginning. Professional applications must update data safely."

---

# 🎯 Learning Objectives

Today you will learn

✅ What is PUT API?

✅ @PutMapping

✅ Updating Existing Records

✅ @PathVariable

✅ @RequestBody

✅ ResponseEntity

✅ HTTP Status Code 200

---

# 📖 What is PUT API?

## Definition

PUT API is used to update an existing resource.

It replaces the existing data with new data.

---

# 🇮🇳 Malayalam Explanation

Database-ൽ already ഉള്ള Employee-യുടെ data update ചെയ്യാൻ

PUT API ഉപയോഗിക്കുന്നു.

Example

Employee Name

Old

```
Sarang
```

New

```
Sarang S
```

PUT API വഴി update ചെയ്യാം.

---

# 🏢 Real Company Example

Employee edits profile

↓

PUT

```
PUT /api/employees/1
```

↓

Controller

↓

Service

↓

Repository

↓

Database Updated

---

# 🏗 Request Flow

Client

↓

PUT Request

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

200 OK

---

# 💻 Controller

```java
@PutMapping("/{id}")
public ResponseEntity<Employee> updateEmployee(
        @PathVariable Long id,
        @RequestBody Employee employee){

    Employee updatedEmployee =
            service.updateEmployee(id, employee);

    return ResponseEntity.ok(updatedEmployee);

}
```

---

# 💻 Service

```java
public Employee updateEmployee(
        Long id,
        Employee employee){

    Employee existingEmployee =
            repository.findById(id)
            .orElseThrow();

    existingEmployee.setName(employee.getName());
    existingEmployee.setEmail(employee.getEmail());
    existingEmployee.setDepartment(employee.getDepartment());

    return repository.save(existingEmployee);

}
```

---

# 📖 @PutMapping

Used to update an existing resource.

Example

```java
@PutMapping("/{id}")
```

---

# 📖 @PathVariable

Reads the employee ID from the URL.

Example

```
PUT /api/employees/5
```

ID = 5

---

# 📖 @RequestBody

Receives updated Employee data in JSON format.

---

# 📖 JSON Request

```json
{
  "name":"Sarang S",
  "email":"sarang@gmail.com",
  "department":"Development"
}
```

---

# 📖 JSON Response

```json
{
  "id":1,
  "name":"Sarang S",
  "email":"sarang@gmail.com",
  "department":"Development"
}
```

---

# 📖 ResponseEntity

```java
return ResponseEntity.ok(updatedEmployee);
```

Status

```
200 OK
```

---

# 🧪 Testing using Postman

Method

PUT

URL

```
http://localhost:8080/api/employees/1
```

Headers

```
Content-Type: application/json
```

Body

```json
{
    "name":"Sarang S",
    "email":"sarang@gmail.com",
    "department":"Development"
}
```

Expected Status

```
200 OK
```

---

# ⚠ Employee Not Found

If ID does not exist

Example

```
PUT /api/employees/100
```

Return

```
404 Not Found
```

(We will implement proper exception handling in a later lesson.)

---

# 🎤 Interview Questions

## Q1

What is PUT API?

Answer

PUT API updates an existing resource.

---

## Q2

What is @PutMapping?

Answer

It maps HTTP PUT requests.

---

## Q3

Which annotation reads the ID from the URL?

Answer

@PathVariable

---

## Q4

Which Repository method is used after updating values?

Answer

save()

---

## Q5

Which status code is returned after a successful update?

Answer

200 OK

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| PUT | Update Resource |
| Update | Modify Existing Data |
| Resource | Database Record |
| Path Variable | URL Value |
| RequestBody | JSON Request |

---

# 💡 Pro Tips

> [!TIP]

Always check whether the resource exists before updating it.

---

> [!IMPORTANT]

Do not create a new record during an update.

Update the existing record.

---

# 🗣 English Practice

Read aloud

PUT updates existing data.

@PathVariable reads the ID.

@RequestBody receives JSON.

ResponseEntity returns HTTP responses.

---

# 🧩 Assignment

- [ ] Create PUT API.
- [ ] Read ID using @PathVariable.
- [ ] Receive JSON using @RequestBody.
- [ ] Update Employee.
- [ ] Test using Postman.

---

# 🚀 GitHub Task

Commit Message

```
feat: implement PUT API for Employee
```

---

# ⭐ Today's Challenge

Without looking at notes

Explain

1. What is PUT API?

2. What is @PutMapping?

3. Why do we use @PathVariable?

4. Why do we call save() after updating?

5. Which status code is returned after update?

---

# 📌 Summary

✔ PUT updates existing resources.

✔ @PutMapping handles HTTP PUT requests.

✔ @PathVariable reads ID from the URL.

✔ @RequestBody receives updated JSON.

✔ ResponseEntity returns 200 OK.

✔ Repository.save() stores updated data.