

> **Module:** Spring Security
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 31 – Refresh Token]]
>
> **Next:** [[📘 Day 33 – Advanced Method-Level Security]]

---

# 🌟 Daily Motivation

> "Not every user should have access to everything."

---

# 🎯 Learning Objectives

Today you will learn

✅ What is Role-Based Authorization?

✅ User Roles

✅ @PreAuthorize

✅ @Secured

✅ hasRole()

✅ hasAnyRole()

✅ Method-Level Security

---

# 📖 What is Role-Based Authorization?

## Definition

Role-Based Authorization restricts access to resources based on the user's role.

---

# 🇮🇳 Malayalam Explanation

Application-ൽ എല്ലാ User-ക്കും ഒരേ permission ഉണ്ടായിരിക്കില്ല.

Example

ADMIN

↓

Create Employee

Update Employee

Delete Employee

---

USER

↓

View Employee മാത്രം

---

MANAGER

↓

View + Update Employee

---

# 🏢 Real Company Example

Employee Management System

```
ADMIN

↓

Create Employee

Delete Employee

Update Employee

View Employee
```

```
USER

↓

View Employee
```

```
MANAGER

↓

View Employee

Update Employee
```

---

# 📖 Common Roles

```
ROLE_ADMIN

ROLE_USER

ROLE_MANAGER

ROLE_HR
```

---

# 💻 Enable Method Security

```java
@Configuration
@EnableMethodSecurity
public class SecurityConfig {

}
```

---

# 📖 @PreAuthorize

Checks authorization before a method executes.

```java
@PreAuthorize("hasRole('ADMIN')")
```

Only ADMIN can access.

---

# 💻 Example

```java
@DeleteMapping("/{id}")

@PreAuthorize("hasRole('ADMIN')")

public void deleteEmployee(
        @PathVariable Long id){

}
```

---

# 📖 hasAnyRole()

Allows multiple roles.

```java
@PreAuthorize(
    "hasAnyRole('ADMIN','MANAGER')"
)
```

---

# 📖 @Secured

Alternative annotation.

```java
@Secured("ROLE_ADMIN")
```

---

# 📖 hasAuthority()

Checks specific authorities.

```java
@PreAuthorize(
    "hasAuthority('EMPLOYEE_READ')"
)
```

---

# 📖 Security Flow

```
User Login

↓

JWT Authentication

↓

Extract Role

↓

@PreAuthorize

↓

Access Granted

↓

Controller

↓

Response
```

---

# 💻 Controller Example

```java
@RestController
@RequestMapping("/employees")

public class EmployeeController {

    @GetMapping

    @PreAuthorize(
        "hasAnyRole('USER','ADMIN')"
    )

    public List<Employee> getAllEmployees(){

        return service.getAllEmployees();

    }

}
```

---

# 📊 Annotation Comparison

| Annotation | Purpose |
|------------|---------|
| @PreAuthorize | Check before method execution |
| @Secured | Restrict by Role |
| hasRole() | Single Role |
| hasAnyRole() | Multiple Roles |
| hasAuthority() | Permission Check |

---

# 🎤 Interview Questions

## Q1

What is Role-Based Authorization?

Answer

It controls access based on user roles.

---

## Q2

What does @PreAuthorize do?

Answer

It checks authorization before executing a method.

---

## Q3

Difference between hasRole() and hasAnyRole()?

Answer

hasRole() checks one role.

hasAnyRole() allows multiple roles.

---

## Q4

What is @Secured?

Answer

It restricts access based on roles.

---

## Q5

What is Method-Level Security?

Answer

Applying security rules directly to controller or service methods.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| Role | User Permission Group |
| Authorization | Access Control |
| @PreAuthorize | Pre-execution Security |
| @Secured | Role Restriction |
| Authority | Specific Permission |

---

# 💡 Pro Tips

> [!TIP]

Use `@PreAuthorize` for new Spring Boot applications because it is more flexible than `@Secured`.

---

> [!IMPORTANT]

Always validate both JWT authentication and user authorization before allowing access to protected APIs.

---

# 🗣 English Practice

Read aloud

Role-Based Authorization controls API access.

Only administrators can delete employees.

Method-Level Security protects controller methods.

---

# 🧩 Assignment

- [ ] Enable `@EnableMethodSecurity`.
- [ ] Protect Delete API using `@PreAuthorize("hasRole('ADMIN')")`.
- [ ] Protect Get API using `hasAnyRole()`.
- [ ] Create ADMIN and USER roles.
- [ ] Test role-based access using Postman.

---

# 🚀 GitHub Task

Commit Message

```
feat: implement role-based authorization
```

---

# ⭐ Today's Challenge

Without looking at notes

Explain

1. What is Role-Based Authorization?

2. What is `@PreAuthorize`?

3. Difference between `hasRole()` and `hasAnyRole()`?

4. What is Method-Level Security?

5. Why do enterprise applications use roles?

---

# 📌 Summary

✔ Role-Based Authorization controls API access.

✔ `@PreAuthorize` secures methods.

✔ `hasRole()` checks a single role.

✔ `hasAnyRole()` allows multiple roles.

✔ `@EnableMethodSecurity` enables method-level security.

✔ Enterprise applications protect APIs using roles and permissions.