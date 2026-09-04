

> **Module:** Spring Boot Backend Engineering
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 18 – ModelMapper]]
>
> **Next:** [[📘 Day 20 – Logging with SLF4J & Logback]]]

---

# 🌟 Daily Motivation

> "Write less code. Build more features."

---

# 🎯 Learning Objectives

Today you will learn

✅ What is Lombok?

✅ Why use Lombok?

✅ @Getter

✅ @Setter

✅ @Data

✅ @NoArgsConstructor

✅ @AllArgsConstructor

✅ @RequiredArgsConstructor

✅ @Builder

---

# 📖 What is Lombok?

## Definition

Lombok is a Java library that automatically generates common boilerplate code at compile time.

It reduces the need to manually write:

- Getters
- Setters
- Constructors
- toString()
- equals()
- hashCode()

---

# 🇮🇳 Malayalam Explanation

Lombok എന്നത്

Java-യിൽ ഒരേ code വീണ്ടും വീണ്ടും എഴുതേണ്ട ആവശ്യം ഒഴിവാക്കുന്ന Library ആണ്.

Getter

Setter

Constructor

toString()

ഇവയെല്ലാം Lombok automatically generate ചെയ്യും.

---

# 🏢 Real Company Example

Without Lombok

Employee.java

↓

200+ lines

With Lombok

↓

30–40 lines

Cleaner Code

---

# 📦 Maven Dependency

```xml
<dependency>
    <groupId>org.projectlombok</groupId>
    <artifactId>lombok</artifactId>
    <optional>true</optional>
</dependency>
```

---

# 📖 @Getter

Generates Getter methods.

```java
@Getter
public class Employee {

    private String name;

}
```

Generated

```java
public String getName(){

    return name;

}
```

---

# 📖 @Setter

Generates Setter methods.

```java
@Setter
public class Employee {

    private String name;

}
```

Generated

```java
public void setName(String name){

    this.name = name;

}
```

---

# 📖 @Data

Generates

- Getter
- Setter
- toString()
- equals()
- hashCode()

```java
@Data
public class Employee {

    private String name;

    private String email;

}
```

---

# 📖 @NoArgsConstructor

Creates a default constructor.

```java
@NoArgsConstructor
public class Employee {

}
```

Generated

```java
public Employee(){

}
```

---

# 📖 @AllArgsConstructor

Creates a constructor with all fields.

```java
@AllArgsConstructor
public class Employee {

    private Long id;

    private String name;

}
```

Generated

```java
public Employee(Long id,
                String name){

}
```

---

# 📖 @RequiredArgsConstructor

Creates a constructor only for final fields.

```java
@RequiredArgsConstructor
@Service
public class EmployeeService {

    private final EmployeeRepository repository;

}
```

Spring automatically injects Repository.

---

# 📖 @Builder

Creates objects using Builder Pattern.

```java
@Builder
public class Employee {

    private String name;

    private String email;

}
```

Usage

```java
Employee employee =
        Employee.builder()
                .name("Sarang")
                .email("sarang@gmail.com")
                .build();
```

---

# 🏗 Without Lombok

```java
Employee employee = new Employee();

employee.setName("Sarang");

employee.setEmail("sarang@gmail.com");
```

---

# 🏗 With Builder

```java
Employee employee =
        Employee.builder()
                .name("Sarang")
                .email("sarang@gmail.com")
                .build();
```

Cleaner and easier to read.

---

# 🎤 Interview Questions

## Q1

What is Lombok?

Answer

Lombok is a Java library that automatically generates boilerplate code.

---

## Q2

Why do we use Lombok?

Answer

To reduce repetitive code and improve readability.

---

## Q3

What does @Data generate?

Answer

Getter

Setter

toString()

equals()

hashCode()

---

## Q4

What is @Builder?

Answer

It implements the Builder Pattern for object creation.

---

## Q5

Why do companies prefer Lombok?

Answer

Cleaner code, easier maintenance, and higher developer productivity.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| Lombok | Java Code Generation Library |
| Boilerplate | Repetitive Code |
| Getter | Read Value |
| Setter | Update Value |
| Builder | Object Creation Pattern |

---

# 💡 Pro Tips

> [!TIP]

Use `@RequiredArgsConstructor` for Service classes instead of writing constructors manually.

---

> [!IMPORTANT]

Avoid using `@Data` on JPA Entities in complex applications. Many teams prefer:

- `@Getter`
- `@Setter`
- `@NoArgsConstructor`
- `@AllArgsConstructor`

because it gives better control over `equals()` and `hashCode()`.

---

# 🗣 English Practice

Read aloud

Lombok reduces boilerplate code.

@Getter creates getter methods.

@Setter creates setter methods.

@Builder creates objects using the Builder Pattern.

---

# 🧩 Assignment

- [ ] Add Lombok dependency.
- [ ] Install Lombok plugin in IntelliJ (if required).
- [ ] Use @Getter and @Setter.
- [ ] Use @Builder.
- [ ] Replace manual constructors with Lombok annotations.

---

# 🚀 GitHub Task

Commit Message

```
feat: integrate Lombok into Employee project
```

---

# ⭐ Today's Challenge

Without looking at notes

Explain

1. What is Lombok?

2. Why do we use Lombok?

3. Difference between @Data and @Getter?

4. What is @Builder?

5. What is @RequiredArgsConstructor?

---

# 📌 Summary

✔ Lombok reduces boilerplate code.

✔ @Getter creates getter methods.

✔ @Setter creates setter methods.

✔ @Data combines common annotations.

✔ @Builder simplifies object creation.

✔ @RequiredArgsConstructor is ideal for dependency injection.