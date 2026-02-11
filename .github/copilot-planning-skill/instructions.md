# Detailed Workflow Instructions

This document provides step-by-step instructions for using the planning-with-files methodology with GitHub Copilot.

## Complete Workflow

### Starting a New Task

1. **Initialize Planning Files**
   ```
   /plan "Your task description"
   ```
   - Creates task_plan.md, findings.md, progress.md
   - Initializes templates with your task context
   - Sets Phase 1 to in_progress

2. **Review Your Plan**
   - Open task_plan.md
   - Review the phases and checkboxes
   - Understand the goal and current phase

3. **Begin Phase 1: Requirements & Discovery**
   - Research and gather requirements
   - Document findings in findings.md
   - Update progress.md with discoveries

### During Active Work

1. **Before Making Decisions**
   - Read task_plan.md → Check current phase and goals
   - Read findings.md → Review past research and decisions
   - Read progress.md → See what was done recently

2. **While Working**
   - After 2 searches/views → Update findings.md (2-Action Rule)
   - After completing work → Update progress.md with actions
   - If errors occur → Log in task_plan.md error table

3. **After Completing a Phase**
   - Run `/update-plan` command
   - Mark phase as complete
   - Log any decisions or errors
   - Review next phase before starting

### Resuming After a Break

1. **Read All Planning Files**
   ```
   - task_plan.md → Where am I? Where am I going?
   - findings.md → What have I learned?
   - progress.md → What have I done?
   ```

2. **Update Progress Log**
   - Add "Session resumed" entry
   - Answer 5-Question Reboot Check

3. **Continue From Current Phase**
   - Check task_plan.md for current phase
   - Review any errors or blockers
   - Continue work

### Completing the Task

1. **Run Completion Check**
   ```
   /check-complete
   ```
   - Verifies all phases marked complete
   - Lists any unfinished items
   - Suggests next steps

2. **Final Review**
   - Review all deliverables
   - Verify all checkboxes marked
   - Update progress.md with final status

## The 2-Action Rule Explained

**Why:** Visual/multimodal information (images, PDFs, browser views) is lost when context window resets or compacts.

**How:**
1. Perform a view/browser/search operation
2. Perform another view/browser/search operation
3. **IMMEDIATELY** write key findings to findings.md

**Example:**
```
✅ Good:
1. Search for "React hooks tutorial"
2. View top result
3. Write to findings.md: "React hooks: useState for state, useEffect for side effects..."

❌ Bad:
1. Search and view 5 different pages
2. (context resets)
3. All visual information lost!
```

## Error Logging Pattern

**When to Log:**
- Build/compile errors
- Test failures
- Import/dependency errors
- Logic errors that require debugging
- Any error that took >5 minutes to resolve

**How to Log (in task_plan.md):**
```markdown
## Errors Encountered

| Error | Attempt | Resolution |
|-------|---------|------------|
| TypeError: undefined is not a function | 1 | Added null check before calling method |
| Test failure: login.test.ts | 2 | Updated mock data to match new API response |
```

**Why:** Prevents repeating the same mistakes, builds institutional knowledge.

## Phase Management

### Phase Lifecycle

```
pending → in_progress → complete
```

### When to Move Phases

**Mark as in_progress:**
- When you start working on that phase
- Update "Current Phase" in task_plan.md

**Mark as complete:**
- When ALL checkboxes in that phase are done
- When deliverables for that phase exist
- Run `/update-plan` to guide you through this

**Stay in same phase:**
- If blocked or encountering errors
- If research is incomplete
- If deliverables aren't ready

### Example Phase Progression

```
Phase 1: Requirements ✅ complete
  → All research done, findings documented

Phase 2: Design ✅ complete
  → Architecture decided, documented in findings.md

Phase 3: Implementation 🔄 in_progress
  → Core features built, tests still pending

Phase 4: Testing ⏸️ pending
  → Waiting for Phase 3 to complete
```

## Decision Tracking

**When to Log Decisions:**
- Architectural choices (framework, library, pattern)
- Technical approaches (algorithm, data structure)
- Tradeoffs (performance vs simplicity)
- User-facing choices (UX, API design)

**Format (in task_plan.md):**
```markdown
## Decisions Made

| Decision | Rationale | Date |
|----------|-----------|------|
| Use React instead of Vue | Team familiarity, larger ecosystem | 2026-02-11 |
| PostgreSQL over MongoDB | Need for ACID transactions | 2026-02-11 |
```

**Why:** Documents reasoning for future reference, prevents relitigating decisions.

## File Interaction Patterns

### task_plan.md
- **Read:** Before starting work, after errors, when resuming
- **Write:** After completing phases, when logging errors, when making decisions
- **Frequency:** 2-3 times per work session

### findings.md
- **Read:** Before making technical decisions, when resuming
- **Write:** After every 2 searches/views, after research, after decisions
- **Frequency:** Often during research phases, less during implementation

### progress.md
- **Read:** When resuming sessions, to see recent work
- **Write:** After any significant work, at end of session
- **Frequency:** Multiple times per session, especially at session boundaries

## Using @workspace

Copilot's @workspace feature can search your codebase. Combine with planning files:

```
Good prompts:
- "Based on task_plan.md, what should I work on next?"
- "Review findings.md and suggest next research steps"
- "Check progress.md - what was I working on last?"
- "@workspace find files related to authentication"
```

## Recovery from Context Reset

If Copilot's context resets (auto-compaction at 95% tokens):

1. **Don't panic** - Planning files persist!
2. Read task_plan.md - recover your roadmap
3. Read findings.md - recover your research
4. Read progress.md - recover your history
5. Continue where you left off

**This is the core value of planning-with-files**: Filesystem survives context resets.

## Tips for Success

1. **Be disciplined** - Without hooks, you must manually update files
2. **Use commands** - `/plan`, `/update-plan`, `/check-complete` reduce friction
3. **Build habits** - Like git commits, make file updates automatic
4. **Trust the system** - Planning files are your safety net
5. **Don't over-plan** - For simple tasks, skip the planning files
