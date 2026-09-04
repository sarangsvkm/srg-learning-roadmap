

> **Module:** Spring Boot Backend Engineering
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 24 – Spring Boot DevTools]]
>
> **Next:** [[📘 Day 26 – Spring Security Basics]]]

---

# 🌟 Daily Motivation

> "Code that isn't tested is code you can't fully trust."

---

# 🎯 Learning Objectives

Today you will learn

✅ What is Testing?

✅ Unit Testing

✅ Integration Testing

✅ JUnit 5

✅ Mockito

✅ @SpringBootTest

✅ @Mock

✅ @InjectMocks

---

# 📖 What is Testing?

## Definition

Testing is the process of verifying that your application works as expected.

It helps detect bugs before the application reaches users.

---

# 🇮🇳 Malayalam Explanation

Application ശരിയായി പ്രവർത്തിക്കുന്നുണ്ടോ എന്ന്

automatically പരിശോധിക്കുന്നതാണ്

Testing.

---

# 🏢 Real Company Example

Developer

↓

Writes Code

↓

Runs Unit Tests

↓

Build Pass

↓

Deploy to Production

---

# 📖 Types of Testing

### Unit Testing

Tests one class or one method.

Example

EmployeeService

---

### Integration Testing

Tests multiple components together.

Example

Controller + Service + Database

---

# 📦 Maven Dependencies

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-test</artifactId>
    <scope>test</scope>
</dependency>
```

---

# 📖 JUnit 5

JUnit is the most popular Java testing framework.

Example

```java
@Test
void testAddition() {

    assertEquals(10, 5 + 5);

}
```

---

# 📖 Assertions

```java
assertEquals(expected, actual);

assertTrue(condition);

assertFalse(condition);

assertNull(object);

assertNotNull(object);

assertThrows(Exception.class, () -> {

});
```

---

# 📖 Mockito

Mockito is used to create Mock Objects.

Mock Objects replace real dependencies during testing.

---

# 💻 @Mock

```java
@Mock

private EmployeeRepository repository;
```

Creates a fake Repository.

---

# 💻 @InjectMocks

```java
@InjectMocks

private EmployeeService service;
```

Injects mocked Repository into Service.

---

# 💻 Sample Test

```java
@ExtendWith(MockitoExtension.class)
class EmployeeServiceTest {

    @Mock
    private EmployeeRepository repository;

    @InjectMocks
    private EmployeeService service;

    @Test
    void shouldReturnEmployees() {

        when(repository.findAll())
                .thenReturn(List.of(new Employee()));

        assertEquals(1, service.getAllEmployees().size());

    }

}
```

---

# 📖 @SpringBootTest

Loads the complete Spring Boot application context.

```java
@SpringBootTest
class EmployeeApplicationTests {

}
```

Used for Integration Testing.

---

# 🏗 Testing Flow

Write Test

↓

Run Test

↓

Pass

↓

Build Success

↓

Deploy

---

# 📊 JUnit vs Mockito

| JUnit | Mockito |
|--------|----------|
| Testing Framework | Mocking Framework |
| Runs Tests | Creates Mock Objects |
| Assertions | Fake Dependencies |

---

# 🎤 Interview Questions

## Q1

What is Unit Testing?

Answer

Testing a single unit (class or method) independently.

---

## Q2

What is Mockito?

Answer

Mockito is a mocking framework used to create fake objects for testing.

---

## Q3

What is @Mock?

Answer

Creates a mock object.

---

## Q4

What is @InjectMocks?

Answer

Injects mocked dependencies into the class being tested.

---

## Q5

Difference between Unit Testing and Integration Testing?

Answer

Unit Testing tests individual components.

Integration Testing tests multiple components together.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| Unit Test | Test Single Component |
| Integration Test | Test Multiple Components |
| Mock | Fake Object |
| Assertion | Verify Result |
| Test Case | Testing Method |

---

# 💡 Pro Tips

> [!TIP]

Write Unit Tests for the Service layer first.

---

> [!IMPORTANT]

Do not connect to a real database in Unit Tests.

Use Mockito to mock the Repository.

---

# 🗣 English Practice

Read aloud

JUnit executes test cases.

Mockito creates mock objects.

Unit tests verify business logic.

Assertions validate expected results.

---

# 🧩 Assignment

- [ ] Add spring-boot-starter-test dependency.
- [ ] Create EmployeeServiceTest.
- [ ] Mock EmployeeRepository.
- [ ] Write one Unit Test.
- [ ] Run all tests.

---

# 🚀 GitHub Task

Commit Message

```
test: add unit tests for EmployeeService
```

---

# ⭐ Today's Challenge

Without looking at notes

Explain

1. What is Testing?

2. What is Unit Testing?

3. What is Mockito?

4. What is @Mock?

5. What is @InjectMocks?

---

# 📌 Summary

✔ Testing improves software quality.

✔ JUnit executes test cases.

✔ Mockito creates mock objects.

✔ @Mock creates fake dependencies.

✔ @InjectMocks injects mock objects into the class under test.

✔ Unit Tests should not depend on a real database.