---
description: Verify all phases are complete before ending session
---

# Check Planning Completion

This command verifies that all phases in task_plan.md are complete before you end your session.

## Task

1. **Read task_plan.md**

2. **Check each phase:**
   - Count total phases
   - Count phases with status: "complete"
   - Count phases with status: "in_progress"
   - Count phases with status: "pending"
   - List any incomplete checkboxes

3. **Generate completion report:**

   If all phases are complete:
   ```
   ✅ ALL PHASES COMPLETE!

   - [N] phases all marked as complete
   - Goal achieved: [goal from task_plan.md]

   **Deliverables:**
   [List files created/modified from progress.md]

   Great work! This task is ready to close.
   ```

   If phases are incomplete:
   ```
   ⚠️ TASK NOT COMPLETE

   **Summary:**
   - ✅ [N] phases complete
   - 🔄 [N] phases in progress
   - ⏸️ [N] phases pending

   **Incomplete Phases:**
   [List phases with status != complete]

   **Unfinished checklist items:**
   [List any unchecked boxes]

   **Recommendation:**
   Continue working on Phase [X] or update task_plan.md if the plan has changed.

   Run /check-complete again when you think you're done.
   ```

4. **Suggest next actions:**
   - If complete: Suggest git commit, creating PR, or final review
   - If incomplete: Suggest which phase to focus on next
   - Remind about updating progress.md before closing session

## Edge Cases

- If task_plan.md doesn't exist, notify user and suggest running `/plan` first
- If phases are out of order (Phase 3 complete but Phase 2 not), flag this as unusual
- If no checkboxes are present, rely solely on status markers
