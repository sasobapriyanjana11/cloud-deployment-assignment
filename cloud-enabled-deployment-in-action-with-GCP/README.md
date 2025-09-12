# Cloud Enabled Deployment In Action with AWS

This repository contains four projects:

- course-service (Spring Boot + MySQL)
- student-service (Spring Boot + MongoDB)
- media-service (Spring Boot + Local file storage, can be extended to S3/MinIO)
- frontend-app (React + TypeScript)

## Backend Services

### 1. course-service
- Entity: Course(id, name, duration)
- Endpoints:
  - GET /courses
  - GET /courses/{id}
  - POST /courses
  - DELETE /courses/{id}
- Default port: 8081
- Configure MySQL settings

### 2. student-service
- Document: Student(registrationNumber, fullName, address, contact, email)
- Endpoints:
  - GET /students
  - GET /students/{id}
  - POST /students
  - DELETE /students/{id}
- Default port: 8082
- Configure MongoDB settings
- 
### Test StudentService Endpoints using POSTMAN
**GET all students**

```http
GET http://localhost:8082/students
```
**Save a student**

```http
POST http://localhost:8082/students
```
**Get Student by Id**

```http
GET http://localhost:8082/students/S001
```
## Postman API Documentation

You can view and test the StudentService endpoints using Postman:

[Open Postman Documentation](https://documenter.getpostman.com/view/35386302/2sB3HoozCd)


### 3. media-service
- Resource: files
- Endpoints:
  - POST /files (multipart/form-data: file)
  - GET /files (list)
  - GET /files/{id} (fetch)
  - DELETE /files/{id} (delete)
- Default port: 8083
- Uses local disk storage at `./data/media` by default (override with env var `MEDIA_STORAGE_DIR`).

### Test MediaService Endpoints using POSTMAN
**Upload a file**

```http
POST http://localhost:8083/files
```
**List all files**

```http
GET http://localhost:8083/files
```
**Download a file**

```http
GET http://localhost:8083/files/14634099-f4c1-464d-a348-2a53ba5931c0
```

**Delete a file**

```http
DELETE http://localhost:8083/files/fcbdb956-f93d-4cb3-b892-b3ea3e8ea142
```
## Postman API Documentation

You can view and test the MediaService endpoints using Postman:
[Open Postman Documentation](https://documenter.getpostman.com/view/35386302/2sB3HoozCd)


## Frontend (frontend-app)
- React + TypeScript + MUI + Axios + Vite app with 3 sections: Courses, Students, Media
- Scripts:
  - npm run dev (Vite dev server)
  - npm run build (TypeScript build + Vite build)
  - npm run preview (Preview built app)

## Build

- Backend: run `mvn -q -e -DskipTests package` at repo root to build services.
- Frontend: run `npm install` then `npm run dev` inside `frontend-app`.
