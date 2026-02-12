# Using MCP with Planning Files

GitHub Copilot supports the **Model Context Protocol (MCP)**, allowing it to connect to external tools (databases, web search, custom scripts).

This document explains how to integrate MCP tools into the "Planning with Files" workflow.

## The Workflow

1.  **Plan**: Create your `task_plan.md` as usual.
2.  **Act**: Use MCP tools to perform actions (e.g., query a database, search the web).
3.  **Log**: **CRITICAL STEP**. MCP tools often return large amounts of data. You must **summarize** the key findings into `findings.md`.

### Why Log MCP Results?

Copilot's context window is limited. If you use an MCP tool to fetch 50 rows from a database, that data is in the *immediate* context but will eventually be compacted or lost.

**Rule:** If an MCP tool returns information that shapes a decision, write that information to `findings.md`.

## Example

**Bad Workflow:**
- User: "Query the users table for active users."
- Copilot (MCP): *Fetches 100 users.*
- User: "Okay, now implementing the billing feature..."
- *...10 minutes later...*
- Copilot: "I forgot which users were active."

**Good Workflow:**
- User: "Query the users table for active users."
- Copilot (MCP): *Fetches 100 users.*
- User: "Log the count and the schema structure to findings.md".
- Copilot: *Updates findings.md:*
  ```markdown
  ## Research
  - **User Data**: Found 100 active users. Schema includes `last_login` and `subscription_status`.
  ```

## Recommended MCP Servers

-   **Filesystem**: Default in many agents, but our `task_plan.md` is better for high-level tracking.
-   **PostgreSQL/SQLite**: For inspecting database state.
-   **Web Search**: For researching libraries. *Always log URLs and key facts to findings.md*.
