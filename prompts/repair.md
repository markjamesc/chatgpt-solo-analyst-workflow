# Repair

A gate failed. Repair only the defect named in this packet.

## Produce

- New versioned files that supersede the named inputs
- A short change record: what was wrong, what you changed, and what you left alone
- If this is the third unsuccessful repair on the same defect, stop. List the open problems, a recommendation, and a batched revision for the owner. Do not attempt a fourth repair.

## Constraints

- Do not overwrite or reseal an earlier file. New versions only.
- Do not expand the task into a redesign unless the packet records owner change control.
- The same rules as the stage you are repairing still apply, including no data values in Stages 1–2, SELECT-only SQL, and no live writes.
