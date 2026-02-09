# 🤖 HiveLoop Agent Types

> Specialist agents for different domains of software development

---

## Overview

HiveLoop uses **specialist agents**, each optimized for a specific domain. This allows for deeper expertise and better parallelization.

---

## Core Agent Types

### 🎯 Orchestrator Agent

**Role**: Coordinates all other agents

**Responsibilities**:
- Analyze project state
- Decompose tasks
- Assign work to specialists
- Aggregate results
- Update progress tracker

**When to use**: Always — every HiveLoop iteration needs an orchestrator

**Token Budget**: 30,000

---

### 📱 Frontend Agent

**Role**: Client-side user interface development

**Specializations**:
- React / Vue / Angular
- React Native / Flutter
- HTML/CSS/JavaScript
- Accessibility

**Typical Tasks**:
- Build UI components
- Implement screens/pages
- Handle client-side state
- Style and animations

**Token Budget**: 40,000

---

### 🖥️ Backend Agent

**Role**: Server-side logic and data management

**Specializations**:
- Node.js / Python / Go / Java
- REST / GraphQL APIs
- Database design
- Business logic

**Typical Tasks**:
- Create API endpoints
- Implement data models
- Write business logic
- Database migrations

**Token Budget**: 40,000

---

### ☁️ DevOps Agent

**Role**: Infrastructure and deployment

**Specializations**:
- Docker / Kubernetes
- CI/CD pipelines
- Cloud platforms (AWS/GCP/Azure)
- Monitoring

**Typical Tasks**:
- Set up infrastructure
- Configure CI/CD
- Write Dockerfiles
- Deployment automation

**Token Budget**: 30,000

---

### ✅ Verification Agent

**Role**: Testing and quality assurance

**Specializations**:
- Unit testing
- Integration testing
- E2E testing
- Code review

**Typical Tasks**:
- Write tests
- Validate implementations
- Check conventions
- Detect regressions

**Token Budget**: 20,000

---

### 🔗 Integration Agent

**Role**: Cross-stack coordination

**Specializations**:
- API contracts
- Type synchronization
- Data flow
- Error handling

**Typical Tasks**:
- Connect frontend to backend
- Ensure type consistency
- Implement loading/error states
- E2E flow validation

**Token Budget**: 35,000

---

### 📝 Documentation Agent

**Role**: Technical writing and documentation

**Specializations**:
- API docs
- README files
- Architecture docs
- User guides

**Typical Tasks**:
- Write documentation
- Generate API references
- Create diagrams
- Update changelogs

**Token Budget**: 25,000

---

## Custom Agents

Create your own specialist agents for domain-specific needs:

### Template

```markdown
# [DOMAIN] AGENT

## Identity
You are a [domain] specialist responsible for [responsibilities].

## Tech Stack
- [Technology 1]
- [Technology 2]

## Required Context
Load before any task:
1. conventions.md
2. tech_stack.md
3. [domain-specific docs]

## Constraints
⚠️ ALWAYS:
- [Rule 1]
- [Rule 2]

⚠️ NEVER:
- [Anti-pattern 1]
- [Anti-pattern 2]

## Output Format
[Define expected output structure]
```

---

## Agent Selection Matrix

| Task Type | Primary Agent | Support Agent |
|-----------|---------------|---------------|
| UI component | Frontend | — |
| API endpoint | Backend | — |
| Full feature | Frontend + Backend | Integration |
| Database change | Backend | — |
| Deployment | DevOps | — |
| Bug fix | Domain-specific | Verification |
| Refactor | Domain-specific | Verification |

---

## Agent Scaling

| Project Size | Recommended Agents |
|--------------|-------------------|
| Solo/small | 1-2 specialists |
| Medium | 2-3 specialists |
| Large | 3-4 specialists |
| Enterprise | 4-5 specialists |

---

## Related

- [Orchestrator Configuration](../core/orchestrator.md)
- [Agent Prompts](../core/agent-prompts.md)
- [Coordination Protocol](../core/coordination.md)
