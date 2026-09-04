

> **Module:** Spring Boot Security
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 26 – Spring Security Basics]]
>
> **Next:** [[📘 Day 28 – JWT (JSON Web Token)]]

---

# 🌟 Daily Motivation

> "Security is not a feature. It is a requirement."

---

# 🎯 Learning Objectives

Today you will learn

✅ UserDetails

✅ UserDetailsService

✅ GrantedAuthority

✅ Roles

✅ In-Memory Authentication

✅ Database Authentication

---

# 📖 Authentication

## Definition

Authentication verifies the identity of the user.

Example

```
Username

Password
```

↓

Spring Security

↓

Authenticated User

---

# 📖 Authorization

## Definition

Authorization checks what the authenticated user is allowed to access.

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

Read Employee
```

---

# 🇮🇳 Malayalam Explanation

Authentication

↓

"നിങ്ങൾ ആരാണ്?"

Authorization

↓

"നിങ്ങൾക്ക് എന്ത് ചെയ്യാൻ അനുവാദമുണ്ട്?"

---

# 🏢 Real Company Example

Employee Login

↓

Username

Password

↓

Authentication

↓

Role Check

↓

Dashboard

---

# 📖 UserDetails

UserDetails represents a logged-in user.

It stores

- Username
- Password
- Roles
- Account Status

---

# 💻 Example

```java
public class CustomUserDetails
        implements UserDetails {

}
```

---

# 📖 UserDetailsService

Loads user information.

```java
public interface UserDetailsService {

    UserDetails loadUserByUsername(
            String username);

}
```

---

# 💻 Example

```java
@Service
public class CustomUserDetailsService
        implements UserDetailsService {

    @Override
    public UserDetails loadUserByUsername(
            String username) {

        return User.builder()
                .username("admin")
                .password(passwordEncoder.encode("admin123"))
                .roles("ADMIN")
                .build();

    }

}
```

---

# 📖 GrantedAuthority

Represents user permissions.

Example

```
ROLE_ADMIN

ROLE_USER

ROLE_MANAGER
```

---

# 📖 Roles

ADMIN

↓

Create

Update

Delete

Read

---

USER

↓

Read Only

---

# 💻 In-Memory Authentication

```java
@Bean
public UserDetailsService users(){

    UserDetails admin =
            User.builder()
                    .username("admin")
                    .password(passwordEncoder().encode("admin123"))
                    .roles("ADMIN")
                    .build();

    return new InMemoryUserDetailsManager(admin);

}
```

---

# 💻 Database Authentication

```
Database

↓

User Entity

↓

UserRepository

↓

UserDetailsService

↓

Spring Security
```

---

# 📖 Security Configuration

```java
@Bean
public SecurityFilterChain securityFilterChain(
        HttpSecurity http)
        throws Exception {

    http
        .authorizeHttpRequests(auth -> auth
            .requestMatchers("/login")
            .permitAll()
            .requestMatchers("/admin/**")
            .hasRole("ADMIN")
            .requestMatchers("/employee/**")
            .hasAnyRole("USER","ADMIN")
            .anyRequest()
            .authenticated()
        )
        .formLogin();

    return http.build();

}
```

---

# 🏗 Authentication Flow

Client

↓

Login

↓

UserDetailsService

↓

Authentication

↓

Authorization

↓

Controller

↓

Response

---

# 📊 Authentication vs Authorization

| Authentication | Authorization |
|----------------|---------------|
| Who are you? | What can you access? |
| Login | Permission |
| Username & Password | Roles |

---

# 🎤 Interview Questions

## Q1

What is UserDetails?

Answer

It represents an authenticated user.

---

## Q2

What is UserDetailsService?

Answer

It loads user information during login.

---

## Q3

What is GrantedAuthority?

Answer

It represents roles and permissions.

---

## Q4

Difference between Authentication and Authorization?

Answer

Authentication verifies identity.

Authorization verifies permissions.

---

## Q5

What is InMemoryUserDetailsManager?

Answer

It stores users in memory for testing and development.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| Authentication | Identity Verification |
| Authorization | Permission Checking |
| UserDetails | Logged-in User |
| Role | User Permission |
| UserDetailsService | User Loader |

---

# 💡 Pro Tips

> [!TIP]

Use In-Memory Authentication only for development and learning.

---

> [!IMPORTANT]

Production applications should authenticate users from a database.

---

# 🗣 English Practice

Read aloud

Authentication verifies identity.

Authorization verifies permissions.

UserDetails stores user information.

Spring Security uses UserDetailsService.

---

# 🧩 Assignment

- [ ] Create CustomUserDetails.
- [ ] Create CustomUserDetailsService.
- [ ] Configure InMemoryUserDetailsManager.
- [ ] Create ADMIN and USER roles.
- [ ] Test role-based access.

---

# 🚀 GitHub Task

Commit Message

```
feat: implement Authentication and Authorization
```

---

# ⭐ Today's Challenge

Without looking at notes

Explain

1. What is Authentication?

2. What is Authorization?

3. What is UserDetails?

4. What is UserDetailsService?

5. What is GrantedAuthority?

---

# 📌 Summary

✔ Authentication verifies user identity.

✔ Authorization controls access based on roles.

✔ UserDetails represents the logged-in user.

✔ UserDetailsService loads user information.

✔ Roles determine what users can access.

✔ In-Memory Authentication is useful for development.