# Persistent lessons

Lessons from benchmark runs are kept as process rules, never as case content or answers.

Format: `ID | observed failure (generic) | rule change | regression test (name or NOT YET WRITTEN)`.

Seed lessons (generic):

- L1 | Large design outputs truncated in one reply | request in parts from the start | GP assembly test (NOT YET WRITTEN)
- L2 | Review counted on a stale or partial file | review coverage requires whole current files; a self-check is not an independent review | G0/G3 coverage test (NOT YET WRITTEN)
- L3 | Counting/key errors found late | run early key/count checks at Stage 3 | G3K test (NOT YET WRITTEN)
- L4 | External account lockouts stalled a run | define a pause rule up front | none
- L5 | Self-review treated as a second reviewer | say so in the limits and do not award an official lock | none

Process lessons from the head-to-head benchmark run (2026-11-10; no case content or answers):

- L6 | The chat had no R runtime, so its first Stage 4 reply was blocked | if the chat cannot run R it emits the script and waits; the operator runs it unchanged in a recorded environment and returns raw output | none (operator rule)
- L7 | A first script failed its own sealed fixture | a script is done only when every sealed fixture passes in the declared environment; validate fixture constraints in code | none (prompt rule)
- L8 | A repaired script called an argument the installed package version does not have | the packet declares the R and package baseline; code targets it and prefers portable constructors | none (prompt rule)
- L9 | The produced-files list was left blank in replies | required `PRODUCED FILES:` format; the operator rejects a blank list | NOT YET WRITTEN
- L10 | A leftover template note was sent in a packet | build sent packets as new versions from the template; never send `TEMPLATE` text or unfilled placeholders | NOT YET WRITTEN
- L11 | The run was scored before the owner approved the finish package | the operator presents the sealed finish package for owner approval before scoring | none (operator rule)
