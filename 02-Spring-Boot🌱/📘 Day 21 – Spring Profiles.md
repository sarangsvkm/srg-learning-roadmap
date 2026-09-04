

> **Module:** Spring Boot Backend Engineering
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 20 – Logging with SLF4J & Logback]]
>
> **Next:** [[📘 Day 22 – @ConfigurationProperties]]

---

# 🌟 Daily Motivation

> "One application, multiple environments. That's the power of Spring Profiles."

---

# 🎯 Learning Objectives

Today you will learn

✅ What are Spring Profiles?

✅ Why use Profiles?

✅ Development Environment

✅ Testing Environment

✅ Production Environment

✅ @Profile Annotation

✅ Active Profile

---

# 📖 What is Spring Profile?

## Definition

A Spring Profile is a way to configure an application differently for different environments.

Each environment can have its own configuration.

---

# 🇮🇳 Malayalam Explanation

ഒരു Application

Development

Testing

Production

എന്നിങ്ങനെ പല Environment-ൽ run ചെയ്യും.

ഓരോ Environment-നും വേറെ configuration വേണം.

അതിന് ഉപയോഗിക്കുന്നത്

Spring Profiles

ആണ്.

---

# 🏢 Real Company Example

Development

↓

Local PostgreSQL

↓

Debug Logging

---

Testing

↓

Test Database

↓

Test API Keys

---

Production

↓

Production Database

↓

Real API Keys

↓

Minimal Logging

---

# 📁 Configuration Files

```
application.properties

application-dev.properties

application-test.properties

application-prod.properties
```

---

# 📖 application-dev.properties

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/employee_db

logging.level.root=DEBUG
```

---

# 📖 application-test.properties

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/test_db

logging.level.root=INFO
```

---

# 📖 application-prod.properties

```properties
spring.datasource.url=jdbc:postgresql://prod-server:5432/employee_db

logging.level.root=WARN
```

---

# 📖 Active Profile

application.properties

```properties
spring.profiles.active=dev
```

Spring Boot loads

```
application-dev.properties
```

---

# 📖 Change Profile

Development

```properties
spring.profiles.active=dev
```

Testing

```properties
spring.profiles.active=test
```

Production

```properties
spring.profiles.active=prod
```

---

# 📖 @Profile Annotation

```java
@Service
@Profile("dev")
public class DevEmailService {

}
```

This bean loads only when the active profile is **dev**.

---

# 💻 Another Example

```java
@Service
@Profile("prod")
public class ProductionEmailService {

}
```

Loaded only in the **prod** environment.

---

# 🏗 Environment Flow

Application Starts

↓

Read Active Profile

↓

Load Matching Configuration

↓

Create Beans

↓

Application Ready

---

# 📊 Profile Comparison

| Profile | Purpose |
|----------|----------|
| dev | Development |
| test | Testing |
| prod | Production |

---

# 🎤 Interview Questions

## Q1

What is Spring Profile?

Answer

A Spring Profile provides environment-specific configuration.

---

## Q2

Why do we use Spring Profiles?

Answer

To manage different configurations for development, testing, and production.

---

## Q3

Which property activates a profile?

Answer

```properties
spring.profiles.active
```

---

## Q4

What does @Profile do?

Answer

It loads a Bean only for the specified profile.

---

## Q5

Can different environments use different databases?

Answer

Yes.

Each profile can have its own database configuration.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| Profile | Environment Configuration |
| Development | Local Environment |
| Testing | Test Environment |
| Production | Live Environment |
| Active Profile | Current Environment |

---

# 💡 Pro Tips

> [!TIP]

Never use production database credentials in your development profile.

---

> [!IMPORTANT]

Keep API keys, passwords, and secrets separate for each environment.

---

# 🗣 English Practice

Read aloud

Spring Profiles manage multiple environments.

Development uses the dev profile.

Production uses the prod profile.

Each profile has its own configuration.

---

# 🧩 Assignment

- [ ] Create application-dev.properties.
- [ ] Create application-test.properties.
- [ ] Create application-prod.properties.
- [ ] Change spring.profiles.active.
- [ ] Test the application with different profiles.

---

# 🚀 GitHub Task

Commit Message

```
feat: configure Spring Profiles for multiple environments
```

---

# ⭐ Today's Challenge

Without looking at notes

Explain

1. What is a Spring Profile?

2. Why do we use Profiles?

3. Difference between dev, test, and prod?

4. What does @Profile do?

5. How do you activate a profile?

---

# 📌 Summary

✔ Spring Profiles provide environment-specific configuration.

✔ Common profiles are dev, test, and prod.

✔ application-dev.properties stores development settings.

✔ @Profile controls bean loading.

✔ spring.profiles.active selects the active profile.