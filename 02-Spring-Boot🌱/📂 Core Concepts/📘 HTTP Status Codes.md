

> **Module:** Spring Boot Core Concepts
>
> **Prerequisite:** [[REST API Basics]]
>
> **Next:** [[Spring Security]]

---

# 🌟 Quote

> "Every HTTP response tells a story through its status code."

---

# 🎯 Learning Objectives

After completing this note, you will understand:

- What are HTTP Status Codes?
- Status Code Categories
- 2xx Success Codes
- 3xx Redirection Codes
- 4xx Client Error Codes
- 5xx Server Error Codes
- Best Practices
- Interview Questions

---

# 📖 What are HTTP Status Codes?

HTTP Status Codes are 3-digit numbers returned by the server.

They tell the client whether the request was successful or failed.

---

# 🇮🇳 Malayalam Explanation

Client ഒരു Request അയക്കുമ്പോൾ

Server ഒരു Response നൽകും.

ആ Response-ന്റെ Result അറിയിക്കാൻ

Status Code ഉപയോഗിക്കുന്നു.

---

# 🏗 Request Flow

```
Client

↓

HTTP Request

↓

Spring Boot API

↓

HTTP Response

↓

Status Code
```

---

# 📖 Status Code Categories

| Range | Meaning |
|--------|---------|
| 1xx | Informational |
| 2xx | Success |
| 3xx | Redirection |
| 4xx | Client Error |
| 5xx | Server Error |

---

# ✅ 2xx – Success Codes

### 200 OK

Request completed successfully.

Example

```
GET /employees
```

Response

```
200 OK
```

---

### 201 Created

New resource created successfully.

Example

```
POST /employees
```

Response

```
201 Created
```

---

### 204 No Content

Request succeeded but nothing is returned.

Example

```
DELETE /employees/1
```

Response

```
204 No Content
```

---

# 🔄 3xx – Redirection Codes

### 301 Moved Permanently

Resource moved permanently.

---

### 302 Found

Temporary redirect.

---

### 304 Not Modified

Browser uses cached data.

---

# ❌ 4xx – Client Error Codes

### 400 Bad Request

Client sent invalid data.

Example

Missing required field.

---

### 401 Unauthorized

Authentication required.

JWT missing or invalid.

---

### 403 Forbidden

User is authenticated

but has no permission.

Example

USER tries to delete data.

---

### 404 Not Found

Requested resource doesn't exist.

Example

Employee ID not found.

---

### 405 Method Not Allowed

Wrong HTTP method used.

Example

POST instead of GET.

---

### 409 Conflict

Duplicate resource exists.

Example

Email already registered.

---

# 💥 5xx – Server Error Codes

### 500 Internal Server Error

Unexpected server error.

Example

NullPointerException

Database Failure

---

### 502 Bad Gateway

Gateway received an invalid response.

---

### 503 Service Unavailable

Server is temporarily unavailable.

Example

Maintenance Mode.

---

### 504 Gateway Timeout

Another server took too long to respond.

---

# 📊 Common Status Codes

| Code | Meaning | Example |
|------|---------|---------|
| 200 | OK | GET Success |
| 201 | Created | POST Success |
| 204 | No Content | DELETE Success |
| 400 | Bad Request | Validation Failed |
| 401 | Unauthorized | Login Required |
| 403 | Forbidden | Access Denied |
| 404 | Not Found | Invalid ID |
| 405 | Method Not Allowed | Wrong HTTP Method |
| 409 | Conflict | Duplicate Email |
| 500 | Internal Server Error | Server Exception |

---

# 💻 ResponseEntity Examples

### 200 OK

```java
return ResponseEntity.ok(employee);
```

---

### 201 Created

```java
return ResponseEntity
        .status(HttpStatus.CREATED)
        .body(employee);
```

---

### 204 No Content

```java
return ResponseEntity
        .noContent()
        .build();
```

---

### 404 Not Found

```java
return ResponseEntity
        .notFound()
        .build();
```

---

### 400 Bad Request

```java
return ResponseEntity
        .badRequest()
        .body("Invalid Request");
```

---

# 🏢 Real Company Example

Employee API

```
GET /employees

↓

200 OK
```

---

Create Employee

```
POST /employees

↓

201 Created
```

---

Delete Employee

```
DELETE /employees/5

↓

204 No Content
```

---

Employee Not Found

```
GET /employees/999

↓

404 Not Found
```

---

Unauthorized Request

```
GET /employees

↓

401 Unauthorized
```

---

# 🎤 Interview Questions

## Q1

What is HTTP Status Code?

Answer

A status code tells whether an HTTP request succeeded or failed.

---

## Q2

Difference between 401 and 403?

Answer

401 → Authentication required.

403 → User is authenticated but not authorized.

---

## Q3

When do we return 201?

Answer

After creating a new resource.

---

## Q4

When do we return 404?

Answer

When the requested resource is not found.

---

## Q5

What is 500?

Answer

Unexpected server-side error.

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| Success | Request Completed |
| Client Error | User Request Problem |
| Server Error | Backend Problem |
| Unauthorized | Authentication Needed |
| Forbidden | Permission Denied |

---

# 💡 Pro Tips

> [!TIP]

Use proper HTTP status codes in every REST API.

---

> [!IMPORTANT]

Never return **200 OK** for failed requests.

Always return the appropriate status code.

---

# 🧩 Assignment

- [ ] Return 200 for GET.
- [ ] Return 201 for POST.
- [ ] Return 204 for DELETE.
- [ ] Return 404 when ID is missing.
- [ ] Return 400 for validation errors.
- [ ] Test all APIs in Postman.

---

# 📌 Summary

✔ HTTP Status Codes describe the result of a request.

✔ 2xx → Success

✔ 3xx → Redirection

✔ 4xx → Client Errors

✔ 5xx → Server Errors

✔ Use ResponseEntity to return proper status codes.

---

# 🔗 Related Notes

- [[REST API Basics]]
- [[Spring REST Controller]]
- [[Spring Security]]