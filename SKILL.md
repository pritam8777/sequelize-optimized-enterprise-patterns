# Sequelize Enterprise Optimization

Description: Opinionated Sequelize performance and query optimization rules
for enterprise Node.js backends using encrypted fields and heavy associations.

## Rules
- Always select attributes explicitly
- Avoid N+1 queries
- Use pagination for list APIs
- Do not fetch encrypted fields unless required