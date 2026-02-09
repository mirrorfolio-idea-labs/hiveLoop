# 🚀 Getting Started with HiveLoop

> Set up HiveLoop for your project in 10 minutes

---

## Prerequisites

- An AI assistant that supports multi-turn conversations (Claude, GPT-4, etc.)
- A software project with defined requirements
- Basic understanding of your project structure

---

## Step 1: Install HiveLoop

### Option A: Clone the repository

```bash
git clone https://github.com/yourorg/hiveloop.git
```

### Option B: Download ZIP

Download from [Releases](https://github.com/yourorg/hiveloop/releases)

---

## Step 2: Set Up Your Project

Create a `.hiveloop/` directory in your project root:

```bash
mkdir .hiveloop
cp -r hiveloop/templates/* .hiveloop/
```

Your project should now look like:

```
your-project/
├── .hiveloop/
│   ├── prd.md
│   ├── tech_stack.md
│   ├── conventions.md
│   ├── implementation_plan.md
│   └── progress_tracker.md
├── src/
└── ...
```

---

## Step 3: Customize Anchor Documents

### 3.1 Edit `prd.md`

Define your product requirements:

```markdown
# Product Requirements Document

## Vision
[What are you building?]

## Features
- [ ] Feature 1
- [ ] Feature 2

## Out of Scope
- [What you're NOT building]
```

### 3.2 Edit `tech_stack.md`

Lock your technology versions:

```markdown
# Tech Stack

## Frontend
- React 18.2.0
- TypeScript 5.0

## Backend
- Node.js 20.x
- PostgreSQL 15
```

### 3.3 Edit `conventions.md`

Define your coding standards:

```markdown
# Conventions

## Naming
- Files: kebab-case
- Functions: camelCase
- Components: PascalCase

## Anti-Patterns
- NO any types
- NO hardcoded secrets
```

### 3.4 Edit `implementation_plan.md`

Break down tasks:

```markdown
# Implementation Plan

## Phase 1: Foundation
- [ ] TASK-01: Initialize project
- [ ] TASK-02: Set up database

## Phase 2: Core Features
- [ ] TASK-03: User authentication
- [ ] TASK-04: Dashboard UI
```

---

## Step 4: Initialize Progress Tracker

Create your starting state:

```markdown
# Progress Tracker

## Current Status
- Total Tasks: 20
- Completed: 0
- In Progress: 0
- Blocked: 0

## Next Up
- TASK-01: Initialize project
```

---

## Step 5: Run Your First Iteration

### Start a new AI session and provide this prompt:

```markdown
# HIVELOOP ORCHESTRATOR SESSION

## Load Anchor Documents
1. Read: .hiveloop/progress_tracker.md
2. Read: .hiveloop/implementation_plan.md
3. Read: .hiveloop/conventions.md
4. Read: .hiveloop/tech_stack.md

## Your Task
Analyze the current state and identify:
1. What tasks are ready to execute?
2. Which can run in parallel?
3. What agent types are needed?

Then execute the first ready task.
```

---

## Step 6: Iterate

After each session:

1. **Update progress tracker** with completed tasks
2. **Document patterns** discovered
3. **Start fresh session** for next iteration
4. **Repeat** until project complete

---

## Example: Web App Setup

```markdown
# HIVELOOP SESSION - Iteration 1

## Orchestrator Analysis
- Ready: TASK-01 (init), TASK-02 (db setup)
- Parallel: Yes, 2 tasks are independent
- Agents: 1 DevOps, 1 Backend

## Execution Plan
| Agent | Task | Est. Time |
|-------|------|-----------|
| DevOps | TASK-01 | 15 min |
| Backend | TASK-02 | 20 min |

## Executing...
```

---

## Next Steps

- Read [Core Concepts](./concepts.md) for deeper understanding
- Explore [Agent Types](./agent-types.md) for specialization
- Check [Examples](../examples/) for project-specific setups

---

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Agent forgets context | Start completely fresh session |
| Conflicting outputs | Use coordination protocol |
| Slow progress | Break tasks into smaller units |

See [Troubleshooting Guide](./troubleshooting.md) for more.
