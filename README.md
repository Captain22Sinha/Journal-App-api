# End-to-End Encrypted Journal App API

## Overview
This is an End-to-End Encrypted Journal App API built with Spring Boot, MongoDB, and Spring Security. The application allows users to securely store and manage their journal entries with encryption to ensure privacy and security.

## Features
- **User Authentication**: Leveraging Spring Security for user authentication and authorization.
- **End-to-End Encryption**: Journal entries are encrypted before being stored in the database, ensuring only authorized users can access them.
- **RESTful API**: Built with REST principles for easy integration with front-end applications.
- **MongoDB Integration**: Utilizes MongoDB for storing journal entries.

## Technologies Used
- **Spring Boot**: For building the RESTful service.
- **MongoDB**: NoSQL database for storing journal entries.
- **Spring Security**: For authentication and authorization of users.

## Getting Started
### Prerequisites
Before you get started, make sure you have the following installed:
- Java JDK 11 or higher
- Maven
- MongoDB

### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/Captain22Sinha/Journal-App-api.git
   ```
2. Navigate to the project directory:
   ```bash
   cd Journal-App-api
   ```
3. Build the application using Maven:
   ```bash
   mvn clean install
   ```
4. Configure the MongoDB database in the `application.properties` file:
   ```properties
   spring.data.mongodb.uri=mongodb://localhost:27017/journalapp
   ```

### Running the Application
Run the application using:
```bash
mvn spring-boot:run
```
The application will start on `http://localhost:8080`.

### API Endpoints
| Method | Endpoint                          | Description                           |
|--------|-----------------------------------|---------------------------------------|
| POST   | /api/auth/signup                  | Register a new user                  |
| POST   | /api/auth/login                   | User login                            |
| GET    | /api/journal/entries              | Get all journal entries               |
| POST   | /api/journal/entries              | Create a new journal entry            |
| GET    | /api/journal/entries/{id}         | Get a specific journal entry          |
| PUT    | /api/journal/entries/{id}         | Update a journal entry                |
| DELETE | /api/journal/entries/{id}         | Delete a journal entry                |

## Contributing
Contributions are welcome! Please fork the repository and submit a pull request with your changes.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments
- Developed by Captain22Sinha
- Inspired by various open-source projects and contributions from the community.