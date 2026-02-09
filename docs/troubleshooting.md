# 🔧 Troubleshooting HiveLoop

> Solutions to common issues

---

## Agent Issues

### Agent forgets earlier context

**Symptom**: Agent doesn't remember instructions from anchor documents.

**Cause**: Context window overflow or session not fresh.

**Solution**:
1. End current session completely
2. Start brand new session
3. Load anchor documents first
4. Verify documents loaded before tasking

---

### Agent produces inconsistent code

**Symptom**: Code style varies between iterations.

**Cause**: Conventions not loaded or context rot.

**Solution**:
1. Always load `conventions.md` first
2. Check token usage isn't near limit
3. Add specific constraints to agent prompt
4. Consider adding examples to conventions

---

### Agent ignores constraints

**Symptom**: Agent violates rules from conventions.

**Cause**: Constraints not prominent or conflicting.

**Solution**:
1. Move constraints to agent prompt header
2. Use ⚠️ ALWAYS / ⚠️ NEVER format
3. Add verification step to check constraints
4. Include negative examples

---

## Coordination Issues

### Conflicting changes from parallel agents

**Symptom**: Two agents modified same file differently.

**Cause**: Task assignment overlap.

**Solution**:
1. Assign file ownership to single agent
2. Use integration agent for shared files
3. Apply conflict resolution protocol
4. Review task dependencies

---

### Handoff failures

**Symptom**: Dependent agent doesn't have what it needs.

**Cause**: Incomplete handoff or missing contract.

**Solution**:
1. Use handoff template from coordination.md
2. Include verification step in handoff
3. Confirm completion before spawning dependent
4. Document API contracts explicitly

---

### Progress tracker out of sync

**Symptom**: Tracker doesn't reflect actual state.

**Cause**: Failed update or concurrent modifications.

**Solution**:
1. Only orchestrator updates tracker
2. Verify state before each iteration
3. Cross-reference with actual files
4. Reset tracker from codebase if needed

---

## Performance Issues

### Slow iteration progress

**Symptom**: Few tasks completed per iteration.

**Cause**: Tasks too large or poor parallelization.

**Solution**:
1. Break tasks into smaller units
2. Review dependency graph for bottlenecks
3. Increase parallel agents if tasks allow
4. Reduce token budget overhead

---

### High token usage

**Symptom**: Agents hitting budget limits quickly.

**Cause**: Too much context or verbose prompts.

**Solution**:
1. Trim anchor documents to essentials
2. Load only relevant sections
3. Use summary references, not full content
4. Split complex tasks across iterations

---

### Low completion rate

**Symptom**: <80% of assigned tasks complete.

**Cause**: Blockers, complexity, or mis-assignment.

**Solution**:
1. Review blocked tasks for patterns
2. Re-estimate task complexity
3. Match tasks to agent expertise
4. Add missing dependencies to plan

---

## Quality Issues

### Context rot detected

**Symptom**: Score dropping across iterations.

**Cause**: Pattern drift, accumulated errors.

**Solution**:
1. Force fresh session immediately
2. Reload all anchor documents
3. Run verification on recent work
4. Consider full context reset

---

### Regressions appearing

**Symptom**: Previously working features break.

**Cause**: Incomplete context or conflicting changes.

**Solution**:
1. Add regression to verification checklist
2. Document critical behaviors
3. Run verification after each iteration
4. Consider dedicated verification agent

---

## Getting Help

If issues persist:

1. Check [GitHub Issues](https://github.com/yourorg/hiveloop/issues)
2. Review recent changes in anchor documents
3. Try minimal reproduction
4. Open new issue with details

---

## Related Documents

| Document | Purpose |
|----------|---------|
| [concepts.md](./concepts.md) | Core concepts |
| [getting-started.md](./getting-started.md) | Setup guide |
| [../core/evaluation.md](../core/evaluation.md) | Metrics |
