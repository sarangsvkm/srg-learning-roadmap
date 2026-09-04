

> **Module:** Spring Boot Core Concepts
>
> **Prerequisite:** [[JPA]]
>
> **Next:** [[Spring Repository]]

---

# 🌟 Quote

> "Write less code, access more data."

---

# 🎯 Learning Objectives

After completing this note, you will understand:

- What is Spring Data JPA?
- Why Spring Data JPA?
- How Spring Data JPA works
- JpaRepository
- CRUD Operations
- Custom Query Methods
- Paging & Sorting
- Interview Questions

---

# 📖 What is Spring Data JPA?

Spring Data JPA is a Spring framework that simplifies database access.

It is built on top of JPA.

Instead of writing DAO classes manually, Spring Data JPA automatically provides CRUD methods.

---

# 🇮🇳 Malayalam Explanation

Spring Data JPA എന്നത്

Database operations വളരെ എളുപ്പമാക്കുന്ന

Spring Framework ആണ്.

CRUD methods

സ്വയം generate ചെയ്യും.

---

# 🤔 Why Spring Data JPA?

Without Spring Data JPA

Developer writes

- DAO Class
- SQL Queries
- CRUD Methods

With Spring Data JPA

Simply create Repository Interface.

Spring automatically provides CRUD methods.

---

# 🏗 Spring Data JPA Architecture

```
Spring Boot

↓

Spring Data JPA

↓

JPA

↓

Hibernate

↓

JDBC

↓

Database
```

---

# 🏢 Real Company Example

Employee Service

↓

EmployeeRepository

↓

Spring Data JPA

↓

Hibernate

↓

PostgreSQL

---

# 📦 Maven Dependency

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>
```

---

# 📖 JpaRepository

JpaRepository provides ready-made CRUD methods.

Example

```java
public interface EmployeeRepository
        extends JpaRepository<Employee, Long> {

}
```

---

# 📖 Common CRUD Methods

Save

```java
repository.save(employee);
```

Find All

```java
repository.findAll();
```

Find By Id

```java
repository.findById(id);
```

Delete

```java
repository.deleteById(id);
```

Count

```java
repository.count();
```

Exists

```java
repository.existsById(id);
```

---

# 📖 Custom Query Methods

Spring creates SQL automatically.

```java
findByEmail(String email)

findByName(String name)

findByDepartment(String department)

findBySalaryGreaterThan(double salary)
```

No SQL required.

---

# 💻 Example

```java
public interface EmployeeRepository
extends JpaRepository<Employee,Long>{

    Employee findByEmail(String email);

}
```

Spring automatically generates the query.

---

# 📖 @Query Annotation

Custom JPQL Query

```java
@Query("SELECT e FROM Employee e WHERE e.department=:department")

List<Employee> findDepartment(String department);
```

---

# 📖 Paging

```java
Page<Employee> findAll(Pageable pageable);
```

---

# 📖 Sorting

```java
findAll(Sort.by("name"));
```

---

# 🏗 Request Flow

```
Controller

↓

Service

↓

Repository

↓

Spring Data JPA

↓

Hibernate

↓

Database
```

---

# 📊 CRUD Flow

| Operation | Method |
|-----------|--------|
| Create | save() |
| Read | findById() |
| Read All | findAll() |
| Update | save() |
| Delete | deleteById() |

---

# 🎤 Interview Questions

## Q1

What is Spring Data JPA?

Answer

Spring Data JPA simplifies database access by providing automatic CRUD operations.

---

## Q2

What is JpaRepository?

Answer

JpaRepository is an interface that provides CRUD methods.

---

## Q3

Who implements JpaRepository?

Answer

Spring Data JPA automatically creates the implementation at runtime.

---

## Q4

Can we create custom query methods?

Answer

Yes.

Spring generates queries from method names.

---

## Q5

Can we write custom SQL?

Answer

Yes.

Using @Query.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| Repository | Data Access Layer |
| CRUD | Create Read Update Delete |
| Query Method | Auto-generated Query |
| Pageable | Pagination |
| Sort | Sorting |

---

# 💡 Pro Tips

> [!TIP]

Use JpaRepository instead of writing DAO classes manually.

---

> [!IMPORTANT]

Use method name queries for simple cases.

Use @Query for complex queries.

---

# 🧩 Assignment

- [ ] Create EmployeeRepository.
- [ ] Extend JpaRepository.
- [ ] Test save().
- [ ] Test findAll().
- [ ] Test findById().
- [ ] Create findByEmail().

---

# 📌 Summary

✔ Spring Data JPA simplifies database access.

✔ JpaRepository provides CRUD methods.

✔ Spring generates Repository implementations automatically.

✔ Query methods reduce SQL writing.

✔ Supports Paging and Sorting.

---

# 🔗 Related Notes

- [[📘 Hibernate]]
- [[JPA]]
- [[Spring Repository]]