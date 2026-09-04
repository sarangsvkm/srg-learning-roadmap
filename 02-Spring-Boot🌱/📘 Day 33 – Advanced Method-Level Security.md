

> **Module:** Spring Security
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 32 – Role-Based Authorization]]]
>
> **Next:** [[📘 Day 34 - OAuth2-Introduction]]

---

# 🌟 Daily Motivation

> "Enterprise security is about permissions, not just authentication."

---

# 🎯 Learning Objectives

Today you will learn

✅ @PostAuthorize

✅ @PreFilter

✅ @PostFilter

✅ Spring Expression Language (SpEL)

✅ Custom Authorization Rules

---

# 📖 What is Method-Level Security?

## Definition

Method-Level Security allows you to control access to individual methods using annotations.

Unlike URL-based security, it secures business logic directly.

---

# 🇮🇳 Malayalam Explanation

Controller അല്ലെങ്കിൽ Service-യിലെ

ഓരോ Method-നും

Security Rules നൽകുന്നതാണ്

Method-Level Security.

---

# 🏢 Real Company Example

Employee Portal

```
ADMIN

↓

View All Employees

Delete Employee

Approve Leave
```

```
EMPLOYEE

↓

View Own Profile

Update Own Profile
```

---

# 📖 @PostAuthorize

Checks authorization **after** the method executes.

Useful when the decision depends on the returned object.

```java
@PostAuthorize("returnObject.username == authentication.name")
```

Meaning:

Only allow users to access their own profile.

---

# 💻 Example

```java
@PostAuthorize(
    "returnObject.email == authentication.name"
)
public Employee getEmployee(Long id){

    return repository.findById(id)
            .orElseThrow();

}
```

---

# 📖 @PreFilter

Filters a collection **before** a method executes.

```java
@PreFilter("filterObject.owner == authentication.name")
```

---

# 💻 Example

```java
@PreFilter("filterObject.department == 'IT'")
public void processEmployees(
        List<Employee> employees){

}
```

Only IT employees are processed.

---

# 📖 @PostFilter

Filters a collection **after** the method executes.

```java
@PostFilter(
    "filterObject.department == 'IT'"
)
```

---

# 💻 Example

```java
@PostFilter(
    "filterObject.salary < 100000"
)
public List<Employee> getEmployees(){

    return repository.findAll();

}
```

Only matching employees are returned.

---

# 📖 Spring Expression Language (SpEL)

Spring Security uses SpEL for authorization rules.

Common expressions:

```java
hasRole('ADMIN')

hasAnyRole('ADMIN','MANAGER')

hasAuthority('EMPLOYEE_READ')

authentication.name

principal.username

permitAll()

denyAll()
```

---

# 💻 Custom Authorization

```java
@PreAuthorize(
    "#id == authentication.principal.id"
)
```

Only the owner can access their record.

---

# 🏗 Security Flow

```
User Login

↓

JWT Authentication

↓

Method-Level Security

↓

SpEL Evaluation

↓

Access Granted

↓

Method Executes

↓

Response
```

---

# 📊 Annotation Comparison

| Annotation | Purpose |
|------------|---------|
| @PreAuthorize | Before method execution |
| @PostAuthorize | After method execution |
| @PreFilter | Filter input collection |
| @PostFilter | Filter returned collection |

---

# 🎤 Interview Questions

## Q1

What is @PostAuthorize?

Answer

It checks authorization after the method executes.

---

## Q2

What is @PreFilter?

Answer

It filters input collections before method execution.

---

## Q3

What is @PostFilter?

Answer

It filters returned collections after method execution.

---

## Q4

What is SpEL?

Answer

Spring Expression Language used to define security rules.

---

## Q5

Why use Method-Level Security?

Answer

It secures business logic and supports fine-grained access control.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| Method-Level Security | Secure Individual Methods |
| SpEL | Spring Expression Language |
| Filter | Remove Unwanted Data |
| Principal | Logged-in User |
| Authorization | Permission Verification |

---

# 💡 Pro Tips

> [!TIP]

Keep business security rules in the Service layer whenever possible.

---

> [!IMPORTANT]

Never rely only on frontend restrictions. Always enforce authorization in the backend.

---

# 🗣 English Practice

Read aloud

Method-Level Security protects business logic.

SpEL defines authorization rules.

@PostFilter filters returned data.

---

# 🧩 Assignment

- [ ] Enable `@EnableMethodSecurity`.
- [ ] Use `@PostAuthorize`.
- [ ] Use `@PreFilter`.
- [ ] Use `@PostFilter`.
- [ ] Create a custom SpEL authorization rule.

---

# 🚀 GitHub Task

Commit Message

```
feat: implement advanced method-level security
```

---

# ⭐ Today's Challenge

Without looking at notes

Explain

1. What is Method-Level Security?

2. Difference between @PreAuthorize and @PostAuthorize?

3. What is @PreFilter?

4. What is @PostFilter?

5. What is SpEL?

---

# 📌 Summary

✔ Method-Level Security protects individual methods.

✔ @PostAuthorize checks permissions after execution.

✔ @PreFilter filters input collections.

✔ @PostFilter filters returned collections.

✔ SpEL enables powerful authorization rules.

✔ Backend authorization is essential for application security.