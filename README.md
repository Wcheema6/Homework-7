# Homework-7
Homework 7 for CISC.
# Campus Task Board API – HW7

## Project Description

In this project, I enhanced my Task Board API by adding advanced backend features such as global exception handling, DTOs, soft delete functionality, request logging, and application monitoring using Spring Boot Actuator.

The goal of this homework was to improve code structure, error handling, and overall API robustness.

---

## Features Added in HW7

### 1. Global Exception Handling
I implemented custom exceptions and a global exception handler using `@RestControllerAdvice` to return clean JSON error responses instead of default error pages.

Custom exceptions:
- TaskNotFoundException
- InvalidTaskDataException

---

### 2. DTOs (Data Transfer Objects)
I added DTOs to separate internal entity structure from API responses:

- TaskRequest → used for incoming data
- TaskResponse → used for outgoing responses
- ErrorResponse → used for error handling

---

### 3. Soft Delete
Instead of permanently deleting tasks, I added a `deleted` field:

- DELETE now sets `deleted = true`
- Active tasks are filtered using `findByDeletedFalse()`

---

### 4. Request Logging
I created a logging filter that logs:

- HTTP method
- endpoint
- response status
- execution time

---

### 5. Actuator (Monitoring)
I added Spring Boot Actuator to monitor the application.

Health endpoint:

http://localhost:8080/actuator/health

---

## How to Run the Application

1. Open the project in VS Code or IntelliJ

2. Run:

```bash
./mvnw spring-boot:run
Open browser:

http://localhost:8080/api/tasks

API Endpoints
Basic CRUD

GET /api/tasks
GET /api/tasks/{id}
POST /api/tasks
PUT /api/tasks/{id}
DELETE /api/tasks/{id}

Additional Endpoints

GET /api/tasks/completed
GET /api/tasks/incomplete
GET /api/tasks/priority/{priority}
GET /api/tasks/search?keyword=...
GET /api/tasks/paginated?page=0&size=5

Error Handling Example

GET /api/tasks/999

Response:

{
  "timestamp": "...",
  "status": 404,
  "error": "Not Found",
  "message": "Task with ID 999 not found",
  "path": "/api/tasks/999"
}
Notes
This project uses Spring Boot, Spring Data JPA, H2 Database, and Actuator.
Soft delete prevents permanent data loss.
Global exception handling improves API clarity.
