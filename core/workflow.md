# 🔄 HiveLoop Workflow

> Step-by-step execution protocol

---

## Execution Overview

```
┌─────────────────────────────────────────────────────────────┐
│                   HIVELOOP ITERATION                        │
└─────────────────────────────────────────────────────────────┘
                            │
    ┌───────────────────────┼───────────────────────┐
    ▼                       ▼                       ▼
STEP 1                  STEP 2                  STEP 3
Orchestrator           Parallel                Aggregate
Analyzes               Execution              & Verify
    │                       │                       │
    └───────────────────────┴───────────────────────┘
                            │
                            ▼
                    STEP 4: Update
                    Progress Tracker
                            │
                            ▼
                    STEP 5: Plan
                    Next Iteration
                            │
                            ▼
                    [REPEAT or DONE]
```

---

## Step 1: Orchestrator Initialization

**Duration**: 2-3 minutes

```markdown
## ORCHESTRATOR SESSION START

### 1.1 Load Anchor Documents
1. progress_tracker.md → Current state
2. implementation_plan.md → Task definitions
3. conventions.md → Constraints

### 1.2 Analyze State
- Tasks completed: [ ]/[TOTAL]
- Tasks unblocked: [list]
- Parallelizable: [count]
- Blockers: [list]

### 1.3 Plan Iteration
| Agent | Tasks | Dependencies |
|-------|-------|--------------|
| [Type] | [IDs] | ✅/❌ |

### 1.4 Prepare Prompts
Generate task delegation for each agent.
```

---

## Step 2: Parallel Agent Execution

**Duration**: 10-20 minutes per agent

```
┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐
│ AGENT 1         │  │ AGENT 2         │  │ AGENT 3         │
│                 │  │                 │  │                 │
│ Fresh Context   │  │ Fresh Context   │  │ Fresh Context   │
│ Load anchors    │  │ Load anchors    │  │ Load anchors    │
│ Execute tasks   │  │ Execute tasks   │  │ Execute tasks   │
│ Report results  │  │ Report results  │  │ Report results  │
└─────────────────┘  └─────────────────┘  └─────────────────┘
         │                    │                    │
         └────────────────────┴────────────────────┘
                              │
                              ▼
                    ORCHESTRATOR COLLECTS
```

### Agent Execution Flow
1. Start fresh session (0 tokens)
2. Load anchor documents
3. Read task delegation
4. Execute assigned tasks
5. Generate output
6. Document patterns
7. Report blockers
8. Return results

### Token Budget
| Agent | Budget | Warning | Reset |
|-------|--------|---------|-------|
| Orchestrator | 30K | 24K | 35K |
| Specialist | 40K | 32K | 50K |
| Verification | 20K | 16K | 25K |

---

## Step 3: Result Aggregation

**Duration**: 5-10 minutes

### 3.1 Collect Outputs
```yaml
agent_1_output:
  completed: [TASK-01, TASK-02]
  files: [list]
  patterns: [list]
  blockers: []

agent_2_output:
  completed: [TASK-03]
  files: [list]
  patterns: [list]
  blockers: [reason]
```

### 3.2 Detect Conflicts
Check for:
- Same file modified
- Contradicting patterns
- API changes

### 3.3 Merge Results
- Combine file lists
- Merge patterns
- Aggregate blockers
- Resolve conflicts if any

---

## Step 4: Verification & Update

**Duration**: 5-10 minutes

### 4.1 Verification Checklist
For each task:
- [ ] Success criteria met
- [ ] Conventions followed
- [ ] No violations
- [ ] No regressions

### 4.2 Update Progress Tracker
```markdown
### Iteration [N] - [Date]

**Completed**: [Task IDs]
**Blocked**: [Task IDs + reasons]
**Patterns Added**: [List]

**Metrics**:
| Agent | Tasks | Success |
|-------|-------|---------|
| ... | ... | ... |
```

---

## Step 5: Plan Next Iteration

**Duration**: 2-3 minutes

### 5.1 Identify Ready Tasks
What's unblocked after this iteration?

### 5.2 Handle Blockers
- Has retry strategy → Schedule retry
- Needs input → Flag for user
- Needs redesign → Update plan

### 5.3 Optimize Assignments
- Reassign based on performance
- Split complex tasks
- Combine trivial ones

### 5.4 End Session
- Save to progress_tracker.md
- Clear context
- Ready for next iteration

---

## Iteration Example

```markdown
## Iteration 3 Log

### Step 1: Analysis
- Completed: 8/25 (32%)
- Ready: TASK-09, TASK-10, TASK-11
- Parallel: 2 Frontend + 1 Backend

### Step 2: Execution
| Agent | Tasks | Duration | 
|-------|-------|----------|
| Frontend | TASK-09, 10 | 15 min |
| Backend | TASK-11 | 12 min |

### Step 3: Aggregation
- Files created: 5
- Conflicts: 0
- Patterns: 1 new

### Step 4: Verification
- All 3 tasks ✅
- Conventions: PASS

### Step 5: Planning
- Now ready: TASK-12, 13
- Next focus: Continue parallel
- Est. completion: 5 more iterations

**Health**: ✅ GOOD
```

---

## Failure Recovery

### Agent Failure
1. Other agents continue
2. Failed task → BLOCKED
3. Capture partial work
4. Retry next iteration

### Orchestrator Failure
1. Progress tracker = source of truth
2. Next session reads tracker
3. Resumes from known state

---

## Related Documents

| Document | Purpose |
|----------|---------|
| [orchestrator.md](./orchestrator.md) | Config |
| [coordination.md](./coordination.md) | Handoffs |
| [evaluation.md](./evaluation.md) | Metrics |
