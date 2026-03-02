---
name: swagger-route-generator-with-joi
description: Generate Swagger (OpenAPI 3.0) routes with Express handlers and
JOI-based request validation using separate validation files per payload.
---

# swagger-route-generator-with-joi

This skill enforces consistent API documentation, routing, and validation
by generating Swagger docs, Express routes, and JOI validation schemas
together in a predictable structure.

---

## When to use

Use this skill when:
- Creating new REST APIs
- Adding Swagger documentation
- Implementing request validation using JOI
- Refactoring or reviewing existing APIs
- Enforcing consistency between Swagger and runtime validation

---

## Instructions

### 1. OpenAPI Standards (MANDATORY)

- ALWAYS use **OpenAPI 3.0**
- Define APIs under `paths`
- Use reusable schemas under `components.schemas`
- Use reusable responses where applicable
- Keep Swagger and JOI schemas logically aligned

---

### 2. Route Generation Rules

For every API route:
- MUST define `summary`
- MUST define `tags`
- MUST define request parameters
- MUST define requestBody (if applicable)
- MUST define responses
- MUST include HTTP status codes

Swagger routes MUST reflect the actual Express routes.

---

### 3. Express Route Structure

Routes MUST follow this structure:

```text
routes/
 └── user.routes.js
controllers/
 └── user.controller.js
validations/
 └── user.validation.js