

> **Module:** Spring Boot Backend Engineering
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 15 – Exception Handling]]
>
> **Next:** [[📘 Day 17 – DTO (Data Transfer Object)]]

---

# 🌟 Daily Motivation

> "Never trust user input. Always validate before saving."

---

# 🎯 Learning Objectives

Today you will learn

✅ What is Validation?

✅ Why Validation is Important?

✅ Bean Validation

✅ @Valid

✅ @NotBlank

✅ @Email

✅ @Size

✅ @Min

✅ @Max

---

# 📖 What is Validation?

## Definition

Validation is the process of checking whether the incoming data is correct before processing or saving it.

---

# 🇮🇳 Malayalam Explanation

User നൽകുന്ന data

Database-ലേക്ക് save ചെയ്യുന്നതിന് മുമ്പ്

ശരിയാണോ എന്ന് പരിശോധിക്കുന്നതാണ്

Validation.

---

# 🏢 Real Company Example

Employee Registration

User enters

```
Name : ""
Email : abc
```

Without Validation

↓

Invalid data saved

With Validation

↓

Validation Error

↓

Data NOT Saved

---

# 📖 Why Validation?

Validation helps to

✔ Prevent Invalid Data

✔ Improve Data Quality

✔ Improve Security

✔ Reduce Errors

---

# 🏗 Request Flow

Client

↓

POST Request

↓

Validation

↓

Controller

↓

Service

↓

Repository

↓

Database

---

# 📖 @Valid

Used to trigger validation.

```java
@PostMapping
public ResponseEntity<Employee> saveEmployee(
        @Valid
        @RequestBody Employee employee){

    return ResponseEntity.ok(
            service.save(employee)
    );

}
```

---

# 📖 @NotBlank

Ensures the field is not null, empty, or only spaces.

```java
@NotBlank(message = "Name is required")
private String name;
```

---

# 📖 @Email

Validates email format.

```java
@Email(message = "Invalid email")
private String email;
```

---

# 📖 @Size

Checks the length of a String.

```java
@Size(min = 3, max = 50,
      message = "Name must contain 3 to 50 characters")
private String name;
```

---

# 📖 @Min

Minimum numeric value.

```java
@Min(value = 18,
      message = "Age must be at least 18")
private Integer age;
```

---

# 📖 @Max

Maximum numeric value.

```java
@Max(value = 60,
      message = "Age must not exceed 60")
private Integer age;
```

---

# 💻 Employee Entity

```java
@Entity
public class Employee {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @NotBlank(message="Name is required")
    @Size(min=3,max=50)
    private String name;

    @Email(message="Invalid Email")
    private String email;

    @NotBlank(message="Department is required")
    private String department;

}
```

---

# 🧪 Postman Test

Request

```json
{
    "name":"",
    "email":"abc",
    "department":""
}
```

Response

```
400 Bad Request
```

Validation Errors

```
Name is required

Invalid Email

Department is required
```

---

# 🎤 Interview Questions

## Q1

What is Validation?

Answer

Validation checks user input before processing.

---

## Q2

Why do we use @Valid?

Answer

To trigger Bean Validation.

---

## Q3

What does @NotBlank do?

Answer

Ensures a String is not null, empty, or blank.

---

## Q4

What does @Email validate?

Answer

It validates email format.

---

## Q5

Which HTTP status code is returned for invalid input?

Answer

400 Bad Request

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| Validation | Input Checking |
| @Valid | Starts Validation |
| @NotBlank | Field Required |
| @Email | Email Validation |
| @Size | Length Validation |

---

# 💡 Pro Tips

> [!TIP]

Always validate request data before saving it.

---

> [!IMPORTANT]

Validation belongs at the API boundary (Controller layer) using `@Valid`.

---

# 🗣 English Practice

Read aloud

Validation checks user input.

@Valid triggers validation.

@NotBlank ensures required fields.

@Email validates email format.

---

# 🧩 Assignment

- [ ] Add validation annotations to Employee.
- [ ] Use @Valid in Controller.
- [ ] Test invalid data using Postman.
- [ ] Verify 400 Bad Request response.

---

# 🚀 GitHub Task

Commit Message

```
feat: add bean validation for Employee
```

---

# ⭐ Today's Challenge

Without looking at notes

Explain

1. What is Validation?

2. Why do we use @Valid?

3. What is @NotBlank?

4. What is @Email?

5. Why should invalid data never be saved?

---

# 📌 Summary

✔ Validation checks user input.

✔ @Valid starts validation.

✔ @NotBlank prevents empty values.

✔ @Email validates email format.

✔ Invalid requests return **400 Bad Request**.

✔ Validation improves data quality and application security.