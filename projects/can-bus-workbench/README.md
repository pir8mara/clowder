# CAN Bus Workbench

A local-first CAN/CAN FD reverse-engineering starter kit for laptop-based analysis.

This module is intended to live inside the broader `clowder` project as a self-contained project seed. It avoids vendor decoder lock-in by using open file formats, local logs, DBC files when available, and repeatable analysis notes.

## What this does

- Capture CAN frames from SocketCAN-compatible interfaces.
- Import existing `candump` text logs.
- Store captures as JSONL for easy scripting and LLM