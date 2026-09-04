# Worklog

Worklogs are an **agent-facing execution trail**, not a source of current product or architecture truth.

Use a worklog for non-trivial work when it improves:

- cross-session handoff;
- debugging or incident reconstruction;
- long-running issue execution;
- auditability of important verification or trade-offs;
- replay context for a future agent.

Trivial edits do not need a worklog.

## Naming

`YYYY-MM-DD-<slug>.md`

## Rules

1. Keep entries concise and evidence-oriented.
2. Record what changed, why, verification performed, and unresolved limitations.
3. Do not copy the entire issue, diff, or test output into the worklog.
4. Worklogs are append-only once the task is complete; correct current truth elsewhere.
5. Promote durable decisions to `.agent/ADR/` or canonical documentation.
6. Put current implementation truth in code, tests, schemas, and configuration.
7. Put current task status and acceptance criteria in the issue or task contract.

Use [`TEMPLATE.md`](TEMPLATE.md) for new entries.