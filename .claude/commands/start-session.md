---
description: Initialize a new chat session with proper context loading
---

# /start-session

**First: Be honest about my memory state.**

| If I... | Then I must... |
|---------|----------------|
| Have direct memory of this session | ✅ Continue |
| Started from a checkpoint/summary | 🚨 Tell you immediately, recommend fresh start |
| Am uncertain | Ask you to clarify |

**Then: Load context**

1. Read `dev_context.md`
2. Read `SOLUTION_ARCHITECTURE.md`
3. Check git: `git branch --show-current && git status --short`
4. Ask you to run `/context` for baseline

**Then: Present options**

Show what work is available based on context file:
- 🎯 PRIMARY task (current phase)
- 🔥 LINGERING items (bugs, ad-hoc)
- 🆕 NEW task (something else)

**Full protocol:** `.ai/workflows/start-session.md`
