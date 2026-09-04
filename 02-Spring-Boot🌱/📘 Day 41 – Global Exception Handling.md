

> **Module:** Spring Boot Backend Engineering
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 40 – File Upload]]
>
> **Next:** [[📘 Day 42 – Logging with SLF4J & Logback]]

---

# 🌟 Daily Motivation

> "Great applications don't expose errors—they handle them gracefully."

---

# 🎯 Learning Objectives

Today you will learn

- ✅ What is Exception Handling?
- ✅ Why Global Exception Handling?
- ✅ @ControllerAdvice
- ✅ @ExceptionHandler
- ✅ Custom Exceptions
- ✅ Error Response
- ✅ Best Practices

---

# 📖 What is Exception Handling?

Exception Handling is the process of handling runtime errors without crashing the application.

It allows applications to return meaningful error messages instead of displaying stack traces.

---

# 🇮🇳 Malayalam Explanation

User

↓

Request

↓

Application

↓

Exception സംഭവിക്കുന്നു

↓

Global Exception Handler

↓

User receives a proper error response

Application crash ആകില്ല.

---

# 🤔 Why Global Exception Handling?

Without Exception Handling

```
User

↓

Request

↓

Application Error

↓

500 Internal Server Error

↓

Stack Trace
```

Problems

- Poor User Experience

- Difficult Debugging

- Unfriendly Error Messages

---

With Global Exception Handling

```
User

↓

Request

↓

Exception

↓

Global Exception Handler

↓

JSON Error Response
```

Advantages

✔ Clean Responses

✔ Centralized Error Handling

✔ Easy Maintenance

✔ Better API Design

---

# 🏢 Real Company Example

Employee API

↓

Employee Not Found

↓

EmployeeNotFoundException

↓

Global Exception Handler

↓

404 Not Found

```json
{
  "status":404,
  "message":"Employee not found"
}
```

---

# 📖 @ControllerAdvice

`@ControllerAdvice` is used to handle exceptions globally across all controllers.

```java
@ControllerAdvice
public class GlobalExceptionHandler {

}
```

---

# 📖 @ExceptionHandler

Handles a specific exception.

```java
@ExceptionHandler(Exception.class)
public ResponseEntity<String> handleException(
        Exception ex){

    return ResponseEntity
            .badRequest()
            .body(ex.getMessage());

}
```

---

# 📖 Custom Exception

```java
public class EmployeeNotFoundException
        extends RuntimeException{

    public EmployeeNotFoundException(
            String message){

        super(message);

    }

}
```

---

# 📖 Throw Exception

```java
Employee employee =
        repository.findById(id)
        .orElseThrow(() ->
            new EmployeeNotFoundException(
                "Employee not found"));
```

---

# 📖 Global Exception Handler

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

# 📖 Error Response DTO

```java
public class ErrorResponse {

    private int status;

    private String message;

    private LocalDateTime timestamp;

}
```

---

# 📖 Standard Error Response

```json
{
    "status":404,
    "message":"Employee not found",
    "timestamp":"2026-08-01T10:20:30"
}
```

---

# 🏗 Exception Handling Flow

```
Client

↓

REST API

↓

Service

↓

Exception

↓

@ControllerAdvice

↓

JSON Response
```

---

# 📊 Common Exceptions

| Exception | Status Code |
|-----------|-------------|
| Resource Not Found | 404 |
| IllegalArgumentException | 400 |
| AccessDeniedException | 403 |
| AuthenticationException | 401 |
| Exception | 500 |

---

# 🎤 Interview Questions

## Q1

What is Global Exception Handling?

**Answer**

It is a centralized mechanism to handle exceptions across the application.

---

## Q2

Which annotation is used?

**Answer**

@ControllerAdvice

---

## Q3

Which annotation handles specific exceptions?

**Answer**

@ExceptionHandler

---

## Q4

Why create Custom Exceptions?

**Answer**

To provide meaningful business-specific error messages.

---

## Q5

Why should we avoid exposing stack traces?

**Answer**

Because stack traces reveal internal implementation details and may create security risks.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| Exception | Runtime Error |
| ControllerAdvice | Global Exception Handler |
| ExceptionHandler | Handles Specific Exceptions |
| RuntimeException | Unchecked Exception |
| Error Response | API Error Message |

---

# 💡 Pro Tips

> [!TIP]

Create custom exceptions for business logic instead of throwing generic exceptions.

---

> [!IMPORTANT]

Never expose Java stack traces in production REST APIs.

Always return meaningful JSON error responses.

---

# 🗣 English Practice

Read aloud

Global Exception Handling improves API quality.

ControllerAdvice handles exceptions globally.

Custom exceptions provide meaningful error messages.

---

# 🧩 Assignment

- [ ] Create EmployeeNotFoundException.
- [ ] Create GlobalExceptionHandler.
- [ ] Handle Resource Not Found.
- [ ] Return ErrorResponse DTO.
- [ ] Test using Postman.
- [ ] Verify HTTP Status Codes.

---

# 🚀 GitHub Task

```text
feat: implement global exception handling
```

---

# 📌 Summary

✔ Global Exception Handling centralizes error management.

✔ @ControllerAdvice handles exceptions globally.

✔ @ExceptionHandler processes specific exceptions.

✔ Custom exceptions improve code readability.

✔ APIs should return structured JSON error responses.

---

# 🔗 Related Notes

- [[📘 Day 40 – File Upload]]
- [[📘 Day 42 – Logging with SLF4J & Logback]]
- [[📘 Day 15 – Exception Handling]]
- [[📘 HTTP Status Codes]]