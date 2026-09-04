

> **Module:** Spring Boot Backend Engineering
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 25 – Spring Boot Testing (JUnit 5 & Mockito)]]
>
> **Next:** [[📘 Day 27 – Authentication & Authorization]]

---

# 🌟 Daily Motivation

> "A working application is good. A secure application is professional."

---

# 🎯 Learning Objectives

Today you will learn

✅ What is Spring Security?

✅ Why do we need Security?

✅ Authentication

✅ Authorization

✅ Security Filter Chain

✅ BCrypt Password Encoder

✅ Basic Security Configuration

---

# 📖 What is Spring Security?

## Definition

Spring Security is a powerful framework used to secure Spring Boot applications.

It provides authentication, authorization, password encryption, session management, and protection against common security attacks.

---

# 🇮🇳 Malayalam Explanation

Application-ൽ

- Login
- Password Protection
- Role-based Access
- API Security

ഇവയെല്ലാം ചെയ്യാൻ ഉപയോഗിക്കുന്ന Framework ആണ് Spring Security.

---

# 🏢 Real Company Example

Employee Portal

↓

Login Page

↓

Username + Password

↓

Spring Security

↓

Authentication

↓

Authorized User

↓

Dashboard

---

# 📖 Why Spring Security?

Without Security

❌ Anyone can access APIs

❌ No Login

❌ No Role Management

❌ Data is not protected

With Spring Security

✔ Secure Login

✔ Protected APIs

✔ Role-Based Access

✔ Password Encryption

---

# 📦 Maven Dependency

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-security</artifactId>
</dependency>
```

---

# 📖 Authentication

Authentication verifies

**Who are you?**

Example

```
Username

Password
```

If correct

↓

Login Success

---

# 📖 Authorization

Authorization verifies

**What are you allowed to do?**

Example

```
ADMIN

↓

Create Employee

Delete Employee

Update Employee
```

```
USER

↓

View Employee Only
```

---

# 📖 Authentication vs Authorization

| Authentication | Authorization |
|----------------|---------------|
| Verify Identity | Verify Permission |
| Login | Access Control |
| Username & Password | Roles & Privileges |

---

# 📖 Security Filter Chain

Request

↓

Security Filter

↓

Authentication

↓

Authorization

↓

Controller

↓

Response

---

# 💻 Security Configuration

```java
@Configuration
@EnableWebSecurity
public class SecurityConfig {

    @Bean
    SecurityFilterChain securityFilterChain(
            HttpSecurity http)
            throws Exception {

        http
            .authorizeHttpRequests(auth -> auth
                .anyRequest()
                .authenticated()
            )
            .formLogin();

        return http.build();
    }

}
```

---

# 📖 BCrypt Password Encoder

Never store passwords as plain text.

Example

❌

```
password123
```

✅

```
$2a$10$KXQz...
```

---

# 💻 Password Encoder Bean

```java
@Bean
public PasswordEncoder passwordEncoder() {

    return new BCryptPasswordEncoder();

}
```

---

# 💻 Encode Password

```java
String encodedPassword =
        passwordEncoder.encode("password123");
```

---

# 🏗 Security Flow

Client

↓

Login Request

↓

Spring Security

↓

Authentication

↓

Authorization

↓

Controller

↓

Response

---

# 🎤 Interview Questions

## Q1

What is Spring Security?

Answer

Spring Security is a framework used to secure Spring Boot applications.

---

## Q2

What is Authentication?

Answer

Authentication verifies the identity of the user.

---

## Q3

What is Authorization?

Answer

Authorization determines what resources a user can access.

---

## Q4

Why do we use BCryptPasswordEncoder?

Answer

To securely hash passwords before storing them.

---

## Q5

Can passwords be stored in plain text?

Answer

No.

Passwords should always be encrypted using BCrypt or another secure hashing algorithm.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| Security | Protection |
| Authentication | Identity Verification |
| Authorization | Permission Checking |
| Password Encoder | Password Hashing |
| Filter Chain | Request Processing Pipeline |

---

# 💡 Pro Tips

> [!TIP]

Always hash passwords before storing them in the database.

---

> [!IMPORTANT]

Never expose login credentials, JWT secrets, or encryption keys in your source code or GitHub repository.

---

# 🗣 English Practice

Read aloud

Spring Security protects applications.

Authentication verifies identity.

Authorization checks permissions.

BCrypt encrypts passwords.

---

# 🧩 Assignment

- [ ] Add Spring Security dependency.
- [ ] Create `SecurityConfig`.
- [ ] Configure `SecurityFilterChain`.
- [ ] Add `BCryptPasswordEncoder` Bean.
- [ ] Run the application and observe the default login page.

---

# 🚀 GitHub Task

Commit Message

```
feat: integrate Spring Security basics
```

---

# ⭐ Today's Challenge

Without looking at notes

Explain

1. What is Spring Security?

2. Difference between Authentication and Authorization?

3. What is SecurityFilterChain?

4. Why do we use BCryptPasswordEncoder?

5. Why should passwords never be stored in plain text?

---

# 📌 Summary

✔ Spring Security secures Spring Boot applications.

✔ Authentication verifies user identity.

✔ Authorization controls user permissions.

✔ SecurityFilterChain processes incoming requests.

✔ BCryptPasswordEncoder securely hashes passwords.

✔ Never store plain-text passwords.