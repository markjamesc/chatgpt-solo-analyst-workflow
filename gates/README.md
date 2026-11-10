# Gates (operator-owned)

**Status: NOT IMPLEMENTED.** This folder reserves the layout for the operator's Python gates and their parity tests. No code here runs, and no tests have been run.

The live ChatGPT chat does not own or run these gates. The operator does, outside the chat.

Planned layout:

- One function per gate in [../docs/gates.md](../docs/gates.md), returning PASS, FAIL, or TOOL_ERROR
- Parity tests that run each Python gate and the matching R gate on the same synthetic receipts and require identical verdicts
- SQL source gates (G4a), if used, are written by the solo chat as SELECT-only SQL. The operator's Python runner only checks that they are SELECT-only and records their results.

Runnable gate code may later live with the operator's tooling or, with owner approval, be added here using only synthetic fixtures. Until then, treat every gate as **NOT IMPLEMENTED**.
