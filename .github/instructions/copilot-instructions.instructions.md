# GitHub Copilot Instructions — Spring Boot Petstore API

## Objective

Build and maintain a clean, production-ready Spring Boot REST API for a Petstore system.

---

## Tech Stack

* Java 17+
* Spring Boot (latest stable)
* Spring Web, Spring Data JPA
* H2 (dev) / PostgreSQL (prod)
* Maven (preferred) or Gradle
* Lombok (optional but preferred for boilerplate reduction)

---

## Project Structure

Follow standard layered architecture:

* controller → REST endpoints
* service → business logic
* repository → database access
* model/entity → JPA entities
* dto → request/response objects
* exception → custom exceptions + handlers
* config → configuration classes

---

## Domain Model (Minimum)

Implement these core entities:

* Pet

  * id (Long)
  * name (String)
  * type (String)
  * age (Integer)
  * status (AVAILABLE, SOLD, PENDING)

* Order

  * id
  * petId
  * quantity
  * status
  * shipDate

* User

  * id
  * username
  * email
  * password (hashed)

---

## API Guidelines

* Use REST conventions
* Base path: /api/v1
* Return proper HTTP status codes
* Use DTOs for all external responses (never expose entities directly)
* Validate inputs using @Valid

---

## Required Endpoints

### Pet

* GET /pets
* GET /pets/{id}
* POST /pets
* PUT /pets/{id}
* DELETE /pets/{id}

### Order

* POST /orders
* GET /orders/{id}

### User

* POST /users
* GET /users/{id}

---

## Coding Standards

* Prefer constructor injection over field injection
* Keep controllers thin, logic in services
* Use meaningful method and variable names
* Avoid hardcoding values
* Write reusable, testable methods

---

## Error Handling

* Use @ControllerAdvice
* Create custom exceptions (e.g., ResourceNotFoundException)
* Return structured error responses:
  {
  timestamp,
  status,
  error,
  message,
  path
  }

---

## Persistence Rules

* Use Spring Data JPA repositories
* Avoid N+1 queries
* Use pagination for list endpoints

---

## Security (Basic)

* Hash passwords using BCrypt
* Never store plain text passwords
* Add basic authentication or JWT if asked

---

## Testing

* Write unit tests for services
* Use MockMvc for controller tests
* Cover happy path + edge cases

---

## Documentation

* Add OpenAPI/Swagger support
* Keep README updated with:

  * setup steps
  * API endpoints
  * sample requests

---

## Development Workflow

* Create small, focused commits
* Use clear commit messages
* Keep PRs small and reviewable

---

## Copilot Behavior Instructions

* Always generate production-quality code, not demo code
* Prefer simplicity over cleverness
* If unsure, choose widely accepted Spring Boot patterns
* Do NOT introduce unnecessary frameworks
* Do NOT duplicate logic across layers
* When adding new features, update:

  * DTOs
  * Service layer
  * Controller
  * Tests

---

## Anti-Patterns to Avoid

* Fat controllers
* Direct entity exposure
* Business logic inside repositories
* Silent exception swallowing
* Magic strings or numbers

---

## Definition of Done

A feature is complete only if:

* API endpoint works
* Validation is in place
* Errors handled properly
* Tests added
* Documentation updated

---

Repository owner: myounus1215
