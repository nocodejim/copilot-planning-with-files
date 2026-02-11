# Manus Principles: Deep Dive

This document explains the core principles from Manus AI that make planning-with-files effective.

## Background: Manus AI

On December 29, 2025, Meta acquired Manus AI for $2 billion. Manus was an AI agent company that pioneered "context engineering" — using filesystem as persistent memory for AI agents.

> "Markdown is my 'working memory' on disk. Since my context has limits, Markdown files serve as checkpoints for progress."
> — Manus AI

## The Five Core Principles

### 1. Filesystem as Memory

**Problem:** AI context windows are volatile (64k-128k tokens) and reset/compact.

**Solution:** Use filesystem as external memory.

```
Context Window = RAM (volatile, limited)
Filesystem = Disk (persistent, unlimited)
```

**Implementation in Copilot:**
- task_plan.md stores roadmap and progress
- findings.md stores research and decisions
- progress.md stores session history
- Files persist across context resets

**Why It Works:** Filesystem survives when context doesn't. It's your external brain.

---

### 2. Attention Manipulation

**Problem:** AI agents forget instructions as context fills up.

**Solution:** Use explicit, persistent reminders to guide attention.

**Manus Approach:** PreToolUse hooks re-read plan before every action.

**Copilot Adaptation:**
- .github/copilot-instructions.md loaded at session start
- Agent Skill provides context-aware reminders
- Template comments remind to read files
- /update-plan command structures updates
- User discipline replaces automated hooks

**Why It Works:** Explicit instructions shape behavior even without hooks.

---

### 3. Error Persistence

**Problem:** AI agents repeat the same mistakes because errors aren't tracked.

**Solution:** Log every error in task_plan.md error table.

**Implementation:**
```markdown
## Errors Encountered

| Error | Attempt | Resolution |
|-------|---------|------------|
| ImportError: No module 'foo' | 1 | Installed missing package |
| Test timeout | 2 | Added await keyword |
```

**3-Strike Protocol:**
1. Attempt 1: Diagnose & fix
2. Attempt 2: Alternative approach (never repeat exact same action)
3. Attempt 3: Broader rethink
4. After 3: Escalate to user

**Why It Works:** Error table builds institutional knowledge, prevents repetition.

---

### 4. Goal Tracking

**Problem:** Long sessions lead to goal drift and scope creep.

**Solution:** Use phases with checkboxes to track progress.

**Implementation:**
```markdown
## Current Phase
Phase 3

### Phase 1: Requirements ✅ complete
### Phase 2: Design ✅ complete
### Phase 3: Implementation 🔄 in_progress
  - [x] Core features
  - [ ] Edge cases
  - [ ] Tests
```

**Why It Works:**
- Visual progress indication
- Clear current focus
- Easy to see what's done vs remaining
- Prevents scope creep

---

### 5. Completion Verification

**Problem:** Sessions end with incomplete work, no verification step.

**Solution:** Explicit completion check before closing.

**Manus Approach:** Stop hook verifies all phases complete before exit.

**Copilot Adaptation:**
- /check-complete command runs manual verification
- Counts complete vs incomplete phases
- Lists unfinished checklist items
- Suggests next actions or confirms done

**Why It Works:** Prevents premature closure, ensures completeness.

---

## The 2-Action Rule (Bonus Principle)

**Problem:** Visual/multimodal information (images, PDFs, browser) gets lost when context resets.

**Solution:** After every 2 view/browser/search operations, immediately save findings to findings.md.

**Why 2 and not 3 or 1?**
- 1: Too frequent, disruptive
- 3+: Risk losing information before writing
- 2: Balance between efficiency and safety

**Example:**
```
✅ Good:
1. Search "React hooks tutorial"
2. View top result
3. WRITE TO FINDINGS.MD

❌ Bad:
1-5. Search and view multiple pages
6. Context resets → All info lost!
```

---

## Copilot-Specific Adaptations

### Without Hooks, How Do We Apply These?

**Principle 1: Filesystem as Memory**
- ✅ Same — Files work identically
- No adaptation needed

**Principle 2: Attention Manipulation**
- ⚠️ Adapted — Explicit reminders instead of hooks
- .github/copilot-instructions.md always loaded
- Agent Skill auto-loads when files exist
- Template comments guide behavior
- User must build habit

**Principle 3: Error Persistence**
- ✅ Same — Error table identical
- User must manually log errors

**Principle 4: Goal Tracking**
- ✅ Same — Phases and checkboxes identical
- /update-plan guides phase updates

**Principle 5: Completion Verification**
- ⚠️ Adapted — Manual /check-complete vs automatic
- User must remember to run command

---

## Why This Pattern Works for Complex Tasks

### Traditional AI Workflow (Without Planning)

```
User: "Build feature X"
AI: *implements*
Context fills → compacts → forgets early goals
AI: *continues but drifts from original intent*
User: "This isn't what I wanted"
```

### Planning-with-Files Workflow

```
User: "Build feature X"
AI: Creates task_plan.md with phases
AI: Implements Phase 1
AI: Updates task_plan.md
Context resets
AI: Reads task_plan.md → Recovers full context
AI: Continues Phase 2 aligned with original goal
User: "Perfect!"
```

---

## The Meta-Application

This very repository was built using planning-with-files:
- See `/home/jim/projects/copilot-pro/examples/` for the actual planning files used
- task_plan.md had 8 phases (Requirements → Delivery)
- findings.md captured research on Copilot capabilities
- progress.md tracked implementation progress
- Result: Complete, validated specifications ready for implementation

Planning-with-files used to plan planning-with-files. Very meta. Very Manus.

---

## Further Reading

- [Manus AI announcement](https://news.ycombinator.com/item?id=42541791)
- [Lance Martin's analysis](https://lancemartin.substack.com/)
- [Original planning-with-files](https://github.com/OthmanAdi/planning-with-files)

---

**Key Takeaway:** Filesystem is your AI's external hard drive. Use it.
