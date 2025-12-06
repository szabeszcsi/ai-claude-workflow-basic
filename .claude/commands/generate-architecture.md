---
description: Create or update SOLUTION_ARCHITECTURE.md
---

# /generate-architecture

**Use for:**
- New project setup
- Documenting existing project
- After major refactoring

**Mode A: Analyze existing project**

1. Scan structure:
   ```bash
   find . -type f -name "*.py" -o -name "*.js" | head -50
   ls -la
   ```

2. Identify patterns (src location, tests, config)

3. Ask clarifying questions:
   - Confirm source/test locations
   - Project type (API, CLI, library)?
   - Languages/frameworks?

4. Generate `SOLUTION_ARCHITECTURE.md`

**Mode B: Design new project**

1. Gather requirements:
   - What does it do?
   - Project type?
   - Languages/frameworks?
   - Expected size?

2. Propose structure:
   ```
   {project}/
   ├── src/
   ├── tests/
   ├── config/
   └── docs/
   ```

3. Confirm with user

4. Generate `SOLUTION_ARCHITECTURE.md`

**Output includes:**
- Directory structure with descriptions
- Component responsibilities
- File placement rules
- Naming conventions
- Entry points

**Template:** `.ai/templates/SOLUTION_ARCHITECTURE_TEMPLATE.md`

**Full protocol:** `.ai/workflows/generate-architecture.md`
