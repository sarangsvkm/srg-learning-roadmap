

> **Module:** Spring Boot Backend Engineering
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 23 – Spring Boot Actuator]]
>
> **Next:** [[📘 Day 25 – Spring Boot Testing (JUnit 5 & Mockito)]]

---

# 🌟 Daily Motivation

> "The faster your development cycle, the faster you become a better developer."

---

# 🎯 Learning Objectives

Today you will learn

✅ What is Spring Boot DevTools?

✅ Automatic Restart

✅ LiveReload

✅ Development Productivity

✅ DevTools Configuration

---

# 📖 What is Spring Boot DevTools?

## Definition

Spring Boot DevTools is a development-time tool that automatically restarts the application whenever source code changes are detected.

It helps developers work faster.

---

# 🇮🇳 Malayalam Explanation

Code change ചെയ്താൽ

Application

Stop

↓

Run

ചെയ്യേണ്ട ആവശ്യമില്ല.

DevTools

Application automatically restart ചെയ്യും.

---

# 🏢 Real Company Example

Developer

↓

Changes Controller

↓

Save File

↓

Application Restarts Automatically

↓

Test API Again

---

# 📦 Maven Dependency

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-devtools</artifactId>
    <scope>runtime</scope>
    <optional>true</optional>
</dependency>
```

---

# 📖 Features

✅ Automatic Restart

✅ LiveReload

✅ Faster Development

✅ Better Productivity

---

# 📖 Automatic Restart

Without DevTools

```
Code Change

↓

Stop Application

↓

Run Again
```

With DevTools

```
Code Change

↓

Save File

↓

Automatic Restart
```

---

# 📖 LiveReload

Automatically refreshes the browser after changes.

Useful for

- Thymeleaf
- HTML
- CSS
- JavaScript

---

# 📖 application.properties

```properties
spring.devtools.restart.enabled=true

spring.devtools.livereload.enabled=true
```

---

# 📖 Restart Exclude

```properties
spring.devtools.restart.exclude=static/**,public/**
```

---

# 📖 Disable Restart

```properties
spring.devtools.restart.enabled=false
```

---

# 🏗 Development Flow

Developer

↓

Edit Code

↓

Save File

↓

DevTools Detects Change

↓

Application Restart

↓

Ready to Test

---

# 📊 Advantages

| Without DevTools | With DevTools |
|------------------|---------------|
| Manual Restart | Automatic Restart |
| Slow Development | Faster Development |
| Time Consuming | Saves Time |
| Less Productive | More Productive |

---

# 🎤 Interview Questions

## Q1

What is Spring Boot DevTools?

Answer

It is a development tool that automatically restarts the application when code changes are detected.

---

## Q2

Why do we use DevTools?

Answer

To speed up development by avoiding manual restarts.

---

## Q3

What is LiveReload?

Answer

LiveReload refreshes the browser automatically after changes.

---

## Q4

Should DevTools be used in production?

Answer

No.

DevTools is only for development.

---

## Q5

Which dependency enables DevTools?

Answer

spring-boot-devtools

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| DevTools | Development Tool |
| Restart | Restart Application |
| LiveReload | Auto Refresh Browser |
| Productivity | Work Efficiency |
| Runtime | Execution Time |

---

# 💡 Pro Tips

> [!TIP]

Use DevTools only during development.

---

> [!IMPORTANT]

Do not package DevTools with your production application.

---

# 🗣 English Practice

Read aloud

DevTools improves development speed.

DevTools automatically restarts the application.

LiveReload refreshes the browser.

---

# 🧩 Assignment

- [ ] Add DevTools dependency.
- [ ] Enable automatic restart.
- [ ] Modify EmployeeController.
- [ ] Save the file.
- [ ] Observe automatic restart.

---

# 🚀 GitHub Task

Commit Message

```
feat: add Spring Boot DevTools
```

---

# ⭐ Today's Challenge

Without looking at notes

Explain

1. What is DevTools?

2. Why do we use DevTools?

3. What is Automatic Restart?

4. What is LiveReload?

5. Why shouldn't DevTools be used in production?

---

# 📌 Summary

✔ DevTools speeds up development.

✔ It automatically restarts the application.

✔ LiveReload refreshes the browser.

✔ It improves developer productivity.

✔ DevTools should only be used in development.