# Agent Model

Clowder uses one persistent conductor and many bounded performers.

## Core idea

The conductor plans, reviews, and coordinates. Performers execute bounded jobs and write structured results. The database is the durable memory.

## Roles

- Conductor: plans phases, reviews results, requests approvals, and coordinates performers.
- Performers: execute bounded tool-specific jobs and write structured results.
- Critic: reviews evidence, challenges findings, and flags uncertainty.
- Reporter: drafts report sections from stored evidence.

## Memory model

The database is the memory. LLM context is temporary.

Persistent model memory is not required for v1. Chaining should come from stored engagement state, not from the model remembering a conversation.

## Conductor duties

The conductor should:

- read the engagement file
- respect the current phase ceiling
- create phase plans
- assign bounded jobs
- summarize results
- identify candidate next steps
- ask for approval when policy requires it
- explain uncertainty

## Performer duties

Performers should:

- accept structured job input
- verify target scope before execution
- run one bounded task
- store raw artifacts
- normalize observations
- report errors clearly

## Critic duties

The critic should:

- challenge unsupported findings
- flag weak evidence
- identify likely false positives
- check whether a finding has enough proof for reporting
- mark hallucination risk when a claim depends on model inference

## Tool execution

Structured tool calls are preferred. Generated shell commands should be treated as a manual or explicitly approved path, not the default execution path.

## Design principle

The model may suggest. Policy decides. The operator approves escalation. The database records what happened.
