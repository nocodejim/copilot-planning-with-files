---
description: Manus-style file-based planning for complex tasks. Auto-activates when task_plan.md, findings.md, or progress.md exist in workspace.
applyTo: "**/{task_plan,findings,progress}.md"
---

# Planning with Files - Agent Skill

This skill automatically activates when planning files exist in your workspace.

## Detection

This skill loads when ANY of these files exist:
- task_plan.md
- findings.md
- progress.md

## Enhanced Guidance

When planning files are present, you should:

### Before Any Major Action

1. **Check task_plan.md:**
   - What phase are you in?
   - What's the current goal?
   - Any errors logged from previous attempts?

2. **Check findings.md:**
   - What have you already discovered?
   - What decisions were made and why?
   - Any resources or references to use?

3. **Check progress.md:**
   - What was done in the last session?
   - Any incomplete actions?
   - What's the last known good state?

### After Completing Work

Update the appropriate file:

- **task_plan.md**: Mark phases complete, log errors, update decisions
- **findings.md**: Add research discoveries, document technical choices
- **progress.md**: Log what you did, files modified, test results

### Automatic Reminders

When you're about to:
- Implement a feature → Re-read task_plan.md current phase
- Make an architectural decision → Check findings.md for past decisions
- Debug an error → Check task_plan.md error log to avoid repetition
- Complete a task → Run `/check-complete` to verify all phases done

### Session Continuity

If this appears to be a new session (progress.md hasn't been updated recently):
1. Suggest reading all three planning files
2. Ask user if they want to update progress.md with session start
3. Reference the 5-Question Reboot Check in progress.md

## Integration with Core Instructions

This skill works alongside `.github/copilot-instructions.md`. Core instructions are always active; this skill provides additional context-aware guidance when planning files exist.

See [instructions.md](instructions.md) for detailed workflow and [examples.md](examples.md) for real-world examples.
