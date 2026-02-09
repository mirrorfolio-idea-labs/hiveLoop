# Conventions

> Define your coding standards and patterns

---

## Naming Conventions

### Files
| Type | Convention | Example |
|------|------------|---------|
| Components | PascalCase | `UserProfile.tsx` |
| Utilities | camelCase | `formatDate.ts` |
| Styles | kebab-case | `user-profile.css` |
| Constants | UPPER_SNAKE | `API_BASE_URL` |

### Code
| Type | Convention | Example |
|------|------------|---------|
| Variables | camelCase | `userName` |
| Functions | camelCase | `getUserById()` |
| Classes | PascalCase | `UserService` |
| Constants | UPPER_SNAKE | `MAX_RETRIES` |
| Private | _prefix | `_internalMethod()` |

### Database
| Type | Convention | Example |
|------|------------|---------|
| Tables | snake_case | `user_profiles` |
| Columns | snake_case | `created_at` |
| Indexes | idx_table_column | `idx_users_email` |

---

## Architecture Patterns

### Frontend
- **State Management**: [Approach - e.g., Zustand stores]
- **Components**: [Pattern - e.g., Atomic design]
- **Data Fetching**: [Approach - e.g., React Query]

### Backend
- **API Style**: [REST/GraphQL]
- **Data Access**: [Pattern - e.g., Repository pattern]
- **Error Handling**: [Approach]

---

## Code Patterns

### Error Handling
```typescript
// ✅ DO: Use structured error handling
try {
  const result = await operation();
  return { success: true, data: result };
} catch (error) {
  logger.error('Operation failed', { error });
  return { success: false, error: 'User-friendly message' };
}

// ❌ DON'T: Let errors bubble unhandled
const result = await operation(); // No try-catch
```

### Async Operations
```typescript
// ✅ DO: Use async/await
const data = await fetchData();

// ❌ DON'T: Use .then() chains
fetchData().then(data => { ... });
```

---

## Security Patterns

### Authentication
- [Pattern description]

### Secrets
- ✅ Store in environment variables
- ❌ Never hardcode

### Password Handling
- ✅ Always hash with [algorithm]
- ❌ Never store plain text

---

## API Conventions

### Endpoints
| Method | Pattern | Example |
|--------|---------|---------|
| GET | /resources | GET /users |
| GET | /resources/:id | GET /users/123 |
| POST | /resources | POST /users |
| PUT | /resources/:id | PUT /users/123 |
| DELETE | /resources/:id | DELETE /users/123 |

### Status Codes
| Code | Use Case |
|------|----------|
| 200 | Success |
| 201 | Created |
| 400 | Bad request |
| 401 | Unauthorized |
| 404 | Not found |
| 500 | Server error |

---

## Anti-Patterns

> ❌ These are prohibited:

| Pattern | Problem | Instead |
|---------|---------|---------|
| `any` type | Loses type safety | Use proper types |
| Hardcoded URLs | Environment-dependent | Use env vars |
| Direct DB in routes | Tight coupling | Use repositories |
| Console.log | Pollutes output | Use logger |

---

## Testing

### Test Structure
```
tests/
├── unit/           # Unit tests
├── integration/    # Integration tests
└── e2e/           # End-to-end tests
```

### Naming
- Test files: `*.test.ts` or `*.spec.ts`
- Describe blocks: Feature name
- It blocks: Should + expected behavior

---

## Related Documents
| Document | Purpose |
|----------|---------|
| [tech_stack.md](./tech_stack.md) | Version locks |
| [prd.md](./prd.md) | Requirements |
