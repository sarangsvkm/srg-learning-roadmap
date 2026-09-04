

> **Module:** Spring Boot Backend Engineering
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 17 – DTO (Data Transfer Object)]]]
>
> **Next:** [[📘 Day 19 – Lombok]]

---

# 🌟 Daily Motivation

> "Write less mapping code and focus on business logic."

---

# 🎯 Learning Objectives

Today you will learn

✅ What is ModelMapper?

✅ Why use ModelMapper?

✅ Manual Mapping vs Automatic Mapping

✅ Configure ModelMapper

✅ DTO ↔ Entity Mapping

---

# 📖 What is ModelMapper?

## Definition

ModelMapper is a Java library that automatically maps one object to another.

It is commonly used to convert:

- DTO → Entity
- Entity → DTO

---

# 🇮🇳 Malayalam Explanation

ModelMapper എന്നത്

DTO-യും Entity-യും

Automatic ആയി convert ചെയ്യുന്ന library ആണ്.

Manual ആയി

```
employee.setName(dto.getName());
```

എഴുതേണ്ട ആവശ്യമില്ല.

---

# 🏢 Real Company Example

Client

↓

EmployeeRequestDTO

↓

ModelMapper

↓

Employee Entity

↓

Database

↓

Employee Entity

↓

ModelMapper

↓

EmployeeResponseDTO

↓

Client

---

# ❌ Manual Mapping

```java
Employee employee = new Employee();

employee.setName(dto.getName());
employee.setEmail(dto.getEmail());
employee.setDepartment(dto.getDepartment());
```

Lots of repetitive code.

---

# ✅ ModelMapper

```java
Employee employee =
        modelMapper.map(
                dto,
                Employee.class
        );
```

One line of code!

---

# 📦 Maven Dependency

```xml
<dependency>
    <groupId>org.modelmapper</groupId>
    <artifactId>modelmapper</artifactId>
    <version>3.2.1</version>
</dependency>
```

---

# ⚙️ Configuration

```java
@Configuration
public class ModelMapperConfig {

    @Bean
    public ModelMapper modelMapper() {
        return new ModelMapper();
    }

}
```

---

# 💻 Inject ModelMapper

```java
@Service
public class EmployeeService {

    private final ModelMapper modelMapper;

    public EmployeeService(
            ModelMapper modelMapper){

        this.modelMapper = modelMapper;

    }

}
```

---

# 💻 DTO → Entity

```java
Employee employee =
        modelMapper.map(
                employeeRequestDTO,
                Employee.class
        );
```

---

# 💻 Entity → DTO

```java
EmployeeResponseDTO responseDTO =
        modelMapper.map(
                employee,
                EmployeeResponseDTO.class
        );
```

---

# 🏗 Request Flow

Client

↓

EmployeeRequestDTO

↓

ModelMapper

↓

Employee Entity

↓

Repository

↓

Database

↓

Employee Entity

↓

ModelMapper

↓

EmployeeResponseDTO

↓

Client

---

# 📊 Manual vs ModelMapper

| Manual Mapping | ModelMapper |
|---------------|-------------|
| More Code | Less Code |
| Time Consuming | Fast |
| Error Prone | Cleaner |
| Hard to Maintain | Easy to Maintain |

---

# 🎤 Interview Questions

## Q1

What is ModelMapper?

Answer

ModelMapper is a library used for automatic object mapping.

---

## Q2

Why do we use ModelMapper?

Answer

To reduce boilerplate mapping code.

---

## Q3

What objects are commonly mapped?

Answer

DTO ↔ Entity

---

## Q4

How do we register ModelMapper?

Answer

Using a `@Bean` inside a `@Configuration` class.

---

## Q5

Can ModelMapper map objects automatically?

Answer

Yes, when field names and types match.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| ModelMapper | Object Mapping Library |
| Mapping | Object Conversion |
| DTO | Data Transfer Object |
| Entity | Database Object |
| Bean | Spring Managed Object |

---

# 💡 Pro Tips

> [!TIP]

Use ModelMapper for simple object mapping.

---

> [!IMPORTANT]

If field names differ significantly or mapping is complex, manual mapping may still be required.

---

# 🗣 English Practice

Read aloud

ModelMapper converts DTO to Entity.

ModelMapper reduces boilerplate code.

Spring injects ModelMapper as a Bean.

---

# 🧩 Assignment

- [ ] Add ModelMapper dependency.
- [ ] Create ModelMapperConfig.
- [ ] Register ModelMapper Bean.
- [ ] Convert RequestDTO → Entity.
- [ ] Convert Entity → ResponseDTO.

---

# 🚀 GitHub Task

Commit Message

```
feat: integrate ModelMapper for DTO mapping
```

---

# ⭐ Today's Challenge

Without looking at notes

Explain

1. What is ModelMapper?

2. Why do we use ModelMapper?

3. DTO → Entity mapping.

4. Entity → DTO mapping.

5. Why is ModelMapper better than manual mapping?

---

# 📌 Summary

✔ ModelMapper automatically maps objects.

✔ It converts DTO ↔ Entity.

✔ It reduces repetitive code.

✔ It is registered as a Spring Bean.

✔ It improves code readability and maintainability.