# 

> **Module:** Spring Boot Backend Engineering
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 03 - Spring Boot Project Setup]]
>
> **Next:** [[📘 Day 05 - Spring Boot Project Structure]]

---

# 🌟 Daily Motivation

> "A professional developer doesn't just write code.
> They understand how the project is built."

---

# 🎯 Learning Objectives

Today you will learn:

✅ What is Maven?

✅ Why do we use Maven?

✅ What is pom.xml?

✅ Maven Project Structure

✅ Dependency Management

---

# 📖 What is Maven?

## Definition

Maven is a build automation and dependency management tool for Java projects.

---

# 🇮🇳 Malayalam Explanation

ഒരു Spring Boot Project-ൽ

100+ Libraries ഉണ്ടാകും.

ഉദാഹരണം

- Spring Web

- Spring Security

- PostgreSQL

- Lombok

- Validation

ഇവയെല്ലാം നമ്മൾ manually download ചെയ്യില്ല.

Maven

Automatic ആയി download ചെയ്യും.

---

# 🏢 Real Company Example

Without Maven

Developer

↓

Search JAR

↓

Download

↓

Copy

↓

Paste

↓

Configure

↓

Run

Very Slow ❌

---

With Maven

Developer

↓

Add Dependency

↓

Save pom.xml

↓

Maven Downloads Automatically

Done ✅

---

# 📖 What is pom.xml?

## Definition

pom.xml is the Project Object Model file.

It contains:

- Project Information

- Dependencies

- Plugins

- Java Version

- Build Configuration

---

# 🇮🇳 Malayalam Explanation

Spring Boot Project-ന്റെ

Heart ❤️

ആണ്

pom.xml

ഇവിടെ നിന്നാണ്

Project-ന് വേണ്ട Libraries download ചെയ്യുന്നത്.

---

# 📄 Sample pom.xml

```xml
<dependencies>

    <dependency>
        <groupId>org.springframework.boot</groupId>

        <artifactId>spring-boot-starter-web</artifactId>

    </dependency>

</dependencies>
```

---

# 📝 Explanation

groupId

↓

Company / Organization

artifactId

↓

Library Name

dependency

↓

Library used by project

---

# 📦 Common Spring Boot Dependencies

- spring-boot-starter-web
- spring-boot-starter-data-jpa
- spring-boot-starter-validation
- lombok
- postgresql
- spring-boot-devtools
- spring-boot-starter-test

---

# 💻 Real Example

Want REST API?

↓

Add

spring-boot-starter-web

Want Database?

↓

Add

spring-boot-starter-data-jpa

Want PostgreSQL?

↓

Add

postgresql

---

# 📖 Project Build Process

Developer

↓

Write Code

↓

Maven Build

↓

Compile

↓

Package

↓

Jar File

↓

Run Application

---

# 🎤 Interview Questions

## Q1

What is Maven?

Answer

Maven is a build automation and dependency management tool for Java projects.

---

## Q2

What is pom.xml?

Answer

pom.xml is the Project Object Model file used to manage dependencies and project configuration.

---

## Q3

Why do we use Maven?

Answer

To automate project build, dependency management and packaging.

---

## Q4

What is Dependency?

Answer

A dependency is an external library required by the project.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| Maven | Build Tool |
| Dependency | External Library |
| Build | Compile & Package |
| Plugin | Additional Feature |
| Repository | Library Storage |

---

# 💡 Pro Tips

> [!TIP]

Never copy JAR files manually.

Always use Maven Dependencies.

---

> [!IMPORTANT]

Every professional Spring Boot project uses Maven or Gradle.

---

# 🗣 English Practice

Read 5 Times

Maven manages project dependencies.

pom.xml contains project configuration.

Spring Boot uses Maven to build applications.

---

# 🧩 Assignment

- [ ] Open pom.xml
- [ ] Identify Java Version
- [ ] Identify Dependencies
- [ ] Add Spring Boot DevTools
- [ ] Reload Maven Project

---

# 🚀 GitHub Task

Commit

docs: completed Day 04 Maven Basics

---

# ⭐ Today's Challenge

Without looking at notes

Explain

What is Maven?

What is pom.xml?

What is Dependency?

---

# 📌 Summary

✔ Maven is a Build Tool.

✔ pom.xml manages project configuration.

✔ Dependencies are downloaded automatically.

✔ Maven simplifies Java development.
