---
description: Guided workflow to update task_plan.md after completing work
---

# Update Planning File

This command helps you update task_plan.md in a structured way.

## Task

1. **Read current task_plan.md** to see current state

2. **Ask the user these questions:**

   a. "Which phase did you just complete or make progress on?"
      (Show them the current phases from task_plan.md)

   b. "What is the status of this phase?"
      - pending (not started)
      - in_progress (currently working)
      - complete (finished)

   c. "Did you encounter any errors?" (Yes/No)
      If yes: "Describe the error, attempt number, and how it was resolved (or if still unresolved)"

   d. "Did you make any important decisions?" (Yes/No)
      If yes: "What decision and what was the rationale?"

   e. "Any files created or modified?" (List them)

3. **Update task_plan.md:**
   - Update the relevant phase's status
   - Check off completed checkboxes in that phase
   - Add any errors to the "Errors Encountered" table
   - Add any decisions to the "Decisions Made" table
   - Update "Current Phase" if moving to next phase

4. **Update progress.md:**
   - Add entry to the relevant phase section
   - List actions taken
   - List files created/modified
   - Update timestamp

5. **Confirm with user:**
   ```
   ✅ Updated task_plan.md and progress.md

   - Phase [X] status: [status]
   - [N] checkboxes completed
   - [Errors/Decisions added if applicable]

   Current Phase: Phase [X]

   **Next:** [Suggest what to do next based on current phase]
   ```

## Reminders

- If a phase is marked "complete", remind user to read next phase before starting
- If approaching final phase, remind about `/check-complete` command
- If many errors logged, suggest the 3-Strike Protocol
