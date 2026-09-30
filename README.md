# Disaster Relief Management System

Full-stack web application developed as a graduate-level Software Engineering project using Agile methodologies. The system simulates disaster reporting, user management, and coordination workflows.

Built with **Java Spring Boot**, **React**, and **MySQL**.

## Tech Stack

- **Backend:** Java 8, Spring Boot 2.2, Spring Data JPA, Spring Data REST, Spring Web
- **Frontend:** React 16, Webpack, Babel
- **Database:** MySQL
- **Build:** Gradle + Node.js (for frontend bundling)
- **Other:** Thymeleaf (templating support)

## Features

- User registration and management (CRUD operations)
- REST API endpoints for user data
- React frontend that consumes the API and displays user information
- JPA entity mapping with Hibernate
- Database schema management via SQL scripts and Hibernate DDL
- Modular structure with separate packages for authentication, requests, and commands
- Integrated frontend build pipeline (Webpack runs as part of the Gradle build)

## Prerequisites

- JDK 8+
- MySQL 5.7+ (or compatible) running locally
- Node.js & npm
- Git

## Database Setup

The application expects a MySQL database named `seproject7` with the following credentials (configurable in `src/main/resources/application.properties`):

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/seproject7
spring.datasource.username=springuser
spring.datasource.password=S0m3!p@ssw0rd
```

Apply the schema:

```bash
mysql -u root -p < db/seproject7.sql
mysql -u root -p < db/user.sql
```

## Running the Application

```bash
# Install frontend dependencies and build
./gradlew build

# Run
./gradlew bootRun
```

The application starts on `http://localhost:8080`.

### Key Endpoints

| Method | Endpoint          | Description              |
|--------|-------------------|--------------------------|
| POST   | `/user/add`       | Create a new user        |
| GET    | `/user/get`       | Retrieve user by name    |
| GET    | `/user/all`       | List all users           |
| GET    | `/api/...`        | Spring Data REST endpoints |

## Project Structure

```
├── db/                          # Database schema scripts
├── src/main/java/.../           # Spring Boot application
│   ├── Application.java         # Entry point
│   ├── User.java                # JPA entity
│   ├── UserController.java      # REST controller
│   ├── UserRepository.java      # Spring Data repository
│   ├── login/                   # Authentication & cryptography
│   ├── requests/                # Request handling
│   └── command/                 # Command listeners
├── src/main/js/                 # React frontend source
├── src/main/resources/          # application.properties, static assets
├── build.gradle                 # Gradle build configuration
└── webpack.config.js            # Frontend build config
```

## Development Notes

This project was developed iteratively using Agile practices as part of a graduate Software Engineering course. The system models core workflows for disaster reporting and resource coordination without connecting to live external systems.

The frontend is bundled via Webpack as part of the Gradle `processResources` task.
```