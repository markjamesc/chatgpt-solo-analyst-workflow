# Stage 3 — Measurement design

Lock how each sealed question will be measured and tested. Use the sealed question and the feasibility verdict. Do not change the question.

## Produce

- An exact definition of every metric, including grain, window, inclusions, and exclusions
- Handling of edge cases (missing values, duplicates, zero denominators, time zones)
- Fixtures with worked answers
- Early key and counting checks
- If SQL will be used later, the SELECT-only SQL source gates that check row counts, keys, duplicates, nulls, and ranges against this design
- A short self-check list of risks (this is not an independent review)

## Constraints

- Do not look beyond the structure and quality already approved for this stage.
- Data must not shape or add questions.
- Fixtures must have worked answers that a later script can check.
- Every fixture or file the design references is a real file with its real sha256. Never copy placeholder fixtures (all-zero or `NOT_SET` hashes) or a template `*.example.json` into the design.
- If the question compares groups, plan the descriptive rates and their differences, labeled descriptive or associational. Do not ban rates; restrict causal wording instead.
- Before you treat a value meaning or a mapping as missing, check the public schema, brief and bundle files. Record what they settle (`DERIVED: ...`) and design with it.
- Large design files must be written in numbered parts, each with a part manifest.
- This design can be approved so the run may continue. That approval is not an official Design lock.
