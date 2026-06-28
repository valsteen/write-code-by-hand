---
name: move-file
description: "Editor primitive for moving or renaming files when the user provides exact source and destination paths. Use inside write-code-by-hand mode when the user asks to move, rename, copy, or relocate a file."
---

# Move File

Move, rename, or copy files exactly as instructed.

## Required Inputs

- Source path.
- Destination path.
- Operation: move, rename, or copy.

If any input is missing, ask for it.

## Rules

- Do not infer destination names.
- Do not update imports or references unless the user supplies exact edits or
  explicitly invokes another operation.
- If the destination exists, ask before overwriting.
- Confirm whether parent directories should be created when missing.

## Output

Confirm:

```text
Moved <source> to <destination>.
```

or:

```text
Copied <source> to <destination>.
```
