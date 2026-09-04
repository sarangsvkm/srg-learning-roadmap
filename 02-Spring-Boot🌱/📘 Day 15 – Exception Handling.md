

> **Module:** Spring Boot Backend Engineering
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 14 – DELETE API (@DeleteMapping)]]
>
> **Next:** [[📘 Day 16 – Validation in Spring Boot]]

---

# 🌟 Daily Motivation

> "Great developers don't just handle success—they handle failures gracefully."

---

# 🎯 Learning Objectives

Today you will learn

✅ What is Exception?

✅ Types of Exceptions

✅ try-catch

✅ Custom Exception

✅ @ExceptionHandler

✅ @ControllerAdvice

✅ Global Exception Handling

---

# 📖 What is an Exception?

## Definition

An Exception is an unexpected event that interrupts the normal flow of a program.

---

# 🇮🇳 Malayalam Explanation

Program run ചെയ്യുമ്പോൾ

Unexpected Error വന്നാൽ

അതിനെ

Exception

എന്ന് വിളിക്കുന്നു.

Example

Employee ID = 100

Database-ൽ ഇല്ല.

↓

Employee Not Found

↓

Exception

---

# 🏢 Real Company Example

User

↓

GET

/api/employees/100

↓

Employee doesn't exist

↓

Return

404 Not Found

Instead of

500 Internal Server Error

---

# 📖 Common Exceptions

- NullPointerException
- ArithmeticException
- IOException
- IllegalArgumentException
- RuntimeException

---

# 💻 Example

```java
int result = 10 / 0;
```

Output

```
ArithmeticException
```

---

# 📖 try-catch

```java
try {

    int result = 10 / 0;

} catch (Exception ex){

    System.out.println(ex.getMessage());

}
```

---

# 📖 Custom Exception

```java
public class EmployeeNotFoundException
        extends RuntimeException {

    public EmployeeNotFoundException(String message){

        super(message);

    }

}
```

---

# 💻 Throw Exception

```java
Employee employee = repository
        .findById(id)
        .orElseThrow(() ->
            new EmployeeNotFoundException(
                    "Employee Not Found"
            )
        );
```

---

# 📖 @ExceptionHandler

Handles specific exceptions.

```java
@ExceptionHandler(EmployeeNotFoundException.class)

public ResponseEntity<String> handleException(
        EmployeeNotFoundException ex){

    return ResponseEntity
            .status(HttpStatus.NOT_FOUND)
            .body(ex.getMessage());

}
```

---

# 📖 @ControllerAdvice

Global Exception Handler.

```java
@ControllerAdvice
public class GlobalExceptionHandler {

}
```

Handles exceptions from every controller.

---

# 💻 Global Exception Example

```java
@ControllerAdvice
public class GlobalExceptionHandler {

    @ExceptionHandler(EmployeeNotFoundException.class)

    public ResponseEntity<String> handleEmployeeException(

            EmployeeNotFoundException ex){

        return ResponseEntity
                .status(HttpStatus.NOT_FOUND)
                .body(ex.getMessage());

    }

}
```

---

# 🏗 Request Flow

Client

↓

Controller

↓

Service

↓

Exception

↓

Global Exception Handler

↓

404 Response

---

# 🧪 Testing

Request

```
GET

/api/employees/100
```

Response

```
404 Not Found
```

Body

```json
{
    "message":"Employee Not Found"
}
```

---

# 🎤 Interview Questions

## Q1

What is an Exception?

Answer

An Exception is an unexpected event during program execution.

---

## Q2

What is RuntimeException?

Answer

It is an exception that occurs during runtime.

---

## Q3

Why do we use @ControllerAdvice?

Answer

To handle exceptions globally.

---

## Q4

What is @ExceptionHandler?

Answer

It handles specific exceptions.

---

## Q5

Why create Custom Exceptions?

Answer

To provide meaningful error messages.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| Exception | Runtime Error |
| try | Execute Code |
| catch | Handle Error |
| throw | Raise Exception |
| ControllerAdvice | Global Error Handler |

---

# 💡 Pro Tips

> [!TIP]

Never expose Java stack traces to API users.

Return meaningful error messages.

---

> [!IMPORTANT]

Always create custom exceptions for business errors.

Example

EmployeeNotFoundException

DepartmentNotFoundException

---

# 🗣 English Practice

Read aloud

Exceptions interrupt normal program execution.

@ControllerAdvice handles exceptions globally.

Custom exceptions improve code readability.

---

# 🧩 Assignment

- [ ] Create EmployeeNotFoundException.
- [ ] Create GlobalExceptionHandler.
- [ ] Handle 404 errors.
- [ ] Test invalid Employee ID.
- [ ] Return JSON error response.

---

# 🚀 GitHub Task

Commit Message

```
feat: add global exception handling
```

---

# ⭐ Today's Challenge

Without looking at notes

Explain

1. What is an Exception?

2. What is @ControllerAdvice?

3. What is @ExceptionHandler?

4. Why create custom exceptions?

5. Difference between try-catch and Global Exception Handler?

---

# 📌 Summary

✔ Exceptions handle runtime errors.

✔ try-catch handles local exceptions.

✔ Custom Exceptions improve readability.

✔ @ExceptionHandler handles specific exceptions.

✔ @ControllerAdvice handles exceptions globally.

✔ Return proper HTTP status codes instead of server errors.