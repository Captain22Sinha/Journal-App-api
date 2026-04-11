# Journal App API

A Spring Boot REST API for managing personal journal entries with user authentication and MongoDB persistence.

## Overview

Journal App API is a backend service that provides RESTful endpoints for creating, reading, updating, and deleting journal entries. It features user authentication, secure storage with Spring Security, and MongoDB integration for reliable data persistence.

## Tech Stack

- **Java 17** - Core programming language
- **Spring Boot 3.5.13** - Framework for building the REST API
- **Spring Data MongoDB** - ORM for MongoDB database operations
- **Spring Security** - Authentication and authorization
- **Spring Web** - REST API development
- **Lombok** - Reduces boilerplate code
- **Maven** - Build and dependency management
- **SonarQube** - Code quality analysis

## Project Structure

```
src/main/
├── java/net/edigest/journalApp/
│   ├── JournalApplication.java        # Main Spring Boot application
│   ├── api/                           # API response models
│   ├── config/                        # Configuration classes
│   ├── controller/                    # REST controllers
│   ├── entity/                        # Domain models (JournalEntry, User)
│   ├── repository/                    # MongoDB repositories
│   └── service/                       # Business logic layer
└── resources/
    └── logback.xml                    # Logging configuration
```

## Key Features

- **User Management** - User registration and profile management
- **Journal Entry CRUD** - Create, read, update, and delete journal entries
- **Security** - Spring Security integration for authentication
- **Transaction Support** - MongoDB transaction management enabled
- **REST API** - Clean and intuitive RESTful endpoints
- **Logging** - Comprehensive logging with Logback

## Prerequisites

- Java 17 or higher
- Maven 3.6+
- MongoDB 4.0+

## Getting Started

### Installation

1. Clone the repository:
```bash
git clone https://github.com/Captain22Sinha/Journal-App-api.git
cd Journal-App-api
```

2. Configure MongoDB connection in `application.properties` or `application.yml`:
```properties
spring.data.mongodb.uri=mongodb://localhost:27017/journalapp
```

3. Build the project:
```bash
./mvnw clean install
```

4. Run the application:
```bash
./mvnw spring-boot:run
```

The API will start on `http://localhost:8080`

## API Endpoints

### User Endpoints
- `POST /api/users` - Create a new user
- `GET /api/users/{id}` - Get user by ID
- `PUT /api/users/{id}` - Update user
- `DELETE /api/users/{id}` - Delete user

### Journal Entry Endpoints
- `POST /api/entries` - Create a new journal entry
- `GET /api/entries` - Get all entries for the authenticated user
- `GET /api/entries/{id}` - Get a specific entry
- `PUT /api/entries/{id}` - Update an entry
- `DELETE /api/entries/{id}` - Delete an entry

## Configuration

### Application Properties

Key configuration options available in `application.properties`:

```properties
# Server
server.port=8080

# MongoDB
spring.data.mongodb.uri=mongodb://localhost:27017/journalapp

# Logging
logging.level.root=INFO
logging.level.net.edigest.journalApp=DEBUG
```

## Dependencies

Key dependencies included:

- `spring-boot-starter-web` - Web development
- `spring-boot-starter-data-mongodb` - MongoDB support
- `spring-boot-starter-security` - Security features
- `spring-boot-starter-test` - Testing support
- `lombok` - Code generation
- `sonar-maven-plugin` - Code quality scanning

## Building and Testing

### Build the project:
```bash
./mvnw clean build
```

### Run tests:
```bash
./mvnw test
```

### Code Quality Analysis:
```bash
./mvnw sonar:sonar
```

## Project Architecture

The application follows a layered architecture:

- **Controller Layer** - Handles HTTP requests and responses
- **Service Layer** - Contains business logic
- **Repository Layer** - Data access layer with MongoDB
- **Entity Layer** - Domain models and data structures
- **Config Layer** - Spring configuration and bean definitions
- **API Layer** - API response models and DTOs

## Transaction Management

MongoDB transactions are enabled and configured in the main application class. Transactions are managed by the `MongoTransactionManager` bean, allowing ACID properties for multi-document operations.

## Development

### Code Quality
This project uses SonarQube for code quality analysis. Configure your SonarQube organization in `pom.xml`:

```xml
<sonar.organization>captain22sinha</sonar.organization>
```

### Logging
The application uses Logback for logging configuration. Adjust logging levels in `logback.xml` as needed.

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is open source and available under the MIT License.

## Author

**Captain22Sinha**

## Support

For support or questions, please open an issue on the GitHub repository.

## Changelog

### Version 0.0.1-SNAPSHOT
- Initial project setup
- User and JournalEntry entities
- RESTful API endpoints
- MongoDB integration
- Spring Security integration
- Transaction management enabled
