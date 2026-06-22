# Architecture

The workbench is deliberately simple. Start with repeatable capture and analysis before adding active testing.

```text
CAN/CAN FD adapter
  -> passive capture
  -> JSONL normalized frames
  -> optional DBC decode
  -> traffic report
  -> local LLM prompt pack
  -> human-validated hypotheses
```

## Components

- **Adapter layer:** hardware bridges the physical CAN bus to a laptop.
- **Capture layer:** `canwb capture` receives frames from SocketCAN and writes JSONL.
- **Import layer:** `canwb import-candump` converts existing `candump` logs.
- **Decode layer:** `canwb decode` applies a DBC file through `cantools`.
- **Report layer:** `canwb analyze` groups frames by arbitration ID and flags movement.
- **LLM layer:** `canwb prompt-pack` wraps the report in a conservative local-LLM analysis prompt.

## Why JSONL

JSONL is boring and useful. Each CAN frame is one line, so logs can be streamed, grepped, chunked, diffed, indexed, and fed to local models without ceremony.
