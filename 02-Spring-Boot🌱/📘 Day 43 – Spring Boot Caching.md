

> **Module:** Spring Boot Backend Engineering
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 42 – Logging with SLF4J & Logback]]
>
> **Next:** [[📘 Day 44 – Redis Integration]]

---

# 🌟 Daily Motivation

> "The fastest database query is the one you don't have to execute."

---

# 🎯 Learning Objectives

Today you will learn

- ✅ What is Caching?
- ✅ Why Caching?
- ✅ Spring Cache Abstraction
- ✅ @EnableCaching
- ✅ @Cacheable
- ✅ @CachePut
- ✅ @CacheEvict
- ✅ Best Practices

---

# 📖 What is Caching?

Caching is the process of storing frequently accessed data in temporary memory so that future requests can be served faster.

Instead of querying the database every time, the application retrieves data from the cache.

---

# 🇮🇳 Malayalam Explanation

User

↓

Request Data

↓

Database

↓

Cache

↓

Next Request

↓

Cache

↓

Fast Response

Database വീണ്ടും query ചെയ്യേണ്ട ആവശ്യമില്ല.

---

# 🤔 Why Caching?

Without Cache

```
User

↓

Application

↓

Database

↓

Response
```

Every request hits the database.

Problems

- Slow Performance
- High Database Load
- Increased Response Time

---

With Cache

```
User

↓

Application

↓

Cache

↓

Response
```

Advantages

✔ Faster Response

✔ Less Database Load

✔ Better Performance

✔ Improved Scalability

---

# 🏢 Real Company Examples

Applications using Caching

- Amazon
- Netflix
- Facebook
- YouTube
- Instagram
- LinkedIn

---

# 🏗 Caching Flow

```
Client

↓

Request

↓

Cache

↓

Data Available?

↓

Yes

↓

Return Cached Data

↓

No

↓

Database

↓

Store in Cache

↓

Return Response
```

---

# 📦 Maven Dependency

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-cache</artifactId>
</dependency>
```

---

# 📖 Enable Caching

```java
@SpringBootApplication

@EnableCaching

public class EmployeeApplication {

}
```

---

# 📖 @Cacheable

Stores the result in cache.

```java
@Cacheable("employees")
public Employee getEmployee(Long id){

    return repository.findById(id).orElse(null);

}
```

First request

↓

Database

Second request

↓

Cache

---

# 📖 @CachePut

Updates both the cache and the database.

```java
@CachePut(value = "employees",
          key = "#employee.id")

public Employee updateEmployee(
        Employee employee){

    return repository.save(employee);

}
```

---

# 📖 @CacheEvict

Removes data from cache.

```java
@CacheEvict(value = "employees",
            key = "#id")

public void deleteEmployee(Long id){

    repository.deleteById(id);

}
```

---

# 📖 Cache Names

```java
@Cacheable("employees")

@Cacheable("products")

@Cacheable("users")
```

Each cache stores its own data.

---

# 🏗 Complete Architecture

```
Client

↓

Controller

↓

Service

↓

Cache

↓

Database

↓

Response
```

---

# 📊 Cache Annotations

| Annotation | Purpose |
|------------|----------|
| @EnableCaching | Enable Cache |
| @Cacheable | Read & Store Cache |
| @CachePut | Update Cache |
| @CacheEvict | Remove Cache |

---

# 📊 Without Cache vs With Cache

| Without Cache | With Cache |
|---------------|------------|
| Database Every Request | Database Only Once |
| Slow | Fast |
| High Load | Low Load |
| More Queries | Fewer Queries |

---

# 🎤 Interview Questions

## Q1

What is Caching?

**Answer**

Caching stores frequently accessed data in memory to improve performance.

---

## Q2

Which annotation enables caching?

**Answer**

@EnableCaching

---

## Q3

What does @Cacheable do?

**Answer**

It stores the method result in the cache and returns cached data for future requests.

---

## Q4

What does @CachePut do?

**Answer**

It updates both the cache and the database.

---

## Q5

What does @CacheEvict do?

**Answer**

It removes data from the cache.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| Cache | Temporary Storage |
| Cache Hit | Data Found in Cache |
| Cache Miss | Data Not Found in Cache |
| Evict | Remove from Cache |
| Memory | Fast Temporary Storage |

---

# 💡 Pro Tips

> [!TIP]

Cache frequently read data, but avoid caching data that changes very often.

---

> [!IMPORTANT]

Always clear or update the cache after updating or deleting database records to prevent stale data.

---

# 🗣 English Practice

Read aloud

Caching improves application performance.

Spring Boot provides cache support using annotations.

Frequently accessed data should be stored in the cache.

---

# 🧩 Assignment

- [ ] Add Cache dependency.
- [ ] Enable caching.
- [ ] Create a @Cacheable method.
- [ ] Update data using @CachePut.
- [ ] Delete data using @CacheEvict.
- [ ] Test cache behavior.

---

# 🚀 GitHub Task

```text
feat: implement Spring Boot caching
```

---

# 📌 Summary

✔ Caching improves application performance.

✔ @EnableCaching enables Spring Cache.

✔ @Cacheable stores method results.

✔ @CachePut updates cached data.

✔ @CacheEvict removes outdated cache entries.

---

# 🔗 Related Notes

- [[📘 Day 42 – Logging with SLF4J & Logback]]
- [[📘 Day 44 – Redis Integration]]
- [[📘 Spring Data JPA]]
- [[📘 HTTP Status Codes]]