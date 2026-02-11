# Comparison: Copilot vs Other IDEs

## Planning-with-Files Across IDEs

| Feature | Copilot (This Repo) | Cursor/Claude Code | Notes |
|---------|-------------------|-------------------|-------|
| **Installation** | Copy .github/ folder | Plugin marketplace | Copilot: simpler |
| **Activation** | /plan command | /planning-with-files:plan | Similar UX |
| **Hook System** | ❌ None | ✅ PreToolUse, PostToolUse, Stop | Critical difference |
| **Automation Level** | ⚠️ Manual (user discipline) | ✅ Automated reminders | Hooks enforce behavior |
| **Template System** | ✅ .github/planning-templates/ | ✅ skill templates/ | Same approach |
| **Session Recovery** | ⚠️ Manual (re-read files) | ✅ Automated (session-catchup.py) | Script not possible in Copilot |
| **Agent Skill** | ✅ Auto-loads when files exist | ✅ Skills system | Similar capability |
| **Slash Commands** | ✅ /plan, /update-plan | ✅ /planning-with-files | Copilot: cleaner namespace |
| **Context Window** | 64k-128k tokens | Varies by IDE | Copilot auto-compacts at 95% |
| **Multi-IDE Support** | ❌ VS Code only | ✅ 14+ IDEs | Original supports many IDEs |

## Tradeoffs

### ✅ Copilot Advantages

1. **Simpler Setup** — No plugin required, just copy files
2. **VS Code Native** — Works in standard VS Code
3. **Clean Commands** — /plan vs /planning-with-files:plan
4. **GitHub Integration** — .github/ folder is standard convention

### ⚠️ Copilot Limitations

1. **No Hooks** — Can't automatically remind you to read/update files
2. **Manual Discipline** — You must remember to update planning files
3. **No Session Recovery** — No automated catchup after context reset
4. **Single IDE** — Only works in VS Code (Copilot only)

## When to Choose Each

**Choose Copilot version if:**
- You use GitHub Copilot in VS Code
- You prefer simple, no-plugin setup
- You're comfortable with manual discipline
- You want clean, native integration

**Choose original multi-IDE version if:**
- You use Cursor, Claude Code, Continue, etc.
- You want automated hooks to enforce planning
- You want session recovery features
- You work across multiple AI IDEs

## Can I Use Both?

Yes! The core 3-file pattern is identical. You can:
- Use Copilot version in VS Code projects
- Use Cursor version in Cursor IDE
- Planning files work the same in both

Just don't mix the instruction files in the same project.

## Migration

### From Cursor/Claude Code to Copilot

1. Keep your task_plan.md, findings.md, progress.md (unchanged)
2. Remove .cursor/ or skills/ folders
3. Add .github/ folder from this repo
4. Reload VS Code

### From Copilot to Cursor/Claude Code

1. Keep your planning files (unchanged)
2. Remove .github/copilot-* files
3. Install planning-with-files plugin/skill
4. Continue working

The planning files are portable!
