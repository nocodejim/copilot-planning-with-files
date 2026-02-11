# Quick Start Guide

Get started with planning-with-files in 5 minutes.

## Prerequisites

- VS Code with GitHub Copilot extension
- GitHub Copilot subscription (or free trial)

## Step 1: Install Instructions (1 minute)

**Option A: Clone into your project**
```bash
cd your-project
git clone https://github.com/[username]/copilot-planning-with-files .github-planning
cp -r .github-planning/.github/* .github/
rm -rf .github-planning
```

**Option B: Manual copy**
Download the repository and copy the `.github/` folder into your project.

## Step 2: Reload VS Code (10 seconds)

Press **Cmd+R** (Mac) or **Ctrl+R** (Windows/Linux) to reload the window.

This loads `.github/copilot-instructions.md` into Copilot's context.

## Step 3: Start Planning (30 seconds)

Open Copilot Chat and type:

```
/plan "Build a CLI todo app with add, list, delete commands"
```

Copilot will create three files:
- ✅ task_plan.md
- ✅ findings.md
- ✅ progress.md

## Step 4: Read Your Plan (2 minutes)

Open `task_plan.md` and review:
- **Goal** — What you're building
- **Phases** — Broken down into steps
- **Current Phase** — Where to start

## Step 5: Start Working (Begin!)

Follow the phases in task_plan.md:

1. **Phase 1: Requirements & Discovery**
   - Research what you need
   - Document in findings.md

2. **Phase 2: Planning & Structure**
   - Design your approach
   - Update decisions in task_plan.md

3. **Continue through phases...**

### Updating Progress

When you complete a phase:
```
/update-plan
```

Copilot will guide you through updating task_plan.md and progress.md.

### Before Ending Session

```
/check-complete
```

Verifies all phases are done.

## Tips for Success

1. **Read Before Act** — Check task_plan.md before implementing
2. **Update After Act** — Mark phases complete, log errors
3. **The 2-Action Rule** — Save findings after 2 searches/views
4. **Log ALL Errors** — They prevent repetition
5. **Use Commands** — /plan, /update-plan, /check-complete

## Next Steps

- Read [Manus Principles](manus-principles.md) to understand *why* this works
- See [Workflow Diagram](workflow.md) for visual guide
- Browse [Examples](../examples/) for real-world usage
- Check [FAQ](faq.md) for common questions

---

**Stuck?** See [Troubleshooting](troubleshooting.md)
