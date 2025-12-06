# {Component} Phase {N} Handoff

**Created:** {Date}  
**Developer:** {Name}  
**Branch:** `{branch}`  
**Status:** Phase {N-1} COMPLETE ✅ - Ready for Phase {N}

---

## 🔒 Task Constants (DO NOT MODIFY)

These were established in earlier phases and **MUST be preserved**.

| Item | Value | Established | Notes |
|------|-------|-------------|-------|
| Test script | `{path}` | Phase {X} | DO NOT RECREATE |
| Constructor | `{Class(params)}` | Phase {X} | DO NOT CHANGE |
| {Other} | `{value}` | Phase {X} | {notes} |

---

## Current Status

### Completed Phases

**Phase {N-1}: {Name}** ✅
- `{Component1}` ({X} lines) - {Purpose}
- `{Component2}` ({X} lines) - {Purpose}
- {X} tests passing

**Total Progress:**
- ~{X} lines of code
- {X} tests passing
- All components < 500 lines

---

## 🎯 Phase {N}: {Phase Name}

### Goal
{1-2 sentence clear description of what this phase achieves}

### Why This Matters
{Brief explanation of importance}

---

## Components to Create

### {ComponentName} (~{X} lines)
**File:** `src/{component}/{file}.py`

**Responsibilities:**
- {Responsibility 1}
- {Responsibility 2}

**Pattern to Follow:**
Copy structure from `{reference_file}`

**Key Methods:**
```python
class {ComponentName}:
    """Brief description."""
    
    def __init__(self, {params}) -> None:
        """Initialize."""
        
    def {method1}(self, {params}) -> {ReturnType}:
        """Description."""
```

---

## Implementation Steps

### Step 1: {Step Name}
**Goal:** {What this achieves}

1. {Specific action}
2. {Specific action}
3. {Specific action}

### Step 2: {Step Name}
**Goal:** {What this achieves}

1. {Specific action}
2. {Specific action}

---

## Testing

**Test File:** `tests/unit/{component}/test_{file}.py`

**Test Cases:**
- Test {scenario 1}
- Test {scenario 2}
- Test error handling for {scenario}

**Target:** {X}+ tests passing

---

## References

- **Pattern:** `{file to follow}`
- **Architecture:** `SOLUTION_ARCHITECTURE.md`
- **Standards:** `.ai/standards/{language}.md`

---

## Success Criteria

Phase {N} is complete when:
- ✅ {Component} created and tested
- ✅ {X}+ tests passing
- ✅ All components < 500 lines
- ✅ Task Constants preserved

---

## After Phase {N}

**Next Phase:** Phase {N+1} - {Name}
{1 sentence description}

**Update Task Constants if needed:**
- New test scripts → add
- New key signatures → add
- Never remove existing

---

**Ready to start!** 🚀

First action: Review Task Constants, then {specific first step}.
