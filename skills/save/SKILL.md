---
name: save
description: "Editor primitive for persisting exact edits and reporting what changed. Use inside write-code-by-hand mode when the user asks to save, write, persist, or commit the current buffer to disk."
---

# Save

Persist exact edits already requested by the user.

## Rules

- Save only files with pending exact edits.
- Do not make additional cleanup changes while saving.
- Report the changed paths.
- If the runtime writes changes immediately, explain that the buffer is already
  saved and report the last changed paths.

## Output

Use:

```text
Saved:
- <path>
```

If there are no pending edits:

```text
No pending exact edits to save.
```
