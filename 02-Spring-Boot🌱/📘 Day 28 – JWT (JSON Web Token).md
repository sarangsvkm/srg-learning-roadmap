

> **Module:** Spring Security
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 27 – Authentication & Authorization]]
>
> **Next:** [[📘 Day 29 – JWT Generation & Validation]]

---

# 🌟 Daily Motivation

> "Modern applications don't remember users with sessions—they trust secure tokens."

---

# 🎯 Learning Objectives

Today you will learn

✅ What is JWT?

✅ Why JWT?

✅ JWT Structure

✅ Header

✅ Payload

✅ Signature

✅ Stateless Authentication

---

# 📖 What is JWT?

## Definition

JWT (JSON Web Token) is a secure token used to authenticate users in REST APIs.

After successful login, the server generates a JWT and sends it to the client.

The client includes the JWT in future requests.

---

# 🇮🇳 Malayalam Explanation

User Login ചെയ്യും

↓

Server

↓

JWT Token Generate ചെയ്യും

↓

Client Token Save ചെയ്യും

↓

ഓരോ API Call-ലും

Token അയക്കും

↓

Server Token Verify ചെയ്യും

↓

Request അനുവദിക്കും.

---

# 🏢 Real Company Example

React App

↓

Login

↓

Spring Boot

↓

JWT Generated

↓

React Stores Token

↓

API Request

↓

Authorization Header

↓

Spring Security

↓

Response

---

# 📖 Why JWT?

Without JWT

```
Login

↓

Server Session

↓

Memory Usage
```

With JWT

```
Login

↓

JWT Token

↓

No Server Session

↓

Stateless
```

---

# 📖 JWT Structure

JWT has three parts

```
Header

.

Payload

.

Signature
```

Example

```
xxxxx.yyyyy.zzzzz
```

---

# 📖 Header

Contains

- Algorithm

- Token Type

Example

```json
{
  "alg":"HS256",
  "typ":"JWT"
}
```

---

# 📖 Payload

Contains User Information

Example

```json
{
  "username":"admin",
  "role":"ADMIN"
}
```

Payload is called **Claims**.

---

# 📖 Signature

Signature verifies that the token has not been modified.

Created using

```
Header

+

Payload

+

Secret Key
```

---

# 📖 JWT Authentication Flow

User Login

↓

Username

Password

↓

Authentication Manager

↓

JWT Generated

↓

Client Stores JWT

↓

Future API Requests

↓

Authorization Header

↓

JWT Filter

↓

Controller

---

# 💻 Authorization Header

```
Authorization

Bearer eyJhbGciOiJIUzI1NiJ9...
```

---

# 📦 JWT Dependency

```xml
<dependency>
    <groupId>io.jsonwebtoken</groupId>
    <artifactId>jjwt-api</artifactId>
    <version>0.12.6</version>
</dependency>
```

---

# 📖 Stateless Authentication

Spring Boot does NOT store sessions.

Every request contains the JWT.

Server verifies the token every time.

---

# 📊 Session vs JWT

| Session | JWT |
|----------|-----|
| Server stores session | Client stores token |
| Stateful | Stateless |
| More Memory | Less Memory |
| Traditional Apps | REST APIs |

---

# 🎤 Interview Questions

## Q1

What is JWT?

Answer

JWT is a secure token used for authentication.

---

## Q2

What are the three parts of JWT?

Answer

Header

Payload

Signature

---

## Q3

What is Payload?

Answer

Payload contains user information (claims).

---

## Q4

Why do REST APIs prefer JWT?

Answer

Because JWT is stateless, scalable, and suitable for distributed systems.

---

## Q5

Where is JWT sent?

Answer

Inside the Authorization Header as a Bearer Token.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| JWT | JSON Web Token |
| Token | Authentication Key |
| Header | Token Metadata |
| Payload | User Claims |
| Signature | Security Verification |
| Bearer Token | Authorization Token |

---

# 💡 Pro Tips

> [!TIP]

Always send JWT using the `Authorization` header.

---

> [!IMPORTANT]

Never store your JWT secret key in source code.

Use `application.properties`, environment variables, or a secret manager.

---

# 🗣 English Practice

Read aloud

JWT provides stateless authentication.

A JWT contains Header, Payload, and Signature.

The client sends the JWT in the Authorization header.

---

# 🧩 Assignment

- [ ] Add JWT dependency.
- [ ] Understand JWT structure.
- [ ] Decode a sample JWT using jwt.io.
- [ ] Identify Header, Payload, and Signature.
- [ ] Explain JWT authentication flow.

---

# 🚀 GitHub Task

Commit Message

```
feat: add JWT dependency and project setup
```

---

# ⭐ Today's Challenge

Without looking at notes

Explain

1. What is JWT?

2. Why do companies use JWT?

3. What are the three parts of a JWT?

4. What is Stateless Authentication?

5. Where is JWT sent in an HTTP request?

---

# 📌 Summary

✔ JWT is used for secure authentication.

✔ JWT contains Header, Payload, and Signature.

✔ JWT enables stateless authentication.

✔ Clients send JWT in the Authorization header.

✔ JWT is widely used in REST APIs and Microservices.