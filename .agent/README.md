# .agent

Supporting records for agent-assisted engineering.

These files are **not** always-on instructions. The root `CLAUDE.md` is the only default agent contract. Read material here only when the task needs it.

## Directories

- [`ADR/`](ADR/) — durable architectural or product-engineering decisions that should survive individual tasks.
- [`WORKLOG/`](WORKLOG/) — concise execution history for non-trivial work, handoff, debugging, or replay context.

## Information boundaries

- Current implementation truth belongs in code, tests, schemas, and configuration.
- Current task scope and acceptance criteria belong in issues or task contracts.
- Durable decisions belong in ADRs.
- Execution history belongs in worklogs.
- Do not treat worklogs as current truth.
- Do not create ADRs for routine implementation choices.

Keep this directory small. Add another durable artifact type only when the repository has a repeated need for it.