# AGENTS.md

A reusable project-level execution contract for coding agents.

This repository contains a deliberately small pair of files:

- [`AGENTS.md`](AGENTS.md) — the agent-neutral execution contract.
- [`CLAUDE.md`](CLAUDE.md) — a thin Claude Code adapter that imports the same contract.

The goal is not to document an entire codebase for an agent. The goal is to give an agent the minimum durable context needed to execute safely and autonomously, then let it inspect repository truth just in time.

## Use it

Copy `AGENTS.md` into the root of a project and fill in its **Project Contract** section:

- mission;
- authoritative architecture sources;
- task/issue authority;
- primary validation commands;
- a short list of hard invariants.

If the project uses Claude Code, copy `CLAUDE.md` as well.

Then keep task-specific requirements in issues or other task contracts rather than growing the root instructions for every new feature.

## Design principles

### Execution, not plan theater

Once implementation has been authorized, routine engineering decisions, repository inspection, testing, debugging, CI repair, and permitted delivery actions should proceed without repeatedly asking the human to continue.

Human input is reserved for genuine product ambiguity, architecture changes, meaningful data/migration risk, security-risk acceptance, unavailable external capabilities, irreversible production actions, or materially different valid outcomes.

### Traps, not maps

Always-on rules should capture durable, non-obvious failure modes. Architecture descriptions, module maps, API references, current status, and implementation history belong elsewhere because agents can inspect them when needed and those descriptions go stale quickly.

A new root rule should normally be:

1. non-obvious;
2. repeatedly encountered or durably risky;
3. specific enough to change behavior.

### Repository truth first

Agents should inspect code, tests, configuration, and recent repository history before making claims about implementation details. Instructions should define boundaries and authority, not replace repository discovery.

### Smallest working change

Prefer focused diffs, existing patterns, and one problem per change. Avoid speculative abstractions, unrelated cleanup, unnecessary dependencies, and architecture expansion.

### Evidence-backed completion

A task is complete because required behavior was implemented and verified, not because an agent says it is done. Test, build, commit, PR, merge, and deployment claims should correspond to operations that actually succeeded.

## Where information belongs

| Information | Preferred home |
| --- | --- |
| Durable agent behavior and recurring traps | `AGENTS.md` |
| Harness-specific adapter instructions | `CLAUDE.md` or equivalent |
| Product intent for a specific change | Issue / task contract |
| Acceptance criteria | Issue / task contract |
| Durable architecture decisions | ADRs / architecture docs |
| Implementation truth | Code, tests, schemas, configuration |
| Local subsystem traps | Nested `AGENTS.md` |
| Current backlog / status | Issue tracker |

## Evolution

Do not automatically add a rule every time an agent makes a mistake.

Use this filter:

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

The best long-term outcome is not an ever-growing instruction file. As a repository becomes easier for agents to understand and verify, its always-on contract should stay small or become smaller.

## License

MIT. Copy it, adapt it, and use it in personal, open-source, or commercial projects.
