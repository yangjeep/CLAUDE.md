# CLAUDE.md

A small template for repository-level coding-agent instructions and durable agent work records.

## TL;DR

Click **Use this template**, create your repository, then customize the **Project Contract** at the top of [`CLAUDE.md`](CLAUDE.md).

The template keeps one agent-facing file at the repository root and puts optional decision/history records under [`.agent/`](.agent/).

## Use it

1. Click **Use this template** on GitHub.
2. Fill in the **Project Contract** in [`CLAUDE.md`](CLAUDE.md): mission, architecture authority, task authority, validation commands, and hard invariants.
3. Keep task-specific scope and acceptance criteria in issues or task contracts.
4. Use [`.agent/ADR/`](.agent/ADR/) only for durable architectural decisions.
5. Use [`.agent/WORKLOG/`](.agent/WORKLOG/) for non-trivial execution history when handoff, debugging, or replay context is useful.
6. Delete unused templates if your repository does not need them.

## Template structure

```text
CLAUDE.md
.agent/
  README.md
  ADR/
    README.md
    TEMPLATE.md
  WORKLOG/
    README.md
    TEMPLATE.md
README.md
LICENSE
```

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
| Durable agent behavior and recurring traps | `CLAUDE.md` |
| Product intent / acceptance criteria for a change | Issue / task contract |
| Durable architecture decisions | `.agent/ADR/` |
| Execution history / cross-session handoff | `.agent/WORKLOG/` |
| Implementation truth | Code, tests, schemas, configuration |
| Current backlog / status | Issue tracker |

## Compatibility

Claude Code uses `CLAUDE.md` directly.

OpenCode's current rules documentation supports project `CLAUDE.md` as a fallback when no `AGENTS.md` exists. OpenCode V2 currently discovers only `AGENTS.md`; if you use that mode, copy or symlink `CLAUDE.md` to `AGENTS.md` for compatibility.

## Evolution

Do not add a root rule every time an agent makes a mistake. Prefer code, tests, types, lint, CI, or better repository discoverability when they can enforce the lesson deterministically.

Add an always-on rule only when the lesson is non-obvious, repeated or durably risky, and actionable.

## License

MIT. Copy it, adapt it, and use it in personal, open-source, or commercial projects.
