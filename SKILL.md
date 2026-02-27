---
name: sequelize-optimized-enterprise-patterns
description: A brief description of what this skill does
---

# sequelize-optimized-enterprise-patterns

This skill enforces high-performance, predictable, and safe Sequelize usage for
large production schemas (Employee, Attendance, Reports, JSON fields, encryption).

---

## When to use

Use this skill when:
- Writing or refactoring Sequelize queries
- Optimizing slow APIs or reports
- Working with association-heavy schemas
- Handling encrypted columns or JSON fields
- Building list, dashboard, or analytics APIs
- Reviewing Sequelize code for performance issues

---

## Instructions

### 1. Query Construction (MANDATORY)

- ALWAYS specify `attributes` in queries
- NEVER fetch all columns using default behavior
- Use pagination (`limit` + `offset`) for all list APIs
- Prefer `raw: true` for read-only queries
- Use `subQuery: false` for large include trees

---

### 2. Association Handling

- Always define `attributes` inside `include`
- Avoid nested includes deeper than 2 levels
- Use `required: false` for optional associations
- Do NOT include associations unless required for response
- Avoid `through` attributes unless explicitly needed

---

### 3. Encrypted Field Rules

- NEVER decrypt fields inside loops
- NEVER fetch encrypted IDs unless required in response
- Prefer DB-level filtering on encrypted values
- Decrypt only at controller/service boundary if needed

---

### 4. Performance & Safety Rules

- Avoid N+1 queries at all costs
- Do NOT use `await` inside loops
- Prefer DB-level aggregation over JS computation
- Use indexed columns for filtering
- Avoid synchronous operations in request lifecycle

---

### 5. JSON / Metadata Columns

- Do NOT fetch full JSON blobs if only one key is needed
- Prefer DB JSON operators where supported
- Cache computed JSON values if reused
- Avoid parsing large JSON repeatedly in loops

---

### 6. Counts & Reports

- Use `Model.count()` with `distinct: true`
- Avoid `include` in count queries unless necessary
- Prefer `GROUP BY`, `SUM`, `COUNT`, `CASE` at DB level
- Attendance/report stats MUST be computed in SQL

---

### 7. Validation Before Final Output

Before returning Sequelize code, ensure:
- No unnecessary columns are fetched
- Pagination is applied where needed
- No encrypted data is leaked
- No N+1 query patterns exist
- Query intent is clear and readable

If optimization intent is unclear, ASK for clarification
instead of guessing.

---

## Expected Outcome

When this skill is active, the agent should:
- Generate efficient, production-ready Sequelize queries
- Avoid common ORM performance pitfalls
- Minimize payload size and DB load
- Respect encryption and data-safety boundaries
- Produce readable and maintainable code