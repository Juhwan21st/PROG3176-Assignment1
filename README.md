# Assignment 1: Course Microservice with CRUD API

Course: PROG3176 - Winter 2026 - Section 1  
Programmed by: Juhwan Seo [8819123]
Due Date: Feb 6, 2026

---

## Description

This microservice provides a RESTful API for managing college courses. It supports full CRUD (Create, Read, Update, Delete) operations using ASP.NET Core Web API, Entity Framework Core, and SQLite. API documentation and testing are available via Swagger UI.

---

## Domain Model

**Entity:** Course

| Property      | Type    | Required | Description                                                    |
|---------------|---------|----------|----------------------------------------------------------------|
| Id            | int     | Yes      | Primary key                                                    |
| CourseCode    | string  | Yes      | 3-4 uppercase letters + 4 digits (e.g., PROG3176), validated   |
| CourseName    | string  | Yes      | Course name (max 100 chars)                                    |
| Credits       | int     | Yes      | Number of credits (1-6)                                        |
| DeliveryMode  | enum    | Yes      | Online, InPerson, Hybrid                                       |
| Description   | string? | No       | Optional course description (max 500 chars)                    |

**Validation:**
- CourseCode: `[Required]`, `[RegularExpression]`
- CourseName: `[Required]`, `[StringLength(100)]`
- Credits: `[Required]`, `[Range(1, 6)]`
- DeliveryMode: `[Required]`
- Description: `[StringLength(500)]`

---

## How to Run

### Prerequisites
- .NET 10.0 SDK
- (Optional) Visual Studio 2022 or VS Code

### Steps

1. Clone or extract the project.
2. Navigate to the project directory:
   ```
   cd JuhwanSeo_Assignment1
   ```
3. Apply database migrations:
   ```
   dotnet ef database update
   ```
4. Run the project:
   ```
   dotnet run
   ```
5. Open Swagger UI in your browser:
   ```
   https://localhost:7009/swagger
   ```

---

## API Endpoints

| Method | Endpoint           | Description              |
|--------|--------------------|--------------------------|
| GET    | /api/Courses       | Get all courses          |
| GET    | /api/Courses/{id}  | Get course by ID         |
| POST   | /api/Courses       | Create new course        |
| PUT    | /api/Courses/{id}  | Update course            |
| DELETE | /api/Courses/{id}  | Delete course            |

---

## Screenshots

- **Read All Courses (GET all)**  
![Read (GET all)](doc_res/postman_GetAllCourses.png)

- **Create Course (POST)**  
![Create (POST)](doc_res/postman_PostCourse.png)

- **Update Course (PUT, error case)**  
![Update (PUT, error case)](doc_res/postman_PutCourse_ERROR.png)

<!-- Add more screenshots as needed for GET by id and DELETE if available -->
