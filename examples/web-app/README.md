# Web App Example

> HiveLoop configuration for a typical web application

---

## Project Structure

```
my-web-app/
├── .hiveloop/
│   ├── prd.md
│   ├── tech_stack.md
│   ├── conventions.md
│   ├── implementation_plan.md
│   └── progress_tracker.md
├── frontend/
│   └── src/
├── backend/
│   └── src/
└── shared/
    └── types/
```

---

## Tech Stack Example

```markdown
## Frontend
- React 18.2
- TypeScript 5.0
- Vite 5.0
- TailwindCSS 3.4

## Backend
- Node.js 20.x
- Express 4.18
- PostgreSQL 15
- Prisma 5.0

## Shared
- Zod (validation)
- TypeScript types
```

---

## Agent Assignment

| Domain | Agent | Tasks |
|--------|-------|-------|
| UI Components | Frontend | TASK-01 to TASK-08 |
| API Endpoints | Backend | TASK-09 to TASK-15 |
| Database | Backend | TASK-16 to TASK-18 |
| Auth | Frontend + Backend | TASK-19 to TASK-22 |
| Integration | Integration | TASK-23 to TASK-25 |

---

## Parallel Execution Plan

```
Phase 1: Foundation
┌─────────────────┐     ┌─────────────────┐
│ Frontend Setup  │     │ Backend Setup   │
│ TASK-01, 02     │     │ TASK-09, 10     │
└─────────────────┘     └─────────────────┘

Phase 2: Core Features  
┌─────────────────┐     ┌─────────────────┐
│ UI Components   │     │ API Endpoints   │
│ TASK-03 to 06   │     │ TASK-11 to 14   │
└─────────────────┘     └─────────────────┘

Phase 3: Integration
┌─────────────────────────────────────────┐
│ Connect Frontend ↔ Backend              │
│ TASK-23 to 25                           │
└─────────────────────────────────────────┘
```

---

## Sample Iteration

```markdown
## Iteration 2 - Web App

### Orchestrator
Analyzed: Phase 1 complete
Ready: TASK-03, 04, 05, 11, 12

### Spawned
| Agent | Tasks | Parallel |
|-------|-------|----------|
| Frontend | 03, 04, 05 | ✅ |
| Backend | 11, 12 | ✅ |

### Results
- Completed: 5/5
- Blocked: 0
- Patterns: 2 new

### Next
- Ready: TASK-06, 07, 13, 14
- Focus: Continue parallel
```

---

## Key Patterns

### API Pattern
```typescript
// Backend endpoint
app.get('/api/users/:id', async (req, res) => {
  const user = await userRepository.findById(req.params.id);
  return res.json(user);
});

// Frontend consumption
const { data } = await api.get<User>(`/users/${id}`);
```

### State Pattern
```typescript
// Zustand store
const useUserStore = create<UserState>((set) => ({
  user: null,
  setUser: (user) => set({ user }),
}));
```

---

## Verification Checklist

- [ ] Frontend builds without errors
- [ ] Backend starts and connects to DB
- [ ] API endpoints return expected data
- [ ] UI renders and navigates correctly
- [ ] Auth flow works end-to-end
