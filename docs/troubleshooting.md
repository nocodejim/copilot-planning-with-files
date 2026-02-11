# Troubleshooting

## Common Issues

### Copilot Not Loading Instructions

**Problem:** Instructions in .github/copilot-instructions.md aren't being used

**Solutions:**
1. Reload VS Code window (Cmd+R / Ctrl+R)
2. Check file is exactly `.github/copilot-instructions.md` (not .txt or other)
3. Ensure Copilot extension is enabled and logged in
4. Try closing and reopening VS Code completely

### /plan Command Not Working

**Problem:** Typing /plan in Copilot Chat does nothing

**Solutions:**
1. Check .github/prompts/plan.prompt.md exists
2. Ensure file has frontmatter (---description--- section)
3. Reload VS Code window
4. Try typing /plan and waiting a moment for autocomplete
5. Alternative: Use Copilot Chat and ask "Create planning files using the template system"

### Planning Files Not Auto-Loading Skill

**Problem:** Agent Skill not providing reminders even though files exist

**Solutions:**
1. Ensure files are named exactly: task_plan.md, findings.md, progress.md
2. Check .github/copilot-planning-skill/skill.md exists
3. Reload VS Code window
4. Note: Skills may take a moment to activate after files are created

### Copilot Doesn't Remind Me to Update Files

**Expected Behavior:** Copilot has no hooks, so reminders are passive (in instructions), not active.

**Workaround:**
1. Build the habit: read task_plan.md before decisions
2. Use /update-plan regularly to structure updates
3. Set a timer or calendar reminder to update files
4. Add "Update planning files" to your personal checklist

### Template Files Have Wrong Format

**Problem:** Created files don't match expected structure

**Solutions:**
1. Check .github/planning-templates/ has all three templates
2. Manually copy templates if /plan isn't working
3. Verify templates weren't modified accidentally
4. Re-download from repository if templates are corrupted

### Context Reset Loses My Progress

**Expected Behavior:** Copilot auto-compacts at 95% token limit

**Workaround:**
1. Planning files ARE your recovery mechanism
2. When resuming: Read all three files (task_plan.md, findings.md, progress.md)
3. Update progress.md with "Session resumed" entry
4. Use 5-Question Reboot Check in progress.md
5. Copilot Pro+ has persistent codebase memory (helps but not perfect)

### Too Much Manual Work Compared to Cursor

**Expected:** Copilot version requires more discipline than Cursor's automated hooks

**Perspective Shift:**
- Cursor: Training wheels (hooks enforce behavior)
- Copilot: You've learned to ride (self-discipline)
- Both get you to the same destination

**Tips:**
1. Use /plan, /update-plan, /check-complete religiously
2. Build muscle memory (like git commit habit)
3. Accept that manual discipline is the tradeoff for simpler setup

### Can't Find Planning Files

**Problem:** Created files but can't find them

**Check:**
1. Files should be in **project root** (not .github/)
2. Use VS Code file explorer (Cmd+Shift+E / Ctrl+Shift+E)
3. Search for "task_plan.md" in VS Code search
4. Check if /plan created them in a subdirectory

### Instructions Seem Outdated Mid-Session

**Known Limitation:** Instructions load once at session start, not re-read

**Workaround:**
1. If you update .github/copilot-instructions.md, reload window
2. For planning file updates, just re-open the file (Copilot can see it)
3. Don't need to reload for planning file changes

## Still Stuck?

1. Check [FAQ](faq.md) for more questions
2. Review [Examples](../examples/) to see correct usage
3. Open an issue on GitHub with details
4. Compare your files to the templates in .github/planning-templates/

## Reporting Bugs

When opening an issue, include:
- VS Code version
- Copilot extension version
- Steps to reproduce
- Expected vs actual behavior
- Relevant file contents (task_plan.md, etc.)
