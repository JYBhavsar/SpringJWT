# SpringJWT

A robust Spring Boot REST API starter project that demonstrates secure authentication and authorization using JWT (JSON Web Token). It supports user registration, login, role-based access control, and leverages Spring Security for best-in-class security practices. Ideal for modern web and mobile backends requiring secure authentication flows.

---

## Table of Contents

- [About the Project](#about-the-project)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Running the Application](#running-the-application)
- [API Endpoints](#api-endpoints)
- [Usage Examples](#usage-examples)
- [Project Structure](#project-structure)
- [Testing](#testing)
- [Security Details](#security-details)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

---

## About the Project

SpringJWT is designed as a starter template for building secure RESTful APIs with Spring Boot. It features:

- User registration (signup) and login (signin)
- Role-based access control (USER, MODERATOR, ADMIN)
- JWT token generation and validation
- Stateless session management
- Easily extensible for custom requirements

This project is perfect for showcasing your skills in Spring Boot, security, and backend API development.

---

## Features

- **User Registration & Authentication:** Secure signup and login endpoints with JWT-based authentication.
- **Role-Based Authorization:** Granular access using roles: `USER`, `MODERATOR`, and `ADMIN`.
- **Spring Security Integration:** Fully configured using Spring Security for modern security best practices.
- **Password Encryption:** Uses BCrypt for password hashing.
- **Stateless API:** No server-side session storage; everything is JWT-based.
- **Comprehensive Error Handling:** API responses are clear and informative.
- **Ready-to-extend:** Easily add more endpoints, roles, or customize security.

---

## Tech Stack

- **Java 17+** (or compatible version)
- **Spring Boot**
- **Spring Security**
- **JWT (io.jsonwebtoken)**
- **Spring Data JPA** (with any JPA-compatible DB)
- **JUnit 5** (for testing)

---

## Getting Started

### Prerequisites

- Java 17 or higher
- Maven 3.6+
- (Recommended) Docker, for running databases

### Installation

1. **Clone the repository:**
   ```sh
   git clone https://github.com/JYBhavsar/SpringJWT.git
   cd SpringJWT
   ```

2. **Configure database (if needed):**
   - Edit `src/main/resources/application.properties` for your DB connection.

3. **Install dependencies:**
   ```sh
   mvn clean install
   ```

### Running the Application

```sh
mvn spring-boot:run
```
The API will be available at `http://localhost:8082/`

---

## API Endpoints

| Endpoint                     | Method | Description               | Access         |
|------------------------------|--------|---------------------------|---------------|
| /api/auth/signup             | POST   | User registration         | Public        |
| /api/auth/signin             | POST   | User login                | Public        |
| /api/test/all                | GET    | Public content            | Public        |
| /api/test/user               | GET    | User content              | USER+         |
| /api/test/mod                | GET    | Moderator content         | MODERATOR+    |
| /api/test/admin              | GET    | Admin content             | ADMIN         |

---

## Usage Examples

### Signup (POST `/api/auth/signup`)
```json
{
  "username": "jay",
  "email": "bhavsarjay@gmail.com",
  "password": "password",
  "roles": ["user", "admin", "moderator"]
}
```

### Signin (POST `/api/auth/signin`)
```json
{
  "username": "mod",
  "password": "password"
}
```
**Response:**
```json
{
  "id": 3,
  "username": "mod",
  "email": "bhavsarjay01@gmail.com",
  "roles": ["ROLE_USER"],
  "accessToken": "eyJhbGciOiJIUzUxMiJ9.eyJzdWIi...",
  "tokenType": "Bearer"
}
```

### Accessing Protected Content
- Use the `accessToken` as a Bearer token in the `Authorization` header.
- Example: `Authorization: Bearer <accessToken>`

---

## Project Structure

```
src/
  main/
    java/
      com/example/
        controllers/      # API controllers (Auth, Test)
        models/           # Entity and enum classes (User, Role, ERole)
        payload/          # Request and response payloads
        repository/       # JPA repositories (UserRepository, RoleRepository)
        security/         # JWT utils, filters, security configs
    resources/
      application.properties
  test/
    java/
      com/example/
        DemoApplicationTests.java
```
- See `CallApis.md` for more usage examples.

---

## Testing

- Run all tests using:
  ```sh
  mvn test
  ```
- Includes minimal context loading tests; expand with integration tests as needed.

---

## Security Details

- **JWT Authentication:** Token generation/validation in `JwtUtils.java`.
- **Custom UserDetailsService:** Loads user details from DB.
- **Role-based method security:** Secured endpoints using `@PreAuthorize`.
- **Exception Handling:** Unauthorized access managed by `AuthEntryPointJwt`.

---

## Contributing

Contributions, issues, and feature requests are welcome!  
Feel free to fork this repo and submit a pull request.

---

## License

Distributed under the MIT License. See [`LICENSE`](LICENSE) for more information.

---

## Contact

- **Author:** JYBhavsar
- **GitHub:** [JYBhavsar](https://github.com/JYBhavsar)

---

*This project is a great starting point for any modern Java/Spring backend requiring secure authentication and RBAC. Showcases expertise in Spring Boot, Security, and REST API development.*
