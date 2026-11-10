# Public scope

This design is intended for a **public** repository. Publish only the workflow method.

## Never add to this repository

- Private answer keys, tokens, passwords, or credentials
- Case data, extracts, fixtures from a real or benchmark case, or any evidence packet
- Hashes of live case files (hashes of *this* method-repo's own files, as in the draft manifest, are fine)
- Account names, emails, personal profile links, or private bot identifiers
- Local paths of private files
- Raw captures, chat logs, or operator notes that could reveal a case or a key

## What belongs here

- Stage flow, gate definitions, prompt and capture format, comparison protocol, limits, standing prompts, and changelogs
- Later, owner-approved executable gates and tests that use only synthetic, non-sensitive fixtures, if this repository is chosen to hold a copy. The operator owns the runnable gates; they are **NOT IMPLEMENTED** here.

If a document would be useful but contains mixed material, split it and keep the sensitive part out of this repository.
