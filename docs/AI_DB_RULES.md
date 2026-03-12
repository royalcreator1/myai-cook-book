# AI Database Design Rules

You are designing database queries for a **scalable backend system**.

Always assume:

* large datasets
* high concurrency
* growing user base

---

# 1. Query Design Principles

Always prioritize:

performance
index usage
minimal database round trips

Avoid:

N+1 queries
full table scans on large tables

---

# 2. Preferred Query Patterns

Use:

indexed filters
pagination for list endpoints
select only required columns

Avoid selecting unnecessary fields.

Example:

Prefer:

SELECT id, name FROM users

Instead of:

SELECT * FROM users

---

# 3. Pagination

All list endpoints must support pagination.

Preferred pattern:

limit + offset

Example:

limit = 50
offset = page * limit

---

# 4. Indexing

When designing new queries:

check if index exists.

Add index if query frequently filters by:

user_id
email
department_id
created_at

Avoid unnecessary indexes because they slow down writes.

---

# 5. Bulk Operations

When processing multiple records:

Prefer batch operations.

Example:

bulk inserts
bulk updates

Avoid looping database queries inside application code.

---

# 6. Transactions

Use transactions when:

multiple operations must succeed together.

Example:

creating a request and updating balance.

Ensure rollback on failure.

---

# 7. Data Consistency

Ensure:

foreign key relationships
referential integrity
consistent field naming

Example:

user_id
department_id

Avoid inconsistent naming like:

userid
deptid

---

# 8. Date Storage

Dates should be stored in standard database date formats.

Application display format:

MM-DD-YYYY

Example:

04-25-2026

---

# 9. Soft Deletes

When records should not be permanently removed:

use soft delete pattern.

Example field:

deleted_at

This preserves historical data.

---

# 10. Query Optimization

Before modifying queries:

analyze current query performance.

Prefer improvements like:

index usage
query simplification
reducing joins when possible
