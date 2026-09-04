

> **Module:** Spring Security
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 28 – JWT (JSON Web Token)]]
>
> **Next:** [[📘 Day 30 – JWT Authentication Filter]]

---

# 🌟 Daily Motivation

> "A secure token is the key that unlocks your protected APIs."

---

# 🎯 Learning Objectives

Today you will learn

✅ JWT Generation

✅ JWT Validation

✅ Secret Key

✅ Expiration Time

✅ Extract Username

✅ JwtService

---

# 📖 JWT Authentication Flow

```
Client

↓

Login

↓

AuthenticationManager

↓

Generate JWT

↓

Return Token

↓

Client Stores Token

↓

Authorization Header

↓

Validate JWT

↓

Protected API Access
```

---

# 📖 What is JwtService?

## Definition

JwtService is responsible for

✔ Generating JWT

✔ Validating JWT

✔ Extracting Username

✔ Checking Token Expiration

---

# 🇮🇳 Malayalam Explanation

JwtService

↓

Create Token

↓

Verify Token

↓

Read Username

↓

Check Expiry

↓

Return Result

---

# 📦 Maven Dependencies

```xml
<dependency>
    <groupId>io.jsonwebtoken</groupId>
    <artifactId>jjwt-api</artifactId>
    <version>0.12.6</version>
</dependency>

<dependency>
    <groupId>io.jsonwebtoken</groupId>
    <artifactId>jjwt-impl</artifactId>
    <version>0.12.6</version>
    <scope>runtime</scope>
</dependency>

<dependency>
    <groupId>io.jsonwebtoken</groupId>
    <artifactId>jjwt-jackson</artifactId>
    <version>0.12.6</version>
    <scope>runtime</scope>
</dependency>
```

---

# 📖 Secret Key

application.properties

```properties
jwt.secret=your-very-secure-secret-key
jwt.expiration=86400000
```

86400000 ms = 24 Hours

---

# 💻 Generate Secret Key

```java
private final String SECRET =
        "your-very-secure-secret-key";
```

Production applications should use a strong secret key from configuration or environment variables.

---

# 💻 Generate JWT

```java
String token =
        Jwts.builder()
                .subject(username)
                .issuedAt(new Date())
                .expiration(new Date(
                        System.currentTimeMillis()
                                + 86400000))
                .signWith(secretKey)
                .compact();
```

---

# 📖 Generated Token

```
eyJhbGciOiJIUzI1NiJ9

.

eyJzdWIiOiJhZG1pbiJ9

.

abcXYZ123...
```

---

# 💻 Extract Username

```java
String username =
        Jwts.parser()
                .verifyWith(secretKey)
                .build()
                .parseSignedClaims(token)
                .getPayload()
                .getSubject();
```

---

# 💻 Validate JWT

```java
public boolean isTokenValid(
        String token,
        UserDetails userDetails){

    String username =
            extractUsername(token);

    return username.equals(
            userDetails.getUsername()
    ) && !isTokenExpired(token);

}
```

---

# 💻 Check Expiration

```java
public boolean isTokenExpired(
        String token){

    return extractExpiration(token)
            .before(new Date());

}
```

---

# 🏗 Complete Flow

```
Login Request

↓

Authentication

↓

Generate JWT

↓

Client Stores Token

↓

Authorization Header

↓

JwtService

↓

Validate Token

↓

Controller

↓

Response
```

---

# 📊 JwtService Responsibilities

| Method | Purpose |
|----------|----------|
| generateToken() | Create JWT |
| validateToken() | Verify JWT |
| extractUsername() | Read Username |
| isTokenExpired() | Check Expiry |

---

# 🎤 Interview Questions

## Q1

What is JwtService?

Answer

A service responsible for generating and validating JWT tokens.

---

## Q2

Where is JWT stored?

Answer

Usually on the client side (browser, mobile app, etc.).

---

## Q3

What is the purpose of the Secret Key?

Answer

It signs and verifies JWT tokens.

---

## Q4

Why do JWTs have an expiration time?

Answer

To reduce the risk of misuse if a token is stolen.

---

## Q5

Can JWT be modified by the client?

Answer

No.

Any modification invalidates the token signature.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| JWT | JSON Web Token |
| Secret Key | Signing Key |
| Subject | Username |
| Expiration | Token Expiry |
| Claims | User Information |

---

# 💡 Pro Tips

> [!TIP]

Always set an expiration time for JWT tokens.

---

> [!IMPORTANT]

Never commit your JWT secret key to GitHub.

Use environment variables or secure configuration.

---

# 🗣 English Practice

Read aloud

JWT tokens are digitally signed.

JwtService generates and validates tokens.

The Authorization header contains the Bearer token.

Expired tokens should be rejected.

---

# 🧩 Assignment

- [ ] Add JJWT dependencies.
- [ ] Create JwtService.
- [ ] Generate a JWT token.
- [ ] Extract username from JWT.
- [ ] Validate JWT.
- [ ] Test token expiration.

---

# 🚀 GitHub Task

Commit Message

```
feat: implement JWT generation and validation
```

---

# ⭐ Today's Challenge

Without looking at notes

Explain

1. What is JwtService?

2. How is a JWT generated?

3. How do you validate a JWT?

4. Why do JWTs expire?

5. Why is the secret key important?

---

# 📌 Summary

✔ JwtService generates JWT tokens.

✔ JwtService validates incoming tokens.

✔ JWT contains username inside its claims.

✔ Secret Key signs and verifies JWT.

✔ Expired tokens should never be accepted.

✔ JWT is the foundation of secure REST API authentication.