# 📘 Day 46 – Asynchronous Programming (@Async)

> **Module:** Spring Boot Backend Engineering
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 45 – Spring Boot Scheduling]]
>
> **Next:** [[📘 Day 47 – Spring Boot ...]]

---

# 🌟 Daily Motivation

> "Build applications that can work efficiently without making users wait unnecessarily."

---

# 🎯 Learning Objectives

Today you will learn

- ✅ What is Asynchronous Programming?
- ✅ Why Asynchronous Programming?
- ✅ Synchronous vs Asynchronous
- ✅ @EnableAsync
- ✅ @Async
- ✅ Async Methods
- ✅ CompletableFuture
- ✅ Best Practices

---

# 📖 What is Asynchronous Programming?

Asynchronous Programming is a programming approach where a task can execute independently without blocking the main execution flow.

Spring Boot provides asynchronous processing using the **@Async** annotation.

---

# 🇮🇳 Malayalam Explanation

Normally, when a method runs:

```text
Request

↓

Method Executes

↓

Task Completes

↓

Response
```

The application waits until the task finishes.

With asynchronous processing:

```text
Request

↓

Start Task

↓

Continue Execution
        ↓
     Response

Task continues in background
```

Example

- Send Email
- Generate Reports
- Process Files
- Background Notifications
- Long-Running Tasks

---

# 🤔 Why Asynchronous Programming?

Without Async

```text
User Request

↓

Long Task

↓

Wait

↓

Task Complete

↓

Response
```

Problems

- User has to wait
- Request takes longer
- Server resources may be blocked
- Poor user experience

---

With Async

```text
User Request

↓

Start Background Task

↓

Continue

↓

Response
```

Advantages

✔ Better Response Time

✔ Background Processing

✔ Better User Experience

✔ Useful for Long-Running Tasks

---

# 🏢 Real Company Examples

Asynchronous processing can be useful for:

- E-Commerce → Send Order Confirmation Email
- Banking → Generate Statements
- School Systems → Generate Reports
- HR Systems → Send Notifications
- SaaS Applications → Background Processing

---

# 📦 Enable Async

Add `@EnableAsync` to the Spring Boot application.

```java
@SpringBootApplication

@EnableAsync

public class EmployeeApplication {

}
```

`@EnableAsync` enables Spring's asynchronous method execution capability.

---

# 📖 Create an Async Method

```java
@Service
public class EmailService {

    @Async
    public void sendEmail() {

        System.out.println("Sending Email...");

    }

}
```

The `@Async` annotation tells Spring to execute the method asynchronously.

---

# 📖 Calling an Async Method

```java
@Service
public class NotificationService {

    private final EmailService emailService;

    public NotificationService(EmailService emailService) {
        this.emailService = emailService;
    }

    public void sendNotification() {

        emailService.sendEmail();

        System.out.println("Notification request completed");

    }

}
```

The email task can execute in the background while the calling thread continues.

---

# ⚠️ Important

`@Async` works through Spring's proxy mechanism.

Therefore, calling an `@Async` method from another method in the **same class** may not execute asynchronously.

Example:

```java
public void methodA() {

    methodB();

}

@Async
public void methodB() {

}
```

This is not the recommended approach.

Prefer calling the async method through another Spring-managed bean.

---

# 📖 CompletableFuture

For asynchronous operations where we need a result, we can use `CompletableFuture`.

```java
@Async
public CompletableFuture<String> processTask() {

    String result = "Task Completed";

    return CompletableFuture.completedFuture(result);

}
```

---

# 📖 Getting the Result

```java
CompletableFuture<String> result = service.processTask();
```

The result can be handled asynchronously.

---

# 🔄 Synchronous vs Asynchronous

| Synchronous | Asynchronous |
|-------------|--------------|
| Waits for task | Does not wait |
| Blocking flow | Non-blocking flow |
| Simple execution | Background execution |
| User may wait | Faster response |
| Suitable for normal tasks | Suitable for background tasks |

---

# 🏗 Asynchronous Flow

```text
Client

↓

Controller

↓

Service

↓

@Async Method

↓

Background Thread

↓

Email / Report / File Processing

↓

Completed
```

---

# 📖 Real Project Example

School Management System

Generate Monthly Attendance Report

```text
Admin

↓

Request Report

↓

Spring Boot

↓

Start @Async Task

↓

Generate Report

↓

Save PDF

↓

Send Email
```

The admin does not necessarily need to wait for the complete report generation process.

---

# 🎤 Interview Questions

## Q1

What is Asynchronous Programming?

**Answer**

Asynchronous Programming allows a task to execute independently without blocking the main execution flow.

---

## Q2

Which annotation enables asynchronous processing in Spring Boot?

**Answer**

@EnableAsync

---

## Q3

Which annotation is used to execute a method asynchronously?

**Answer**

@Async

---

## Q4

Why do we use @Async?

**Answer**

`@Async` is used to execute long-running or background tasks without blocking the calling thread.

---

## Q5

Can @Async return a result?

**Answer**

Yes. An asynchronous method can return a `CompletableFuture`.

---

## Q6

What is CompletableFuture?

**Answer**

`CompletableFuture` represents the result of an asynchronous computation and allows asynchronous processing of that result.

---

## Q7

Can we call an @Async method from the same class?

**Answer**

It is not recommended because the call may bypass Spring's proxy mechanism and therefore may not execute asynchronously.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| Asynchronous | Executes independently |
| Synchronous | Waits for completion |
| Blocking | Waiting for an operation |
| Background Task | Task running separately |
| Thread | Unit of execution |
| CompletableFuture | Represents an async result |

---

# 💡 Pro Tips

> [!TIP]

Use **@Async** for tasks such as:

- Email sending
- Notifications
- Report generation
- File processing
- Background jobs

---

> [!IMPORTANT]

Do not use asynchronous processing for every method.

Use it when a task can safely run independently from the main request flow.

---

# 🗣 English Practice

Read aloud

Spring Boot supports asynchronous processing using the @Async annotation.

Asynchronous processing allows background tasks to execute independently.

CompletableFuture can be used when an asynchronous task needs to return a result.

---

# 🧩 Assignment

- [ ] Enable asynchronous processing.
- [ ] Create an `@Async` service method.
- [ ] Call the async method from another service.
- [ ] Test the execution.
- [ ] Create an async method using `CompletableFuture`.
- [ ] Compare synchronous and asynchronous execution.

---

# 🚀 GitHub Task

```text
feat: implement asynchronous background tasks
```

---

# 📌 Summary

✔ Asynchronous Programming allows tasks to execute independently.

✔ `@EnableAsync` enables asynchronous processing.

✔ `@Async` executes a method asynchronously.

✔ `CompletableFuture` can represent the result of an asynchronous computation.

✔ Async processing is useful for background tasks such as emails, notifications, reports, and file processing.

✔ `@Async` should be used carefully and through Spring-managed beans.

---

# 🔗 Related Notes

- [[📘 Day 45 – Spring Boot Scheduling]]
- [[📘 Day 47 – Spring Boot ...]]
- [[📘 Day 42 – Logging with SLF4J & Logback]]
- [[📘 Day 20 – Logging]]
