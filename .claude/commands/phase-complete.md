---
description: Phase completion protocol - run before committing
---

# /phase-complete

## 🚨 STOP - DO NOT COMMIT YET

**Pre-check:**
1. Ask user for `/context` result
2. Verify tests pass
3. Verify correct branch: `git branch --show-current`

**Required steps (ALL must complete):**

- [ ] Run tests → must pass
- [ ] Create completion doc: `docs/tasks/{component}_phase{N}_complete.md`
- [ ] Create handoff doc: `docs/tasks/{component}_phase{N+1}_handoff.md`
- [ ] Update `dev_context.md` (preserve Task Constants!)
- [ ] Archive old handoff to `docs/tasks/completed/`
- [ ] Git commit and push
- [ ] Provide new session prompt

**Final phase special handling:**
- No handoff needed
- Archive Task Constants to completion doc
- Remove Task Constants from dev_context.md

**Output:**
```
🎉 Phase {N} Complete!

✅ Created: completion doc
✅ Created: handoff doc  
✅ Updated: dev_context.md
✅ Committed: {branch}

⚠️ START PHASE {N+1} IN NEW CHAT
```

**Full protocol:** `.ai/workflows/phase-complete.md`
