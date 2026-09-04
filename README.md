# AGENTS.md

A reusable project-level execution contract for coding agents.

## TL;DR

Copy [`AGENTS.md`](AGENTS.md) into your project, fill in the **Project Contract**, and let coding agents work from repository truth instead of an ever-growing prompt.

If you use Claude Code, copy [`CLAUDE.md`](CLAUDE.md) too. It imports the same contract.

The default workflow is simple: inspect first, establish a baseline, test behavior, make the smallest working change, commit coherent slices, record durable decisions when needed, and verify before declaring done.

## Use it

1. Copy [`AGENTS.md`](AGENTS.md) to the root of your repository.
2. Fill in the **Project Contract**:
   - mission;
   - authoritative architecture sources;
   - task/issue authority;
   - primary validation commands;
   - ADR location, if used;
   - worklog location, if used;
   - a short list of hard invariants.
3. If you use Claude Code, copy [`CLAUDE.md`](CLAUDE.md) as well.
4. Keep task-specific scope and acceptance criteria in issues or task contracts instead of growing the root instructions for every feature.

## Design principles

### Repository truth first

### Smallest working change

### Test behavior first

### Small, coherent commits

### Durable decisions belong in ADRs

### Worklogs are history, not truth

### Evidence-backed completion

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
