# GitHub Copilot Planning Instructions

You are working in a repository that uses **Manus-style file-based planning**. This methodology uses three persistent markdown files as your "working memory on disk" to prevent context loss and goal drift.

## Core Principle

```
Context Window = RAM (volatile, limited 64k-128k tokens)
Filesystem = Disk (persistent, unlimited)

→ Anything important gets written to disk.
```

## The Three Planning Files

When working on complex tasks (3+ steps, research, multi-file projects), you will use:

1. **task_plan.md** — Roadmap with phases, progress tracking, decisions, errors
2. **findings.md** — Research discoveries, technical decisions, resources
3. **progress.md** — Session log, test results, 5-Question Reboot Check

## Getting Started

**To start planning on a new task:**
```
/plan "Your task description here"
```

This command creates the three planning files from templates and initializes your workflow.

## Critical Rules

### 1. Create Plan First
Never start a complex task without task_plan.md. Non-negotiable.

### 2. Read Before Decide
**Before making major decisions or implementations:**
1. Re-read task_plan.md (check current phase, goals, past errors)
2. Check findings.md (review research and discoveries)
3. Review progress.md if resuming after a break

### 3. Update After Act
After completing ANY phase or significant work:
- Mark phase status: `pending` → `in_progress` → `complete`
- Log any errors encountered (they prevent repetition)
- Note files created/modified
- Update progress.md with actions taken

### 4. The 2-Action Rule
After every 2 view/browser/search operations, IMMEDIATELY save key findings to findings.md.
This prevents visual/multimodal information from being lost.

### 5. Log ALL Errors
Every error goes in task_plan.md's error table. This builds knowledge and prevents repeating failures.

```markdown
## Errors Encountered
| Error | Attempt | Resolution |
|-------|---------|------------|
| FileNotFoundError | 1 | Created default config |
```

### 6. Never Repeat Failures
```
if action_failed:
    next_action != same_action
```
Track what you tried. Mutate the approach. Use the 3-Strike Protocol.

## The 3-Strike Error Protocol

```
ATTEMPT 1: Diagnose & Fix
  → Read error carefully, identify root cause, apply targeted fix

ATTEMPT 2: Alternative Approach
  → Same error? Try different method/tool/library
  → NEVER repeat exact same failing action

ATTEMPT 3: Broader Rethink
  → Question assumptions, search for solutions, consider updating plan

AFTER 3 FAILURES: Escalate to User
  → Explain what you tried, share error, ask for guidance
```

## Read vs Write Decision Matrix

| Situation | Action | Reason |
|-----------|--------|--------|
| Just wrote a file | DON'T read | Content still in context |
| Viewed image/PDF/browser | Write findings NOW | Multimodal → text before lost |
| Starting new phase | Read plan/findings | Re-orient if context stale |
| Resuming after break | Read ALL planning files | Recover full state |
| Error occurred | Read relevant planning file | Need current state to fix |

## Helpful Commands

- `/plan` — Initialize planning files for a new task
- `/update-plan` — Guided workflow to update task_plan.md status
- `/check-complete` — Verify all phases complete before ending session

## When to Use Planning Files

**Use for:**
- Multi-step tasks (3+ steps)
- Research tasks
- Building/creating projects
- Tasks spanning many tool calls

**Skip for:**
- Simple questions
- Single-file edits
- Quick lookups

## Resuming a Session

If resuming after a break or context reset:
1. Read task_plan.md (see current phase and goals)
2. Read findings.md (review discoveries)
3. Read progress.md (see what was last done)
4. Update progress.md with "Session resumed" entry
5. Answer the 5-Question Reboot Check in progress.md

## Anti-Patterns (Don't Do These)

| Don't | Do Instead |
|-------|------------|
| State goals once and forget | Re-read task_plan.md before decisions |
| Hide errors and retry silently | Log errors to task_plan.md |
| Stuff everything in context | Store large content in findings.md |
| Start executing immediately | Create task_plan.md FIRST |
| Repeat failed actions | Track attempts, mutate approach |

## Templates

Planning file templates are in `.github/planning-templates/`. The `/plan` command automatically copies and initializes them for you.

---

**Remember:** Planning files are your persistent memory. Context windows reset, but filesystem persists forever. Use it.
