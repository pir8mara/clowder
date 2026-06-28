# Progressive Engagement Pipeline

Clowder is organized around a natural assessment progression. Each phase feeds evidence, context, and constraints into the next phase.

```text
OSINT Recon
  -> Deep Recon
  -> Security Posture Assessment
  -> Vulnerability Assessment
  -> Red-Team / Simulated Attacker
  -> Destructive Testing Pass
```

The phases are cumulative. They are not disconnected buttons. A user may stop at any phase, but later phases should reuse the structured output from earlier phases.

## Phase rules

Each phase defines:

- allowed actions
- blocked actions
- approval rules
- expected inputs
- expected outputs
- escalation criteria
- evidence requirements
- detection notes

## 1. OSINT Recon

Purpose: identify public exposure without active testing against target systems.

Typical outputs:

- domains and subdomains
- public IP hints
- public repos and metadata
- exposed brands, products, and subsidiaries
- technology hints
- candidate targets for validation

## 2. Deep Recon

Purpose: validate and expand discovered surface within the authorized scope.

Typical outputs:

- live hosts
- exposed services
- web and API surfaces
- DNS and certificate relationships
- framework and service fingerprints
- login portals and administrative surfaces

## 3. Security Posture Assessment

Purpose: evaluate configuration, hygiene, exposure, and obvious control failures.

Typical outputs:

- TLS and header issues
- risky service exposure
- weak authentication posture
- exposed admin interfaces
- default pages or sensitive files
- likely misconfiguration candidates

## 4. Vulnerability Assessment

Purpose: validate likely weaknesses, reduce scanner noise, and produce evidence-backed findings.

Typical outputs:

- confirmed findings
- false-positive notes
- affected assets
- reproduction summaries
- evidence links
- candidate attack paths

## 5. Red-Team / Simulated Attacker

Purpose: model realistic attacker behavior under explicit engagement rules.

Typical outputs:

- validated attack paths
- blocked paths and defensive control notes
- detection expectations
- timestamped activity timeline
- risk narrative

## 6. Destructive Testing Pass

Purpose: separately approved validation of risky or disruptive test cases.

This is not a discovery phase. It only uses previously documented paths that were selected and approved by the operator.

## Data lineage

Clowder should preserve this lineage:

```text
artifact -> observation -> hypothesis -> test -> evidence -> finding -> attack path -> report item
```

This lineage is the product. It makes results reviewable, repeatable, and auditable.
