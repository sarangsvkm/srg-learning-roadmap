# 📘 Day 37 – Facebook OAuth2 Login

> **Module:** Spring Boot Backend Engineering
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 36 – GitHub OAuth2 Login]]
>
> **Next:** [[📘 Day 38 – Email Verification]]

---

# 🌟 Daily Motivation

> "Authentication should be simple for users and secure for developers."

---

# 🎯 Learning Objectives

Today you will learn

- ✅ Facebook OAuth2 Login
- ✅ Meta for Developers
- ✅ Facebook App Creation
- ✅ App ID
- ✅ App Secret
- ✅ Redirect URI
- ✅ Spring Security Configuration
- ✅ Facebook OAuth2 Flow

---

# 📖 What is Facebook OAuth2 Login?

Facebook OAuth2 Login allows users to sign in using their Facebook account instead of creating a new account for your application.

It provides a fast and secure authentication process.

---

# 🇮🇳 Malayalam Explanation

User

↓

Click **Continue with Facebook**

↓

Facebook Login Page

↓

User Login

↓

Facebook verifies the user

↓

Spring Boot receives user information

↓

User enters the application

---

# 🤔 Why Facebook OAuth2?

Traditional Login

```
User

↓

Username

↓

Password

↓

Database
```

Problems

- Password Storage
- Forgot Password
- Security Risks

---

Facebook OAuth2 Login

```
User

↓

Facebook Login

↓

Facebook Authentication

↓

Spring Boot

↓

Dashboard
```

Advantages

✔ Secure Authentication

✔ No Password Storage

✔ Faster Registration

✔ Trusted Login

---

# 🏢 Real Company Examples

Many applications support Facebook Login

- Spotify
- Pinterest
- Airbnb
- Canva
- Duolingo
- PUBG Mobile

---

# 📦 Maven Dependency

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-oauth2-client</artifactId>
</dependency>
```

---

# 📖 Meta for Developers

Go to

Meta for Developers

↓

Create App

↓

Choose

Consumer App

↓

Add Facebook Login

↓

Generate

- App ID
- App Secret

---

# 📖 application.yml

```yaml
spring:
  security:
    oauth2:
      client:
        registration:
          facebook:
            client-id: YOUR_APP_ID
            client-secret: YOUR_APP_SECRET
```

---

# 📖 Redirect URI

```
http://localhost:8080/login/oauth2/code/facebook
```

Facebook redirects users to this URL after successful login.

---

# 🏗 Facebook OAuth2 Login Flow

```
User

↓

Click Login with Facebook

↓

Facebook Login

↓

Authentication

↓

Authorization Code

↓

Spring Security

↓

Access Token

↓

Facebook User Profile

↓

Dashboard
```

---

# 📖 OAuth2User

After successful login

Spring Security creates

```
OAuth2User
```

Example

```java
@GetMapping("/profile")
public OAuth2User profile(
        @AuthenticationPrincipal OAuth2User user){

    return user;

}
```

---

# 📖 User Information

Facebook returns

- Name
- Email
- Facebook ID
- Profile Picture

---

# 📖 Authentication Success Handler

```java
@Bean
AuthenticationSuccessHandler successHandler(){

    return (request,response,authentication)->{

        response.sendRedirect("/dashboard");

    };

}
```

---

# 📖 Logout

```java
http.logout(logout ->
    logout.logoutSuccessUrl("/")
);
```

---

# 📊 Google vs GitHub vs Facebook

| Google | GitHub | Facebook |
|---------|---------|-----------|
| Gmail Account | GitHub Account | Facebook Account |
| General Users | Developers | Social Users |
| Email & Profile | Developer Profile | Social Profile |

---

# 📊 Traditional Login vs Facebook OAuth2

| Traditional Login | Facebook OAuth2 |
|-------------------|-----------------|
| Username & Password | Facebook Account |
| Password Stored | No Password Stored |
| Manual Registration | One Click Login |
| More Security Risk | More Secure |

---

# 🎤 Interview Questions

## Q1

What is Facebook OAuth2 Login?

**Answer**

It allows users to authenticate using their Facebook account.

---

## Q2

Where do we create Facebook OAuth credentials?

**Answer**

Meta for Developers Portal.

---

## Q3

What credentials are required?

**Answer**

- App ID
- App Secret

---

## Q4

What is Redirect URI?

**Answer**

The callback URL where Facebook redirects the user after successful authentication.

---

## Q5

What object stores the authenticated user?

**Answer**

OAuth2User

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| App ID | Application Identifier |
| App Secret | Application Secret |
| OAuth2User | Authenticated User |
| Redirect URI | Callback URL |
| Access Token | Authentication Token |

---

# 💡 Pro Tips

> [!TIP]

Always request only the permissions your application actually needs.

---

> [!IMPORTANT]

Never expose your App Secret in GitHub or public repositories.

Store secrets securely using environment variables.

---

# 🗣 English Practice

Read aloud

Facebook OAuth2 provides secure authentication.

Spring Security supports Facebook Login.

OAuth2User contains authenticated user information.

---

# 🧩 Assignment

- [ ] Create a Meta Developer account.
- [ ] Create a Facebook App.
- [ ] Generate App ID.
- [ ] Generate App Secret.
- [ ] Configure application.yml.
- [ ] Test Facebook Login.
- [ ] Display Facebook user information.

---

# 🚀 GitHub Task

```text
feat: implement Facebook OAuth2 login
```

---

# 📌 Summary

✔ Facebook OAuth2 enables secure authentication.

✔ Spring Security integrates Facebook Login.

✔ OAuth2User stores authenticated user information.

✔ App ID and App Secret identify the application.

✔ Redirect URI receives the authentication response.

---

# 🔗 Related Notes

- [[📘 Day 36 – GitHub OAuth2 Login]]
- [[📘 Day 38 – Email Verification]]
- [[📘 Day 34 – OAuth2 Introduction]]
- [[📘 Day 26 – Spring Security Basics]]