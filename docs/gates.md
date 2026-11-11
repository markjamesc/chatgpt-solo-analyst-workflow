# Gate list

Every gate returns PASS, FAIL (analysis defect), or TOOL_ERROR. An unrun gate is not PASS. No verbal waiver. All Python gates are owned and run by the **operator**, outside the chat. The live chat may write SELECT-only SQL source gates; it does not run them on a live source.

These are the same gate IDs as Version 2, so the process can be compared. In this Version 1 design, a PASS is a process check only. It does **not** confer an official Design or Finish lock.

| ID | Gate | Written by | Run by | Reviewed by | Checks |
|---|---|---|---|---|---|
| G0 | Packet integrity | Operator (Python) | Operator | — | Every attachment whole, current hash, correct path; no forbidden content; no input with template placeholder references; replaced packets marked superseded (`superseded_by`, reason, time) stay sealed and are not counted |
| GD | Public-file derivability | Operator (Python) | Operator, before accepting any stop | — | Every `MISSING INPUT` checked against the public schema, brief and bundle files; derivable items record the derivation and continue; only non-derivable items stop, escalated to the owner |
| G1 | Decision | Operator (Python) | Operator | — | Decision, owner, actions per result, limits present |
| G2 | Question lock | Operator (Python) | Operator | — | One question; population, window, metric, threshold; capacity stance |
| G2F | Data feasibility | Operator (Python) wraps the chat's output | Operator | — (no independent reviewer) | yes/partly/no plus reason per question; no new questions; structure and quality only |
| G3 | Design | Operator (Python) | Operator | — | Required fields, ML mode explicit, fixtures with worked answers, no template placeholder references, no blanket ban on descriptive rates. No official lock. |
| G3K | Early key/count checks | Operator (Python) | Operator | — | Keys unique, counts reconcile on fixtures; repair cap 3 |
| G4a | SQL source gates | Solo chat, if SQL is used (SELECT-only SQL) | Operator | — | Row counts, keys, duplicates, nulls, ranges match the design |
| G4b | Fixtures | Operator (Python) | Operator | — | The R result (and SQL, if used) match worked answers |
| G4c | Consistency | Operator (Python) | Operator | — | Exact match on locked critical fields; mismatch count 0. Same-chat R vs SQL is not independent confirmation. |
| G4d | Release (Stage 4→5) | Operator (Python) | Operator | — | All lower gates PASS by hash; no open issues |
| G5 | Claims | Operator (Python) | Operator | — | Every material claim tied to sealed evidence; a rate or difference labeled descriptive/associational, not causal. No official Finish lock. |
| G6 | Certificate | Operator (Python) | Operator | — | All stages in order; hashes still current. Certificate of process, not of an official lock. |
| GP | Assembly regression | Operator (Python) | Operator | — | Assembled parts equal the declared whole; no omitted part |

**Python gates stay with the operator.** Each needs a parity test against the existing R gate before use. Status: **NOT IMPLEMENTED**. Until code exists, the operator does the G0, GD, G3 and G5 checks above by hand and records them as manual checks (never an official lock). The Grok team repositories implement the same checks in Python (`gates/derivability.py`, `gates/guards.py`). See [../gates/README.md](../gates/README.md).

**Review coverage.** This version has no separate reviewer. A self-check by the live chat does not count as a required independent review.

**Repair cap.** Three unsuccessful repairs on the same defect, then escalate. Changing wording or adding SQL does not reset the count.
