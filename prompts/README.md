# Prompts for the solo chat

These are the public-safe instructions the operator gives the ChatGPT Work chat. They contain no case data, keys, evidence, or private paths.

How to use them:

1. Send [standing.md](standing.md) once at the start of the chat, and again with any repair packet if the chat may have lost context.
2. For each stage, send the matching stage file with a sealed packet as defined in [../docs/handoff.md](../docs/handoff.md).
3. For a failed gate, send [repair.md](repair.md) plus a new `-vN` packet that names the defect and the files it supersedes.
4. Never put the private answer key, Version 2 work, or out-of-stage data into a prompt.

| File | When it is sent |
|---|---|
| [standing.md](standing.md) | Start of the run, and with repairs if needed |
| [stage-1-start.md](stage-1-start.md) | Stage 1 |
| [stage-2-framing.md](stage-2-framing.md) | Stage 2 |
| [stage-2f-feasibility.md](stage-2f-feasibility.md) | Between Stages 2 and 3 |
| [stage-3-design.md](stage-3-design.md) | Stage 3 |
| [stage-4-execution.md](stage-4-execution.md) | Stage 4 |
| [stage-5-finish.md](stage-5-finish.md) | Stage 5 |
| [repair.md](repair.md) | After a gate FAIL, if the repair cap has not been reached |
