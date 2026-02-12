# Evaluation Prompt: Copilot Planning-with-Files

> **Purpose:** Give this prompt to any AI agent (Copilot, Claude, Gemini, etc.) to get an independent evaluation of this repository and recommendations for deeper GitHub Copilot integration.

---

## Instructions for the Agent

You are evaluating the **copilot-planning-with-files** repository. This repo implements a "3-file planning pattern" (task_plan.md, findings.md, progress.md) adapted for GitHub Copilot in VS Code. It was inspired by Manus AI's context engineering methodology.

Perform the following evaluation steps. Write your findings to a new file called `evaluation-results.md` in the project root.

---

### Step 1: Understand the Repository

Read these files in order to understand the full scope:

1. `README.md` — Overview and quick start
2. `.github/copilot-instructions.md` — Core AI instructions
3. `.github/copilot-planning-skill/skill.md` — Agent Skill definition
4. `docs/manus-principles.md` — The underlying methodology
5. `docs/comparison.md` — How this compares to Cursor/Claude Code versions
6. `docs/workflow.md` — The intended workflow
7. At least one example in `examples/`

### Step 2: Evaluate Current Implementation

Assess the repository against these criteria. Rate each 1-5 (1=poor, 5=excellent):

| Criteria | Rating | Notes |
|----------|--------|-------|
| **Clarity** — Can a new user understand and use this in under 10 minutes? | | |
| **Completeness** — Are all necessary files, templates, and docs present? | | |
| **Copilot Integration** — Does this leverage Copilot's features effectively? | | |
| **Practical Value** — Would this actually improve a developer's workflow? | | |
| **Manus Fidelity** — Does this faithfully preserve the core methodology? | | |
| **Gap vs Hooks** — How well does it compensate for Copilot's lack of hooks? | | |

### Step 3: Research Current GitHub Copilot Capabilities

Research the **latest** GitHub Copilot features and capabilities. Specifically investigate:

1. **Has Copilot added any hook or event system since early 2026?** (PreToolUse, PostToolUse, etc.)
2. **What is the current state of Agent Skills?** Have they gained new capabilities (auto-triggering, memory, state)?
3. **Has Copilot introduced persistent memory or session continuity features?** (Beyond Pro+ codebase memory)
4. **What new prompt file capabilities exist?** (Variables, chaining, conditional logic?)
5. **Are there new MCP (Model Context Protocol) integrations** that could replace or enhance the 3-file pattern?
6. **Has the Copilot context window changed?** (Size, compaction behavior, manual controls?)
7. **Are there new Copilot CLI features** that could support automated planning file management?
8. **Custom Agents** — Can custom agents now enforce behaviors that would replicate hooks?

### Step 4: Identify Integration Opportunities

Based on your research, answer:

1. **Can any new Copilot features close the "hook gap"?** — The biggest weakness is that Copilot can't automatically enforce reading/updating planning files. Has anything changed?
2. **Can MCP servers provide persistent state?** — Could an MCP server track planning file freshness and prompt the user?
3. **Can custom agents enforce planning discipline?** — Could a "Planning Agent" profile automatically read planning files before responding?
4. **Is there a better file structure?** — Given current Copilot conventions, should `.github/` organization change?
5. **Can VS Code tasks or extensions help?** — Would a simple VS Code task definition or workspace setting enhance the workflow?
6. **Is the 3-file pattern still optimal?** — Or has the ecosystem evolved to support something better (e.g., embedded metadata, frontmatter-driven context)?

### Step 5: Propose Improvements

Provide concrete, actionable recommendations in three tiers:

#### Quick Wins (< 1 hour to implement)
- Changes to existing files that improve integration or clarity

#### Medium Effort (1-4 hours)
- New files, restructured workflows, or new slash commands

#### Ambitious (research + implementation needed)
- MCP integrations, custom agents, VS Code extension concepts

### Step 6: Write Your Verdict

Summarize with:

1. **Overall Score** (1-10) for the current implementation
2. **Biggest Strength** of this approach
3. **Biggest Weakness** that should be addressed
4. **Is the 3-file pattern still the right approach for Copilot?** (Yes/No/It Depends — and why)
5. **Top 3 recommendations** ordered by impact

---

## Expected Output

Create `evaluation-results.md` with:
- All ratings from Step 2
- Research findings from Step 3
- Answers to Step 4 questions
- Tiered recommendations from Step 5
- Final verdict from Step 6

**Be honest and critical.** The goal is to make this repository better, not to validate it.
