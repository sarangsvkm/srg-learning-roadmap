

> **Module:** Spring Boot Backend Engineering
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 21 – Spring Profiles]]
>
> **Next:** [[📘 Day 23 – Spring Boot Actuator]]]

---

# 🌟 Daily Motivation

> "Hardcoded values make applications rigid. Configuration makes them flexible."

---

# 🎯 Learning Objectives

Today you will learn

✅ What is Configuration?

✅ @Value

✅ @ConfigurationProperties

✅ Type-safe Configuration

✅ Custom Properties

✅ Configuration Class

---

# 📖 What is Configuration?

## Definition

Configuration contains values that control the application's behavior without changing the source code.

Examples

- Database URL
- Server Port
- API Keys
- Email Settings

---

# 🇮🇳 Malayalam Explanation

Application-ൽ മാറാൻ സാധ്യതയുള്ള values

Code-ൽ hardcode ചെയ്യാതെ

application.properties-ൽ സൂക്ഷിക്കുന്നതാണ് Configuration.

---

# 🏢 Real Company Example

```
Employee API

↓

Database URL

↓

Mail Server

↓

JWT Secret

↓

Cloud Storage

↓

Configured using application.properties
```

---

# 📖 Using @Value

```properties
app.company.name=Sarang Technologies
```

```java
@Value("${app.company.name}")
private String companyName;
```

Good for

✔ One or Two Properties

---

# 📖 Why @ConfigurationProperties?

If you have many related properties,

using @Value repeatedly becomes difficult.

Example

```
mail.host

mail.port

mail.username

mail.password
```

Better solution

@ConfigurationProperties

---

# 📁 application.properties

```properties
company.name=Sarang Technologies
company.location=Kochi
company.email=info@sarang.com
company.phone=9876543210
```

---

# 💻 Configuration Class

```java
@Configuration
@ConfigurationProperties(prefix = "company")
public class CompanyProperties {

    private String name;

    private String location;

    private String email;

    private String phone;

    // Getters and Setters

}
```

---

# 📖 Enable Configuration Properties

```java
@SpringBootApplication
@ConfigurationPropertiesScan
public class EmployeeApplication {

}
```

---

# 💻 Inject Configuration

```java
@Service
@RequiredArgsConstructor
public class EmployeeService {

    private final CompanyProperties companyProperties;

}
```

---

# 💻 Use Properties

```java
log.info(companyProperties.getName());

log.info(companyProperties.getEmail());
```

---

# 🏗 Request Flow

```
application.properties

↓

@ConfigurationProperties

↓

Spring Bean

↓

Service

↓

Controller
```

---

# 📊 @Value vs @ConfigurationProperties

| @Value | @ConfigurationProperties |
|---------|--------------------------|
| Single Property | Group of Properties |
| Simple | Scalable |
| Less Maintainable | More Maintainable |
| Good for Small Apps | Best for Enterprise Apps |

---

# 🎤 Interview Questions

## Q1

What is @ConfigurationProperties?

Answer

It binds multiple related properties into a Java class.

---

## Q2

Why use @ConfigurationProperties instead of @Value?

Answer

It is cleaner, type-safe, and easier to maintain for multiple properties.

---

## Q3

What annotation scans configuration classes?

Answer

@ConfigurationPropertiesScan

---

## Q4

Can ConfigurationProperties become a Spring Bean?

Answer

Yes.

---

## Q5

Where are configuration values stored?

Answer

application.properties or application.yml

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| Configuration | Application Settings |
| Property | Configuration Value |
| Prefix | Common Property Name |
| Bean | Spring Managed Object |
| Type-safe | Strongly Typed Configuration |

---

# 💡 Pro Tips

> [!TIP]

Use @ConfigurationProperties when you have multiple related configuration values.

---

> [!IMPORTANT]

Never hardcode API keys, passwords, or secrets in Java code.

Keep them in configuration files or environment variables.

---

# 🗣 English Practice

Read aloud

Configuration controls application behavior.

@ConfigurationProperties groups related properties.

Spring injects configuration as a Bean.

---

# 🧩 Assignment

- [ ] Create CompanyProperties class.
- [ ] Add @ConfigurationProperties.
- [ ] Add custom properties in application.properties.
- [ ] Inject CompanyProperties into a Service.
- [ ] Print property values using log.info().

---

# 🚀 GitHub Task

Commit Message

```
feat: add @ConfigurationProperties support
```

---

# ⭐ Today's Challenge

Without looking at notes

Explain

1. What is Configuration?

2. What is @ConfigurationProperties?

3. Difference between @Value and @ConfigurationProperties?

4. Why do companies use ConfigurationProperties?

5. Where should API keys be stored?

---

# 📌 Summary

✔ Configuration stores application settings.

✔ @Value is suitable for single properties.

✔ @ConfigurationProperties groups related properties.

✔ Configuration classes are Spring Beans.

✔ Enterprise applications prefer @ConfigurationProperties.