# Prompt format and capture (single chat)

Every message from the operator to the live chat is a packet. Packets are sealed once sent and never edited. The chat works only from the packet it receives.

```text
PACKET_ID: <run>-<stage>-<seq>[-vN]
ROLE: solo-chat
STAGE: <1-5 or 2F>
TASK: <one paragraph>
INPUTS:
  - <relative path> sha256=<hash> bytes=<n>   (whole file; parts listed as part k of K)
ALLOWED TO SEE: <list>
NOT ALLOWED TO SEE: answer key; data values in Stages 1-2; <others>
RULES: <only the rules this task needs>
EXPECTED OUTPUT: <files and format; parts if large>
REPLY ENDS WITH: ANSWERED <PACKET_ID> + list of produced files
```

Every reply ends like this. The list is never blank, and `ANSWERED` is the last line:

```text
PRODUCED FILES:
- <path of each file produced>

ANSWERED <PACKET_ID>
```

A reply that settled a missing item from the public files says so, one line per item, and keeps working:

```text
DERIVED: <item> from <public file path>: <how>
```

A reply that must stop because the public files do not settle an item says so, one line per item:

```text
MISSING INPUT: <item>
```

The standing instructions and the stage prompt from [../prompts/](../prompts/) are sent with the packet. They contain no case data.

## Operator duties

- Record send time, the packet hash, and the captured reply hash in the run ledger.
- Check the reply against EXPECTED OUTPUT before sealing it. Reject a reply whose produced-files list is blank or missing, or that does not end with `ANSWERED <PACKET_ID>`, and send a new packet asking for it.
- Build each sent packet from its template as a new version file. Before sending, check that it contains no `TEMPLATE` text and no unfilled `{{placeholder}}`. Leave the template unsent.
- For Stage 4 packets, declare the R version and package versions you will run the code with.
- If the chat has no R runtime, run its script **unchanged**, fixtures first, in that recorded environment (record R and package versions and the exact command), and return raw stdout, stderr and the exit status in a new packet. Do not edit the chat's code, and do not interpret the output for the chat.
- At the end of Stage 5, present the sealed finish package (files and hashes) to the owner and record the owner's approval before scoring.
- A correction is a new packet with a `-vN` suffix that names what it supersedes.
- When a packet is replaced, mark the old ledger row with `superseded_by` (the newer packet id), `superseded_reason` and `superseded_at` (ISO timestamp with zone). Never edit or reseal the old packet; it is no longer counted as open.
- **Before accepting a stop on `MISSING INPUT`**, check the public schema, brief and bundle files yourself and record the result in `artifacts/derivability.json` (item, files checked with hashes, derivable yes/no, derivation or reason). If the item is derivable, send a new `-vN` packet with the derivation and continue. Escalate to the owner only an item the public files do not settle. Never close a stage as unresolved on a derivable item.
- List the public schema, brief and bundle files as inputs in every packet that may need them.
- Never attach a template JSON (`*.example.json`) or any file holding placeholder references (all-zero or `NOT_SET` hashes) as an input.
- Never overwrite or reseal a sent, reviewed, or frozen input.
- Do not put the private answer key, peer-version work, or out-of-stage data in a packet.
- Run the Python gates on the sealed reply. The chat does not run those gates.
- Request large outputs in numbered parts from the start. Assemble them with a script and a transform log. The assembly script and regression test are **NOT IMPLEMENTED**.

## Chat duties

- Work only from the packet. If something needed is missing, stale, or truncated, say so in the reply instead of guessing.
- Before stopping on a missing input or mapping, check the public files in the packet; record `DERIVED:` and continue if they settle it, and write `MISSING INPUT:` only if they do not.
- End every reply with a non-blank `PRODUCED FILES:` list and `ANSWERED <PACKET_ID>` as the last line.
- If the chat cannot run R, emit the script only and wait for the operator's run output. Never invent results.
- Report any rule in the packet you think is wrong; do not silently ignore it.
