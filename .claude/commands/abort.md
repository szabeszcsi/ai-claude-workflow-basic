---
description: Emergency recovery when things go wrong
---

# /abort

## 🚨 STOP IMMEDIATELY

Do not make any more changes.

**When to use:**
- 🔥 Broke something, can't fix
- 🔥 Tests failing after multiple attempts
- 🔥 Wrong branch/files modified
- 🔥 Context severely degraded

**Step 1: Assess damage**
```bash
git status
git diff --stat
```

Ask: What went wrong? How far back to go?

**Step 2: Choose recovery**

| Option | Command | Warning |
|--------|---------|---------|
| Discard all | `git checkout -- . && git clean -fd` | ⚠️ Destroys uncommitted |
| Stash | `git stash push -m "Recovery"` | Saves for later |
| Reset to commit | `git reset --hard HEAD` | ⚠️ Destroys since commit |
| Selective | `git checkout HEAD -- {file}` | Single file |

**Step 3: Verify**
```bash
git status
pytest tests/ -v --tb=short
```

**Step 4: Document (optional)**
Create `docs/working/incident_{date}.md`

**Step 5: Report**
```
🔄 ABORT COMPLETE

Recovery: {action taken}
Status: {clean/needs work}

Recommendation: Fresh chat with /start-session
```

**Full protocol:** `.ai/workflows/abort.md`
