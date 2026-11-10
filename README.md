# ChatGPT solo analyst workflow (design draft)

This folder is a **local design draft** of a single-chat ChatGPT version of a five-stage analyst workflow. One ChatGPT Work chat does the whole job end to end. It is meant to be published later as a **public method repository**, a portable workflow design, not a case archive.

Suggested public repository name: **`chatgpt-solo-analyst-workflow`**.

Suggested description: *ChatGPT version of an AI-assisted analyst workflow: one ChatGPT Work chat does the whole job alone, built for a head-to-head test against a Grok Bot parent-and-child version.*

Nothing in this draft has been committed or pushed. Do not create a remote, commit to a remote, or merge to `main` until the owner gives explicit approval. A push to `main` needs a separate, single owner approval.

## What this is, and what it is not

- It is the design for **Version 1** of a head-to-head methods test: one ChatGPT Work chat does all five stages alone, compared later with a parent Grok Bot plus child Grok Bots (Version 2).
- Work goes through this chat completely. There are no parent/child roles inside the chat.
- It incorporates the ten approved post-benchmark changes listed below, as they apply to a single chat.
- It is **method only**. It contains no case data, private answer keys, evidence packets, live-file hashes, account names, emails, tokens, or private local paths.
- It does **not** claim that one chat is as accurate as a team, or that self-review is independent review.
- This version has no independent reviewer, so it **cannot earn an official Design or Finish lock** under the current gates. It is scored on **accuracy only**. The gates are **not** weakened.
- Gate **code** is not implemented here. Python gates are owned and run by the operator, outside the chat. See [gates/README.md](gates/README.md).

## Honest limit

This is one chat doing the whole job, including any check of its own work. That is self-review, not independent review. The chat has single-model blind spots, and there is no second author to catch them. Agreement between an R result and a SQL result from the same chat does not count as independent confirmation. See [docs/limits.md](docs/limits.md).

## Who does what

| Role | Who | Job |
|---|---|---|
| Solo chat | One ChatGPT Work chat | Does Stages 1–5: decision, locked question, feasibility check, design, R analysis (and SELECT-only SQL if used), and interpretation. |
| Operator | Outside the chat (a human, or the Version 2 parent bot acting only as operator) | Packs and seals prompts, captures replies, runs Python gates and assembly scripts, records the run, and escalates. Does not author analysis or interpretation. |
| Scorer | The earlier key preparer from the ChatGPT side, who is not the live chat | Holds the private key and scores both versions blind, after both are sealed. |

Stage-by-stage instructions for the chat: [prompts/](prompts/). Prompt and capture format: [docs/handoff.md](docs/handoff.md).

## Stages

1. **Start** — turn a request into a clear decision.
2. **Framing** — turn the decision into one precise, locked question.
3. **Design** — lock how the question will be measured and tested. A **data-feasibility gate** sits between Stage 2 and Stage 3.
4. **Execution** — write and check the code (analysis in R; SQL, if used, is SELECT-only).
5. **Finish** — interpret the sealed results and recommend an action. Scoring happens only after the freeze, by the scorer, who is not the live chat.

Details: [docs/stages.md](docs/stages.md) and [docs/explainer.md](docs/explainer.md).

## Approved post-benchmark changes built into this design

These are design requirements for this draft. They are not yet implemented as executable code, and they must not be pushed to `main` of any repository without one owner approval.

1. **Python gates with parity tests** against the current R gates. Run by the operator outside the chat. Not implemented.
2. **Analysis stays in R.** SQL, if used, is SELECT-only (feasibility, source gates, and an optional second computation). The operator runs any SQL source gates. R and SQL from the same chat are not independent.
3. **Data-feasibility gate** between Stage 2 and Stage 3: `yes` / `partly` / `no`, with a reason. Stages 1 and 2 stay blind to the data. Data must never shape or add questions. A `partly` or `no` goes to the owner.
4. **Fewer, clearer rules**, backed by the evidence rules below.
5. **Greater autonomy.** Escalate only materially consequential analytical or business changes, and genuinely required approvals.
6. **Persistent lessons** from benchmark runs: process lessons only, never keys or case answers. See [docs/lessons.md](docs/lessons.md).
7. **Feasibility gate sees structure and quality only**, not values or the answer key.
8. **Large outputs in parts**, with an assembly script, a transform log, and a regression test for omitted output. The test is not yet written.
9. **Early key and counting checks**, with a repair cap of **3** on the same defect. After that, escalate to the owner with the open problems, a recommendation, and a batched revision.
10. **Explainer document** for the five stages: [docs/explainer.md](docs/explainer.md).

## Standing rules

- **Do not weaken gates.** This Version 1 design is scored on accuracy only, outside the official lock. It does not earn a Design or Finish lock under these rules. Version 2 (the Grok Bot parent-and-child design) may seek an official lock. The gate is not relaxed for this chat.
- **Immutability.** Never overwrite or reseal a sent, reviewed, or frozen input. Repairs create a new versioned artifact and a truthful change record.
- **Blinded scoring.** The live chat never sees the private answer key. The earlier key preparer holds the key and scores after the freeze.
- **No writes to live systems** without owner approval. Default execution uses frozen, hashed extracts or an owner-approved read-only source. SQL, if used, is SELECT-only.
- **Self-review is not a required independent review.** A self-check by this chat does not satisfy a review-coverage rule that needs a separate reviewer.
- **A second computation by the same chat is not a guarantee of independent errors.**

## Run cap (head-to-head test)

One attempt per version on Case B. A maximum of 3 repair rounds. Stop and report after about a day of work per side. If a side is blocked, wait and retry up to 3 times, then report.

## Copyright

The owner holds the copyright to this design. No license is granted, and no LICENSE file is included or should be added. The public may read this repository; that is not permission to copy, modify, or reuse it.

## Document index

| Document | Contents |
|---|---|
| [docs/explainer.md](docs/explainer.md) | Plain-language tour of the five stages |
| [docs/stages.md](docs/stages.md) | Stage-by-stage flow for the single chat |
| [docs/gates.md](docs/gates.md) | Gate list and what each one decides |
| [docs/handoff.md](docs/handoff.md) | Prompt format and capture for the single chat |
| [docs/comparison.md](docs/comparison.md) | Scoring protocol vs the Grok Bot version |
| [docs/limits.md](docs/limits.md) | Honest limits of a single-chat run |
| [docs/lessons.md](docs/lessons.md) | How persistent lessons are recorded |
| [docs/public-scope.md](docs/public-scope.md) | What must never go in this public repository |
| [docs/rules.md](docs/rules.md) | Standing operating rules |
| [prompts/](prompts/) | Stage-by-stage instructions given to the chat |
| [CHANGELOG.md](CHANGELOG.md) | Design revisions |
| [gates/](gates/) | Note on operator-owned Python gates (**NOT IMPLEMENTED**) |

## Status

This is design documentation. Python gates, parity tests, assembly scripts, and the assembly regression test are **NOT IMPLEMENTED**. No tests have been run. No workflow has been started from this draft.
