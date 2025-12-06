---
description: Save progress mid-session without completing phase
---

# /update-context

**Use when:** Made progress but not done, session ending, want checkpoint

**Don't use when:** Phase complete → use `/phase-complete`

**Steps:**

1. **Identify work type:**
   - [P] Primary phase task
   - [L] Lingering task
   - [N] New issue discovered

2. **Gather summary:**
   - What was accomplished?
   - Current status?
   - Immediate next step?

3. **Check for new Task Constants:**
   - Did we create test scripts, signatures, or config that must be preserved?
   - If yes → add to Task Constants section

4. **Update dev_context.md:**
   - Update Primary Task progress
   - Add/update Lingering items
   - Keep Task Constants section current

5. **Create session doc if significant:**
   - Location: `docs/working/{task}_{date}.md`

6. **Check file size:**
   - < 1.5 KB: OK
   - 1.5-2 KB: Consider archiving
   - > 2 KB: Archive NOW

**Output:**
```
✅ CONTEXT SAVED

Updated: dev_context.md
Status: {status}
Size: {X} KB

Next session prompt:
---
I'm {Name}. Continue {task}.
Read dev_context.md for state.
Branch: {branch}
---
```

**Full protocol:** `.ai/workflows/update-context.md`
