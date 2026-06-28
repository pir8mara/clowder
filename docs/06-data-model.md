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
- Hypothesis
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

A finding should not exist as a free-floating claim. It should link back to the evidence and jobs that produced it.

## Engagement

An engagement records the authorized work package. It should include scope, mode ceiling, authorization notes, contacts, testing windows, and evidence rules.

## Job

A job records a bounded unit of work assigned to a performer. It should include phase, target, approval state, start time, finish time, performer, input, output, and error state.

## Artifact

An artifact is raw or derived evidence. Examples include tool output, request and response samples, screenshots, logs, normalized JSON, and report extracts.

## Finding

A finding is a validated security issue linked to evidence. It may include severity, affected assets, reproduction summary, remediation guidance, and framework mappings.

## Attack path

An attack path links multiple observations or findings into a realistic scenario. It should include assumptions, blockers, approvals, and detection expectations.

## Storage

SQLite is the preferred v1 storage layer because it is local, inspectable, portable, easy to back up, and easy to audit.

## Framework mappings

Framework mappings should be metadata, not the finding itself. Initial mappings may include CWE, CVE, CVSS, OWASP, NIST SP 800-53, NIST CSF, and MITRE ATT&CK where applicable.
