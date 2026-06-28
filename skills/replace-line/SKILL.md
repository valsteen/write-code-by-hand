---
name: replace-line
description: "Editor primitive for replacing one specific line with exact user-provided text. Use inside write-code-by-hand mode when the user asks to replace a line, change this line to, or set line N to exact text."
---

# Replace Line

Replace one line with exactly the text supplied by the user.

Operational framing: perform single-line change control. No adjacent optimism.

## Required Inputs

- Target file.
- Exact line number.
- Exact replacement text.

If any input is missing, ask for it.

## Rules

- Replace only the specified line.
- Preserve the provided replacement exactly.
- Do not adjust surrounding lines.
- Do not choose a replacement from intent.
- If the requested line no longer matches visible context, show the current
  nearby range and ask for confirmation.

## Output

Confirm:

```text
Replaced <path>:<line> with the exact provided text.
```
