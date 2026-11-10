# The five stages, explained

1. **Start.** Find the decision behind the request and who makes it.
2. **Framing.** Turn it into one precise question: who or what is measured, over which window, what counts as better, and what threshold changes the decision.
3. **Feasibility, then Design.** First check whether the data can answer the question (yes, partly, or no), looking only at structure and quality. Then define every metric exactly, handle the edge cases, write test cases with known answers, and lock the design for the run. In this Version 1 design, that lock is a run decision, not an official Design lock.
4. **Execution.** Confirm the source with SQL source gates if SQL is used, then build the analysis in R (and, optionally, a SELECT-only SQL computation). Test on the fixtures, let the operator run the gates, and release only when every gate that was run has passed. A pass still does not confer an official lock.
5. **Finish.** Interpret only the sealed results, recommend an action, and score blind afterwards. The live chat does not see the key.

A mistake early carries forward, so Stage 3 matters most. This chat checks its own work; that is not a substitute for a second reviewer. See [limits.md](limits.md).
