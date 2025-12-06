# AI Claude Workflow - Basic Template

A portable, phase-based workflow system for AI-assisted development with Claude Code.

## 🎯 What Problem Does This Solve?

**Long AI chat sessions suffer from:**
- Context degradation (AI "forgets" earlier decisions)
- Lost progress (hard to resume work)
- Poor handoffs (next session starts from scratch)
- No structure (files end up everywhere)

**This template provides:**
- Phase-based development (2-4 hour chunks)
- Clean handoffs between sessions
- Context health monitoring
- Consistent file placement
- Portable structure you can copy to any project

## 🚀 Quick Start

### Option 1: Clone the repo
```bash
git clone https://github.com/szabeszcsi/ai-claude-workflow-basic.git my-project
cd my-project
rm -rf .git  # Remove template git history
git init     # Start fresh
```

### Option 2: Download ZIP
Download from GitHub and extract to your project folder.

### Then:
1. Edit `dev_context.md` - Add your name
2. Edit `.devcontainer/devcontainer.json` - Customize for your stack (see guide inside)
3. Open in VS Code → "Dev Containers: Reopen in Container"
4. Run `claude auth login` (first time only)
5. Start working with `/start-session`

## 📁 Structure

```
project/
├── CLAUDE.md                    ← AI reads this first
├── SOLUTION_ARCHITECTURE.md     ← Your project structure
├── dev_context.md               ← Session state & progress
│
├── .ai/                         ← 📦 Portable AI system
│   ├── workflows/               ← Full workflow protocols
│   ├── standards/               ← Coding standards (Python, SQL, DAX, JS)
│   ├── templates/               ← Document templates
│   └── guides/                  ← Task generation guide
│
├── .claude/commands/            ← 📦 Slash commands
│   ├── start-session.md
│   ├── check-status.md
│   ├── phase-complete.md
│   └── ...
│
├── .devcontainer/               ← 📦 Dev container config
│   ├── devcontainer.json
│   └── CUSTOMIZATION_GUIDE.md
│
└── docs/                        ← Project-specific docs
    ├── tasks/                   ← Task files & handoffs
    ├── working/                 ← Work in progress
    └── archive/                 ← Archived sessions
```

## 🛠️ Slash Commands

| Command | When to Use |
|---------|-------------|
| `/start-session` | Begin every new chat |
| `/check-status` | Verify context health |
| `/phase-complete` | Before committing completed work |
| `/update-context` | Save progress mid-session |
| `/abort` | Emergency recovery |
| `/generate-architecture` | Create project structure doc |

## 📋 Workflow Overview

```
1. /start-session        ← Load context, pick task
2. Work on code          ← Create files, tests
3. /check-status         ← Monitor context health
4. /update-context       ← Save progress if needed
5. /phase-complete       ← When phase done
6. New chat              ← Fresh context for next phase
```

## 🔒 Key Concepts

### Phase-Based Development
Break work into 2-4 hour phases. Each phase:
- Has clear, testable goals
- Ends with passing tests
- Creates handoff doc for next session
- Commits only when complete

### Task Constants
Key decisions made early that must NOT change in later phases (test scripts, signatures, etc.). Prevents AI from "helpfully" breaking working code.

### Context Monitoring
AI can't check its own context usage. Run `/context` command and share the percentage:
- `<60%` - Healthy
- `60-75%` - Plan wrap-up
- `75-85%` - Complete current item
- `>85%` - Save and start new chat

## 🐳 Dev Container

The template includes a generic dev container with:
- Ubuntu base (minimal)
- Python 3.12
- Node.js LTS (required for Claude CLI)
- Git

**Customize for your project:** See `.devcontainer/CUSTOMIZATION_GUIDE.md` for adding languages, frameworks, and tools.

## 📝 Coding Standards

Pre-configured standards in `.ai/standards/`:
- `_common.md` - Universal principles
- `python.md` - Python/PEP 8
- `sql.md` - SQL Server/T-SQL
- `dax.md` - DAX/Power BI
- `javascript.md` - JS/TypeScript

Claude loads only the relevant standard for your current task.

## ⚠️ Known Limitations

1. **VS Code Extension bugs** - WebSearch permissions may not work correctly. Slash commands should work, but if not, tell Claude: "read and execute `.claude/commands/start-session.md`"

2. **Claude auth** - Need to re-authenticate after container rebuild: `claude auth login`

## 🤝 Contributing

Found a bug or have an improvement? PRs welcome!

## 📄 License

MIT - Use freely, modify as needed.

---

**Origin:** Adapted from a Windsurf AI workflow system that achieved zero context degradation across multi-phase projects. Ported to Claude Code Extension + VS Code Dev Containers.
