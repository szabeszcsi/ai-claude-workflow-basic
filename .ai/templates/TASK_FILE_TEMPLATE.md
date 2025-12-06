# Task: {Feature Name}

**Developer:** {Name}  
**Branch:** `feature/{feature-name}`  
**Timeline:** {N} phases ({estimate})  
**Priority:** {HIGH/MEDIUM/LOW}  
**Status:** {📋 Ready / 🚧 In Progress / ✅ Complete}

---

## Overview

{2-3 sentence description of the feature and its purpose}

---

## 🔒 Task Constants Tracking

Track key decisions that must be preserved across ALL phases.

| Item | Value | Established | Status |
|------|-------|-------------|--------|
| *Add as phases progress* | | | |

**Rules:**
- Add items as key decisions are made
- Never remove until task FULLY complete
- Copy to each handoff doc AND dev_context.md

---

## Phases

### ✅ Phase 0: Planning (if applicable)
**Goal:** {What this phase achieved}

**Deliverables:**
- ✅ {Deliverable 1}
- ✅ {Deliverable 2}

---

### 📋 Phase 1: {Phase Name}
**Goal:** {Specific, measurable goal}

**Components to Create:**
1. `src/{component}/{file1}.py` - {Purpose}
2. `src/{component}/{file2}.py` - {Purpose}

**Tests:**
- `tests/unit/{component}/test_{file1}.py`
- `tests/unit/{component}/test_{file2}.py`

**Success Criteria:**
- {Specific criterion 1}
- {Specific criterion 2}
- {N}+ tests passing

---

### 📋 Phase 2: {Phase Name}
**Goal:** {Specific, measurable goal}

**Components:**
1. `{path}` - {Purpose}

**Success Criteria:**
- {Criteria}

---

### 📋 Phase N: {Final Phase}
**Goal:** {Final integration/completion goal}

**Task Constants Handling:**
- Archive all constants to completion doc
- Remove from dev_context.md

---

## Quick Start

**New chat prompt:**
```
I'm {Name}. Starting {Feature} Phase {X}.

Read:
1. dev_context.md
2. docs/tasks/{feature}_phase{X}_handoff.md

Branch: feature/{feature-name}
```

---

## Success Criteria (Overall)

**Minimum (Must Have):**
- {Core requirement 1}
- {Core requirement 2}

**Good (Should Have):**
- {Enhanced feature 1}

---

## Files to Create

```
src/{component}/
├── {file1}.py              # NEW
└── {file2}.py              # NEW

tests/unit/{component}/
└── test_{file}.py          # NEW
```

---

## References

- Architecture: `SOLUTION_ARCHITECTURE.md`
- Standards: `.ai/standards/{language}.md`
- Similar: `{reference to similar existing code}`

---

## Notes

{Any important context, constraints, or decisions}
