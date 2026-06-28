---
name: delete-range
description: "Editor primitive for deleting an exact line range after explicit confirmation. Use inside write-code-by-hand mode when the user asks to delete, remove, or cut specific lines or a selected range."
---

# Delete Range

Delete only the exact line range requested.

Operational framing: remove bytes while preserving authorship boundaries.

## Required Inputs

- Target file.
- Start line.
- End line.
- Confirmation for destructive deletion unless the request is already exact and
  explicit.

## Rules

- Delete only the specified contiguous range.
- Do not clean up surrounding blank lines unless separately instructed.
- Do not infer that imports, tests, or references should also be removed.
- If the range is ambiguous, show the nearby lines and ask for a precise range.

## Output

Confirm:

```text
Deleted <path>:<start>-<end>.
```

Report the new cursor location.
