

> **Module:** Spring Security
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 29 – JWT Generation & Validation]]
>
> **Next:** [[📘 Day 31 – Refresh Token]]

---

# 🌟 Daily Motivation

> "A JWT token is useful only when every request is verified."

---

# 🎯 Learning Objectives

Today you will learn

✅ What is JWT Filter?

✅ OncePerRequestFilter

✅ Authorization Header

✅ Bearer Token

✅ SecurityContextHolder

✅ Authentication Flow

---

# 📖 What is JWT Authentication Filter?

## Definition

A JWT Authentication Filter intercepts every incoming HTTP request, extracts the JWT token, validates it, and authenticates the user.

---

# 🇮🇳 Malayalam Explanation

Client API Call ചെയ്യും

↓

JWT Filter

↓

Token ഉണ്ടോ?

↓

അതെ

↓

Token Valid ആണോ?

↓

അതെ

↓

User Authenticate ചെയ്യും

↓

Controller-ലേക്ക് Request പോകും

---

# 🏢 Real Company Example

React Application

↓

Authorization Header

↓

Bearer Token

↓

JWT Filter

↓

JwtService

↓

SecurityContext

↓

Controller

↓

JSON Response

---

# 📖 Why JWT Filter?

Without JWT Filter

❌ Anyone can access APIs

❌ Token is never checked

With JWT Filter

✔ Every request is verified

✔ Only authenticated users access protected APIs

---

# 📖 OncePerRequestFilter

`OncePerRequestFilter` ensures that the filter executes only once for each HTTP request.

```java
public class JwtAuthenticationFilter
        extends OncePerRequestFilter {

}
```

---

# 💻 Filter Skeleton

```java
@Component
@RequiredArgsConstructor
public class JwtAuthenticationFilter
        extends OncePerRequestFilter {

    private final JwtService jwtService;

    private final UserDetailsService userDetailsService;

}
```

---

# 📖 Authorization Header

```
Authorization

Bearer eyJhbGciOiJIUzI1NiJ9...
```

---

# 💻 Extract Bearer Token

```java
String authHeader =
        request.getHeader("Authorization");

if(authHeader == null ||
   !authHeader.startsWith("Bearer ")){

    filterChain.doFilter(request,response);

    return;

}
```

---

# 💻 Extract JWT

```java
String jwt =
        authHeader.substring(7);
```

---

# 💻 Extract Username

```java
String username =
        jwtService.extractUsername(jwt);
```

---

# 💻 Load User

```java
UserDetails userDetails =
        userDetailsService
                .loadUserByUsername(username);
```

---

# 💻 Validate Token

```java
if(jwtService.validateToken(jwt,userDetails)){

    // Authentication Success

}
```

---

# 📖 SecurityContextHolder

Stores authenticated user information.

```java
SecurityContextHolder
        .getContext()
        .setAuthentication(authentication);
```

After this,

Spring Security treats the user as authenticated.

---

# 🏗 JWT Filter Flow

```
Client

↓

Authorization Header

↓

JWT Filter

↓

Extract Token

↓

Validate Token

↓

Load User

↓

SecurityContext

↓

Controller

↓

Response
```

---

# 📖 Security Configuration

```java
http.addFilterBefore(
        jwtAuthenticationFilter,
        UsernamePasswordAuthenticationFilter.class
);
```

The JWT Filter executes before Spring Security's default authentication filter.

---

# 📊 Authentication Flow

| Step | Action |
|-------|--------|
| 1 | Login |
| 2 | JWT Generated |
| 3 | Client Stores Token |
| 4 | Bearer Token Sent |
| 5 | JWT Filter Validates |
| 6 | User Authenticated |
| 7 | Controller Executes |

---

# 🎤 Interview Questions

## Q1

What is JWT Authentication Filter?

Answer

A filter that validates JWT tokens for every incoming request.

---

## Q2

Why do we extend OncePerRequestFilter?

Answer

To ensure the filter executes only once per request.

---

## Q3

Where is JWT stored in a request?

Answer

Inside the Authorization header as a Bearer token.

---

## Q4

What is SecurityContextHolder?

Answer

It stores authentication information for the current request.

---

## Q5

Why do we add the JWT filter before UsernamePasswordAuthenticationFilter?

Answer

To authenticate JWT requests before Spring Security processes them.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| Filter | Request Interceptor |
| Bearer Token | JWT Token |
| SecurityContext | Logged-in User Context |
| Authentication | User Verification |
| OncePerRequestFilter | Executes Once Per Request |

---

# 💡 Pro Tips

> [!TIP]

Skip JWT validation for public endpoints such as:

- /login
- /register
- /actuator/health

---

> [!IMPORTANT]

Always validate:

✔ Signature

✔ Username

✔ Expiration

before authenticating the user.

---

# 🗣 English Practice

Read aloud

JWT Filter intercepts every request.

Bearer Token is sent in the Authorization header.

SecurityContext stores authentication information.

OncePerRequestFilter executes once per request.

---

# 🧩 Assignment

- [ ] Create JwtAuthenticationFilter.
- [ ] Extend OncePerRequestFilter.
- [ ] Extract Bearer Token.
- [ ] Validate JWT.
- [ ] Set SecurityContext.
- [ ] Register Filter in SecurityConfig.

---

# 🚀 GitHub Task

Commit Message

```
feat: implement JWT authentication filter
```

---

# ⭐ Today's Challenge

Without looking at notes

Explain

1. What is JWT Authentication Filter?

2. Why do we use OncePerRequestFilter?

3. What is SecurityContextHolder?

4. Where is the JWT stored?

5. Why is the filter added before UsernamePasswordAuthenticationFilter?

---

# 📌 Summary

✔ JWT Filter intercepts every request.

✔ JWT is read from the Authorization header.

✔ JwtService validates the token.

✔ SecurityContextHolder stores the authenticated user.

✔ Protected APIs become accessible only after successful JWT validation.
