
> **Module:** Spring Boot Backend Engineering
>
> **Project:** Employee Management System
>
> **Previous:** [[📘 Day 39 – Password Reset]]
>
> **Next:** [[📘 Day 41 – Global Exception Handling]]

---

# 🌟 Daily Motivation

> "Modern applications don't just store data—they also manage files securely and efficiently."

---

# 🎯 Learning Objectives

Today you will learn

- ✅ What is File Upload?
- ✅ Multipart File
- ✅ MultipartFile Interface
- ✅ Upload API
- ✅ File Validation
- ✅ File Storage
- ✅ Download API
- ✅ Delete File API
- ✅ Best Practices

---

# 📖 What is File Upload?

File Upload is the process of sending files from a client application to the server.

Examples include

- Profile Photos
- Resume PDF
- Documents
- Images
- Videos
- Excel Files

---

# 🇮🇳 Malayalam Explanation

User

↓

Choose File

↓

Upload

↓

Spring Boot

↓

Server Storage

↓

Database (Optional)

↓

Success Response

---

# 🤔 Why File Upload?

Without File Upload

Users cannot upload

- Profile Pictures
- Documents
- Attachments

Modern applications require secure file management.

---

# 🏢 Real Company Examples

Applications using File Upload

- Google Drive
- Dropbox
- LinkedIn Resume Upload
- Gmail Attachments
- Facebook Photos
- WhatsApp Documents

---

# 🏗 File Upload Flow

```
User

↓

Choose File

↓

HTTP Request

↓

Spring Boot API

↓

Validate File

↓

Save File

↓

Database (Optional)

↓

Success Response
```

---

# 📦 Maven Dependency

Already included in

```xml
spring-boot-starter-web
```

No additional dependency is required.

---

# 📖 MultipartFile

Spring Boot uses the `MultipartFile` interface to receive uploaded files.

Example

```java
@PostMapping("/upload")
public String uploadFile(
        @RequestParam MultipartFile file){

    return "Uploaded Successfully";

}
```

---

# 📖 Save File

```java
String uploadDir = "uploads/";

Path path = Paths.get(uploadDir + file.getOriginalFilename());

Files.copy(
        file.getInputStream(),
        path,
        StandardCopyOption.REPLACE_EXISTING
);
```

---

# 📖 Upload API

```java
@PostMapping("/upload")
public ResponseEntity<String> upload(

        @RequestParam MultipartFile file){

    fileService.upload(file);

    return ResponseEntity.ok("File Uploaded");

}
```

---

# 📖 Download API

```java
@GetMapping("/download/{fileName}")
public ResponseEntity<Resource> download(
        @PathVariable String fileName){

    // Return File Resource

}
```

---

# 📖 Delete API

```java
@DeleteMapping("/{fileName}")
public ResponseEntity<String> delete(
        @PathVariable String fileName){

    fileService.delete(fileName);

    return ResponseEntity.ok("Deleted");

}
```

---

# 📖 application.yml

```yaml
spring:
  servlet:
    multipart:
      enabled: true
      max-file-size: 10MB
      max-request-size: 10MB
```

---

# 📖 File Validation

Validate

- File Size
- File Type
- File Name

Allowed Types

- PDF
- JPG
- PNG
- DOCX

Reject

- EXE
- BAT
- Unknown Files

---

# 📖 File Storage Options

| Storage | Example |
|----------|---------|
| Local Storage | uploads/ |
| Database | BLOB |
| AWS S3 | Cloud Storage |
| Azure Blob | Cloud Storage |
| Google Cloud Storage | Cloud Storage |

---

# 🏗 Complete Architecture

```
Client

↓

REST API

↓

Controller

↓

Service

↓

File System

↓

Database

↓

Response
```

---

# 📊 Upload Process

| Step | Description |
|------|-------------|
| 1 | Select File |
| 2 | Send Multipart Request |
| 3 | Validate File |
| 4 | Save File |
| 5 | Return Response |

---

# 🎤 Interview Questions

## Q1

What interface is used for file upload in Spring Boot?

**Answer**

MultipartFile

---

## Q2

How do you limit file size?

**Answer**

Configure `spring.servlet.multipart.max-file-size` in `application.yml`.

---

## Q3

Where can uploaded files be stored?

**Answer**

- Local File System
- Database
- AWS S3
- Azure Blob
- Google Cloud Storage

---

## Q4

Why should file types be validated?

**Answer**

To prevent malicious or unsupported files from being uploaded.

---

## Q5

Can Spring Boot upload multiple files?

**Answer**

Yes.

Using

```java
MultipartFile[]
```

or

```java
List<MultipartFile>
```

---

# 📖 Vocabulary

| Word | Meaning |
|------|---------|
| MultipartFile | Uploaded File |
| Upload | Send File |
| Download | Retrieve File |
| Validation | File Checking |
| Storage | File Location |

---

# 💡 Pro Tips

> [!TIP]

Rename uploaded files using UUID to avoid duplicate file names.

Example

```
550e8400-e29b-41d4-a716-446655440000.jpg
```

---

> [!IMPORTANT]

Never trust the original file name.

Always validate

- File Type
- File Size
- File Extension

before saving the file.

---

# 🗣 English Practice

Read aloud

Spring Boot uses MultipartFile for file uploads.

Uploaded files should always be validated.

Cloud storage is commonly used in production applications.

---

# 🧩 Assignment

- [ ] Create Upload API.
- [ ] Upload Profile Image.
- [ ] Validate File Type.
- [ ] Validate File Size.
- [ ] Save File.
- [ ] Create Download API.
- [ ] Create Delete API.

---

# 🚀 GitHub Task

```text
feat: implement secure file upload and download APIs
```

---

# 📌 Summary

✔ Spring Boot supports file upload using MultipartFile.

✔ Files should always be validated.

✔ Files can be stored locally or in cloud storage.

✔ Download and Delete APIs improve file management.

✔ Secure file handling is essential for production applications.

---

# 🔗 Related Notes

- [[📘 Day 39 – Password Reset]]
- [[📘 Day 41 – Global Exception Handling]]
- [[📘 Day 15 – Exception Handling]]
- [[📘 Day 16 – Validation]]