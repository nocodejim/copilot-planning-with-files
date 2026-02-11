# Frequently Asked Questions

## General

### Q: What is planning-with-files?

A: A methodology from Manus AI (acquired by Meta for $2B) that uses persistent markdown files as "working memory on disk" for AI agents.

### Q: Why three files instead of one?

A: Separation of concerns:
- task_plan.md = Roadmap (where you are, where you're going)
- findings.md = Knowledge base (what you've learned)
- progress.md = History (what you've done)

### Q: Do I need to use all three files?

A: Yes, for best results. Each file serves a specific purpose. Skipping one defeats the pattern.

## Setup & Installation

### Q: Do I need a plugin?

A: No! Just copy the .github/ folder into your project. Copilot auto-loads it.

### Q: Does this work with GitHub.com Copilot?

A: Partially. Custom instructions work, but slash commands require VS Code.

### Q: Can I use this without GitHub Copilot?

A: The planning files themselves work with any AI or even manually. But the instructions and commands are Copilot-specific.

### Q: Do I need Copilot Pro?

A: No. Works with any Copilot tier. Pro+ gets persistent memory bonus.

## Usage

### Q: When should I use planning files?

A: For tasks with 3+ steps, research, multi-file projects, or anything complex.

### Q: When should I NOT use planning files?

A: For simple questions, single-file edits, or quick lookups. Overkill for trivial tasks.

### Q: Do I create new planning files for every task?

A: Yes, each significant task gets its own set of three files. Or create a subdirectory structure.

### Q: Can I have multiple sets of planning files?

A: Yes! Organize by subdirectory:
```
my-project/
├── feature-a/
│   ├── task_plan.md
│   ├── findings.md
│   └── progress.md
└── feature-b/
    ├── task_plan.md
    ├── findings.md
    └── progress.md
```

### Q: How do I know when to update the files?

A: Guidelines:
- **task_plan.md**: After completing each phase
- **findings.md**: After every 2 view/browser/search operations (2-Action Rule)
- **progress.md**: After any significant work or errors

### Q: What if I forget to update the files?

A: Your context will drift and you'll lose progress. Build the habit like git commits.

## Copilot-Specific

### Q: Why doesn't Copilot automatically remind me like Cursor does?

A: Copilot has no hook system. Reminders are in instructions (passive), not triggered (active). Requires user discipline.

### Q: Can I force Copilot to re-read the planning files?

A: No automatic re-reading. You must:
1. Mention the file: "Based on task_plan.md, what should I do next?"
2. Use @workspace to include repository context
3. Just open the file (it's in your VS Code, Copilot sees it)

### Q: Will Agent Skills replace hooks?

A: Partially. Skills auto-load when relevant but can't *enforce* behavior like hooks can.

### Q: Can I add custom slash commands?

A: Yes! Add .md files to .github/prompts/ with frontmatter. See plan.prompt.md for example.

## Comparison

### Q: How is this different from the original planning-with-files?

A: Same core 3-file pattern. Differences:
- **Original**: Multi-IDE support, automated hooks, session recovery
- **Copilot**: Simpler setup, VS Code only, manual discipline

### Q: Should I use this or the original repository?

A: Use this if you use GitHub Copilot. Use original if you use Cursor, Claude Code, Continue, etc.

### Q: Can planning files be shared across IDEs?

A: Yes! The task_plan.md, findings.md, progress.md are IDE-agnostic. Only the .github/ configuration is Copilot-specific.

## Best Practices

### Q: How detailed should my phases be?

A: Break into 3-7 phases. Each phase should be completable in one session or less.

### Q: What goes in findings.md vs task_plan.md?

A:
- **findings.md**: Research results, resources, technical context
- **task_plan.md**: Phases, decisions, errors, progress tracking

### Q: Should I commit planning files to git?

A: Personal preference:
- **Commit**: Helps team understand context, useful for reviews
- **Ignore**: Temporary planning docs, personal workspace
- Suggested: Commit task_plan.md, ignore findings.md and progress.md

### Q: How do I handle errors?

A: Log EVERY error in task_plan.md's error table. Follow 3-Strike Protocol:
1. Attempt 1: Diagnose & fix
2. Attempt 2: Alternative approach
3. Attempt 3: Broader rethink
4. After 3: Escalate to user

## Troubleshooting

### Q: /plan command doesn't work

A: See [Troubleshooting Guide](troubleshooting.md#plan-command-not-working)

### Q: Copilot ignores my instructions

A: See [Troubleshooting Guide](troubleshooting.md#copilot-not-loading-instructions)

### Q: Context keeps resetting

A: See [Troubleshooting Guide](troubleshooting.md#context-reset-loses-my-progress)

## Philosophy

### Q: Why is filesystem better than context window?

A:
- Context window: 64k-128k tokens, auto-compacts, volatile
- Filesystem: Unlimited, permanent, searchable, shareable

### Q: What if I don't like this pattern?

A: That's okay! It's optimized for complex, multi-step tasks. For simple work, it's overkill. Use what works for you.

### Q: Is this just over-engineering?

A: For trivial tasks, yes. For complex projects, no. Manus built a $2B company on this pattern.

## Contributing

### Q: Can I contribute improvements?

A: Yes! See [CONTRIBUTING.md](../CONTRIBUTING.md) for guidelines.

### Q: Can I fork this for my own IDE?

A: Yes! MIT License. Please credit original authors and share improvements.

---

**More questions?** Open an issue on GitHub.
