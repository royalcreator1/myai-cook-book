# AI Testing Guidelines

Testing ensures system reliability and prevents regressions.

Whenever logic changes, verify that existing functionality remains stable.

---

# 1. Testing Philosophy

Tests should verify:

expected behavior
edge cases
error conditions

Tests should not depend on internal implementation details.

---

# 2. Test Types

Primary tests used in this project:

Unit Tests
API Tests

---

# 3. Unit Tests

Unit tests focus on individual components.

Examples:

service logic
validation functions
utility helpers

Unit tests should:

run fast
be isolated
avoid external dependencies

---

# 4. API Tests

API tests verify:

request validation
response structure
status codes

Ensure endpoints return correct responses.

---

# 5. Test Coverage

When modifying logic:

update or add tests.

Important areas:

authentication
business rules
data updates
error handling

---

# 6. Edge Cases

Always test edge cases.

Examples:

null values
empty inputs
invalid IDs
duplicate records

Edge cases often reveal hidden bugs.

---

# 7. Mocking

When testing services:

mock external systems.

Examples:

external APIs
notification systems
third-party integrations

This ensures tests remain stable.

---

# 8. Deterministic Tests

Tests must produce consistent results.

Avoid:

random data without control
time dependent tests without mocking time

---

# 9. Naming Conventions

Test names should describe behavior.

Example:

test_create_user_success
test_create_user_missing_email
test_update_user_invalid_department

---

# 10. Test Structure

Recommended pattern:

Arrange
Act
Assert

Arrange → prepare test data
Act → execute functionality
Assert → verify result

---

# 11. Regression Prevention

Whenever a bug is fixed:

add a test case reproducing that bug.

This prevents the same issue from returning later.
