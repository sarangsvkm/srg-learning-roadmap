# 📘 Day 31 – Refresh Token

> **Module:** Spring Security
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 30 – JWT Authentication Filter]]
> 
> **Next:** [[📘 Day 32 – Role-Based Authorization]]]

---

# 🌟 Daily Motivation

> "A secure authentication system doesn't just issue tokens—it manages their lifecycle."

---

# 🎯 Learning Objectives

Today you will learn

✅ What is a Refresh Token?

✅ Access Token vs Refresh Token

✅ Token Expiration

✅ Refresh Token API

✅ Token Rotation

✅ Logout & Token Revocation

---

# 📖 What is a Refresh Token?

## Definition

A Refresh Token is a long-lived token used to generate a new Access Token without asking the user to log in again.

---

# 🇮🇳 Malayalam Explanation

User Login ചെയ്യും

↓

Server

↓

Access Token

+

Refresh Token

↓

Access Token Expire ആകും

↓

Refresh Token ഉപയോഗിച്ച്

പുതിയ Access Token ലഭിക്കും

↓

User വീണ്ടും Login ചെയ്യേണ്ടതില്ല.

---

# 🏢 Real Company Example

React App

↓

Login

↓

Access Token (15 Minutes)

↓

Refresh Token (7 Days)

↓

Access Token Expired

↓

Refresh API

↓

New Access Token

↓

Continue Using App

---

# 📖 Access Token

Purpose

- Access Protected APIs

Lifetime

- Short (15–30 Minutes)

---

# 📖 Refresh Token

Purpose

- Generate New Access Token

Lifetime

- Long (7–30 Days)

---

# 📊 Access Token vs Refresh Token

| Access Token | Refresh Token |
|--------------|---------------|
| Short Lifetime | Long Lifetime |
| Used for API Requests | Used to get a new Access Token |
| Expires Quickly | Expires Later |

---

# 🏗 Authentication Flow

```
User Login

↓

Access Token

+

Refresh Token

↓

API Request

↓

Access Token Valid

↓

Response

↓

Access Token Expired

↓

Refresh API

↓

New Access Token

↓

Continue
```

---

# 💻 Login Response

```json
{
  "accessToken":"eyJhbGciOiJIUzI1NiJ9...",
  "refreshToken":"eyJhbGciOiJIUzI1NiJ9..."
}
```

---

# 💻 Refresh API

```
POST

/api/auth/refresh
```

Request

```json
{
   "refreshToken":"eyJhbGc..."
}
```

Response

```json
{
   "accessToken":"new-access-token"
}
```

---

# 📖 Token Rotation

Instead of reusing the same Refresh Token,

Generate

✔ New Access Token

✔ New Refresh Token

Old Refresh Token becomes invalid.

---

# 📖 Logout

On Logout

- Delete Refresh Token
- Reject old tokens
- Clear Security Context

---

# 📖 Best Practices

✔ Access Token → 15–30 Minutes

✔ Refresh Token → 7–30 Days

✔ Store Refresh Tokens securely

✔ Revoke Refresh Token during logout

---

# 🏗 Complete Flow

```
Login

↓

Access Token

↓

API Request

↓

Expired

↓

Refresh Token

↓

New Access Token

↓

Protected API
```

---

# 🎤 Interview Questions

## Q1

What is a Refresh Token?

Answer

A long-lived token used to generate a new Access Token.

---

## Q2

Why do we use Refresh Tokens?

Answer

To avoid asking users to log in again after the Access Token expires.

---

## Q3

Which token is sent with API requests?

Answer

Access Token.

---

## Q4

What is Token Rotation?

Answer

Generating a new Refresh Token whenever a new Access Token is issued.

---

## Q5

What should happen during logout?

Answer

Refresh Tokens should be revoked or deleted so they cannot be reused.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| Access Token | API Authentication Token |
| Refresh Token | Token Renewal Token |
| Expiration | Token Lifetime |
| Rotation | Replace Old Token |
| Revocation | Invalidate Token |

---

# 💡 Pro Tips

> [!TIP]

Keep Access Tokens short-lived and Refresh Tokens securely stored.

---

> [!IMPORTANT]

Never expose Refresh Tokens in URLs or logs. Store them securely and invalidate them during logout.

---

# 🗣 English Practice

Read aloud

Access Tokens authenticate API requests.

Refresh Tokens generate new Access Tokens.

Token Rotation improves security.

Logout revokes Refresh Tokens.

---

# 🧩 Assignment

- [ ] Create RefreshToken entity.
- [ ] Generate Access and Refresh Tokens.
- [ ] Create `/api/auth/refresh` endpoint.
- [ ] Implement Token Rotation.
- [ ] Test token refresh using Postman.

---

# 🚀 GitHub Task

Commit Message

```
feat: implement Refresh Token authentication
```

---

# ⭐ Today's Challenge

Without looking at notes

Explain

1. What is a Refresh Token?

2. Difference between Access Token and Refresh Token?

3. What happens when an Access Token expires?

4. What is Token Rotation?

5. Why should Refresh Tokens be revoked during logout?

---

# 📌 Summary

✔ Access Tokens are used for API authentication.

✔ Refresh Tokens generate new Access Tokens.

✔ Access Tokens should have a short lifetime.

✔ Refresh Tokens should be stored securely.

✔ Token Rotation improves security.

✔ Logout should invalidate Refresh Tokens.