# AI Workflow System

**Version:** 2.2  
**Purpose:** Portable AI-assisted development workflow for Claude Code

---

## 📦 What's In This Folder

```
.ai/
├── README.md                 ← You are here
├── WORKFLOW_QUICKREF.md      ← Quick reference card
├── NEW_PROJECT_CHECKLIST.md  ← Setup checklist for new projects
│
├── workflows/                ← Full workflow protocols
│   ├── start-session.md
│   ├── check-status.md
│   ├── phase-complete.md
│   ├── update-context.md
│   ├── abort.md
│   └── generate-architecture.md
│
├── standards/                ← Language-specific coding standards
│   ├── _common.md            ← Universal principles
│   ├── python.md
│   ├── sql.md
│   ├── dax.md
│   └── javascript.md
│
├── templates/                ← Document templates
│   ├── DEV_CONTEXT_TEMPLATE.md
│   ├── SOLUTION_ARCHITECTURE_TEMPLATE.md
│   ├── TASK_FILE_TEMPLATE.md
│   ├── HANDOFF_TEMPLATE.md
│   └── COMPLETION_TEMPLATE.md
│
└── guides/
    └── TASK_FILE_GENERATION_GUIDE.md
```

---

## 🎯 Core Concepts

### Rule #0: Checkpoint Integrity
AI must be honest about what it remembers. If it started from a summary/checkpoint rather than direct memory, it must disclose this immediately.

### Context Monitoring
Claude cannot directly check its context usage. The user runs `/context` command and shares the percentage. Thresholds:
- `<60%` - Healthy, continue freely
- `60-75%` - Moderate, plan wrap-up point
- `75-85%` - High, complete current item and save
- `>85%` - Critical, save immediately and start new session

### Phase-Based Development
Break work into phases (2-4 hours each). Each phase:
- Has clear, measurable goals
- Ends with passing tests
- Creates handoff documentation for next phase
- Commits only when complete

### Task Constants
Key decisions/files established in early phases that must NOT be modified in later phases. Prevents AI from "helpfully" recreating working code.

---

## 🔄 Typical Workflow

```
1. /start-session          ← Begin new chat
2. Work on tasks           ← Code, test, iterate
3. /check-status           ← Periodic health check
4. /update-context         ← Save progress mid-session
5. /phase-complete         ← When phase done, before commit
6. New chat                ← Fresh context for next phase
```

---

## 📁 Related Files (Project Root)

| File | Purpose | Portable? |
|------|---------|-----------|
| `CLAUDE.md` | AI entry point | ✅ Yes |
| `SOLUTION_ARCHITECTURE.md` | Project structure | ⚠️ Generate per project |
| `dev_context.md` | Session state | ⚠️ Generate per project |
| `.claude/commands/` | Slash commands | ✅ Yes |
| `.devcontainer/` | Container config | ✅ Yes (customize) |
| `docs/tasks/` | Project task files | ❌ Project-specific |

---

## 🚀 Setting Up New Project

See `NEW_PROJECT_CHECKLIST.md` for step-by-step guide.

Quick version:
1. Copy `.ai/`, `.claude/`, `.devcontainer/`, `CLAUDE.md` to new project
2. Create `docs/{tasks/completed,working,archive}` directories
3. Copy templates for `SOLUTION_ARCHITECTURE.md` and `dev_context.md`
4. Customize `.devcontainer/devcontainer.json` for your stack
5. Open in container, auth Claude, start working

---

## 🔧 Customization

### Adding Languages
Add new file to `.ai/standards/` following existing patterns.

### Modifying Workflows
Edit files in `.ai/workflows/` and corresponding `.claude/commands/`.

### Project-Specific Rules
Add to `SOLUTION_ARCHITECTURE.md` (not to portable `.ai/` files).

---

## 📚 Original Source

This system was adapted from a Windsurf AI workflow that achieved:
- Zero context degradation across multiple phases
- Successful multi-developer coordination
- Consistent code quality and documentation

Key adaptations for Claude Code:
- Slash commands in `.claude/commands/`
- Context monitoring via `/context` command
- Dev container isolation for safety
