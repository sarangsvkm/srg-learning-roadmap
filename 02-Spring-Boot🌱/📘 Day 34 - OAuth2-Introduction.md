

> **Module:** Spring Security
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 33 – Advanced Method-Level Security]]]
>
> **Next:** [[📘 Day 35 – Google OAuth2 Login]]

---

# 🌟 Daily Motivation

> "Never ask users for their passwords. Let trusted identity providers handle authentication securely."

---

# 🎯 Learning Objectives

Today you will learn

✅ What is OAuth2?

✅ Why OAuth2?

✅ OAuth2 Components

✅ OAuth2 Roles

✅ Authorization Server

✅ Resource Server

✅ Authorization Code Flow

✅ OAuth2 Architecture

---

# 📖 What is OAuth2?

## Definition

OAuth 2.0 is an authorization framework that allows a user to grant a third-party application limited access to their resources without sharing their password.

OAuth2 enables secure login using trusted providers such as Google, GitHub, Microsoft, and Facebook.

---

# 🇮🇳 Malayalam Explanation

ഉദാഹരണം

"Continue with Google"

↓

Google Login Page

↓

Google User-നെ Verify ചെയ്യും

↓

Application-ന് Access Token നൽകും

↓

Application Login ചെയ്യും

Google Password Application-ന് ഒരിക്കലും അറിയില്ല.

---

# 🤔 Why OAuth2?

Before OAuth2

```
User

↓

Application asks for Password

↓

Security Risk
```

After OAuth2

```
User

↓

Google Login

↓

Google Authentication

↓

Access Token

↓

Application
```

Advantages

✔ Secure Authentication

✔ No Password Sharing

✔ Trusted Login

✔ Easy Social Login

---

# 🏢 Real Company Example

Netflix

↓

Continue with Google

↓

Google Authentication

↓

OAuth2 Access Token

↓

Netflix Dashboard

---

GitHub

↓

Login with Microsoft

↓

Microsoft Authentication

↓

Access Token

↓

GitHub Dashboard

---

# 📖 OAuth2 Components

### Resource Owner

The User

---

### Client

Spring Boot Application

---

### Authorization Server

Google

GitHub

Microsoft

Facebook

---

### Resource Server

Spring Boot REST API

---

# 🏗 OAuth2 Architecture

```
User

↓

Browser

↓

Spring Boot Client

↓

Authorization Server

↓

Access Token

↓

Spring Boot API

↓

Database
```

---

# 📖 OAuth2 Authorization Code Flow

```
User

↓

Click Login with Google

↓

Google Login Page

↓

User Login

↓

Authorization Code

↓

Spring Boot

↓

Access Token

↓

User Information

↓

Dashboard
```

---

# 📖 OAuth2 Grant Types

Authorization Code

✔ Web Applications

✔ Most Secure

---

Client Credentials

✔ Machine-to-Machine Communication

---

Refresh Token

✔ Generate New Access Token

---

Device Code

✔ Smart TVs

✔ IoT Devices

---

# 📖 Access Token

Access Token is used to access protected APIs.

Example

```
Authorization

Bearer eyJhbGc...
```

Usually expires in

15–60 Minutes

---

# 📖 Refresh Token

Refresh Token generates a new Access Token.

User does not need to log in again.

Usually expires in

7–30 Days

---

# 🏗 Authentication Flow

```
User

↓

Google Login

↓

Authorization Server

↓

Authorization Code

↓

Spring Boot

↓

Access Token

↓

Resource Server

↓

Protected API

↓

Response
```

---

# 📊 OAuth2 Roles

| Role | Responsibility |
|------|----------------|
| User | Resource Owner |
| Spring Boot | Client |
| Google | Authorization Server |
| API | Resource Server |

---

# 📊 Traditional Login vs OAuth2

| Traditional Login | OAuth2 |
|-------------------|---------|
| Password Stored | No Password Stored |
| Custom Login | Social Login |
| More Responsibility | Delegated Authentication |
| Hard to Maintain | Easy to Integrate |

---

# 🎤 Interview Questions

## Q1

What is OAuth2?

Answer

OAuth2 is an authorization framework that allows secure delegated access without sharing passwords.

---

## Q2

Why do companies use OAuth2?

Answer

To provide secure social login and delegated authorization.

---

## Q3

Who is the Resource Owner?

Answer

The User.

---

## Q4

Who is the Client?

Answer

The Spring Boot Application.

---

## Q5

What is an Access Token?

Answer

A token used to access protected resources.

---

## Q6

What is an Authorization Server?

Answer

A trusted provider that authenticates users and issues tokens.

Example

Google

GitHub

Microsoft

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| OAuth2 | Authorization Framework |
| Client | Spring Boot Application |
| Resource Owner | User |
| Authorization Server | Identity Provider |
| Resource Server | Protected API |
| Access Token | API Access Token |
| Refresh Token | Token Renewal |

---

# 💡 Pro Tips

> [!TIP]

Always use Authorization Code Flow for Spring Boot applications.

---

> [!IMPORTANT]

Never expose Client Secret in GitHub repositories.

Store secrets in environment variables or secure configuration.

---

# 🗣 English Practice

Read aloud

OAuth2 provides secure authorization.

Google is an Authorization Server.

Spring Boot acts as an OAuth2 Client.

Access Tokens allow secure API access.

---

# 🧩 Assignment

- [ ] Add OAuth2 Client dependency.
- [ ] Understand OAuth2 roles.
- [ ] Study Authorization Code Flow.
- [ ] Learn Access Token usage.
- [ ] Prepare project for Google Login.

---

# 🚀 GitHub Task

Commit Message

```text
feat: configure OAuth2 authentication
```

---

# ⭐ Today's Challenge

Without looking at notes

Explain

1. What is OAuth2?

2. Why is OAuth2 more secure than traditional login?

3. What are the four OAuth2 roles?

4. What is an Access Token?

5. Explain the Authorization Code Flow.

---

# 📌 Summary

✔ OAuth2 is an authorization framework.

✔ Users never share passwords with applications.

✔ Google, GitHub and Microsoft act as Authorization Servers.

✔ Spring Boot acts as the OAuth2 Client.

✔ Access Tokens provide secure access to APIs.

✔ OAuth2 is widely used for social login in enterprise applications.

---

# 🔗 Related Notes

- [[Day-33-Method-Level-Security]]
- [[Day-35-Google-OAuth2-Login]]
- [[JWT (JSON Web Token)]]
- [[Spring Security]]