

> **Module:** Spring Boot Core Concepts
>
> **Prerequisite:** [[Spring Repository]]
>
> **Next:** [[Spring Controller]]

---

# 🌟 Quote

> "Business logic belongs in the Service layer, not in the Controller."

---

# 🎯 Learning Objectives

After completing this note, you will understand:

- What is Spring Service?
- Why Service Layer?
- @Service Annotation
- Business Logic
- Service Architecture
- Service Flow
- Best Practices
- Interview Questions

---

# 📖 What is Spring Service?

Spring Service is the **Business Logic Layer** of a Spring Boot application.

It processes data, validates business rules, communicates with repositories, and returns results to the controller.

---

# 🇮🇳 Malayalam Explanation

Service Layer എന്നത്

Application-ന്റെ Brain ആണ്.

Controller-ൽ നിന്ന് Request സ്വീകരിക്കും.

↓

Business Logic execute ചെയ്യും.

↓

Repository-യിലേക്ക് Database Operation അയക്കും.

↓

Result Controller-ലേക്ക് തിരികെ നൽകും.

---

# 🤔 Why Service Layer?

Without Service

```
Controller

↓

Repository

↓

Database
```

Problems

❌ Business Logic inside Controller

❌ Difficult Maintenance

❌ Poor Reusability

---

With Service

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

✔ Business Logic Centralized

✔ Reusable Code

✔ Easy Testing

---

# 🏗 Service Architecture

```
Client

↓

REST Controller

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

EmployeeController

↓

EmployeeService

↓

EmployeeRepository

↓

PostgreSQL Database

---

# 📖 @Service Annotation

Marks a class as a Service Bean.

```java
@Service
public class EmployeeService {

}
```

Spring automatically manages the object.

---

# 💻 Dependency Injection

```java
@Service
@RequiredArgsConstructor
public class EmployeeService {

    private final EmployeeRepository repository;

}
```

Spring injects the Repository automatically.

---

# 📖 Business Logic Example

```java
public Employee saveEmployee(Employee employee){

    employee.setStatus("ACTIVE");

    return repository.save(employee);

}
```

The Service adds business rules before saving.

---

# 💻 Validation Example

```java
public Employee createEmployee(Employee employee){

    if(employee.getSalary() < 10000){

        throw new IllegalArgumentException(
                "Invalid Salary");

    }

    return repository.save(employee);

}
```

---

# 📖 Service Methods

```java
saveEmployee()

getEmployee()

getAllEmployees()

updateEmployee()

deleteEmployee()
```

---

# 🏗 Complete Flow

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

# 📊 Responsibilities

| Layer | Responsibility |
|--------|---------------|
| Controller | Receive Request |
| Service | Business Logic |
| Repository | Database Access |

---

# 📊 Service vs Repository

| Service | Repository |
|----------|------------|
| Business Logic | Database Logic |
| Validation | CRUD |
| Calculations | Queries |
| Rules | Data Access |

---

# 🎤 Interview Questions

## Q1

What is Spring Service?

Answer

Service Layer contains business logic.

---

## Q2

Why do we use @Service?

Answer

To register the class as a Spring-managed Service Bean.

---

## Q3

Can Service access Database directly?

Answer

No.

It should use Repository.

---

## Q4

Should validation be inside Controller?

Answer

No.

Validation and business rules belong in the Service layer.

---

## Q5

Can one Controller use multiple Services?

Answer

Yes.

Large applications often use multiple Services.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| Service | Business Logic Layer |
| Bean | Spring Managed Object |
| Validation | Rule Checking |
| Business Logic | Application Rules |
| Dependency Injection | Automatic Object Injection |

---

# 💡 Pro Tips

> [!TIP]

Keep Controllers thin and Services smart.

---

> [!IMPORTANT]

Never write SQL or database code inside the Service.

Use Repository for data access.

---

# 🗣 English Practice

Read aloud

The Service layer contains business logic.

The Service communicates with the Repository.

Business rules belong in the Service layer.

---

# 🧩 Assignment

- [ ] Create EmployeeService.
- [ ] Add @Service.
- [ ] Inject EmployeeRepository.
- [ ] Implement saveEmployee().
- [ ] Implement getEmployeeById().
- [ ] Implement updateEmployee().
- [ ] Implement deleteEmployee().

---

# 📌 Summary

✔ Service is the Business Logic Layer.

✔ @Service creates a Spring-managed Bean.

✔ Service communicates with Repository.

✔ Validation belongs in the Service layer.

✔ Controllers should remain thin.

---

# 🔗 Related Notes

- [[Spring Repository]]
- [[Spring Controller]]
- [[Spring REST Controller]]