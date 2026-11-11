# Stage-by-stage flow

Each step is: operator packs a prompt → the solo chat works → operator captures and seals the reply → operator runs the gate. A failed gate goes back to the owning stage as a new versioned prompt. The chat does not run the Python gates itself.

| Stage | Author | Review | Gate | Owner touchpoint |
|---|---|---|---|---|
| 1 Start | Solo chat | Self-check only (not independent) | G1 decision | None unless the decision is unclear |
| 2 Framing | Solo chat | Self-check only | G2 question lock | Approve the locked question so the run may continue (not an official lock) |
| 2→3 Feasibility | Solo chat | Operator records the verdict; no independent reviewer | G2F feasibility | Only on `partly` / `no` |
| 3 Design | Solo chat | Self-check only | G3 design, G3K early key/count checks | Approve the exact design hash so the run may continue (not an official lock) |
| 4 Execution | Solo chat (R; optional SELECT-only SQL) | Operator runs the gates | G4a source, G4b fixtures, G4c consistency, G4d release | Only after 3 failed repairs or a changed decision |
| 5 Finish | Solo chat | Self-check only | G5 claims, G6 certificate | Owner approves the exact sealed finish package **before scoring** (not an official Finish lock) |
| Score | Scorer outside the live chat | — | — | — |

## Notes

- **Before any stop on a missing input.** The chat first checks the public schema, brief and bundle files in its packet. If they settle the item, it writes `DERIVED: <item> from <path>: <how>` and keeps working. Only if they do not does it stop with `MISSING INPUT: <item>`. The operator re-checks the public files and records the result in `artifacts/derivability.json` before accepting any stop: a derivable item goes back as a new `-vN` packet with the derivation; only a non-derivable item is escalated to the owner. No stage closes as "unresolved" on a derivable item.
- Descriptive rates and differences are part of the expected Stage 4 and 5 results when the question compares groups. They are labeled descriptive or associational, never causal.
- Stages 1–2 never see data values. Feasibility sees structure and quality only and cannot add or reshape questions.
- Stage 4 order: any SQL source gates pass → the chat builds the R analysis (and optional SQL) → freeze → fixtures → operator checks consistency → release gate. A same-chat R vs SQL comparison is a consistency check, not an independent reconciliation.
- If the chat has no R runtime, it emits the script only and waits. The operator runs it **unchanged** in a recorded environment (R and package versions), fixtures first, and returns raw stdout, stderr and the exit status in a new packet. The chat interprets only that output and never invents results. A script is done only when every sealed fixture passes in the declared environment.
- Every reply must end with a non-blank `PRODUCED FILES:` list and `ANSWERED <PACKET_ID>`. The operator rejects a reply with a blank or missing list.
- Every sent packet is built from its template as a new version. The operator never sends a packet that still contains `TEMPLATE` or an unfilled `{{placeholder}}`; the template itself stays unsent.
- At the end of Stage 5 the operator presents the sealed finish package (files and hashes) to the owner and records the owner's approval before the run is scored.
- A difference is traced to a cause and repaired from the design. The design itself does not change without owner change control and a new version.
- Large artifacts are requested in parts from the start and joined with an assembly script that logs every transform. The assembly script and its regression test are **NOT IMPLEMENTED**.
- Passing G3 or G5 in this version does not earn an official Design or Finish lock. The run may continue after owner approval of the current hash. Scoring is on accuracy only.
