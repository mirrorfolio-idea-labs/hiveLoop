# 🧠 HiveLoop Core Concepts

> Understanding the foundations of multi-agent AI orchestration

---

## The Problem: Context Rot

When AI assistants work on extended tasks, output quality degrades as the context window fills. We call this **context rot**.

### Symptoms of Context Rot

- Forgetting earlier instructions
- Contradicting previous decisions
- Introducing patterns inconsistent with established code
- "Hallucinating" non-existent files or functions
- Increasing error rate over time

### Why It Happens

```
Session Start: 0 tokens → HIGH QUALITY OUTPUT
     ↓
Mid Session: 50K tokens → QUALITY DEGRADATION BEGINS
     ↓
Late Session: 100K+ tokens → CONTEXT ROT ZONE
```

---

## The Solution: HiveLoop

HiveLoop prevents context rot through:

### 1. Fresh Sessions Per Agent

Each agent starts with **zero context**, eliminating accumulated noise.

### 2. Anchor Documents

Agents load **standardized project documents** to understand the codebase:

| Document | Purpose |
|----------|---------|
| PRD | What to build |
| Tech Stack | How to build it |
| Conventions | Patterns to follow |
| Implementation Plan | Task breakdown |
| Progress Tracker | Current state |

### 3. Parallel Execution

Multiple agents work **simultaneously** on independent tasks:

```
TIME →
────────────────────────────────────
Frontend │████████████████│ DONE
Backend  │████████████████████│ DONE
DevOps   │██████████│ DONE
────────────────────────────────────
         Parallel saves 60% time vs sequential
```

### 4. Orchestrated Aggregation

A lead **Orchestrator agent** coordinates:
- Task assignment
- Conflict detection
- Result merging
- Progress updates

---

## Token Budget Model

Each agent operates within a **token budget** to ensure quality:

| Agent Type | Budget | Warning | Reset |
|------------|--------|---------|-------|
| Orchestrator | 30,000 | 24,000 | 35,000 |
| Specialist | 40,000 | 32,000 | 50,000 |
| Verification | 20,000 | 16,000 | 25,000 |

When budget exceeds the warning zone:
1. Complete current task
2. Save state
3. End session
4. Start fresh next iteration

---

## Iteration Cycle

```
┌─────────────────────────────────────────┐
│         HIVELOOP ITERATION              │
└─────────────────────────────────────────┘
                    │
                    ▼
         1. ORCHESTRATOR ANALYZES
            • Load progress tracker
            • Identify ready tasks
            • Plan parallelization
                    │
                    ▼
         2. SPAWN SPECIALISTS
            • Each starts fresh
            • Loads anchor docs
            • Executes assigned tasks
                    │
                    ▼
         3. AGGREGATE RESULTS
            • Collect outputs
            • Detect conflicts
            • Merge changes
                    │
                    ▼
         4. UPDATE & REPEAT
            • Update progress tracker
            • Plan next iteration
            • End session
                    │
                    ▼
              [NEXT ITERATION]
```

---

## Key Metrics

| Metric | Calculation | Target |
|--------|-------------|--------|
| Completion Rate | completed / total | >90% |
| First-Try Success | no_retry / total | >70% |
| Context Rot Score | 100 - (violations × weight) | >90 |
| Parallel Efficiency | parallel / parallelizable | >80% |

---

## When to Use What

| Situation | Approach |
|-----------|----------|
| Quick fix (<15 min) | Single agent |
| One-domain task | Single specialist agent |
| Cross-domain work | HiveLoop 2-3 agents |
| Full feature | HiveLoop 3-5 agents |
| System redesign | HiveLoop + dedicated architect |

---

## Related Concepts

- **Ralph Loop** — Single-agent predecessor
- **Swarm Intelligence** — Inspiration for parallel coordination
- **Orchestrator-Worker** — Pattern from Anthropic research
