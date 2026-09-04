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
- ADR location, if the project uses ADRs;
- worklog location, if the project uses an agent worklog;
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

Before changing behavior, establish a green baseline with the narrowest relevant existing tests when practical. A failing check should not be dismissed as "pre-existing" without evidence.

### Smallest working change

Prefer focused diffs, existing patterns, and one problem per change. Avoid speculative abstractions, unrelated cleanup, unnecessary dependencies, and architecture expansion.

### Test behavior, then implement

For bugs and deterministic behavior changes, prefer a RED → GREEN → REFACTOR loop:

1. reproduce the missing or broken behavior with a focused failing test;
2. confirm the failure is for the expected reason;
3. make the smallest implementation change that passes;
4. refactor only while staying green.

The contract intentionally stops short of demanding mechanical TDD for every possible file type. When RED-first testing is genuinely impractical, the agent should explain the gap and provide the best available regression evidence.

### Small, coherent commits

Prefer logical commits that are independently understandable and reviewable over one large implementation dump.

A good commit represents one coherent change, carries the tests required for that change, and leaves the repository valid when practical. Mechanical moves and behavior changes should be separated when that makes review easier.

Small does not mean noisy: checkpoint commits such as `fix tests`, `fix lint`, or `finish implementation` are not useful history when those fixes belong in the logical commit that introduced the change.

### Decisions are different from history

Use ADRs for durable decisions that are expensive to reverse, surprising, or defined by meaningful architectural trade-offs. Accepted decisions are historical records; supersede or amend them instead of silently rewriting the past.

Use worklogs, when a repository has them, for execution history and cross-session handoff. A worklog is not authoritative architecture or product truth. Promote durable decisions into ADRs and current facts into their canonical source.

### Evidence-backed completion

A task is complete because required behavior was implemented and verified, not because an agent says it is done. Test, build, commit, PR, merge, and deployment claims should correspond to operations that actually succeeded.

Before delivery, the agent should re-read the original task, review the final diff as a reviewer, remove scope drift and unnecessary abstraction, and confirm every claimed behavior has evidence.

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
