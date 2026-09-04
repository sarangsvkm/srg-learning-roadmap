# 

> **Module:** Spring Boot Core Concepts
>
> **Prerequisite:** [[📘 Spring Service]]
>
> **Next:** [[Spring REST Controller]]

---

# 🌟 Quote

> "A Controller receives the request, but the Service makes the decisions."

---

# 🎯 Learning Objectives

After completing this note, you will understand:

- What is Spring Controller?
- MVC Architecture
- @Controller Annotation
- @RequestMapping
- Model
- View
- Request Flow
- Best Practices
- Interview Questions

---

# 📖 What is Spring Controller?

Spring Controller is a component that receives HTTP requests from the client and returns a View (HTML/JSP/Thymeleaf).

It acts as the entry point of a Spring MVC application.

---

# 🇮🇳 Malayalam Explanation

Controller എന്നത്

User-ൽ നിന്ന് Request സ്വീകരിക്കുന്ന Layer ആണ്.

↓

Service-നെ വിളിക്കും

↓

Result ലഭിക്കും

↓

View-ലേക്ക് അയക്കും.

---

# 🤔 Why Controller?

Without Controller

```
Client

↓

Service
```

Not a proper MVC architecture.

---

With Controller

```
Client

↓

Controller

↓

Service

↓

Repository

↓

Database
```

Controller handles only HTTP requests.

---

# 🏗 MVC Architecture

```
User

↓

Controller

↓

Service

↓

Repository

↓

Database

↓

Service

↓

Controller

↓

View
```

---

# 🏢 Real Company Example

Employee Portal

Employee List Page

↓

EmployeeController

↓

EmployeeService

↓

EmployeeRepository

↓

Database

↓

Employee List View

---

# 📖 @Controller

Marks a class as a Spring MVC Controller.

```java
@Controller
public class EmployeeController {

}
```

Spring automatically detects it as a Controller Bean.

---

# 📖 @RequestMapping

Maps HTTP requests to Controller methods.

```java
@Controller
@RequestMapping("/employees")
public class EmployeeController {

}
```

Base URL

```
/employees
```

---

# 💻 Display Employee List

```java
@Controller
@RequestMapping("/employees")

public class EmployeeController {

    @GetMapping

    public String getEmployees(){

        return "employees";

    }

}
```

Returns

```
employees.html
```

---

# 📖 Using Model

Model transfers data from Controller to View.

```java
@GetMapping

public String getEmployees(Model model){

    model.addAttribute(
            "employees",
            service.getAllEmployees());

    return "employees";

}
```

---

# 📖 View Resolver

Controller

↓

Returns View Name

↓

Spring MVC

↓

Thymeleaf

↓

HTML Page

---

# 🏗 Request Flow

```
Browser

↓

Controller

↓

Service

↓

Repository

↓

Database

↓

Service

↓

Controller

↓

HTML View
```

---

# 📊 Responsibilities

| Layer | Responsibility |
|--------|---------------|
| Controller | Receive Request |
| Service | Business Logic |
| Repository | Database Access |
| View | Display Data |

---

# 📊 @Controller vs @RestController

| @Controller | @RestController |
|--------------|-----------------|
| Returns View | Returns JSON |
| Used in MVC | Used in REST API |
| HTML | JSON/XML |

---

# 🎤 Interview Questions

## Q1

What is Spring Controller?

Answer

A Controller receives HTTP requests and returns a View.

---

## Q2

What annotation creates a Controller?

Answer

@Controller

---

## Q3

What is @RequestMapping?

Answer

It maps URLs to Controller methods.

---

## Q4

What is Model?

Answer

Model transfers data from Controller to View.

---

## Q5

Does @Controller return JSON?

Answer

No.

Normally it returns a View.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| Controller | Request Handler |
| View | HTML Page |
| Model | Data Container |
| Request Mapping | URL Mapping |
| MVC | Model View Controller |

---

# 💡 Pro Tips

> [!TIP]

Keep Controllers lightweight.

Move business logic to the Service layer.

---

> [!IMPORTANT]

Use `@Controller` only when returning HTML pages.

Use `@RestController` for REST APIs.

---

# 🗣 English Practice

Read aloud

The Controller handles HTTP requests.

The Controller returns a View.

The Model transfers data to the View.

---

# 🧩 Assignment

- [ ] Create EmployeeController.
- [ ] Add @Controller.
- [ ] Add @RequestMapping("/employees").
- [ ] Create a GET endpoint.
- [ ] Return an HTML page.
- [ ] Pass data using Model.

---

# 📌 Summary

✔ Controller receives HTTP requests.

✔ @Controller creates an MVC controller.

✔ @RequestMapping maps URLs.

✔ Model transfers data to the View.

✔ Controllers should not contain business logic.

---

# 🔗 Related Notes

- [[📘 Spring Service]]
- [[Spring REST Controller]]
- [[REST API Basics]]