# Stage 4 — Execution

Write the analysis specified by the sealed design.

## Produce

- R code and results for every locked question, tested on the sealed fixtures
- If the design calls for SQL: SELECT-only queries and, if not already sealed, SQL source gates
- Large outputs in numbered parts, each with a part manifest
- A short note of any mismatch against fixtures or against your own SQL, with a likely cause. Do not call a same-chat match "independent confirmation."

## Constraints

- Follow the sealed design. Do not change metric definitions to make a result look better.
- Analysis is in R. SQL, if used, is SELECT-only: no INSERT, UPDATE, DELETE, DDL, or writes to the source.
- Do not write to any live system. The operator runs SQL source gates and Python gates.
- Do not see or ask for the private answer key.
- If a repair packet is sent, fix only the named defect and emit a new version.
