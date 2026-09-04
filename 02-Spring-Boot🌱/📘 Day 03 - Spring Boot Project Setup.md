

> **Module:** Spring Boot Backend Engineering
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 02 - Spring Framework]]]
>
> **Next:** [[📘 Day 04 – Maven & pom.xml]]

---

# 🌟 Daily Motivation

> "Every professional developer starts with a single project. Build it step by step."

---

# 🎯 Learning Objectives

By the end of this lesson, you will be able to:

- Explain what Spring Initializr is.
- Create your first Spring Boot project.
- Understand the Spring Boot project structure.
- Run your first Spring Boot application successfully.

---

# 📖 What is Spring Initializr?

## Definition

Spring Initializr is an online tool used to generate a ready-to-use Spring Boot project.

Official Website:

https://start.spring.io

---

# 🇮🇳 Malayalam Explanation

Spring Boot project നമ്മൾ manually create ചെയ്യേണ്ടതില്ല.

Spring Initializr

↓

Automatic ആയി

- Folder Structure
- Maven Project
- Dependencies
- Main Class

എല്ലാം create ചെയ്യും.

---

# 🏢 Real Company Example

ഒരു പുതിയ project തുടങ്ങുമ്പോൾ

Developer

↓

Open Spring Initializr

↓

Select Dependencies

↓

Generate Project

↓

Open in IntelliJ IDEA

↓

Start Coding

ഇതാണ് മിക്ക കമ്പനികളിലും follow ചെയ്യുന്ന workflow.

---

# 🛠 Create Your First Project

## Project

Maven

## Language

Java

## Spring Boot

Latest Stable Version

## Group

com.sarang

## Artifact

employee-management-system

## Name

employee-management-system

## Package Name

com.sarang.ems

## Packaging

Jar

## Java

21

---

# 📦 Dependencies

- Spring Web
- Spring Data JPA
- PostgreSQL Driver
- Lombok
- Validation

---

# 📂 Project Structure

```
employee-management-system
│
├── src
│   ├── main
│   │
│   ├── java
│   │
│   └── resources
│
├── test
│
├── pom.xml
│
└── mvnw
```

---

# 📖 Folder Explanation

## src/main/java

Contains Java source code.

---

## src/main/resources

Contains

- application.properties
- static
- templates

---

## src/test

Contains test classes.

---

## pom.xml

Contains

- Dependencies
- Plugins
- Build Configuration

---

# 💻 Main Class

```java
@SpringBootApplication
public class EmployeeManagementApplication {

    public static void main(String[] args) {

        SpringApplication.run(
            EmployeeManagementApplication.class,
            args
        );

    }

}
```

---

# 📝 Program Explanation

@SpringBootApplication

↓

Marks the main Spring Boot application.

SpringApplication.run()

↓

Starts the embedded Tomcat server.

Loads all Spring Beans.

Starts the application.

---

# 🚀 Running the Project

Click

Run

↓

Console

↓

You should see

```
Tomcat started on port 8080
Started EmployeeManagementApplication
```

Now open

http://localhost:8080

---

# 🎤 Interview Questions

## Q1

What is Spring Initializr?

**Answer**

Spring Initializr is a web-based tool used to generate Spring Boot projects.

---

## Q2

What is pom.xml?

**Answer**

pom.xml is the Maven configuration file used to manage dependencies and project build settings.

---

## Q3

What is @SpringBootApplication?

**Answer**

It marks the main class of a Spring Boot application and combines multiple Spring annotations.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| Initializr | Project Generator |
| Dependency | Required Library |
| Maven | Build Tool |
| Artifact | Project Name |
| Package | Java Namespace |

---

# 💡 Pro Tips

> [!TIP]
> Always create Spring Boot projects using Spring Initializr instead of manually creating folders.

> [!IMPORTANT]
> Learn the project structure before writing business logic. A well-organized project is easier to maintain.

---

# 🗣 English Practice

Read aloud:

Spring Initializr is used to create Spring Boot projects.

Maven manages project dependencies.

The main class starts the Spring Boot application.

---

# 🧩 Assignment

- [ ] Create a Spring Boot project.
- [ ] Add the required dependencies.
- [ ] Run the application successfully.
- [ ] Explore the project folders.
- [ ] Open and read the pom.xml file.

---

# 🚀 GitHub Task

Repository:

employee-management-system

Commit Message:

feat: create Spring Boot project using Spring Initializr

---

# ⭐ Today's Challenge

Without looking at your notes:

Explain:

1. What is Spring Initializr?
2. What is pom.xml?
3. What is the purpose of src/main/java?
4. What is the purpose of src/main/resources?

---

# 📌 Summary

- Spring Initializr creates Spring Boot projects.
- Maven manages dependencies and build configuration.
- The project follows a standard folder structure.
- The application starts from the main class using @SpringBootApplication.