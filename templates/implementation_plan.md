# Implementation Plan

> Break down your project into atomic tasks

---

## Overview

| Phase | Tasks | Status |
|-------|-------|--------|
| Phase 1: [Name] | X | ⬜ |
| Phase 2: [Name] | X | ⬜ |
| Phase 3: [Name] | X | ⬜ |
| **Total** | **X** | **0% complete** |

---

## Phase 1: [Foundation / Setup]

### TASK-01: [Task Title]
- **Description**: [What to build/do]
- **Agent**: [Frontend/Backend/DevOps]
- **Dependencies**: None
- **Files**:
  - `path/to/file1`
  - `path/to/file2`
- **Verification**:
  - [ ] [Check 1]
  - [ ] [Check 2]

### TASK-02: [Task Title]
- **Description**: [What to build/do]
- **Agent**: [Frontend/Backend/DevOps]
- **Dependencies**: TASK-01
- **Files**:
  - `path/to/file`
- **Verification**:
  - [ ] [Check]

---

## Phase 2: [Core Features]

### TASK-03: [Task Title]
- **Description**: [What to build/do]
- **Agent**: [Type]
- **Dependencies**: Phase 1
- **Files**:
  - `path/to/file`
- **Verification**:
  - [ ] [Check]

### TASK-04: [Task Title]
- **Description**: [What to build/do]
- **Agent**: [Type]
- **Dependencies**: TASK-03
- **Files**:
  - `path/to/file`
- **Verification**:
  - [ ] [Check]

---

## Phase 3: [Integration / Polish]

### TASK-05: [Task Title]
- **Description**: [What to build/do]
- **Agent**: Integration
- **Dependencies**: Phase 2
- **Files**:
  - `path/to/file`
- **Verification**:
  - [ ] [Check]

---

## Dependency Graph

```
TASK-01 ─────────┬───────────► TASK-03 ────► TASK-05
                 │
TASK-02 ─────────┘             TASK-04 ────►
```

---

## Parallel Opportunities

| Parallel Group | Tasks | Agents Needed |
|----------------|-------|---------------|
| Group 1 | TASK-01, TASK-02 | Frontend, Backend |
| Group 2 | TASK-03, TASK-04 | Frontend, Backend |

---

## Task Template

Use this to add new tasks:

```markdown
### TASK-XX: [Title]
- **Description**: [What to build/do]
- **Agent**: [Frontend/Backend/DevOps/Integration/Verification]
- **Dependencies**: [Task IDs or "None"]
- **Files**:
  - `path/to/file`
- **Verification**:
  - [ ] [Success criterion]
```

---

## Related Documents
| Document | Purpose |
|----------|---------|
| [progress_tracker.md](./progress_tracker.md) | Track status |
| [prd.md](./prd.md) | Requirements |
