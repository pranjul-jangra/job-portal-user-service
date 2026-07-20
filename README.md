# 👤 Job Portal - User Service

The User Service is responsible for managing user profiles within the **Job Portal** application. It provides APIs for profile management, profile picture and resume uploads, skill management, and job applications while securely communicating with other microservices.

---

## ✨ Features

- 👤 User Profile Management
- 📝 Update Personal Information
- 🖼️ Profile Picture Upload
- 📄 Resume Upload
- 🛠️ Add & Remove Skills
- 💼 Apply for Jobs
- 📋 View Applied Jobs
- 🔐 JWT Protected Routes
- ☁️ File Upload Integration through Utils Service
- 🗄️ PostgreSQL Database Integration
- 🐳 Dockerized Deployment
- 📝 Centralized Error Handling
- 📂 TypeScript Support

---

## 🏗️ Architecture

```text
                    Client
                       │
                       ▼
              User Service (Express)
                       │
        ┌──────────────┼──────────────┐
        │              │              │
        ▼              ▼              ▼
 PostgreSQL      Auth Service    Utils Service
                       │
                       ▼
              JWT Authentication
```

The User Service manages user-specific operations while relying on the Auth Service for authentication. File uploads such as profile pictures and resumes are delegated to the Utils Service, whereas user information is stored in PostgreSQL.

---

# 🛠️ Tech Stack

| Category | Technologies |
|----------|--------------|
| Runtime | Node.js |
| Language | TypeScript |
| Framework | Express.js |
| Database | PostgreSQL |
| Authentication | JWT |
| HTTP Client | Axios |
| File Upload | Multer |
| Environment | dotenv |
| Deployment | Docker |

---

# 📁 Project Structure

```text
user-service/
│
├── src/
│   ├── controllers/
│   ├── middleware/
│   ├── routes/
│   ├── utils/
│   ├── index.ts
│   └── app.ts
│
├── Dockerfile
├── package.json
├── tsconfig.json
└── README.md
```

---

# 🌐 API Endpoints

| Method | Endpoint | Description |
|---------|----------|-------------|
| GET | `/me` | Get logged-in user profile |
| GET | `/:userId` | Get user profile by ID |
| PUT | `/update/profile` | Update user profile |
| PUT | `/update/pic` | Update profile picture |
| PUT | `/update/resume` | Update resume |
| POST | `/skill/add` | Add a skill |
| PUT | `/skill/delete` | Remove a skill |
| POST | `/apply/job` | Apply for a job |
| GET | `/application/all` | Get all job applications |

---

# 🔑 Authentication

All protected routes require a valid **JWT Access Token** issued by the **Auth Service**.

Authentication middleware verifies the token before allowing access to user-specific resources.

---

# ☁️ File Upload Integration

The User Service delegates file uploads to the **Utils Service** instead of storing files directly.

Supported uploads include:

- Profile Pictures
- Resume Documents

Benefits:

- Centralized file management
- Independent scaling
- Reduced service complexity
- Better separation of concerns

---

# 🐳 Docker

The project is fully containerized using Docker, enabling consistent deployments across different environments.

The Docker image packages the application along with all required dependencies for production-ready execution.

---

# 📦 Dependencies

Some of the primary packages used include:

- Express
- PostgreSQL
- JWT
- Axios
- Multer
- dotenv
- DataURI
- TypeScript

---

# 🛡️ Error Handling

The service includes centralized error handling for:

- Unauthorized requests
- Invalid user data
- File upload failures
- Missing resources
- Validation errors
- Database exceptions
- Internal server errors

---

# 🔗 Related Microservices

| Service | Description |
|----------|-------------|
| Auth Service | Handles authentication and JWT generation |
| Job Service | Manages job postings and applications |
| Payment Service | Processes subscriptions and payments |
| Utils Service | File uploads and utility operations |
```