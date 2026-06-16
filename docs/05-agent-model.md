# Agent Model

Clowder uses one persistent conductor and many bounded performers.

## Roles

- Conductor: plans phases, reviews results, requests approvals, and coordinates performers.
- Performers: execute bounded tool-specific jobs and write structured results.
- Critic: reviews evidence, challenges findings, and flags uncertainty.
- Reporter: drafts report sections from stored evidence.

## Memory model

The database is the memory. LLM context is temporary