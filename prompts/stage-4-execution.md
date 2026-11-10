# Stage 4 — Execution

Write the analysis specified by the sealed design.

## Produce

- R code and results for every locked question, tested on the sealed fixtures
- The R and package baseline the code targets (R version and each package version), copied from the packet
- If the design calls for SQL: SELECT-only queries and, if not already sealed, SQL source gates
- Large outputs in numbered parts, each with a part manifest
- A short note of any mismatch against fixtures or against your own SQL, with a likely cause. Do not call a same-chat match "independent confirmation."

## Constraints

- Follow the sealed design. Do not change metric definitions to make a result look better.
- Analysis is in R. SQL, if used, is SELECT-only: no INSERT, UPDATE, DELETE, DDL, or writes to the source.
- Do not write to any live system. The operator runs SQL source gates and Python gates.
- Do not see or ask for the private answer key.
- If a repair packet is sent, fix only the named defect and emit a new version.

## Fixtures first

- A script is done only when it passes **every sealed fixture** in the declared environment. Run the fixtures before the full data. If the fixtures fail, the script is not done; report the failure, do not call it done.
- Validate fixture and input constraints in code and stop with a clear error when they are broken (for example probabilities between 0 and 1 and summing to 1, unique keys, no missing required fields).

## Declared package baseline

- The packet declares the R version and package versions the operator will use. Target that baseline. Do not pass arguments the declared version does not have. Prefer portable base-R constructors over version-specific arguments. If the packet declares no baseline, ask for one before writing code.

## If this chat cannot run R

- Emit the complete script and the exact command to run it, then stop and wait. Do not invent, estimate, or simulate results.
- The operator runs the script **unchanged** in the recorded environment (fixtures first) and returns raw stdout, stderr and the exit status in a new packet. Interpret only that output. If it fails, that is a repair round on the named defect.

## Reply

- End with `PRODUCED FILES:` and one `- <path>` line per file (never blank), then `ANSWERED <PACKET_ID>` as the last line.
