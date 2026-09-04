

> **Module:** Spring Boot Backend Engineering
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 44 – Redis Integration]]
>
> **Next:** [[📘 Day 46 – Asynchronous Programming (@Async)]]

---

# 🌟 Daily Motivation

> "Automate repetitive tasks so your application can work even when you are away."

---

# 🎯 Learning Objectives

Today you will learn

- ✅ What is Scheduling?
- ✅ Why Scheduling?
- ✅ @EnableScheduling
- ✅ @Scheduled
- ✅ fixedRate
- ✅ fixedDelay
- ✅ cron Expression
- ✅ Best Practices

---

# 📖 What is Scheduling?

Scheduling is the process of executing a task automatically at a specific time or at regular intervals without manual intervention.

Spring Boot provides scheduling support using the **@Scheduled** annotation.

---

# 🇮🇳 Malayalam Explanation

Application Starts

↓

Scheduler Starts

↓

Scheduled Time

↓

Task Executes Automatically

↓

Repeat

Example

- Send Daily Reports
- Clean Old Logs
- Backup Database
- Send Email Notifications

---

# 🤔 Why Scheduling?

Without Scheduling

```
Admin

↓

Run Task Manually

↓

Time Consuming
```

Problems

- Manual Work
- Missed Tasks
- Human Errors

---

With Scheduling

```
Application

↓

Scheduler

↓

Execute Task

↓

Complete
```

Advantages

✔ Automation

✔ Saves Time

✔ Reliable

✔ No Manual Work

---

# 🏢 Real Company Examples

Applications using Scheduling

- Amazon → Order Status Emails
- Netflix → Subscription Renewal
- Google → Backup Jobs
- Banking Applications → Interest Calculation
- HR Systems → Attendance Reports

---

# 📦 Enable Scheduling

```java
@SpringBootApplication

@EnableScheduling

public class EmployeeApplication {

}
```

---

# 📖 Create a Scheduler

```java
@Component

public class ReportScheduler {

    @Scheduled(fixedRate = 60000)

    public void generateReport(){

        System.out.println("Generating Report...");

    }

}
```

Runs every **60 seconds**.

---

# 📖 fixedRate

```java
@Scheduled(fixedRate = 5000)
```

Runs every **5 seconds**, measured from the **start** of the previous execution.

---

# 📖 fixedDelay

```java
@Scheduled(fixedDelay = 5000)
```

Runs **5 seconds after** the previous execution finishes.

---

# 📖 initialDelay

```java
@Scheduled(

    initialDelay = 10000,

    fixedRate = 60000

)
```

Waits **10 seconds** after application startup before executing the first task.

---

# 📖 Cron Expression

```java
@Scheduled(cron = "0 0 9 * * *")
```

Runs every day at **9:00 AM**.

---

# 📖 Common Cron Examples

| Cron | Meaning |
|-------|---------|
| `0 * * * * *` | Every Minute |
| `0 0 * * * *` | Every Hour |
| `0 0 9 * * *` | Every Day at 9 AM |
| `0 0 0 * * MON` | Every Monday |
| `0 0 0 1 * *` | First Day of Every Month |

---

# 🏗 Scheduling Flow

```
Application

↓

Scheduler

↓

Scheduled Method

↓

Business Logic

↓

Database / Email / Report

↓

Completed
```

---

# 📊 Scheduling Types

| Type | Description |
|------|-------------|
| fixedRate | Runs at a fixed interval |
| fixedDelay | Runs after previous execution finishes |
| cron | Runs at a specific date/time |

---

# 📖 Real Project Example

Employee Attendance Report

```
Every Day

↓

09:00 PM

↓

Generate Report

↓

Send Email to HR
```

---

# 🎤 Interview Questions

## Q1

What is Scheduling?

**Answer**

Scheduling is the automatic execution of tasks at predefined times or intervals.

---

## Q2

Which annotation enables scheduling?

**Answer**

@EnableScheduling

---

## Q3

Which annotation schedules a method?

**Answer**

@Scheduled

---

## Q4

Difference between fixedRate and fixedDelay?

**Answer**

- **fixedRate** → Time is calculated from the start of the previous execution.
- **fixedDelay** → Time is calculated after the previous execution completes.

---

## Q5

What is a Cron Expression?

**Answer**

A Cron Expression defines the exact schedule for a task, such as every day at 9:00 AM.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| Scheduler | Task Executor |
| Cron | Time-Based Schedule |
| fixedRate | Fixed Interval |
| fixedDelay | Delay After Completion |
| Automation | Automatic Execution |

---

# 💡 Pro Tips

> [!TIP]

Use **cron** for business tasks like reports, emails, and backups.

---

> [!IMPORTANT]

Avoid long-running tasks inside `@Scheduled` methods.

For heavy background jobs, combine scheduling with **@Async**.

---

# 🗣 English Practice

Read aloud

Spring Boot supports scheduling using the @Scheduled annotation.

Cron expressions define when a task should execute.

Scheduling automates repetitive tasks.

---

# 🧩 Assignment

- [ ] Enable Scheduling.
- [ ] Create a Scheduler Class.
- [ ] Execute a task every minute.
- [ ] Create a Daily Cron Job.
- [ ] Log scheduler execution.
- [ ] Test the scheduler.

---

# 🚀 GitHub Task

```text
feat: implement scheduled background tasks
```

---

# 📌 Summary

✔ Scheduling automates repetitive tasks.

✔ @EnableScheduling enables scheduling.

✔ @Scheduled executes methods automatically.

✔ fixedRate, fixedDelay, and cron provide different scheduling options.

✔ Scheduling is widely used for reports, emails, backups, and maintenance tasks.

---

# 🔗 Related Notes

- [[📘 Day 44 – Redis Integration]]
- [[📘 Day 46 – Asynchronous Programming (@Async)]]
- [[📘 Day 42 – Logging with SLF4J & Logback]]
- [[📘 Day 20 – Logging]]