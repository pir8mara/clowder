# Product Requirements

## Product thesis

Clowder is a local-first, open, auditable offensive security workbench for experienced security testers. It coordinates assessment tools, preserves evidence, and produces repeatable findings without sending client data to a third-party service.

## Target users

- internal red teams
- product security teams
- enterprise security teams
- security consultants working under authorization

## Primary goals

- run locally by default
- protect client privacy
- require explicit engagement scope
- support human-supervised autonomy
- normalize tool output into evidence-backed findings
- preserve repeatable engagement state
- produce useful technical reports
- support detection-aware offensive testing

## Non-goals for v1

- unmanaged autonomous testing
- social engineering
- public target testing without explicit authorization
- persistence or stealth behavior
- general-purpose post-assessment control
- replacing knowledgeable security testers
- becoming a scanner dashboard with an AI summary bolted on

## V1 scope

V1 focuses on:

- engagement scope file
- progressive engagement pipeline
- local LLM orchestration
- CLI operation
- SQLite-backed state
- recon and web/API assessment flow
- evidence storage
- raw technical reports
- detection-correlation timeline

## V1 outputs

- executive summary draft
- technical findings
- evidence appendix
- raw JSON export
- activity timeline for defensive correlation

## Success criteria

A successful v1 can take an authorized target or target set, apply policy constraints, run bounded assessment phases, store evidence, deduplicate observations, and generate a report where every finding links back to supporting evidence.
