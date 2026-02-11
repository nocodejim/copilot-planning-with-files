---
description: Initialize Manus-style planning files for a new task
---

# Initialize Planning Files

You are creating planning files for a new task using the Manus methodology.

## Input

The user has provided: ${input}

If no task description was provided, ask the user to describe their task.

## Task

1. **Check if planning files already exist:**
   - Look for task_plan.md, findings.md, progress.md in the project root
   - If they exist, warn the user and ask if they want to overwrite
   - If they say no, offer to append to existing files instead

2. **Copy templates from .github/planning-templates/:**
   - task_plan.md → Copy to project root
   - findings.md → Copy to project root
   - progress.md → Copy to project root

3. **Initialize task_plan.md:**
   - Replace `[Brief Description]` with the user's task description
   - Replace `[One sentence describing the end state]` with extracted goal
   - Update date placeholders with current date (YYYY-MM-DD format)
   - Keep all template structure and comments
   - Set "Current Phase" to "Phase 1"
   - Mark Phase 1 status as "in_progress"

4. **Initialize findings.md:**
   - Add user's task to Requirements section
   - Update date placeholders
   - Keep all template structure

5. **Initialize progress.md:**
   - Set session date to today
   - Update "Phase 1" entry with "Started: [current timestamp]"
   - Mark Phase 1 status as "in_progress"
   - Add initial entry: "Created planning files using /plan command"

6. **Guide the user:**
   - Explain the three files and their purposes
   - Suggest starting with Phase 1: Requirements & Discovery
   - Remind them about helpful commands: /update-plan, /check-complete
   - Encourage them to read the planning files before starting work

## Output

After creating the files, provide a brief summary:

```
✅ Planning files initialized!

Created:
- task_plan.md — Your roadmap and phase tracker
- findings.md — Research and discoveries storage
- progress.md — Session log and progress tracking

**Next steps:**
1. Review task_plan.md to understand the phases
2. Start with Phase 1: Requirements & Discovery
3. Use /update-plan when you complete a phase
4. Use /check-complete before ending your session

**Remember:** Read task_plan.md before making major decisions!
```

## Template Reference

Templates are in: `.github/planning-templates/`
Refer to the template files for exact structure.
