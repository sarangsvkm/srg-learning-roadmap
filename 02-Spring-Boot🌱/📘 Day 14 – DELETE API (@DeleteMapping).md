

> **Module:** Spring Boot Backend Engineering
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 13 – PUT API (@PutMapping)]]
>
> **Next:** [[📘 Day 15 – Exception Handling]]

---

# 🌟 Daily Motivation

> "Good developers don't just create data. They also know how to remove it safely."

---

# 🎯 Learning Objectives

Today you will learn

✅ What is DELETE API?

✅ @DeleteMapping

✅ deleteById()

✅ @PathVariable

✅ ResponseEntity

✅ HTTP Status Code 204

✅ Resource Not Found

---

# 📖 What is DELETE API?

## Definition

DELETE API is used to remove an existing resource from the database.

---

# 🇮🇳 Malayalam Explanation

Database-ൽ ഉള്ള Employee Record permanently delete ചെയ്യാൻ

DELETE API ഉപയോഗിക്കുന്നു.

Example

Employee ID = 10

↓

DELETE Request

↓

Employee Deleted

---

# 🏢 Real Company Example

Employee Management System

Delete Employee

↓

DELETE

```
DELETE /api/employees/10
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

Employee Deleted

---

# 🏗 Request Flow

Client

↓

DELETE Request

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

204 No Content

---

# 💻 Controller

```java
@DeleteMapping("/{id}")
public ResponseEntity<Void> deleteEmployee(
        @PathVariable Long id){

    service.deleteEmployee(id);

    return ResponseEntity.noContent().build();

}
```

---

# 💻 Service

```java
public void deleteEmployee(Long id){

    Employee employee = repository.findById(id)
            .orElseThrow();

    repository.delete(employee);

}
```

---

# 💻 Alternative Method

```java
repository.deleteById(id);
```

---

# 📖 @DeleteMapping

Used to handle HTTP DELETE requests.

Example

```java
@DeleteMapping("/{id}")
```

---

# 📖 @PathVariable

Reads the Employee ID from the URL.

Example

```
DELETE /api/employees/5
```

ID = 5

---

# 📖 ResponseEntity

```java
return ResponseEntity.noContent().build();
```

Returns

```
204 No Content
```

No response body is sent.

---

# 🧪 Testing in Postman

Method

DELETE

URL

```
http://localhost:8080/api/employees/1
```

Expected Status

```
204 No Content
```

---

# ⚠ Employee Not Found

If the Employee does not exist

```
DELETE /api/employees/100
```

Return

```
404 Not Found
```

We'll implement this properly in Day 15 using Exception Handling.

---

# 🎤 Interview Questions

## Q1

What is DELETE API?

Answer

DELETE API removes an existing resource from the database.

---

## Q2

What is @DeleteMapping?

Answer

It maps HTTP DELETE requests.

---

## Q3

Which Repository method deletes data?

Answer

delete()

or

deleteById()

---

## Q4

Which status code is returned after successful deletion?

Answer

204 No Content

---

## Q5

Why do we use @PathVariable?

Answer

To identify which resource should be deleted.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| DELETE | Remove Resource |
| deleteById | Delete by Primary Key |
| Resource | Database Record |
| No Content | Empty Response |
| Path Variable | URL Parameter |

---

# 💡 Pro Tips

> [!TIP]

Always verify that the resource exists before deleting it.

---

> [!IMPORTANT]

Use **204 No Content** for successful DELETE operations.

---

# 🗣 English Practice

Read aloud

DELETE removes data.

@PathVariable reads the ID.

deleteById deletes the record.

204 No Content means the request succeeded.

---

# 🧩 Assignment

- [ ] Create DELETE API.
- [ ] Read ID using @PathVariable.
- [ ] Delete Employee using deleteById().
- [ ] Return 204 No Content.
- [ ] Test using Postman.

---

# 🚀 GitHub Task

Commit Message

```
feat: implement DELETE API for Employee
```

---

# ⭐ Today's Challenge

Without looking at notes

Explain

1. What is DELETE API?

2. What is @DeleteMapping?

3. Why do we use @PathVariable?

4. What is deleteById()?

5. Which status code is returned after deletion?

---

# 📌 Summary

✔ DELETE removes existing resources.

✔ @DeleteMapping handles DELETE requests.

✔ @PathVariable identifies the resource.

✔ deleteById() deletes the record.

✔ Successful deletion returns HTTP 204 No Content.

✔ If the resource does not exist, return 404 Not Found.