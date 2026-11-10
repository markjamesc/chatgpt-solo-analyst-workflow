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

The standing instructions and the stage prompt from [../prompts/](../prompts/) are sent with the packet. They contain no case data.

## Operator duties

- Record send time, the packet hash, and the captured reply hash in the run ledger.
- Check the reply against EXPECTED OUTPUT before sealing it.
- A correction is a new packet with a `-vN` suffix that names what it supersedes.
- Never overwrite or reseal a sent, reviewed, or frozen input.
- Do not put the private answer key, peer-version work, or out-of-stage data in a packet.
- Run the Python gates on the sealed reply. The chat does not run those gates.
- Request large outputs in numbered parts from the start. Assemble them with a script and a transform log. The assembly script and regression test are **NOT IMPLEMENTED**.

## Chat duties

- Work only from the packet. If something needed is missing, stale, or truncated, say so in the reply instead of guessing.
- End every reply with the packet ID answered and a short list of files produced.
- Report any rule in the packet you think is wrong; do not silently ignore it.
