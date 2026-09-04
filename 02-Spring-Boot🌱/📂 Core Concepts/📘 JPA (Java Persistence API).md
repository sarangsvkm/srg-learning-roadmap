

> **Module:** Spring Boot Core Concepts
>
> **Prerequisite:** [[📘 Hibernate]]
>
> **Next:** [[Spring Data JPA]]

---

# 🌟 Quote

> "JPA defines the rules. Hibernate implements them."

---

# 🎯 Learning Objectives

After completing this note, you will understand:

- What is JPA?
- Why JPA was created?
- JPA Architecture
- JPA vs Hibernate
- EntityManager
- Persistence Context
- Entity Lifecycle
- Interview Questions

---

# 📖 What is JPA?

JPA (Java Persistence API) is a Java Specification for Object Relational Mapping (ORM).

It defines a standard way to map Java Objects to Database Tables.

JPA itself is **not a framework**.

It is only a specification.

---

# 🇮🇳 Malayalam Explanation

JPA എന്നത്

Java Objects Database-ൽ എങ്ങനെ Save ചെയ്യണം എന്ന് പറയുന്ന ഒരു Specification ആണ്.

JPA സ്വയം database operations ചെയ്യുന്നില്ല.

അതിന് Hibernate പോലുള്ള implementation വേണം.

---

# 🤔 Why JPA?

Before JPA,

Every ORM framework had its own API.

Example

- Hibernate API
- EclipseLink API
- OpenJPA API

Developers had to learn different APIs.

JPA introduced one common standard.

---

# 📖 JPA Architecture

```
Java Application

↓

JPA Specification

↓

Hibernate

↓

JDBC

↓

Database
```

---

# 🏢 Real Company Example

Spring Boot Application

↓

JPA

↓

Hibernate

↓

PostgreSQL

---

# 📖 JPA Provider

A JPA Provider is a framework that implements JPA.

Popular Providers

- Hibernate
- EclipseLink
- OpenJPA

Spring Boot uses **Hibernate** by default.

---

# 📖 EntityManager

EntityManager is the main interface of JPA.

It performs database operations.

Example

```java
entityManager.persist(employee);

entityManager.find(Employee.class,1L);

entityManager.merge(employee);

entityManager.remove(employee);
```

---

# 📖 Entity

A Java class mapped to a database table.

```java
@Entity

public class Employee{

}
```

---

# 📖 Primary Key

```java
@Id

@GeneratedValue

private Long id;
```

---

# 📖 Persistence Context

Persistence Context manages entity objects.

It tracks changes made to entities.

If an entity changes,

JPA automatically synchronizes it with the database.

---

# 📖 Entity Lifecycle

```
New

↓

Managed

↓

Detached

↓

Removed
```

---

# 💻 Example

```java
Employee employee = new Employee();

entityManager.persist(employee);

entityManager.find(Employee.class,1L);

entityManager.remove(employee);
```

---

# 🏗 JPA Flow

```
Java Object

↓

EntityManager

↓

Hibernate

↓

JDBC

↓

Database
```

---

# 📊 JPA vs Hibernate

| JPA | Hibernate |
|------|-----------|
| Specification | Implementation |
| Standard API | ORM Framework |
| Defines Rules | Implements Rules |
| Cannot Work Alone | Can Work Alone |

---

# 📊 JDBC vs JPA

| JDBC | JPA |
|------|-----|
| Manual SQL | Automatic SQL |
| Manual Mapping | Automatic Mapping |
| More Code | Less Code |
| Hard Maintenance | Easy Maintenance |

---

# 🎤 Interview Questions

## Q1

What is JPA?

Answer

JPA is a Java Specification for Object Relational Mapping.

---

## Q2

Is JPA a framework?

Answer

No.

JPA is only a specification.

---

## Q3

Who implements JPA?

Answer

Hibernate, EclipseLink and OpenJPA.

---

## Q4

What is EntityManager?

Answer

EntityManager performs CRUD operations using JPA.

---

## Q5

Difference between JPA and Hibernate?

Answer

JPA defines the standard.

Hibernate implements the standard.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| JPA | Java Persistence API |
| Entity | Database Object |
| EntityManager | Database Manager |
| Persistence Context | Entity Cache |
| Provider | JPA Implementation |

---

# 💡 Pro Tips

> [!TIP]

Always program against the JPA API instead of using Hibernate-specific APIs whenever possible.

---

> [!IMPORTANT]

Spring Data JPA is built on top of JPA.

JPA usually uses Hibernate as its default provider in Spring Boot.

---

# 🧩 Assignment

- [ ] Create an Employee Entity.
- [ ] Add @Entity annotation.
- [ ] Add @Id and @GeneratedValue.
- [ ] Use EntityManager to persist an object.
- [ ] Read an Employee using EntityManager.

---

# 📌 Summary

✔ JPA is a Java Specification.

✔ JPA defines ORM standards.

✔ Hibernate is the default JPA Provider.

✔ EntityManager performs CRUD operations.

✔ Spring Data JPA builds on top of JPA.

---

# 🔗 Related Notes

- [[📘 Hibernate]]
- [[Spring Data JPA]]
- [[Spring Repository]]
- [[Day 17 – DTO]]
- [[Day 18 – ModelMapper]]