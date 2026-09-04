

> **Module:** Spring Boot Backend Engineering
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 37 – Facebook OAuth2 Login]]
>
> **Next:** [[📘 Day 39 – Password Reset]]

---

# 🌟 Daily Motivation

> "A verified email builds trust, improves security, and protects user accounts."

---

# 🎯 Learning Objectives

Today you will learn

- ✅ What is Email Verification?
- ✅ Why Email Verification?
- ✅ Email Verification Flow
- ✅ Verification Token
- ✅ Java Mail Sender
- ✅ Spring Boot Email Configuration
- ✅ Verify User Account
- ✅ Best Practices

---

# 📖 What is Email Verification?

Email Verification is the process of confirming that a user owns the email address used during registration.

After registration, the application sends a verification email containing a unique link or token.

The user clicks the link to activate the account.

---

# 🇮🇳 Malayalam Explanation

User Register ചെയ്യുന്നു

↓

Application Email അയക്കും

↓

User Email Open ചെയ്യും

↓

Verification Link Click ചെയ്യും

↓

Account Verified

↓

Login ചെയ്യാം

---

# 🤔 Why Email Verification?

Without Email Verification

```
User

↓

Fake Email

↓

Account Created
```

Problems

- Fake Accounts
- Spam Users
- Invalid Email Addresses

---

With Email Verification

```
User

↓

Register

↓

Verification Email

↓

Verify Email

↓

Account Activated
```

Advantages

✔ Valid Email Address

✔ Better Security

✔ Prevent Fake Accounts

✔ Trusted Users

---

# 🏢 Real Company Examples

Applications using Email Verification

- Gmail
- Amazon
- Flipkart
- GitHub
- LinkedIn
- Facebook

---

# 🏗 Email Verification Flow

```
User Registration

↓

Save User

↓

Generate Verification Token

↓

Send Email

↓

User Clicks Link

↓

Verify Token

↓

Activate Account

↓

Login
```

---

# 📖 Verification Token

Each user receives a unique verification token.

Example

```
9d3fa2b7-7a81-4a22-a52d-ef91d1c7a342
```

This token is stored in the database.

---

# 📦 Maven Dependency

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-mail</artifactId>
</dependency>
```

---

# 📖 application.yml

```yaml
spring:
  mail:
    host: smtp.gmail.com
    port: 587
    username: your_email@gmail.com
    password: your_app_password

    properties:
      mail:
        smtp:
          auth: true
          starttls:
            enable: true
```

---

# 📖 Sending Email

```java
SimpleMailMessage message = new SimpleMailMessage();

message.setTo(user.getEmail());

message.setSubject("Verify Your Email");

message.setText(
        "Click the verification link.");

mailSender.send(message);
```

---

# 📖 Verification Link

```
http://localhost:8080/api/auth/verify?token=abc123xyz
```

---

# 📖 Verification API

```java
@GetMapping("/verify")
public String verifyEmail(
        @RequestParam String token){

    return authService.verifyEmail(token);

}
```

---

# 📖 Database Design

User Table

| Column | Description |
|---------|-------------|
| id | User ID |
| name | User Name |
| email | User Email |
| password | Password |
| enabled | Email Verified |

---

Verification Token Table

| Column | Description |
|---------|-------------|
| id | Token ID |
| token | Verification Token |
| user_id | User Reference |
| expiry_date | Expiration Time |

---

# 🏗 Complete Flow

```
User

↓

Register

↓

Database

↓

Generate Token

↓

Send Email

↓

User Clicks Link

↓

Verify Token

↓

Enable Account

↓

Login
```

---

# 🎤 Interview Questions

## Q1

What is Email Verification?

**Answer**

It confirms that a user owns the registered email address before activating the account.

---

## Q2

Why is Email Verification important?

**Answer**

It prevents fake registrations and ensures valid email addresses.

---

## Q3

What is a Verification Token?

**Answer**

A unique token sent to the user's email to verify ownership.

---

## Q4

Which Spring Boot dependency is used for sending emails?

**Answer**

spring-boot-starter-mail

---

## Q5

What happens after successful verification?

**Answer**

The user's account is activated, allowing login.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| SMTP | Simple Mail Transfer Protocol |
| Verification | Confirm Ownership |
| Token | Unique Identifier |
| Mail Sender | Email Service |
| Activation | Enable Account |

---

# 💡 Pro Tips

> [!TIP]

Always set an expiration time for verification tokens.

---

> [!IMPORTANT]

Never activate a user account before email verification is completed.

---

# 🗣 English Practice

Read aloud

Email verification confirms user identity.

Verification tokens activate user accounts.

Spring Boot can send emails using Java Mail Sender.

---

# 🧩 Assignment

- [ ] Configure Gmail SMTP.
- [ ] Add Java Mail dependency.
- [ ] Generate verification token.
- [ ] Send verification email.
- [ ] Create verification API.
- [ ] Activate user account after verification.

---

# 🚀 GitHub Task

```text
feat: implement email verification
```

---

# 📌 Summary

✔ Email Verification confirms user ownership.

✔ Verification links activate user accounts.

✔ Java Mail Sender sends verification emails.

✔ Verification tokens improve application security.

✔ Verified users can log in safely.

---

# 🔗 Related Notes

- [[📘 Day 37 – Facebook OAuth2 Login]]
- [[📘 Day 39 – Password Reset]]
- [[📘 Day 26 – Spring Security Basics]]
- [[📘 Day 28 – JWT Introduction]]