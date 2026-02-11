# Real-World Examples

This document shows how planning files evolve during actual development tasks.

## Example 1: Building a CLI Todo App

### Initial task_plan.md (After /plan)

```markdown
# Task Plan: Build CLI Todo App

## Goal
Create a command-line todo application with add, list, and delete commands using Node.js.

## Current Phase
Phase 1

## Phases

### Phase 1: Requirements & Discovery
- [ ] Research CLI libraries (commander, yargs, etc.)
- [ ] Research data storage options
- [ ] Define command interface
- **Status:** in_progress

### Phase 2: Setup & Structure
- [ ] Initialize Node.js project
- [ ] Install dependencies
- [ ] Create file structure
- **Status:** pending
```

### findings.md (After Research)

```markdown
# Findings: CLI Todo App

## Library Research

### CLI Frameworks
**Commander.js** - Chosen
- Clean API, widely used
- Good TypeScript support
- Active maintenance

**Yargs** - Considered
- More features but complex
- Overkill for simple app

### Storage Options
**JSON file** - Chosen
- Simple, no dependencies
- Easy to debug
- Sufficient for CLI app

**SQLite** - Considered
- Overkill for simple todo list
- Adds complexity
```

### progress.md (After Phase 1)

```markdown
# Progress Log: CLI Todo App

## Session: 2026-02-11

### Phase 1: Requirements & Discovery — Complete
**Status:** complete

#### Actions Taken
- Researched CLI libraries: commander.js vs yargs
- Decided on commander.js (simpler API)
- Researched storage: JSON file vs SQLite
- Decided on JSON file (appropriate for scope)
- Documented all findings in findings.md

#### Files Created/Modified
- findings.md — Library and storage research

#### Next Steps
- Begin Phase 2: Setup & Structure
```

## Example 2: Debugging a Complex Error

### task_plan.md (Error Logged)

```markdown
## Errors Encountered

| Error | Attempt | Resolution |
|-------|---------|------------|
| "Cannot find module './config'" | 1 | Path was relative, changed to absolute |
| "Cannot find module './config'" | 2 | Forgot to export, added module.exports |
| Test timeout after 5000ms | 1 | Async function not awaited, added await |
```

### progress.md (Debugging Session)

```markdown
### Phase 3: Implementation — In Progress

#### Actions Taken
- Implemented config loader
- Hit "Cannot find module" error
- Attempt 1: Fixed relative path → still failing
- Attempt 2: Realized missing export → FIXED
- Started writing tests
- Hit timeout error → missing await → FIXED
- All tests now passing ✅
```

**Learning:** Error table prevented repeating attempt 1's solution after it failed.

## Example 3: The 2-Action Rule in Practice

### Scenario: Researching React State Management

```markdown
# findings.md

## State Management Research (2026-02-11)

### Searched "React state management 2025"
- Top result: Redux still popular but Context API sufficient for small apps
- Zustand emerging as lightweight alternative

### Viewed Redux Toolkit documentation
- Redux Toolkit reduces boilerplate significantly
- But still requires significant setup

[WROTE TO FINDINGS.MD HERE - 2 actions complete!]

### Decision
- Use Context API for this project
- Scope: Small app, 2-3 global states
- Rationale: Avoid Redux complexity for simple case
```

**Why this works:** Visual info (docs, screenshots) captured as text before context reset.

## Example 4: Session Resumption

### progress.md (Session Boundary)

```markdown
## Session: 2026-02-10 Evening
- Completed Phase 2: Setup
- Started Phase 3: Implementing auth
- Got blocked on JWT library choice
- Status: Paused at auth implementation

## Session: 2026-02-11 Morning - RESUMED

### 5-Question Reboot Check
1. **Where am I?** Phase 3, auth implementation started
2. **Where am I going?** Complete auth, then move to Phase 4 (testing)
3. **What's the goal?** User authentication system
4. **What have I learned?** JWT vs session tokens (see findings.md)
5. **What have I done?** Setup complete, auth route stubbed out

### Actions
- Re-read task_plan.md → Confirmed in Phase 3
- Re-read findings.md → Saw JWT decision pending
- Made decision: Use JWT (stateless, mobile-friendly)
- Implemented JWT auth
- Updated findings.md with decision
```

**Learning:** 5-Question Reboot Check restored full context after overnight break.

## Example 5: Update Plan Command

### Before /update-plan

**User:** "Just finished Phase 2"

**Copilot:**
```
Which phase did you just complete? Phase 2: Setup & Structure

What is the status? complete

Did you encounter any errors? Yes
Describe: npm install failed initially
Resolution: Network issue, ran again successfully

Did you make any important decisions? Yes
Decision: Use Jest instead of Mocha
Rationale: Better React integration

Any files created/modified?
- package.json
- jest.config.js
- src/index.ts

✅ Updated task_plan.md and progress.md

Current Phase: Phase 3
Next: Implement core features
```

**Learning:** Guided workflow ensures consistent updates.

## Example 6: Check Complete Command

### Before Closing Session

**User:** `/check-complete`

**Copilot:**
```
⚠️ TASK NOT COMPLETE

**Summary:**
- ✅ 3 phases complete
- 🔄 1 phase in progress
- ⏸️ 1 phase pending

**Incomplete Phases:**
- Phase 4: Testing (in_progress)
- Phase 5: Documentation (pending)

**Unfinished checklist items:**
- [ ] Write integration tests
- [ ] Add README examples
- [ ] Create deployment guide

**Recommendation:**
Continue with Phase 4 or update task_plan.md if scope has changed.
```

**Learning:** Prevented closing session with incomplete work.

## Anti-Pattern Examples

### ❌ Bad: Forgetting to Update

```markdown
# task_plan.md (stale)
Current Phase: Phase 1

# (User actually completed Phases 1-3)
# Files exist but plan not updated
# Context lost, no record of decisions
```

### ✅ Good: Consistent Updates

```markdown
# task_plan.md (current)
Current Phase: Phase 4

### Phase 1 ✅ complete
### Phase 2 ✅ complete
### Phase 3 ✅ complete
### Phase 4 🔄 in_progress
```

### ❌ Bad: Repeating Failed Actions

```markdown
# progress.md
- Tried "npm install package-a" → Failed
- Tried "npm install package-a" → Failed again
- Tried "npm install package-a" → Still failing!
```

### ✅ Good: 3-Strike Protocol

```markdown
# task_plan.md Error Table

| Error | Attempt | Resolution |
|-------|---------|------------|
| Package-a install fails | 1 | Checked npm registry, package exists |
| Package-a install fails | 2 | Tried yarn instead → still fails |
| Package-a install fails | 3 | Searched issue tracker, found Node 20 required, upgraded Node → FIXED |
```

## Summary

These examples show:
- How planning files evolve during real work
- How error logging prevents repetition
- How 2-Action Rule captures research
- How session resumption recovers context
- How commands guide workflow
- How anti-patterns waste time

**Key takeaway:** Planning files are living documents that grow with your project.
