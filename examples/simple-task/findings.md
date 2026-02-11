# Findings: CLI Todo App

## Requirements

### Core Requirements
- Add todos with description
- List all todos
- Delete todos by ID
- Persist data between sessions

## Research & Discoveries

### CLI Libraries

**Commander.js** — CHOSEN
- Clean, declarative API
- Wide adoption (26k+ GitHub stars)
- Good TypeScript support
- Example:
```js
program
  .command('add <task>')
  .description('Add a new task')
  .action(addTask);
```

**Yargs** — Considered
- More features (positional args, advanced parsing)
- More complex setup
- Overkill for simple 3-command CLI

### Storage Options

**JSON File** — CHOSEN
- Simple read/write with fs.readFile/writeFile
- Human-readable
- No dependencies
- Perfect for <1000 items
- Location: ~/.todos.json

**SQLite** — Rejected
- Overkill for simple list
- Adds dependency
- More complex queries
- Only worth it for >10k items or relationships

## Technical Decisions

### Data Structure
```js
[
  {id: 1, task: "Buy milk", created: "2026-02-10"},
  {id: 2, task: "Write code", created: "2026-02-11"}
]
```

Simple array of objects, ID auto-increments

### Command Interface
```
todo add "task description"
todo list
todo delete <id>
```

Standard CLI patterns, intuitive

## Resources
- [Commander.js docs](https://github.com/tj/commander.js)
- [Node.js fs module](https://nodejs.org/api/fs.html)
