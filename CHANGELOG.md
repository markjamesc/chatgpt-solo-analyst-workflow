# Changelog

All notable changes to this design draft are recorded here. Dates are America/Chicago.

## 0.1.1 — 2026-11-10

Process corrections from the Case B head-to-head run (process only; no case content or answers):

- If the chat has no R runtime, it emits the script only and waits. The operator runs the script **unchanged** in a recorded environment (R and package versions), fixtures first, and returns raw stdout, stderr and the exit status. The chat never invents results (`prompts/standing.md`, `prompts/stage-4-execution.md`, `docs/stages.md`, `docs/handoff.md`, `docs/limits.md`).
- Fixtures first: a script is done only when every sealed fixture passes in the declared environment, and it validates fixture constraints in code (`prompts/stage-4-execution.md`, `prompts/repair.md`).
- Declared package baseline: Stage 4 packets declare R and package versions; code targets them and uses only arguments those versions have.
- Replies must end with a non-blank `PRODUCED FILES:` list and `ANSWERED <PACKET_ID>`; the operator rejects a blank list.
- The operator never sends a packet that still contains `TEMPLATE` text or an unfilled `{{placeholder}}`; sent packets are new versions built from the template.
- The operator presents the sealed finish package for owner approval before scoring. That approval is still not an official Finish lock.
- New rules 11–14 and lessons L6–L11.

## 0.1.0 — 2026-11-09

- Initial local design of the ChatGPT solo workflow (Version 1 of the head-to-head): one ChatGPT Work chat does all five stages, with an operator outside the chat to pack, capture, and run gates.
- Incorporates all ten approved post-benchmark changes as they apply to a single chat (Python gates with parity tests run by the operator, analysis in R, data-feasibility gate, fewer clearer rules, greater autonomy, persistent lessons, feasibility sees structure and quality only, large outputs in parts, early key/counting checks with a 3-round repair cap, and the explainer).
- Records that this version has no independent reviewer, cannot earn an official Design or Finish lock, and is scored on accuracy only. The gates are not weakened.
- Records copyright: the owner holds copyright; no LICENSE file; no license is granted.
- Records scoring: the earlier key preparer from the ChatGPT side holds the private key and scores both versions blind.
- Records the run cap: one attempt per version on Case B, a maximum of 3 repair rounds, stop and report after about a day of work per side, and retry up to 3 times if blocked.
- Gate code, parity tests, assembly scripts, and the assembly regression test are specified only and marked **NOT IMPLEMENTED**. No tests were run.
- Public-scope rule added: method only; no keys, case data, evidence packets, account identifiers, or private paths.
