# Task File Generation Guide

How to create effective phase-based task files for AI-assisted development.

---

## Why Phase-Based Tasks?

**Problem:** Long tasks in single chat → context degradation, lost progress, poor handoffs

**Solution:** Break into phases (2-4 hours each):
- Focused scope per phase
- Clean handoffs between sessions
- Testable milestones
- Fresh context each phase

---

## The Three-Document Pattern

Every phase needs:

1. **Master Task File** (`docs/tasks/{feature}_tasks.md`)
   - Complete implementation guide
   - All phases, comprehensive reference
   - Updated as phases complete

2. **Phase Handoff** (`docs/tasks/{component}_phase{N}_handoff.md`)
   - Detailed guide for ONE phase
   - Created at END of previous phase
   - Implementation steps, code examples

3. **Start Prompt** (in `dev_context.md`)
   - Ready-to-paste chat starter
   - Minimal, tells AI what to load

---

## Creating a Task File

### Step 1: Gather Information

Ask yourself/user:
- What feature are we building?
- What's the expected scope? (small/medium/large)
- Are there existing patterns to follow?
- What are the key requirements?

### Step 2: Break Into Phases

**Rules:**
- Each phase: 2-4 hours of work
- Each phase: Delivers working, tested code
- Each phase: Self-contained (not dependent on uncommitted future work)

**Typical breakdown:**
- Phase 1: Core components (parsing, models)
- Phase 2: Processing/analysis
- Phase 3: Enhancement (AI, enrichment)
- Phase 4: Output generation
- Phase 5: Integration/orchestration

### Step 3: Define Success Criteria

For each phase:
- Specific deliverables (files to create)
- Measurable outcomes
- Test requirements (minimum count)
- Performance targets (if applicable)

### Step 4: Use the Template

Copy from `.ai/templates/TASK_FILE_TEMPLATE.md`

Fill in:
- Overview and goals
- Phase breakdown
- File paths for each component
- Success criteria
- References to patterns

---

## Task Constants

Key decisions that must be preserved across ALL phases.

### What to Track:
- Test scripts with specific setup
- Constructor/method signatures
- Config structure keys
- Fixture file paths
- Architectural decisions

### Lifecycle:
1. **Phase 1:** Create initial constants
2. **Phases 2-N:** Add new, never remove
3. **Final phase:** Archive to completion doc, remove from dev_context

### Size Limit:
- < 500 bytes in dev_context.md
- If larger, create `docs/working/{task}_constants.md`

---

## Phase Completion Checklist

Every phase MUST include these final steps:

```
- [ ] Run tests and validate
- [ ] Update Task Constants if new key items
- [ ] Create completion doc
- [ ] Create handoff doc (unless final)
- [ ] Copy Task Constants to handoff
```

---

## Anti-Patterns to Avoid

❌ **Vague goals:** "Setup the project"
✅ **Specific goals:** "Parse PBIR files and extract page/visual structure"

❌ **Phases too large:** 3 weeks in one phase
✅ **Right size:** 2-4 hours per phase

❌ **Missing tests:** "Make sure it works"
✅ **Test requirements:** "15+ tests passing, 80% coverage"

❌ **No handoff:** Just commit and move on
✅ **Full handoff:** Completion doc, handoff doc, start prompt

❌ **Code in chat:** Explaining implementation in conversation
✅ **Create files:** Make the actual files, show <10 line snippets

---

## Example Phase Structure

```markdown
### Phase 1: Core Parsing
**Goal:** Parse config files and extract structure

**Components:**
1. `src/parser/config_parser.py` - Main parser
2. `src/parser/validators.py` - Input validation

**Tests:**
- `tests/unit/parser/test_config_parser.py`
- `tests/unit/parser/test_validators.py`

**Success Criteria:**
- Parse all config formats (YAML, JSON)
- Validate required fields
- 12+ tests passing
- Handle malformed input gracefully
```

---

## Templates Reference

| Template | Use For |
|----------|---------|
| `TASK_FILE_TEMPLATE.md` | Master task file |
| `HANDOFF_TEMPLATE.md` | Phase handoffs |
| `COMPLETION_TEMPLATE.md` | Phase completion docs |
| `DEV_CONTEXT_TEMPLATE.md` | Session state |

All in `.ai/templates/`

---

## Quick Start

1. Copy `TASK_FILE_TEMPLATE.md` to `docs/tasks/{feature}_tasks.md`
2. Fill in overview and phases
3. Create Phase 1 handoff from `HANDOFF_TEMPLATE.md`
4. Update `dev_context.md` with start prompt
5. Begin work!
