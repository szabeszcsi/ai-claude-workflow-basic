---
description: Quick context health check and status report
---

# /check-status

**Step 1:** Ask user to run `/context` and share the result.

**Step 2:** Interpret the percentage:

| Usage | Status | Action |
|-------|--------|--------|
| < 60% | ✅ Healthy | Continue freely |
| 60-75% | ⚠️ Moderate | Plan wrap-up point |
| 75-85% | 🟠 High | Complete current item, save |
| > 85% | 🚨 Critical | Save NOW, new session |

**Step 3:** Self-check for degradation symptoms:
- Re-reading files already read?
- Asking answered questions?
- Confusion about current task?
- Making repeated mistakes?

**Step 4:** Generate status report:

```
📊 STATUS CHECK

👤 {Name} | 🌿 {branch}
📍 Context: {X}% - {status}

🎯 PRIMARY: {task} - {progress}
🔥 LINGERING: {count} items
📈 This session: {accomplishments}

💡 Recommendation: {action}
```

**Full protocol:** `.ai/workflows/check-status.md`
