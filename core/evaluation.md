# 📊 HiveLoop Evaluation

> Metrics and evaluation framework

---

## Key Metrics

### Per-Agent Metrics

| Metric | Calculation | Target |
|--------|-------------|--------|
| Task Completion | completed / assigned | >90% |
| First-Try Success | no_retry / total | >70% |
| Token Efficiency | tokens / task_count | <30,000 |
| Context Rot Score | 100 - (violations × 5) | >90 |
| Pattern Adherence | matched / total | >95% |

### Coordination Metrics

| Metric | Calculation | Target |
|--------|-------------|--------|
| Parallel Efficiency | parallel / parallelizable | >80% |
| Conflict Rate | conflicts / handoffs | <5% |
| Handoff Latency | avg time between handoffs | <5 min |

---

## Agent Scorecards

### Frontend Agent

```yaml
evaluation:
  functional:
    - Renders without errors
    - Navigation works
    - State updates correctly
    - Matches specifications
    
  quality:
    - Follows naming conventions
    - Uses specified patterns
    - No deprecated APIs
    - Proper error handling
    
  score:
    5: All criteria met
    4: Minor issues, functional
    3: Some issues, mostly works
    2: Multiple violations
    1: Critical failures
```

### Backend Agent

```yaml
evaluation:
  functional:
    - Endpoints respond correctly
    - Database operations work
    - Errors return proper status
    
  quality:
    - Repository pattern followed
    - Input validation present
    - Secrets in env vars
    
  security:
    - Passwords hashed
    - Auth implemented
    - No data leaks
    
  score:
    5: All criteria met, secure
    4: Minor issues, functional
    3: Some violations, works
    2: Security concerns
    1: Critical security issues
```

### Verification Agent

```yaml
evaluation:
  coverage:
    - All tasks verified
    - Integration checked
    - Security validated
    
  accuracy:
    - Correct issue detection
    - No false positives
    - No missed violations
    
  score:
    5: Comprehensive, accurate
    4: Good coverage
    3: Adequate
    2: Incomplete
    1: Unreliable
```

---

## Iteration Health

### Health Indicators

| Status | Meaning |
|--------|---------|
| ✅ EXCELLENT | >90% completion, <5% conflicts |
| ✅ GOOD | >80% completion, <10% conflicts |
| ⚠️ FAIR | >60% completion, <20% conflicts |
| ❌ POOR | <60% completion OR >20% conflicts |

### Calculation

```python
def iteration_health(metrics):
    completion = metrics.completed / metrics.total
    conflict_rate = metrics.conflicts / metrics.handoffs
    
    if completion > 0.9 and conflict_rate < 0.05:
        return "EXCELLENT"
    elif completion > 0.8 and conflict_rate < 0.1:
        return "GOOD"
    elif completion > 0.6 and conflict_rate < 0.2:
        return "FAIR"
    else:
        return "POOR"
```

---

## Context Rot Score

Measures quality preservation across iterations.

### Calculation

```
Context Rot Score = 100 - (violations × weight)

Violations:
- Pattern drift: 5 points each
- Constraint violation: 10 points each
- Regression: 15 points each
```

### Thresholds

| Score | Status | Action |
|-------|--------|--------|
| 90-100 | Healthy | Continue |
| 80-89 | Warning | Review patterns |
| 70-79 | Degraded | Reload anchors |
| <70 | Critical | Full reset |

---

## Iteration Report Template

```markdown
## Iteration Report - #[N]

### Summary
| Metric | Value | Target | Status |
|--------|-------|--------|--------|
| Completion | X/Y | >90% | ✅/❌ |
| First-Try | X% | >70% | ✅/❌ |
| Rot Score | XX | >90 | ✅/❌ |

### Per-Agent
| Agent | Tasks | Success | Score |
|-------|-------|---------|-------|
| [Type] | X | X% | X/5 |

### Issues
- [Issue 1]
- [Issue 2]

### Patterns Discovered
- [Pattern 1]

### Next Iteration
- [Priority 1]
- [Priority 2]

### Health: [STATUS]
```

---

## LLM-as-Judge Evaluation

For complex quality assessment, use another LLM to evaluate:

```markdown
## Evaluation Prompt

Evaluate this code against the project conventions.

**Task**: [Description]
**Expected**: [Criteria]

**Code**:
[Agent output]

**Rate**:
1. Functional correctness (0-1)
2. Pattern adherence (0-1)
3. Code quality (0-1)
4. Constraint compliance (0-1)

**Verdict**: PASS / FAIL
```

---

## Related Documents

| Document | Purpose |
|----------|---------|
| [workflow.md](./workflow.md) | Execution |
| [orchestrator.md](./orchestrator.md) | Coordination |
| [../docs/concepts.md](../docs/concepts.md) | Core concepts |
