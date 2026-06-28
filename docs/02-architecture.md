# Architecture

## Overview

Clowder is built around a persistent conductor, bounded performers, a policy engine, and an evidence-first local datastore.

```text
Operator
  -> CLI / Baton
  -> Engagement Policy
  -> Conductor
  -> Job Queue
  -> Performers
  -> SQLite + Evidence Workspace
  -> Reports
```

## Main components

### CLI / Baton

The operator interface. It loads engagement files, starts phases, reviews plans, grants approvals, and exports reports.

### Engagement policy

The policy layer enforces scope, phase ceiling, blocked actions, approval gates, and evidence handling rules.

### Conductor

The conductor is the planning and coordination layer. It reads engagement state, proposes phase plans, assigns bounded jobs, reviews results, and requests approvals.

### Performers

Performers are task-specific workers. Each performer receives a bounded job, verifies scope, runs an approved action, stores raw output, and writes normalized results.

### Critic

The critic reviews evidence and challenges findings before they become reportable. Its job is to reduce false positives and flag unsupported claims.

### SQLite engagement database

SQLite stores durable engagement state, jobs, approvals, observations, findings, evidence links, and report sections.

### Evidence workspace

The workspace stores raw artifacts such as tool output, request samples, screenshots, logs, and generated report material.

## Execution model

The preferred execution path is structured tool calls. Generated shell commands should require explicit human approval unless they are typed and run manually by the operator.

## Local LLM strategy

The LLM interface should support OpenAI-compatible local servers so the project can work with LM Studio, Ollama, vLLM, llama.cpp, or other compatible runtimes.

## Container strategy

Performers may run inside containers for isolation and repeatability. Chaining should happen through the database and evidence workspace, not through a shared uncontrolled shell.

## Design principle

The conductor suggests. Policy enforces. The operator approves escalation. The database records what happened.
