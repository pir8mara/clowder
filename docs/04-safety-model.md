# Safety and Engagement Policy Model

Clowder requires an explicit engagement scope before meaningful assessment activity. The platform is intended for knowledgeable operators performing authorized security work.

## Core rules

- No scope, no assessment.
- No evidence, no finding.
- No mode authorization, no escalation.
- Destructive testing is never enabled by default.
- Social engineering is out of scope for v1.
- Activities that resemble persistence, evasion, or post-assessment control are excluded from v1 except as future explicitly governed research areas.

## Engagement controls

The engagement file defines:

- authorized targets
- explicit exclusions
- assessment phase ceiling
- active testing rules
- approval gates
- rate limits
- testing windows
- evidence retention
- report redaction requirements

## Approval gates

The operator must approve phase escalation when an action exceeds the current mode. Approval should be recorded before execution and linked to the resulting job.

Approval is required for:

- phase escalation into Red-Team / Simulated Attacker
- any destructive testing pass
- credential testing
- scope expansion
- unusually high traffic or disruptive testing
- any action marked risky by a performer or critic

## Mode ceilings

A run may stop at any phase. For example, an operator can run through Security Posture Assessment only, or run through Vulnerability Assessment while blocking Red-Team simulation.

The phase ceiling is a hard limit. The conductor may recommend escalation, but policy enforcement decides what is allowed.

## Public targets

Public internet targets are blocked unless they are explicitly listed in the engagement scope. A domain such as `demoncore.net` may be in scope when the operator has authority over it.

## Audit requirements

Every job should record:

- phase
- target
- tool or performer
- normalized action type
- timestamp
- approval state
- command or structured action summary
- raw output artifact reference
- resulting observations or findings

## Detection notes

Significant actions should produce detection notes for defensive correlation. The v1 goal is not SIEM integration. The v1 goal is a timestamped activity trail that defenders can compare against their own telemetry.
