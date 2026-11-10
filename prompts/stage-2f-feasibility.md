# Stage 2F — Data-feasibility check

Decide whether the data can answer each locked question already sealed in Stage 2.

## What you may see

Structure and quality summaries only: schemas, keys, grain, null rates, date ranges, duplicate rates, and similar quality facts. You must not see row-level values, aggregates that answer the question, or the answer key.

## Produce

For each locked question, a verdict: `yes`, `partly`, or `no`, with a reason. If you write checks, write them as SELECT-only SQL (row counts, keys, duplicates, nulls, ranges). Do not run them on a live source; the operator will run them.

## Constraints

- Do not propose, add, or reshape questions from the data.
- Do not use values that would start to answer the question.
- A `partly` or `no` must be clear enough for the owner to decide whether to stop, narrow, or change the question under change control.
