# 🔗 HiveLoop Coordination Protocol

> Inter-agent communication patterns

---

## Communication Patterns

### Pattern 1: Task Handoff

When one agent completes work that another depends on:

```markdown
## HANDOFF: [Source Agent] → [Target Agent]

**Completed Task**: [Task ID]

**Deliverables**:
- [File/endpoint/component created]
- [Location]

**Contract**:
[Interface/API specification]

**Ready For**: [Dependent Task ID]

**Verification**: [How to confirm it works]
```

---

### Pattern 2: Conflict Escalation

When agents attempt to modify the same resource:

```markdown
## CONFLICT DETECTED

**Agents**: [Agent A] + [Agent B]

**Resource**: [File/component path]

**Agent A's Change**:
[Description or code]

**Agent B's Change**:
[Description or code]

**Resolution Protocol**:
1. HALT both agents
2. Orchestrator reviews
3. Merge if compatible
4. Choose one if not
5. Resume execution

**Decision**: [Which version and why]
```

---

### Pattern 3: Shared State Update

Progress tracker updates:

```markdown
## PROGRESS UPDATE PROTOCOL

**Rule**: Only Orchestrator writes to progress_tracker.md

**Agent Reporting Format**:
agent: [type]
iteration: [N]
tasks:
  - id: [TASK-01]
    status: COMPLETE
    files: [list]
    patterns: [list]
    blockers: []
  - id: [TASK-02]
    status: BLOCKED
    blocker: [reason]
    retry_strategy: [approach]

**Orchestrator merges, resolves conflicts, updates tracker**
```

---

## Synchronization Points

### Sync 1: Phase Boundaries

```
PHASE N COMPLETE
     │
     ▼
┌─────────────────────────────────────────┐
│           SYNC CHECKPOINT               │
│                                         │
│ 1. All agents report final status       │
│ 2. Orchestrator aggregates              │
│ 3. Progress tracker updated             │
│ 4. Patterns consolidated                │
│ 5. Next phase assigned                  │
└─────────────────────────────────────────┘
     │
     ▼
PHASE N+1 BEGINS
```

### Sync 2: Cross-Stack Integration

```markdown
## INTEGRATION SYNC - [Feature]

**Requires Both**:
- Frontend: [Task ID] ✅
- Backend: [Task ID] ✅

**Sync Protocol**:
1. Both agents confirm completion
2. Orchestrator spawns Integration Agent
3. Integration Agent connects components
4. Verification Agent validates E2E
5. All mark complete after E2E passes
```

### Sync 3: Pattern Discovery

```markdown
## PATTERN SYNC

**Discovery**: [Agent type] found reusable pattern

**Pattern**:
[Code or description]

**Validation Steps**:
1. Agent documents in output
2. Orchestrator collects at iteration end
3. Verification Agent validates
4. If valid → Add to conventions.md
5. All agents receive update
```

---

## Handoff Templates

### Frontend → Backend

```markdown
## HANDOFF: Frontend → Backend

**Frontend Needs**: [API endpoint]

**Data Requirements**:
| Field | Type | Notes |
|-------|------|-------|
| [field] | [type] | [notes] |

**Expected Response**:
[Shape/interface]

**Priority**: [HIGH/MEDIUM/LOW]
```

### Backend → Frontend

```markdown
## HANDOFF: Backend → Frontend

**Endpoint Ready**: [METHOD /path]

**Contract**:
// Request
{ ... }

// Response  
{ ... }

**Test Command**:
curl -X [METHOD] [URL]

**Frontend Can Now**: [Task IDs unblocked]
```

---

## Conflict Resolution

### Priority Order

1. **Security** — Never compromise
2. **Architecture patterns** — Maintain consistency
3. **Conventions** — Follow established rules
4. **Implementation details** — Prefer completeness

### Resolution Process

1. Identify conflicting changes
2. Check if changes can merge (different sections)
3. If not, apply priority order
4. Document decision
5. Notify affected agents

---

## Related Documents

| Document | Purpose |
|----------|---------|
| [orchestrator.md](./orchestrator.md) | Orchestration |
| [agent-prompts.md](./agent-prompts.md) | Templates |
| [workflow.md](./workflow.md) | Execution flow |
