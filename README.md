# claude-plugins

> **Note:** This plugin is currently in daily use and in active development/testing. The interface, agent prompts, and workflow structure may change before a 1.0.0 release. Use with that in mind.

A Claude Code plugin that implements an end-to-end AI dev loop, orchestrating a team of specialised agents through a structured plan → implement → review → document cycle.

## What it does

Running `/chrismou-claude-plugins:project-manager <task description>` spins up a coordinated pipeline of agents:

1. **Architect** — analyses your codebase, writes a technical design doc to `plans/YYYYMMDD-slug.md`, then pauses so you can review and edit it before anything is touched.
2. **Coder** — executes the plan precisely: creates/modifies files, runs syntax checks, and self-corrects minor blockers.
3. **QA** — reviews the implementation for bugs, edge cases, missing error handling, and test coverage gaps. If it finds issues, it sends work back to the Coder.
4. **Reviewer** — audits for security issues, performance problems, and style consistency. Loops back to the Coder if changes are required.
5. **Documenter** — updates `README.md`, docstrings, and `CHANGELOG.md` to reflect the changes made.

There are two human checkpoints built in:

- After planning, so you can review and tweak the design doc before code is written.
- After review, so you can accept the result or request changes.

Plan files are never deleted — they're kept in `plans/` for audit and version history.

## Requirements

- [Claude Code](https://claude.ai/code) with plugin support enabled

## Installation

### Option A: Install from GitHub

```bash
claude plugin marketplace add chrismou/claude-plugins
claude plugin install chrismou-claude-plugins@chrismou-claude-plugins
```

### Option B: Install from source

```bash
git clone https://github.com/chrismou/claude-plugins
claude plugin install ./claude-plugins/project-manager
```

## Usage

From within any Claude Code session in your project:

```
/chrismou-claude-plugins:project-manager <description of your task>
```

**Example:**

```
/chrismou-claude-plugins:project-manager Add rate limiting to the public API endpoints
```

### What to expect

1. The Architect analyses your project and writes a plan. You'll see the plan path printed.
2. Open the plan file, review it, make any edits you want.
3. Type `GO` to kick off implementation.
4. The Coder, QA, and Reviewer agents run in sequence (looping back as needed).
5. You'll be asked to confirm the final result. Type `Yes` to proceed to documentation, or `No` to provide feedback and restart the loop.

## Agents

| Agent      | Model             | Role                                          |
| ---------- | ----------------- | --------------------------------------------- |
| architect  | claude-sonnet-4-6 | Writes technical design docs, no code changes |
| coder      | claude-sonnet-4-6 | Implements the plan                           |
| qa-tester  | claude-sonnet-4-6 | Tests for bugs, edge cases, coverage gaps     |
| reviewer   | claude-sonnet-4-6 | Security, performance, and style audit        |
| documenter | claude-haiku-4-5  | Updates docs and CHANGELOG                    |

## Project structure

```
.
├── .claude-plugin/
│   └── marketplace.json
├── project-manager/
│   ├── agents/
│   │   ├── architect.md
│   │   ├── coder.md
│   │   ├── qa.md
│   │   ├── reviewer.md
│   │   └── documenter.md
│   ├── commands/
│   │   └── project-manager.md
│   └── plugin.json
└── README.md
```

## License

MIT
