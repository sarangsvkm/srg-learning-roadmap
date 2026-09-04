

> **Module:** Spring Boot Backend Engineering
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 43 – Spring Boot Caching]]
>
> **Next:** [[📘 Day 45 – Spring Boot Scheduling]]

---

# 🌟 Daily Motivation

> "Fast applications don't always use faster databases—they use smarter caching."

---

# 🎯 Learning Objectives

Today you will learn

- ✅ What is Redis?
- ✅ Why Redis?
- ✅ Redis Architecture
- ✅ Spring Boot Redis Integration
- ✅ Redis Configuration
- ✅ RedisTemplate
- ✅ Cache with Redis
- ✅ Best Practices

---

# 📖 What is Redis?

Redis (Remote Dictionary Server) is an open-source, in-memory data store.

It is commonly used for

- Caching
- Session Management
- Rate Limiting
- Message Queues
- Leaderboards

Because data is stored in memory (RAM), Redis is much faster than traditional databases.

---

# 🇮🇳 Malayalam Explanation

User

↓

Request

↓

Spring Boot

↓

Redis Cache

↓

If Data Exists

↓

Return Data

Else

↓

Database

↓

Save to Redis

↓

Return Response

---

# 🤔 Why Redis?

Without Redis

```
User

↓

Application

↓

Database

↓

Response
```

Problems

- Slow Database Queries
- High Database Load
- Increased Response Time

---

With Redis

```
User

↓

Application

↓

Redis

↓

Response
```

Advantages

✔ Very Fast

✔ Reduced Database Load

✔ Better Performance

✔ Better Scalability

---

# 🏢 Real Company Examples

Applications using Redis

- Netflix
- Amazon
- Instagram
- Facebook
- Uber
- Twitter
- LinkedIn

---

# 🏗 Redis Architecture

```
Client

↓

Spring Boot

↓

Redis

↓

Database

↓

Response
```

---

# 📦 Maven Dependency

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-redis</artifactId>
</dependency>
```

---

# 📖 Install Redis

Ubuntu

```bash
sudo apt update

sudo apt install redis-server

redis-server
```

Check Version

```bash
redis-server --version
```

---

# 📖 application.yml

```yaml
spring:
  data:
    redis:
      host: localhost
      port: 6379
```

---

# 📖 RedisTemplate

Spring Boot provides `RedisTemplate` to interact with Redis.

```java
@Autowired

private RedisTemplate<String,Object> redisTemplate;
```

---

# 📖 Save Data

```java
redisTemplate.opsForValue()
        .set("employee","Sarang");
```

---

# 📖 Read Data

```java
String employee =
(String) redisTemplate
.opsForValue()
.get("employee");
```

---

# 📖 Delete Data

```java
redisTemplate.delete("employee");
```

---

# 📖 Cache with Redis

```java
@Cacheable("employees")
public Employee getEmployee(Long id){

    return repository.findById(id)
            .orElse(null);

}
```

Redis stores the cached data automatically.

---

# 📖 Redis Data Types

| Type | Example |
|------|---------|
| String | User Name |
| List | Notifications |
| Set | Roles |
| Hash | Employee Details |
| Sorted Set | Leaderboard |

---

# 🏗 Complete Flow

```
Client

↓

Controller

↓

Service

↓

Redis

↓

Database

↓

Response
```

---

# 📊 Spring Cache vs Redis

| Spring Cache | Redis |
|--------------|-------|
| Cache Abstraction | In-Memory Data Store |
| Annotation-Based | Dedicated Server |
| Works with Redis | Stores Cached Data |

---

# 📊 Redis vs Database

| Redis | Database |
|--------|----------|
| RAM | Disk Storage |
| Very Fast | Slower |
| Temporary Data | Permanent Data |
| Cache | Primary Storage |

---

# 🎤 Interview Questions

## Q1

What is Redis?

**Answer**

Redis is an open-source in-memory data store used for caching and fast data access.

---

## Q2

Why is Redis faster than a database?

**Answer**

Because Redis stores data in memory (RAM) instead of reading from disk.

---

## Q3

Which port does Redis use by default?

**Answer**

6379

---

## Q4

What class is commonly used to access Redis in Spring Boot?

**Answer**

RedisTemplate

---

## Q5

Can Redis be used only for caching?

**Answer**

No.

Redis is also used for sessions, queues, rate limiting, leaderboards, and distributed locking.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| Redis | In-Memory Database |
| Cache | Temporary Storage |
| RedisTemplate | Redis Client |
| Key | Identifier |
| Value | Stored Data |

---

# 💡 Pro Tips

> [!TIP]

Cache frequently accessed data in Redis to improve API performance.

---

> [!IMPORTANT]

Do not store critical permanent data only in Redis.

Redis is primarily designed for caching and temporary storage.

---

# 🗣 English Practice

Read aloud

Redis stores data in memory.

Spring Boot integrates Redis using RedisTemplate.

Redis improves application performance.

---

# 🧩 Assignment

- [ ] Install Redis.
- [ ] Configure Redis in Spring Boot.
- [ ] Connect using RedisTemplate.
- [ ] Store a value.
- [ ] Read a value.
- [ ] Delete a value.
- [ ] Test Redis caching.

---

# 🚀 GitHub Task

```text
feat: integrate Redis caching with Spring Boot
```

---

# 📌 Summary

✔ Redis is an in-memory data store.

✔ Redis significantly improves application performance.

✔ Spring Boot integrates Redis using RedisTemplate.

✔ Redis is widely used for caching, sessions, and rate limiting.

✔ Redis reduces database load and improves response time.

---

# 🔗 Related Notes

- [[📘 Day 43 – Spring Boot Caching]]
- [[📘 Day 45 – Spring Boot Scheduling]]
- [[📘 Spring Data JPA]]
- [[📘 HTTP Status Codes]]