# Workflow Diagram

This document describes the planning-with-files workflow for GitHub Copilot.

## File Flow

```
.github/planning-templates/
  ├── task_plan.md       ─┐
  ├── findings.md        ─┼─> /plan command
  └── progress.md        ─┘
                           │
                           ↓
                    Project Root/
                      ├── task_plan.md
                      ├── findings.md
                      └── progress.md
```

## Command Flow

```
/plan "task"
  └──> Creates planning files from templates
        └──> Initialize with task context
              └──> Set Phase 1 to in_progress

During Work:
  Read task_plan.md ──> Make decisions ──> Update files
                                            └──> /update-plan
                                                  └──> Guided update workflow

End Session:
  /check-complete ──> Verify all phases done
                      └──> Ready to close (or continue work)
```

## Agent Skill Activation

```
Planning files exist?
  ├─ Yes ──> Agent Skill loads automatically
  │           └──> Context-aware reminders
  │                 └──> Before major actions: Check files
  │                       After work: Update files
  └─ No ──> Only core instructions active
```

## Session Start/Resume

```
VS Code launches
  └──> Loads .github/copilot-instructions.md
        └──> Instructions active for all requests

Planning files exist?
  └──> Yes: Agent Skill activates
        └──> Suggests reading files if resuming
              └──> 5-Question Reboot Check
```

## The 3-File Pattern in Action

```
Phase Start:
  1. Read task_plan.md (current phase goals)
  2. Check findings.md (past decisions)
  3. Review progress.md (recent work)

During Phase:
  - Research/view/search (×2) ──> Update findings.md
  - Complete work ──> Update progress.md
  - Hit errors ──> Log in task_plan.md

Phase Complete:
  - Run /update-plan
  - Mark phase complete
  - Move to next phase
```

## Context Reset Recovery

```
Context window at 95% ──> Auto-compaction
                           └──> Planning files persist!
                                 └──> Read all three files
                                       └──> Context recovered
```

## File Interaction Patterns

**task_plan.md:**
- Read: Before decisions, after errors, when resuming
- Write: After phases, when logging errors/decisions

**findings.md:**
- Read: Before technical decisions, when resuming
- Write: After 2-Action Rule, after research

**progress.md:**
- Read: When resuming sessions
- Write: After significant work, at session boundaries

## Key Principle

```
Context Window = Volatile RAM (64k-128k tokens)
Filesystem = Persistent Disk (unlimited)

→ Important information ALWAYS goes to disk
```

## Workflow Benefits

1. **No Context Loss** — Files survive context resets
2. **No Goal Drift** — Phases keep you on track
3. **No Repeated Errors** — Error table prevents repetition
4. **Easy Recovery** — 5-Question Reboot Check restores context
5. **Completion Verification** — /check-complete ensures done

---

See [Quick Start](quickstart.md) for hands-on walkthrough.
