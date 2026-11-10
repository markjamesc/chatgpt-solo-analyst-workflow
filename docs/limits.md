# Honest limits (Version 1)

This design must be described accurately. Do not claim more independence or assurance than it has.

## No independent review

One chat does the framing, the design, the analysis, and the interpretation, and then checks its own work. That is **self-review**. It is useful discipline. It is not a second reviewer. Self-review is biased toward the author's own framing and can miss mistakes the author would not think to look for.

Because there is no independent reviewer, this version **cannot earn an official Design or Finish lock** under the current gates. Passing a gate is a process check run by the operator. It is not an official lock. The gate is not weakened to change that.

## Single-model blind spots

The live work is one ChatGPT chat. Errors that this model family tends to make can pass through every stage. A later self-check by the same chat is likely to share those blind spots.

## No independence between R and SQL

If the same chat writes both the R analysis and a SELECT-only SQL computation, agreement between them is a consistency check, not independent confirmation. Do not describe it as a two-analyst or two-family result.

## Operator-run execution

If the chat has no R runtime, the operator runs the chat's script unchanged and returns the raw output. The operator is not an author: it does not edit the code, choose methods, or interpret results. The run record must say that execution was operator-run and name the R and package versions used. Results depend on that declared environment.

## Owner finish approval

The owner approves the sealed finish package before scoring. That approval lets the run be scored as finished. It is still **not** an official Finish lock.

## What this version can still be scored on

Accuracy against the private key, after the freeze, by a scorer who was not the live chat. Time, operator effort, usage, and cost. Completeness of the process record. Those scores are useful. They are not a claim of general superiority, and they are not an official lock.
