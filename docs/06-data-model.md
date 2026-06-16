# Data Model

Clowder's core data model is evidence-first.

## Primary entities

- Engagement
- Scope
- Target
- Phase
- Job
- Tool run
- Artifact
- Observation
- Finding
- Evidence link
- Approval
- Attack path
- Report section

## Lineage

Clowder should preserve this lineage:

```text
artifact -> observation -> hypothesis -> test -> evidence -> finding -> attack path -> report item
```

## Storage

SQLite is the preferred v1 storage layer because it is local, inspectable, portable