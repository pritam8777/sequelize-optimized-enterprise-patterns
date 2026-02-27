# Sequelize Enterprise Optimization

Description: Opinionated Sequelize performance and query optimization rules
for enterprise Node.js backends using encrypted fields, heavy associations,
and reporting-style queries.

## Rules

### MUST
- Always specify `attributes` in queries
- Use pagination for list APIs
- Avoid N+1 queries
- Use DB-level aggregation instead of JS loops
- Avoid decrypting fields inside loops

### MUST NOT
- Fetch encrypted fields unless required
- Use `findAll()` without limit/offset
- Include associations without attributes
- Run awaits inside loops