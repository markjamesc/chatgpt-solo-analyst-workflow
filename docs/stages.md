# Stage-by-stage flow

Each step is: operator packs a prompt → the solo chat works → operator captures and seals the reply → operator runs the gate. A failed gate goes back to the owning stage as a new versioned prompt. The chat does not run the Python gates itself.

| Stage | Author | Review | Gate | Owner touchpoint |
|---|---|---|---|---|
| 1 Start | Solo chat | Self-check only (not independent) | G1 decision | None unless the decision is unclear |
| 2 Framing | Solo chat | Self-check only | G2 question lock | Approve the locked question so the run may continue (not an official lock) |
| 2→3 Feasibility | Solo chat | Operator records the verdict; no independent reviewer | G2F feasibility | Only on `partly` / `no` |
| 3 Design | Solo chat | Self-check only | G3 design, G3K early key/count checks | Approve the exact design hash so the run may continue (not an official lock) |
| 4 Execution | Solo chat (R; optional SELECT-only SQL) | Operator runs the gates | G4a source, G4b fixtures, G4c consistency, G4d release | Only after 3 failed repairs or a changed decision |
| 5 Finish | Solo chat | Self-check only | G5 claims, G6 certificate | Human approval of the finish package (not an official Finish lock) |
| Score | Scorer outside the live chat | — | — | — |

## Notes

- Stages 1–2 never see data values. Feasibility sees structure and quality only and cannot add or reshape questions.
- Stage 4 order: any SQL source gates pass → the chat builds the R analysis (and optional SQL) → freeze → fixtures → operator checks consistency → release gate. A same-chat R vs SQL comparison is a consistency check, not an independent reconciliation.
- A difference is traced to a cause and repaired from the design. The design itself does not change without owner change control and a new version.
- Large artifacts are requested in parts from the start and joined with an assembly script that logs every transform. The assembly script and its regression test are **NOT IMPLEMENTED**.
- Passing G3 or G5 in this version does not earn an official Design or Finish lock. The run may continue after owner approval of the current hash. Scoring is on accuracy only.
