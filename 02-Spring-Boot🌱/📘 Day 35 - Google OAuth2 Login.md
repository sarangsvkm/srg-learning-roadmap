
> **Module:** Spring Security
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 34 - OAuth2-Introduction]]]
>
> **Next:** [[📘 Day 36 – GitHub OAuth2 Login]]

---

# 🌟 Daily Motivation

> "Secure authentication begins with trusted identity providers."

---

# 🎯 Learning Objectives

Today you will learn

- ✅ Google OAuth2 Login
- ✅ Google Cloud Console
- ✅ OAuth Client ID
- ✅ Client Secret
- ✅ Redirect URI
- ✅ Spring Security OAuth2 Configuration
- ✅ Login Flow

---

# 📖 What is Google OAuth2 Login?

Google OAuth2 Login allows users to authenticate using their Google account without creating a separate username and password for your application.

---

# 🇮🇳 Malayalam Explanation

User

↓

Click **Continue with Google**

↓

Google Login Page

↓

User Login

↓

Google verifies the user

↓

Spring Boot receives User Information

↓

User logs into the application

---

# 🏢 Real Company Examples

- Gmail
- YouTube
- Notion
- Canva
- Trello
- Slack

All support **Continue with Google**.

---

# 📦 Required Dependency

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-oauth2-client</artifactId>
</dependency>
```

---

# 📖 Google Cloud Console

Create a project.

↓

Enable

```
Google Identity Services
```

↓

Create

```
OAuth 2.0 Client ID
```

↓

Get

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
          google:
            client-id: YOUR_CLIENT_ID
            client-secret: YOUR_CLIENT_SECRET
            scope:
              - profile
              - email
```

---

# 📖 Redirect URI

Example

```
http://localhost:8080/login/oauth2/code/google
```

After successful login,

Google redirects the user to this URL.

---

# 🏗 Login Flow

```
User

↓

Click Login with Google

↓

Google Login

↓

Google Authentication

↓

Authorization Code

↓

Spring Security

↓

Access Token

↓

User Profile

↓

Dashboard
```

---

# 📖 OAuth2User

Spring Security stores the logged-in user as an `OAuth2User`.

Example

```java
@GetMapping("/profile")
public OAuth2User profile(
        @AuthenticationPrincipal OAuth2User user) {

    return user;

}
```

---

# 📖 User Information

Google returns

- Name
- Email
- Profile Picture
- Google ID
- Locale

---

# 📖 OAuth2 Success Handler

```java
@Bean
public AuthenticationSuccessHandler successHandler() {

    return (request, response, authentication) -> {

        response.sendRedirect("/dashboard");

    };

}
```

---

# 📖 Logout

```java
http.logout(logout ->
        logout.logoutSuccessUrl("/"));
```

---

# 📊 Login Comparison

| Traditional Login | Google OAuth2 Login |
|-------------------|---------------------|
| Username & Password | Google Account |
| Password Stored | No Password Stored |
| Manual Registration | One Click Login |
| Higher Risk | More Secure |

---

# 🎤 Interview Questions

## Q1

What is Google OAuth2 Login?

**Answer**

A secure authentication mechanism that allows users to sign in using their Google account.

---

## Q2

What credentials are required?

**Answer**

- Client ID
- Client Secret

---

## Q3

What is Redirect URI?

**Answer**

The URL where Google sends the user after successful authentication.

---

## Q4

What object contains the logged-in user?

**Answer**

`OAuth2User`

---

## Q5

Where are Client ID and Client Secret configured?

**Answer**

`application.yml` or `application.properties`

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| OAuth Client | Registered Application |
| Client ID | Application Identifier |
| Client Secret | Application Secret |
| Redirect URI | Callback URL |
| OAuth2User | Logged-in User |

---

# 💡 Pro Tips

> [!TIP]

Never commit your Client Secret to GitHub.

---

> [!IMPORTANT]

Always use HTTPS in production for OAuth2 callbacks.

---

# 🗣 English Practice

Read aloud

Google OAuth2 provides secure authentication.

Spring Security supports OAuth2 login.

OAuth2User contains the authenticated user's profile.

---

# 🧩 Assignment

- [ ] Create a Google Cloud Project.
- [ ] Generate Client ID.
- [ ] Generate Client Secret.
- [ ] Configure application.yml.
- [ ] Test Google Login.
- [ ] Display logged-in user's name and email.

---

# 🚀 GitHub Task

```text
feat: implement Google OAuth2 login
```

---

# 📌 Summary

✔ Google OAuth2 enables secure login.

✔ Spring Security integrates OAuth2 easily.

✔ Client ID and Client Secret identify the application.

✔ OAuth2User stores authenticated user details.

✔ Redirect URI receives the authentication response.

---

# 🔗 Related Notes

- [[Day-34-OAuth2-Introduction]]
- [[Day-36-GitHub-OAuth2-Login]]
- [[Day-28-JWT-Introduction]]
- [[Day-26-Spring-Security-Basics]]