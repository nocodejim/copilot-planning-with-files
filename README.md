# Copilot Planning with Files

> **Work like Manus** — The AI agent company Meta acquired for $2 billion.

Use persistent markdown files for planning, progress tracking, and knowledge storage in GitHub Copilot.

[![VS Code](https://img.shields.io/badge/VS%20Code-Copilot-blue)](https://code.visualstudio.com/docs/copilot)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## Quick Start

1. **Clone this repository into your project:**
   ```bash
   git clone https://github.com/nocodejim/copilot-planning-with-files .github-planning
   cp -r .github-planning/.github/* .github/
   rm -rf .github-planning
   ```

2. **Reload VS Code window** (Cmd+R or Ctrl+R) to load instructions

3. **Start planning:**
   ```
   /plan "Build a todo CLI app"
   ```

That's it! Copilot will create `task_plan.md`, `findings.md`, and `progress.md`.

## Why This Pattern?

On December 29, 2025, Meta acquired Manus for $2 billion. Their secret? **Context engineering**.

> "Markdown is my 'working memory' on disk. Since my context has limits, Markdown files serve as checkpoints for progress."
> — Manus AI

### The Problem

GitHub Copilot (like most AI) suffers from:
- **Volatile memory** — Context resets, goals forgotten
- **Goal drift** — After long sessions, original goals get lost
- **Hidden errors** — Failures aren't tracked, same mistakes repeat
- **Context limits** — 64k-128k tokens, then auto-compaction

### The Solution: 3-File Pattern

For every complex task, create THREE files:

```
task_plan.md      → Track phases and progress
findings.md       → Store research and findings
progress.md       → Session log and test results
```

**Core Principle:**
```
Context Window = RAM (volatile, limited)
Filesystem = Disk (persistent, unlimited)

→ Anything important gets written to disk.
```

## Features

- ✅ **Auto-loaded instructions** (.github/copilot-instructions.md)
- ✅ **Agent Skill** for context-aware reminders
- ✅ **Slash commands** (/plan, /update-plan, /check-complete)
- ✅ **Template system** for quick initialization
- ✅ **Manus principles** adapted for Copilot
- ✅ **VS Code native** (no plugins required)

## Usage

### Starting a Task

```
/plan "Your task description"
```

This creates the three planning files and guides you through Phase 1.

### During Work

- **Before decisions:** Read task_plan.md
- **After discoveries:** Update findings.md
- **After actions:** Update progress.md
- **Phase complete:** Run /update-plan

### Ending Session

```
/check-complete
```

Verifies all phases complete before you close.

## The Manus Principles

| Principle | Implementation |
|-----------|----------------|
| Filesystem as memory | Store in files, not context |
| Attention manipulation | Explicit reminders in instructions |
| Error persistence | Log failures in task_plan.md |
| Goal tracking | Checkboxes show progress |
| Completion verification | /check-complete command |

## Documentation

- [Quick Start Guide](docs/quickstart.md) — 5-step walkthrough
- [Workflow Diagram](docs/workflow.md) — Visual guide
- [Manus Principles](docs/manus-principles.md) — Deep dive
- [Comparison](docs/comparison.md) — vs Cursor, Claude Code, etc.
- [FAQ](docs/faq.md) — Common questions
- [Troubleshooting](docs/troubleshooting.md) — Common issues

## When to Use

**Use for:**
- Multi-step tasks (3+ steps)
- Research tasks
- Building/creating projects
- Tasks spanning many tool calls

**Skip for:**
- Simple questions
- Single-file edits
- Quick lookups

## Examples

See [examples/](examples/) for complete examples:
- [Simple Task](examples/simple-task/) — Building a CLI todo app
- [Complex Project](examples/complex-project/) — Multi-feature application

## Comparison with Other IDEs

This is the **GitHub Copilot** version. For other IDEs:

| IDE | Repository |
|-----|------------|
| Claude Code, Cursor, Continue, etc. | [planning-with-files](https://github.com/OthmanAdi/planning-with-files) |
| GitHub Copilot | ⬅️ **You are here** |

**Key Differences:**
- ✅ Copilot: Simple setup, VS Code native, no plugins
- ⚠️ Copilot: Manual discipline (no automated hooks)
- ✅ Other IDEs: Automated hooks enforce behavior
- ⚠️ Other IDEs: Require plugin/skill installation

See [docs/comparison.md](docs/comparison.md) for detailed comparison.

## Contributing

Contributions welcome! See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

MIT License — feel free to use, modify, and distribute.

## Acknowledgments

- **Manus AI** — For pioneering context engineering patterns
- **OthmanAdi** — Original planning-with-files for multi-IDE support
- **GitHub** — For Copilot and extensible instruction system
- **Lance Martin** — Detailed Manus architecture analysis

---

**Author:** nocodejim
**Original Pattern:** Based on [planning-with-files](https://github.com/OthmanAdi/planning-with-files) by OthmanAdi
