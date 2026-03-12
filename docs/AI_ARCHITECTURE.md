# AI Architecture Guidelines

You are working on a backend system that follows **Layered Architecture**.

Always follow these structural principles when adding or modifying code.

---

# 1. Architectural Layers

The system is divided into the following layers.

controllers
services
repositories
models
utils/helpers

Each layer has a specific responsibility.

---

# 2. Layer Responsibilities

## Controllers

Responsibilities:

Handle HTTP requests and responses
Validate incoming request data
Call service layer

Controllers must NOT contain business logic.

Example responsibilities:

* request validation
* authentication checks
* returning API responses

---

## Services

Services contain **core business logic**.

Responsibilities:

* implement business workflows
* call repositories for data access
* coordinate multiple components

Services should never contain:

* HTTP request handling
* raw database queries

---

## Repositories

Repositories handle **database interaction only**.

Responsibilities:

* CRUD operations
* optimized queries
* mapping database results

Repositories must not include business rules.

---

## Models

Models represent database entities.

Responsibilities:

* schema definition
* relationships
* serialization if needed

Models should not contain heavy business logic.

---

## Utils / Helpers

Reusable utilities used across the application.

Examples:

* date helpers
* formatting functions
* validation helpers
* common query helpers

Always check utils before creating new helper logic.

---

# 3. Dependency Direction

Allowed dependencies:

controllers → services
services → repositories
repositories → models

Not allowed:

repositories calling services
models calling services
controllers directly querying database

---

# 4. Adding New Features

When implementing new functionality:

1. Check if existing services already handle similar logic
2. Extend existing service when possible
3. Add repository methods only if required
4. Keep controller thin

---

# 5. Code Organization

Prefer small, focused modules.

Example:

services/
user_service.py
auth_service.py

repositories/
user_repository.py
department_repository.py

controllers/
user_controller.py
auth_controller.py

---

# 6. Scalability Considerations

Always assume the system will grow.

Prefer:

stateless services
clear boundaries between layers
reusable services
modular structure

Avoid tight coupling between modules.

---

# 7. Refactoring Rules

When refactoring:

* do not change external API contracts unless required
* keep changes minimal
* preserve existing behavior
* reuse utilities

Refactoring should improve readability without breaking functionality.
