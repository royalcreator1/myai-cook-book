# AI-Assisted Development Guidelines

This repository is designed to be developed with the help of AI coding agents such as Codex, Cursor, Claude, or GitHub Copilot.

To ensure consistent, secure, and maintainable code, this project includes **AI rule files** that define architecture standards, database practices, testing rules, and engineering principles.

AI agents working in this repository **must read these documents before writing or modifying code.**

---

# 1. AI Knowledge Files

The repository includes a set of documents that guide AI behavior.

docs/

AI_ARCHITECTURE.md
AI_DB_RULES.md
AI_TESTING_RULES.md

Root:

AI_ENGINEERING_RULES.md

Each document provides specific guidance for the AI agent.

---

# 2. Purpose of Each File

## AI_ENGINEERING_RULES.md

This is the **main instruction file** for AI agents.

It defines:

* coding principles (KISS, YAGNI, DRY)
* security rules
* response format
* bug fixing workflow
* error handling rules
* API design standards

This file should always be read first.

---

## docs/AI_ARCHITECTURE.md

Defines the **project architecture structure**.

Includes:

* layered architecture rules
* separation of responsibilities
* controller/service/repository boundaries
* dependency flow
* module organization

This ensures the AI respects the system design.

---

## docs/AI_DB_RULES.md

Defines **database design standards**.

Includes:

* query optimization practices
* indexing guidelines
* pagination rules
* transaction usage
* scalable query design

These rules ensure the system performs well at scale.

---

## docs/AI_TESTING_RULES.md

Defines **testing expectations**.

Includes:

* unit test design
* API test rules
* edge case testing
* mocking strategy
* regression prevention

AI should add or update tests when modifying logic.

---

# 3. Required AI Workflow

When an AI agent performs any coding task, it must follow this workflow.

Step 1
Read the following files:

AI_ENGINEERING_RULES.md
docs/AI_ARCHITECTURE.md
docs/AI_DB_RULES.md
docs/AI_TESTING_RULES.md

Step 2
Understand existing code before writing new code.

Step 3
Reuse existing helpers, services, and utilities whenever possible.

Step 4
Implement changes with minimal modifications.

Step 5
Follow the architecture and database rules.

Step 6
Provide a short summary of changes at the end.

---

# 4. How to Prompt AI Agents

When interacting with AI tools, always begin prompts like this:

Read AI_ENGINEERING_RULES.md and docs/*.md before writing code.

Task: <describe your task>

Example:

Read AI_ENGINEERING_RULES.md and docs/*.md before writing code.

Task:
Add pagination to the users API.

Example bug fix prompt:

Read AI_ENGINEERING_RULES.md and docs/*.md before writing code.

fix it tom!

Users API throws a 500 error when department_id is null.

---

# 5. Repository Structure

Recommended project layout:

project/

src/
controllers/
services/
repositories/
models/
utils/

tests/

docs/
AI_ARCHITECTURE.md
AI_DB_RULES.md
AI_TESTING_RULES.md

AI_ENGINEERING_RULES.md
README.md

---

# 6. Security Rules

AI must never:

* read `.env` files
* expose secrets
* print tokens or credentials
* log sensitive data

Sensitive files:

.env
.env.*
credentials/
secrets/

---

# 7. Coding Principles

All code must follow:

KISS – Keep It Simple
YAGNI – Avoid unnecessary features
DRY – Avoid duplicated logic

Prefer improving existing code instead of creating new abstractions.

---

# 8. Performance Considerations

Assume the application may scale to a large number of users.

AI must:

* avoid N+1 queries
* prefer indexed queries
* minimize database round trips
* design efficient APIs

---

# 9. Date Format

All user-facing dates must use:

MM-DD-YYYY

Example:

04-25-2026

---

# 10. Response Format Requirement

Every AI response must end with:

### Changes Summary

Example:

### Changes Summary

* Fixed null handling in users service
* Reused validation helper
* Added pagination to user listing
* Improved database query performance

---

# 11. Bug Fix Workflow

If a prompt begins with:

fix it tom!

AI must:

1. analyze existing code
2. identify root cause
3. reuse existing utilities
4. fix with minimal changes
5. avoid rewriting working code

---

# 12. When Adding Features

AI must:

* check existing services before creating new ones
* maintain layer separation
* keep controllers thin
* add tests when modifying logic

---

# 13. Continuous Improvement

These AI guidance documents should evolve with the project.

When architecture or design patterns change, update the relevant rule files.

Keeping these documents accurate ensures AI agents produce high-quality code.

