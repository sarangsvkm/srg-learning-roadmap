

> **Module:** Spring Boot Backend Engineering
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 06 - application.properties]]
>
> **Next:** [[📘 Day 08 – Spring Controller]]

---

# 🌟 Daily Motivation

> "Spring's power comes from IoC and Dependency Injection, not from annotations alone."

---

# 🎯 Learning Objectives

Today you will learn:

✅ What is IoC?

✅ What is Dependency?

✅ What is Dependency Injection?

✅ What is Spring Bean?

✅ Spring IoC Container

✅ Bean Lifecycle

✅ Constructor Injection

✅ Field Injection

✅ Setter Injection

---

# 📖 What is Dependency?

## Definition

A Dependency is an object required by another object to perform its work.

---

# 🇮🇳 Malayalam Explanation

ഒരു Class-ന് മറ്റൊരു Class ആവശ്യമുണ്ടെങ്കിൽ

ആ Class

↓

Dependency

ആണ്.

Example

EmployeeService

↓

EmployeeRepository

EmployeeService depends on EmployeeRepository.

---

# 💻 Example

```java
public class Engine {

}
```

```java
public class Car {

    private Engine engine;

}
```

Car

↓

needs

↓

Engine

Engine = Dependency

---

# ❌ Without Spring

```java
public class Car {

    private Engine engine = new Engine();

}
```

Problems

❌ Tight Coupling

❌ Hard to Test

❌ Difficult Maintenance

---

# 📖 What is IoC?

## Definition

IoC (Inversion of Control) means Spring Container creates and manages objects instead of the developer.

---

# 🇮🇳 Malayalam Explanation

Normally

Developer creates Objects.

```java
Engine engine = new Engine();
```

Spring Boot-ൽ

Spring Container

creates Objects automatically.

Developer doesn't use

new

everywhere.

---

# 🏢 Real Company Example

Without Spring

Developer

↓

new Repository()

↓

new Service()

↓

new Controller()

---

With Spring

Spring Container

↓

Creates Beans

↓

Injects Dependencies

↓

Application Ready

---

# 📖 What is Dependency Injection?

## Definition

Dependency Injection is a design pattern where Spring automatically provides required objects.

---

# 🇮🇳 Malayalam Explanation

Developer

Object create ചെയ്യേണ്ട.

Spring

Object create ചെയ്ത്

Inject ചെയ്യും.

---

# 💻 Constructor Injection (Recommended)

```java
@Service
public class EmployeeService {

    private final EmployeeRepository repository;

    public EmployeeService(EmployeeRepository repository) {

        this.repository = repository;

    }

}
```

Spring automatically injects

EmployeeRepository.

---

# 💻 Field Injection

```java
@Service
public class EmployeeService {

    @Autowired

    private EmployeeRepository repository;

}
```

---

# 💻 Setter Injection

```java
@Service
public class EmployeeService {

    private EmployeeRepository repository;

    @Autowired

    public void setRepository(EmployeeRepository repository) {

        this.repository = repository;

    }

}
```

---

# ⭐ Best Practice

✅ Constructor Injection

Reasons

- Easy Unit Testing
- Immutable Objects
- Recommended by Spring Team
- Clear Dependencies

---

# 📖 What is Spring Bean?

## Definition

A Spring Bean is an object that is created, managed, and destroyed by the Spring IoC Container.

---

# 🇮🇳 Malayalam Explanation

Spring Container create ചെയ്യുന്ന എല്ലാ Objects-ഉം

Bean

എന്നാണ് വിളിക്കുന്നത്.

Example

EmployeeController

EmployeeService

EmployeeRepository

എല്ലാം Spring Beans ആണ്.

---

# 📦 Bean Annotations

```java
@Component
```

Generic Spring Bean

---

```java
@Service
```

Business Logic Layer

---

```java
@Repository
```

Database Layer

---

```java
@Controller
```

MVC Controller

---

```java
@RestController
```

REST API Controller

---

```java
@Configuration
```

Configuration Class

---

# 🏗 Spring IoC Flow

Application Starts

↓

Spring IoC Container

↓

Scans Packages

↓

Creates Beans

↓

Injects Dependencies

↓

Application Ready

---

# 🎤 Interview Questions

## Q1

What is IoC?

Answer

IoC means Spring Container manages object creation instead of the developer.

---

## Q2

What is Dependency Injection?

Answer

Dependency Injection is the process of providing required objects automatically.

---

## Q3

What is Spring Bean?

Answer

A Spring Bean is an object managed by the Spring IoC Container.

---

## Q4

Which Dependency Injection type is recommended?

Answer

Constructor Injection.

---

## Q5

What is the difference between @Component and @Service?

Answer

@Service is a specialized form of @Component used for business logic classes.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| IoC | Inversion of Control |
| Dependency | Required Object |
| Injection | Providing Objects |
| Bean | Spring Managed Object |
| Container | Object Manager |

---

# 💡 Pro Tips

> [!TIP]

Always use Constructor Injection in production projects.

---

> [!IMPORTANT]

Avoid using the `new` keyword for Spring-managed components.

Let Spring create and inject Beans.

---

# 🗣 English Practice

Read aloud:

Spring Container manages Beans.

Dependency Injection reduces coupling.

Constructor Injection is recommended.

Spring Beans are managed by the IoC Container.

---

# 🧩 Assignment

- [ ] Explain IoC.
- [ ] Explain Dependency Injection.
- [ ] Explain Spring Bean.
- [ ] Compare Constructor, Field and Setter Injection.
- [ ] Draw the Spring IoC flow in your notebook.

---

# 🚀 GitHub Task

Commit Message

```
docs: completed Day 07 IoC DI and Spring Beans
```

---

# ⭐ Today's Challenge

Without looking at notes:

1. What is IoC?

2. What is Dependency?

3. What is Dependency Injection?

4. What is Spring Bean?

5. Which Injection type is recommended?

---

# 📌 Summary

✔ Dependency = Required Object

✔ IoC = Spring manages object creation.

✔ Dependency Injection = Spring injects required objects.

✔ Spring Bean = Object managed by Spring.

✔ Constructor Injection is the best practice.

✔ Spring Container manages the complete object lifecycle.