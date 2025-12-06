# Workflow Quick Reference

## Slash Commands

| Command | When | Priority |
|---------|------|----------|
| `/start-session` | Every new chat | 🔴 Required |
| `/phase-complete` | Phase done, before commit | 🔴 Required |
| `/check-status` | Verify context health | 🟡 Periodic |
| `/update-context` | Mid-phase progress save | 🟢 Optional |
| `/abort` | Emergency rollback | 🔴 Emergency |
| `/generate-architecture` | Create/update project structure | 🟢 Setup |

---

## Context Health (from `/context` command)

| Usage | Status | Action |
|-------|--------|--------|
| < 60% | ✅ Healthy | Continue freely |
| 60-75% | ⚠️ Moderate | Plan wrap-up point |
| 75-85% | 🟠 High | Complete current item, save |
| > 85% | 🚨 Critical | Save immediately, new session |

---

## File Locations

```
Project Root:
├── CLAUDE.md              ← AI entry point
├── SOLUTION_ARCHITECTURE.md  ← Project structure
├── dev_context.md         ← Session state
│
├── .ai/                   ← Portable AI system
│   ├── workflows/         ← Full protocols
│   ├── standards/         ← Coding standards
│   ├── templates/         ← Doc templates
│   └── guides/            ← Guides
│
├── .claude/commands/      ← Slash commands
├── .devcontainer/         ← Container config
│
└── docs/
    ├── tasks/             ← Task files & handoffs
    │   └── completed/     ← Archived handoffs
    ├── working/           ← WIP files
    └── archive/           ← Old sessions
```

---

## ⛔ Never

- Pretend to remember when starting from checkpoint
- Commit without `/phase-complete`
- Continue chat after phase complete
- Create files in project root (except CLAUDE.md, SOLUTION_ARCHITECTURE.md, dev_context.md)
- Write implementation code in chat (create files instead)
- Ignore 🚨 prompts
- Modify Task Constants without explicit permission

---

## Dev Context Size

| Size | Status |
|------|--------|
| < 1.5 KB | ✅ Healthy |
| 1.5-2 KB | ⚠️ Archive soon |
| > 2 KB | 🚨 Archive now |

---

## Quick Actions

| Situation | Action |
|-----------|--------|
| New chat | `/start-session` |
| Made progress, not done | `/update-context` |
| Phase complete | `/phase-complete` |
| Confused about state | `/check-status` |
| Something broke | `/abort` |
| New project setup | `/generate-architecture` |
| Context > 75% | Wrap up, `/update-context`, new chat |
