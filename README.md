# AGENTS.md

A reusable project-level execution contract for coding agents.

## TL;DR

Use this repository as a GitHub template, fill in the **Project Contract** in [`AGENTS.md`](AGENTS.md), and start working.

`AGENTS.md` is agent-neutral. [`CLAUDE.md`](CLAUDE.md) is the Claude Code adapter and imports the same contract.

## Use it

1. Click **Use this template** on GitHub and create your repository.
2. Fill in the **Project Contract** in `AGENTS.md`:
   - mission;
   - authoritative architecture sources;
   - task/issue authority;
   - primary validation commands;
   - ADR location, if used;
   - worklog location, if used;
   - hard invariants.
3. Keep task-specific scope and acceptance criteria in issues or task contracts instead of growing the root instructions for every feature.
4. Remove `CLAUDE.md` if you do not use Claude Code.

## Design principles

- Repository truth first
- Smallest working change
- Test behavior first
- Small, coherent commits
- Durable decisions belong in ADRs
- Worklogs are history, not truth
- Evidence-backed completion

## Where information belongs

| Information | Preferred home |
| --- | --- |
| Durable agent behavior and recurring traps | `AGENTS.md` |
| Harness-specific adapter instructions | `CLAUDE.md` or equivalent |
| Product intent for a specific change | Issue / task contract |
| Acceptance criteria | Issue / task contract |
| Durable architecture decisions | ADRs / architecture docs |
| Execution history / cross-session handoff | Worklog, if the project uses one |
| Implementation truth | Code, tests, schemas, configuration |
| Local subsystem traps | Nested `AGENTS.md` |
| Current backlog / status | Issue tracker |

## Evolution

Do not add a root rule every time an agent makes a mistake.

```text
Agent makes a mistake
        ↓
Could repository inspection have answered it?
        ├─ yes → improve execution, tooling, tests, or discoverability
        └─ no
             ↓
Is the lesson non-obvious, repeated, and actionable?
        ├─ no → do not add an always-on rule
        └─ yes
             ↓
Can code, types, tests, lint, or CI enforce it deterministically?
        ├─ yes → encode it there
        └─ no → add the narrowest applicable agent rule
```

As a repository becomes easier for agents to understand and verify, its always-on contract should stay small or become smaller.

## License

MIT. Copy it, adapt it, and use it in personal, open-source, or commercial projects.
