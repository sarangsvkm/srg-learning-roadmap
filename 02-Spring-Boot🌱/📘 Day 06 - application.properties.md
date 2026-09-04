
> **Module:** Spring Boot Backend Engineering
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 05 - Spring Boot Project Structure]]
>
> **Next:** [[📘 Day 07 – Spring IoC, Dependency Injection (DI) & Spring Beans 2]]

---

# 🌟 Daily Motivation

> "A well-configured application is easier to develop, test, and deploy."

---

# 🎯 Learning Objectives

Today you will learn:

- What is application.properties?
- Why is it used?
- Configure Server Port
- Configure Application Name
- Configure PostgreSQL
- Configure Hibernate
- Logging Configuration

---

# 📖 What is application.properties?

## Definition

`application.properties` is the main configuration file of a Spring Boot application.

It stores application settings such as:

- Server Port
- Database Connection
- Logging
- Spring Profiles
- Hibernate Settings

---

# 🇮🇳 Malayalam Explanation

`application.properties`

Spring Boot application-ന്റെ settings file ആണ്.

Java code മാറ്റാതെ application-ന്റെ configuration ഇവിടെ മാറ്റാം.

---

# 📂 Location

```
src
└── main
    └── resources
        └── application.properties
```

---

# 🏢 Real Company Example

Suppose your company wants the application to run on port **9090** instead of **8080**.

You don't change Java code.

You only change:

```properties
server.port=9090
```

Restart the application.

Done ✅

---

# ⚙️ Server Configuration

```properties
server.port=8080
```

Change Port

```properties
server.port=9090
```

---

# 📌 Application Name

```properties
spring.application.name=employee-management-system
```

---

# 🗄 PostgreSQL Configuration

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/employee_db

spring.datasource.username=postgres

spring.datasource.password=password
```

---

# 📦 Hibernate Configuration

```properties
spring.jpa.hibernate.ddl-auto=update

spring.jpa.show-sql=true

spring.jpa.properties.hibernate.format_sql=true
```

---

# 📝 Meaning

ddl-auto=update

Automatically updates database tables.

show-sql=true

Displays SQL queries in console.

format_sql=true

Formats SQL for better readability.

---

# 🪵 Logging

```properties
logging.level.root=INFO

logging.level.org.springframework=DEBUG
```

---

# 💻 Complete Example

```properties
spring.application.name=employee-management-system

server.port=8080

spring.datasource.url=jdbc:postgresql://localhost:5432/employee_db
spring.datasource.username=postgres
spring.datasource.password=password

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
```

---

# 🎤 Interview Questions

## Q1

What is application.properties?

**Answer**

It is the main configuration file used to configure a Spring Boot application.

---

## Q2

Where is application.properties located?

**Answer**

`src/main/resources`

---

## Q3

How do you change the server port?

**Answer**

```properties
server.port=9090
```

---

## Q4

How do you configure PostgreSQL?

**Answer**

Configure:

- URL
- Username
- Password

inside application.properties.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| Configuration | Settings |
| Server | Application Host |
| Database | Data Storage |
| Logging | Application Logs |
| Hibernate | ORM Framework |

---

# 💡 Pro Tips

> [!TIP]

Never hardcode database credentials inside Java classes.

Always use application.properties.

---

> [!IMPORTANT]

Keep passwords secure.

In production, use environment variables instead of storing secrets in source code.

---

# 🗣 English Practice

Read aloud:

application.properties stores application configuration.

Spring Boot reads configuration during startup.

Database settings are configured in application.properties.

---

# 🧩 Assignment

- [ ] Open application.properties.
- [ ] Change server.port to 9090.
- [ ] Add application name.
- [ ] Read all existing properties.
- [ ] Run the application.

---

# 🚀 GitHub Task

Commit Message

```
docs: completed Day 06 application.properties
```

---

# ⭐ Today's Challenge

Without looking at notes:

1. What is application.properties?
2. Where is it located?
3. How do you change the server port?
4. How do you configure PostgreSQL?

---

# 📌 Summary

✔ application.properties stores application configuration.

✔ Server port can be changed without modifying Java code.

✔ Database connection details are configured here.

✔ Hibernate and logging settings are also managed here.