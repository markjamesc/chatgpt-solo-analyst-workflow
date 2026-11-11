# Standing rules (short list)

1. Do not weaken a gate. No verbal waivers. A PASS in this version is not an official lock.
2. Never overwrite or reseal sent, reviewed, or frozen inputs. Make new versions.
3. Keep the private key away from the live chat. Score blind, after the freeze, by the earlier key preparer.
4. This is one chat doing the whole job. Self-review is not independent review. Say so.
5. Analysis is in R. SQL, if used, is SELECT-only. Python gates are owned and run by the operator outside the chat.
6. No writes to live systems without owner approval.
7. Escalate only material analytical or business changes and required approvals.
8. Repair cap of 3 per defect, then escalate with problems, a recommendation, and a batched revision.
9. Large outputs come in parts, with assembly and a log.
10. No push to `main` without one owner approval.
11. If the chat cannot run R, it emits the script and waits; the operator runs it unchanged in a recorded environment. Never invent results.
12. A script is done only when every sealed fixture passes in the declared R and package baseline.
13. Reject a reply with a blank produced-files list. Never send a packet that still contains template text.
14. The owner approves the sealed finish package before scoring. That is not an official Finish lock.
15. **Check public files before stopping.** Before the chat stops, or the operator closes a stage as unresolved, on a missing input or mapping (what a field value means, which entity is which, a code list, a unit), check the public schema, brief and bundle files. If they settle it, record the derivation and continue. Only an item they do not settle may stop the work, and the operator escalates it to the owner. The operator records each check in `artifacts/derivability.json`.
16. **Descriptive rates are allowed and expected.** Report group rates and their differences (each group's rate and the gap in points) when the question compares groups, labeled descriptive or associational, not causal. Never write a blanket "no rates" rule; restrict causal wording instead.
17. **No template placeholders in the evidence.** Never attach a shape template (`*.example.json`, placeholder fixtures, all-zero or `NOT_SET` hashes) as a packet input or design reference. Use real frozen files with real hashes.
18. **Replaced packets are marked superseded.** When a packet is replaced, mark the old ledger row with `superseded_by`, `superseded_reason` and `superseded_at`. It stays sealed and is no longer counted as open.
