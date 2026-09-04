

> **Module:** Spring Boot Core Concepts
>
> **Prerequisite:** [[Spring Data JPA]]
>
> **Next:** [[📘 Spring Service]]

---

# 🌟 Quote

> "Repositories separate business logic from database logic."

---

# 🎯 Learning Objectives

After completing this note, you will understand:

- What is Repository?
- Why Repository?
- Repository Layer
- @Repository
- JpaRepository
- CRUD Operations
- Custom Query Methods
- Repository Architecture
- Best Practices

---

# 📖 What is Spring Repository?

Spring Repository is the **Data Access Layer (DAL)** of a Spring Boot application.

It communicates with the database using Spring Data JPA.

The Repository layer contains database-related operations only.

---

# 🇮🇳 Malayalam Explanation

Repository എന്നത്

Database-മായി

സംസാരിക്കുന്ന Layer ആണ്.

Controller

↓

Service

↓

Repository

↓

Database

Repository-ൽ Business Logic എഴുതരുത്.

Database Operations മാത്രം എഴുതണം.

---

# 🤔 Why Repository?

Without Repository

```
Controller

↓

Database
```

Problems

❌ Tight Coupling

❌ Hard Maintenance

❌ Poor Code Structure

---

With Repository

```
Controller

↓

Service

↓

Repository

↓

Database
```

Advantages

✔ Clean Architecture

✔ Easy Maintenance

✔ Reusable Code

✔ Better Testing

---

# 🏗 Repository Architecture

```
Controller

↓

Service

↓

Repository

↓

Spring Data JPA

↓

Hibernate

↓

JDBC

↓

Database
```

---

# 🏢 Real Company Example

Employee Management System

EmployeeController

↓

EmployeeService

↓

EmployeeRepository

↓

PostgreSQL

---

# 📖 @Repository

Marks a class as a Repository.

```java
@Repository
public class EmployeeRepository {

}
```

In Spring Data JPA, the annotation is optional when extending JpaRepository.

---

# 📖 JpaRepository

```java
public interface EmployeeRepository
        extends JpaRepository<Employee, Long> {

}
```

Spring automatically creates the implementation.

No need to write SQL.

---

# 📖 CRUD Methods

Save

```java
repository.save(employee);
```

Find All

```java
repository.findAll();
```

Find By Id

```java
repository.findById(id);
```

Delete

```java
repository.deleteById(id);
```

Count

```java
repository.count();
```

Exists

```java
repository.existsById(id);
```

---

# 📖 Custom Query Methods

Spring generates queries automatically.

```java
Employee findByEmail(String email);

List<Employee> findByDepartment(String department);

List<Employee> findByNameContaining(String name);

List<Employee> findBySalaryGreaterThan(Double salary);
```

---

# 📖 Using @Query

```java
@Query("SELECT e FROM Employee e WHERE e.department = :department")
List<Employee> findEmployeesByDepartment(String department);
```

---

# 📖 Return Types

```java
Employee

Optional<Employee>

List<Employee>

Page<Employee>

Slice<Employee>

boolean

long
```

---

# 🏗 Repository Flow

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

↓

Repository

↓

Service

↓

Controller

↓

Response
```

---

# 📊 Repository Responsibilities

| Responsibility | Example |
|----------------|---------|
| Save Data | save() |
| Read Data | findById() |
| Read All | findAll() |
| Update Data | save() |
| Delete Data | deleteById() |
| Count Records | count() |

---

# 📊 Repository vs Service

| Repository | Service |
|------------|---------|
| Database Logic | Business Logic |
| CRUD Operations | Business Rules |
| SQL/JPA | Application Logic |

---

# 🎤 Interview Questions

## Q1

What is Repository?

Answer

Repository is the Data Access Layer responsible for database operations.

---

## Q2

What annotation marks a Repository?

Answer

@Repository

---

## Q3

Do we need to implement JpaRepository?

Answer

No.

Spring generates the implementation automatically.

---

## Q4

Can Repository contain business logic?

Answer

No.

Business logic belongs in the Service layer.

---

## Q5

Why use Optional in findById()?

Answer

To safely handle cases where data may not exist, avoiding NullPointerException.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| Repository | Data Access Layer |
| CRUD | Create Read Update Delete |
| Optional | Safe Wrapper |
| Query Method | Auto-generated Query |
| JpaRepository | Spring Data Repository |

---

# 💡 Pro Tips

> [!TIP]

Keep Repository methods focused only on database access.

---

> [!IMPORTANT]

Never put validation or business rules inside the Repository.

Those belong in the Service layer.

---

# 🗣 English Practice

Read aloud

Repository accesses the database.

JpaRepository provides CRUD methods.

Business logic belongs in the Service layer.

---

# 🧩 Assignment

- [ ] Create EmployeeRepository.
- [ ] Extend JpaRepository.
- [ ] Test save().
- [ ] Test findAll().
- [ ] Test findById().
- [ ] Create findByEmail().
- [ ] Create findByDepartment().

---

# 📌 Summary

✔ Repository is the Data Access Layer.

✔ Repository communicates with the database.

✔ JpaRepository provides built-in CRUD methods.

✔ Spring generates Repository implementations automatically.

✔ Business logic should stay in the Service layer.

---

# 🔗 Related Notes

- [[📘 Hibernate]]
- [[JPA]]
- [[Spring Data JPA]]
- [[📘 Spring Service]]