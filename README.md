# 📔 Journal App API

A comprehensive REST API for managing personal journal entries with user authentication, authorization, and secure data storage.

## 🎯 Overview

Journal App API is a Spring Boot-based backend service that enables users to create, manage, and organize their journal entries. It provides role-based access control with admin and user roles, secure authentication, and persistent data storage using MongoDB.

## ✨ Key Features

- **User Authentication & Authorization**: Spring Security with role-based access control (USER, ADMIN)
- **Journal Entry Management**: Full CRUD operations for personal journal entries
- **Secure Access**: Each user can only access their own journal entries
- **MongoDB Integration**: Non-relational database for flexible document storage
- **Transaction Support**: Enabled for data consistency with MongoDB
- **Admin Controls**: Admin endpoints for user management
- **RESTful API Design**: Clean, intuitive endpoints following REST principles

## 🛠️ Tech Stack

| Technology | Purpose |
|-----------|---------|
| **Java 17** | Programming language |
| **Spring Boot 3.5.13** | Application framework |
| **Spring Security** | Authentication & authorization |
| **Spring Data MongoDB** | Database ORM |
| **MongoDB** | NoSQL database |
| **Lombok** | Reducing boilerplate code |
| **Maven** | Build and dependency management |
| **SonarQube** | Code quality analysis |

## 📋 Prerequisites

Before running the application, ensure you have:

- **Java 17** or higher installed
- **Maven 3.6+** installed
- **MongoDB** running locally or accessible via network
- **Git** for cloning the repository

## 🚀 Getting Started

### 1. Clone the Repository
```bash
git clone https://github.com/Captain22Sinha/Journal-App-api.git
cd Journal-App-api
```

### 2. Configure MongoDB Connection
Update `src/main/resources/application.properties` with your MongoDB connection details:
```properties
spring.data.mongodb.uri=mongodb://localhost:27017/journalApp
spring.data.mongodb.database=journalApp
```

### 3. Build the Application
```bash
./mvnw clean install
```

### 4. Run the Application
```bash
./mvnw spring-boot:run
```

The API will start on `http://localhost:8080`

## 📚 API Endpoints

### Public Endpoints (No Authentication Required)

#### Health Check
```
GET /public/health-check
Response: "OK"
```

#### Create User
```
POST /public/create-user
Content-Type: application/json

Request Body:
{
  "userName": "john_doe",
  "password": "secure_password",
  "roles": ["USER"]
}

Response: 200 OK
```

### User Endpoints (Authentication Required - USER Role)

#### Get All Journal Entries
```
GET /journal
Authorization: Bearer {token}

Response: 
[
  {
    "id": "507f1f77bcf86cd799439011",
    "title": "My First Entry",
    "content": "Today was a great day...",
    "date": "2026-04-04T10:30:00"
  }
]
```

#### Create Journal Entry
```
POST /journal
Authorization: Bearer {token}
Content-Type: application/json

Request Body:
{
  "title": "My Entry Title",
  "content": "Entry content goes here",
  "date": "2026-04-04T10:30:00"
}

Response: 201 CREATED
```

#### Get Specific Journal Entry
```
GET /journal/id/{entryId}
Authorization: Bearer {token}

Response:
{
  "id": "507f1f77bcf86cd799439011",
  "title": "My First Entry",
  "content": "Today was a great day...",
  "date": "2026-04-04T10:30:00"
}
```

#### Update Journal Entry
```
PUT /journal/id/{entryId}
Authorization: Bearer {token}
Content-Type: application/json

Request Body:
{
  "title": "Updated Title",
  "content": "Updated content"
}

Response: 200 OK
```

#### Delete Journal Entry
```
DELETE /journal/id/{entryId}
Authorization: Bearer {token}

Response: 204 NO CONTENT
```

#### Update User Profile
```
PUT /user
Authorization: Bearer {token}
Content-Type: application/json

Request Body:
{
  "userName": "new_username",
  "password": "new_password"
}

Response: 204 NO CONTENT
```

#### Delete User Account
```
DELETE /user
Authorization: Bearer {token}

Response: 204 NO CONTENT
```

### Admin Endpoints (Authentication Required - ADMIN Role)

#### Get All Users
```
GET /admin/all-users
Authorization: Bearer {token}

Response:
[
  {
    "id": "507f1f77bcf86cd799439012",
    "userName": "admin_user",
    "roles": ["ADMIN"]
  }
]
```

#### Create Admin User
```
POST /admin/create-admin-user
Authorization: Bearer {token}
Content-Type: application/json

Request Body:
{
  "userName": "new_admin",
  "password": "admin_password",
  "roles": ["ADMIN"]
}

Response: 200 OK
```

## 📁 Project Structure

```
src/
├── main/
│   ├── java/net/edigest/journalApp/
│   │   ├── JournalApplication.java          # Spring Boot main application
│   │   ├── controller/
│   │   │   ├── JournalEntryController.java  # Journal entry endpoints
│   │   │   ├── UserController.java          # User management endpoints
│   │   │   ├── AdminController.java         # Admin endpoints
│   │   │   └── PublicController.java        # Public endpoints
│   │   ├── entity/
│   │   │   ├── User.java                    # User document model
│   │   │   └── JournalEntry.java            # Journal entry document model
│   │   ├── service/
│   │   │   ├── UserService.java             # User business logic
│   │   │   └── JournalEntryService.java     # Journal entry business logic
│   │   └── repository/
│   │       ├── UserRepository.java          # User data access
│   │       └── JournalEntryRepository.java  # Journal entry data access
│   └── resources/
│       └── application.properties           # Application configuration
└── test/
    └── java/...                              # Unit and integration tests
```

## 🔐 Security Features

- **Spring Security**: Implements authentication and authorization
- **Role-Based Access Control**: Different endpoints for USER and ADMIN roles
- **Password Storage**: Secure password handling (ensure proper encoding in production)
- **Request Validation**: Input validation on all endpoints
- **User Isolation**: Users can only access their own data

## 📊 Database Schema

### Users Collection
```json
{
  "_id": ObjectId,
  "userName": "string (unique, required)",
  "password": "string (required)",
  "journalEntries": [ObjectId],
  "roles": ["USER" | "ADMIN"]
}
```

### Journal Entries Collection
```json
{
  "_id": ObjectId,
  "title": "string (required)",
  "content": "string",
  "date": "LocalDateTime"
}
```

## 🧪 Testing

Run the test suite with:
```bash
./mvnw test
```

For integration tests with MongoDB:
```bash
./mvnw verify
```

## 🔍 Code Quality

This project uses SonarQube for code quality analysis. To run SonarQube analysis:
```bash
./mvnw sonar:sonar
```

## 📝 Example Usage

### Create a User
```bash
curl -X POST http://localhost:8080/public/create-user \
  -H "Content-Type: application/json" \
  -d '{
    "userName": "john_doe",
    "password": "mypassword",
    "roles": ["USER"]
  }'
```

### Create a Journal Entry
```bash
curl -X POST http://localhost:8080/journal \
  -H "Authorization: Bearer {YOUR_TOKEN}" \
  -H "Content-Type: application/json" \
  -d '{
    "title": "My Day",
    "content": "Today was productive!",
    "date": "2026-04-04T15:30:00"
  }'
```

## 🤝 Contributing

We welcome contributions! Here's how:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is open source and available under the MIT License.

## 👤 Author

**Captain22Sinha**
- GitHub: [@Captain22Sinha](https://github.com/Captain22Sinha)

## 💬 Support

For questions or issues, please:
- Open an issue on GitHub
- Check existing documentation
- Review the API endpoints above

## 🎓 Learning Resources

- [Spring Boot Documentation](https://spring.io/projects/spring-boot)
- [Spring Security Guide](https://spring.io/guides/gs/securing-web/)
- [MongoDB Documentation](https://docs.mongodb.com/)
- [REST API Best Practices](https://restfulapi.net/)

---

Made with ❤️ by Captain22Sinha