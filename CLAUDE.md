# CLAUDE.md - AI Assistant Instructions

> **Claude reads this file automatically.** Keep it lean. Details live in `.ai/` folder.

---

## 🚨 Rule #0: Checkpoint Integrity (HIGHEST PRIORITY)

**On FIRST interaction or any `/check-status`:**

| Situation | Action |
|-----------|--------|
| Direct memory of this session | ✅ Continue normally |
| Started from checkpoint/summary | 🚨 **DISCLOSE IMMEDIATELY** → Recommend fresh `/start-session` |
| Uncertain about state | 🔄 Ask user to run `/context`, then assess |

**NEVER pretend to have direct memory when you don't.**

---

## 📋 Session Start Protocol

**Every new chat MUST begin with:**
1. Read `dev_context.md` (current state)
2. Read `SOLUTION_ARCHITECTURE.md` (project structure)
3. Verify git branch: `git branch --show-current`
4. Ask user to run `/context` for baseline health check

**Workflow:** `/start-session` or see `.ai/workflows/start-session.md`

---

## 🔄 Context Monitoring

**Claude cannot directly check context usage.** When degradation suspected:

1. Ask user: "Please run `/context` and share the result"
2. Interpret: `<60%` good | `60-75%` moderate | `75-85%` high | `>85%` critical
3. Act accordingly (wrap up, save progress, recommend new session)

**Self-monitor for symptoms:**
- Re-reading files already read this session
- Asking questions already answered
- Confusion about current task or branch
- User says "you seem confused"

---

## 📁 Key Files

| File | Purpose |
|------|---------|
| `SOLUTION_ARCHITECTURE.md` | Project structure (generate with `/generate-architecture`) |
| `dev_context.md` | Session state, current task, lingering items |
| `.ai/WORKFLOW_QUICKREF.md` | Command quick reference |
| `.ai/standards/{language}.md` | Coding standards (load per language) |

---

## 🛠️ Workflows (via slash commands)

| Command | When to Use |
|---------|-------------|
| `/start-session` | Every new chat session |
| `/check-status` | Verify context health |
| `/phase-complete` | Before committing completed phase |
| `/update-context` | Save mid-session progress |
| `/abort` | Emergency recovery |
| `/generate-architecture` | Create/update SOLUTION_ARCHITECTURE.md |

Full protocols: `.ai/workflows/`

---

## 📝 Coding Standards

Load the relevant standard when writing code:
- `.ai/standards/_common.md` - Universal principles
- `.ai/standards/python.md` - Python
- `.ai/standards/sql.md` - SQL Server / T-SQL  
- `.ai/standards/dax.md` - DAX / Power BI
- `.ai/standards/javascript.md` - JavaScript/TypeScript

---

## 🚨 Hard Rules

1. **Tests pass → Phase complete** - Run `/phase-complete` before committing
2. **Context degradation** - If symptoms detected, recommend `/check-status`
3. **File placement** - Follow `SOLUTION_ARCHITECTURE.md`, never dump in root
4. **No code in chat** - Create files, show only <10 line snippets
5. **Plan before coding** - Brief steps, confirm with user

---

## 📚 Additional Resources

| Need | Location |
|------|----------|
| Quick reference | `.ai/WORKFLOW_QUICKREF.md` |
| Full workflow docs | `.ai/workflows/` |
| Templates | `.ai/templates/` |
| Task generation guide | `.ai/guides/TASK_FILE_GENERATION_GUIDE.md` |

---

*For system overview, see `.ai/README.md`*
