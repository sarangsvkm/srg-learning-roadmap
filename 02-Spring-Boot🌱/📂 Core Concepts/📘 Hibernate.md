
> **Module:** Spring Boot Core Concepts
>
> **Prerequisite:** Java, JDBC
>
> **Next:** [[JPA]]

---

# 🌟 Quote

> "Hibernate simplifies database programming by removing repetitive JDBC code."

---

# 🎯 Learning Objectives

After completing this note, you will understand:

- What is Hibernate?
- Why Hibernate was created?
- Problems with JDBC
- Hibernate Architecture
- ORM (Object Relational Mapping)
- Hibernate Lifecycle
- Advantages & Disadvantages
- Interview Questions

---

# 📖 What is Hibernate?

Hibernate is an **Open Source ORM (Object Relational Mapping) Framework** for Java.

It simplifies database operations by converting Java Objects into Database Tables.

Instead of writing SQL queries manually, Hibernate performs database operations automatically.

---

# 🇮🇳 Malayalam Explanation

Hibernate എന്നത്

Java Object-നെ

Database Table-ആയി മാറ്റുന്ന Framework ആണ്.

SQL Query എല്ലാം നേരിട്ട് എഴുതേണ്ട ആവശ്യം കുറയുന്നു.

---

# 🤔 Why Hibernate?

Before Hibernate,

Developers used JDBC.

Problems with JDBC:

- Too much Boilerplate Code
- Manual SQL Queries
- Manual Connection Handling
- Manual Object Mapping
- Difficult Maintenance

Hibernate solves all these problems.

---

# 📖 What is ORM?

ORM = Object Relational Mapping

Object

↓

Java Class

↓

ORM

↓

Database Table

Example

```java
Employee employee = new Employee();
```

↓

Hibernate

↓

Employee Table

---

# 🏗 Hibernate Architecture

```
Java Application

↓

Hibernate

↓

JDBC

↓

Database
```

---

# 🏢 Real Company Example

Employee Management System

Employee.java

↓

Hibernate

↓

employee table

↓

PostgreSQL Database

---

# 📦 Hibernate Dependencies

```xml
<dependency>
    <groupId>org.hibernate.orm</groupId>
    <artifactId>hibernate-core</artifactId>
</dependency>
```

---

# 📖 Hibernate Flow

```
Java Object

↓

Session

↓

Hibernate

↓

SQL

↓

Database
```

---

# 📖 Hibernate Session

A Session is used to communicate with the database.

It is responsible for:

- Save
- Update
- Delete
- Fetch

Example

```java
Session session =
        sessionFactory.openSession();
```

---

# 📖 CRUD Operations

Create

```java
session.persist(employee);
```

Read

```java
session.find(Employee.class,1L);
```

Update

```java
session.merge(employee);
```

Delete

```java
session.remove(employee);
```

---

# 📖 Entity

Entity means

A Java Class that represents a Database Table.

Example

```java
@Entity

public class Employee {

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

# 🏗 Hibernate Lifecycle

```
Create Object

↓

Session

↓

Persist

↓

Database

↓

Close Session
```

---

# 📊 JDBC vs Hibernate

| JDBC | Hibernate |
|------|-----------|
| Manual SQL | Automatic SQL |
| More Code | Less Code |
| Manual Mapping | Automatic Mapping |
| Slower Development | Faster Development |
| Hard Maintenance | Easy Maintenance |

---

# ✅ Advantages

- Less Boilerplate Code
- Automatic SQL Generation
- Database Independent
- Faster Development
- Better Productivity
- Easy Object Mapping

---

# ❌ Disadvantages

- Learning Curve
- Slight Performance Overhead
- Complex Queries may need native SQL

---

# 🎤 Interview Questions

## Q1

What is Hibernate?

Answer

Hibernate is an ORM Framework for Java.

---

## Q2

Why do we use Hibernate?

Answer

To reduce JDBC boilerplate code and simplify database operations.

---

## Q3

What is ORM?

Answer

ORM maps Java Objects to Database Tables.

---

## Q4

What is a Session?

Answer

A Session is the interface used by Hibernate to communicate with the database.

---

## Q5

Does Hibernate replace JDBC?

Answer

No.

Hibernate internally uses JDBC to communicate with the database.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| ORM | Object Relational Mapping |
| Entity | Java Class mapped to Table |
| Session | Database Communication |
| Persist | Save Object |
| Mapping | Object to Table Conversion |

---

# 💡 Pro Tips

> [!TIP]

Hibernate works on top of JDBC.

You don't need to write most SQL queries manually.

---

> [!IMPORTANT]

Hibernate is an **implementation** of the **JPA specification**.

In modern Spring Boot applications, developers usually use **Spring Data JPA**, which internally uses Hibernate by default.

---

# 🧩 Assignment

- [ ] Create an Employee Entity.
- [ ] Add @Entity annotation.
- [ ] Add @Id and @GeneratedValue.
- [ ] Save an Employee using Hibernate.
- [ ] Fetch Employee by ID.

---

# 📌 Summary

✔ Hibernate is an ORM Framework.

✔ Hibernate maps Java Objects to Database Tables.

✔ Hibernate reduces JDBC boilerplate code.

✔ Hibernate internally uses JDBC.

✔ Hibernate is the default JPA implementation in most Spring Boot projects.

---

# 🔗 Related Notes

- [[JPA]]
- [[Spring Data JPA]]
- [[Spring Repository]]
- [[Day 17 – DTO]]
- [[Day 18 – ModelMapper]]