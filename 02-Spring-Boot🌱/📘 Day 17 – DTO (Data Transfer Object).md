

> **Module:** Spring Boot Backend Engineering
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 16 – Validation in Spring Boot]]
>
> **Next:** [[📘 Day 18 – ModelMapper]]]

---

# 🌟 Daily Motivation

> "Professional APIs expose DTOs, not database entities."

---

# 🎯 Learning Objectives

Today you will learn

✅ What is DTO?

✅ Why do we use DTO?

✅ Entity vs DTO

✅ Request DTO

✅ Response DTO

✅ DTO Mapping

---

# 📖 What is DTO?

## Definition

DTO (Data Transfer Object) is a simple Java object used to transfer data between the client and the server.

DTO is mainly used in REST APIs.

---

# 🇮🇳 Malayalam Explanation

DTO എന്നത്

Client-നും

Backend-നും

ഇടയിൽ

Data അയക്കാൻ ഉപയോഗിക്കുന്ന Java Object ആണ്.

Database Entity

നേരിട്ട് API-യിൽ അയക്കില്ല.

DTO ആണ് അയക്കുന്നത്.

---

# 🏢 Real Company Example

Mobile App

↓

EmployeeRequestDTO

↓

Controller

↓

Service

↓

Repository

↓

Employee Entity

↓

Database

↓

EmployeeResponseDTO

↓

Client

---

# 📖 Why DTO?

Without DTO

```
Client

↓

Employee Entity

↓

Database
```

Problems

❌ Password exposed

❌ Internal fields exposed

❌ Security issues

---

With DTO

```
Client

↓

EmployeeDTO

↓

Controller

↓

Service

↓

Entity

↓

Database
```

Advantages

✔ Better Security

✔ Clean API

✔ Flexible Response

✔ Better Maintainability

---

# 💻 Employee Entity

```java
@Entity
public class Employee {

    @Id
    private Long id;

    private String name;

    private String email;

    private String password;

}
```

---

# 💻 EmployeeResponseDTO

```java
public class EmployeeResponseDTO {

    private Long id;

    private String name;

    private String email;

}
```

Password is NOT returned.

---

# 💻 EmployeeRequestDTO

```java
public class EmployeeRequestDTO {

    private String name;

    private String email;

    private String password;

}
```

Used while creating Employee.

---

# 📖 Entity vs DTO

| Entity | DTO |
|---------|-----|
| Database Object | API Object |
| Contains all fields | Contains required fields only |
| Used with JPA | Used with REST APIs |
| Stored in Database | Sent to Client |

---

# 🏗 Request Flow

Client

↓

EmployeeRequestDTO

↓

Controller

↓

Service

↓

Employee Entity

↓

Repository

↓

Database

↓

EmployeeResponseDTO

↓

Client

---

# 💻 Manual Mapping

DTO → Entity

```java
Employee employee = new Employee();

employee.setName(dto.getName());

employee.setEmail(dto.getEmail());

employee.setPassword(dto.getPassword());
```

---

Entity → DTO

```java
EmployeeResponseDTO dto = new EmployeeResponseDTO();

dto.setId(employee.getId());

dto.setName(employee.getName());

dto.setEmail(employee.getEmail());
```

---

# 🎤 Interview Questions

## Q1

What is DTO?

Answer

DTO is a Data Transfer Object used to transfer data between client and server.

---

## Q2

Why do we use DTO?

Answer

To improve security, reduce unnecessary data exposure, and design clean APIs.

---

## Q3

Should Entity be returned directly?

Answer

No.

Use DTO instead.

---

## Q4

Can DTO contain validation annotations?

Answer

Yes.

Example

```java
@NotBlank

@Email
```

---

## Q5

Where is DTO used?

Answer

Between Controller and Client.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| DTO | Data Transfer Object |
| Entity | Database Object |
| Mapping | Data Conversion |
| Request DTO | Incoming Data |
| Response DTO | Outgoing Data |

---

# 💡 Pro Tips

> [!TIP]

Never expose Entity directly in REST APIs.

Always use DTO.

---

> [!IMPORTANT]

Store password in Entity.

Never return password in Response DTO.

---

# 🗣 English Practice

Read aloud

DTO transfers data.

Entity stores database information.

DTO improves API security.

---

# 🧩 Assignment

- [ ] Create EmployeeRequestDTO.
- [ ] Create EmployeeResponseDTO.
- [ ] Map DTO to Entity.
- [ ] Map Entity to DTO.
- [ ] Test API response.

---

# 🚀 GitHub Task

Commit Message

```
feat: add DTO layer for Employee API
```

---

# ⭐ Today's Challenge

Without looking at notes

Explain

1. What is DTO?

2. Why do we use DTO?

3. Difference between Entity and DTO?

4. Why should password not be returned?

5. Where is DTO used?

---

# 📌 Summary

✔ DTO transfers data between client and server.

✔ Entity represents the database table.

✔ DTO improves security.

✔ Response DTO hides sensitive fields.

✔ Request DTO accepts client input.

✔ Professional APIs always use DTOs.