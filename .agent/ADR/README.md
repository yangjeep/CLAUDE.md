# Architectural Decision Records

Use an ADR for a durable decision that is expensive or risky to reverse, surprising to future maintainers, or defined by a meaningful trade-off.

Typical triggers include changes to:

- system boundaries or authoritative state;
- persistence or data ownership;
- authentication, authorization, or security model;
- external-provider strategy;
- major dependencies or infrastructure;
- architectural patterns that future work must preserve.

Do **not** write ADRs for routine implementation details.

## Naming

`NNN-kebab-case-title.md`

Example: `001-event-sourcing-over-crud.md`

## Lifecycle

Recommended statuses:

- `Proposed`
- `Accepted`
- `Superseded`
- `Rejected`

Accepted ADRs are historical records. Do not rewrite an accepted decision to make history match current reality. If the decision changes, create a new ADR and explicitly supersede the old one.

Use [`TEMPLATE.md`](TEMPLATE.md) for new records.