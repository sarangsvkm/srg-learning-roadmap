
> **Module:** Spring Boot Backend Engineering
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 35 - Google OAuth2 Login]]]
>
> **Next:** [[📘 Day 37 – Facebook OAuth2 Login]]

---

# 🌟 Daily Motivation

> "Developers trust GitHub. Your application should too."

---

# 🎯 Learning Objectives

Today you will learn

- ✅ GitHub OAuth2 Login
- ✅ GitHub Developer Settings
- ✅ OAuth App
- ✅ Client ID
- ✅ Client Secret
- ✅ Redirect URI
- ✅ Spring Security Configuration
- ✅ GitHub OAuth2 Flow

---

# 📖 What is GitHub OAuth2 Login?

GitHub OAuth2 Login allows users to sign in using their GitHub account instead of creating a new username and password.

It is widely used in developer platforms and SaaS applications.

---

# 🇮🇳 Malayalam Explanation

User

↓

Click **Continue with GitHub**

↓

GitHub Login Page

↓

User Login

↓

GitHub verifies the user

↓

Spring Boot receives user information

↓

User enters the application

---

# 🤔 Why GitHub OAuth2?

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

- Password Management
- Forgot Password
- Security Risks

---

GitHub OAuth2 Login

```
User

↓

GitHub Login

↓

GitHub Authentication

↓

Spring Boot

↓

Dashboard
```

Advantages

✔ Secure Login

✔ No Password Storage

✔ Trusted Authentication

✔ Quick Registration

---

# 🏢 Real Company Examples

Developer Platforms

- Docker Hub
- Vercel
- Netlify
- Railway
- Render
- DigitalOcean
- Supabase

All support GitHub Login.

---

# 📦 Maven Dependency

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-oauth2-client</artifactId>
</dependency>
```

---

# 📖 GitHub OAuth App

GitHub

↓

Settings

↓

Developer Settings

↓

OAuth Apps

↓

New OAuth App

Generate

- Client ID
- Client Secret

---

# 📖 application.yml

```yaml
spring:
  security:
    oauth2:
      client:
        registration:
          github:
            client-id: YOUR_CLIENT_ID
            client-secret: YOUR_CLIENT_SECRET
```

---

# 📖 Redirect URI

```
http://localhost:8080/login/oauth2/code/github
```

GitHub redirects the user to this URL after successful authentication.

---

# 🏗 GitHub OAuth2 Flow

```
User

↓

Click Login with GitHub

↓

GitHub Login

↓

Authentication

↓

Authorization Code

↓

Spring Security

↓

Access Token

↓

GitHub User Profile

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

GitHub returns

- Username
- Name
- Email
- Avatar URL
- GitHub ID

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

# 📊 Google vs GitHub OAuth2

| Google | GitHub |
|---------|---------|
| Google Account | GitHub Account |
| Gmail Profile | Developer Profile |
| Social Login | Developer Login |
| Email & Profile | Username & Repository Access |

---

# 📊 Traditional Login vs GitHub OAuth2

| Traditional Login | GitHub OAuth2 |
|-------------------|---------------|
| Username & Password | GitHub Account |
| Password Stored | No Password Stored |
| Manual Registration | One Click Login |
| More Security Risk | More Secure |

---

# 🎤 Interview Questions

## Q1

What is GitHub OAuth2 Login?

**Answer**

It allows users to authenticate using their GitHub account.

---

## Q2

Where do we create OAuth credentials?

**Answer**

GitHub Developer Settings → OAuth Apps

---

## Q3

What credentials are required?

**Answer**

- Client ID
- Client Secret

---

## Q4

What is Redirect URI?

**Answer**

The callback URL that GitHub redirects to after successful authentication.

---

## Q5

What object contains the authenticated user?

**Answer**

OAuth2User

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| OAuth App | Registered Application |
| Client ID | Application Identifier |
| Client Secret | Application Secret |
| Redirect URI | Callback URL |
| OAuth2User | Authenticated User |

---

# 💡 Pro Tips

> [!TIP]

Use GitHub OAuth2 for developer-focused applications.

---

> [!IMPORTANT]

Never expose your Client Secret in public repositories.

Use environment variables for production.

---

# 🗣 English Practice

Read aloud

GitHub OAuth2 provides secure authentication.

Spring Security supports GitHub Login.

OAuth2User contains authenticated user information.

---

# 🧩 Assignment

- [ ] Create a GitHub OAuth App.
- [ ] Generate Client ID.
- [ ] Generate Client Secret.
- [ ] Configure application.yml.
- [ ] Test GitHub Login.
- [ ] Display GitHub username and email.

---

# 🚀 GitHub Task

```text
feat: implement GitHub OAuth2 login
```

---

# 📌 Summary

✔ GitHub OAuth2 provides secure authentication.

✔ Spring Security supports GitHub Login.

✔ OAuth2User stores authenticated user information.

✔ Client ID and Client Secret identify the application.

✔ Redirect URI receives the authentication response.

---

# 🔗 Related Notes

- [[📘 Day 35 – Google OAuth2 Login]]
- [[📘 Day 37 – Facebook OAuth2 Login]]
- [[📘 Day 34 – OAuth2 Introduction]]
- [[📘 Day 26 – Spring Security Basics]]