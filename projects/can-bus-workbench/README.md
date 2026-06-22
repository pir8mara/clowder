# CAN Bus Workbench

Local-first CAN/CAN FD reverse-engineering starter kit for laptop-based analysis.

This module avoids vendor decoder lock-in by using open capture formats, optional DBC files, repeatable reports, and local LLM prompt packs.

## Features

- Passive SocketCAN capture to JSONL.
- Import existing `candump` text logs.
- Decode captures with DBC files using `cantools`.
- Generate Markdown traffic reports by arbitration ID.
- Generate local-LLM prompt packs for hypothesis review.
- Start with a listen-first safety posture. No general transmit command in v0.1.

## Quick start

```bash
cd projects/can-bus-workbench
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
pip install -e .
```

Analyze the included sample:

```bash
canwb import-candump examples/sample_candump.log --output examples/sample_capture.jsonl
canwb analyze examples/sample_capture.jsonl --output examples/sample_report.md
canwb prompt-pack examples/sample_report.md --output examples/sample_prompt_pack.md
```

Decode with a DBC file:

```bash
canwb decode examples/sample_capture.jsonl --dbc examples/sample_vehicle.dbc --output decoded.csv
```

Capture from SocketCAN:

```bash
sudo ip link set can0 up type can bitrate 500000
canwb capture --channel can0 --output logs/capture.jsonl --duration 30
```

## Hardware tiers

| Tier | Examples | Notes |
|---|---|---|
| Low-cost lab | CANable 2.0, MKS CANable, ODrive USB-CAN | Fine for bench learning. Be cautious around expensive systems. |
| Safer hobby/prototype | Isolated CANable Pro, Entrée V2, isolated USB-CAN FD adapters | Better for real devices and CAN FD experiments. |
| Professional | PEAK PCAN-USB FD, Kvaser Leaf, Intrepid ValueCAN | Better drivers, isolation, timestamping, support, and fewer clone adventures. |

## Workflow

```text
CAN interface
  -> passive capture
  -> open JSONL log
  -> optional DBC decode
  -> traffic report
  -> human notes
  -> local LLM prompt pack
  -> validated reverse-engineering hypotheses
```

The adapter is just the door. The real project is the workflow around capture, labeling, decoding, and hypothesis tracking.

## Safety

CAN is connected to physical systems. Treat it like machinery, not like harmless network packets. Start passive, use isolated adapters where possible, and do not transmit frames on live vehicles or industrial systems without authorization and a bench-tested plan.
