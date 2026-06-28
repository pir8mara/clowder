# Clowder

Local-first AI-assisted offensive security workbench.

Clowder is an early-stage project for authorized security testing by knowledgeable operators. The goal is an open, auditable, privacy-preserving platform that coordinates offensive testing tools under explicit engagement scope and human supervision.

## Core idea

Clowder treats offensive security work as a progressive, evidence-backed engagement pipeline:

```text
OSINT Recon
  -> Deep Recon
  -> Security Posture Assessment
  -> Vulnerability Assessment
  -> Red-Team / Simulated Attacker
  -> Destructive Testing Pass
```

Each phase feeds structured evidence and context into the next phase. The operator controls the phase ceiling and approval gates.

## Design principles

- Local-first and privacy-preserving
- Open and auditable
- Scope-constrained by default
- Human-supervised autonomy
- Evidence-backed findings
- Repeatable engagement state
- Detection-aware offensive testing

## License and contributions

Clowder is licensed under AGPL-3.0-only.

Contributions use the Developer Certificate of Origin. No Contributor License Agreement is required, and no copyright assignment is required.

## Initial docs

- [Vision](docs/00-vision.md)
- [Product Requirements](docs/01-product-requirements.md)
- [Architecture](docs/02-architecture.md)
- [Engagement Pipeline](docs/03-engagement-pipeline.md)
- [Safety Model](docs/04-safety-model.md)
- [Agent Model](docs/05-agent-model.md)
- [Data Model](docs/06-data-model.md)
- [Roadmap](ROADMAP.md)

## Current status

This repository is in planning and architecture mode. Code will follow once the engagement model, safety model, and data model are coherent enough to build against.
